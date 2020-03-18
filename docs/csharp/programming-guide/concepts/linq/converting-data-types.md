---
title: 轉換資料型別 (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347193"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="ad2be-102">轉換資料型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="ad2be-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="ad2be-103">轉換方法會變更輸入物件的類型。</span><span class="sxs-lookup"><span data-stu-id="ad2be-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="ad2be-104">LINQ 查詢中的轉換作業可用於各種應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad2be-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="ad2be-105">下列是一些範例：</span><span class="sxs-lookup"><span data-stu-id="ad2be-105">Following are some examples:</span></span>

- <span data-ttu-id="ad2be-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="ad2be-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="ad2be-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="ad2be-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="ad2be-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。</span><span class="sxs-lookup"><span data-stu-id="ad2be-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="ad2be-109">方法</span><span class="sxs-lookup"><span data-stu-id="ad2be-109">Methods</span></span>
 <span data-ttu-id="ad2be-110">下表列出執行資料型別轉換的標準查詢運算子方法。</span><span class="sxs-lookup"><span data-stu-id="ad2be-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="ad2be-111">此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。</span><span class="sxs-lookup"><span data-stu-id="ad2be-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="ad2be-112">名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。</span><span class="sxs-lookup"><span data-stu-id="ad2be-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="ad2be-113">方法名稱</span><span class="sxs-lookup"><span data-stu-id="ad2be-113">Method Name</span></span>|<span data-ttu-id="ad2be-114">描述</span><span class="sxs-lookup"><span data-stu-id="ad2be-114">Description</span></span>|<span data-ttu-id="ad2be-115">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="ad2be-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="ad2be-116">相關資訊</span><span class="sxs-lookup"><span data-stu-id="ad2be-116">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="ad2be-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="ad2be-117">AsEnumerable</span></span>|<span data-ttu-id="ad2be-118">傳回 <xref:System.Collections.Generic.IEnumerable%601> 類型的輸入。</span><span class="sxs-lookup"><span data-stu-id="ad2be-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="ad2be-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="ad2be-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ad2be-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="ad2be-120">AsQueryable</span></span>|<span data-ttu-id="ad2be-121">將 (泛型) <xref:System.Collections.IEnumerable> 轉換成 (泛型) <xref:System.Linq.IQueryable>。</span><span class="sxs-lookup"><span data-stu-id="ad2be-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="ad2be-122">不適用。</span><span class="sxs-lookup"><span data-stu-id="ad2be-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ad2be-123">Cast</span><span class="sxs-lookup"><span data-stu-id="ad2be-123">Cast</span></span>|<span data-ttu-id="ad2be-124">將集合的項目轉型為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="ad2be-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="ad2be-125">使用類型明確的範圍變數。</span><span class="sxs-lookup"><span data-stu-id="ad2be-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="ad2be-126">例如：</span><span class="sxs-lookup"><span data-stu-id="ad2be-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ad2be-127">OfType</span><span class="sxs-lookup"><span data-stu-id="ad2be-127">OfType</span></span>|<span data-ttu-id="ad2be-128">根據可轉型為所指定類型的能力來篩選值。</span><span class="sxs-lookup"><span data-stu-id="ad2be-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="ad2be-129">不適用。</span><span class="sxs-lookup"><span data-stu-id="ad2be-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ad2be-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="ad2be-130">ToArray</span></span>|<span data-ttu-id="ad2be-131">將集合轉換為陣列。</span><span class="sxs-lookup"><span data-stu-id="ad2be-131">Converts a collection to an array.</span></span> <span data-ttu-id="ad2be-132">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ad2be-132">This method forces query execution.</span></span>|<span data-ttu-id="ad2be-133">不適用。</span><span class="sxs-lookup"><span data-stu-id="ad2be-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ad2be-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="ad2be-134">ToDictionary</span></span>|<span data-ttu-id="ad2be-135">根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="ad2be-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="ad2be-136">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ad2be-136">This method forces query execution.</span></span>|<span data-ttu-id="ad2be-137">不適用。</span><span class="sxs-lookup"><span data-stu-id="ad2be-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ad2be-138">ToList</span><span class="sxs-lookup"><span data-stu-id="ad2be-138">ToList</span></span>|<span data-ttu-id="ad2be-139">將集合轉換成 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="ad2be-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="ad2be-140">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ad2be-140">This method forces query execution.</span></span>|<span data-ttu-id="ad2be-141">不適用。</span><span class="sxs-lookup"><span data-stu-id="ad2be-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ad2be-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="ad2be-142">ToLookup</span></span>|<span data-ttu-id="ad2be-143">根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="ad2be-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="ad2be-144">這個方法會強制執行查詢。</span><span class="sxs-lookup"><span data-stu-id="ad2be-144">This method forces query execution.</span></span>|<span data-ttu-id="ad2be-145">不適用。</span><span class="sxs-lookup"><span data-stu-id="ad2be-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="ad2be-146">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="ad2be-146">Query Expression Syntax Example</span></span>

<span data-ttu-id="ad2be-147">以下代碼示例使用顯式類型範圍變數在訪問僅在子類型上可用的成員之前，將類型轉換為子類型。</span><span class="sxs-lookup"><span data-stu-id="ad2be-147">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

```csharp
class Plant
{
    public string Name { get; set; }
}

class CarnivorousPlant : Plant
{
    public string TrapType { get; set; }
}

static void Cast()
{
    Plant[] plants = new Plant[] {
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }
    };

    var query = from CarnivorousPlant cPlant in plants
                where cPlant.TrapType == "Snap Trap"
                select cPlant;

    foreach (Plant plant in query)
        Console.WriteLine(plant.Name);

    /* This code produces the following output:

        Venus Fly Trap
        Waterwheel Plant
    */
}
```

## <a name="see-also"></a><span data-ttu-id="ad2be-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad2be-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ad2be-149">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="ad2be-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ad2be-150">從 條款</span><span class="sxs-lookup"><span data-stu-id="ad2be-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="ad2be-151">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="ad2be-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="ad2be-152">如何使用 LINQ （C#） 查詢 ArrayList</span><span class="sxs-lookup"><span data-stu-id="ad2be-152">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
