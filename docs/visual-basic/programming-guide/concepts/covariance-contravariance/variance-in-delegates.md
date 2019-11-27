---
title: 委派中的變異數
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 11146bc4a60f55fc0373f0b5dfa5d44dcf748a5b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349006"
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="5bb40-102">委派中的變異數（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="5bb40-102">Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="5bb40-103">.NET Framework 3.5 引進了變異數支援，以便在和 Visual Basic 中C#的所有委派中，將方法簽章與委派類型相符。</span><span class="sxs-lookup"><span data-stu-id="5bb40-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="5bb40-104">這表示您可以指派給委派的不只是具有相符簽章的方法，也可以是會傳回更多衍生型別 (共變數) 的方法，或接受衍生型別 (反變數) 比委派型別指定少的參數的方法。</span><span class="sxs-lookup"><span data-stu-id="5bb40-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="5bb40-105">這包括泛型和非泛型委派。</span><span class="sxs-lookup"><span data-stu-id="5bb40-105">This includes both generic and non-generic delegates.</span></span>

<span data-ttu-id="5bb40-106">例如，請考慮下列程式碼，有兩個類別和兩個委派︰泛型和非泛型。</span><span class="sxs-lookup"><span data-stu-id="5bb40-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

<span data-ttu-id="5bb40-107">當您建立 `SampleDelegate` 或 `SampleDelegate(Of A, R)` 型別的委派時，您可以指派下列任一方法給這些委派。</span><span class="sxs-lookup"><span data-stu-id="5bb40-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>

```vb
' Matching signature.
Public Shared Function ASecondRFirst(
    ByVal second As Second) As First
    Return New First()
End Function

' The return type is more derived.
Public Shared Function ASecondRSecond(
    ByVal second As Second) As Second
    Return New Second()
End Function

' The argument type is less derived.
Public Shared Function AFirstRFirst(
    ByVal first As First) As First
    Return New First()
End Function

' The return type is more derived
' and the argument type is less derived.
Public Shared Function AFirstRSecond(
    ByVal first As First) As Second
    Return New Second()
End Function
```

<span data-ttu-id="5bb40-108">下列程式碼範例會示範方法簽章與委派型別之間的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="5bb40-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>

```vb
' Assigning a method with a matching signature
' to a non-generic delegate. No conversion is necessary.
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a non-generic delegate.
' The implicit conversion is used.
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond

' Assigning a method with a matching signature to a generic delegate.
' No conversion is necessary.
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a generic delegate.
' The implicit conversion is used.
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond
```

