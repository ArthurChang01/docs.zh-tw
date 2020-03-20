---
title: 內容模型
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187398"
---
# <a name="wpf-content-model"></a><span data-ttu-id="ac13f-102">WPF 內容模型</span><span class="sxs-lookup"><span data-stu-id="ac13f-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="ac13f-103">是展示平台，提供許多以顯示不同類型內容為主要目的的控制項和類控制項類型。</span><span class="sxs-lookup"><span data-stu-id="ac13f-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="ac13f-104">為了判斷要使用哪一種控制項或從哪一種控制項衍生，您應該了解特定控制項顯示哪些物件的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="ac13f-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="ac13f-105">本主題摘要說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項和類控制項類型所適用的內容模型。</span><span class="sxs-lookup"><span data-stu-id="ac13f-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="ac13f-106">內容模型描述控制項中可使用的內容。</span><span class="sxs-lookup"><span data-stu-id="ac13f-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="ac13f-107">本主題同時列出每一個內容模型的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="ac13f-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="ac13f-108">內容屬性是一種用於儲存物件內容的屬性。</span><span class="sxs-lookup"><span data-stu-id="ac13f-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="ac13f-109">包含任意內容的類別</span><span class="sxs-lookup"><span data-stu-id="ac13f-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="ac13f-110">某些控制項可以包含任何類型的物件，例如字串、<xref:System.DateTime>物件或<xref:System.Windows.UIElement>作為其他項的容器的物件。</span><span class="sxs-lookup"><span data-stu-id="ac13f-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="ac13f-111">例如，可以包含<xref:System.Windows.Controls.Button>圖像和某些文本;例如，可以包含圖像和某些文本。或<xref:System.Windows.Controls.CheckBox>可以包含 的值<xref:System.DateTime.Now%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ac13f-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="ac13f-112">有四種可包含任意內容的類別。</span><span class="sxs-lookup"><span data-stu-id="ac13f-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="ac13f-113">下表列出了從 繼承的<xref:System.Windows.Controls.Control>類。</span><span class="sxs-lookup"><span data-stu-id="ac13f-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="ac13f-114">包含任意內容的類別</span><span class="sxs-lookup"><span data-stu-id="ac13f-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="ac13f-115">內容</span><span class="sxs-lookup"><span data-stu-id="ac13f-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="ac13f-116">單一任意物件。</span><span class="sxs-lookup"><span data-stu-id="ac13f-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="ac13f-117">標頭和單一項目，兩者都是任意物件。</span><span class="sxs-lookup"><span data-stu-id="ac13f-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="ac13f-118">任意物件的集合。</span><span class="sxs-lookup"><span data-stu-id="ac13f-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="ac13f-119">標頭和項目集合，這些全部都是任意物件。</span><span class="sxs-lookup"><span data-stu-id="ac13f-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="ac13f-120">繼承自這些類別的控制項可以包含相同類型的內容，並且以相同方式處理內容。</span><span class="sxs-lookup"><span data-stu-id="ac13f-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="ac13f-121">下圖顯示了每個內容模型中包含圖像和某些文本的控制項：</span><span class="sxs-lookup"><span data-stu-id="ac13f-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![顯示四個不同控制項的螢幕截圖，每個內容模型一個。](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="ac13f-123">包含單一任意物件的控制項</span><span class="sxs-lookup"><span data-stu-id="ac13f-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="ac13f-124">該<xref:System.Windows.Controls.ContentControl>類包含一段任意內容。</span><span class="sxs-lookup"><span data-stu-id="ac13f-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="ac13f-125">其內容屬性為<xref:System.Windows.Controls.ContentControl.Content%2A>。</span><span class="sxs-lookup"><span data-stu-id="ac13f-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="ac13f-126">以下控制項繼承<xref:System.Windows.Controls.ContentControl>並使用其內容模型：</span><span class="sxs-lookup"><span data-stu-id="ac13f-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 <span data-ttu-id="ac13f-127"><xref:System.Windows.Controls.ContentControl.Content%2A>下圖顯示了四個按鈕，其設置為字串、<xref:System.DateTime>物件、和<xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Panel> ， 包含 和<xref:System.Windows.Shapes.Ellipse>： <xref:System.Windows.Controls.TextBlock></span><span class="sxs-lookup"><span data-stu-id="ac13f-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![顯示四個不同內容類型的按鈕的螢幕截圖。](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="ac13f-129">有關如何設置<xref:System.Windows.Controls.ContentControl.Content%2A>屬性的示例，請參閱<xref:System.Windows.Controls.ContentControl>。</span><span class="sxs-lookup"><span data-stu-id="ac13f-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="ac13f-130">包含標頭和單一任意物件的控制項</span><span class="sxs-lookup"><span data-stu-id="ac13f-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="ac13f-131">類<xref:System.Windows.Controls.HeaderedContentControl>繼承<xref:System.Windows.Controls.ContentControl>並顯示具有標頭的內容。</span><span class="sxs-lookup"><span data-stu-id="ac13f-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="ac13f-132">它繼承<xref:System.Windows.Controls.ContentControl.Content%2A>內容屬性 ， 和<xref:System.Windows.Controls.ContentControl>定義<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>類型<xref:System.Object>的屬性 ;因此，兩者都可以是任意物件。</span><span class="sxs-lookup"><span data-stu-id="ac13f-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="ac13f-133">以下控制項繼承<xref:System.Windows.Controls.HeaderedContentControl>並使用其內容模型：</span><span class="sxs-lookup"><span data-stu-id="ac13f-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="ac13f-134">下圖顯示了兩<xref:System.Windows.Controls.TabItem>個物件。</span><span class="sxs-lookup"><span data-stu-id="ac13f-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="ac13f-135">第一<xref:System.Windows.Controls.TabItem>個<xref:System.Windows.UIElement>物件為<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和<xref:System.Windows.Controls.ContentControl.Content%2A>。</span><span class="sxs-lookup"><span data-stu-id="ac13f-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="ac13f-136"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A>設置為<xref:System.Windows.Controls.StackPanel>包含 和<xref:System.Windows.Shapes.Ellipse>的 。 <xref:System.Windows.Controls.TextBlock></span><span class="sxs-lookup"><span data-stu-id="ac13f-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="ac13f-137"><xref:System.Windows.Controls.ContentControl.Content%2A>設置為<xref:System.Windows.Controls.StackPanel>包含 和<xref:System.Windows.Controls.TextBlock>的 。 <xref:System.Windows.Controls.Label></span><span class="sxs-lookup"><span data-stu-id="ac13f-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="ac13f-138">第二<xref:System.Windows.Controls.TabItem>個在 和<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>中有<xref:System.Windows.Controls.TextBlock>一個<xref:System.Windows.Controls.ContentControl.Content%2A>字串。</span><span class="sxs-lookup"><span data-stu-id="ac13f-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![在"標頭"屬性中使用不同類型的 TabControl。](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="ac13f-140">有關如何創建<xref:System.Windows.Controls.TabItem>物件的示例，請參閱<xref:System.Windows.Controls.HeaderedContentControl>。</span><span class="sxs-lookup"><span data-stu-id="ac13f-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="ac13f-141">包含任意物件集合的控制項</span><span class="sxs-lookup"><span data-stu-id="ac13f-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="ac13f-142">類<xref:System.Windows.Controls.ItemsControl>繼承 from<xref:System.Windows.Controls.Control>可以包含多個項，如字串、物件或其他元素。</span><span class="sxs-lookup"><span data-stu-id="ac13f-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="ac13f-143">其內容屬性為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>和<xref:System.Windows.Controls.ItemsControl.Items%2A>。</span><span class="sxs-lookup"><span data-stu-id="ac13f-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="ac13f-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>通常用於使用資料收集填充 。 <xref:System.Windows.Controls.ItemsControl></span><span class="sxs-lookup"><span data-stu-id="ac13f-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="ac13f-145">如果不想使用集合填充 ，<xref:System.Windows.Controls.ItemsControl>則可以使用 屬性<xref:System.Windows.Controls.ItemsControl.Items%2A>添加項。</span><span class="sxs-lookup"><span data-stu-id="ac13f-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="ac13f-146">以下控制項繼承<xref:System.Windows.Controls.ItemsControl>並使用其內容模型：</span><span class="sxs-lookup"><span data-stu-id="ac13f-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="ac13f-147">下圖顯示了包含這些類型的項<xref:System.Windows.Controls.ListBox>的 圖所示：</span><span class="sxs-lookup"><span data-stu-id="ac13f-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="ac13f-148">字串。</span><span class="sxs-lookup"><span data-stu-id="ac13f-148">A string.</span></span>  
  
