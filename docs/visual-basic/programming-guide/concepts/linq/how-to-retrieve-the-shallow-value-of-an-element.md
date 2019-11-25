---
title: 如何：擷取項目的淺層值
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 7449d6d1230313aef6005284270370bb9d243a3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346917"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a>How to: Retrieve the Shallow Value of an Element (Visual Basic)

本主題說明如何取得項目的表層值。 表層值僅是特定項目的值。與深層值不同的是，深層值包含了由所有子代項目連結成單一字串的值。

當您使用轉換或 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性，您擷取的是深層值。 若要擷取表層值，您可以使用 `ShallowValue` 擴充方法，如下列範例所示。 當您想要根據項目的內容進行選取時，擷取表層值就非常有用。

下列範例會宣告擷取項目表層值的擴充方法。 接著會在查詢中使用此擴充方法，將所有包含計算值的項目列出。

## <a name="example"></a>範例

下列文字檔 Report.xml 是此範例的原始檔。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Report>
  <Section>
    <Heading>
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>
      <Column Name="Name">=Customer.Name.Heading</Column>
    </Heading>
    <Detail>
      <Column Name="CustomerId">=Customer.CustomerId</Column>
      <Column Name="Name">=Customer.Name</Column>
    </Detail>
  </Section>
</Report>
```

```vb
Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function ShallowValue(ByVal xe As XElement)
        Return xe _
               .Nodes() _
               .OfType(Of XText)() _
               .Aggregate(New StringBuilder(), _
                              Function(s, c) s.Append(c), _
                              Function(s) s.ToString())
    End Function

    Sub Main()
        Dim root As XElement = XElement.Load("Report.xml")

        Dim query As IEnumerable(Of XElement) = _
            From el In root.Descendants() _
            Where (el.ShallowValue().StartsWith("=")) _
            Select el

        For Each q As XElement In query
            Console.WriteLine("{0}{1}{2}", _
                q.Name.ToString().PadRight(8), _
                q.Attribute("Name").ToString().PadRight(20), _
                q.ShallowValue())
        Next
    End Sub
End Module
```

這個範例會產生下列輸出：

```console
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a>請參閱

- [LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
