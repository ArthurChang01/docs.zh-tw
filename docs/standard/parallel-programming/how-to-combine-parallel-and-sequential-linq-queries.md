---
title: 如何：結合平行和循序 LINQ 查詢
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 074714b1152c8804ee1e747104dbaf47f4645546
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635861"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="b4010-102">如何：結合平行和循序 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="b4010-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>

<span data-ttu-id="b4010-103">此範例示範如何使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 方法來指示 PLINQ 循序處理查詢中所有後續的運算子。</span><span class="sxs-lookup"><span data-stu-id="b4010-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="b4010-104">儘管順序處理通常比並行慢,但有時需要生成正確的結果。</span><span class="sxs-lookup"><span data-stu-id="b4010-104">Although sequential processing is often slower than parallel, sometimes it's necessary to produce correct results.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4010-105">此示例旨在演示使用方式,並且可能不會比等效的連續 LINQ 到物件查詢運行得更快。</span><span class="sxs-lookup"><span data-stu-id="b4010-105">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="b4010-106">如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="b4010-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4010-107">範例</span><span class="sxs-lookup"><span data-stu-id="b4010-107">Example</span></span>  
 <span data-ttu-id="b4010-108">下列範例示範必須使用 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> 的案例，也就是要保留先前的查詢子句中所建立的順序。</span><span class="sxs-lookup"><span data-stu-id="b4010-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b4010-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b4010-109">Compiling the Code</span></span>  
 <span data-ttu-id="b4010-110">要編譯與執行此代碼,請將您的程式貼上[到 PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)項目中,新增一`Main`行以呼叫方法,然後按**F5**。</span><span class="sxs-lookup"><span data-stu-id="b4010-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press **F5**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4010-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4010-111">See also</span></span>

- [<span data-ttu-id="b4010-112">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b4010-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
