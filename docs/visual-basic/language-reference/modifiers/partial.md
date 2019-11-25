---
title: Partial
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: df85571b757fd54496677bad1195fab9690b79cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351351"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="0ce12-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce12-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="0ce12-103">表示類別宣告為類型的部分定義。</span><span class="sxs-lookup"><span data-stu-id="0ce12-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="0ce12-104">您可以使用 `Partial` 關鍵字，將一個類型的定義分割成數個宣告。</span><span class="sxs-lookup"><span data-stu-id="0ce12-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="0ce12-105">您可以在任意數目的不同原始程式檔中，使用任意數目的部分宣告。</span><span class="sxs-lookup"><span data-stu-id="0ce12-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="0ce12-106">不過，所有宣告都必須位於相同的組件和相同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="0ce12-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ce12-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span><span class="sxs-lookup"><span data-stu-id="0ce12-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="0ce12-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce12-109">語法</span><span class="sxs-lookup"><span data-stu-id="0ce12-109">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="0ce12-110">組件</span><span class="sxs-lookup"><span data-stu-id="0ce12-110">Parts</span></span>  
  
|<span data-ttu-id="0ce12-111">詞彙</span><span class="sxs-lookup"><span data-stu-id="0ce12-111">Term</span></span>|<span data-ttu-id="0ce12-112">定義</span><span class="sxs-lookup"><span data-stu-id="0ce12-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="0ce12-113">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-113">Optional.</span></span> <span data-ttu-id="0ce12-114">套用至此類型的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="0ce12-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="0ce12-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span><span class="sxs-lookup"><span data-stu-id="0ce12-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="0ce12-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-116">Optional.</span></span> <span data-ttu-id="0ce12-117">指定哪些程式碼可以存取此類型。</span><span class="sxs-lookup"><span data-stu-id="0ce12-117">Specifies what code can access this type.</span></span> <span data-ttu-id="0ce12-118">請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="0ce12-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="0ce12-119">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-119">Optional.</span></span> <span data-ttu-id="0ce12-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="0ce12-121">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-121">Optional.</span></span> <span data-ttu-id="0ce12-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="0ce12-123">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-123">Optional.</span></span> <span data-ttu-id="0ce12-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="0ce12-125">必要項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-125">Required.</span></span> <span data-ttu-id="0ce12-126">此類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ce12-126">Name of this type.</span></span> <span data-ttu-id="0ce12-127">必須符合相同類型的所有其他部分宣告中定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ce12-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="0ce12-128">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-128">Optional.</span></span> <span data-ttu-id="0ce12-129">指定這是否為泛型類型。</span><span class="sxs-lookup"><span data-stu-id="0ce12-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="0ce12-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="0ce12-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="0ce12-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="0ce12-133">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-133">Optional.</span></span> <span data-ttu-id="0ce12-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="0ce12-135">如果您使用 `Inherits`，則此為必要項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="0ce12-136">此類別衍生自的類別或介面名稱。</span><span class="sxs-lookup"><span data-stu-id="0ce12-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="0ce12-137">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-137">Optional.</span></span> <span data-ttu-id="0ce12-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="0ce12-139">如果您使用 `Implements`，則此為必要項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-139">Required if you use `Implements`.</span></span> <span data-ttu-id="0ce12-140">此類型實作的介面名稱。</span><span class="sxs-lookup"><span data-stu-id="0ce12-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="0ce12-141">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-141">Optional.</span></span> <span data-ttu-id="0ce12-142">宣告類型的其他變數和事件的陳述式。</span><span class="sxs-lookup"><span data-stu-id="0ce12-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="0ce12-143">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0ce12-143">Optional.</span></span> <span data-ttu-id="0ce12-144">宣告和定義類型的其他程序的陳述式。</span><span class="sxs-lookup"><span data-stu-id="0ce12-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="0ce12-145">`End Class` 或 `End Structure`</span><span class="sxs-lookup"><span data-stu-id="0ce12-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="0ce12-146">結束此部分 `Class` 或 `Structure` 定義。</span><span class="sxs-lookup"><span data-stu-id="0ce12-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ce12-147">備註</span><span class="sxs-lookup"><span data-stu-id="0ce12-147">Remarks</span></span>  
 <span data-ttu-id="0ce12-148">Visual Basic 使用部分類別定義來劃分個別原始程式檔中產生的程式碼與使用者撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0ce12-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="0ce12-149">例如，[Windows Form 設計工具] 會定義控制項的部分類別，如 <xref:System.Windows.Forms.Form>。</span><span class="sxs-lookup"><span data-stu-id="0ce12-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="0ce12-150">您不應該在這些控制項中修改產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0ce12-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="0ce12-151">建立部分類型時會套用類別、結構、介面和模組建立的所有規則，例如修飾詞的使用方式和繼承。</span><span class="sxs-lookup"><span data-stu-id="0ce12-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="0ce12-152">最佳作法</span><span class="sxs-lookup"><span data-stu-id="0ce12-152">Best Practices</span></span>  
  
