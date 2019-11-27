---
title: If 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 6d25519dac31dc91f8560fd3252ba3e2622de370
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331009"
---
# <a name="if-operator-visual-basic"></a><span data-ttu-id="26a7f-102">If 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26a7f-102">If Operator (Visual Basic)</span></span>

<span data-ttu-id="26a7f-103">使用短路評估來有條件地傳回兩個值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="26a7f-103">Uses short-circuit evaluation to conditionally return one of two values.</span></span> <span data-ttu-id="26a7f-104">您可以使用三個引數或兩個引數來呼叫 `If` 運算子。</span><span class="sxs-lookup"><span data-stu-id="26a7f-104">The `If` operator can be called with three arguments or with two arguments.</span></span>

## <a name="syntax"></a><span data-ttu-id="26a7f-105">語法</span><span class="sxs-lookup"><span data-stu-id="26a7f-105">Syntax</span></span>

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a><span data-ttu-id="26a7f-106">如果呼叫了具有三個引數的運算子</span><span class="sxs-lookup"><span data-stu-id="26a7f-106">If operator called with three arguments</span></span>

<span data-ttu-id="26a7f-107">使用三個引數呼叫 `If` 時，第一個引數必須評估為可轉換為 `Boolean`的值。</span><span class="sxs-lookup"><span data-stu-id="26a7f-107">When `If` is called by using three arguments, the first argument must evaluate to a value that can be cast as a `Boolean`.</span></span> <span data-ttu-id="26a7f-108">該 `Boolean` 值會決定要評估和傳回的兩個引數中的哪一個。</span><span class="sxs-lookup"><span data-stu-id="26a7f-108">That `Boolean` value will determine which of the other two arguments is evaluated and returned.</span></span> <span data-ttu-id="26a7f-109">下列清單只有在使用三個引數呼叫 `If` 運算子時才適用。</span><span class="sxs-lookup"><span data-stu-id="26a7f-109">The following list applies only when the `If` operator is called by using three arguments.</span></span>

### <a name="parts"></a><span data-ttu-id="26a7f-110">組件</span><span class="sxs-lookup"><span data-stu-id="26a7f-110">Parts</span></span>

