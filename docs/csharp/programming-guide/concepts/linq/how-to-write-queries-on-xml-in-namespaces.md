---
title: 如何在命名空間中撰寫 XML 的查詢C#（）
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337366"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>如何在命名空間中撰寫 XML 的查詢C#（）
若要撰寫命名空間 (Namespace) 中的 XML 查詢，您必須使用具有正確命名空間的 <xref:System.Xml.Linq.XName> 物件。  
  
 若為 C#，最常見的方法是使用包含 URI 的字串初始化 <xref:System.Xml.Linq.XNamespace>，然後使用加法運算子多載結合命名空間與區域名稱。  
  
 本主題中的第一組範例會示範如何在預設命名空間中建立 XML 樹狀結構。 第二組範例則示範如何在具有前置詞的命名空間中建立 XML 樹狀結構。  
  
## <a name="example"></a>範例  
 下列範例會建立位於預設命名空間中的 XML 樹狀。 接著，它會擷取項目的集合。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 這個範例會產生下列輸出：  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>範例  
 在 C# 中，不論您要針對使用具有前置詞之命名空間的 XML 樹狀，還是針對具有預設命名空間的 XML 樹狀撰寫查詢，查詢的撰寫方式都相同。  
  
 下列範例會建立位於命名空間中，具有前置詞的 XML 樹狀。 接著，它會擷取項目的集合。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 這個範例會產生下列輸出：  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>請參閱

- [命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
