---
title: 自訂控制項的 UI 自動化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
ms.openlocfilehash: a370ed2c6b1f3273eca93b4865a032e8299f1cfb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738195"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>WPF 自訂控制項的 UI 自動化
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] 提供一個單一的通用介面，可讓自動化用戶端用來檢查或操作各種平台和架構的使用者介面。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 可讓品質保證 (測試) 程式碼和協助工具應用程式 (例如螢幕助讀程式) 檢查使用者介面元素，並模擬從其他程式碼與它們進行的使用者互動。 如需跨所有平台之 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 的相關資訊，請參閱＜協助工具＞。  
  
 本主題說明如何針對在 WPF 應用程式中執行的自訂控制項，實作伺服器端 UI 自動化提供者。 WPF 是透過與使用者介面元素樹狀結構平行的對等自動化物件樹狀結構，來支援 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]。 提供協助工具功能的測試程式碼和應用程式，可以直接使用自動化對等物件 (針對同處理序程式碼)，或透過由 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 提供的一般介面來使用這些物件。  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>自動化對等類別  
 WPF 控制項透過衍生自 <xref:System.Windows.Automation.Peers.AutomationPeer>的對等類別樹狀結構，支援 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]。 依照慣例，對等類別名稱會以控制項類別名稱開始，並以 "AutomationPeer" 結束。 例如，<xref:System.Windows.Automation.Peers.ButtonAutomationPeer> 是 <xref:System.Windows.Controls.Button> 控制項類別的對等類別。 對等類別大致上相當於 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 控制項型別，但僅適用于 WPF 元素。 透過 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 介面存取 WPF 應用程式的自動化程式碼並不會直接使用自動化對等，但相同處理序空間中的自動化程式碼則可以直接使用自動化對等。  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>內建自動化對等類別  
 如果元素接受來自使用者的介面活動，或包含螢幕助讀應用程式使用者所需的資訊，便會實作自動化對等類別。 並非所有 WPF 視覺元素都有自動化對等。 執行自動化對等的類別範例包括 <xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.TextBox>和 <xref:System.Windows.Controls.Label>。 未執行自動化對等的類別範例，是衍生自 <xref:System.Windows.Controls.Decorator>的類別，例如 <xref:System.Windows.Controls.Border>，以及以 <xref:System.Windows.Controls.Panel>為基礎的類別，例如 <xref:System.Windows.Controls.Grid> 和 <xref:System.Windows.Controls.Canvas>。  
  
 基底 <xref:System.Windows.Controls.Control> 類別沒有對應的對等類別。 如果您需要對等類別，使其對應到衍生自 <xref:System.Windows.Controls.Control>的自訂控制項，您應該從 <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>衍生自訂的對等類別。  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>衍生對等的安全性考量  
 自動化對等必須在部分信任的環境中執行。 UIAutomationClient 組件中的程式碼並沒有針對在部分信任的環境中執行進行設定，因此自動化對等程式碼不應該參考該組件。 您應該改為使用 UIAutomationTypes 組件中的類別。 例如，您應該使用 UIAutomationTypes 元件中的 <xref:System.Windows.Automation.AutomationElementIdentifiers> 類別，其對應至 Uiautomationclient.dll 元件中的 <xref:System.Windows.Automation.AutomationElement> 類別。 在自動化對等程式碼中參考 UIAutomationTypes 組件是安全的。  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>對等瀏覽  
 尋找自動化對等之後，同進程程式碼可以藉由呼叫物件的 <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> 和 <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> 方法來導覽對等樹狀結構。 在控制項內的 WPF 專案之間流覽，是由 <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> 方法的對等執行所支援。 UI 自動化系統會呼叫此方法來建置控制項內所包含之子元素的樹狀結構，例如清單方塊中的清單項目。 預設 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> 方法會遍歷元素的視覺化樹狀結構，以建立自動化對等的樹狀結構。 自訂控制項會覆寫此方法，以將子系元素公開給自動化用戶端，並傳回能傳達資訊或允許使用者互動的元素自動化對等。  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>衍生對等中的自訂  
 衍生自 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 的所有類別都包含受保護的虛擬方法 <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>。 WPF 會呼叫 <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> 來取得每個控制項的自動化對等物件。 自動化程式碼可以使用對等來取得控制項特性和功能的相關資訊，並模擬互動式使用。 支援 automation 的自訂控制項必須覆寫 <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>，並傳回衍生自 <xref:System.Windows.Automation.Peers.AutomationPeer>之類別的實例。 例如，如果自訂控制項是從 <xref:System.Windows.Controls.Primitives.ButtonBase> 類別衍生而來，則 <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> 所傳回的物件應該衍生自 <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>。  
  
 實作自訂控制項時，您必須從描述您自訂控制項唯一且特定之行為的基底自動化對等類別，覆寫 "Core" 方法。  
  
### <a name="override-oncreateautomationpeer"></a>覆寫 OnCreateAutomationPeer  
 覆寫自訂控制項的 <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> 方法，使其傳回提供者物件，必須直接或間接從 <xref:System.Windows.Automation.Peers.AutomationPeer>衍生。  
  
