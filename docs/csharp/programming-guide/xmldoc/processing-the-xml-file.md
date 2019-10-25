---
title: 處理 XML 檔案 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: b2b19a2b2c46df5b78b6ebba48955cae55d32121
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846941"
---
# <a name="processing-the-xml-file-c-programming-guide"></a><span data-ttu-id="cd390-102">處理 XML 檔案 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="cd390-102">Processing the XML File (C# Programming Guide)</span></span>

<span data-ttu-id="cd390-103">編譯器會針對程式碼中，標記為要產生文件的每個建構產生識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="cd390-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="cd390-104">（如需如何標記程式碼的相關資訊，請參閱[建議的檔註解標記](./recommended-tags-for-documentation-comments.md)）。識別碼字串可唯一識別結構。</span><span class="sxs-lookup"><span data-stu-id="cd390-104">(For information about how to tag your code, see [Recommended Tags for Documentation Comments](./recommended-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="cd390-105">處理 XML 檔案的程式可以使用識別碼字串，來識別對應該識別碼且適用於該文件的 .NET Framework 中繼資料/反映項目。</span><span class="sxs-lookup"><span data-stu-id="cd390-105">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item that the documentation applies to.</span></span>

<span data-ttu-id="cd390-106">XML 檔案不會以階層方式呈現您的程式碼；它是具有針對每個元素所產生之識別碼的一般清單。</span><span class="sxs-lookup"><span data-stu-id="cd390-106">The XML file is not a hierarchical representation of your code; it is a flat list that has a generated ID for each element.</span></span>

<span data-ttu-id="cd390-107">編譯器在產生識別碼字串時會遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="cd390-107">The compiler observes the following rules when it generates the ID strings:</span></span>

- <span data-ttu-id="cd390-108">字串中沒有空白字元。</span><span class="sxs-lookup"><span data-stu-id="cd390-108">No white space is in the string.</span></span>

- <span data-ttu-id="cd390-109">識別碼字串的第一個部分會識別所識別的成員類型，格式為單一字元後面接著一個冒號。</span><span class="sxs-lookup"><span data-stu-id="cd390-109">The first part of the ID string identifies the kind of member being identified, by way of a single character followed by a colon.</span></span> <span data-ttu-id="cd390-110">使用的成員類型如下：</span><span class="sxs-lookup"><span data-stu-id="cd390-110">The following member types are used:</span></span>

    |<span data-ttu-id="cd390-111">字元</span><span class="sxs-lookup"><span data-stu-id="cd390-111">Character</span></span>|<span data-ttu-id="cd390-112">描述</span><span class="sxs-lookup"><span data-stu-id="cd390-112">Description</span></span>|
    |---------------|-----------------|
    |<span data-ttu-id="cd390-113">N</span><span class="sxs-lookup"><span data-stu-id="cd390-113">N</span></span>|<span data-ttu-id="cd390-114">namespace</span><span class="sxs-lookup"><span data-stu-id="cd390-114">namespace</span></span><br /><br /> <span data-ttu-id="cd390-115">您無法將文件註解新增至命名空間，但可讓 cref 參考它們 (如果支援)。</span><span class="sxs-lookup"><span data-stu-id="cd390-115">You cannot add documentation comments to a namespace, but you can make cref references to them, where supported.</span></span>|
    |<span data-ttu-id="cd390-116">T</span><span class="sxs-lookup"><span data-stu-id="cd390-116">T</span></span>|<span data-ttu-id="cd390-117">型別︰類別、介面、建構、列舉、委派</span><span class="sxs-lookup"><span data-stu-id="cd390-117">type: class, interface, struct, enum, delegate</span></span>|
    |<span data-ttu-id="cd390-118">F</span><span class="sxs-lookup"><span data-stu-id="cd390-118">F</span></span>|<span data-ttu-id="cd390-119">Field - 欄位</span><span class="sxs-lookup"><span data-stu-id="cd390-119">field</span></span>|
    |<span data-ttu-id="cd390-120">P</span><span class="sxs-lookup"><span data-stu-id="cd390-120">P</span></span>|<span data-ttu-id="cd390-121">屬性 (包括索引子或其他索引屬性)</span><span class="sxs-lookup"><span data-stu-id="cd390-121">property (including indexers or other indexed properties)</span></span>|
    |<span data-ttu-id="cd390-122">M</span><span class="sxs-lookup"><span data-stu-id="cd390-122">M</span></span>|<span data-ttu-id="cd390-123">方法 (包括像是建構函式、運算子之類的特殊方法)</span><span class="sxs-lookup"><span data-stu-id="cd390-123">method (including such special methods as constructors, operators, and so forth)</span></span>|
    |<span data-ttu-id="cd390-124">E</span><span class="sxs-lookup"><span data-stu-id="cd390-124">E</span></span>|<span data-ttu-id="cd390-125">event</span><span class="sxs-lookup"><span data-stu-id="cd390-125">event</span></span>|
    |<span data-ttu-id="cd390-126">!</span><span class="sxs-lookup"><span data-stu-id="cd390-126">!</span></span>|<span data-ttu-id="cd390-127">錯誤字串</span><span class="sxs-lookup"><span data-stu-id="cd390-127">error string</span></span><br /><br /> <span data-ttu-id="cd390-128">字串的其餘部分提供與錯誤相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="cd390-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="cd390-129">C# 編譯器會針對無法解析的連結產生錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="cd390-129">The C# compiler generates error information for links that cannot be resolved.</span></span>|

