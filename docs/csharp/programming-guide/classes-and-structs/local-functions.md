---
title: 區域函式 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 24b7d6f98e331110ddcd971d0d0b21003dbe023d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736845"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="b14a9-102">區域函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b14a9-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="b14a9-103">從 C# 7.0 開始，C# 支援*區域函式*。</span><span class="sxs-lookup"><span data-stu-id="b14a9-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="b14a9-104">區域函式是另一個成員中巢狀型別的私用方法。</span><span class="sxs-lookup"><span data-stu-id="b14a9-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="b14a9-105">它們只可以從其包含成員呼叫。</span><span class="sxs-lookup"><span data-stu-id="b14a9-105">They can only be called from their containing member.</span></span> <span data-ttu-id="b14a9-106">區域函式可以宣告於下列項目中，以及從下列項目呼叫：</span><span class="sxs-lookup"><span data-stu-id="b14a9-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="b14a9-107">方法，特別是迭代器方法和非同步方法</span><span class="sxs-lookup"><span data-stu-id="b14a9-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="b14a9-108">建構函式</span><span class="sxs-lookup"><span data-stu-id="b14a9-108">Constructors</span></span>
- <span data-ttu-id="b14a9-109">屬性存取子</span><span class="sxs-lookup"><span data-stu-id="b14a9-109">Property accessors</span></span>
- <span data-ttu-id="b14a9-110">事件存取子</span><span class="sxs-lookup"><span data-stu-id="b14a9-110">Event accessors</span></span>
- <span data-ttu-id="b14a9-111">匿名方法</span><span class="sxs-lookup"><span data-stu-id="b14a9-111">Anonymous methods</span></span>
- <span data-ttu-id="b14a9-112">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="b14a9-112">Lambda expressions</span></span>
- <span data-ttu-id="b14a9-113">完成項</span><span class="sxs-lookup"><span data-stu-id="b14a9-113">Finalizers</span></span>
- <span data-ttu-id="b14a9-114">其他區域函式</span><span class="sxs-lookup"><span data-stu-id="b14a9-114">Other local functions</span></span>

<span data-ttu-id="b14a9-115">不過，區域函式不能宣告於運算式主體成員內。</span><span class="sxs-lookup"><span data-stu-id="b14a9-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="b14a9-116">在某些情況下，您可以使用 Lambda 運算式來實作區域函式也支援的功能。</span><span class="sxs-lookup"><span data-stu-id="b14a9-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="b14a9-117">如需比較，請參閱[區域函式與 Lambda 運算式的比較](../../local-functions-vs-lambdas.md)。</span><span class="sxs-lookup"><span data-stu-id="b14a9-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="b14a9-118">區域函式讓程式碼的意圖更為清楚。</span><span class="sxs-lookup"><span data-stu-id="b14a9-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="b14a9-119">讀取您程式碼的任何人都可以看到方法無法呼叫，但包含方法除外。</span><span class="sxs-lookup"><span data-stu-id="b14a9-119">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="b14a9-120">對於 Team 專案，它們也可讓另一個開發人員無法從類別或結構的其他位置錯誤地直接呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b14a9-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="b14a9-121">區域函式語法</span><span class="sxs-lookup"><span data-stu-id="b14a9-121">Local function syntax</span></span>

