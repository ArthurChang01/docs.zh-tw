---
title: REM 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: bdde4beae242c3175b02cd2af252babb850416f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346735"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="a40f3-102">REM 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a40f3-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="a40f3-103">用來在程式的原始程式碼中包含說明備註。</span><span class="sxs-lookup"><span data-stu-id="a40f3-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a40f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="a40f3-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="a40f3-105">組件</span><span class="sxs-lookup"><span data-stu-id="a40f3-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="a40f3-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="a40f3-106">Optional.</span></span> <span data-ttu-id="a40f3-107">您想要包含之任何批註的文字。</span><span class="sxs-lookup"><span data-stu-id="a40f3-107">The text of any comment you want to include.</span></span> <span data-ttu-id="a40f3-108">`REM` 關鍵字與 `comment`之間必須有空格。</span><span class="sxs-lookup"><span data-stu-id="a40f3-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a40f3-109">備註</span><span class="sxs-lookup"><span data-stu-id="a40f3-109">Remarks</span></span>  
 <span data-ttu-id="a40f3-110">您可以將 `REM` 語句單獨放在一行上，也可以將它放在另一個語句後面的一行。</span><span class="sxs-lookup"><span data-stu-id="a40f3-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="a40f3-111">`REM` 語句必須是該行的最後一個語句。</span><span class="sxs-lookup"><span data-stu-id="a40f3-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="a40f3-112">如果它遵循另一個語句，`REM` 必須以空格與該語句隔開。</span><span class="sxs-lookup"><span data-stu-id="a40f3-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="a40f3-113">您可以使用單引號（`'`），而不是 `REM`。</span><span class="sxs-lookup"><span data-stu-id="a40f3-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="a40f3-114">無論您的批註是在同一行的另一個語句後面，還是單獨放在一行上，都是如此。</span><span class="sxs-lookup"><span data-stu-id="a40f3-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a40f3-115">您不能使用行接續順序（`_`）繼續 `REM` 語句。</span><span class="sxs-lookup"><span data-stu-id="a40f3-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="a40f3-116">當批註開始時，編譯器不會檢查字元是否有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="a40f3-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="a40f3-117">對於多行批註，請在每一行上使用另一個 `REM` 語句或批註符號（`'`）。</span><span class="sxs-lookup"><span data-stu-id="a40f3-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a40f3-118">範例</span><span class="sxs-lookup"><span data-stu-id="a40f3-118">Example</span></span>  
 <span data-ttu-id="a40f3-119">下列範例說明用來在程式中包含說明備註的 `REM` 語句。</span><span class="sxs-lookup"><span data-stu-id="a40f3-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="a40f3-120">它也會顯示使用單引號字元（`'`），而不是 `REM`的替代方法。</span><span class="sxs-lookup"><span data-stu-id="a40f3-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a40f3-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="a40f3-121">See also</span></span>

- [<span data-ttu-id="a40f3-122">程式碼中的註解</span><span class="sxs-lookup"><span data-stu-id="a40f3-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="a40f3-123">操作說明：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="a40f3-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
