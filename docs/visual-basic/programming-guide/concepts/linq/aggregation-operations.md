---
title: 彙總作業
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 5c7f9344d379af2fed2a8f3d9f7c031c8ca00e8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345782"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="b7524-102">匯總作業（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b7524-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="b7524-103">彙總運算會計算值集合中的單一值。</span><span class="sxs-lookup"><span data-stu-id="b7524-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="b7524-104">彙總運算的一個範例是，當您使用一個月中每天的溫度值來計算每天平均溫度時。</span><span class="sxs-lookup"><span data-stu-id="b7524-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="b7524-105">下圖顯示一系列數字之三個不同彙總作業的結果。</span><span class="sxs-lookup"><span data-stu-id="b7524-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="b7524-106">第一項作業會加總這些數字。</span><span class="sxs-lookup"><span data-stu-id="b7524-106">The first operation sums the numbers.</span></span> <span data-ttu-id="b7524-107">第二個作業會傳回序列中的最大值。</span><span class="sxs-lookup"><span data-stu-id="b7524-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![顯示 LINQ 彙總作業的圖例。](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="b7524-109">下節列出執行彙總作業的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="b7524-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7524-110">方法</span><span class="sxs-lookup"><span data-stu-id="b7524-110">Methods</span></span>  
  
|<span data-ttu-id="b7524-111">方法名稱</span><span class="sxs-lookup"><span data-stu-id="b7524-111">Method Name</span></span>|<span data-ttu-id="b7524-112">描述</span><span class="sxs-lookup"><span data-stu-id="b7524-112">Description</span></span>|<span data-ttu-id="b7524-113">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="b7524-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="b7524-114">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="b7524-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="b7524-115">Aggregate</span><span class="sxs-lookup"><span data-stu-id="b7524-115">Aggregate</span></span>|<span data-ttu-id="b7524-116">對集合的值執行自訂彙總運算。</span><span class="sxs-lookup"><span data-stu-id="b7524-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="b7524-117">不適用。</span><span class="sxs-lookup"><span data-stu-id="b7524-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7524-118">平均</span><span class="sxs-lookup"><span data-stu-id="b7524-118">Average</span></span>|<span data-ttu-id="b7524-119">計算值集合的平均值。</span><span class="sxs-lookup"><span data-stu-id="b7524-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7524-120">計數</span><span class="sxs-lookup"><span data-stu-id="b7524-120">Count</span></span>|<span data-ttu-id="b7524-121">計算集合中的項目，選擇性僅計算滿足述詞函式的項目。</span><span class="sxs-lookup"><span data-stu-id="b7524-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7524-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="b7524-122">LongCount</span></span>|<span data-ttu-id="b7524-123">計算大型集合中的項目，選擇性僅計算滿足述詞函式的項目。</span><span class="sxs-lookup"><span data-stu-id="b7524-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7524-124">Max</span><span class="sxs-lookup"><span data-stu-id="b7524-124">Max</span></span>|<span data-ttu-id="b7524-125">決定集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="b7524-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7524-126">最小</span><span class="sxs-lookup"><span data-stu-id="b7524-126">Min</span></span>|<span data-ttu-id="b7524-127">決定集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="b7524-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7524-128">Sum</span><span class="sxs-lookup"><span data-stu-id="b7524-128">Sum</span></span>|<span data-ttu-id="b7524-129">計算集合中值的總和。</span><span class="sxs-lookup"><span data-stu-id="b7524-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="b7524-130">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="b7524-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="b7524-131">平均</span><span class="sxs-lookup"><span data-stu-id="b7524-131">Average</span></span>  
 <span data-ttu-id="b7524-132">下列程式碼範例會使用 Visual Basic 中的 `Aggregate Into Average` 子句，來計算代表溫度的數位陣列中的平均溫度。</span><span class="sxs-lookup"><span data-stu-id="b7524-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="b7524-133">計數</span><span class="sxs-lookup"><span data-stu-id="b7524-133">Count</span></span>  
 <span data-ttu-id="b7524-134">下列程式碼範例會使用 Visual Basic 中的 `Aggregate Into Count` 子句，計算陣列中大於或等於80的值數目。</span><span class="sxs-lookup"><span data-stu-id="b7524-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="b7524-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="b7524-135">LongCount</span></span>  
 <span data-ttu-id="b7524-136">下列程式碼範例會使用 `Aggregate Into LongCount` 子句來計算陣列中的值數目。</span><span class="sxs-lookup"><span data-stu-id="b7524-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="b7524-137">Max</span><span class="sxs-lookup"><span data-stu-id="b7524-137">Max</span></span>  
 <span data-ttu-id="b7524-138">下列程式碼範例會使用 `Aggregate Into Max` 子句來計算代表溫度之數位陣列中的最大溫度。</span><span class="sxs-lookup"><span data-stu-id="b7524-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="b7524-139">最小</span><span class="sxs-lookup"><span data-stu-id="b7524-139">Min</span></span>  
 <span data-ttu-id="b7524-140">下列程式碼範例會使用 `Aggregate Into Min` 子句來計算代表溫度的數位陣列中的最小溫度。</span><span class="sxs-lookup"><span data-stu-id="b7524-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="b7524-141">Sum</span><span class="sxs-lookup"><span data-stu-id="b7524-141">Sum</span></span>  
 <span data-ttu-id="b7524-142">下列程式碼範例會使用 `Aggregate Into Sum` 子句，從代表費用的值陣列計算總費用金額。</span><span class="sxs-lookup"><span data-stu-id="b7524-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b7524-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7524-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b7524-144">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7524-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b7524-145">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="b7524-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="b7524-146">如何：計算 CSV 文字檔中的資料行值（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b7524-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="b7524-147">如何：統計、加總或平均資料</span><span class="sxs-lookup"><span data-stu-id="b7524-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="b7524-148">如何：尋找查詢結果中的最小或最大值</span><span class="sxs-lookup"><span data-stu-id="b7524-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="b7524-149">如何：查詢目錄樹狀結構中的最大檔案（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b7524-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="b7524-150">如何：查詢一組資料夾中的總位元組數（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b7524-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