|<span data-ttu-id="26a7f-111">詞彙</span><span class="sxs-lookup"><span data-stu-id="26a7f-111">Term</span></span>|<span data-ttu-id="26a7f-112">定義</span><span class="sxs-lookup"><span data-stu-id="26a7f-112">Definition</span></span>|
|---|---|
|`argument1`|<span data-ttu-id="26a7f-113">必要。</span><span class="sxs-lookup"><span data-stu-id="26a7f-113">Required.</span></span> <span data-ttu-id="26a7f-114">`Boolean`</span><span class="sxs-lookup"><span data-stu-id="26a7f-114">`Boolean`.</span></span> <span data-ttu-id="26a7f-115">決定要評估和傳回的其他引數。</span><span class="sxs-lookup"><span data-stu-id="26a7f-115">Determines which of the other arguments to evaluate and return.</span></span>|
|`argument2`|<span data-ttu-id="26a7f-116">必要。</span><span class="sxs-lookup"><span data-stu-id="26a7f-116">Required.</span></span> <span data-ttu-id="26a7f-117">`Object`</span><span class="sxs-lookup"><span data-stu-id="26a7f-117">`Object`.</span></span> <span data-ttu-id="26a7f-118">如果 `argument1` 評估為 `True`，則評估並傳回。</span><span class="sxs-lookup"><span data-stu-id="26a7f-118">Evaluated and returned if `argument1` evaluates to `True`.</span></span>|
|`argument3`|<span data-ttu-id="26a7f-119">必要。</span><span class="sxs-lookup"><span data-stu-id="26a7f-119">Required.</span></span> <span data-ttu-id="26a7f-120">`Object`</span><span class="sxs-lookup"><span data-stu-id="26a7f-120">`Object`.</span></span> <span data-ttu-id="26a7f-121">如果 `argument1` 評估為 `False`，或如果 `argument1` 是評估為[無](../../../visual-basic/language-reference/nothing.md)的[可為 null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` 變數，則評估並傳回。</span><span class="sxs-lookup"><span data-stu-id="26a7f-121">Evaluated and returned if `argument1` evaluates to `False` or if `argument1` is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>|

<span data-ttu-id="26a7f-122">使用三個引數呼叫的 `If` 運算子，其運作方式類似 `IIf` 函數，不同之處在于它會使用最少運算。</span><span class="sxs-lookup"><span data-stu-id="26a7f-122">An `If` operator that is called with three arguments works like an `IIf` function except that it uses short-circuit evaluation.</span></span> <span data-ttu-id="26a7f-123">`IIf` 函式一律會評估它的全部三個引數，而具有三個引數的 `If` 運算子只會評估其中兩個。</span><span class="sxs-lookup"><span data-stu-id="26a7f-123">An `IIf` function always evaluates all three of its arguments, whereas an `If` operator that has three arguments evaluates only two of them.</span></span> <span data-ttu-id="26a7f-124">第一個 `If` 引數會進行評估，並將結果轉換為 `Boolean` 值 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="26a7f-124">The first `If` argument is evaluated and the result is cast as a `Boolean` value, `True` or `False`.</span></span> <span data-ttu-id="26a7f-125">如果 `True`值，則會評估 `argument2`，並傳回其值，但不會評估 `argument3`。</span><span class="sxs-lookup"><span data-stu-id="26a7f-125">If the value is `True`, `argument2` is evaluated and its value is returned, but `argument3` is not evaluated.</span></span> <span data-ttu-id="26a7f-126">如果 `Boolean` 運算式的值為 `False`，`argument3` 會進行評估，並傳回其值，但不會評估 `argument2`。</span><span class="sxs-lookup"><span data-stu-id="26a7f-126">If the value of the `Boolean` expression is `False`, `argument3` is evaluated and its value is returned, but `argument2` is not evaluated.</span></span> <span data-ttu-id="26a7f-127">下列範例說明使用三個引數時的 `If` 用法：</span><span class="sxs-lookup"><span data-stu-id="26a7f-127">The following examples illustrate the use of `If` when three arguments are used:</span></span>

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

<span data-ttu-id="26a7f-128">下列範例說明最少運算評估的值。</span><span class="sxs-lookup"><span data-stu-id="26a7f-128">The following example illustrates the value of short-circuit evaluation.</span></span> <span data-ttu-id="26a7f-129">此範例會顯示兩個嘗試除以變數 `number` 的變數 `divisor` 但 `divisor` 為零時除外。</span><span class="sxs-lookup"><span data-stu-id="26a7f-129">The example shows two attempts to divide variable `number` by variable `divisor` except when `divisor` is zero.</span></span> <span data-ttu-id="26a7f-130">在此情況下，應該會傳回0，而且不會嘗試執行除法，因為執行階段錯誤會產生。</span><span class="sxs-lookup"><span data-stu-id="26a7f-130">In that case, a 0 should be returned, and no attempt should be made to perform the division because a run-time error would result.</span></span> <span data-ttu-id="26a7f-131">由於 `If` 運算式使用的是最少運算，因此它會評估第二個或第三個引數，視第一個引數的值而定。</span><span class="sxs-lookup"><span data-stu-id="26a7f-131">Because the `If` expression uses short-circuit evaluation, it evaluates either the second or the third argument, depending on the value of the first argument.</span></span> <span data-ttu-id="26a7f-132">如果第一個引數為 true，則除數不是零，而且可以安全地評估第二個引數並執行除法。</span><span class="sxs-lookup"><span data-stu-id="26a7f-132">If the first argument is true, the divisor is not zero and it is safe to evaluate the second argument and perform the division.</span></span> <span data-ttu-id="26a7f-133">如果第一個引數為 false，則只會評估第三個引數，並傳回0。</span><span class="sxs-lookup"><span data-stu-id="26a7f-133">If the first argument is false, only the third argument is evaluated and a 0 is returned.</span></span> <span data-ttu-id="26a7f-134">因此，當除數為0時，不會嘗試執行除法，也不會產生錯誤結果。</span><span class="sxs-lookup"><span data-stu-id="26a7f-134">Therefore, when the divisor is 0, no attempt is made to perform the division and no error results.</span></span> <span data-ttu-id="26a7f-135">不過，因為 `IIf` 不會使用最少運算，所以即使第一個引數為 false，也會評估第二個引數。</span><span class="sxs-lookup"><span data-stu-id="26a7f-135">However, because `IIf` does not use short-circuit evaluation, the second argument is evaluated even when the first argument is false.</span></span> <span data-ttu-id="26a7f-136">這會導致執行時間零除的錯誤。</span><span class="sxs-lookup"><span data-stu-id="26a7f-136">This causes a run-time divide-by-zero error.</span></span>

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a><span data-ttu-id="26a7f-137">如果使用兩個引數呼叫運算子</span><span class="sxs-lookup"><span data-stu-id="26a7f-137">If operator called with two arguments</span></span>

<span data-ttu-id="26a7f-138">可以省略 `If` 的第一個引數。</span><span class="sxs-lookup"><span data-stu-id="26a7f-138">The first argument to `If` can be omitted.</span></span> <span data-ttu-id="26a7f-139">這可讓您只使用兩個引數來呼叫運算子。</span><span class="sxs-lookup"><span data-stu-id="26a7f-139">This enables the operator to be called by using only two arguments.</span></span> <span data-ttu-id="26a7f-140">下列清單只適用于使用兩個引數呼叫 `If` 運算子時。</span><span class="sxs-lookup"><span data-stu-id="26a7f-140">The following list applies only when the `If` operator is called with two arguments.</span></span>

### <a name="parts"></a><span data-ttu-id="26a7f-141">組件</span><span class="sxs-lookup"><span data-stu-id="26a7f-141">Parts</span></span>

|<span data-ttu-id="26a7f-142">詞彙</span><span class="sxs-lookup"><span data-stu-id="26a7f-142">Term</span></span>|<span data-ttu-id="26a7f-143">定義</span><span class="sxs-lookup"><span data-stu-id="26a7f-143">Definition</span></span>|
|---|---|
|`argument2`|<span data-ttu-id="26a7f-144">必要。</span><span class="sxs-lookup"><span data-stu-id="26a7f-144">Required.</span></span> <span data-ttu-id="26a7f-145">`Object`</span><span class="sxs-lookup"><span data-stu-id="26a7f-145">`Object`.</span></span> <span data-ttu-id="26a7f-146">必須是參考或可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="26a7f-146">Must be a reference or nullable type.</span></span> <span data-ttu-id="26a7f-147">評估並傳回（當它評估為 `Nothing`以外的任何專案時）。</span><span class="sxs-lookup"><span data-stu-id="26a7f-147">Evaluated and returned when it evaluates to anything other than `Nothing`.</span></span>|
|`argument3`|<span data-ttu-id="26a7f-148">必要。</span><span class="sxs-lookup"><span data-stu-id="26a7f-148">Required.</span></span> <span data-ttu-id="26a7f-149">`Object`</span><span class="sxs-lookup"><span data-stu-id="26a7f-149">`Object`.</span></span> <span data-ttu-id="26a7f-150">如果 `argument2` 評估為 `Nothing`，則評估並傳回。</span><span class="sxs-lookup"><span data-stu-id="26a7f-150">Evaluated and returned if `argument2` evaluates to `Nothing`.</span></span>|

<span data-ttu-id="26a7f-151">當省略 `Boolean` 引數時，第一個引數必須是參考或可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="26a7f-151">When the `Boolean` argument is omitted, the first argument must be a reference or nullable type.</span></span> <span data-ttu-id="26a7f-152">如果第一個引數評估為 `Nothing`，則會傳回第二個引數的值。</span><span class="sxs-lookup"><span data-stu-id="26a7f-152">If the first argument evaluates to `Nothing`, the value of the second argument is returned.</span></span> <span data-ttu-id="26a7f-153">在所有其他情況下，會傳回第一個引數的值。</span><span class="sxs-lookup"><span data-stu-id="26a7f-153">In all other cases, the value of the first argument is returned.</span></span> <span data-ttu-id="26a7f-154">下列範例說明此評估的運作方式：</span><span class="sxs-lookup"><span data-stu-id="26a7f-154">The following example illustrates how this evaluation works:</span></span>

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a><span data-ttu-id="26a7f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26a7f-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [<span data-ttu-id="26a7f-156">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="26a7f-156">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="26a7f-157">Nothing</span><span class="sxs-lookup"><span data-stu-id="26a7f-157">Nothing</span></span>](../nothing.md)
