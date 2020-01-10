---
title: goto 陳述式 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715278"
---
# <a name="goto-c-reference"></a><span data-ttu-id="f6b7a-102">goto (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f6b7a-102">goto (C# Reference)</span></span>

<span data-ttu-id="f6b7a-103">`goto` 陳述式會將程式控制權直接轉移到標記陳述式。</span><span class="sxs-lookup"><span data-stu-id="f6b7a-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="f6b7a-104">`goto` 的一個常見用法是將控制權轉移到特定的切換案例標籤，或 `switch` 陳述式中的預設標籤。</span><span class="sxs-lookup"><span data-stu-id="f6b7a-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="f6b7a-105">`goto` 陳述式也適用於跳出深度巢狀的迴圈。</span><span class="sxs-lookup"><span data-stu-id="f6b7a-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="f6b7a-106">範例</span><span class="sxs-lookup"><span data-stu-id="f6b7a-106">Example</span></span>

<span data-ttu-id="f6b7a-107">下列範例示範如何在 [switch](switch.md) 陳述式中使用 `goto`。</span><span class="sxs-lookup"><span data-stu-id="f6b7a-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="f6b7a-108">範例</span><span class="sxs-lookup"><span data-stu-id="f6b7a-108">Example</span></span>

<span data-ttu-id="f6b7a-109">下列範例示範如何使用 `goto` 跳出巢狀迴圈。</span><span class="sxs-lookup"><span data-stu-id="f6b7a-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="f6b7a-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f6b7a-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f6b7a-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6b7a-111">See also</span></span>

- [<span data-ttu-id="f6b7a-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f6b7a-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f6b7a-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f6b7a-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f6b7a-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f6b7a-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f6b7a-115">goto 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="f6b7a-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
