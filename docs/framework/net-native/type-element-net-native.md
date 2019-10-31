---
title: <Type> 元素（.NET Native）
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
ms.openlocfilehash: 4e88b49b82513079ddcf6f0bafe02d44235a406a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091847"
---
# <a name="type-element-net-native"></a><span data-ttu-id="e4b24-102">\<類型 > 元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="e4b24-102">\<Type> Element (.NET Native)</span></span>

<span data-ttu-id="e4b24-103">將執行階段原則套用到特定的類型，例如類別或結構。</span><span class="sxs-lookup"><span data-stu-id="e4b24-103">Applies runtime policy to a particular type, such as a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4b24-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4b24-104">Syntax</span></span>

```xml
<Type Name="type_name"
      Activate="policy_type"
      Browse="policy_type"
      Dynamic="policy_type"
      Serialize="policy_type"
      DataContractSerializer="policy_setting"
      DataContractJsonSerializer="policy_setting"
      XmlSerializer="policy_setting"
      MarshalObject="policy_setting"
      MarshalDelegate="policy_setting"
      MarshalStructure="policy_setting" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4b24-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4b24-105">Attributes and Elements</span></span>

<span data-ttu-id="e4b24-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e4b24-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4b24-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e4b24-107">Attributes</span></span>

|<span data-ttu-id="e4b24-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e4b24-108">Attribute</span></span>|<span data-ttu-id="e4b24-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="e4b24-109">Attribute type</span></span>|<span data-ttu-id="e4b24-110">描述</span><span class="sxs-lookup"><span data-stu-id="e4b24-110">Description</span></span>|
|---------------|--------------------|-----------------|
|`Name`|<span data-ttu-id="e4b24-111">一般</span><span class="sxs-lookup"><span data-stu-id="e4b24-111">General</span></span>|<span data-ttu-id="e4b24-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-112">Required attribute.</span></span> <span data-ttu-id="e4b24-113">指定類型名稱。</span><span class="sxs-lookup"><span data-stu-id="e4b24-113">Specifies the type name.</span></span>|
|`Activate`|<span data-ttu-id="e4b24-114">反射</span><span class="sxs-lookup"><span data-stu-id="e4b24-114">Reflection</span></span>|<span data-ttu-id="e4b24-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-115">Optional attribute.</span></span> <span data-ttu-id="e4b24-116">控制建構函式的執行階段存取，以便啟動執行個體。</span><span class="sxs-lookup"><span data-stu-id="e4b24-116">Controls runtime access to constructors to enable activation of instances.</span></span>|
|`Browse`|<span data-ttu-id="e4b24-117">反射</span><span class="sxs-lookup"><span data-stu-id="e4b24-117">Reflection</span></span>|<span data-ttu-id="e4b24-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-118">Optional attribute.</span></span> <span data-ttu-id="e4b24-119">控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。</span><span class="sxs-lookup"><span data-stu-id="e4b24-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|
|`Dynamic`|<span data-ttu-id="e4b24-120">反射</span><span class="sxs-lookup"><span data-stu-id="e4b24-120">Reflection</span></span>|<span data-ttu-id="e4b24-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-121">Optional attribute.</span></span> <span data-ttu-id="e4b24-122">控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="e4b24-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|
|`Serialize`|<span data-ttu-id="e4b24-123">序列化</span><span class="sxs-lookup"><span data-stu-id="e4b24-123">Serialization</span></span>|<span data-ttu-id="e4b24-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-124">Optional attribute.</span></span> <span data-ttu-id="e4b24-125">控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="e4b24-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|
|`DataContractSerializer`|<span data-ttu-id="e4b24-126">序列化</span><span class="sxs-lookup"><span data-stu-id="e4b24-126">Serialization</span></span>|<span data-ttu-id="e4b24-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-127">Optional attribute.</span></span> <span data-ttu-id="e4b24-128">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 類別的序列化原則。</span><span class="sxs-lookup"><span data-stu-id="e4b24-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|
|`DataContractJsonSerializer`|<span data-ttu-id="e4b24-129">序列化</span><span class="sxs-lookup"><span data-stu-id="e4b24-129">Serialization</span></span>|<span data-ttu-id="e4b24-130">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-130">Optional attribute.</span></span> <span data-ttu-id="e4b24-131">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 類別的 JSON 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="e4b24-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|
|`XmlSerializer`|<span data-ttu-id="e4b24-132">序列化</span><span class="sxs-lookup"><span data-stu-id="e4b24-132">Serialization</span></span>|<span data-ttu-id="e4b24-133">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-133">Optional attribute.</span></span> <span data-ttu-id="e4b24-134">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 類別的 XML 序列化原則。</span><span class="sxs-lookup"><span data-stu-id="e4b24-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|
|`MarshalObject`|<span data-ttu-id="e4b24-135">Interop</span><span class="sxs-lookup"><span data-stu-id="e4b24-135">Interop</span></span>|<span data-ttu-id="e4b24-136">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-136">Optional attribute.</span></span> <span data-ttu-id="e4b24-137">控制 Windows 執行階段和 COM 之參考類型的封送處理原則。</span><span class="sxs-lookup"><span data-stu-id="e4b24-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|
|`MarshalDelegate`|<span data-ttu-id="e4b24-138">Interop</span><span class="sxs-lookup"><span data-stu-id="e4b24-138">Interop</span></span>|<span data-ttu-id="e4b24-139">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-139">Optional attribute.</span></span> <span data-ttu-id="e4b24-140">控制將委派類型當作函式指標封送處理至機器碼的原則。</span><span class="sxs-lookup"><span data-stu-id="e4b24-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|
|`MarshalStructure`|<span data-ttu-id="e4b24-141">Interop</span><span class="sxs-lookup"><span data-stu-id="e4b24-141">Interop</span></span>|<span data-ttu-id="e4b24-142">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-142">Optional attribute.</span></span> <span data-ttu-id="e4b24-143">控制將值類型封送處理為原生程式碼的原則。</span><span class="sxs-lookup"><span data-stu-id="e4b24-143">Controls policy for marshaling value types to native code.</span></span>|

## <a name="name-attribute"></a><span data-ttu-id="e4b24-144">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="e4b24-144">Name attribute</span></span>

|<span data-ttu-id="e4b24-145">值</span><span class="sxs-lookup"><span data-stu-id="e4b24-145">Value</span></span>|<span data-ttu-id="e4b24-146">描述</span><span class="sxs-lookup"><span data-stu-id="e4b24-146">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="e4b24-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="e4b24-147">*type_name*</span></span>|<span data-ttu-id="e4b24-148">類型名稱。</span><span class="sxs-lookup"><span data-stu-id="e4b24-148">The type name.</span></span> <span data-ttu-id="e4b24-149">如果這個 `<Type>` 元素是 [\<Namespace>](namespace-element-net-native.md) 元素或另一個 `<Type>` 元素的子系，則 *type_name* 可以包含類型的名稱，而不含命名空間。</span><span class="sxs-lookup"><span data-stu-id="e4b24-149">If this `<Type>` element is the child of either a [\<Namespace>](namespace-element-net-native.md) element or another `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="e4b24-150">否則，*type_name* 必須包含完整的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="e4b24-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|