- <span data-ttu-id="0ce12-153">在正常情況下，您不該將單一類型的開發分成兩個或多個宣告。</span><span class="sxs-lookup"><span data-stu-id="0ce12-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="0ce12-154">因此，在大部分情況下您不需要 `Partial` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0ce12-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="0ce12-155">為了便於閱讀，類型的每個部分宣告都應該包含 `Partial` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0ce12-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="0ce12-156">編譯器最多允許一個部分宣告省略關鍵字；如果有兩個或多個部分宣告省略關鍵字，則編譯器會發出錯誤訊號。</span><span class="sxs-lookup"><span data-stu-id="0ce12-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="0ce12-157">行為</span><span class="sxs-lookup"><span data-stu-id="0ce12-157">Behavior</span></span>  
  
- <span data-ttu-id="0ce12-158">**Union of Declarations.**</span><span class="sxs-lookup"><span data-stu-id="0ce12-158">**Union of Declarations.**</span></span> <span data-ttu-id="0ce12-159">編譯器會將此類型視為其所有部分宣告的等位。</span><span class="sxs-lookup"><span data-stu-id="0ce12-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="0ce12-160">每個部分定義的每個修飾詞都會套用至整個類型，而每個部分定義的每個成員均可用於整個類型。</span><span class="sxs-lookup"><span data-stu-id="0ce12-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="0ce12-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span><span class="sxs-lookup"><span data-stu-id="0ce12-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="0ce12-162">如果部分定義在某個模組內，則該類型的類型提升會自動失效。</span><span class="sxs-lookup"><span data-stu-id="0ce12-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="0ce12-163">在這種情況下，一組部分定義可能會導致非預期的結果，甚至是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="0ce12-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="0ce12-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="0ce12-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="0ce12-165">只有在完整路徑相同時，編譯器才會合併部分定義。</span><span class="sxs-lookup"><span data-stu-id="0ce12-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="0ce12-166">`Partial` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="0ce12-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="0ce12-167">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="0ce12-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="0ce12-168">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="0ce12-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="0ce12-169">範例</span><span class="sxs-lookup"><span data-stu-id="0ce12-169">Example</span></span>  
 <span data-ttu-id="0ce12-170">下列範例會將 `sampleClass` 類別的定義分割成兩個宣告，每個定義可定義不同的 `Sub` 程序。</span><span class="sxs-lookup"><span data-stu-id="0ce12-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="0ce12-171">上述範例中的兩個部分定義可位於相同的原始程式檔或在兩個不同的原始程式檔中。</span><span class="sxs-lookup"><span data-stu-id="0ce12-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce12-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ce12-172">See also</span></span>

- [<span data-ttu-id="0ce12-173">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="0ce12-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="0ce12-174">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="0ce12-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="0ce12-175">型別提升</span><span class="sxs-lookup"><span data-stu-id="0ce12-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="0ce12-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="0ce12-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="0ce12-177">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ce12-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="0ce12-178">部分方法</span><span class="sxs-lookup"><span data-stu-id="0ce12-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
