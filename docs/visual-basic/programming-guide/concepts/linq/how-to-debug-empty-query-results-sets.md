---
title: 如何：偵錯空白查詢結果集
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 21c161a702338c0c6943fa09212deaea7fdd72f9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353067"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="cf0be-102">How to: Debug Empty Query Results Sets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf0be-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>

<span data-ttu-id="cf0be-103">查詢 XML 時所遇到的其中一個最常見的問題是，如果 XML 樹狀結構有預設的命名空間，即使 XML 不在命名空間中，開發人員有時候還是會撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="cf0be-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="cf0be-104">本主題中的第一組範例會顯示將 XML 載入預設命名空間而且查詢錯誤的常見方式。</span><span class="sxs-lookup"><span data-stu-id="cf0be-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>

<span data-ttu-id="cf0be-105">第二組範例顯示所需的修正，讓您可以在命名空間中查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="cf0be-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="cf0be-106">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cf0be-106">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf0be-107">範例</span><span class="sxs-lookup"><span data-stu-id="cf0be-107">Example</span></span>

<span data-ttu-id="cf0be-108">此範例顯示 XML 在命名空間中的建立，以及傳回空結果集的查詢。</span><span class="sxs-lookup"><span data-stu-id="cf0be-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

<span data-ttu-id="cf0be-109">此範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="cf0be-109">This example produces the following result:</span></span>

```console
Result set follows:
End of result set
```

## <a name="example"></a><span data-ttu-id="cf0be-110">範例</span><span class="sxs-lookup"><span data-stu-id="cf0be-110">Example</span></span>

<span data-ttu-id="cf0be-111">此範例顯示 XML 在命名空間中的建立，以及編碼正確的查詢。</span><span class="sxs-lookup"><span data-stu-id="cf0be-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>

<span data-ttu-id="cf0be-112">The solution is to declare and initialize a global default namespace.</span><span class="sxs-lookup"><span data-stu-id="cf0be-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="cf0be-113">這會將所有 XML 屬性放在預設的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="cf0be-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="cf0be-114">此範例不需要其他任何修改，就可以讓它正常運作。</span><span class="sxs-lookup"><span data-stu-id="cf0be-114">No other modifications are required to the example to make it work properly.</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="cf0be-115">此範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="cf0be-115">This example produces the following result:</span></span>

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="cf0be-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf0be-116">See also</span></span>

- [<span data-ttu-id="cf0be-117">Basic Queries (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf0be-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
