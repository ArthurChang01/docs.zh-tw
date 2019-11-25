---
title: 如何尋找具有特定名稱之同級的屬性（XPath-LINQ to XML）（C#）
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 788945232874ed5c1ba9a8a43c10eaf012320cbb
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141137"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="613ad-102">如何尋找具有特定名稱之同級的屬性（XPath-LINQ to XML）（C#）</span><span class="sxs-lookup"><span data-stu-id="613ad-102">How to find attributes of siblings with a specific name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="613ad-103">本主題顯示如何尋找內容節點之同層級的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="613ad-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="613ad-104">在集合中，只會傳回具有特定名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="613ad-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="613ad-105">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="613ad-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="613ad-106">範例</span><span class="sxs-lookup"><span data-stu-id="613ad-106">Example</span></span>  
 <span data-ttu-id="613ad-107">此範例會先尋找 `Book` 項目，接著尋找名稱為 `Book` 的所有同層級項目，然後尋找名稱為 `id` 的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="613ad-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="613ad-108">結果為屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="613ad-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="613ad-109">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="613ad-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="613ad-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="613ad-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  