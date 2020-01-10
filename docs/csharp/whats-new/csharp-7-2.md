---
title: C# 7.2 的新功能
description: C# 7.2 新功能的概觀。
ms.date: 08/16/2017
ms.openlocfilehash: 7febefb81bbea6f24690adb05488ad6a18bbf552
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694591"
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="8aa93-103">C# 7.2 的新功能</span><span class="sxs-lookup"><span data-stu-id="8aa93-103">What's new in C# 7.2</span></span>

<span data-ttu-id="8aa93-104">C# 7.2 是另一個小數點版本，其中新增了一些實用的功能。</span><span class="sxs-lookup"><span data-stu-id="8aa93-104">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="8aa93-105">此版本的主題之一是能夠避免不必要的複製或配置，讓實質型別作業能夠更有效率。</span><span class="sxs-lookup"><span data-stu-id="8aa93-105">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span>

<span data-ttu-id="8aa93-106">其餘功能則無足輕重。</span><span class="sxs-lookup"><span data-stu-id="8aa93-106">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="8aa93-107">C# 7.2 使用了[語言版本選取項目](../language-reference/configure-language-version.md)組態元素來選取編譯器語言版本。</span><span class="sxs-lookup"><span data-stu-id="8aa93-107">C# 7.2 uses the [language version selection](../language-reference/configure-language-version.md) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="8aa93-108">此版本的新款語言功能包括：</span><span class="sxs-lookup"><span data-stu-id="8aa93-108">The new language features in this release are:</span></span>

