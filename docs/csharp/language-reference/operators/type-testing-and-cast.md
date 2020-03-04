---
title: 型別測試和轉換運算子 - C# 參考
description: 了解可用來檢查運算式結果型別的 C# 運算子，並視需要將它轉換成其他型別。
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: c29833ece83e386446aaf0a5d242bda366cbfbb0
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239036"
---
# <a name="type-testing-and-cast-operators-c-reference"></a><span data-ttu-id="63b81-103">型別測試和轉換運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="63b81-103">Type-testing and cast operators (C# reference)</span></span>

<span data-ttu-id="63b81-104">您可以使用下列運算子來執行型別檢查或型別轉換：</span><span class="sxs-lookup"><span data-stu-id="63b81-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="63b81-105">[is 運算子](#is-operator)：檢查運算式的執行階段型別是否與給定型別相容</span><span class="sxs-lookup"><span data-stu-id="63b81-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="63b81-106">[as 運算子](#as-operator)：如果運算式的執行階段型別與給定型別相容，就將它明確地轉換成該型別</span><span class="sxs-lookup"><span data-stu-id="63b81-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="63b81-107">[轉換運算子 ()](#cast-operator-)：執行明確轉換</span><span class="sxs-lookup"><span data-stu-id="63b81-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="63b81-108">[typeof 運算子](#typeof-operator)：取得型別的 <xref:System.Type?displayProperty=nameWithType> 執行個體</span><span class="sxs-lookup"><span data-stu-id="63b81-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="63b81-109">is 運算子</span><span class="sxs-lookup"><span data-stu-id="63b81-109">is operator</span></span>

<span data-ttu-id="63b81-110">`is` 運算子會檢查運算式結果的執行階段型別是否與給定型別相容。</span><span class="sxs-lookup"><span data-stu-id="63b81-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="63b81-111">從C# 7.0 開始，`is` 運算子也會針對模式測試運算式結果。</span><span class="sxs-lookup"><span data-stu-id="63b81-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="63b81-112">使用型別測試 `is` 運算子運算式有下列格式</span><span class="sxs-lookup"><span data-stu-id="63b81-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="63b81-113">其中 `E` 是會傳回值的運算式，而 `T` 是型別名稱或型別參數。</span><span class="sxs-lookup"><span data-stu-id="63b81-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="63b81-114">`E` 不能是匿名方法或 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="63b81-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="63b81-115">如果 `E is T` 的結果是非 Null 且可轉換成型別 `true` (藉由參考轉換、Boxing 轉換或 Unboxing 轉換)，則 `E` 運算式傳回 `T`；否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="63b81-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="63b81-116">`is` 運算子不會考慮使用者定義轉換。</span><span class="sxs-lookup"><span data-stu-id="63b81-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="63b81-117">下列範例示範當運算式結果的執行階段型別衍生自給定型別 (表示型別之間存在參考轉換) 時，`is` 運算子傳回 `true`：</span><span class="sxs-lookup"><span data-stu-id="63b81-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="63b81-118">下一個範例顯示 `is` 運算子會將裝箱和取消裝箱轉換納入考慮，但不會考慮[數值轉換](../builtin-types/numeric-conversions.md)：</span><span class="sxs-lookup"><span data-stu-id="63b81-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="63b81-119">如需 C# 轉換的資訊，請參閱 [C# 語言規格](~/_csharplang/spec/conversions.md)的[轉換](~/_csharplang/spec/introduction.md)一章。</span><span class="sxs-lookup"><span data-stu-id="63b81-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="63b81-120">包含模式比對的型別測試</span><span class="sxs-lookup"><span data-stu-id="63b81-120">Type testing with pattern matching</span></span>

<span data-ttu-id="63b81-121">從C# 7.0 開始，`is` 運算子也會針對模式測試運算式結果。</span><span class="sxs-lookup"><span data-stu-id="63b81-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="63b81-122">尤其是，它支援下列格式的型別模式：</span><span class="sxs-lookup"><span data-stu-id="63b81-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="63b81-123">其中 `E` 是會傳回值的運算式，`T` 是型別名稱或型別參數，而 `v` 是型別為 `T` 的新區域變數。</span><span class="sxs-lookup"><span data-stu-id="63b81-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="63b81-124">如果 `E` 的結果是非 Null，且可轉換成 `T` (藉由參考、Boxing 或 Unboxing 轉換)，則 `E is T v` 運算式會傳回 `true`，且 `E` 的結果會指派至變數 `v`。</span><span class="sxs-lookup"><span data-stu-id="63b81-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="63b81-125">下列範例示範包含型別模式的 `is` 運算子用法：</span><span class="sxs-lookup"><span data-stu-id="63b81-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="63b81-126">如需型別模式和其他支援模式的詳細資訊，請參閱[使用 is 的模式比對](../keywords/is.md#pattern-matching-with-is)。</span><span class="sxs-lookup"><span data-stu-id="63b81-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="63b81-127">as 運算子</span><span class="sxs-lookup"><span data-stu-id="63b81-127">as operator</span></span>

<span data-ttu-id="63b81-128">`as` 運算子將運算式的結果明確地轉換成給定參考或可為 Null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="63b81-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="63b81-129">如果無法轉換，則 `as` 運算子會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="63b81-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="63b81-130">不同於[轉換運算子 ()](#cast-operator-)，`as` 運算子一律不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="63b81-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="63b81-131">以下格式的運算式</span><span class="sxs-lookup"><span data-stu-id="63b81-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="63b81-132">其中 `E` 是會傳回值的運算式，而 `T` 是型別名稱或型別參數，產生的結果與下列相同</span><span class="sxs-lookup"><span data-stu-id="63b81-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="63b81-133">但只會評估 `E` 一次。</span><span class="sxs-lookup"><span data-stu-id="63b81-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="63b81-134">`as` 運算子只考慮參考、可為 Null、Boxing 和 Unboxing 轉換。</span><span class="sxs-lookup"><span data-stu-id="63b81-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="63b81-135">您無法使用 `as` 運算子來執行使用者定義轉換。</span><span class="sxs-lookup"><span data-stu-id="63b81-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="63b81-136">若要那麼做，請使用[轉換運算子 ()](#cast-operator-)。</span><span class="sxs-lookup"><span data-stu-id="63b81-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="63b81-137">下列範例示範 `as` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="63b81-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="63b81-138">如上述範例所示，您需要將 `as` 陳述式的結果與 `null` 比較，以檢查轉換是否成功。</span><span class="sxs-lookup"><span data-stu-id="63b81-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="63b81-139">從C# 7.0 開始，您可以使用[is 運算子](#type-testing-with-pattern-matching)來測試轉換是否成功，如果成功，請將其結果指派給新的變數。</span><span class="sxs-lookup"><span data-stu-id="63b81-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="63b81-140">轉換運算子 ()</span><span class="sxs-lookup"><span data-stu-id="63b81-140">Cast operator ()</span></span>

<span data-ttu-id="63b81-141">格式為 `(T)E` 的轉換運算式會執行明確轉換，將運算式 `E` 的結果轉換成型別 `T`。</span><span class="sxs-lookup"><span data-stu-id="63b81-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="63b81-142">如果沒有從型別 `E` 轉換成型別 `T` 的明確轉換存在，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="63b81-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="63b81-143">在執行階段，明確轉換可能不會成功，且轉換運算式可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="63b81-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="63b81-144">下列範例示範明確的數值和參考轉換：</span><span class="sxs-lookup"><span data-stu-id="63b81-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="63b81-145">如需支援之明確轉換的資訊，請參閱 [C# 語言規格](~/_csharplang/spec/conversions.md#explicit-conversions)的[明確轉換](~/_csharplang/spec/introduction.md)一節。</span><span class="sxs-lookup"><span data-stu-id="63b81-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="63b81-146">如需如何定義自訂明確或隱含型別轉換的資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="63b81-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="63b81-147">() 的其他用法</span><span class="sxs-lookup"><span data-stu-id="63b81-147">Other usages of ()</span></span>

<span data-ttu-id="63b81-148">您也使用括號來[呼叫方法或叫用委派](member-access-operators.md#invocation-operator-)。</span><span class="sxs-lookup"><span data-stu-id="63b81-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="63b81-149">括弧的其他用法是調整評估運算式中作業的順序。</span><span class="sxs-lookup"><span data-stu-id="63b81-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="63b81-150">如需詳細資訊，請參閱 [C# 運算子](index.md)。</span><span class="sxs-lookup"><span data-stu-id="63b81-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="63b81-151">typeof 運算子</span><span class="sxs-lookup"><span data-stu-id="63b81-151">typeof operator</span></span>

<span data-ttu-id="63b81-152">`typeof` 運算子會取得型別的 <xref:System.Type?displayProperty=nameWithType> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="63b81-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="63b81-153">`typeof` 運算子的引數必須是型別名稱或型別參數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="63b81-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="63b81-154">您也可以搭配使用 `typeof` 運算子和未繫結的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="63b81-154">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="63b81-155">未繫結泛型型別的名稱必須包含適當數目的逗號，也就是比型別參數數目少一。</span><span class="sxs-lookup"><span data-stu-id="63b81-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="63b81-156">下列範例顯示搭配使用 `typeof` 運算子和未繫結泛型型別的用法：</span><span class="sxs-lookup"><span data-stu-id="63b81-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="63b81-157">運算式不能作為 `typeof` 運算子的引數。</span><span class="sxs-lookup"><span data-stu-id="63b81-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="63b81-158">若要取得運算式結果之執行時間類型的 <xref:System.Type?displayProperty=nameWithType> 實例，請使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="63b81-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="63b81-159">使用 `typeof` 運算子的型別測試</span><span class="sxs-lookup"><span data-stu-id="63b81-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="63b81-160">使用 `typeof` 運算子來檢查運算式結果的執行階段型別，是否完全符合給定型別。</span><span class="sxs-lookup"><span data-stu-id="63b81-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="63b81-161">下列範例示範使用 `typeof` 運算子和 [is 運算子](#is-operator)，執行型別檢查之間的差異：</span><span class="sxs-lookup"><span data-stu-id="63b81-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/snippets/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="63b81-162">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="63b81-162">Operator overloadability</span></span>

<span data-ttu-id="63b81-163">`is`、`as`和 `typeof` 運算子無法多載。</span><span class="sxs-lookup"><span data-stu-id="63b81-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="63b81-164">使用者定義型別不可多載 `()` 運算子，但可定義可由轉換運算式執行的自訂型別轉換。</span><span class="sxs-lookup"><span data-stu-id="63b81-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="63b81-165">如需詳細資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="63b81-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="63b81-166">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="63b81-166">C# language specification</span></span>

<span data-ttu-id="63b81-167">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="63b81-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="63b81-168">is 運算子</span><span class="sxs-lookup"><span data-stu-id="63b81-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="63b81-169">as 運算子</span><span class="sxs-lookup"><span data-stu-id="63b81-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="63b81-170">轉換運算式</span><span class="sxs-lookup"><span data-stu-id="63b81-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="63b81-171">typeof 運算子</span><span class="sxs-lookup"><span data-stu-id="63b81-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="63b81-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63b81-172">See also</span></span>

- [<span data-ttu-id="63b81-173">C# 參考</span><span class="sxs-lookup"><span data-stu-id="63b81-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="63b81-174">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="63b81-174">C# operators</span></span>](index.md)
- [<span data-ttu-id="63b81-175">如何使用模式比對和 is 和 as 運算子，安全地轉換</span><span class="sxs-lookup"><span data-stu-id="63b81-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="63b81-176">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="63b81-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
