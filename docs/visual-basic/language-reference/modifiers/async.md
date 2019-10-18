---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: fc0ae67c0ebc11a0428ffc18c8db103b619e27ec
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524800"
---
# <a name="async-visual-basic"></a><span data-ttu-id="fbd5c-102">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbd5c-102">Async (Visual Basic)</span></span>

<span data-ttu-id="fbd5c-103">@No__t_0 修飾詞表示它修改的方法或[lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)是非同步。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-103">The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="fbd5c-104">這類方法稱為「*非同步方法*」。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-104">Such methods are referred to as *async methods*.</span></span>

<span data-ttu-id="fbd5c-105">非同步方法提供了方便進行可能需要長時間執行之工作的方式，而不需封鎖呼叫端的執行緒。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="fbd5c-106">非同步方法的呼叫端可以繼續其工作，而不需要等待非同步方法完成。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="fbd5c-107">`Async` 和 `Await` 關鍵字是在 Visual Studio 2012 中引入。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="fbd5c-108">如需非同步程式設計的簡介，請參閱[使用 async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="fbd5c-109">以下範例將示範非同步方法的結構。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="fbd5c-110">依照慣例，非同步方法的名稱會以 "Async" 結尾。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-110">By convention, async method names end in "Async."</span></span>

```vb
Public Async Function ExampleMethodAsync() As Task(Of Integer)
    ' . . .

    ' At the Await expression, execution in this method is suspended and,
    ' if AwaitedProcessAsync has not already finished, control returns
    ' to the caller of ExampleMethodAsync. When the awaited task is
    ' completed, this method resumes execution.
    Dim exampleInt As Integer = Await AwaitedProcessAsync()

    ' . . .

    ' The return statement completes the task. Any method that is
    ' awaiting ExampleMethodAsync can now get the integer result.
    Return exampleInt
End Function
```

<span data-ttu-id="fbd5c-111">一般來說，`Async` 關鍵字所修改的方法至少包含一個[Await](../../../visual-basic/language-reference/modifiers/async.md)運算式或語句。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-111">Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement.</span></span> <span data-ttu-id="fbd5c-112">方法會以同步方式執行，直到達到第一個 `Await`，此時它會暫止，直到等候的工作完成。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="fbd5c-113">同時，控制權會返回方法的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="fbd5c-114">如果方法未包含 `Await` 運算式或陳述式，則方法就不會暫止，並且會像同步方法一樣執行。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-114">If the method doesn’t contain an `Await` expression or statement, the method isn’t suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="fbd5c-115">編譯器警告會對未包含 `Await` 的任何非同步方法發出警示，因為這種情況可能表示發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="fbd5c-116">如需詳細資訊，請參閱[編譯器錯誤](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md)。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-116">For more information, see the [compiler error](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).</span></span>

<span data-ttu-id="fbd5c-117">`Async` 關鍵字是未保留的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="fbd5c-118">它是修飾方法或 Lambda 運算式時的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="fbd5c-119">在所有其他內容中，它會解譯為識別項。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-119">In all other contexts, it is interpreted as an identifier.</span></span>

## <a name="return-types"></a><span data-ttu-id="fbd5c-120">傳回型別</span><span class="sxs-lookup"><span data-stu-id="fbd5c-120">Return Types</span></span>

<span data-ttu-id="fbd5c-121">非同步方法可以是[Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)程式，或是傳回類型為 <xref:System.Threading.Tasks.Task> 或[<xref:System.Threading.Tasks.Task%601> 的函](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)式程式。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-121">An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="fbd5c-122">方法無法宣告任何[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)參數。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-122">The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="fbd5c-123">如果方法的[return](../../../visual-basic/language-reference/statements/return-statement.md)語句有類型為 TResult 的運算元，您可以為非同步方法的傳回類型指定 `Task(Of TResult)`。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="fbd5c-124">如果方法完成時未傳回任何有意義的值，則使用 `Task`。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="fbd5c-125">也就是說，呼叫方法會傳回 `Task`，但是當 `Task` 完成時，任何等候 `Await` 的 `Task` 陳述式都不會產生結果值。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>

<span data-ttu-id="fbd5c-126">Async 副程式主要是用來定義需要 `Sub` 程序的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="fbd5c-127">非同步副程式的呼叫端無法等候它，而且無法攔截方法擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="fbd5c-128">如需詳細資訊和範例，請參閱[非同步方法的傳回型別](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-128">For more information and examples, see [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="fbd5c-129">範例</span><span class="sxs-lookup"><span data-stu-id="fbd5c-129">Example</span></span>

<span data-ttu-id="fbd5c-130">下列範例將示範非同步事件處理常式、非同步 Lambda 運算式及非同步方法。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="fbd5c-131">如需使用這些元素的完整範例，請參閱[逐步解說：使用 Async 和 Await 存取 Web](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="fbd5c-132">您可以從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下載逐步解說程式碼。</span><span class="sxs-lookup"><span data-stu-id="fbd5c-132">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

```vb
' An event handler must be a Sub procedure.
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click
    textBox1.Clear()
    ' SumPageSizesAsync is a method that returns a Task.
    Await SumPageSizesAsync()
    textBox1.Text = vbCrLf & "Control returned to button1_Click."
End Sub

' The following async lambda expression creates an equivalent anonymous
' event handler.
AddHandler button1.Click, Async Sub(sender, e)
                              textBox1.Clear()
                              ' SumPageSizesAsync is a method that returns a Task.
                              Await SumPageSizesAsync()
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."
                          End Sub

' The following async method returns a Task(Of T).
' A typical call awaits the Byte array result:
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

    ' The downloaded resource ends up in the variable named content.
    Dim content = New MemoryStream()

    ' Initialize an HttpWebRequest for the current URL.
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

    ' Send the request to the Internet resource and wait for
    ' the response.
    Using response As WebResponse = Await webReq.GetResponseAsync()
        ' Get the data stream that is associated with the specified URL.
        Using responseStream As Stream = response.GetResponseStream()
            ' Read the bytes in responseStream and copy them to content.
            ' CopyToAsync returns a Task, not a Task<T>.
            Await responseStream.CopyToAsync(content)
        End Using
    End Using

    ' Return the result as a byte array.
    Return content.ToArray()
End Function
```

## <a name="see-also"></a><span data-ttu-id="fbd5c-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbd5c-133">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="fbd5c-134">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="fbd5c-134">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="fbd5c-135">使用 Async 和 Await 進行非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="fbd5c-135">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="fbd5c-136">逐步解說：使用 Async 和 Await 存取 Web</span><span class="sxs-lookup"><span data-stu-id="fbd5c-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
