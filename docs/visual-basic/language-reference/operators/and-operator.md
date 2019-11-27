---
title: And 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 78a65843a449bd15d5615710e1685f40d94c37f7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350246"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="43e04-102">And 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43e04-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="43e04-103">在兩個 `Boolean` 運算式上執行邏輯結合，或在兩個數值運算式上進行位結合。</span><span class="sxs-lookup"><span data-stu-id="43e04-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43e04-104">語法</span><span class="sxs-lookup"><span data-stu-id="43e04-104">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="43e04-105">組件</span><span class="sxs-lookup"><span data-stu-id="43e04-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="43e04-106">必要。</span><span class="sxs-lookup"><span data-stu-id="43e04-106">Required.</span></span> <span data-ttu-id="43e04-107">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="43e04-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="43e04-108">針對布林比較，`result` 是兩個 `Boolean` 值的邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="43e04-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="43e04-109">對於位運算而言，`result` 是代表兩個數值位模式之位合的數值。</span><span class="sxs-lookup"><span data-stu-id="43e04-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="43e04-110">必要。</span><span class="sxs-lookup"><span data-stu-id="43e04-110">Required.</span></span> <span data-ttu-id="43e04-111">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="43e04-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="43e04-112">必要。</span><span class="sxs-lookup"><span data-stu-id="43e04-112">Required.</span></span> <span data-ttu-id="43e04-113">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="43e04-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43e04-114">備註</span><span class="sxs-lookup"><span data-stu-id="43e04-114">Remarks</span></span>  
 <span data-ttu-id="43e04-115">對於布林值比較，只有在 `expression1` 和 `expression2` 都評估為 `True`時，才會 `True` `result`。</span><span class="sxs-lookup"><span data-stu-id="43e04-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="43e04-116">下表說明如何決定 `result`。</span><span class="sxs-lookup"><span data-stu-id="43e04-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="43e04-117">如果 `expression1` 為</span><span class="sxs-lookup"><span data-stu-id="43e04-117">If `expression1` is</span></span>|<span data-ttu-id="43e04-118">而 `expression2` 為</span><span class="sxs-lookup"><span data-stu-id="43e04-118">And `expression2` is</span></span>|<span data-ttu-id="43e04-119">`result` 的值為</span><span class="sxs-lookup"><span data-stu-id="43e04-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="43e04-120">在布林值比較中，`And` 運算子一律會評估兩個運算式，這可能包括進行程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="43e04-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="43e04-121">[AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)會執行最少運算，這表示如果 `False` *`expression1`，則*不會評估 `expression2`。</span><span class="sxs-lookup"><span data-stu-id="43e04-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="43e04-122">套用至數值時，`And` 運算子會在兩個數值運算式中執行相同位置位的位比較，並根據下表設定 `result` 中的對應位。</span><span class="sxs-lookup"><span data-stu-id="43e04-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="43e04-123">如果 `expression1` 中的位為</span><span class="sxs-lookup"><span data-stu-id="43e04-123">If bit in `expression1` is</span></span>|<span data-ttu-id="43e04-124">`expression2` 中的和位是</span><span class="sxs-lookup"><span data-stu-id="43e04-124">And bit in `expression2` is</span></span>|<span data-ttu-id="43e04-125">`result` 中的位是</span><span class="sxs-lookup"><span data-stu-id="43e04-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="43e04-126">1</span><span class="sxs-lookup"><span data-stu-id="43e04-126">1</span></span>|<span data-ttu-id="43e04-127">1</span><span class="sxs-lookup"><span data-stu-id="43e04-127">1</span></span>|<span data-ttu-id="43e04-128">1</span><span class="sxs-lookup"><span data-stu-id="43e04-128">1</span></span>|  
|<span data-ttu-id="43e04-129">1</span><span class="sxs-lookup"><span data-stu-id="43e04-129">1</span></span>|<span data-ttu-id="43e04-130">0</span><span class="sxs-lookup"><span data-stu-id="43e04-130">0</span></span>|<span data-ttu-id="43e04-131">0</span><span class="sxs-lookup"><span data-stu-id="43e04-131">0</span></span>|  
|<span data-ttu-id="43e04-132">0</span><span class="sxs-lookup"><span data-stu-id="43e04-132">0</span></span>|<span data-ttu-id="43e04-133">1</span><span class="sxs-lookup"><span data-stu-id="43e04-133">1</span></span>|<span data-ttu-id="43e04-134">0</span><span class="sxs-lookup"><span data-stu-id="43e04-134">0</span></span>|  
|<span data-ttu-id="43e04-135">0</span><span class="sxs-lookup"><span data-stu-id="43e04-135">0</span></span>|<span data-ttu-id="43e04-136">0</span><span class="sxs-lookup"><span data-stu-id="43e04-136">0</span></span>|<span data-ttu-id="43e04-137">0</span><span class="sxs-lookup"><span data-stu-id="43e04-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="43e04-138">由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此應該將任何位運算括在括弧中，以確保結果正確。</span><span class="sxs-lookup"><span data-stu-id="43e04-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="43e04-139">資料類型</span><span class="sxs-lookup"><span data-stu-id="43e04-139">Data Types</span></span>  
 <span data-ttu-id="43e04-140">如果運算元包含一個 `Boolean` 運算式和一個數值運算式，Visual Basic 會將 `Boolean` 運算式轉換成數值（-1 代表 `True`，0代表 `False`），並執行位運算。</span><span class="sxs-lookup"><span data-stu-id="43e04-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="43e04-141">若為布林值比較，結果的資料類型會是 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="43e04-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="43e04-142">針對位比較，結果資料類型是適用于 `expression1` 和 `expression2`的資料類型的數數值型別。</span><span class="sxs-lookup"><span data-stu-id="43e04-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="43e04-143">請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關聯式和位比較」資料表。</span><span class="sxs-lookup"><span data-stu-id="43e04-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43e04-144">`And` 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="43e04-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="43e04-145">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="43e04-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="43e04-146">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="43e04-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43e04-147">範例</span><span class="sxs-lookup"><span data-stu-id="43e04-147">Example</span></span>  
 <span data-ttu-id="43e04-148">下列範例會使用 `And` 運算子，在兩個運算式上執行邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="43e04-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="43e04-149">結果為 `Boolean` 值，表示兩個運算式是否都 `True`。</span><span class="sxs-lookup"><span data-stu-id="43e04-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="43e04-150">上述範例會分別產生 `True` 和 `False`的結果。</span><span class="sxs-lookup"><span data-stu-id="43e04-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43e04-151">範例</span><span class="sxs-lookup"><span data-stu-id="43e04-151">Example</span></span>  
 <span data-ttu-id="43e04-152">下列範例會使用 `And` 運算子，在兩個數值運算式的個別位上執行邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="43e04-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="43e04-153">如果運算元中對應的位都設定為1，則結果模式中的位會設定為。</span><span class="sxs-lookup"><span data-stu-id="43e04-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="43e04-154">上述範例會分別產生8、2和0的結果。</span><span class="sxs-lookup"><span data-stu-id="43e04-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e04-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43e04-155">See also</span></span>

- [<span data-ttu-id="43e04-156">邏輯/位運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="43e04-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="43e04-157">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="43e04-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="43e04-158">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="43e04-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="43e04-159">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="43e04-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="43e04-160">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="43e04-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