- [<span data-ttu-id="8aa93-109">撰寫安全、有效率之程式碼的技巧</span><span class="sxs-lookup"><span data-stu-id="8aa93-109">Techniques for writing safe efficient code</span></span>](#safe-efficient-code-enhancements)
  - <span data-ttu-id="8aa93-110">這是語法改進功能組合，這些改進功能可讓您使用參考語意來處理實值型別。</span><span class="sxs-lookup"><span data-stu-id="8aa93-110">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
- [<span data-ttu-id="8aa93-111">非後置具名引數</span><span class="sxs-lookup"><span data-stu-id="8aa93-111">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="8aa93-112">具名引數之後可以接著位置引數。</span><span class="sxs-lookup"><span data-stu-id="8aa93-112">Named arguments can be followed by positional arguments.</span></span>
- [<span data-ttu-id="8aa93-113">數值常值中的前置底線</span><span class="sxs-lookup"><span data-stu-id="8aa93-113">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="8aa93-114">數值常值的任何列印數字之前，現都可加上前置底線。</span><span class="sxs-lookup"><span data-stu-id="8aa93-114">Numeric literals can now have leading underscores before any printed digits.</span></span>
- [<span data-ttu-id="8aa93-115">`private protected` 存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="8aa93-115">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="8aa93-116">您可利用 `private protected` 存取修飾詞，存取相同組件中的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="8aa93-116">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>
- [<span data-ttu-id="8aa93-117">`ref` 條件運算式</span><span class="sxs-lookup"><span data-stu-id="8aa93-117">Conditional `ref` expressions</span></span>](#conditional-ref-expressions)
  - <span data-ttu-id="8aa93-118">條件運算式 (`?:`) 的結果現在可以是參考。</span><span class="sxs-lookup"><span data-stu-id="8aa93-118">The result of a conditional expression (`?:`) can now be a reference.</span></span>

<span data-ttu-id="8aa93-119">此文章的其餘部分將概述各個功能。</span><span class="sxs-lookup"><span data-stu-id="8aa93-119">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="8aa93-120">您將了解每項功能背後的原因。</span><span class="sxs-lookup"><span data-stu-id="8aa93-120">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="8aa93-121">您將了解語法。</span><span class="sxs-lookup"><span data-stu-id="8aa93-121">You'll learn the syntax.</span></span> <span data-ttu-id="8aa93-122">您可以使用 `dotnet try` 全域工具，在您的環境中探索這些功能：</span><span class="sxs-lookup"><span data-stu-id="8aa93-122">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="8aa93-123">安裝 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全域工具。</span><span class="sxs-lookup"><span data-stu-id="8aa93-123">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="8aa93-124">複製 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="8aa93-124">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="8aa93-125">將目前目錄設為 *try-samples* 存放庫的 *csharp7* 子目錄。</span><span class="sxs-lookup"><span data-stu-id="8aa93-125">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="8aa93-126">執行 `dotnet try`。</span><span class="sxs-lookup"><span data-stu-id="8aa93-126">Run `dotnet try`.</span></span>

## <a name="safe-efficient-code-enhancements"></a><span data-ttu-id="8aa93-127">安全、有效率的程式碼增強功能</span><span class="sxs-lookup"><span data-stu-id="8aa93-127">Safe efficient code enhancements</span></span>

<span data-ttu-id="8aa93-128">您可利用 7.2 版新加入的語言功能，於使用參考語意時運用實值型別。</span><span class="sxs-lookup"><span data-stu-id="8aa93-128">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="8aa93-129">這些功能之設計目的是加強加效能，方法是將複製實質型別最小化，而不產生與使用參考型別相關的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="8aa93-129">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="8aa93-130">功能包括：</span><span class="sxs-lookup"><span data-stu-id="8aa93-130">The features include:</span></span>

- <span data-ttu-id="8aa93-131">參數上的 `in` 修飾詞，可指定引數將以傳址方式傳遞，但不受呼叫的方法修改。</span><span class="sxs-lookup"><span data-stu-id="8aa93-131">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span> <span data-ttu-id="8aa93-132">將 `in` 修飾詞新增至引數是[來源相容變更](version-update-considerations.md#source-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="8aa93-132">Adding the `in` modifier to an argument is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span>
- <span data-ttu-id="8aa93-133">方法上 `ref readonly` 修飾詞的傳回內容，可指示方法要以傳址方式傳回其值，但不允許寫入該物件。</span><span class="sxs-lookup"><span data-stu-id="8aa93-133">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span> <span data-ttu-id="8aa93-134">如果將傳回項目指派給值。則新增 `ref readonly` 修飾詞是[來源相容變更](version-update-considerations.md#source-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="8aa93-134">Adding the `ref readonly` modifier is a [source compatible change](version-update-considerations.md#source-compatible-changes), if the return is assigned to a value.</span></span> <span data-ttu-id="8aa93-135">將 `readonly` 修飾詞新增至現有 `ref` 傳回陳述式是[不相容的變更](version-update-considerations.md#incompatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="8aa93-135">Adding the `readonly` modifier to an existing `ref` return statement is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="8aa93-136">需要呼叫端更新 `ref` 本機變數的宣告，以包含 `readonly` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="8aa93-136">It requires callers to update the declaration of `ref` local variables to include the `readonly` modifier.</span></span>
- <span data-ttu-id="8aa93-137">`readonly struct` 宣告，可指示結構會固定，且應以 `in` 參數傳遞至其成員方法。</span><span class="sxs-lookup"><span data-stu-id="8aa93-137">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span> <span data-ttu-id="8aa93-138">將 `readonly` 修飾詞新增至現有 struct 宣告是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="8aa93-138">Adding the `readonly` modifier to an existing struct declaration is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>
- <span data-ttu-id="8aa93-139">`ref struct` 宣告，可指示結構類型會直接存取受控記憶體，且一律會配置堆疊。</span><span class="sxs-lookup"><span data-stu-id="8aa93-139">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span> <span data-ttu-id="8aa93-140">將 `ref` 修飾詞新增至現有 `struct` 宣告是[不相容的變更](version-update-considerations.md#incompatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="8aa93-140">Adding the `ref` modifier to an existing `struct` declaration is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="8aa93-141">`ref struct` 不能是類別的成員，或用於可能會在堆積上配置的其他位置。</span><span class="sxs-lookup"><span data-stu-id="8aa93-141">A `ref struct` cannot be a member of a class or used in other locations where it may be allocated on the heap.</span></span>

<span data-ttu-id="8aa93-142">您可以在[撰寫安全、有效率的程式碼](../write-safe-efficient-code.md)深入了解這些變更。</span><span class="sxs-lookup"><span data-stu-id="8aa93-142">You can read more about all these changes in [Write safe efficient code](../write-safe-efficient-code.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="8aa93-143">無後置具名引數</span><span class="sxs-lookup"><span data-stu-id="8aa93-143">Non-trailing named arguments</span></span>

<span data-ttu-id="8aa93-144">當具名引數位於正確位置時，方法呼叫現在可以在位置引數前面使用具名引數。</span><span class="sxs-lookup"><span data-stu-id="8aa93-144">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="8aa93-145">如需詳細資訊，請參閱[具名和選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="8aa93-145">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="8aa93-146">數值常值中的前置底線</span><span class="sxs-lookup"><span data-stu-id="8aa93-146">Leading underscores in numeric literals</span></span>

<span data-ttu-id="8aa93-147">C# 7.0 中的數字分隔符號之實作支援，並不允許將 `_` 作為常值的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="8aa93-147">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="8aa93-148">十六進位與二進位數值常值現在可以使用 `_` 開頭。</span><span class="sxs-lookup"><span data-stu-id="8aa93-148">Hex and binary numeric literals may now begin with an `_`.</span></span>

<span data-ttu-id="8aa93-149">例如：</span><span class="sxs-lookup"><span data-stu-id="8aa93-149">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a><span data-ttu-id="8aa93-150">*private protected* 存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="8aa93-150">*private protected* access modifier</span></span>

<span data-ttu-id="8aa93-151">新的複合存取修飾詞：`private protected` 指出可藉由包含類別或在相同組件中宣告的衍生類別來存取成員。</span><span class="sxs-lookup"><span data-stu-id="8aa93-151">A new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="8aa93-152">`protected internal` 允許衍生類別或相同組件中的類別進行存取，而 `private protected` 則限制在相同組件中宣告的衍生類型進行存取。</span><span class="sxs-lookup"><span data-stu-id="8aa93-152">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="8aa93-153">如需詳細資訊，請參閱語言參考中的[存取修飾詞](../language-reference/keywords/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="8aa93-153">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

## <a name="conditional-ref-expressions"></a><span data-ttu-id="8aa93-154">`ref` 條件運算式</span><span class="sxs-lookup"><span data-stu-id="8aa93-154">Conditional `ref` expressions</span></span>

<span data-ttu-id="8aa93-155">最後，條件運算式可能會產生參考結果，而不是實值結果。</span><span class="sxs-lookup"><span data-stu-id="8aa93-155">Finally, the conditional expression may produce a ref result instead of a value result.</span></span> <span data-ttu-id="8aa93-156">例如，您可以撰寫下列程式碼，在兩個陣列的其中一個上，擷取對第一個元素的參考：</span><span class="sxs-lookup"><span data-stu-id="8aa93-156">For example, you would write the following to retrieve a reference to the first element in one of two arrays:</span></span>

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

<span data-ttu-id="8aa93-157">變數 `r` 是 `arr` 或 `otherArr` 中對第一個值的參考。</span><span class="sxs-lookup"><span data-stu-id="8aa93-157">The variable `r` is a reference to the first value in either `arr` or `otherArr`.</span></span>

<span data-ttu-id="8aa93-158">如需詳細資訊，請參閱語言參考中的[條件運算子 (?:)](../language-reference/operators/conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="8aa93-158">For more information, see [conditional operator (?:)](../language-reference/operators/conditional-operator.md) in the language reference.</span></span>
