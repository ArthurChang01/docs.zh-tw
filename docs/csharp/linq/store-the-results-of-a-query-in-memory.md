---
title: 將查詢的結果儲存在記憶體中
description: 如何儲存結果。
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "65633559"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="9bb92-103">將查詢的結果儲存在記憶體中</span><span class="sxs-lookup"><span data-stu-id="9bb92-103">Store the results of a query in memory</span></span>

<span data-ttu-id="9bb92-104">查詢基本上是如何擷取和組織資料的一組指令。</span><span class="sxs-lookup"><span data-stu-id="9bb92-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="9bb92-105">要求結果中的每個後續項目時，會延遲執行查詢。</span><span class="sxs-lookup"><span data-stu-id="9bb92-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="9bb92-106">當您使用 `foreach` 逐一查看結果時，會將項目傳回為已存取。</span><span class="sxs-lookup"><span data-stu-id="9bb92-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="9bb92-107">若要評估查詢，並儲存其結果，而不執行 `foreach` 迴圈，則只要在查詢變數上呼叫下列其中一種方法即可︰</span><span class="sxs-lookup"><span data-stu-id="9bb92-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="9bb92-108">建議當您儲存查詢結果時，將傳回的集合物件指派給新的變數，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="9bb92-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="9bb92-109">範例</span><span class="sxs-lookup"><span data-stu-id="9bb92-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="9bb92-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bb92-110">See also</span></span>

- [<span data-ttu-id="9bb92-111">語言綜合查詢（LINQ）</span><span class="sxs-lookup"><span data-stu-id="9bb92-111">Language Integrated Query (LINQ)</span></span>](index.md)
