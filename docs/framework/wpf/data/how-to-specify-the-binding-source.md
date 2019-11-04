---
title: 操作說明：指定繫結來源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 4fde66b22bac6b4a2cfeb4eceb50027daadee387
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454362"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="c8c05-102">操作說明：指定繫結來源</span><span class="sxs-lookup"><span data-stu-id="c8c05-102">How to: Specify the Binding Source</span></span>
<span data-ttu-id="c8c05-103">在資料繫結中，繫結來源物件是指您的資料取得來源物件。</span><span class="sxs-lookup"><span data-stu-id="c8c05-103">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="c8c05-104">本主題說明指定繫結來源的不同方式。</span><span class="sxs-lookup"><span data-stu-id="c8c05-104">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8c05-105">範例</span><span class="sxs-lookup"><span data-stu-id="c8c05-105">Example</span></span>  
 <span data-ttu-id="c8c05-106">如果您將數個屬性繫結至同一個來源，要使用 `DataContext` 屬性，它是建立範圍的便利方式，在這個範圍中所有資料繫結屬性都繼承同一個來源。</span><span class="sxs-lookup"><span data-stu-id="c8c05-106">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="c8c05-107">下列範例會在應用程式的根元素建立資料內容。</span><span class="sxs-lookup"><span data-stu-id="c8c05-107">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="c8c05-108">這會使所有子元素都繼承這個資料內容。</span><span class="sxs-lookup"><span data-stu-id="c8c05-108">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="c8c05-109">繫結的資料來自自訂的資料類別 `NetIncome`，這個類別是直接透過對應來參考，並且具有資源索引鍵 `incomeDataSource`。</span><span class="sxs-lookup"><span data-stu-id="c8c05-109">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="c8c05-110">下列範例顯示 `NetIncome` 類別的定義。</span><span class="sxs-lookup"><span data-stu-id="c8c05-110">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> <span data-ttu-id="c8c05-111">上述範例將標記中的物件具現化，並當做資源使用。</span><span class="sxs-lookup"><span data-stu-id="c8c05-111">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="c8c05-112">如果您想繫結至已在程式碼中具現化的物件，必須以程式設計的方式設定 `DataContext` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c8c05-112">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="c8c05-113">如需範例，請參閱[讓資料可於 XAML 中繫結](how-to-make-data-available-for-binding-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="c8c05-113">For an example, see [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="c8c05-114">或者，如果您想明確指定個別繫結的來源，則有以下選擇。</span><span class="sxs-lookup"><span data-stu-id="c8c05-114">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="c8c05-115">這些屬性優先於繼承的資料內容。</span><span class="sxs-lookup"><span data-stu-id="c8c05-115">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="c8c05-116">屬性</span><span class="sxs-lookup"><span data-stu-id="c8c05-116">Property</span></span>|<span data-ttu-id="c8c05-117">描述</span><span class="sxs-lookup"><span data-stu-id="c8c05-117">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="c8c05-118">使用這個屬性將來源設定為物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c8c05-118">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="c8c05-119">如果您不需要建立範圍的功能，其中有數個屬性會繼承相同的資料內容，您可以使用 [<xref:System.Windows.Data.Binding.Source%2A>] 屬性，而不是 [`DataContext`] 屬性。</span><span class="sxs-lookup"><span data-stu-id="c8c05-119">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="c8c05-120">如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.Source%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8c05-120">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="c8c05-121">當您想以相對於繫結目標的位置指定來源，這十分有用。</span><span class="sxs-lookup"><span data-stu-id="c8c05-121">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="c8c05-122">使用這個屬性的常見案例是，當您想將元素的一個屬性繫結至同一元素的其他屬性時，或當您正在樣式或範本中定義繫結時。</span><span class="sxs-lookup"><span data-stu-id="c8c05-122">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="c8c05-123">如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.RelativeSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8c05-123">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="c8c05-124">指定一個字串來代表您想繫結至的元素。</span><span class="sxs-lookup"><span data-stu-id="c8c05-124">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="c8c05-125">當您想要繫結至應用程式中其他元素的屬性時，這十分有用。</span><span class="sxs-lookup"><span data-stu-id="c8c05-125">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="c8c05-126">例如，如果您想要使用 <xref:System.Windows.Controls.Slider> 來控制應用程式中另一個控制項的高度，或想要將控制項的 <xref:System.Windows.Controls.ContentControl.Content%2A> 系結至 <xref:System.Windows.Controls.ListBox> 控制項的 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="c8c05-126">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="c8c05-127">如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.ElementName%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8c05-127">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8c05-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8c05-128">See also</span></span>

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c8c05-129">屬性值繼承</span><span class="sxs-lookup"><span data-stu-id="c8c05-129">Property Value Inheritance</span></span>](../advanced/property-value-inheritance.md)
- [<span data-ttu-id="c8c05-130">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="c8c05-130">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c8c05-131">繫結宣告概觀</span><span class="sxs-lookup"><span data-stu-id="c8c05-131">Binding Declarations Overview</span></span>](binding-declarations-overview.md)
- [<span data-ttu-id="c8c05-132">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="c8c05-132">How-to Topics</span></span>](data-binding-how-to-topics.md)
