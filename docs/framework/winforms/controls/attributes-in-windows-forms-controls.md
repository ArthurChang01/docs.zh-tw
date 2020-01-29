---
title: 控制項中的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: b32e4f87e953438a3bb11569445a9270e11c7922
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732136"
---
# <a name="attributes-in-windows-forms-controls"></a><span data-ttu-id="c313e-102">Windows Form 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="c313e-102">Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="c313e-103">.NET Framework 提供各種不同的屬性，供您套用至自訂控制項和元件的成員。</span><span class="sxs-lookup"><span data-stu-id="c313e-103">The .NET Framework provides a variety of attributes you can apply to the members of your custom controls and components.</span></span> <span data-ttu-id="c313e-104">其中一些屬性會影響類別的執行階段行為，有些則會影響設計階段行為。</span><span class="sxs-lookup"><span data-stu-id="c313e-104">Some of these attributes affect the run-time behavior of a class, and others affect the design-time behavior.</span></span>  
  
## <a name="attributes-for-control-and-component-properties"></a><span data-ttu-id="c313e-105">控制項和元件屬性 (Property) 的屬性 (Attribute)</span><span class="sxs-lookup"><span data-stu-id="c313e-105">Attributes for Control and Component Properties</span></span>  
 <span data-ttu-id="c313e-106">下表描述的屬性 (Attribute) 可套用至自訂控制項和元件的屬性 (Property) 或其他成員。</span><span class="sxs-lookup"><span data-stu-id="c313e-106">The following table shows the attributes you can apply to properties or other members of your custom controls and components.</span></span> <span data-ttu-id="c313e-107">如需有關使用許多這些屬性的範例，請參閱[如何：在 Windows Forms 控制項中套用屬性](how-to-apply-attributes-in-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="c313e-107">For an example that uses many of these attributes, see [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
|<span data-ttu-id="c313e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c313e-108">Attribute</span></span>|<span data-ttu-id="c313e-109">描述</span><span class="sxs-lookup"><span data-stu-id="c313e-109">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|<span data-ttu-id="c313e-110">指定要傳遞至屬性的值，讓屬性從其他來源取得其值。</span><span class="sxs-lookup"><span data-stu-id="c313e-110">Specifies the value to pass to a property to cause the property to get its value from another source.</span></span> <span data-ttu-id="c313e-111">這稱為「環境」。</span><span class="sxs-lookup"><span data-stu-id="c313e-111">This is known as *ambience*.</span></span>|  
|<xref:System.ComponentModel.BrowsableAttribute>|<span data-ttu-id="c313e-112">指定是否應該在 [屬性] 視窗中顯示屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="c313e-112">Specifies whether a property or event should be displayed in a **Properties** window.</span></span>|  
|<xref:System.ComponentModel.CategoryAttribute>|<span data-ttu-id="c313e-113">指定在 <xref:System.Windows.Forms.PropertyGrid> 控制項中顯示設定為 <xref:System.Windows.Forms.PropertySort.Categorized> 模式時，要將屬性或事件分組的類別目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="c313e-113">Specifies the name of the category in which to group the property or event when displayed in a <xref:System.Windows.Forms.PropertyGrid> control set to <xref:System.Windows.Forms.PropertySort.Categorized> mode.</span></span>|  
|<xref:System.ComponentModel.DefaultValueAttribute>|<span data-ttu-id="c313e-114">指定屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="c313e-114">Specifies the default value for a property.</span></span>|  
|<xref:System.ComponentModel.DescriptionAttribute>|<span data-ttu-id="c313e-115">指定屬性或事件的描述。</span><span class="sxs-lookup"><span data-stu-id="c313e-115">Specifies a description for a property or event.</span></span>|  
|<xref:System.ComponentModel.DisplayNameAttribute>|<span data-ttu-id="c313e-116">指定不接受引數的屬性、事件或 `public void` 方法的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c313e-116">Specifies the display name for a property, event, or `public void` method that takes no arguments.</span></span>|  
|<xref:System.ComponentModel.EditorAttribute>|<span data-ttu-id="c313e-117">指定用來變更屬性的編輯器。</span><span class="sxs-lookup"><span data-stu-id="c313e-117">Specifies the editor to use to change a property.</span></span>|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|<span data-ttu-id="c313e-118">指定在編輯器中可檢視的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="c313e-118">Specifies that a property or method is viewable in an editor.</span></span>|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|<span data-ttu-id="c313e-119">指定類別或成員的內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c313e-119">Specifies the context keyword for a class or member.</span></span>|  
|<xref:System.ComponentModel.LocalizableAttribute>|<span data-ttu-id="c313e-120">指定是否應該當地語系化屬性。</span><span class="sxs-lookup"><span data-stu-id="c313e-120">Specifies whether a property should be localized.</span></span>|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|<span data-ttu-id="c313e-121">指出以星號之類的字元來遮蔽物件的文字表示。</span><span class="sxs-lookup"><span data-stu-id="c313e-121">Indicates that an object's text representation is obscured by characters such as asterisks.</span></span>|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|<span data-ttu-id="c313e-122">指定這個屬性 (Attribute) 所繫結的屬性 (Property) 在設計階段是唯讀或讀寫。</span><span class="sxs-lookup"><span data-stu-id="c313e-122">Specifies whether the property this attribute is bound to is read-only or read/write at design time.</span></span>|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|<span data-ttu-id="c313e-123">指出屬性方格應該在關聯的屬性值變更時重新整理。</span><span class="sxs-lookup"><span data-stu-id="c313e-123">Indicates that the property grid should refresh when the associated property value changes.</span></span>|  
|<xref:System.ComponentModel.TypeConverterAttribute>|<span data-ttu-id="c313e-124">指定要用來做為此屬性所繫結至物件的型別轉換子。</span><span class="sxs-lookup"><span data-stu-id="c313e-124">Specifies what type to use as a converter for the object this attribute is bound to.</span></span>|  
  
## <a name="attributes-for-data-binding-properties"></a><span data-ttu-id="c313e-125">資料繫結屬性 (Property) 的屬性 (Attribute)</span><span class="sxs-lookup"><span data-stu-id="c313e-125">Attributes for Data Binding Properties</span></span>  
 <span data-ttu-id="c313e-126">下表顯示您可以套用的屬性，以指定自訂控制項和元件如何資料繫結互動。</span><span class="sxs-lookup"><span data-stu-id="c313e-126">The following table shows the attributes you can apply to specify how your custom controls and components interact with data binding.</span></span>  
  
|<span data-ttu-id="c313e-127">屬性</span><span class="sxs-lookup"><span data-stu-id="c313e-127">Attribute</span></span>|<span data-ttu-id="c313e-128">描述</span><span class="sxs-lookup"><span data-stu-id="c313e-128">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|<span data-ttu-id="c313e-129">指定屬性是否通常用於繫結。</span><span class="sxs-lookup"><span data-stu-id="c313e-129">Specifies whether a property is typically used for binding.</span></span>|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|<span data-ttu-id="c313e-130">指定元件的資料來源和資料成員屬性。</span><span class="sxs-lookup"><span data-stu-id="c313e-130">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|<span data-ttu-id="c313e-131">指定元件的預設繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="c313e-131">Specifies the default binding property for a component.</span></span>|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|<span data-ttu-id="c313e-132">指定元件的資料來源和資料成員屬性。</span><span class="sxs-lookup"><span data-stu-id="c313e-132">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|<span data-ttu-id="c313e-133">啟用屬性重新導向。</span><span class="sxs-lookup"><span data-stu-id="c313e-133">Enables attribute redirection.</span></span>|  
  
## <a name="attributes-for-classes"></a><span data-ttu-id="c313e-134">類別的屬性</span><span class="sxs-lookup"><span data-stu-id="c313e-134">Attributes for Classes</span></span>  
 <span data-ttu-id="c313e-135">下表顯示您可以套用的屬性，以指定自訂控制項和元件在設計階段的行為。</span><span class="sxs-lookup"><span data-stu-id="c313e-135">The following table shows the attributes you can apply to specify the behavior of your custom controls and components at design time.</span></span>  
  
|<span data-ttu-id="c313e-136">屬性</span><span class="sxs-lookup"><span data-stu-id="c313e-136">Attribute</span></span>|<span data-ttu-id="c313e-137">描述</span><span class="sxs-lookup"><span data-stu-id="c313e-137">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|<span data-ttu-id="c313e-138">指定元件的預設事件。</span><span class="sxs-lookup"><span data-stu-id="c313e-138">Specifies the default event for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|<span data-ttu-id="c313e-139">指定元件的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="c313e-139">Specifies the default property for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerAttribute>|<span data-ttu-id="c313e-140">指定用來實作元件之設計階段服務的類別。</span><span class="sxs-lookup"><span data-stu-id="c313e-140">Specifies the class used to implement design-time services for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|<span data-ttu-id="c313e-141">指定類別的設計工具屬於特定的分類。</span><span class="sxs-lookup"><span data-stu-id="c313e-141">Specifies that the designer for a class belongs to a certain category.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|<span data-ttu-id="c313e-142">代表工具箱項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="c313e-142">Represents an attribute of a toolbox item.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|<span data-ttu-id="c313e-143">指定用於工具箱項目的篩選字串和篩選類型。</span><span class="sxs-lookup"><span data-stu-id="c313e-143">Specifies the filter string and filter type to use for a Toolbox item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c313e-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="c313e-144">See also</span></span>

- <xref:System.Attribute>
- [<span data-ttu-id="c313e-145">操作說明：在 Windows Forms 控制項中套用屬性</span><span class="sxs-lookup"><span data-stu-id="c313e-145">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- <span data-ttu-id="c313e-146">[擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c313e-146">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="c313e-147">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="c313e-147">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