<span data-ttu-id="5bb40-109">如需更多範例，請參閱[在委派中使用變異數（Visual Basic）](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)和[針對 Func 和 Action 泛型委派使用變異數（Visual Basic）](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="5bb40-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="5bb40-110">泛型型別參數中的差異</span><span class="sxs-lookup"><span data-stu-id="5bb40-110">Variance in Generic Type Parameters</span></span>

<span data-ttu-id="5bb40-111">在 .NET Framework 4 和更新版本中，您可以啟用委派之間的隱含轉換，讓具有泛型型別參數所指定之不同類型的泛型委派可以指派給彼此，如果類型是由所需的彼此繼承變化.</span><span class="sxs-lookup"><span data-stu-id="5bb40-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>

<span data-ttu-id="5bb40-112">若要啟用隱含轉換，您必須使用 `in` 或 `out` 關鍵字，明確宣告委派中的泛型參數為 Covariant 或 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="5bb40-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>

<span data-ttu-id="5bb40-113">下列程式碼範例示範如何建立具有 Covariant 泛型型別參數的委派。</span><span class="sxs-lookup"><span data-stu-id="5bb40-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>

```vb
' Type T is declared covariant by using the out keyword.
Public Delegate Function SampleGenericDelegate(Of Out T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "
    ' You can assign delegates to each other,
    ' because the type T is declared covariant.
    Dim dObject As SampleGenericDelegate(Of Object) = dString
End Sub
```

<span data-ttu-id="5bb40-114">如果您使用唯一的差異支援來比對方法簽章與委派型別，請不要使用 `in` 和 `out` 關鍵字，因為您會發現，有時候您會使用相同的 lambda 運算式或方法具現化委派，但無法將一個委派指派給另一個。</span><span class="sxs-lookup"><span data-stu-id="5bb40-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>

<span data-ttu-id="5bb40-115">在下列程式碼範例中，`SampleGenericDelegate(Of String)` 無法明確轉換成 `SampleGenericDelegate(Of Object)`，但 `String` 會繼承 `Object`。</span><span class="sxs-lookup"><span data-stu-id="5bb40-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="5bb40-116">您可以使用 `T` 關鍵字標記泛型參數 `out`，修正這個問題。</span><span class="sxs-lookup"><span data-stu-id="5bb40-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>

```vb
Public Delegate Function SampleGenericDelegate(Of T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "

    ' You can assign the dObject delegate
    ' to the same lambda expression as dString delegate
    ' because of the variance support for
    ' matching method signatures with delegate types.
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "

    ' The following statement generates a compiler error
    ' because the generic type T is not marked as covariant.
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString

End Sub
```

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="5bb40-117">.NET Framework 中具有 Variant 型別參數的泛型委派</span><span class="sxs-lookup"><span data-stu-id="5bb40-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>

<span data-ttu-id="5bb40-118">.NET Framework 4 推出差異支援，適用於數個現有泛型委派中的泛型型別參數：</span><span class="sxs-lookup"><span data-stu-id="5bb40-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>

- <span data-ttu-id="5bb40-119">`Action` 命名空間中的 <xref:System> 委派，例如 <xref:System.Action%601> 和 <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="5bb40-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>

- <span data-ttu-id="5bb40-120">`Func` 命名空間中的 <xref:System> 委派，例如 <xref:System.Func%601> 和 <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="5bb40-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>

- <span data-ttu-id="5bb40-121"><xref:System.Predicate%601> 委派</span><span class="sxs-lookup"><span data-stu-id="5bb40-121">The <xref:System.Predicate%601> delegate</span></span>

- <span data-ttu-id="5bb40-122"><xref:System.Comparison%601> 委派</span><span class="sxs-lookup"><span data-stu-id="5bb40-122">The <xref:System.Comparison%601> delegate</span></span>

- <span data-ttu-id="5bb40-123"><xref:System.Converter%602> 委派</span><span class="sxs-lookup"><span data-stu-id="5bb40-123">The <xref:System.Converter%602> delegate</span></span>

<span data-ttu-id="5bb40-124">如需詳細資訊和範例，請參閱針對[Func 和 Action 泛型委派使用變異數（Visual Basic）](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="5bb40-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="5bb40-125">宣告泛型委派中的 Variant 型別參數</span><span class="sxs-lookup"><span data-stu-id="5bb40-125">Declaring Variant Type Parameters in Generic Delegates</span></span>

<span data-ttu-id="5bb40-126">如果泛型委派具有 Covariant 或 Contravariant 泛型型別參數，它可以稱之為「Variant 泛型委派」。</span><span class="sxs-lookup"><span data-stu-id="5bb40-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>

<span data-ttu-id="5bb40-127">您可以使用 `out` 關鍵字將泛型委派中的泛型型別參數宣告為 Covariant。</span><span class="sxs-lookup"><span data-stu-id="5bb40-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="5bb40-128">Covariant 型別僅可用為方法傳回型別，不能用為方法引數的型別。</span><span class="sxs-lookup"><span data-stu-id="5bb40-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="5bb40-129">以下程式碼範例會示範如何宣告 Covariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="5bb40-129">The following code example shows how to declare a covariant generic delegate.</span></span>

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

<span data-ttu-id="5bb40-130">您可以使用 `in` 關鍵字將泛型委派中的泛型型別參數宣告為 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="5bb40-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="5bb40-131">Contravariant 型別僅可用為方法引數的型別，不能用為方法傳回型別。</span><span class="sxs-lookup"><span data-stu-id="5bb40-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="5bb40-132">以下程式碼範例會示範如何宣告 Contravariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="5bb40-132">The following code example shows how to declare a contravariant generic delegate.</span></span>

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> <span data-ttu-id="5bb40-133">Visual Basic 中的 `ByRef` 參數不能標記為 variant。</span><span class="sxs-lookup"><span data-stu-id="5bb40-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>

<span data-ttu-id="5bb40-134">您也可以支援相同委派中不同型別參數的差異和共變數。</span><span class="sxs-lookup"><span data-stu-id="5bb40-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="5bb40-135">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="5bb40-135">This is shown in the following example.</span></span>

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="5bb40-136">具現化及叫用 Variant 泛型委派</span><span class="sxs-lookup"><span data-stu-id="5bb40-136">Instantiating and Invoking Variant Generic Delegates</span></span>

<span data-ttu-id="5bb40-137">您可以具現化及叫用 Variant 委派，一如您具現化及叫用非變異委派。</span><span class="sxs-lookup"><span data-stu-id="5bb40-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="5bb40-138">在下例中，委派是由 lambda 運算式具現化。</span><span class="sxs-lookup"><span data-stu-id="5bb40-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="5bb40-139">結合 Variant 泛型委派</span><span class="sxs-lookup"><span data-stu-id="5bb40-139">Combining Variant Generic Delegates</span></span>

<span data-ttu-id="5bb40-140">您不應該組合 Variant 委派。</span><span class="sxs-lookup"><span data-stu-id="5bb40-140">You should not combine variant delegates.</span></span> <span data-ttu-id="5bb40-141"><xref:System.Delegate.Combine%2A> 方法不支援 Variant 委派轉換，且委派的類型必須完全一致。</span><span class="sxs-lookup"><span data-stu-id="5bb40-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="5bb40-142">當您使用 <xref:System.Delegate.Combine%2A> 方法（在和 Visual Basic 中C# ）或使用 `+` 運算子（在中C#）結合委派時，這可能會導致執行時間例外狀況，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="5bb40-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="5bb40-143">實值型別和參考型別的泛型型別參數中的差異</span><span class="sxs-lookup"><span data-stu-id="5bb40-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>

<span data-ttu-id="5bb40-144">僅參考型別支援泛型型別參數的差異。</span><span class="sxs-lookup"><span data-stu-id="5bb40-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="5bb40-145">例如，`DVariant(Of Int)`無法隱含地轉換成 `DVariant(Of Object)` 或 `DVariant(Of Long)`，因為整數是實值型別。</span><span class="sxs-lookup"><span data-stu-id="5bb40-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>

<span data-ttu-id="5bb40-146">下例示範實值型別不支援的泛型型別參數的差異。</span><span class="sxs-lookup"><span data-stu-id="5bb40-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>

```vb
' The type T is covariant.
Public Delegate Function DVariant(Of Out T)() As T
' The type T is invariant.
Public Delegate Function DInvariant(Of T)() As T
Sub Test()
    Dim i As Integer = 0
    Dim dInt As DInvariant(Of Integer) = Function() i
    Dim dVariantInt As DVariant(Of Integer) = Function() i

    ' All of the following statements generate a compiler error
    ' because type variance in generic parameters is not supported
    ' for value types, even if generic type parameters are declared variant.
    ' Dim dObject As DInvariant(Of Object) = dInt
    ' Dim dLong As DInvariant(Of Long) = dInt
    ' Dim dVariantObject As DInvariant(Of Object) = dInt
    ' Dim dVariantLong As DInvariant(Of Long) = dInt
End Sub
```

## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="5bb40-147">Visual Basic 中的寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="5bb40-147">Relaxed Delegate Conversion in Visual Basic</span></span>

<span data-ttu-id="5bb40-148">寬鬆委派轉換可讓您更有彈性地比對方法簽章與委派類型。</span><span class="sxs-lookup"><span data-stu-id="5bb40-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="5bb40-149">例如，當您將方法指派給委派時，它可讓您省略參數規格並省略函數傳回值。</span><span class="sxs-lookup"><span data-stu-id="5bb40-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="5bb40-150">如需詳細資訊，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="5bb40-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5bb40-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bb40-151">See also</span></span>

- [<span data-ttu-id="5bb40-152">泛型</span><span class="sxs-lookup"><span data-stu-id="5bb40-152">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="5bb40-153">針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bb40-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
