---
title: TypeOf 運算子
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350883"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="8926c-102">TypeOf 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8926c-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="8926c-103">檢查運算式結果的執行時間類型是否與指定的類型相容。</span><span class="sxs-lookup"><span data-stu-id="8926c-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="8926c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8926c-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="8926c-105">組件</span><span class="sxs-lookup"><span data-stu-id="8926c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="8926c-106">更有效率。</span><span class="sxs-lookup"><span data-stu-id="8926c-106">Returned.</span></span> <span data-ttu-id="8926c-107">`Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="8926c-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="8926c-108">必要。</span><span class="sxs-lookup"><span data-stu-id="8926c-108">Required.</span></span> <span data-ttu-id="8926c-109">評估為參考類型的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="8926c-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="8926c-110">必要。</span><span class="sxs-lookup"><span data-stu-id="8926c-110">Required.</span></span> <span data-ttu-id="8926c-111">任何資料類型名稱。</span><span class="sxs-lookup"><span data-stu-id="8926c-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8926c-112">備註</span><span class="sxs-lookup"><span data-stu-id="8926c-112">Remarks</span></span>  
 <span data-ttu-id="8926c-113">`TypeOf` 運算子會判定 `objectexpression` 的執行階段類型是否相容 `typename`。</span><span class="sxs-lookup"><span data-stu-id="8926c-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="8926c-114">相容性取決 `typename` 的類型分類。</span><span class="sxs-lookup"><span data-stu-id="8926c-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="8926c-115">下表顯示如何判斷相容性。</span><span class="sxs-lookup"><span data-stu-id="8926c-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="8926c-116">`typename` 的類型分類</span><span class="sxs-lookup"><span data-stu-id="8926c-116">Type category of `typename`</span></span>|<span data-ttu-id="8926c-117">相容性準則</span><span class="sxs-lookup"><span data-stu-id="8926c-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="8926c-118">執行個體</span><span class="sxs-lookup"><span data-stu-id="8926c-118">Class</span></span>|<span data-ttu-id="8926c-119">`objectexpression` 的類型 `typename` 或繼承自 `typename`</span><span class="sxs-lookup"><span data-stu-id="8926c-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="8926c-120">結構</span><span class="sxs-lookup"><span data-stu-id="8926c-120">Structure</span></span>|<span data-ttu-id="8926c-121">`objectexpression` 的類型為 `typename`</span><span class="sxs-lookup"><span data-stu-id="8926c-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="8926c-122">介面</span><span class="sxs-lookup"><span data-stu-id="8926c-122">Interface</span></span>|<span data-ttu-id="8926c-123">`objectexpression` 會執行 `typename`，或繼承自實作為的類別 `typename`</span><span class="sxs-lookup"><span data-stu-id="8926c-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="8926c-124">如果 `objectexpression` 的執行階段類別滿足相容性準則，則 `result` 是 `True`。</span><span class="sxs-lookup"><span data-stu-id="8926c-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="8926c-125">否則，`result` 為 `False`。</span><span class="sxs-lookup"><span data-stu-id="8926c-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="8926c-126">如果 `objectexpression` 為 null，則 `TypeOf`...`Is` 傳回 `False`，`IsNot` 則傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="8926c-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="8926c-127">`TypeOf` 一律與 `Is` 關鍵字搭配使用，以建立 `TypeOf`...`Is` 運算式，或使用 `IsNot` 關鍵字來建立 `TypeOf`運算式。`IsNot`</span><span class="sxs-lookup"><span data-stu-id="8926c-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8926c-128">範例</span><span class="sxs-lookup"><span data-stu-id="8926c-128">Example</span></span>  
 <span data-ttu-id="8926c-129">下列範例會使用 `TypeOf`...`Is` 運算式，測試兩個包含各種資料類型的物件參考變數的類型相容性。</span><span class="sxs-lookup"><span data-stu-id="8926c-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="8926c-130">變數 `refInteger` 具有執行階段類型 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="8926c-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="8926c-131">它相容 `Integer`，但不相容 `Double`。</span><span class="sxs-lookup"><span data-stu-id="8926c-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="8926c-132">變數 `refForm` 具有執行階段類型 <xref:System.Windows.Forms.Form>。</span><span class="sxs-lookup"><span data-stu-id="8926c-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="8926c-133">它相容 <xref:System.Windows.Forms.Form> (因為那是其類型)、相容 <xref:System.Windows.Forms.Control> (因為 <xref:System.Windows.Forms.Form> 繼承自 <xref:System.Windows.Forms.Control>)，且具有 <xref:System.ComponentModel.IComponent> (因為 <xref:System.Windows.Forms.Form> 繼承自 <xref:System.ComponentModel.Component>，它會實作 <xref:System.ComponentModel.IComponent>)。</span><span class="sxs-lookup"><span data-stu-id="8926c-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="8926c-134">不過，`refForm` 不相容 <xref:System.Windows.Forms.Label>。</span><span class="sxs-lookup"><span data-stu-id="8926c-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8926c-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="8926c-135">See also</span></span>

- [<span data-ttu-id="8926c-136">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="8926c-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="8926c-137">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="8926c-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="8926c-138">Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="8926c-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="8926c-139">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="8926c-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8926c-140">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="8926c-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8926c-141">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="8926c-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
