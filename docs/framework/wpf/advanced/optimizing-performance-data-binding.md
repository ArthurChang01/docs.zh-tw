---
title: 最佳化效能：資料繫結
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 31fdc3c31c8792fea5f3e71dedb7370ebd63c98e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458556"
---
# <a name="optimizing-performance-data-binding"></a>最佳化效能：資料繫結
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結在資料的展示和互動上，提供應用程式簡單而一致的方式。 元素可以系結至各種資料來源中的資料，其格式為 CLR 物件和 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]。  
  
 本主題提供資料繫結的效能建議。  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>資料繫結參考的解析方式  
 在討論資料繫結效能問題之前，值得先探討 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結引擎如何解析物件參考以進行繫結。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料系結的來源可以是任何 CLR 物件。 您可以系結至 CLR 物件的屬性、子屬性或索引子。 您可以使用 Microsoft .NET Framework 反映或 <xref:System.ComponentModel.ICustomTypeDescriptor>來解析系結參考。 以下是三種解析繫結用之物件參考的方法。  
  
 第一個方法涉及使用反映。 在此情況下，<xref:System.Reflection.PropertyInfo> 物件是用來探索屬性（property）的屬性（attribute），並提供屬性中繼資料的存取權。 使用 <xref:System.ComponentModel.ICustomTypeDescriptor> 介面時，資料系結引擎會使用此介面來存取屬性值。 在物件沒有靜態屬性集的情況下，<xref:System.ComponentModel.ICustomTypeDescriptor> 介面特別有用。  
  
 藉由執行 <xref:System.ComponentModel.INotifyPropertyChanged> 介面或使用與 <xref:System.ComponentModel.TypeDescriptor>相關聯的變更通知，即可提供屬性變更通知。 不過，用來執行屬性變更通知的慣用策略是使用 <xref:System.ComponentModel.INotifyPropertyChanged>。  
  
 如果來源物件是 CLR 物件，且 source 屬性是 CLR 屬性，則 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料系結引擎必須先在來源物件上使用反映來取得 <xref:System.ComponentModel.TypeDescriptor>，然後查詢 <xref:System.ComponentModel.PropertyDescriptor>。 這個反映作業序列從效能觀點來看可能非常耗時。  
  
 解析物件參考的第二個方法包含可執行 <xref:System.ComponentModel.INotifyPropertyChanged> 介面的 CLR 來源物件，以及屬於 CLR 屬性的來源屬性。 在此情況下，資料繫結引擎會直接對來源類型使用反映，並取得必要的屬性。 這仍不是最佳的方法，但它的工作集需求的成本會比第一種方法低。  
  
 解析物件參考的第三個方法包含一個 <xref:System.Windows.DependencyObject> 的來源物件，以及一個 <xref:System.Windows.DependencyProperty>的來源屬性。 在此情況下，資料繫結引擎不必使用反映。 相反地，屬性引擎和資料繫結引擎會一起獨立解析屬性參考。 這是解析用於資料繫結之物件參考的最佳方法。  
  
 下表比較使用這三種方法，將資料系結至 1000 <xref:System.Windows.Controls.TextBlock> 元素的 <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性的速度。  
  
|**繫結 TextBlock 的 Text 屬性**|**繫結時間 (毫秒)**|**轉譯時間 -- 包括繫結 (毫秒)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|至 CLR 物件的屬性|115|314|  
|至執行之 CLR 物件的屬性（property） <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|<xref:System.Windows.DependencyObject>的 <xref:System.Windows.DependencyProperty>。|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>繫結至大型 CLR 物件  
 當您將資料系結至具有數千個屬性的單一 CLR 物件時，會有明顯的效能影響。 將單一物件劃分成多個具有較少屬性的 CLR 物件，可以將此影響降至最低。 下表顯示資料系結至單一大型 CLR 物件與多個較小物件的系結和轉譯時間。  
  
