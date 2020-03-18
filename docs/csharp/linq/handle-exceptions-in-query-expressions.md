---
title: 處理查詢運算式中的例外狀況 (C# 中的 LINQ)
description: 了解如何處理 C# 之 LINQ 查詢運算式中的例外狀況。
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688497"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="662b4-103">處理查詢運算式中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="662b4-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="662b4-104">您可在查詢運算式的內容中呼叫任何方法。</span><span class="sxs-lookup"><span data-stu-id="662b4-104">It's possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="662b4-105">不過，我們建議您避免在查詢運算式中呼叫任何方法，因為它會產生副作用，例如修改資料來源的內容或擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="662b4-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="662b4-106">此範例顯示如何避免在查詢運算式中呼叫方法時引發例外狀況，卻不違反處理例外狀況的一般 .NET 方針。</span><span class="sxs-lookup"><span data-stu-id="662b4-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET guidelines on exception handling.</span></span> <span data-ttu-id="662b4-107">這些方針指出，當您了解為何在指定內容中擲回時，可以接受攔截特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="662b4-107">Those guidelines state that it's acceptable to catch a specific exception when you understand why it's thrown in a given context.</span></span> <span data-ttu-id="662b4-108">有關詳細資訊，請參閱[異常的最佳做法](../../standard/exceptions/best-practices-for-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="662b4-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>

<span data-ttu-id="662b4-109">最後一個範例顯示如何處理這種當您在查詢執行期間必須擲回例外狀況的情況。</span><span class="sxs-lookup"><span data-stu-id="662b4-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>

## <a name="example"></a><span data-ttu-id="662b4-110">範例</span><span class="sxs-lookup"><span data-stu-id="662b4-110">Example</span></span>

<span data-ttu-id="662b4-111">下例示範如何將例外狀況處理程式碼移到查詢運算式之外。</span><span class="sxs-lookup"><span data-stu-id="662b4-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="662b4-112">只有當方法不依賴任何查詢區域變數時才可以。</span><span class="sxs-lookup"><span data-stu-id="662b4-112">This is only possible when the method does not depend on any variables local to the query.</span></span>

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a><span data-ttu-id="662b4-113">範例</span><span class="sxs-lookup"><span data-stu-id="662b4-113">Example</span></span>

<span data-ttu-id="662b4-114">在某些情況下，對從查詢中擲回的例外狀況的最佳回應，可能是立即停止執行查詢。</span><span class="sxs-lookup"><span data-stu-id="662b4-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="662b4-115">下例示範如何處理可能從查詢主體內擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="662b4-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="662b4-116">假設 `SomeMethodThatMightThrow` 可能造成需要停止執行查詢的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="662b4-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>

<span data-ttu-id="662b4-117">請注意，`try` 區塊會括住 `foreach` 迴圈，不是括住查詢本身。</span><span class="sxs-lookup"><span data-stu-id="662b4-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="662b4-118">這是因為 `foreach` 迴圈是查詢實際執行的點。</span><span class="sxs-lookup"><span data-stu-id="662b4-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="662b4-119">有關詳細資訊，請參閱[LINQ 查詢簡介](../programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="662b4-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="662b4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="662b4-120">See also</span></span>

- [<span data-ttu-id="662b4-121">語言綜合查詢（LINQ）</span><span class="sxs-lookup"><span data-stu-id="662b4-121">Language Integrated Query (LINQ)</span></span>](index.md)
