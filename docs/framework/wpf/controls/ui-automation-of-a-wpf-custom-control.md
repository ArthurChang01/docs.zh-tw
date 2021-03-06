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
ms.openlocfilehash: 97db94215220ac2a68e0395bd63b7a874a745a48
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243241"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>WPF 自訂控制項的 UI 自動化
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] 提供一個單一的通用介面，可讓自動化用戶端用來檢查或操作各種平台和架構的使用者介面。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 可讓品質保證 (測試) 程式碼和協助工具應用程式 (例如螢幕助讀程式) 檢查使用者介面元素，並模擬從其他程式碼與它們進行的使用者互動。 如需跨所有平台之 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 的相關資訊，請參閱＜協助工具＞。  
  
 本主題說明如何針對在 WPF 應用程式中執行的自訂控制項，實作伺服器端 UI 自動化提供者。 WPF 是透過與使用者介面元素樹狀結構平行的對等自動化物件樹狀結構，來支援 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]。 提供協助工具功能的測試程式碼和應用程式，可以直接使用自動化對等物件 (針對同處理序程式碼)，或透過由 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 提供的一般介面來使用這些物件。  

<a name="AutomationPeerClasses"></a>
## <a name="automation-peer-classes"></a>自動化對等類別  
 WPF[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]通過 派<xref:System.Windows.Automation.Peers.AutomationPeer>生自 的對等類樹控制支援。 依照慣例，對等類別名稱會以控制項類別名稱開始，並以 "AutomationPeer" 結束。 例如,<xref:System.Windows.Automation.Peers.ButtonAutomationPeer>是控件類<xref:System.Windows.Controls.Button>的 對等類。 對等類大致等同於[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]控件類型,但特定於 WPF 元素。 透過 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 介面存取 WPF 應用程式的自動化程式碼並不會直接使用自動化對等，但相同處理序空間中的自動化程式碼則可以直接使用自動化對等。  
  
<a name="BuiltInAutomationPeerClasses"></a>
## <a name="built-in-automation-peer-classes"></a>內建自動化對等類別  
 如果元素接受來自使用者的介面活動，或包含螢幕助讀應用程式使用者所需的資訊，便會實作自動化對等類別。 並非所有 WPF 視覺元素都有自動化對等。 實現自動化對等體的類別範例是<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.Label>。 和 。 不實現自動化對等體的類的範例是從 派生<xref:System.Windows.Controls.Decorator>的類,<xref:System.Windows.Controls.Border><xref:System.Windows.Controls.Panel><xref:System.Windows.Controls.Grid><xref:System.Windows.Controls.Canvas>如  
  
 基<xref:System.Windows.Controls.Control>類沒有相應的對等類。 如果需要對等類來對應於派生自<xref:System.Windows.Controls.Control>的自定義控件,則應<xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>從 派生自定義對等類。  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations-for-derived-peers"></a>衍生對等的安全性考量  
 自動化對等必須在部分信任的環境中執行。 UIAutomationClient 組件中的程式碼並沒有針對在部分信任的環境中執行進行設定，因此自動化對等程式碼不應該參考該組件。 您應該改為使用 UIAutomationTypes 組件中的類別。 例如,應使用 UIAutomationType 程式<xref:System.Windows.Automation.AutomationElementIdentifiers>集中的 類,該程式集對應於 UIAutomationClient 程式集中的<xref:System.Windows.Automation.AutomationElement>類。 在自動化對等程式碼中參考 UIAutomationTypes 組件是安全的。  
  
<a name="PeerNavigation"></a>
## <a name="peer-navigation"></a>對等瀏覽  
 找到自動化對等體后,進程內代碼可以通過調用<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A>物件<xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A>和方法 來導航對等樹。 控制件中的 WPF 元素之間的導航由對等體<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A>的方法實現 提供支援。 UI 自動化系統會呼叫此方法來建置控制項內所包含之子元素的樹狀結構，例如清單方塊中的清單項目。 默認<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType>方法遍歷元素的可視樹以生成自動化對等體的樹。 自訂控制項會覆寫此方法，以將子系元素公開給自動化用戶端，並傳回能傳達資訊或允許使用者互動的元素自動化對等。  
  
<a name="Customizations"></a>
## <a name="customizations-in-a-derived-peer"></a>衍生對等中的自訂  
 派生自<xref:System.Windows.UIElement><xref:System.Windows.ContentElement>並 包含受保護<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>虛擬方法 的所有類。 WPF<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>調用以獲取每個控制件的自動化對等物件。 自動化程式碼可以使用對等來取得控制項特性和功能的相關資訊，並模擬互動式使用。 支援自動化的自定義控制項必須重寫<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>並返回派生<xref:System.Windows.Automation.Peers.AutomationPeer>自的類的實例。 例如,如果自定義控制項派生自<xref:System.Windows.Controls.Primitives.ButtonBase>類,則傳回的<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>物件 應派<xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>生自 。  
  
 實作自訂控制項時，您必須從描述您自訂控制項唯一且特定之行為的基底自動化對等類別，覆寫 "Core" 方法。  
  
### <a name="override-oncreateautomationpeer"></a>覆寫 OnCreateAutomationPeer  
 重寫自訂<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>控制項的方法,以便它傳回提供程式物件,該物件必須直接或間接派<xref:System.Windows.Automation.Peers.AutomationPeer>生自 。  
  
