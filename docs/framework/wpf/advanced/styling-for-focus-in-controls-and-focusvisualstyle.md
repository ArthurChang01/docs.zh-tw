---
title: 設定控制項中焦點的樣式和 FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 988b084144532df6f7a6073184fcf035b0813bfd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458674"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>設定控制項中焦點的樣式和 FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供兩種平行機制，在控制項接收到鍵盤焦點時，用來變更它的視覺外觀。 第一種機制是在套用至控制項的樣式或範本中，使用屬性（例如 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>）的屬性 setter。 第二個機制是提供另一個樣式做為 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 屬性的值;「焦點視覺化樣式」會針對在控制項之上繪製的裝飾項，建立個別的視覺化樹狀結構，而不是藉由取代控制項或其他 UI 專案的視覺化樹狀結構來變更它。 本主題將討論每一種機制的適用案例。  

<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>焦點視覺化樣式的用途  
 焦點視覺化樣式功能提供常見的「物件模型」，以介紹根據鍵盤瀏覽至任何 UI 元素的視覺化使用者回饋。 即使不將新的範本套用至控制項，或是知道特定的範本組合，還是能夠達成此目的。  
  
 不過，正因為焦點視覺化樣式功能可以在不知道控制項範本的情況下運作，所以，一定要限制可使用焦點視覺化樣式，針對控制項顯示的視覺化回饋。 此功能真正的運作方式是，在視覺化樹狀結構上方重疊不同的視覺化樹狀結構 (提示)，如同由控制項透過其範本的轉譯來建立。 您可以使用填滿 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> 屬性的樣式來定義此個別的視覺化樹狀結構。  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>預設的焦點視覺化樣式行為  
 只有當焦點動作是由鍵盤所起始時，焦點視覺化樣式才會運作。 任何的滑鼠動作或程式設計焦點變更，都會停用焦點視覺化樣式的模式。 如需焦點模式之間差異的詳細資訊，請參閱[焦點概觀](focus-overview.md)。  
  
 控制項的佈景主題包括預設的焦點視覺化樣式行為，其會成為佈景主題中所有控制項的焦點視覺化樣式。 這個主題樣式是以靜態金鑰 <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>的值來識別。 當您在應用程式層級宣告自己的焦點視覺化樣式時，會取代佈景主題的這個預設樣式行為。 或者，如果您定義整個佈景主題，則您應該使用這個相同的索引鍵，針對整個佈景主題定義預設行為的樣式。  
  
 在佈景主題中，預設的焦點視覺化樣式通常非常簡單。 以下是一種概略的方式：  
  
```xaml  
<Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}">  
  <Setter Property="Control.Template">  
    <Setter.Value>  
      <ControlTemplate>  
        <Rectangle StrokeThickness="1"  
          Stroke="Black"  
          StrokeDashArray="1 2"  
          SnapsToDevicePixels="true"/>  
      </ControlTemplate>  
    </Setter.Value>  
  </Setter>  
</Style>  
```  
  
