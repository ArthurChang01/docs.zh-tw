---
title: 將玻璃框架擴充至 WPF 應用程式
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
ms.openlocfilehash: b78547aa8b414c585bb2e5c9c6680ed159731bc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746539"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="6946c-102">將玻璃框架擴充至 WPF 應用程式中</span><span class="sxs-lookup"><span data-stu-id="6946c-102">Extend Glass Frame Into a WPF Application</span></span>

<span data-ttu-id="6946c-103">本主題示範如何將 Windows Vista 玻璃框架擴充到 Windows Presentation Foundation （WPF）應用程式的工作區中。</span><span class="sxs-lookup"><span data-stu-id="6946c-103">This topic demonstrates how to extend the Windows Vista glass frame into the client area of a Windows Presentation Foundation (WPF) application.</span></span>

> [!NOTE]
> <span data-ttu-id="6946c-104">這個範例只適用于執行桌面視窗管理員（DWM）並已啟用玻璃的 Windows Vista 電腦。</span><span class="sxs-lookup"><span data-stu-id="6946c-104">This example will only work on a Windows Vista machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> <span data-ttu-id="6946c-105">Windows Vista Home Basic edition 並不支援透明玻璃效果。</span><span class="sxs-lookup"><span data-stu-id="6946c-105">Windows Vista Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="6946c-106">在其他版本的 Windows Vista 上，通常會以透明玻璃效果轉譯的區域會呈現不透明。</span><span class="sxs-lookup"><span data-stu-id="6946c-106">Areas that would typically render with the transparent glass effect on other editions of Windows Vista are rendered opaque.</span></span>

## <a name="example"></a><span data-ttu-id="6946c-107">範例</span><span class="sxs-lookup"><span data-stu-id="6946c-107">Example</span></span>

<span data-ttu-id="6946c-108">下圖說明延伸到 Internet Explorer 7 網址列的玻璃框架：</span><span class="sxs-lookup"><span data-stu-id="6946c-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7:</span></span>

![螢幕擷取畫面，顯示在 IE7 網址列後方擴充的玻璃框架。](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

<span data-ttu-id="6946c-110">若要擴充 WPF 應用程式上的玻璃框架，需要存取非受控 API。</span><span class="sxs-lookup"><span data-stu-id="6946c-110">To extend the glass frame on a WPF application, access to unmanaged API is needed.</span></span> <span data-ttu-id="6946c-111">下列程式碼範例會針對將框架擴充到工作區所需的兩個 API，執行平台叫用（pinvoke）。</span><span class="sxs-lookup"><span data-stu-id="6946c-111">The following code example does a Platform Invoke (pinvoke) for the two API needed to extend the frame into the client area.</span></span> <span data-ttu-id="6946c-112">這些 API 中的每一個都是在名為**NonClientRegionAPI**的類別中宣告。</span><span class="sxs-lookup"><span data-stu-id="6946c-112">Each of these API are declared in a class called **NonClientRegionAPI**.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential)]
public struct MARGINS
{
    public int cxLeftWidth;      // width of left border that retains its size
    public int cxRightWidth;     // width of right border that retains its size
    public int cyTopHeight;      // height of top border that retains its size
    public int cyBottomHeight;   // height of bottom border that retains its size
};

[DllImport("DwmApi.dll")]
public static extern int DwmExtendFrameIntoClientArea(
    IntPtr hwnd,
    ref MARGINS pMarInset);
```

```vb
<StructLayout(LayoutKind.Sequential)>
Public Structure MARGINS
    Public cxLeftWidth As Integer ' width of left border that retains its size
    Public cxRightWidth As Integer ' width of right border that retains its size
    Public cyTopHeight As Integer ' height of top border that retains its size
    Public cyBottomHeight As Integer ' height of bottom border that retains its size
End Structure

