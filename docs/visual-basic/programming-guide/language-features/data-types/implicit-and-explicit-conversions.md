---
title: 隱含和明確轉換
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: b7215933cec89b7023f08e8996a283b39b3a3c83
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346362"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="c4c72-102">隱含和明確轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4c72-102">Implicit and Explicit Conversions (Visual Basic)</span></span>

<span data-ttu-id="c4c72-103">*隱含轉換*在原始程式碼中不需要任何特殊語法。</span><span class="sxs-lookup"><span data-stu-id="c4c72-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="c4c72-104">在下列範例中，Visual Basic 會將 `k` 的值隱含地轉換成單精確度浮點數，再將它指派給 `q`。</span><span class="sxs-lookup"><span data-stu-id="c4c72-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

<span data-ttu-id="c4c72-105">*明確轉換*會使用類型轉換關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c4c72-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="c4c72-106">Visual Basic 提供了數個這類關鍵字，可將括弧中的運算式強制轉型為所需的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c4c72-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="c4c72-107">這些關鍵字的作用就像函式，但編譯器會產生內嵌程式碼，因此執行的速度會比函式呼叫稍微快。</span><span class="sxs-lookup"><span data-stu-id="c4c72-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>

<span data-ttu-id="c4c72-108">在上述範例的下列延伸模組中，`CInt` 關鍵字會先將 `q` 的值轉換回整數，再將它指派給 `k`。</span><span class="sxs-lookup"><span data-stu-id="c4c72-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a><span data-ttu-id="c4c72-109">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="c4c72-109">Conversion Keywords</span></span>

<span data-ttu-id="c4c72-110">下表顯示可用的轉換關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c4c72-110">The following table shows the available conversion keywords.</span></span>

