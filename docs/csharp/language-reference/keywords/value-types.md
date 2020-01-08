---
title: 實值型別 - C# 參考
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 31563eccd50e6acd27a8e5a4ee96046fd2728695
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345352"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="0fcd6-102">實值型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0fcd6-102">Value types (C# Reference)</span></span>

<span data-ttu-id="0fcd6-103">有兩種實值型別：</span><span class="sxs-lookup"><span data-stu-id="0fcd6-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="0fcd6-104">結構</span><span class="sxs-lookup"><span data-stu-id="0fcd6-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="0fcd6-105">列舉</span><span class="sxs-lookup"><span data-stu-id="0fcd6-105">Enumerations</span></span>](../builtin-types/enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="0fcd6-106">實值型別的主要功能</span><span class="sxs-lookup"><span data-stu-id="0fcd6-106">Main features of value types</span></span>

<span data-ttu-id="0fcd6-107">實值型別的變數會包含該型別的值。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="0fcd6-108">例如，`int` 型別的變數可能包含 `42`值。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="0fcd6-109">這與參考型別的變數不同，參考型別的變數會包含型別執行個體 (也稱為物件) 的參考。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="0fcd6-110">當您指派新值給某個實值型別的變數時，系統會複製該值。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="0fcd6-111">當您指派新值給某個參考型別的變數時，系統會複製參考，而不是物件本身。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="0fcd6-112">所有實值型別都是隱含地衍生自 <xref:System.ValueType?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0fcd6-113">與參考型別不同，您無法從實值型別衍生新的類型。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="0fcd6-114">不過，就像參考型別，結構可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="0fcd6-115">實值型別預設不可為 `null`。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="0fcd6-116">不過，可以 `null`對應的[可為 null 實數值型別](../builtin-types/nullable-value-types.md)的變數。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-116">However, variables of the corresponding [nullable value types](../builtin-types/nullable-value-types.md) can be `null`.</span></span>

<span data-ttu-id="0fcd6-117">每種實值型別都具有初始化該型別預設值的隱含無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="0fcd6-118">如需有關實值型別預設值的資訊，請參閱[預設值表](default-values-table.md)。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="0fcd6-119">簡單型別</span><span class="sxs-lookup"><span data-stu-id="0fcd6-119">Simple types</span></span>

<span data-ttu-id="0fcd6-120">「簡單型別」是 C# 所提供的一組預先定義結構型別，其中包含下列型別：</span><span class="sxs-lookup"><span data-stu-id="0fcd6-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="0fcd6-121">[整數型別](../builtin-types/integral-numeric-types.md)：整數數字型別和 [char](../builtin-types/char.md) 型別</span><span class="sxs-lookup"><span data-stu-id="0fcd6-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](../builtin-types/char.md) type</span></span>
- [<span data-ttu-id="0fcd6-122">浮點類型</span><span class="sxs-lookup"><span data-stu-id="0fcd6-122">Floating-point types</span></span>](../builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="0fcd6-123">bool</span><span class="sxs-lookup"><span data-stu-id="0fcd6-123">bool</span></span>](../builtin-types/bool.md)

<span data-ttu-id="0fcd6-124">透過關鍵字即可識別簡單型別，但這些關鍵字只是 <xref:System> 命名空間中預先定義之結構型別的別名。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="0fcd6-125">例如，[int](../builtin-types/integral-numeric-types.md) 是 <xref:System.Int32?displayProperty=nameWithType> 的別名。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0fcd6-126">如需完整的別名清單，請參閱[內建型別表](built-in-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="0fcd6-127">簡單型別與其他結構型別的差異在於它們可允許某些額外的作業：</span><span class="sxs-lookup"><span data-stu-id="0fcd6-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="0fcd6-128">簡單類型可以使用常值進行初始化。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="0fcd6-129">例如，`'A'` 是 `char` 型別的常值，而 `2001` 則是 `int` 型別的常值。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="0fcd6-130">您可以使用 [const](const.md) 關鍵字來宣告簡單型別的常數。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="0fcd6-131">其他結構型別則不可能有常數。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="0fcd6-132">常數運算式如果運算元全都是簡單型別常數，就會在編譯階段進行評估。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="0fcd6-133">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[簡單型別](~/_csharplang/spec/types.md#simple-types)一節。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="0fcd6-134">將實值型別初始化</span><span class="sxs-lookup"><span data-stu-id="0fcd6-134">Initializing value types</span></span>

<span data-ttu-id="0fcd6-135">必須先初始化 C# 中的區域變數，再使用它們。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="0fcd6-136">例如，您可以宣告區域變數，而不進行初始化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0fcd6-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="0fcd6-137">您不能先使用它，再將它初始化。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="0fcd6-138">您可以使用下列陳述式來初始化執行個體：</span><span class="sxs-lookup"><span data-stu-id="0fcd6-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="0fcd6-139">這個陳述式相當於下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="0fcd6-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="0fcd6-140">當然，您可以有相同陳述式中的宣告和初始化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0fcd6-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="0fcd6-141">-或-</span><span class="sxs-lookup"><span data-stu-id="0fcd6-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="0fcd6-142">使用 [new](../operators/new-operator.md) 運算子會呼叫特定型別的無參數建構函式，並將預設值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="0fcd6-143">在上述範例中，無參數建構函式已將 `0` 值指派給 `myInt`。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="0fcd6-144">如需有關透過呼叫無參數建構函式來指派的值之詳細資訊，請參閱[預設值表](default-values-table.md)。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-144">For more information about values assigned by calling parameterless constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="0fcd6-145">如果要使用使用者定義型別，請使用 [new](../operators/new-operator.md) 來叫用無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="0fcd6-146">例如，下列陳述式會叫用 `Point` 結構的無參數建構函式：</span><span class="sxs-lookup"><span data-stu-id="0fcd6-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="0fcd6-147">在此呼叫之後，會視為已明確指派結構，也就是說，其所有成員都已初始化為其預設值。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="0fcd6-148">如需有關 `new` 運算子的詳細資訊，請參閱 [new](../operators/new-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="0fcd6-149">如需有關將數字型別輸出格式化的資訊，請參閱[格式化數值結果表](formatting-numeric-results-table.md)。</span><span class="sxs-lookup"><span data-stu-id="0fcd6-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0fcd6-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="0fcd6-150">See also</span></span>

- [<span data-ttu-id="0fcd6-151">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0fcd6-151">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0fcd6-152">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="0fcd6-152">C# keywords</span></span>](index.md)
- [<span data-ttu-id="0fcd6-153">參考型別</span><span class="sxs-lookup"><span data-stu-id="0fcd6-153">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="0fcd6-154">可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="0fcd6-154">Nullable value types</span></span>](../builtin-types/nullable-value-types.md)
