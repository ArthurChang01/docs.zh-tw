---
title: 如何查找兩個位置路徑（XPath-LINQ 到 XML）（C#）的聯合
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 17a3310f367cb68b3b80b1a3f30af40428f6d2c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141217"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>如何查找兩個位置路徑（XPath-LINQ 到 XML）（C#）的聯合
XPath 可讓您尋找兩個 XPath 位置路徑結果的等位。  
  
 XPath 運算式為：  
  
 `//Category|//Price`  
  
 您可以使用 <xref:System.Linq.Enumerable.Concat%2A> 標準查詢運算子，達到相同的結果。  
  
## <a name="example"></a>範例  
 此範例會尋找所有 `Category` 項目與所有 `Price` 項目，然後將它們串連為單一集合。 請注意，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢會呼叫 <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> 來排列結果。 XPath 運算式評估的結果也是以文件的順序排列。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：數值資料 (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md)。  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 這個範例會產生下列輸出：  
  
```output  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  