- <span data-ttu-id="cd390-130">字串的第二個部分是項目的完整名稱 (從命名空間的根開始)。</span><span class="sxs-lookup"><span data-stu-id="cd390-130">The second part of the string is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="cd390-131">項目名稱、其封入類型及命名空間會以句號來分隔。</span><span class="sxs-lookup"><span data-stu-id="cd390-131">The name of the item, its enclosing type(s), and namespace are separated by periods.</span></span> <span data-ttu-id="cd390-132">如果項目名稱本身包含句點，則會以雜湊符號 ('#') 來取代它們。</span><span class="sxs-lookup"><span data-stu-id="cd390-132">If the name of the item itself has periods, they are replaced by the hash-sign ('#').</span></span> <span data-ttu-id="cd390-133">假設沒有項目的名稱中直接含有雜湊符號。</span><span class="sxs-lookup"><span data-stu-id="cd390-133">It is assumed that no item has a hash-sign directly in its name.</span></span> <span data-ttu-id="cd390-134">例如，String 建構函式的完整名稱會是 "System.String.#ctor"。</span><span class="sxs-lookup"><span data-stu-id="cd390-134">For example, the fully qualified name of the String constructor would be "System.String.#ctor".</span></span>

- <span data-ttu-id="cd390-135">針對屬性和方法，如果有方法的引數，則後面會接著以括弧括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="cd390-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="cd390-136">如果沒有任何引數，就不會出現括弧。</span><span class="sxs-lookup"><span data-stu-id="cd390-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="cd390-137">引數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="cd390-137">The arguments are separated by commas.</span></span> <span data-ttu-id="cd390-138">每個引數的編碼方式都會直接遵循它在 .NET Framework 簽章中的編碼方式：</span><span class="sxs-lookup"><span data-stu-id="cd390-138">The encoding of each argument follows directly how it is encoded in a .NET Framework signature:</span></span>

  - <span data-ttu-id="cd390-139">基底類型。</span><span class="sxs-lookup"><span data-stu-id="cd390-139">Base types.</span></span> <span data-ttu-id="cd390-140">一般類型 (ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE) 會表示為類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="cd390-140">Regular types (ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE) are represented as the fully qualified name of the type.</span></span>

  - <span data-ttu-id="cd390-141">內建類型（例如 ELEMENT_TYPE_I4、ELEMENT_TYPE_OBJECT、ELEMENT_TYPE_STRING、ELEMENT_TYPE_TYPEDBYREF 和 ELEMENT_TYPE_VOID）會表示為對應完整類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="cd390-141">Intrinsic types (for example, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF, and ELEMENT_TYPE_VOID) are represented as the fully qualified name of the corresponding full type.</span></span> <span data-ttu-id="cd390-142">例如，System.Int32 或 System.TypedReference。</span><span class="sxs-lookup"><span data-stu-id="cd390-142">For example, System.Int32 or System.TypedReference.</span></span>

  - <span data-ttu-id="cd390-143">ELEMENT_TYPE_PTR 會表示為 '\*'，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="cd390-143">ELEMENT_TYPE_PTR is represented as a '\*' following the modified type.</span></span>

  - <span data-ttu-id="cd390-144">ELEMENT_TYPE_BYREF 會表示為 '\@'，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="cd390-144">ELEMENT_TYPE_BYREF is represented as a '\@' following the modified type.</span></span>

  - <span data-ttu-id="cd390-145">ELEMENT_TYPE_PINNED 會表示為 '^'，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="cd390-145">ELEMENT_TYPE_PINNED is represented as a '^' following the modified type.</span></span> <span data-ttu-id="cd390-146">C# 編譯器永遠都不會產生這個。</span><span class="sxs-lookup"><span data-stu-id="cd390-146">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="cd390-147">ELEMENT_TYPE_CMOD_REQ 會表示為 '&#124;' 和修飾詞類別的完整名稱，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="cd390-147">ELEMENT_TYPE_CMOD_REQ is represented as a '&#124;' and the fully qualified name of the modifier class, following the modified type.</span></span> <span data-ttu-id="cd390-148">C# 編譯器永遠都不會產生這個。</span><span class="sxs-lookup"><span data-stu-id="cd390-148">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="cd390-149">ELEMENT_TYPE_CMOD_OPT 會表示為 '!' 和修飾詞類別的完整名稱，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="cd390-149">ELEMENT_TYPE_CMOD_OPT is represented as a '!' and the fully qualified name of the modifier class, following the modified type.</span></span>

  - <span data-ttu-id="cd390-150">ELEMENT_TYPE_SZARRAY 會表示為 "[]"，緊接在陣列的元素類型之後。</span><span class="sxs-lookup"><span data-stu-id="cd390-150">ELEMENT_TYPE_SZARRAY is represented as "[]" following the element type of the array.</span></span>

  - <span data-ttu-id="cd390-151">ELEMENT_TYPE_GENERICARRAY 會表示為 "[?]"，緊接在陣列的元素類型之後。</span><span class="sxs-lookup"><span data-stu-id="cd390-151">ELEMENT_TYPE_GENERICARRAY is represented as "[?]" following the element type of the array.</span></span> <span data-ttu-id="cd390-152">C# 編譯器永遠都不會產生這個。</span><span class="sxs-lookup"><span data-stu-id="cd390-152">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="cd390-153">ELEMENT_TYPE_ARRAY 會表示為 [*lowerbound*:`size`,*lowerbound*:`size`]，其中逗號數目的順位是 -1，而每個維度的下限和大小 (如果已知) 會以十進位格式表示。</span><span class="sxs-lookup"><span data-stu-id="cd390-153">ELEMENT_TYPE_ARRAY is represented as [*lowerbound*:`size`,*lowerbound*:`size`] where the number of commas is the rank - 1, and the lower bounds and size of each dimension, if known, are represented in decimal.</span></span> <span data-ttu-id="cd390-154">如果未指定下限或大小，就會加以省略。</span><span class="sxs-lookup"><span data-stu-id="cd390-154">If a lower bound or size is not specified, it is simply omitted.</span></span> <span data-ttu-id="cd390-155">如果省略了特定維度的下限和大小，也會省略 ':'。</span><span class="sxs-lookup"><span data-stu-id="cd390-155">If the lower bound and size for a particular dimension are omitted, the ':' is omitted as well.</span></span> <span data-ttu-id="cd390-156">例如，下限為 1 且未指定大小的 2 維度陣列是 [1:,1:]。</span><span class="sxs-lookup"><span data-stu-id="cd390-156">For example, a 2-dimensional array with 1 as the lower bounds and unspecified sizes is [1:,1:].</span></span>

  - <span data-ttu-id="cd390-157">ELEMENT_TYPE_FNPTR 會表示為 "=FUNC:`type`(*signature*)"，其中 `type` 是傳回類型，而 *signature* 是方法的引數。</span><span class="sxs-lookup"><span data-stu-id="cd390-157">ELEMENT_TYPE_FNPTR is represented as "=FUNC:`type`(*signature*)", where `type` is the return type, and *signature* is the arguments of the method.</span></span> <span data-ttu-id="cd390-158">如果沒有任何引數，就會省略括弧。</span><span class="sxs-lookup"><span data-stu-id="cd390-158">If there are no arguments, the parentheses are omitted.</span></span> <span data-ttu-id="cd390-159">C# 編譯器永遠都不會產生這個。</span><span class="sxs-lookup"><span data-stu-id="cd390-159">The C# compiler never generates this.</span></span>

    <span data-ttu-id="cd390-160">下列簽章元件不會出現，因為絕對不會使用它們來區別多載方法：</span><span class="sxs-lookup"><span data-stu-id="cd390-160">The following signature components are not represented because they are never used for differentiating overloaded methods:</span></span>

  - <span data-ttu-id="cd390-161">呼叫慣例</span><span class="sxs-lookup"><span data-stu-id="cd390-161">calling convention</span></span>

  - <span data-ttu-id="cd390-162">傳回類型</span><span class="sxs-lookup"><span data-stu-id="cd390-162">return type</span></span>

  - <span data-ttu-id="cd390-163">ELEMENT_TYPE_SENTINEL</span><span class="sxs-lookup"><span data-stu-id="cd390-163">ELEMENT_TYPE_SENTINEL</span></span>

