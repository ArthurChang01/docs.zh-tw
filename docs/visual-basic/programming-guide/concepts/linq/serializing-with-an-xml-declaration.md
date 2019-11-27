---
title: 使用 XML 宣告進行序列化
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 96c95b4c94290016684721a194ca31a836a49740
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350626"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="a10ac-102">使用 XML 宣告序列化（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a10ac-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="a10ac-103">這個主題描述如何控制序列化是否產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="a10ac-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="a10ac-104">XML 宣告產生</span><span class="sxs-lookup"><span data-stu-id="a10ac-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="a10ac-105">使用 <xref:System.IO.File> 方法或 <xref:System.IO.TextWriter> 方法序列化為 <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> 會產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="a10ac-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="a10ac-106">當您序列化為 <xref:System.Xml.XmlWriter> 時，寫入器設定 (在 <xref:System.Xml.XmlWriterSettings> 物件中指定) 會決定是否產生 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="a10ac-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="a10ac-107">如果您要使用 `ToString` 方法序列化為字串，所產生的 XML 將不會包含 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="a10ac-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="a10ac-108">使用 XML 宣告進行序列化</span><span class="sxs-lookup"><span data-stu-id="a10ac-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="a10ac-109">下列範例會建立 <xref:System.Xml.Linq.XElement>、將文件儲存為檔案，然後將檔案列印到主控台：</span><span class="sxs-lookup"><span data-stu-id="a10ac-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="a10ac-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a10ac-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="a10ac-111">不使用 XML 宣告序列化</span><span class="sxs-lookup"><span data-stu-id="a10ac-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="a10ac-112">下列範例顯示如何將 <xref:System.Xml.Linq.XElement> 儲存為 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="a10ac-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="a10ac-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a10ac-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a10ac-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="a10ac-114">See also</span></span>

- [<span data-ttu-id="a10ac-115">序列化 XML 樹狀結構（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a10ac-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