### <a name="override-getpattern"></a>覆寫 GetPattern  
 自動化對等可簡化伺服器端 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 提供者的部分實作層面，但自訂控制項自動化對等仍須處理模式介面。 與非 WPF 提供程式一樣,對等體<xref:System.Windows.Automation.Provider?displayProperty=nameWithType>通過在命名空間<xref:System.Windows.Automation.Provider.IInvokeProvider>(如中)中提供介面的實現來支援控制模式。 控制項模式介面可以由對等本身實作，或是由另一個物件實作。 對等體的實現<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>返回支援指定模式的物件。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]代碼調用<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>方法並<xref:System.Windows.Automation.Peers.PatternInterface>指定 枚舉值。 的重寫<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>應返回實現指定模式的物件。 如果控件沒有模式的自定義實現,則可以調用 基類型的<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>實現 來檢索其實現,如果此控制項類型不支援該模式,則可以調用 其實現。 例如,可以將自定義數位 UpDown 控件設置為範圍內的值,[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]因此其 對等控制<xref:System.Windows.Automation.Provider.IRangeValueProvider>項將實現介面。 下面的示例演示如何重寫對等體<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>的方法以<xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType>回應 值。  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 方法<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>還可以將子元素指定為模式提供程式。 以下代碼顯示如何<xref:System.Windows.Controls.ItemsControl>將滾動模式處理傳輸到其內部<xref:System.Windows.Controls.ScrollViewer>控制 的對等體。  
  
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
  
 要指定模式處理的子元素,此代碼獲取子元素物件,使用<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A>方法創建對等體,將新對等<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>體的屬性設置到當前對等體,並返回新的對等體。 在<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>子元素上設置可防止子元素出現在自動化對等樹中,並將子元素引發的所有事件指定為源自<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>中 指定的控制件。 控制項<xref:System.Windows.Controls.ScrollViewer>不顯示在自動化樹中,並且它產生的捲動事件似乎源自物件<xref:System.Windows.Controls.ItemsControl>。  
  
### <a name="override-core-methods"></a>覆寫 "Core" 方法  
 自動化程式碼會呼叫對等類別的公用方法，來取得控制項的相關資訊。 若要提供您控制項的相關資訊，請在您的控制項實作和由基底自動化對等類別所提供的不同時，覆寫所有名稱以 "Core" 為結尾的方法。 至少,控件必須實現<xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A><xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>和方法,如以下示例所示。  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 的<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>實現通過<xref:System.Windows.Automation.ControlType>返回 值來描述控件。 儘管可以返回<xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>,但如果控件準確描述,則應返回其中一種更具體的控件類型。 返回值<xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>需要 提供程式實現的[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]額外工作[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)],並且客戶端產品無法預測控制結構、鍵盤互動和可能的控制模式。  
  
 實現<xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A>和<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>方法以指示控制項是否包含資料內容或是否在使用者介面(或兩者)中完成互動式角色。 根據預設，這兩個方法皆會傳回 `true`。 這些設定能改善自動化工具 (例如螢幕助讀程式) 的可用性，這些工具可以使用這些方法來篩選自動化樹狀結構。 如果<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>方法將模式處理傳輸到子元素對等體,子元素對等體<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>的方法可以返回 false 以從自動化樹中隱藏子元素對等體。 例如<xref:System.Windows.Controls.ListBox>,在中滾動<xref:System.Windows.Controls.ScrollViewer>由 處理,<xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType>並且的自動化對等體<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>由 與<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>關聯<xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>的方法傳回 。因此,<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>該<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>方法`false`返回<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>,使 不會在自動化樹中出現。  
  
 您的自動化對等應該為您的控制項提供適當的預設值。 請注意,引用控件的 XAML<xref:System.Windows.Automation.AutomationProperties>可以通過包括 屬性來覆蓋核心方法的對等實現。 例如，下列 XAML 會建立有兩個自訂 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 屬性的按鈕。  
  
```xaml  
<Button AutomationProperties.Name="Special"
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>實作模式提供者  
 如果擁有元素直接派生自<xref:System.Windows.Controls.Control>,則顯式聲明由自定義提供程式實現的介面。 例如,以下代碼聲明實現範圍值的<xref:System.Windows.Controls.Control>的對等方。  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 如果所屬控件派生自特定類型的控件(如<xref:System.Windows.Controls.Primitives.RangeBase>,對等體)可以從等效派生的對等類派生。 在這種情況下,對等體將派生自<xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>,後者提供<xref:System.Windows.Automation.Provider.IRangeValueProvider>的基本 實現。 下列程式碼顯示這種對等的宣告。  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
有關實現的範例,請參閱實現和使用數位 UpDown 自訂控制元件的[C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)或[可視化基本](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)原始碼。  
  
### <a name="raise-events"></a>引發事件  
 自動化用戶端可以訂閱自動化事件。 自定義控制項必須透過調用<xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A>方法報告更改以控制狀態。 同樣,當屬性值發生更改時,調用<xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A>方法。 下列程式碼示範如何從控制項程式碼內取得對等物件，並呼叫方法以引發事件。 做為最佳化的手段，程式碼會判斷此事件類型是否有任何接聽程式。 只在有接聽程式的情況下引發事件，可以避免不必要的額外負荷並協助保持控制項的反應性。  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>另請參閱

- [UI 自動化概觀](../../ui-automation/ui-automation-overview.md)
- [伺服器端 UI 自動化提供者實作](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [GitHub 上的數位往上自訂控制件 (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [GitHub 上的數位往上自訂控制元件(視覺基本控制)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
