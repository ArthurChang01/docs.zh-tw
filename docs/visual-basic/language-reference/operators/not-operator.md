---
title: Not 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 08b091ccf6c50438b5ad9d6c445510112abe7418
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348300"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="a01ed-102">Not 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a01ed-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="a01ed-103">在 `Boolean` 運算式上執行邏輯否定，或在數值運算式上執行位否定。</span><span class="sxs-lookup"><span data-stu-id="a01ed-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="a01ed-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a01ed-105">組件</span><span class="sxs-lookup"><span data-stu-id="a01ed-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="a01ed-106">必要。</span><span class="sxs-lookup"><span data-stu-id="a01ed-106">Required.</span></span> <span data-ttu-id="a01ed-107">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="a01ed-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="a01ed-108">必要。</span><span class="sxs-lookup"><span data-stu-id="a01ed-108">Required.</span></span> <span data-ttu-id="a01ed-109">任何 `Boolean` 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="a01ed-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a01ed-110">備註</span><span class="sxs-lookup"><span data-stu-id="a01ed-110">Remarks</span></span>  
 <span data-ttu-id="a01ed-111">針對 `Boolean` 運算式，下表說明如何決定 `result`。</span><span class="sxs-lookup"><span data-stu-id="a01ed-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a01ed-112">如果 `expression` 為</span><span class="sxs-lookup"><span data-stu-id="a01ed-112">If `expression` is</span></span>|<span data-ttu-id="a01ed-113">`result` 的值為</span><span class="sxs-lookup"><span data-stu-id="a01ed-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="a01ed-114">對於數值運算式，`Not` 運算子會反轉任何數值運算式的位值，並根據下表設定 `result` 中的對應位。</span><span class="sxs-lookup"><span data-stu-id="a01ed-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="a01ed-115">如果 `expression` 中的位為</span><span class="sxs-lookup"><span data-stu-id="a01ed-115">If bit in `expression` is</span></span>|<span data-ttu-id="a01ed-116">`result` 中的位是</span><span class="sxs-lookup"><span data-stu-id="a01ed-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="a01ed-117">1</span><span class="sxs-lookup"><span data-stu-id="a01ed-117">1</span></span>|<span data-ttu-id="a01ed-118">0</span><span class="sxs-lookup"><span data-stu-id="a01ed-118">0</span></span>|  
|<span data-ttu-id="a01ed-119">0</span><span class="sxs-lookup"><span data-stu-id="a01ed-119">0</span></span>|<span data-ttu-id="a01ed-120">1</span><span class="sxs-lookup"><span data-stu-id="a01ed-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a01ed-121">由於邏輯和位運算子的優先順序比其他算術和關係運算子低，因此應該將任何位運算括在括弧中，以確保正確執行。</span><span class="sxs-lookup"><span data-stu-id="a01ed-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a01ed-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="a01ed-122">Data Types</span></span>  
 <span data-ttu-id="a01ed-123">如果是布林值否定，結果的資料類型會是 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="a01ed-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="a01ed-124">若為位否定，結果資料類型與 `expression`相同。</span><span class="sxs-lookup"><span data-stu-id="a01ed-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="a01ed-125">不過，如果 expression 為 `Decimal`，則會 `Long`結果。</span><span class="sxs-lookup"><span data-stu-id="a01ed-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a01ed-126">多載化</span><span class="sxs-lookup"><span data-stu-id="a01ed-126">Overloading</span></span>  
 <span data-ttu-id="a01ed-127">`Not` 運算子可以多載 *，這*表示當類別或結構的運算元具有該類別或結構的類型時，就可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="a01ed-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="a01ed-128">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="a01ed-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a01ed-129">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="a01ed-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a01ed-130">範例</span><span class="sxs-lookup"><span data-stu-id="a01ed-130">Example</span></span>  
 <span data-ttu-id="a01ed-131">下列範例會使用 `Not` 運算子，在 `Boolean` 運算式上執行邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="a01ed-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="a01ed-132">結果為 `Boolean` 值，表示運算式值的反轉。</span><span class="sxs-lookup"><span data-stu-id="a01ed-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="a01ed-133">上述範例會分別產生 `False` 和 `True`的結果。</span><span class="sxs-lookup"><span data-stu-id="a01ed-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a01ed-134">範例</span><span class="sxs-lookup"><span data-stu-id="a01ed-134">Example</span></span>  
 <span data-ttu-id="a01ed-135">下列範例會使用 `Not` 運算子，來執行數值運算式之個別位的邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="a01ed-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="a01ed-136">結果模式中的位會設定為運算元模式中對應位的反向，包括符號位。</span><span class="sxs-lookup"><span data-stu-id="a01ed-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="a01ed-137">上述範例會分別產生–11、–9和–7的結果。</span><span class="sxs-lookup"><span data-stu-id="a01ed-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01ed-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="a01ed-138">See also</span></span>

- [<span data-ttu-id="a01ed-139">邏輯/位運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a01ed-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="a01ed-140">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="a01ed-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a01ed-141">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="a01ed-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a01ed-142">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="a01ed-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