<a name="When"></a>   
## <a name="when-to-use-focus-visual-styles"></a>使用焦點視覺化樣式的時機  
 概念上，套用至控制項的焦點視覺化樣式外觀在各個控制項之間應該保持一致。 確保一致性的方法之一是，只有當您在撰寫整個佈景主題時，才能變更焦點視覺化樣式，而定義於該佈景主題中的每一個控制項都會取得完全相同的焦點視覺化樣式，或是控制項之間視覺上相關之樣式的一些變化。 另外，您可以使用相同的樣式 (或類似樣式)，為頁面上或 UI 中每一個可透過鍵盤取得焦點的元素設定樣式。  
  
 針對不屬於主題一部分的個別控制項樣式設定 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>，並不是要使用焦點視覺化樣式。 這是因為控制項之間不一致的視覺化行為，可導致使用者在關於鍵盤焦點方面得到令人困惑的體驗。 如果您想要針對在主題中刻意不一致的鍵盤焦點來執行控制項特定的行為，更好的方法是在個別輸入狀態屬性的樣式中使用觸發程式，例如 <xref:System.Windows.UIElement.IsFocused%2A> 或 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>。  
  
 焦點視覺化樣式是鍵盤焦點專用的。 因此，焦點視覺化樣式是一種協助工具功能。 如果您想要針對任何類型的焦點進行 UI 變更 (不論是透過滑鼠、鍵盤或程式設計)，則您不應該使用焦點視覺化樣式，而應該在從一般焦點屬性 (例如 <xref:System.Windows.UIElement.IsFocused%2A> 或 <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>) 的值運作的樣式或範本中改用 setter 和觸發程序。  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>建立焦點視覺化樣式的方式  
 您為焦點視覺化樣式所建立的樣式，應一律具有 <xref:System.Windows.Controls.Control>的 <xref:System.Windows.Style.TargetType%2A>。 樣式應主要由 <xref:System.Windows.Controls.ControlTemplate>組成。 您不會將目標型別指定為將焦點視覺化樣式指派給 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>的類型。  
  
 因為目標型別一律 <xref:System.Windows.Controls.Control>，所以您必須使用所有控制項通用的屬性（使用 <xref:System.Windows.Controls.Control> 類別的屬性及其基類）來設定樣式。 您應該建立將正常運作的範本來與 UI 元素重疊，而且將不會混淆控制項的功能區域。 一般而言，這表示視覺化回饋應該出現在控制項邊界外部，或者做為暫時性或不引人注目的效果，這類效果將不會在套用焦點視覺化樣式的控制項上封鎖點擊測試。 您可以在範本系結中使用的屬性，其適用于判斷重迭範本的大小和位置，包括 <xref:System.Windows.FrameworkElement.ActualHeight%2A>、<xref:System.Windows.FrameworkElement.ActualWidth%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>和 <xref:System.Windows.Controls.Control.Padding%2A>。  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>使用焦點視覺化樣式的替代方案  
 針對不適合使用焦點視覺化樣式的情況 (可能是因為您只設定單一控制項的樣式，或因為您想要對控制項範本有更大的控制權)，有許多其他可存取的屬性和技術可用於建立視覺化行為來回應焦點的變更。  
  
 如需所有對觸發程序、setter 及事件 setter 的詳細討論，請參閱[設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。 [路由事件概觀](routed-events-overview.md)中則會討論如何處理路由事件。  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 如果您特別想要使用鍵盤焦點，<xref:System.Windows.UIElement.IsKeyboardFocused%2A> 相依性屬性可以用於屬性 <xref:System.Windows.Trigger>。 若要定義非常專屬於單一控制項的鍵盤焦點行為，樣式或範本中的屬性觸發程序是更為合適的技術，而這可能不會以視覺化方式符合其他控制項的鍵盤焦點行為。  
  
 另一個類似的相依性屬性會 <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>，如果您想要以視覺方式呼叫鍵盤焦點位於控制項的功能區域內的某個位置，則可能適合使用。 例如，您可能會放置一個 <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> 觸發程式，讓數個控制群組成群組的面板會以不同的方式出現，即使鍵盤焦點可能更精確地放在該面板內的個別元素上。  
  
 您也可以使用 [事件 <xref:System.Windows.UIElement.GotKeyboardFocus>] 和 [<xref:System.Windows.UIElement.LostKeyboardFocus>] （以及其預覽對等專案）。 您可以使用這些事件做為 <xref:System.Windows.EventSetter>的基礎，也可以在程式碼後置中撰寫事件的處理常式。  
  
### <a name="other-focus-properties"></a>其他焦點屬性  
 如果您想要變更焦點的所有可能原因都要產生視覺行為，您應該以 <xref:System.Windows.UIElement.IsFocused%2A> 相依性屬性為 setter 或觸發程式，或是在用於 <xref:System.Windows.EventSetter>的 <xref:System.Windows.UIElement.GotFocus> 或 <xref:System.Windows.UIElement.LostFocus> 事件上。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [焦點概觀](focus-overview.md)
- [輸入概觀](input-overview.md)
