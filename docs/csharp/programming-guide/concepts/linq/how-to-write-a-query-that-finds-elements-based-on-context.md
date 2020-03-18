---
title: 如何編寫基於上下文 （C#） 查找元素的查詢
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 3fc131fdeb8dbf8871bfa455bc54eab0eeca7022
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75348371"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="a43cb-102">如何編寫基於上下文 （C#） 查找元素的查詢</span><span class="sxs-lookup"><span data-stu-id="a43cb-102">How to write a query that finds elements based on context (C#)</span></span>
<span data-ttu-id="a43cb-103">有時候您可能必須撰寫會依其內容選取項目的查詢。</span><span class="sxs-lookup"><span data-stu-id="a43cb-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="a43cb-104">您可能想要依據前面或後面的同層級項目進行篩選。</span><span class="sxs-lookup"><span data-stu-id="a43cb-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="a43cb-105">您可能想要依據子系或祖系項目進行篩選。</span><span class="sxs-lookup"><span data-stu-id="a43cb-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="a43cb-106">您僅能撰寫查詢並使用 `where` 子句中的查詢結果來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="a43cb-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="a43cb-107">如果您必須先依據 Null 進行測試，然後再測試值，在 `let` 子句中進行查詢，然後使用 `where` 子句中的結果會比較方便。</span><span class="sxs-lookup"><span data-stu-id="a43cb-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a43cb-108">範例</span><span class="sxs-lookup"><span data-stu-id="a43cb-108">Example</span></span>  
 <span data-ttu-id="a43cb-109">下列範例會選取緊跟著 `p` 項目後面的所有 `ul` 項目。</span><span class="sxs-lookup"><span data-stu-id="a43cb-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="a43cb-110">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a43cb-110">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="a43cb-111">範例</span><span class="sxs-lookup"><span data-stu-id="a43cb-111">Example</span></span>  
 <span data-ttu-id="a43cb-112">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="a43cb-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a43cb-113">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a43cb-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="a43cb-114">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a43cb-114">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="a43cb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a43cb-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
