---
title: GoTo 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: d5cdcd214c9679e245645505fe11cb5d521ce085
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351078"
---
# <a name="goto-statement"></a><span data-ttu-id="957f5-102">GoTo 陳述式</span><span class="sxs-lookup"><span data-stu-id="957f5-102">GoTo Statement</span></span>
<span data-ttu-id="957f5-103">無條件地分支到程式中的指定行。</span><span class="sxs-lookup"><span data-stu-id="957f5-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="957f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="957f5-104">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="957f5-105">組件</span><span class="sxs-lookup"><span data-stu-id="957f5-105">Part</span></span>  
 `line`  
 <span data-ttu-id="957f5-106">必要。</span><span class="sxs-lookup"><span data-stu-id="957f5-106">Required.</span></span> <span data-ttu-id="957f5-107">任何行標籤。</span><span class="sxs-lookup"><span data-stu-id="957f5-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="957f5-108">備註</span><span class="sxs-lookup"><span data-stu-id="957f5-108">Remarks</span></span>  
 <span data-ttu-id="957f5-109">`GoTo` 語句只能分支至其出現所在程式中的行。</span><span class="sxs-lookup"><span data-stu-id="957f5-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="957f5-110">這一行必須有 `GoTo` 可以參考的行標籤。</span><span class="sxs-lookup"><span data-stu-id="957f5-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="957f5-111">如需詳細資訊，請參閱 how [to： Label 語句](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="957f5-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="957f5-112">`GoTo` 語句可能會使程式碼更容易讀取和維護。</span><span class="sxs-lookup"><span data-stu-id="957f5-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="957f5-113">請盡可能改用控制結構。</span><span class="sxs-lookup"><span data-stu-id="957f5-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="957f5-114">如需詳細資訊，請參閱[控制流程](../../../visual-basic/programming-guide/language-features/control-flow/index.md)。</span><span class="sxs-lookup"><span data-stu-id="957f5-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="957f5-115">您無法使用 `GoTo` 語句，從 `For`...`Next`、`For Each`...`Next`、`SyncLock`...`End SyncLock`、`Try`...`Catch`...`Finally`、`With`...`End With`，或 `Using`...`End Using` 結構，到內部的標籤進行分支。</span><span class="sxs-lookup"><span data-stu-id="957f5-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="957f5-116">分支和 Try 結構</span><span class="sxs-lookup"><span data-stu-id="957f5-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="957f5-117">在 `Try`...`Catch`...`Finally` 結構中，下列規則適用于使用 `GoTo` 語句的分支。</span><span class="sxs-lookup"><span data-stu-id="957f5-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="957f5-118">封鎖或區域</span><span class="sxs-lookup"><span data-stu-id="957f5-118">Block or region</span></span>|<span data-ttu-id="957f5-119">從外部分支</span><span class="sxs-lookup"><span data-stu-id="957f5-119">Branching in from outside</span></span>|<span data-ttu-id="957f5-120">從內部分支</span><span class="sxs-lookup"><span data-stu-id="957f5-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="957f5-121">`Try` 區塊</span><span class="sxs-lookup"><span data-stu-id="957f5-121">`Try` block</span></span>|<span data-ttu-id="957f5-122">僅來自相同結構<sup>1</sup>的 `Catch` 區塊</span><span class="sxs-lookup"><span data-stu-id="957f5-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="957f5-123">僅限於整個結構外</span><span class="sxs-lookup"><span data-stu-id="957f5-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="957f5-124">`Catch` 區塊</span><span class="sxs-lookup"><span data-stu-id="957f5-124">`Catch` block</span></span>|<span data-ttu-id="957f5-125">不允許</span><span class="sxs-lookup"><span data-stu-id="957f5-125">Never allowed</span></span>|<span data-ttu-id="957f5-126">僅限於整個結構外，或相同結構<sup>1</sup>的 `Try` 區塊</span><span class="sxs-lookup"><span data-stu-id="957f5-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="957f5-127">`Finally` 區塊</span><span class="sxs-lookup"><span data-stu-id="957f5-127">`Finally` block</span></span>|<span data-ttu-id="957f5-128">不允許</span><span class="sxs-lookup"><span data-stu-id="957f5-128">Never allowed</span></span>|<span data-ttu-id="957f5-129">不允許</span><span class="sxs-lookup"><span data-stu-id="957f5-129">Never allowed</span></span>|  
  
 <span data-ttu-id="957f5-130"><sup>1</sup>如果一個 `Try`...`Catch`...`Finally` 結構嵌套在另一個中，`Catch` 區塊可以在自己的嵌套層級分支至 `Try` 區塊，但不能放入任何其他的 `Try` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="957f5-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="957f5-131">Nested `Try`...`Catch`...`Finally` 結構必須完全包含在其所用之結構的 `Try` 或 `Catch` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="957f5-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="957f5-132">下圖顯示一個嵌套在另一個中的 `Try` 結構。</span><span class="sxs-lookup"><span data-stu-id="957f5-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="957f5-133">兩個結構的區塊之間的各種分支會指出為有效或無效。</span><span class="sxs-lookup"><span data-stu-id="957f5-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Try 語法結構中的分支示意圖](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="957f5-135">範例</span><span class="sxs-lookup"><span data-stu-id="957f5-135">Example</span></span>  
 <span data-ttu-id="957f5-136">下列範例會使用 `GoTo` 語句，在程式中分支至行標籤。</span><span class="sxs-lookup"><span data-stu-id="957f5-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="957f5-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="957f5-137">See also</span></span>

- [<span data-ttu-id="957f5-138">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="957f5-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="957f5-139">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="957f5-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="957f5-140">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="957f5-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="957f5-141">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="957f5-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="957f5-142">Select...Case 陳述式</span><span class="sxs-lookup"><span data-stu-id="957f5-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="957f5-143">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="957f5-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="957f5-144">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="957f5-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="957f5-145">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="957f5-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
