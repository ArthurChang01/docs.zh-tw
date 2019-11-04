---
title: 屬性變更事件
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], change events
- property value changes [WPF]
- change events [WPF], property
- events [WPF], change in property values
- creating property triggers [WPF]
- property change events [WPF], types of
- property change events [WPF]
- property triggers [WPF]
- identifying changed property events [WPF]
- property triggers [WPF], definition of
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
ms.openlocfilehash: 68be4c6bf7cce8a3aeb928e1f0b0e8131263320c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459337"
---
# <a name="property-change-events"></a>屬性變更事件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 會定義數個要引發來回應屬性值變更的事件。 屬性通常是相依性屬性。 事件本身有時是路由事件，有時是標準的 common language runtime （CLR）事件。 事件的定義會因案例而異，因為某些屬性變更較適合透過元素樹狀結構進行路由傳送，而其他屬性變更通常只會與變更屬性的物件有關。  
  
## <a name="identifying-a-property-change-event"></a>識別屬性變更事件  
 並非所有報告屬性變更的事件都會明確識別為屬性已變更的事件，不論是透過簽章模式或命名模式。 一般來說，SDK 檔中的事件描述會指出事件是否直接系結至屬性值變更，並提供屬性和事件之間的交互參考。  
  
### <a name="routedpropertychanged-events"></a>RoutedPropertyChanged 事件  
 某些事件會使用明確用於屬性變更事件的事件資料類型和委派。 事件資料類型為 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>，且委派為 <xref:System.Windows.RoutedPropertyChangedEventHandler%601>。 事件資料和委派兩者都有一個泛型類型參數，可在您定義處理常式時，指定變更屬性的實際類型。 事件資料包含兩個屬性，<xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> 和 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>，這兩者都會當做事件資料中的型別引數傳遞。  
  
 名稱中 "Routed" 的部分表示已將屬性已變更的事件註冊為路由事件。 路由傳送屬性已變更事件的優點是，如果子元素 (控制項的複合組件) 上的屬性會變更值，控制項的最上層就可以接收屬性已變更的事件。 例如，您可以建立一個包含 <xref:System.Windows.Controls.Primitives.RangeBase> 控制項（例如 <xref:System.Windows.Controls.Slider>）的控制項。 如果 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 屬性的值在滑杆元件上變更，您可能會想要在父控制項上處理該變更，而不是在元件上。  
  
 由於您有舊值與新值，因此，您可能想要使用此事件處理常式做為屬性值的驗證程式。 不過，大多數屬性已變更事件的設計意圖並不在此。 一般來說，之所以提供值，是要讓您在程式碼的其他邏輯區域對那些值執行動作，但不建議在事件處理常式內實際變更值，而且根據處理常式的實作方式而定，這可能會導致意外遞迴。  
  
 如果您的屬性是自訂相依性屬性，或如果您正在使用已定義具現化程式碼的衍生類別，則會有更好的機制來追蹤內建于 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統中的屬性變更：屬性系統回呼 <xref:System.Windows.CoerceValueCallback> 和 <xref:System.Windows.PropertyChangedCallback>。 如需您如何使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統進行驗證和強制型轉的詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)及[自訂相依性屬性](custom-dependency-properties.md)。  
  
### <a name="dependencypropertychanged-events"></a>DependencyPropertyChanged 事件  
 另一對屬於屬性已變更事件案例的類型，是 <xref:System.Windows.DependencyPropertyChangedEventArgs> 和 <xref:System.Windows.DependencyPropertyChangedEventHandler>。 這些屬性變更的事件不會路由傳送;它們是標準的 CLR 事件。 <xref:System.Windows.DependencyPropertyChangedEventArgs> 是不尋常的事件資料包告類型，因為它不是衍生自 <xref:System.EventArgs>;<xref:System.Windows.DependencyPropertyChangedEventArgs> 是一種結構，而不是類別。  
  
 使用 <xref:System.Windows.DependencyPropertyChangedEventArgs> 和 <xref:System.Windows.DependencyPropertyChangedEventHandler> 的事件比 `RoutedPropertyChanged` 事件稍微常見。 <xref:System.Windows.UIElement.IsMouseCapturedChanged>使用這些類型的事件範例。  
  
 如同 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>，<xref:System.Windows.DependencyPropertyChangedEventArgs> 也會報告屬性的舊值和新值。 此外，能對值執行的動作也適用同樣的考量，一般不建議嘗試在傳送端再次變更值來回應事件。  
  
## <a name="property-triggers"></a>屬性觸發程序  
 與屬性已變更事件密切相關的概念是屬性觸發程序。 屬性觸發程序建立於樣式或範本內，可讓您根據指派該屬性觸發程序之屬性的值來建立條件式行為。  
  
 屬性觸發程序的屬性必須是相依性屬性。 它可以 (而且通常) 是唯讀的相依性屬性。 當控制項所公開的相依性屬性至少有部分設計為屬性觸發程序時，可以從屬性名稱是否以 "Is" 開頭來辨識。 以此命名的屬性通常是唯讀的布林值相依性屬性，屬性的主要用途是報告可能對即時 UI 產生影響的控制項狀態，因此可做為屬性觸發程序候選項目。  
  
 這其中部分屬性也會有專用的屬性已變更事件。 例如，屬性 <xref:System.Windows.UIElement.IsMouseCaptured%2A> 有屬性已變更事件 <xref:System.Windows.UIElement.IsMouseCapturedChanged>。 屬性本身是唯讀的，其值會由輸入系統調整，而輸入系統會在每次即時變更時引發 <xref:System.Windows.UIElement.IsMouseCapturedChanged>。  
  
 相較於真正的屬性已變更事件，使用屬性觸發程序對屬性變更採取動作有一些限制。  
  
 屬性觸發程序可透過精確比對邏輯來運作。 您可以指定屬性和值，以指出觸發程式將作用的特定值。例如： `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`。 由於此限制，屬性觸發程序多用於布林值屬性，或是接受專用列舉值的屬性，其中的可能值範圍容易管理，可為每種情況定義觸發程序。 或者，屬性觸發程序只能用於特殊值，例如，當項目計數到達零，且沒有任何觸發程序負責當屬性值再從零變成其他數字的情況 (這裡不使用適用所有情況的觸發程序，您在此處可能需要一個程式碼事件處理常式，或是當值為非零值時，再次從觸發程序狀態切換回來的預設行為)。  
  
 屬性觸發程序語法類似於程式設計中的 "if" 陳述式。 如果觸發程序條件為 true，接著就會「執行」屬性觸發程序的「主體」。 屬性觸發程序的「主體」不是程式碼，而是標記。 該標記僅限於使用一或多個 <xref:System.Windows.Setter> 元素來設定套用樣式或範本之物件的其他屬性。  
  
 若要位移具有各種可能值之屬性觸發程式的 "if" 條件，通常建議使用 <xref:System.Windows.Setter>，將相同的屬性值設定為預設值。 如此一來，當觸發條件為 true 時，<xref:System.Windows.Trigger> 包含的 setter 會有優先順序，而且當觸發條件為 false 時，不在 <xref:System.Windows.Trigger> 內的 <xref:System.Windows.Setter> 會有優先順序。  
  
 一般適合使用屬性觸發程序的情況是，一或多個外觀屬性會根據同一個元素上的其他屬性狀態而變更。  
  
 若要深入了解屬性觸發程序，請參閱[設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。  
  
## <a name="see-also"></a>請參閱

- [路由事件概觀](routed-events-overview.md)
- [相依性屬性概觀](dependency-properties-overview.md)
