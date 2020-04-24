---
title: 演練:樣式 WPF 內容
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07241d41e3fbf270a76bd241765bfa369ee265d5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646322"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="19150-102">演練:樣式 WPF 內容</span><span class="sxs-lookup"><span data-stu-id="19150-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="19150-103">本文介紹如何將樣式應用於 Windows 窗體上託管的 Windows 演示文稿基礎 (WPF) 控制項。</span><span class="sxs-lookup"><span data-stu-id="19150-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="19150-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="19150-104">Prerequisites</span></span>

<span data-ttu-id="19150-105">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="19150-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="19150-106">建立專案</span><span class="sxs-lookup"><span data-stu-id="19150-106">Create the project</span></span>

<span data-ttu-id="19150-107">打開視覺化工作室,並在名為`StylingWpfContent`的「視覺基本」或「視覺 C#」中創建新的 Windows 窗體應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="19150-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="19150-108">裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="19150-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="19150-109">建立 WPF 控制項型態</span><span class="sxs-lookup"><span data-stu-id="19150-109">Create the WPF control types</span></span>

<span data-ttu-id="19150-110">在將 WPF 控制項加入專案後，即可將它裝載至 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。</span><span class="sxs-lookup"><span data-stu-id="19150-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="19150-111">將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="19150-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="19150-112">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="19150-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="19150-113">有關詳細資訊,請參閱[演練:在設計時間在 Windows 窗體上建立新的 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="19150-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="19150-114">在 [設計] 檢視中，確定已選取 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="19150-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="19150-115">在 **「屬性」** 視窗中,<xref:System.Windows.FrameworkElement.Width%2A><xref:System.Windows.FrameworkElement.Height%2A>將與屬性的值設定為**200**。</span><span class="sxs-lookup"><span data-stu-id="19150-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="19150-116">將<xref:System.Windows.Controls.Button?displayProperty=nameWithType>控制項加入,<xref:System.Windows.Controls.UserControl><xref:System.Windows.Controls.ContentControl.Content%2A>並將屬性的值設定為 **"取消**" 。</span><span class="sxs-lookup"><span data-stu-id="19150-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="19150-117">將第二<xref:System.Windows.Controls.Button?displayProperty=nameWithType>個控制項添加<xref:System.Windows.Controls.UserControl>到<xref:System.Windows.Controls.ContentControl.Content%2A>,並將屬性的值設置為 **"確定**"</span><span class="sxs-lookup"><span data-stu-id="19150-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="19150-118">建置專案。</span><span class="sxs-lookup"><span data-stu-id="19150-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="19150-119">將樣式應用於 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="19150-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="19150-120">您可以套用不同的樣式至 WPF 控制項，以變更其外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="19150-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="19150-121">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="19150-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="19150-122">在**工具箱**中,按`UserControl1`兩下 以在窗`UserControl1`體上創建的實例。</span><span class="sxs-lookup"><span data-stu-id="19150-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="19150-123">`UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="19150-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="19150-124">在`elementHost1`的智慧標記面板中,按一下拉清單中**的「編輯託管內容**」 。。</span><span class="sxs-lookup"><span data-stu-id="19150-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="19150-125">`UserControl1`在 WPF 設計器中打開。</span><span class="sxs-lookup"><span data-stu-id="19150-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="19150-126">在 [XAML] 檢閱中，插入下列 XAML 到 `<UserControl>` 開頭標記後面。</span><span class="sxs-lookup"><span data-stu-id="19150-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="19150-127">此 XAML 會建立具有對比漸層框線的漸層。</span><span class="sxs-lookup"><span data-stu-id="19150-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="19150-128">按一下控制項時，漸層會變更，產生已按下的按鈕外觀。</span><span class="sxs-lookup"><span data-stu-id="19150-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="19150-129">有關詳細資訊,請參閱[樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)化。</span><span class="sxs-lookup"><span data-stu-id="19150-129">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

1. <span data-ttu-id="19150-130">通過在「`SimpleButton`取消」`<Button>`按鈕的標記中插入以下 XAML,將上一步中定義的樣式應用於「**取消」** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="19150-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="19150-131">您的按鈕宣告類似於以下 XAML:</span><span class="sxs-lookup"><span data-stu-id="19150-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="19150-132">建置專案。</span><span class="sxs-lookup"><span data-stu-id="19150-132">Build the project.</span></span>

1. <span data-ttu-id="19150-133">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="19150-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="19150-134">新的樣式會套用至按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="19150-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="19150-135">在 **「調試」** 選單中,選擇 **「開始除錯」** 以執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="19150-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="19150-136">按下「**確定\*\*\*\*」 與「取消」** 按鈕並查看差異。</span><span class="sxs-lookup"><span data-stu-id="19150-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="19150-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19150-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="19150-138">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="19150-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="19150-139">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="19150-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="19150-140">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="19150-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="19150-141">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="19150-141">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="19150-142">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="19150-142">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