|**資料繫結 1000 個 TextBlock 物件**|**繫結時間 (毫秒)**|**轉譯時間 -- 包括繫結 (毫秒)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|至具有1000屬性的 CLR 物件|950|1200|  
|至具有一個屬性的 1000 CLR 物件|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>繫結至 ItemsSource  
 假設您有一個 CLR <xref:System.Collections.Generic.List%601> 物件，其中包含您想要在 <xref:System.Windows.Controls.ListBox>中顯示的員工清單。 若要建立這兩個物件之間的對應，您可以將員工清單系結至 <xref:System.Windows.Controls.ListBox>的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性。 不過，假設您有新的員工加入您的群組。 您可能會認為，為了將這個新人員插入您的系結 <xref:System.Windows.Controls.ListBox> 值，您只需將此人員加入您的員工清單，並預期資料系結引擎會自動辨識這項變更。 該假設會證明 false;實際上，這項變更不會自動反映在 <xref:System.Windows.Controls.ListBox> 中。 這是因為 CLR <xref:System.Collections.Generic.List%601> 物件不會自動引發集合已變更事件。 為了讓 <xref:System.Windows.Controls.ListBox> 取得變更，您必須重新建立員工清單，並將其重新附加至 <xref:System.Windows.Controls.ListBox>的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性。 雖然這個解決方案有效，但它造成了嚴重的效能影響。 每次您將 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 重新指派給新的物件時，<xref:System.Windows.Controls.ListBox> 會先擲回其先前的專案，然後重新產生整個清單。 如果您的 <xref:System.Windows.Controls.ListBox> 對應至複雜的 <xref:System.Windows.DataTemplate>，則會影響效能。  
  
 此問題的一個非常有效率的解決方案，就是讓您的員工清單成為 <xref:System.Collections.ObjectModel.ObservableCollection%601>。 <xref:System.Collections.ObjectModel.ObservableCollection%601> 物件會引發資料系結引擎可以接收的變更通知。 事件會從 <xref:System.Windows.Controls.ItemsControl> 中新增或移除專案，而不需要重新產生整個清單。  
  
 下表顯示新增一個專案時，更新 <xref:System.Windows.Controls.ListBox> （已關閉 UI 虛擬化）所需的時間。 第一個資料列中的數位代表 CLR <xref:System.Collections.Generic.List%601> 物件系結至 <xref:System.Windows.Controls.ListBox> 元素 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的經過時間。 第二個數據列中的數位代表當 <xref:System.Collections.ObjectModel.ObservableCollection%601> 系結至 <xref:System.Windows.Controls.ListBox> 元素的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>時所經過的時間。 請注意，使用 <xref:System.Collections.ObjectModel.ObservableCollection%601> 的資料系結策略可節省大量時間。  
  
|**資料繫結 ItemsSource**|**1 個項目的更新時間 (毫秒)**|  
|--------------------------------------|---------------------------------------|  
|至 CLR <xref:System.Collections.Generic.List%601> 物件|1656|  
|至 <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>將 IList 繫結至 ItemsControl 而非 IEnumerable  
 如果您可以選擇將 <xref:System.Collections.Generic.IList%601> 或 <xref:System.Collections.IEnumerable> 系結至 <xref:System.Windows.Controls.ItemsControl> 物件，請選擇 <xref:System.Collections.Generic.IList%601> 物件。 將 <xref:System.Collections.IEnumerable> 系結至 <xref:System.Windows.Controls.ItemsControl> 會強制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 建立包裝函式 <xref:System.Collections.Generic.IList%601> 物件，這表示您的效能會受到第二個物件不必要的額外負荷影響。  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>不要只為了資料繫結而將 CLR 物件轉換成 XML。  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您將資料系結至 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 內容;不過，[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 內容的資料系結會比系結至 CLR 物件的資料更慢。 如果唯一的目的是要進行資料系結，請勿將 CLR 物件資料轉換成 XML。  
  
## <a name="see-also"></a>請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [逐步解說：在 WPF 應用程式中快取應用程式資料](walkthrough-caching-application-data-in-a-wpf-application.md)
