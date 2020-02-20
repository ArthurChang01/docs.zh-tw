---
title: 屬性
description: 瞭解屬性F#如何讓中繼資料套用至程式設計結構。
ms.date: 05/16/2016
ms.openlocfilehash: 1e42dc61d44f31930a7b34799f28a68a2db69c8c
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504111"
---
# <a name="attributes"></a><span data-ttu-id="a7efd-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a7efd-103">Attributes</span></span>

<span data-ttu-id="a7efd-104">屬性可讓中繼資料套用至程式設計結構。</span><span class="sxs-lookup"><span data-stu-id="a7efd-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7efd-105">語法</span><span class="sxs-lookup"><span data-stu-id="a7efd-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="a7efd-106">備註</span><span class="sxs-lookup"><span data-stu-id="a7efd-106">Remarks</span></span>

<span data-ttu-id="a7efd-107">在先前的語法中，*目標*是選擇性的，如果有的話，則會指定要套用屬性的程式實體類型。</span><span class="sxs-lookup"><span data-stu-id="a7efd-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="a7efd-108">*Target*的有效值會顯示在本檔稍後所顯示的表格中。</span><span class="sxs-lookup"><span data-stu-id="a7efd-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="a7efd-109">*屬性名稱*是指有效屬性類型的名稱（可能是以命名空間限定），而不含後置字元 `Attribute` 通常用於屬性類型名稱。</span><span class="sxs-lookup"><span data-stu-id="a7efd-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="a7efd-110">例如，您可以將類型 `ObsoleteAttribute` 縮短為在此內容中 `Obsolete`。</span><span class="sxs-lookup"><span data-stu-id="a7efd-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="a7efd-111">*引數*是屬性類型之函式的引數。</span><span class="sxs-lookup"><span data-stu-id="a7efd-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="a7efd-112">如果屬性具有無參數的函式，則可以省略引數清單和括弧。</span><span class="sxs-lookup"><span data-stu-id="a7efd-112">If an attribute has a parameterless constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="a7efd-113">屬性同時支援位置引數和具名引數。</span><span class="sxs-lookup"><span data-stu-id="a7efd-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="a7efd-114">*位置引數*是以它們出現的順序來使用的引數。</span><span class="sxs-lookup"><span data-stu-id="a7efd-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="a7efd-115">如果屬性具有公用屬性，則可以使用具名引數。</span><span class="sxs-lookup"><span data-stu-id="a7efd-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="a7efd-116">您可以使用引數清單中的下列語法來設定這些參數。</span><span class="sxs-lookup"><span data-stu-id="a7efd-116">You can set these by using the following syntax in the argument list.</span></span>

```fsharp
property-name = property-value
```