## <a name="all-other-attributes"></a><span data-ttu-id="e4b24-151">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="e4b24-151">All other attributes</span></span>

|<span data-ttu-id="e4b24-152">值</span><span class="sxs-lookup"><span data-stu-id="e4b24-152">Value</span></span>|<span data-ttu-id="e4b24-153">描述</span><span class="sxs-lookup"><span data-stu-id="e4b24-153">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="e4b24-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e4b24-154">*policy_setting*</span></span>|<span data-ttu-id="e4b24-155">要套用到此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="e4b24-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="e4b24-156">可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="e4b24-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="e4b24-157">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e4b24-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e4b24-158">子項目</span><span class="sxs-lookup"><span data-stu-id="e4b24-158">Child Elements</span></span>

|<span data-ttu-id="e4b24-159">項目</span><span class="sxs-lookup"><span data-stu-id="e4b24-159">Element</span></span>|<span data-ttu-id="e4b24-160">描述</span><span class="sxs-lookup"><span data-stu-id="e4b24-160">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4b24-161">\<AttributeImplies></span><span class="sxs-lookup"><span data-stu-id="e4b24-161">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)|<span data-ttu-id="e4b24-162">如果包含之類型是屬性，則定義屬性套用到的程式碼項目的執行階段原則。</span><span class="sxs-lookup"><span data-stu-id="e4b24-162">If the containing type is an attribute, defines runtime policy for code elements to which the attribute is applied.</span></span>|
|[<span data-ttu-id="e4b24-163">\<Event></span><span class="sxs-lookup"><span data-stu-id="e4b24-163">\<Event></span></span>](event-element-net-native.md)|<span data-ttu-id="e4b24-164">將反映原則套用至屬於此類型的事件。</span><span class="sxs-lookup"><span data-stu-id="e4b24-164">Applies reflection policy to an event belonging to this type.</span></span>|
|[<span data-ttu-id="e4b24-165">\<Field></span><span class="sxs-lookup"><span data-stu-id="e4b24-165">\<Field></span></span>](field-element-net-native.md)|<span data-ttu-id="e4b24-166">將反映原則套用至屬於此類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="e4b24-166">Applies reflection policy to a field belonging to this type.</span></span>|
|[<span data-ttu-id="e4b24-167">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="e4b24-167">\<GenericParameter></span></span>](genericparameter-element-net-native.md)|<span data-ttu-id="e4b24-168">將原則套用至泛型類型的參數類型。</span><span class="sxs-lookup"><span data-stu-id="e4b24-168">Applies policy to the parameter type of a generic type.</span></span>|
|[<span data-ttu-id="e4b24-169">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="e4b24-169">\<ImpliesType></span></span>](impliestype-element-net-native.md)|<span data-ttu-id="e4b24-170">如果原則已套用至包含 `<Type>` 元素所表示的類型，則會將該原則套用至類型。</span><span class="sxs-lookup"><span data-stu-id="e4b24-170">Applies policy to a type, if that policy has been applied to the type represented by the containing `<Type>` element.</span></span>|
|[<span data-ttu-id="e4b24-171">\<Method></span><span class="sxs-lookup"><span data-stu-id="e4b24-171">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="e4b24-172">將反映原則套用至屬於此類型的方法。</span><span class="sxs-lookup"><span data-stu-id="e4b24-172">Applies reflection policy to a method belonging to this type.</span></span>|
|[<span data-ttu-id="e4b24-173">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="e4b24-173">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)|<span data-ttu-id="e4b24-174">將反映原則套用至屬於此類型的建構泛型方法。</span><span class="sxs-lookup"><span data-stu-id="e4b24-174">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|
|[<span data-ttu-id="e4b24-175">\<Property></span><span class="sxs-lookup"><span data-stu-id="e4b24-175">\<Property></span></span>](property-element-net-native.md)|<span data-ttu-id="e4b24-176">將反映原則套用至屬於此類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-176">Applies reflection policy to a property belonging to this type.</span></span>|
|[<span data-ttu-id="e4b24-177">\<Subtypes></span><span class="sxs-lookup"><span data-stu-id="e4b24-177">\<Subtypes></span></span>](subtypes-element-net-native.md)|<span data-ttu-id="e4b24-178">將執行階段原則套用至從包含類型繼承的所有類別。</span><span class="sxs-lookup"><span data-stu-id="e4b24-178">Applies runtime policy to all classes inherited from the containing type.</span></span>|
|`<Type>`|<span data-ttu-id="e4b24-179">將反映原則套用至巢狀類型。</span><span class="sxs-lookup"><span data-stu-id="e4b24-179">Applies reflection policy to a nested type.</span></span>|
|[<span data-ttu-id="e4b24-180">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="e4b24-180">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="e4b24-181">將反映原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="e4b24-181">Applies reflection policy to a constructed generic type.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e4b24-182">父項目</span><span class="sxs-lookup"><span data-stu-id="e4b24-182">Parent Elements</span></span>

|<span data-ttu-id="e4b24-183">項目</span><span class="sxs-lookup"><span data-stu-id="e4b24-183">Element</span></span>|<span data-ttu-id="e4b24-184">描述</span><span class="sxs-lookup"><span data-stu-id="e4b24-184">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4b24-185">\<Application></span><span class="sxs-lookup"><span data-stu-id="e4b24-185">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="e4b24-186">做為容器，以包含整個應用程式的類型，以及中繼資料可在執行階段用於反映的類型成員。</span><span class="sxs-lookup"><span data-stu-id="e4b24-186">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|
|[<span data-ttu-id="e4b24-187">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="e4b24-187">\<Assembly></span></span>](assembly-element-net-native.md)|<span data-ttu-id="e4b24-188">將反映原則套用至指定組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="e4b24-188">Applies reflection policy to all the types in a specified assembly.</span></span>|
|[<span data-ttu-id="e4b24-189">\<Library></span><span class="sxs-lookup"><span data-stu-id="e4b24-189">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="e4b24-190">定義包含類型和類型成員的組件，這些類型和類型成員的中繼資料可在執行階段用於反映。</span><span class="sxs-lookup"><span data-stu-id="e4b24-190">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|
|[<span data-ttu-id="e4b24-191">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="e4b24-191">\<Namespace></span></span>](namespace-element-net-native.md)|<span data-ttu-id="e4b24-192">將反映原則套用至命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="e4b24-192">Applies reflection policy to all the types in a namespace.</span></span>|
|`<Type>`|<span data-ttu-id="e4b24-193">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="e4b24-193">Applies reflection policy to a type and all its members.</span></span>|
|[<span data-ttu-id="e4b24-194">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="e4b24-194">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="e4b24-195">將反映原則套用至建構泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="e4b24-195">Applies reflection policy to a constructed generic type and all its members.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4b24-196">備註</span><span class="sxs-lookup"><span data-stu-id="e4b24-196">Remarks</span></span>

<span data-ttu-id="e4b24-197">反映、序列化和 interop 屬性都是選用性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-197">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="e4b24-198">如果都不存在，`<Type>` 項目會做為容器，其子類型會定義個別成員的原則。</span><span class="sxs-lookup"><span data-stu-id="e4b24-198">If none are present, the `<Type>` element serves as a container whose child types define policy for individual members.</span></span>

<span data-ttu-id="e4b24-199">如果 `<Type>` 元素是 [\<Assembly>](assembly-element-net-native.md)、[\<Namespace>](namespace-element-net-native.md)、`<Type>` 或 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 元素的子系，它會覆寫父元素所定義的原則設定。</span><span class="sxs-lookup"><span data-stu-id="e4b24-199">If a `<Type>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), `<Type>`, or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element, it overrides the policy settings defined by the parent element.</span></span>

<span data-ttu-id="e4b24-200">泛型類型的 `<Type>` 項目會將其原則套用至沒有自己的原則的所有例項。</span><span class="sxs-lookup"><span data-stu-id="e4b24-200">A `<Type>` element of a generic type applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="e4b24-201">建構的泛型型別原則是由 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 元素所定義。</span><span class="sxs-lookup"><span data-stu-id="e4b24-201">The policy of constructed generic types is defined by the [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>

<span data-ttu-id="e4b24-202">如果類型是泛型類型，其名稱會標示抑音符號符號 (\`) 後面接著其泛型參數的數目。</span><span class="sxs-lookup"><span data-stu-id="e4b24-202">If the type is a generic type, its name is decorated by a grave accent symbol (\`) followed by its number of generic parameters.</span></span> <span data-ttu-id="e4b24-203">例如，`Name` 類別之 `<Type>` 項目的 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 屬性，會顯示為 ``Name="System.Collections.Generic.List`1"``。</span><span class="sxs-lookup"><span data-stu-id="e4b24-203">For example, the `Name` attribute of a `<Type>` element for the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class appears as ``Name="System.Collections.Generic.List`1"``.</span></span>

## <a name="example"></a><span data-ttu-id="e4b24-204">範例</span><span class="sxs-lookup"><span data-stu-id="e4b24-204">Example</span></span>

<span data-ttu-id="e4b24-205">下列範例使用反映來顯示 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 類別之欄位、屬性和方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4b24-205">The following example uses reflection to display information about the fields, properties, and methods of the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e4b24-206">範例中的變數 `b` 是 <xref:Windows.UI.Xaml.Controls.TextBlock> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e4b24-206">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span> <span data-ttu-id="e4b24-207">因為範例只會擷取類型資訊，所以中繼資料的可用性是由 `Browse` 原則設定所控制。</span><span class="sxs-lookup"><span data-stu-id="e4b24-207">Because the example simply retrieves type information, the availability of metadata is controlled by the `Browse` policy setting.</span></span>

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 <span data-ttu-id="e4b24-208">因為 <xref:System.Collections.Generic.List%601> 類別的中繼資料不會自動包含在 .NET Native 工具鏈中，所以範例無法在執行時間顯示所要求的成員資訊。</span><span class="sxs-lookup"><span data-stu-id="e4b24-208">Because metadata for the <xref:System.Collections.Generic.List%601> class isn't automatically included by the .NET Native tool chain, the example fails to display the requested member information at run time.</span></span> <span data-ttu-id="e4b24-209">若要提供必要的中繼資料，將下列 `<Type>` 項目加入到執行階段指示詞檔案。</span><span class="sxs-lookup"><span data-stu-id="e4b24-209">To provide the necessary metadata, add the following `<Type>` element to the runtime directives file.</span></span> <span data-ttu-id="e4b24-210">請注意，因為我們提供了父代 [<Namespace\>](namespace-element-net-native.md) 元素，所以不必在 `<Type>` 元素中提供完整的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="e4b24-210">Note that, because we've provided a parent [<Namespace\>](namespace-element-net-native.md) element, we don't have to provide a fully qualified type name in the `<Type>` element.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="*Application*" Dynamic="Required All" />
      <Namespace Name ="System.Collections.Generic" >
        <Type Name="List`1" Browse="Required All" />
     </Namespace>
   </Application>
</Directives>
```

## <a name="example"></a><span data-ttu-id="e4b24-211">範例</span><span class="sxs-lookup"><span data-stu-id="e4b24-211">Example</span></span>
 <span data-ttu-id="e4b24-212">下列範例使用反映來擷取 <xref:System.Reflection.PropertyInfo> 物件，代表 <xref:System.String.Chars%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b24-212">The following example uses reflection to retrieve a <xref:System.Reflection.PropertyInfo> object that represents the <xref:System.String.Chars%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e4b24-213">然後，它使用 <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法擷取字串中的第七個字元的值，並顯示字串中的所有字元。</span><span class="sxs-lookup"><span data-stu-id="e4b24-213">It then uses the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method to retrieve the value of the seventh character in a string, and to display all the characters in the string.</span></span> <span data-ttu-id="e4b24-214">範例中的變數 `b` 是 <xref:Windows.UI.Xaml.Controls.TextBlock> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e4b24-214">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 <span data-ttu-id="e4b24-215">因為 <xref:System.String> 物件的中繼資料無法使用，所以在使用 .NET Native 工具鏈編譯時，呼叫 <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法會在執行時間擲回 <xref:System.NullReferenceException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e4b24-215">Because metadata for the <xref:System.String> object isn't available, the call to the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method throws a <xref:System.NullReferenceException> exception at run time when compiled with the .NET Native tool chain.</span></span> <span data-ttu-id="e4b24-216">若要消除例外狀況，並提供必要的中繼資料，將下列 `<Type>` 項目加入至執行階段指示詞檔案：</span><span class="sxs-lookup"><span data-stu-id="e4b24-216">To eliminate the exception and provide the necessary metadata, add the following `<Type>` element to the runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a><span data-ttu-id="e4b24-217">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4b24-217">See also</span></span>

- [<span data-ttu-id="e4b24-218">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="e4b24-218">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e4b24-219">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="e4b24-219">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="e4b24-220">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="e4b24-220">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
