---
title: If...Then...Else 陳述式
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351167"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="7ee3b-102">If...Then...Else 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ee3b-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="7ee3b-103">根據運算式的值而定，有條件地執行陳述式群組。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ee3b-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ee3b-104">Syntax</span></span>

```vb
' Multiline syntax:
If condition [ Then ]
    [ statements ]
[ ElseIf elseifcondition [ Then ]
    [ elseifstatements ] ]
[ Else
    [ elsestatements ] ]
End If

' Single-line syntax:
If condition Then [ statements ] [ Else [ elsestatements ] ]
```

## <a name="quick-links-to-example-code"></a><span data-ttu-id="7ee3b-105">範例程式碼的快速連結</span><span class="sxs-lookup"><span data-stu-id="7ee3b-105">Quick links to example code</span></span>

<span data-ttu-id="7ee3b-106">本文包含幾個範例，說明 `If`...`Then`...`Else` 語句的用法：</span><span class="sxs-lookup"><span data-stu-id="7ee3b-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="7ee3b-107">多行語法範例</span><span class="sxs-lookup"><span data-stu-id="7ee3b-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="7ee3b-108">嵌套語法範例</span><span class="sxs-lookup"><span data-stu-id="7ee3b-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="7ee3b-109">單行語法範例</span><span class="sxs-lookup"><span data-stu-id="7ee3b-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="7ee3b-110">組件</span><span class="sxs-lookup"><span data-stu-id="7ee3b-110">Parts</span></span>

`condition` \
<span data-ttu-id="7ee3b-111">必要。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-111">Required.</span></span> <span data-ttu-id="7ee3b-112">運算式.</span><span class="sxs-lookup"><span data-stu-id="7ee3b-112">Expression.</span></span> <span data-ttu-id="7ee3b-113">必須評估為 `True` 或 `False`，或是可隱含轉換成 `Boolean`的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="7ee3b-114">如果運算式是評估為「[無](../../../visual-basic/language-reference/nothing.md)」的[可為 null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` 變數，則會將條件視為 `False`運算式，而且會評估 `ElseIf` 區塊（如果存在的話），否則會執行 `Else` 區塊（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="7ee3b-115">單行語法中的必要項;在多行語法中為選擇性。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="7ee3b-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-116">Optional.</span></span> <span data-ttu-id="7ee3b-117">`If`...`Then` 之後的一或多個語句會在 `condition` 評估為 `True`時執行。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="7ee3b-118">如果有 `ElseIf`，則為必要。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="7ee3b-119">運算式.</span><span class="sxs-lookup"><span data-stu-id="7ee3b-119">Expression.</span></span> <span data-ttu-id="7ee3b-120">必須評估為 `True` 或 `False`，或是可隱含轉換成 `Boolean`的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="7ee3b-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-121">Optional.</span></span> <span data-ttu-id="7ee3b-122">`ElseIf`...`Then` 之後的一或多個語句會在 `elseifcondition` 評估為 `True`時執行。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="7ee3b-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-123">Optional.</span></span> <span data-ttu-id="7ee3b-124">如果沒有上一個 `condition` 或 `elseifcondition` 運算式評估為 `True`，就會執行一或多個語句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="7ee3b-125">終止 `If`...`Then`...`Else` 區塊的多行版本。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ee3b-126">備註</span><span class="sxs-lookup"><span data-stu-id="7ee3b-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="7ee3b-127">多行語法</span><span class="sxs-lookup"><span data-stu-id="7ee3b-127">Multiline syntax</span></span>

<span data-ttu-id="7ee3b-128">遇到 `If`...`Then`...`Else` 語句時，`condition` 會經過測試。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="7ee3b-129">如果 `True``condition`，則會執行 `Then` 後面的語句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="7ee3b-130">如果 `False``condition`，則會依序評估每個 `ElseIf` 語句（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="7ee3b-131">找到 `True` `elseifcondition` 時，會執行緊接在相關聯 `ElseIf` 後面的語句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="7ee3b-132">如果沒有 `elseifcondition` 評估為 `True`，或沒有任何 `ElseIf` 的語句，則會執行 `Else` 後面的語句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="7ee3b-133">在執行 `Then`、`ElseIf`或 `Else`後面的語句之後，會繼續執行 `End If`後面的語句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="7ee3b-134">`ElseIf` 和 `Else` 子句都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="7ee3b-135">您可以在 `If`...`Then`...`Else` 語句中擁有任意數量的 `ElseIf` 子句，但 `ElseIf` 子句後面不能出現任何 `Else` 子句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="7ee3b-136">`If`...`Then`...`Else` 語句可以在彼此之間嵌套。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="7ee3b-137">在多行語法中，`If` 語句必須是第一行的唯一語句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="7ee3b-138">`ElseIf`、`Else`和 `End If` 語句的前面只能加上行標籤。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="7ee3b-139">`If`...`Then`...`Else` 區塊的結尾必須是 `End If` 語句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="7ee3b-140">[[選取 ...]](../../../visual-basic/language-reference/statements/select-case-statement.md)當您評估具有數個可能值的單一運算式時，Case 語句可能會更有用。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="7ee3b-141">單行語法</span><span class="sxs-lookup"><span data-stu-id="7ee3b-141">Single-Line syntax</span></span>

<span data-ttu-id="7ee3b-142">若為 true，您可以將單行語法用於具有程式碼的單一條件來執行。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="7ee3b-143">不過，多行語法提供更多的結構和彈性，且更容易讀取、維護和調試。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="7ee3b-144">檢查 `Then` 關鍵字之後，以判斷語句是否為單行 `If`。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="7ee3b-145">如果在同一行 `Then` 之後出現批註以外的任何內容，則會將語句視為單行 `If` 語句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="7ee3b-146">如果 `Then` 不存在，它必須是多行 `If`...`Then`...`Else`的開頭。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="7ee3b-147">在單行語法中，您可以將多個語句當做 `If`...`Then` 決策的結果來執行。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="7ee3b-148">所有的語句都必須在同一行，並以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="7ee3b-149">多行語法範例</span><span class="sxs-lookup"><span data-stu-id="7ee3b-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="7ee3b-150">下列範例說明如何使用 `If`...`Then`...`Else` 語句的多行語法。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="7ee3b-151">嵌套語法範例</span><span class="sxs-lookup"><span data-stu-id="7ee3b-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="7ee3b-152">下列範例包含 nested `If`...`Then`...`Else` 語句。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="7ee3b-153">單行語法範例</span><span class="sxs-lookup"><span data-stu-id="7ee3b-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="7ee3b-154">下列範例說明如何使用單行語法。</span><span class="sxs-lookup"><span data-stu-id="7ee3b-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="7ee3b-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ee3b-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="7ee3b-156">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="7ee3b-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="7ee3b-157">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ee3b-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="7ee3b-158">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="7ee3b-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="7ee3b-159">決策結構</span><span class="sxs-lookup"><span data-stu-id="7ee3b-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="7ee3b-160">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="7ee3b-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="7ee3b-161">If 運算子</span><span class="sxs-lookup"><span data-stu-id="7ee3b-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