<DllImport("DwmApi.dll")>
Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer
End Function
```

<span data-ttu-id="6946c-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) 是會將框架擴充至工作區的 DWM 函式。</span><span class="sxs-lookup"><span data-stu-id="6946c-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="6946c-114">它接受兩個參數：視窗控制代碼和 [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) 結構。</span><span class="sxs-lookup"><span data-stu-id="6946c-114">It takes two parameters; a window handle and a [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) structure.</span></span> <span data-ttu-id="6946c-115">[MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) 是用來告知 DWM 應該額外將多少框架擴充至工作區。</span><span class="sxs-lookup"><span data-stu-id="6946c-115">[MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>

## <a name="example"></a><span data-ttu-id="6946c-116">範例</span><span class="sxs-lookup"><span data-stu-id="6946c-116">Example</span></span>

<span data-ttu-id="6946c-117">若要使用 [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) 函式，必須取得視窗控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6946c-117">To use the [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) function, a window handle must be obtained.</span></span> <span data-ttu-id="6946c-118">在 WPF 中，您可以從 <xref:System.Windows.Interop.HwndSource>的 <xref:System.Windows.Interop.HwndSource.Handle%2A> 屬性取得視窗控制碼。</span><span class="sxs-lookup"><span data-stu-id="6946c-118">In WPF, the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="6946c-119">在下列範例中，畫面格會延伸到視窗之 <xref:System.Windows.FrameworkElement.Loaded> 事件的工作區中。</span><span class="sxs-lookup"><span data-stu-id="6946c-119">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>

```csharp
void OnLoaded(object sender, RoutedEventArgs e)
{
   try
   {
      // Obtain the window handle for WPF application
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);

      // Get System Dpi
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);
      float DesktopDpiX = desktop.DpiX;
      float DesktopDpiY = desktop.DpiY;

      // Set Margins
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();

      // Extend glass frame into client area
      // Note that the default desktop Dpi is 96dpi. The  margins are
      // adjusted for the system Dpi.
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));

      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);
      //
      if (hr < 0)
      {
         //DwmExtendFrameIntoClientArea Failed
      }
   }
   // If not Vista, paint background white.
   catch (DllNotFoundException)
   {
      Application.Current.MainWindow.Background = Brushes.White;
   }
}
```

## <a name="example"></a><span data-ttu-id="6946c-120">範例</span><span class="sxs-lookup"><span data-stu-id="6946c-120">Example</span></span>

<span data-ttu-id="6946c-121">下列範例示範將框架擴充至工作區的簡單視窗。</span><span class="sxs-lookup"><span data-stu-id="6946c-121">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="6946c-122">畫面格會延伸到包含兩個 <xref:System.Windows.Controls.TextBox> 物件的上框線後面。</span><span class="sxs-lookup"><span data-stu-id="6946c-122">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>

```xaml
<Window x:Class="SDKSample.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Extended Glass in WPF" Height="300" Width="400"
    Loaded="OnLoaded" Background="Transparent"
    >
  <Grid ShowGridLines="True">
    <DockPanel Name="mainDock">
      <!-- The border is used to compute the rendered height with margins.
           topBar contents will be displayed on the extended glass frame.-->
      <Border Name="topBar" DockPanel.Dock="Top" >
        <Grid Name="grid">
          <Grid.ColumnDefinitions>
            <ColumnDefinition MinWidth="100" Width="*"/>
            <ColumnDefinition Width="Auto"/>
          </Grid.ColumnDefinitions>
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>
        </Grid>
      </Border>
      <Grid DockPanel.Dock="Top" >
        <Grid.ColumnDefinitions>
          <ColumnDefinition/>
        </Grid.ColumnDefinitions>
        <TextBox Grid.Column="0" AcceptsReturn="True"/>
      </Grid>
    </DockPanel>
  </Grid>
</Window>
```

<span data-ttu-id="6946c-123">下圖說明擴充至 WPF 應用程式的玻璃框架：</span><span class="sxs-lookup"><span data-stu-id="6946c-123">The following image illustrates the glass frame extended into a WPF application:</span></span>

![螢幕擷取畫面：顯示擴充至 WPF 應用程式的玻璃框架。](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a><span data-ttu-id="6946c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6946c-125">See also</span></span>

- [<span data-ttu-id="6946c-126">桌面視窗管理員總覽</span><span class="sxs-lookup"><span data-stu-id="6946c-126">Desktop Window Manager Overview</span></span>](/windows/desktop/dwm/dwm-overview)
- [<span data-ttu-id="6946c-127">桌面視窗管理員模糊總覽</span><span class="sxs-lookup"><span data-stu-id="6946c-127">Desktop Window Manager Blur Overview</span></span>](/windows/desktop/dwm/blur-ovw)
- [<span data-ttu-id="6946c-128">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="6946c-128">DwmExtendFrameIntoClientArea</span></span>](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
