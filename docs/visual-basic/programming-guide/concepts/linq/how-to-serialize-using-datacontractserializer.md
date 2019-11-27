---
title: 如何：使用 DataContractSerializer 進行序列化
ms.date: 07/20/2015
ms.assetid: ecaea518-8a0f-4249-b4e5-9b3fb0cdd8ad
ms.openlocfilehash: 6c4142673cc374fbc6202e5806d1e9016cc81893
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352365"
---
# <a name="how-to-serialize-using-datacontractserializer-visual-basic"></a><span data-ttu-id="05d81-102">如何：使用 DataContractSerializer 進行序列化（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="05d81-102">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>
<span data-ttu-id="05d81-103">本主題顯示的範例會使用 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化與還原序列化。</span><span class="sxs-lookup"><span data-stu-id="05d81-103">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05d81-104">範例</span><span class="sxs-lookup"><span data-stu-id="05d81-104">Example</span></span>  
 <span data-ttu-id="05d81-105">下列範例會建立多個包含 <xref:System.Xml.Linq.XElement> 物件的物件。</span><span class="sxs-lookup"><span data-stu-id="05d81-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="05d81-106">接著，它會將這些物件序列化為文字檔，然後從文字檔還原序列化。</span><span class="sxs-lookup"><span data-stu-id="05d81-106">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Linq  
Imports System.IO  
Imports System.Runtime.Serialization  
  
Public Class XLinqTest  
    Shared Sub Main()  
        Test(Of XElement)(CreateXElement())  
        Test(Of XElementContainer)(New XElementContainer())  
        Test(Of XElementNullContainer)(New XElementNullContainer())  
    End Sub  
  
    Public Shared Sub Test(Of T)(ByRef obj)  
        Dim s As DataContractSerializer = New DataContractSerializer(GetType(T))  
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Create)  
            Console.WriteLine("Testing for type: {0}", GetType(T))  
            s.WriteObject(fs, obj)  
        End Using  
  
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Open)  
            Dim s2 As Object = s.ReadObject(fs)  
            If s2 Is Nothing Then  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)")  
            Else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType())  
            End If  
        End Using  
    End Sub  
  
    Public Shared Function CreateXElement() As XElement  
        Return New XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"))  
    End Function  
End Class  
  
<DataContract()> _  
Public Class XElementContainer  
    <DataMember()> _  
    Public member As XElement  
  
    Public Sub XElementContainer()  
        member = XLinqTest.CreateXElement()  
    End Sub  
End Class  
  
<DataContract()> _  
Public Class XElementNullContainer  
    <DataMember()> _  
    Public member As XElement  
  
    Public Sub XElementNullContainer()  
        member = Nothing  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="05d81-107">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="05d81-107">This example produces the following output:</span></span>  
  
```console  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="05d81-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05d81-108">See also</span></span>

- [<span data-ttu-id="05d81-109">序列化包含 System.xml.linq.xelement> 物件的物件圖形（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="05d81-109">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)