### <a name="override-getpattern"></a>覆寫 GetPattern  
 自動化對等可簡化伺服器端 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 提供者的部分實作層面，但自訂控制項自動化對等仍須處理模式介面。 如同非 WPF 提供者，對等會藉由在 <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> 命名空間（例如 <xref:System.Windows.Automation.Provider.IInvokeProvider>）中提供介面的執行，來支援控制項模式。 控制項模式介面可以由對等本身實作，或是由另一個物件實作。 對等的 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> 的執行會傳回支援指定模式的物件。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 程式碼會呼叫 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> 方法，並指定 <xref:System.Windows.Automation.Peers.PatternInterface> 列舉值。 您的 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> 覆寫應該會傳回執行指定模式的物件。 如果您的控制項沒有模式的自訂執行，您可以呼叫基底類型的 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> 來取得其實值，如果此控制項類型不支援此模式，則會傳回 null。 例如，自訂的 NumericUpDown 控制項可以設定為範圍內的值，因此它的 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 對等會執行 <xref:System.Windows.Automation.Provider.IRangeValueProvider> 介面。 下列範例顯示如何覆寫對等的 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> 方法，以回應 <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> 值。  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> 方法也可以指定子項目做為模式提供者。 下列程式碼顯示 <xref:System.Windows.Controls.ItemsControl> 如何將捲軸模式處理傳輸至其內部 <xref:System.Windows.Controls.ScrollViewer> 控制項的對等體。  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 若要指定用於模式處理的子項目，此程式碼會取得子項目物件、使用 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> 方法建立對等、將新對等的 <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> 屬性設定為目前的對等，並傳回新的對等。 在子項目上設定 <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> 會防止子項目出現在自動化對等樹狀目錄中，並將子項目引發的所有事件指定為來自 <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>中指定的控制項。 <xref:System.Windows.Controls.ScrollViewer> 控制項不會出現在自動化樹狀目錄中，而它所產生的滾動事件就會顯示為來自 <xref:System.Windows.Controls.ItemsControl> 物件。  
  
### <a name="override-core-methods"></a>覆寫 "Core" 方法  
 自動化程式碼會呼叫對等類別的公用方法，來取得控制項的相關資訊。 若要提供您控制項的相關資訊，請在您的控制項實作和由基底自動化對等類別所提供的不同時，覆寫所有名稱以 "Core" 為結尾的方法。 您的控制項至少必須執行 <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> 和 <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> 方法，如下列範例所示。  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 您的 <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> 的執行會藉由傳回 <xref:System.Windows.Automation.ControlType> 值來描述您的控制項。 雖然您可以傳回 <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>，但如果它正確地描述您的控制項，您應該傳回其中一個更特定的控制項類型。 <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> 的傳回值需要額外的工作，讓提供者能夠執行 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]，而 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 用戶端產品無法預期控制結構、鍵盤互動，以及可能的控制項模式。  
  
 執行 <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> 和 <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> 方法，以指出您的控制項是否包含資料內容，或在使用者介面（或兩者）中滿足互動式角色。 根據預設，這兩個方法皆會傳回 `true`。 這些設定能改善自動化工具 (例如螢幕助讀程式) 的可用性，這些工具可以使用這些方法來篩選自動化樹狀結構。 如果您的 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> 方法會將模式處理傳輸至子項目對等體，子項目對等的 <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> 方法可能會傳回 false，以隱藏來自 automation 樹狀結構的子項目對等體。 例如，<xref:System.Windows.Controls.ListBox> 中的滾動是由 <xref:System.Windows.Controls.ScrollViewer>所處理，而 <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> 的自動化對等則是由與 <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> 相關聯之 <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>的 <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> 方法所傳回。因此，<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> 的 <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> 方法會傳回 `false`，因此 <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> 不會出現在自動化樹狀結構中。  
  
 您的自動化對等應該為您的控制項提供適當的預設值。 請注意，參考您控制項的 XAML 可以藉由包含 <xref:System.Windows.Automation.AutomationProperties> 屬性來覆寫核心方法的對等執行。 例如，下列 XAML 會建立有兩個自訂 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 屬性的按鈕。  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>實作模式提供者  
 如果擁有元素直接從 <xref:System.Windows.Controls.Control>衍生，則會明確宣告自訂提供者所實作為的介面。 例如，下列程式碼會針對執行範圍值的 <xref:System.Windows.Controls.Control> 宣告對等。  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 如果擁有控制項衍生自特定類型的控制項，例如 <xref:System.Windows.Controls.Primitives.RangeBase>，則可以從對等的衍生對等類別衍生對等。 在此情況下，對等會衍生自 <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>，而這會提供 <xref:System.Windows.Automation.Provider.IRangeValueProvider>的基底執行。 下列程式碼顯示這種對等的宣告。  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
如需範例的執行方式， [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)請參閱或[Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)原始程式碼，以執行並使用 NumericUpDown 自訂控制項。  
  
### <a name="raise-events"></a>引發事件  
 自動化用戶端可以訂閱自動化事件。 自訂控制項必須藉由呼叫 <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> 方法，來報告控制狀態的變更。 同樣地，當屬性值變更時，請呼叫 <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> 方法。 下列程式碼示範如何從控制項程式碼內取得對等物件，並呼叫方法以引發事件。 做為最佳化的手段，程式碼會判斷此事件類型是否有任何接聽程式。 只在有接聽程式的情況下引發事件，可以避免不必要的額外負荷並協助保持控制項的反應性。  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>請參閱

- [UI 自動化概觀](../../ui-automation/ui-automation-overview.md)
- [伺服器端 UI 自動化提供者實作](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [在 GitHub 上 NumericUpDownC#自訂控制項（）](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [GitHub 上的 NumericUpDown 自訂控制項（Visual Basic）](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
