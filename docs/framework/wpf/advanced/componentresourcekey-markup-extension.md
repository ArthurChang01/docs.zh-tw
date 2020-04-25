---
title: ComponentResourceKey 標記延伸
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: f86b7000b97bbc1287347947a9244c24a7de74c2
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141130"
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="8cb32-102">ComponentResourceKey 標記延伸</span><span class="sxs-lookup"><span data-stu-id="8cb32-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="8cb32-103">定義和參考從外部元件載入之資源的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8cb32-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="8cb32-104">這可讓資源查閱指定元件中的目標型別，而不是元件或類別上的明確資源字典。</span><span class="sxs-lookup"><span data-stu-id="8cb32-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="8cb32-105">XAML 屬性使用方式（設定金鑰、壓縮）</span><span class="sxs-lookup"><span data-stu-id="8cb32-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" ... />  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="8cb32-106">XAML 屬性使用方式（設定索引鍵，詳細資訊）</span><span class="sxs-lookup"><span data-stu-id="8cb32-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" ... />  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="8cb32-107">XAML 屬性使用方式（要求資源，compact）</span><span class="sxs-lookup"><span data-stu-id="8cb32-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" ... />  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="8cb32-108">XAML 屬性使用方式（要求資源，詳細資訊）</span><span class="sxs-lookup"><span data-stu-id="8cb32-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" ... />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8cb32-109">XAML 值</span><span class="sxs-lookup"><span data-stu-id="8cb32-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="8cb32-110">在資源元件中定義的公用 common language runtime （CLR）類型名稱。</span><span class="sxs-lookup"><span data-stu-id="8cb32-110">The name of the public common language runtime (CLR) type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="8cb32-111">資源的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8cb32-111">The key for the resource.</span></span> <span data-ttu-id="8cb32-112">查閱資源時， `targetID`會類似于資源的[x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="8cb32-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cb32-113">備註</span><span class="sxs-lookup"><span data-stu-id="8cb32-113">Remarks</span></span>  
 <span data-ttu-id="8cb32-114">如上所述，{`ComponentResourceKey`} 標記延伸使用方式可在兩個地方找到：</span><span class="sxs-lookup"><span data-stu-id="8cb32-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
- <span data-ttu-id="8cb32-115">主題資源字典中的索引鍵定義，如同控制項作者所提供。</span><span class="sxs-lookup"><span data-stu-id="8cb32-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
- <span data-ttu-id="8cb32-116">當您重新範本化控制項，但想要使用來自控制項主題所提供之資源的屬性值時，從元件存取主題資源。</span><span class="sxs-lookup"><span data-stu-id="8cb32-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="8cb32-117">若要參考來自主題的元件資源，通常建議您使用`{DynamicResource}`而不是。 `{StaticResource}`</span><span class="sxs-lookup"><span data-stu-id="8cb32-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="8cb32-118">這會顯示在使用方式中。</span><span class="sxs-lookup"><span data-stu-id="8cb32-118">This is shown in the usages.</span></span> <span data-ttu-id="8cb32-119">`{DynamicResource}`建議使用，因為使用者可以變更主題本身。</span><span class="sxs-lookup"><span data-stu-id="8cb32-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="8cb32-120">如果您想要讓元件資源最符合控制項作者的意圖來支援主題，您應該讓元件資源參考也是動態的。</span><span class="sxs-lookup"><span data-stu-id="8cb32-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="8cb32-121">會<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>識別存在於實際定義資源之目標群組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="8cb32-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="8cb32-122">`ComponentResourceKey`可以單獨定義和使用，而不需要確切瞭解定義<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>的位置，但最終必須透過參考的元件來解析類型。</span><span class="sxs-lookup"><span data-stu-id="8cb32-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="8cb32-123">的常見用法<xref:System.Windows.ComponentResourceKey>是定義接著公開為類別成員的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8cb32-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="8cb32-124">在這種情況下，您<xref:System.Windows.ComponentResourceKey>可以使用類別的「函式」，而不是標記延伸。</span><span class="sxs-lookup"><span data-stu-id="8cb32-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="8cb32-125">如需詳細資訊， <xref:System.Windows.ComponentResourceKey>請參閱或主題[控制項撰寫總覽](../controls/control-authoring-overview.md)的「定義和參考主題資源的索引鍵」一節。</span><span class="sxs-lookup"><span data-stu-id="8cb32-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="8cb32-126">對於建立金鑰和參考索引鍵，屬性語法通常用於`ComponentResourceKey`標記延伸。</span><span class="sxs-lookup"><span data-stu-id="8cb32-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="8cb32-127">所顯示的精簡語法會依賴<xref:System.Windows.ComponentResourceKey.%23ctor%2A>標記延伸的「函式簽章」和「位置參數使用方式」。</span><span class="sxs-lookup"><span data-stu-id="8cb32-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="8cb32-128">指定`targetTypeName`和`targetID`的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="8cb32-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="8cb32-129">Verbose 語法依賴無參數的<xref:System.Windows.ComponentResourceKey.%23ctor%2A>函式，然後以類似物件<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>專案<xref:System.Windows.ComponentResourceKey.ResourceId%2A>上 true 屬性語法的方式來設定和。</span><span class="sxs-lookup"><span data-stu-id="8cb32-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> parameterless constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="8cb32-130">在 verbose 語法中，屬性的設定順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="8cb32-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="8cb32-131">這兩種替代方案的關聯性和機制（compact 和 verbose）在主題[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)中有更詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="8cb32-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="8cb32-132">就技術上而言， `targetID`的值可以是任何物件，而不一定是字串。</span><span class="sxs-lookup"><span data-stu-id="8cb32-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="8cb32-133">不過，WPF 中最常見的用法是將`targetID`值與字串的形式對齊，這類字串在[XamlName 文法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中是有效的。</span><span class="sxs-lookup"><span data-stu-id="8cb32-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="8cb32-134">`ComponentResourceKey`可以在物件專案語法中使用。</span><span class="sxs-lookup"><span data-stu-id="8cb32-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="8cb32-135">在此情況下，必須同時指定<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>和<xref:System.Windows.ComponentResourceKey.ResourceId%2A>屬性的值，才能正確地初始化延伸模組。</span><span class="sxs-lookup"><span data-stu-id="8cb32-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="8cb32-136">在讀取[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]器的執行中，此標記延伸的處理是由<xref:System.Windows.ComponentResourceKey>類別所定義。</span><span class="sxs-lookup"><span data-stu-id="8cb32-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="8cb32-137">`ComponentResourceKey` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="8cb32-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="8cb32-138">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="8cb32-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="8cb32-139">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="8cb32-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="8cb32-140">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="8cb32-140">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb32-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cb32-141">See also</span></span>

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="8cb32-142">控制項撰寫概觀</span><span class="sxs-lookup"><span data-stu-id="8cb32-142">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
- [<span data-ttu-id="8cb32-143">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="8cb32-143">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="8cb32-144">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="8cb32-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