- <span data-ttu-id="cd390-164">僅針對轉換運算子 (op_Implicit 和 op_Explicit)，此方法的傳回值會編碼為 ' ~'，後面接著傳回類型，如上述編碼所示。</span><span class="sxs-lookup"><span data-stu-id="cd390-164">For conversion operators only (op_Implicit and op_Explicit), the return value of the method is encoded as a '~' followed by the return type, as encoded above.</span></span>

- <span data-ttu-id="cd390-165">針對泛型類型，類型的名稱後面會接著反引號，然後是表示泛型類型參數數目的數字。</span><span class="sxs-lookup"><span data-stu-id="cd390-165">For generic types, the name of the type is followed by a backtick and then a number that indicates the number of generic type parameters.</span></span> <span data-ttu-id="cd390-166">例如:</span><span class="sxs-lookup"><span data-stu-id="cd390-166">For example:</span></span>

     <span data-ttu-id="cd390-167">``<member name="T:SampleClass`2">`` 是類型的標籤，定義為 `public class SampleClass<T, U>`。</span><span class="sxs-lookup"><span data-stu-id="cd390-167">``<member name="T:SampleClass`2">`` is the tag for a type that is defined as `public class SampleClass<T, U>`.</span></span>

     <span data-ttu-id="cd390-168">針對接受泛型類型作為參數的方法，會將泛型類型參數指定為前面加上反引號的數字 (例如\`0、\`1)。</span><span class="sxs-lookup"><span data-stu-id="cd390-168">For methods taking generic types as parameters, the generic type parameters are specified as numbers prefaced with backticks (for example \`0,\`1).</span></span> <span data-ttu-id="cd390-169">每個數字都表示類型泛型參數之以零為起始的陣列標記法。</span><span class="sxs-lookup"><span data-stu-id="cd390-169">Each number representing a zero-based array notation for the type's generic parameters.</span></span>

## <a name="examples"></a><span data-ttu-id="cd390-170">範例</span><span class="sxs-lookup"><span data-stu-id="cd390-170">Examples</span></span>

<span data-ttu-id="cd390-171">下列範例顯示針對類別及其成員產生識別碼字串的方式：</span><span class="sxs-lookup"><span data-stu-id="cd390-171">The following examples show how the ID strings for a class and its members would be generated:</span></span>

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a><span data-ttu-id="cd390-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd390-172">See also</span></span>

- [<span data-ttu-id="cd390-173">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cd390-173">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cd390-174">-doc (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="cd390-174">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="cd390-175">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="cd390-175">XML Documentation Comments</span></span>](./index.md)