|<span data-ttu-id="c4c72-111">類型轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="c4c72-111">Type conversion keyword</span></span>|<span data-ttu-id="c4c72-112">將運算式轉換為資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-112">Converts an expression to data type</span></span>|<span data-ttu-id="c4c72-113">允許轉換之運算式的資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-113">Allowable data types of expression to be converted</span></span>|
|---|---|---|
|`CBool`|[<span data-ttu-id="c4c72-114">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="c4c72-115">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`String``Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|
|`CByte`|[<span data-ttu-id="c4c72-116">Byte 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="c4c72-117">任何數數值型別（包括 `SByte` 和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CChar`|[<span data-ttu-id="c4c72-118">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="c4c72-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-119">`String`, `Object`</span></span>|
|`CDate`|[<span data-ttu-id="c4c72-120">Date 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="c4c72-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-121">`String`, `Object`</span></span>|
|`CDbl`|[<span data-ttu-id="c4c72-122">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="c4c72-123">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CDec`|[<span data-ttu-id="c4c72-124">Decimal 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="c4c72-125">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CInt`|[<span data-ttu-id="c4c72-126">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="c4c72-127">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CLng`|[<span data-ttu-id="c4c72-128">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="c4c72-129">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CObj`|[<span data-ttu-id="c4c72-130">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="c4c72-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="c4c72-131">任何型別</span><span class="sxs-lookup"><span data-stu-id="c4c72-131">Any type</span></span>|
|`CSByte`|[<span data-ttu-id="c4c72-132">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="c4c72-133">任何數數值型別（包括 `Byte` 和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CShort`|[<span data-ttu-id="c4c72-134">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="c4c72-135">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CSng`|[<span data-ttu-id="c4c72-136">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="c4c72-137">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CStr`|[<span data-ttu-id="c4c72-138">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="c4c72-139">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`Char`、`Char` 陣列、`Date`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|
|`CType`|<span data-ttu-id="c4c72-140">在逗號後面指定的類型（`,`）</span><span class="sxs-lookup"><span data-stu-id="c4c72-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="c4c72-141">轉換成*基本資料類型*（包括基本類型的陣列）時，與對應的轉換關鍵字所允許的類型相同</span><span class="sxs-lookup"><span data-stu-id="c4c72-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="c4c72-142">轉換成*複合資料型別*時，它所執行的介面和它所繼承的類別</span><span class="sxs-lookup"><span data-stu-id="c4c72-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="c4c72-143">轉換成您已多載 `CType`的類別或結構時，該類別或結構</span><span class="sxs-lookup"><span data-stu-id="c4c72-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|
|`CUInt`|[<span data-ttu-id="c4c72-144">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="c4c72-145">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CULng`|[<span data-ttu-id="c4c72-146">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="c4c72-147">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CUShort`|[<span data-ttu-id="c4c72-148">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="c4c72-149">任何數數值型別（包括 `Byte`、`SByte`和列舉類型）、`Boolean`、`String`、`Object`</span><span class="sxs-lookup"><span data-stu-id="c4c72-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|

## <a name="the-ctype-function"></a><span data-ttu-id="c4c72-150">CType 函式</span><span class="sxs-lookup"><span data-stu-id="c4c72-150">The CType Function</span></span>

<span data-ttu-id="c4c72-151">[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)會在兩個引數上運作。</span><span class="sxs-lookup"><span data-stu-id="c4c72-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="c4c72-152">第一個是要轉換的運算式，第二個是目的地資料類型或物件類別。</span><span class="sxs-lookup"><span data-stu-id="c4c72-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="c4c72-153">請注意，第一個引數必須是運算式，而不是類型。</span><span class="sxs-lookup"><span data-stu-id="c4c72-153">Note that the first argument must be an expression, not a type.</span></span>

<span data-ttu-id="c4c72-154">`CType` 是*內嵌*函式，這表示已編譯的程式碼會進行轉換，通常不會產生函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4c72-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="c4c72-155">這會改善效能。</span><span class="sxs-lookup"><span data-stu-id="c4c72-155">This improves performance.</span></span>

<span data-ttu-id="c4c72-156">如需 `CType` 與其他類型轉換關鍵字的比較，請參閱[DirectCast 運算子](../../../../visual-basic/language-reference/operators/directcast-operator.md)和[TryCast 運算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c72-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>

### <a name="elementary-types"></a><span data-ttu-id="c4c72-157">基本類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-157">Elementary Types</span></span>

<span data-ttu-id="c4c72-158">下列範例示範 `CType` 的用法。</span><span class="sxs-lookup"><span data-stu-id="c4c72-158">The following example demonstrates the use of `CType`.</span></span>

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a><span data-ttu-id="c4c72-159">複合類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-159">Composite Types</span></span>

<span data-ttu-id="c4c72-160">您可以使用 `CType`，將值轉換成複合資料型別以及基本類型。</span><span class="sxs-lookup"><span data-stu-id="c4c72-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="c4c72-161">您也可以使用它將物件類別強制轉型為其中一個介面的類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c4c72-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a><span data-ttu-id="c4c72-162">陣列類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-162">Array Types</span></span>

<span data-ttu-id="c4c72-163">`CType` 也可以轉換陣列資料類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c4c72-163">`CType` can also convert array data types, as in the following example.</span></span>

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

<span data-ttu-id="c4c72-164">如需詳細資訊和範例，請參閱[陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c72-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>

### <a name="types-defining-ctype"></a><span data-ttu-id="c4c72-165">定義 CType 的類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-165">Types Defining CType</span></span>

<span data-ttu-id="c4c72-166">您可以在已定義的類別或結構上定義 `CType`。</span><span class="sxs-lookup"><span data-stu-id="c4c72-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="c4c72-167">這可讓您將值轉換為類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="c4c72-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="c4c72-168">如需詳細資訊和範例，請參閱[如何：定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c72-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c4c72-169">搭配轉換關鍵字使用的值，對於目的地資料類型而言必須是有效的，否則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4c72-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="c4c72-170">例如，如果您嘗試將 `Long` 轉換為 `Integer`，則 `Long` 的值必須在 `Integer` 資料類型的有效範圍內。</span><span class="sxs-lookup"><span data-stu-id="c4c72-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>

> [!CAUTION]
> <span data-ttu-id="c4c72-171">如果來源類型不是衍生自目的地類型，指定 `CType` 在執行時間時，從一個類別類型轉換成另一個類別，會失敗。</span><span class="sxs-lookup"><span data-stu-id="c4c72-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="c4c72-172">這類失敗會擲回 <xref:System.InvalidCastException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4c72-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="c4c72-173">不過，如果其中一種類型是您已定義的結構或類別，而且您已在該結構或類別上定義 `CType`，則轉換可以成功滿足您的 `CType`需求。</span><span class="sxs-lookup"><span data-stu-id="c4c72-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="c4c72-174">請參閱[如何：定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c72-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>

<span data-ttu-id="c4c72-175">執行明確轉換也稱為將運算式*轉換*成指定的資料類型或物件類別。</span><span class="sxs-lookup"><span data-stu-id="c4c72-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4c72-176">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4c72-176">See also</span></span>

- [<span data-ttu-id="c4c72-177">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="c4c72-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="c4c72-178">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="c4c72-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="c4c72-179">如何：在 Visual Basic 中將物件轉換為另一種類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="c4c72-180">結構</span><span class="sxs-lookup"><span data-stu-id="c4c72-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c4c72-181">資料類型</span><span class="sxs-lookup"><span data-stu-id="c4c72-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="c4c72-182">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="c4c72-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="c4c72-183">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="c4c72-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