<span data-ttu-id="a7efd-117">這類屬性初始化可以依任何順序排列，但必須遵循任何位置引數。</span><span class="sxs-lookup"><span data-stu-id="a7efd-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="a7efd-118">以下是使用位置引數和屬性初始化的屬性範例：</span><span class="sxs-lookup"><span data-stu-id="a7efd-118">The following is an example of an attribute that uses positional arguments and property initializations:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="a7efd-119">在此範例中，屬性是 `DllImportAttribute`，這裡以縮短的形式使用。</span><span class="sxs-lookup"><span data-stu-id="a7efd-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="a7efd-120">第一個引數是位置參數，而第二個是屬性。</span><span class="sxs-lookup"><span data-stu-id="a7efd-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="a7efd-121">屬性是一種 .NET 程式設計結構，可讓稱為*屬性*的物件與型別或其他程式元素產生關聯。</span><span class="sxs-lookup"><span data-stu-id="a7efd-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="a7efd-122">套用屬性的程式元素稱為*屬性目標*。</span><span class="sxs-lookup"><span data-stu-id="a7efd-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="a7efd-123">屬性通常包含其目標的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a7efd-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="a7efd-124">在此內容中，中繼資料可能是除了其欄位和成員以外類型的任何資料。</span><span class="sxs-lookup"><span data-stu-id="a7efd-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="a7efd-125">中F#的屬性可以套用至下列程式設計結構：函式、方法、元件、模組、類型（類別、記錄、結構、介面、委派、列舉、等位等等）、程式（attribute）、屬性（property）、欄位、參數、型別參數和傳回值。</span><span class="sxs-lookup"><span data-stu-id="a7efd-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="a7efd-126">屬性不允許用於類別、運算式或工作流程運算式中的 `let` 系結。</span><span class="sxs-lookup"><span data-stu-id="a7efd-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="a7efd-127">一般而言，屬性宣告會直接出現在屬性目標的宣告前面。</span><span class="sxs-lookup"><span data-stu-id="a7efd-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="a7efd-128">可以同時使用多個屬性宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a7efd-128">Multiple attribute declarations can be used together, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="a7efd-129">您可以在執行時間使用 .NET 反映來查詢屬性。</span><span class="sxs-lookup"><span data-stu-id="a7efd-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="a7efd-130">如先前的程式碼範例所示，您可以個別宣告多個屬性，或者，如果您使用分號來分隔個別屬性和構造函式，則可以在一組方括弧中宣告它們，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a7efd-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="a7efd-131">通常遇到的屬性包括 `Obsolete` 屬性、安全性考慮的屬性、COM 支援的屬性、與程式碼擁有權相關的屬性，以及指出類型是否可以序列化的屬性。</span><span class="sxs-lookup"><span data-stu-id="a7efd-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="a7efd-132">下列範例示範 `Obsolete` 屬性的用法。</span><span class="sxs-lookup"><span data-stu-id="a7efd-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="a7efd-133">針對 `assembly` 和 `module`的屬性目標，您可以將屬性套用至元件中的最上層 `do` 系結。</span><span class="sxs-lookup"><span data-stu-id="a7efd-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="a7efd-134">您可以在屬性宣告中包含 `assembly` 或 `module` 這一字，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a7efd-134">You can include the word `assembly` or `module` in the attribute declaration, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="a7efd-135">如果您省略套用至 `do` 系結之屬性的屬性目標，則F#編譯器會嘗試判斷對該屬性有意義的屬性目標。</span><span class="sxs-lookup"><span data-stu-id="a7efd-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="a7efd-136">許多屬性類別都具有類型 `System.AttributeUsageAttribute` 的屬性，其中包含該屬性所支援之可能目標的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a7efd-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="a7efd-137">如果 `System.AttributeUsageAttribute` 指出屬性支援以函式作為目標，則會採用屬性以套用至程式的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="a7efd-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="a7efd-138">如果 `System.AttributeUsageAttribute` 指出屬性支援將元件當做目標，則編譯器會採用屬性以套用至元件。</span><span class="sxs-lookup"><span data-stu-id="a7efd-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="a7efd-139">大部分的屬性都不會同時套用至函式和元件，但在這些情況下，會採用屬性以套用至程式的 main 函式。</span><span class="sxs-lookup"><span data-stu-id="a7efd-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="a7efd-140">如果明確指定屬性目標，則會將屬性套用至指定的目標。</span><span class="sxs-lookup"><span data-stu-id="a7efd-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="a7efd-141">雖然您通常不需要明確指定屬性目標，但在屬性中， *target*的有效值和使用方式範例如下表所示：</span><span class="sxs-lookup"><span data-stu-id="a7efd-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute along with examples of usage are shown in the following table:</span></span>

<table>
  <tr>
    <th><span data-ttu-id="a7efd-142">屬性目標</span><span class="sxs-lookup"><span data-stu-id="a7efd-142">Attribute target</span></span></td>
    <th><span data-ttu-id="a7efd-143">範例</span><span class="sxs-lookup"><span data-stu-id="a7efd-143">Example</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="a7efd-144">組件 (assembly)</span><span class="sxs-lookup"><span data-stu-id="a7efd-144">assembly</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="a7efd-145">return</span><span class="sxs-lookup"><span data-stu-id="a7efd-145">return</span></span></td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="a7efd-146">field</span><span class="sxs-lookup"><span data-stu-id="a7efd-146">field</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="a7efd-147">屬性</span><span class="sxs-lookup"><span data-stu-id="a7efd-147">property</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="a7efd-148">參數</span><span class="sxs-lookup"><span data-stu-id="a7efd-148">param</span></span></td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="a7efd-149">type</span><span class="sxs-lookup"><span data-stu-id="a7efd-149">type</span></span></td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(LayoutKind.Sequential)&gt;]
type MyStruct =
  struct
    val x : byte
    val y : int
  end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="a7efd-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7efd-150">See also</span></span>

- [<span data-ttu-id="a7efd-151">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a7efd-151">F# Language Reference</span></span>](index.md)