- <span data-ttu-id="ac13f-149"><xref:System.DateTime> 物件。</span><span class="sxs-lookup"><span data-stu-id="ac13f-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="ac13f-150"><xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="ac13f-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="ac13f-151">包含<xref:System.Windows.Controls.Panel>和<xref:System.Windows.Shapes.Ellipse>的 A。 <xref:System.Windows.Controls.TextBlock></span><span class="sxs-lookup"><span data-stu-id="ac13f-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![顯示包含四種類型的內容的 ListBox 的螢幕截圖。](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="ac13f-153">包含標頭和任意物件集合的控制項</span><span class="sxs-lookup"><span data-stu-id="ac13f-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="ac13f-154">類<xref:System.Windows.Controls.HeaderedItemsControl>繼承和<xref:System.Windows.Controls.ItemsControl>可以包含多個項，如字串、物件或其他元素以及標頭。</span><span class="sxs-lookup"><span data-stu-id="ac13f-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="ac13f-155">它繼承<xref:System.Windows.Controls.ItemsControl>內容屬性<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>和<xref:System.Windows.Controls.ItemsControl.Items%2A>，並定義可以是任意物件<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>的屬性。</span><span class="sxs-lookup"><span data-stu-id="ac13f-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="ac13f-156">以下控制項繼承<xref:System.Windows.Controls.HeaderedItemsControl>並使用其內容模型：</span><span class="sxs-lookup"><span data-stu-id="ac13f-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="ac13f-157">包含 UIElement 物件集合的類別</span><span class="sxs-lookup"><span data-stu-id="ac13f-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="ac13f-158">類<xref:System.Windows.Controls.Panel>位置並排列子<xref:System.Windows.UIElement>物件。</span><span class="sxs-lookup"><span data-stu-id="ac13f-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="ac13f-159">其內容屬性為<xref:System.Windows.Controls.Panel.Children%2A>。</span><span class="sxs-lookup"><span data-stu-id="ac13f-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="ac13f-160">以下類從<xref:System.Windows.Controls.Panel>類繼承並使用其內容模型：</span><span class="sxs-lookup"><span data-stu-id="ac13f-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="ac13f-161">如需詳細資訊，請參閱[面板概觀](panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ac13f-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="ac13f-162">影響 UIElement 外觀的類別</span><span class="sxs-lookup"><span data-stu-id="ac13f-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="ac13f-163">該<xref:System.Windows.Controls.Decorator>類對單個子項<xref:System.Windows.UIElement>或周圍應用視覺效果。</span><span class="sxs-lookup"><span data-stu-id="ac13f-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="ac13f-164">其內容屬性為<xref:System.Windows.Controls.Decorator.Child%2A>。</span><span class="sxs-lookup"><span data-stu-id="ac13f-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="ac13f-165">以下類繼承<xref:System.Windows.Controls.Decorator>並使用其內容模型：</span><span class="sxs-lookup"><span data-stu-id="ac13f-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="ac13f-166">下圖顯示了一個<xref:System.Windows.Controls.TextBox>（用）其周圍裝飾<xref:System.Windows.Controls.Border>的。</span><span class="sxs-lookup"><span data-stu-id="ac13f-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="ac13f-167">![具有黑色框線的 TextBox](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="ac13f-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="ac13f-168">具有框線的 TextBlock</span><span class="sxs-lookup"><span data-stu-id="ac13f-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="ac13f-169">提供 UIElement 相關視覺化回應的類別</span><span class="sxs-lookup"><span data-stu-id="ac13f-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="ac13f-170">類<xref:System.Windows.Documents.Adorner>向使用者提供可視提示。</span><span class="sxs-lookup"><span data-stu-id="ac13f-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="ac13f-171">例如，使用<xref:System.Windows.Documents.Adorner>將函數控制碼添加到元素或提供有關控制項的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="ac13f-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="ac13f-172">該<xref:System.Windows.Documents.Adorner>類提供了一個框架，以便您可以創建自己的修飾器。</span><span class="sxs-lookup"><span data-stu-id="ac13f-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="ac13f-173">不會提供任何已實作的裝飾項。</span><span class="sxs-lookup"><span data-stu-id="ac13f-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="ac13f-174">如需詳細資訊，請參閱[裝飾項概觀](adorners-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ac13f-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="ac13f-175">可讓使用者輸入文字的類別</span><span class="sxs-lookup"><span data-stu-id="ac13f-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="ac13f-176">WPF 提供三種可讓使用者輸入文字的主要控制項。</span><span class="sxs-lookup"><span data-stu-id="ac13f-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="ac13f-177">每一個控制項都會以不同方式顯示文字。</span><span class="sxs-lookup"><span data-stu-id="ac13f-177">Each control displays the text differently.</span></span> <span data-ttu-id="ac13f-178">下表列出這三個文字相關控制項、它們顯示文字時的功能，以及其包含控制項文字的屬性。</span><span class="sxs-lookup"><span data-stu-id="ac13f-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="ac13f-179">控制</span><span class="sxs-lookup"><span data-stu-id="ac13f-179">Control</span></span>|<span data-ttu-id="ac13f-180">文字顯示為</span><span class="sxs-lookup"><span data-stu-id="ac13f-180">Text is displayed as</span></span>|<span data-ttu-id="ac13f-181">內容屬性</span><span class="sxs-lookup"><span data-stu-id="ac13f-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="ac13f-182">純文字</span><span class="sxs-lookup"><span data-stu-id="ac13f-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="ac13f-183">格式化文字</span><span class="sxs-lookup"><span data-stu-id="ac13f-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="ac13f-184">隱藏文字 (字元會加上遮罩)</span><span class="sxs-lookup"><span data-stu-id="ac13f-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a><span data-ttu-id="ac13f-185">顯示文字的類別</span><span class="sxs-lookup"><span data-stu-id="ac13f-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="ac13f-186">有數種類別可用來顯示純文字或格式化文字。</span><span class="sxs-lookup"><span data-stu-id="ac13f-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="ac13f-187">您可以使用<xref:System.Windows.Controls.TextBlock>來顯示少量的文本。</span><span class="sxs-lookup"><span data-stu-id="ac13f-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="ac13f-188">如果要顯示大量文本，請使用 。 <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer></span><span class="sxs-lookup"><span data-stu-id="ac13f-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="ac13f-189">具有<xref:System.Windows.Controls.TextBlock>兩個內容屬性： <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock.Inlines%2A>和 。</span><span class="sxs-lookup"><span data-stu-id="ac13f-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="ac13f-190">當您要顯示使用一致格式的文本時，該<xref:System.Windows.Controls.TextBlock.Text%2A>屬性通常是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="ac13f-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="ac13f-191">如果計畫在整個文本中使用不同的格式，請使用 該<xref:System.Windows.Controls.TextBlock.Inlines%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ac13f-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="ac13f-192">該<xref:System.Windows.Controls.TextBlock.Inlines%2A>屬性是<xref:System.Windows.Documents.Inline>物件的集合，它指定如何設置文本的格式。</span><span class="sxs-lookup"><span data-stu-id="ac13f-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="ac13f-193">下表列出了<xref:System.Windows.Controls.FlowDocumentReader>和<xref:System.Windows.Controls.FlowDocumentPageViewer><xref:System.Windows.Controls.FlowDocumentScrollViewer>類的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="ac13f-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="ac13f-194">控制</span><span class="sxs-lookup"><span data-stu-id="ac13f-194">Control</span></span>|<span data-ttu-id="ac13f-195">內容屬性</span><span class="sxs-lookup"><span data-stu-id="ac13f-195">Content property</span></span>|<span data-ttu-id="ac13f-196">內容屬性類型</span><span class="sxs-lookup"><span data-stu-id="ac13f-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="ac13f-197">Document</span><span class="sxs-lookup"><span data-stu-id="ac13f-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="ac13f-198">Document</span><span class="sxs-lookup"><span data-stu-id="ac13f-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="ac13f-199">Document</span><span class="sxs-lookup"><span data-stu-id="ac13f-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="ac13f-200">實現<xref:System.Windows.Documents.FlowDocument><xref:System.Windows.Documents.IDocumentPaginatorSource>介面;因此，所有三個類都可以以<xref:System.Windows.Documents.FlowDocument>作為內容。</span><span class="sxs-lookup"><span data-stu-id="ac13f-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a><span data-ttu-id="ac13f-201">格式化文字的類別</span><span class="sxs-lookup"><span data-stu-id="ac13f-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="ac13f-202"><xref:System.Windows.Documents.TextElement>及其相關類允許您設置文本格式。</span><span class="sxs-lookup"><span data-stu-id="ac13f-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="ac13f-203"><xref:System.Windows.Documents.TextElement>物件在 和 中<xref:System.Windows.Controls.TextBlock>包含<xref:System.Windows.Documents.FlowDocument>和設置文本的格式。</span><span class="sxs-lookup"><span data-stu-id="ac13f-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="ac13f-204">物件的兩種主要類型<xref:System.Windows.Documents.TextElement>是<xref:System.Windows.Documents.Block>元素和<xref:System.Windows.Documents.Inline>元素。</span><span class="sxs-lookup"><span data-stu-id="ac13f-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="ac13f-205">元素<xref:System.Windows.Documents.Block>表示文字區塊，如段落或清單。</span><span class="sxs-lookup"><span data-stu-id="ac13f-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="ac13f-206">元素<xref:System.Windows.Documents.Inline>表示塊中文本的一部分。</span><span class="sxs-lookup"><span data-stu-id="ac13f-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="ac13f-207">許多<xref:System.Windows.Documents.Inline>類指定應用它們的文本的格式。</span><span class="sxs-lookup"><span data-stu-id="ac13f-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="ac13f-208">每個<xref:System.Windows.Documents.TextElement>都有自己的內容模型。</span><span class="sxs-lookup"><span data-stu-id="ac13f-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="ac13f-209">如需詳細資訊，請參閱 [TextElement 內容模型概觀](../advanced/textelement-content-model-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ac13f-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac13f-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac13f-210">See also</span></span>

- [<span data-ttu-id="ac13f-211">進階</span><span class="sxs-lookup"><span data-stu-id="ac13f-211">Advanced</span></span>](../advanced/index.md)
