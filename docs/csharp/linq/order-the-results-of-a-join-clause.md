---
title: 排序 join 子句的結果 (C# 中的 LINQ)
description: 了解如何在 C# 中排序 LINQ join 子句的結果。
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659861"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="4e402-103">排序 join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="4e402-103">Order the results of a join clause</span></span>

<span data-ttu-id="4e402-104">本例示範如何排序聯結作業的結果。</span><span class="sxs-lookup"><span data-stu-id="4e402-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="4e402-105">請注意，排序是在聯結後執行。</span><span class="sxs-lookup"><span data-stu-id="4e402-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="4e402-106">雖然您可以在聯結之前使用 `orderby` 子句搭配一或多個來源序列，但通常不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="4e402-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="4e402-107">某些 LINQ 提供者在聯結後可能不會保留排序。</span><span class="sxs-lookup"><span data-stu-id="4e402-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="4e402-108">範例</span><span class="sxs-lookup"><span data-stu-id="4e402-108">Example</span></span>

<span data-ttu-id="4e402-109">此查詢會建立群組聯結，然後根據類別項目排序仍在範圍內的群組。</span><span class="sxs-lookup"><span data-stu-id="4e402-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="4e402-110">在匿名型別初始設定式內，子查詢會排序產品序列中的所有相符項目。</span><span class="sxs-lookup"><span data-stu-id="4e402-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="4e402-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e402-111">See also</span></span>

- [<span data-ttu-id="4e402-112">語言綜合查詢（LINQ）</span><span class="sxs-lookup"><span data-stu-id="4e402-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="4e402-113">orderby 子句</span><span class="sxs-lookup"><span data-stu-id="4e402-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="4e402-114">聯接子句</span><span class="sxs-lookup"><span data-stu-id="4e402-114">join clause</span></span>](../language-reference/keywords/join-clause.md)
