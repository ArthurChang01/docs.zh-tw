---
title: 聯結作業 (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: 456894dd07f512d7e694ad0056b1e861dc3012c5
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423386"
---
# <a name="join-operations-c"></a><span data-ttu-id="ebd36-102">聯結作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="ebd36-102">Join Operations (C#)</span></span>
<span data-ttu-id="ebd36-103">兩個資料來源的「聯結」，就是某個資料來源中的物件，和另一個資料來源中共用通用屬性的物件的關聯。</span><span class="sxs-lookup"><span data-stu-id="ebd36-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="ebd36-104">對於不能直接追蹤目標資料來源彼此之間的關聯性的查詢而言，聯結是很重要的作業。</span><span class="sxs-lookup"><span data-stu-id="ebd36-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="ebd36-105">在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。</span><span class="sxs-lookup"><span data-stu-id="ebd36-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="ebd36-106">一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="ebd36-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="ebd36-107">若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。</span><span class="sxs-lookup"><span data-stu-id="ebd36-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="ebd36-108">LINQ 架構中所提供的 join 方法是 <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A>。</span><span class="sxs-lookup"><span data-stu-id="ebd36-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="ebd36-109">這些方法會執行等聯結，或是執行根據其索引鍵相等與否配對兩個資料來源的聯結。</span><span class="sxs-lookup"><span data-stu-id="ebd36-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="ebd36-110">（為了進行比較，Transact-sql 支援 ' equals ' 以外的聯結運算子，例如 ' 小於 ' 運算子）。在關係資料庫詞彙中，<xref:System.Linq.Enumerable.Join%2A> 會執行內部聯結，這是一種聯結類型，其中只會傳回在其他資料集中具有相符項的物件。</span><span class="sxs-lookup"><span data-stu-id="ebd36-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="ebd36-111"><xref:System.Linq.Enumerable.GroupJoin%2A> 方法從關聯式資料庫觀點來看沒有直接的對應項目，但它會實作內部聯結和左方外部聯結的超集。</span><span class="sxs-lookup"><span data-stu-id="ebd36-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="ebd36-112">左方外部聯結是傳回第一個 (左) 資料來源中每個項目的聯結，即使它在其他資料來源中沒有相互關聯的項目也一樣。</span><span class="sxs-lookup"><span data-stu-id="ebd36-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="ebd36-113">以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。</span><span class="sxs-lookup"><span data-stu-id="ebd36-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![顯示內部&#47;外部的兩個重疊圓形。](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="ebd36-115">方法</span><span class="sxs-lookup"><span data-stu-id="ebd36-115">Methods</span></span>  
  
|<span data-ttu-id="ebd36-116">方法名稱</span><span class="sxs-lookup"><span data-stu-id="ebd36-116">Method Name</span></span>|<span data-ttu-id="ebd36-117">描述</span><span class="sxs-lookup"><span data-stu-id="ebd36-117">Description</span></span>|<span data-ttu-id="ebd36-118">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="ebd36-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="ebd36-119">更多資訊</span><span class="sxs-lookup"><span data-stu-id="ebd36-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="ebd36-120">Join</span><span class="sxs-lookup"><span data-stu-id="ebd36-120">Join</span></span>|<span data-ttu-id="ebd36-121">根據索引鍵選取器函式聯結兩個序列並擷取值組。</span><span class="sxs-lookup"><span data-stu-id="ebd36-121">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebd36-122">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="ebd36-122">GroupJoin</span></span>|<span data-ttu-id="ebd36-123">根據索引鍵選取器函式聯結兩個序列，並為每個項目的相符結果進行分組。</span><span class="sxs-lookup"><span data-stu-id="ebd36-123">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="ebd36-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="ebd36-124">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ebd36-125">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="ebd36-125">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ebd36-126">匿名類型</span><span class="sxs-lookup"><span data-stu-id="ebd36-126">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="ebd36-127">制定聯結和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="ebd36-127">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="ebd36-128">join 子句</span><span class="sxs-lookup"><span data-stu-id="ebd36-128">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="ebd36-129">如何：使用複合索引鍵執行聯結</span><span class="sxs-lookup"><span data-stu-id="ebd36-129">How to: Join by Using Composite Keys</span></span>](../../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="ebd36-130">如何：從不同的檔案聯結內容 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ebd36-130">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="ebd36-131">如何：排序 Join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="ebd36-131">How to: Order the Results of a Join Clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="ebd36-132">如何：執行自訂聯結作業</span><span class="sxs-lookup"><span data-stu-id="ebd36-132">How to: Perform Custom Join Operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="ebd36-133">如何：執行群組聯結</span><span class="sxs-lookup"><span data-stu-id="ebd36-133">How to: Perform Grouped Joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="ebd36-134">如何：執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="ebd36-134">How to: Perform Inner Joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="ebd36-135">如何：執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="ebd36-135">How to: Perform Left Outer Joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="ebd36-136">如何：從多個來源填入物件集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ebd36-136">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
