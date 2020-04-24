---
title: 使用 XPathNavigator 比對節點
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: f0988c3a112fefc351175de02c790dc25fe6e94a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710683"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="e1cba-102">使用 XPathNavigator 比對節點</span><span class="sxs-lookup"><span data-stu-id="e1cba-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="e1cba-103"><xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法來判斷節點是否符合 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="e1cba-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="e1cba-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法採用 XPath 運算式做為輸入並傳回<xref:System.Boolean>，其指出目前節點是否符合指定的 XPath 運算式或指定之編譯的 <xref:System.Xml.XPath.XPathExpression> 物件。</span><span class="sxs-lookup"><span data-stu-id="e1cba-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="e1cba-105">比對節點</span><span class="sxs-lookup"><span data-stu-id="e1cba-105">Matching Nodes</span></span>  
 <span data-ttu-id="e1cba-106">如果目前節點符合指定的 XPath 運算式，則 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="e1cba-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="e1cba-107">例如，在下面的程式碼範例中，如果目前節點是項目 <xref:System.Xml.XPath.XPathNavigator.Matches%2A>，且項目 `true` 具有屬性 `b`，則 `b` 方法將傳回 `c`。</span><span class="sxs-lookup"><span data-stu-id="e1cba-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1cba-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法不會變更 <xref:System.Xml.XPath.XPathNavigator> 的狀態。</span><span class="sxs-lookup"><span data-stu-id="e1cba-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1cba-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1cba-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="e1cba-110">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="e1cba-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="e1cba-111">使用 XPathNavigator 選取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="e1cba-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="e1cba-112">使用 XPathNavigator 評估 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="e1cba-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="e1cba-113">在 XPath 查詢中辨識的節點型別</span><span class="sxs-lookup"><span data-stu-id="e1cba-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="e1cba-114">XPath 查詢及命名空間</span><span class="sxs-lookup"><span data-stu-id="e1cba-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="e1cba-115">編譯 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="e1cba-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