<span data-ttu-id="b14a9-122">區域函式定義為包含成員內的巢狀方法。</span><span class="sxs-lookup"><span data-stu-id="b14a9-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="b14a9-123">其定義具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="b14a9-123">Its definition has the following syntax:</span></span>

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="b14a9-124">區域函式可以使用 [async](../../language-reference/keywords/async.md) 和 [unsafe](../../language-reference/keywords/unsafe.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="b14a9-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="b14a9-125">請注意，在區域函式中可以存取包含成員中所定義的所有區域變數 (包含其方法參數)。</span><span class="sxs-lookup"><span data-stu-id="b14a9-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="b14a9-126">不同于方法定義，區域函式定義不能包含成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="b14a9-126">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="b14a9-127">因為所有區域函式都是私用，所以包含 `private` 這類關鍵字的存取修飾詞會產生編譯器錯誤 CS0106「修飾詞 'private' 對此項目無效」。</span><span class="sxs-lookup"><span data-stu-id="b14a9-127">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

> [!NOTE]
> <span data-ttu-id="b14a9-128">在C# 8.0 之前，區域函式不能包含 `static` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="b14a9-128">Prior to C# 8.0, local functions cannot include the `static` modifier.</span></span> <span data-ttu-id="b14a9-129">包含 `static` 關鍵字會產生編譯器錯誤 CS0106「修飾詞 'static' 對此項目無效」。</span><span class="sxs-lookup"><span data-stu-id="b14a9-129">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="b14a9-130">此外，屬性無法套用至區域函式或其參數和型別參數。</span><span class="sxs-lookup"><span data-stu-id="b14a9-130">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="b14a9-131">下列範例定義名為 `AppendPathSeparator` 的區域函式，而此區域函式是名為 `GetText` 之方法的私用項目：</span><span class="sxs-lookup"><span data-stu-id="b14a9-131">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="b14a9-132">區域函式和例外狀況</span><span class="sxs-lookup"><span data-stu-id="b14a9-132">Local functions and exceptions</span></span>

<span data-ttu-id="b14a9-133">區域函式的其中一個有用功能是它們可以允許立即顯示例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b14a9-133">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="b14a9-134">對於方法迭代器，只有在列舉傳回的序列時，才會顯示例外狀況，而不是擷取迭代器時。</span><span class="sxs-lookup"><span data-stu-id="b14a9-134">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="b14a9-135">對於非同步方法，等候傳回的工作時，會觀察到非同步方法中擲回的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b14a9-135">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="b14a9-136">下列範例定義 `OddSequence` 方法，以列舉所指定範圍之間的奇數。</span><span class="sxs-lookup"><span data-stu-id="b14a9-136">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="b14a9-137">因為它會將一個大於 100 的數字傳遞至 `OddSequence` 列舉值方法，所以此方法會擲回 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="b14a9-137">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="b14a9-138">顯示範例輸出時，只有在您逐一查看數字時，才會顯示例外狀況，而不是擷取列舉值時。</span><span class="sxs-lookup"><span data-stu-id="b14a9-138">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="b14a9-139">相反地，您可以在執行驗證時以及從區域函式傳回迭代器來擷取迭代器之前擲回例外狀況，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b14a9-139">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="b14a9-140">透過類似的方式，可以使用區域函式來處理非同步作業外的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b14a9-140">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="b14a9-141">非同步方法中擲回的例外狀況通常需要您檢查 <xref:System.AggregateException> 的內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b14a9-141">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="b14a9-142">區域函式允許您的程式碼快速失敗，並允許擲回並同步觀察到您的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b14a9-142">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="b14a9-143">下列範例使用名為 `GetMultipleAsync` 的非同步方法暫停指定的秒數，並傳回該秒數之隨機倍數的值。</span><span class="sxs-lookup"><span data-stu-id="b14a9-143">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="b14a9-144">延遲上限是 5 秒；如果值大於 5，則會產生 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="b14a9-144">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="b14a9-145">如下列範例所示，在 `GetMultipleAsync` 方法開始執行之後，會將值 6 傳遞給 `GetMultipleAsync` 方法時所擲回的例外狀況包裝在 <xref:System.AggregateException> 中。</span><span class="sxs-lookup"><span data-stu-id="b14a9-145">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="b14a9-146">與使用方法迭代器執行的作業相同，我們可以從這個範例重構程式碼先進行驗證，再呼叫非同步方法。</span><span class="sxs-lookup"><span data-stu-id="b14a9-146">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="b14a9-147">如下列範例輸出所示，<xref:System.ArgumentOutOfRangeException> 不會包裝在 <xref:System.AggregateException> 中。</span><span class="sxs-lookup"><span data-stu-id="b14a9-147">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="b14a9-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="b14a9-148">See also</span></span>

- [<span data-ttu-id="b14a9-149">方法</span><span class="sxs-lookup"><span data-stu-id="b14a9-149">Methods</span></span>](methods.md)
