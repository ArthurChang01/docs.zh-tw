---
title: 撰寫安全且有效率的 C# 程式碼
description: 最近對 C# 語言的增強功能，可讓您撰寫可驗證的安全程式碼，獲得先前使用不安全程式碼時的效能。
ms.date: 10/23/2018
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: bb53264f61192c042da469ba687da6c472e8c6d4
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506979"
---
# <a name="write-safe-and-efficient-c-code"></a><span data-ttu-id="0f499-103">撰寫安全且有效率的 C# 程式碼</span><span class="sxs-lookup"><span data-stu-id="0f499-103">Write safe and efficient C# code</span></span>

<span data-ttu-id="0f499-104">C# 中的新功能可讓您撰寫可驗證的安全程式碼，取得更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="0f499-104">New features in C# enable you to write verifiable safe code with better performance.</span></span> <span data-ttu-id="0f499-105">若您小心套用這些技術，則需要不安全程式碼的案例將減少。</span><span class="sxs-lookup"><span data-stu-id="0f499-105">If you carefully apply these techniques, fewer scenarios require unsafe code.</span></span> <span data-ttu-id="0f499-106">這些功能可讓使用實值型別參考作為方法引數和方法傳回值的過程變得更為容易。</span><span class="sxs-lookup"><span data-stu-id="0f499-106">These features make it easier to use references to value types as method arguments and method returns.</span></span> <span data-ttu-id="0f499-107">當以安全的方式執行時，這些技術可最小化複製實值型別的次數。</span><span class="sxs-lookup"><span data-stu-id="0f499-107">When done safely, these techniques minimize copying value types.</span></span> <span data-ttu-id="0f499-108">透過使用實值型別，您可以最小化傳遞的配置數及記憶體回收數。</span><span class="sxs-lookup"><span data-stu-id="0f499-108">By using value types, you can minimize the number of allocations and garbage collection passes.</span></span>

<span data-ttu-id="0f499-109">本文中的許多範例程式碼都使用了 C# 7.2 新增功能。</span><span class="sxs-lookup"><span data-stu-id="0f499-109">Much of the sample code in this article uses features added in C# 7.2.</span></span> <span data-ttu-id="0f499-110">若要使用這些功能，您必須設定您的專案，以使用 C# 7.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0f499-110">To use those features, you must configure your project to use C# 7.2 or later.</span></span> <span data-ttu-id="0f499-111">有關設置語言版本的詳細資訊，請參閱[配置語言版本](language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="0f499-111">For more information on setting the language version, see [configure the language version](language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="0f499-112">本文聚焦於高效率資源管理的技術。</span><span class="sxs-lookup"><span data-stu-id="0f499-112">This article focuses on techniques for efficient resource management.</span></span> <span data-ttu-id="0f499-113">使用實值型別的一個優點是它們通常可避免堆積配置。</span><span class="sxs-lookup"><span data-stu-id="0f499-113">One advantage to using value types is that they often avoid heap allocations.</span></span> <span data-ttu-id="0f499-114">相對地，缺點則是它們是以實值複製。</span><span class="sxs-lookup"><span data-stu-id="0f499-114">The disadvantage is that they're copied by value.</span></span> <span data-ttu-id="0f499-115">這種兩難的情況使得最佳化針對大量資料進行運作的演算法，變得更加困難。</span><span class="sxs-lookup"><span data-stu-id="0f499-115">This tradeoff makes it harder to optimize algorithms that operate on large amounts of data.</span></span> <span data-ttu-id="0f499-116">C# 7.2 中新的語言功能提供一項機制，可讓您使用實值型別參考來撰寫安全且有效率的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f499-116">New language features in C# 7.2 provide mechanisms that enable safe efficient code using references to value types.</span></span> <span data-ttu-id="0f499-117">若能善用這些功能，即可同時最小化配置及複製作業。</span><span class="sxs-lookup"><span data-stu-id="0f499-117">Use these features wisely to minimize both allocations and copy operations.</span></span> <span data-ttu-id="0f499-118">本文會探討這些新功能。</span><span class="sxs-lookup"><span data-stu-id="0f499-118">This article explores those new features.</span></span>

<span data-ttu-id="0f499-119">本文聚焦於下列資源管理技術：</span><span class="sxs-lookup"><span data-stu-id="0f499-119">This article focuses on the following resource management techniques:</span></span>

- <span data-ttu-id="0f499-120">聲明[`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example)表示類型不**可變**，並使編譯器能夠在使用[`in`](language-reference/keywords/in-parameter-modifier.md)參數時保存副本。</span><span class="sxs-lookup"><span data-stu-id="0f499-120">Declare a [`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example) to express that a type is **immutable** and enables the compiler to save copies when using [`in`](language-reference/keywords/in-parameter-modifier.md) parameters.</span></span>
- <span data-ttu-id="0f499-121">如果類型不能不可變，請聲明`struct`成員`readonly`以指示成員不修改狀態。</span><span class="sxs-lookup"><span data-stu-id="0f499-121">If a type can't be immutable, declare `struct` members `readonly` to indicate that the member doesn't modify state.</span></span>
- <span data-ttu-id="0f499-122">當[`ref readonly`](language-reference/keywords/ref.md#reference-return-values)傳回值`struct`大於<xref:System.IntPtr.Size?displayProperty=nameWithType>並且存儲存留期大於傳回值的方法時，請使用返回。</span><span class="sxs-lookup"><span data-stu-id="0f499-122">Use a [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) return when the return value is a `struct` larger than <xref:System.IntPtr.Size?displayProperty=nameWithType> and the storage lifetime is greater than the method returning the value.</span></span>
- <span data-ttu-id="0f499-123">當 `readonly struct` 的大小大於 <xref:System.IntPtr.Size?displayProperty=nameWithType> 時，基於效能原因，您應將它作為 `in` 參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="0f499-123">When the size of a `readonly struct` is bigger than <xref:System.IntPtr.Size?displayProperty=nameWithType>, you should pass it as an `in` parameter for performance reasons.</span></span>
- <span data-ttu-id="0f499-124">除非使用`readonly`修改`struct`器聲明`in`參數或方法僅`readonly`調用結構的成員，否則切勿將 傳遞為參數。</span><span class="sxs-lookup"><span data-stu-id="0f499-124">Never pass a `struct` as an `in` parameter unless it's declared with the `readonly` modifier or the method calls only `readonly` members of the struct.</span></span> <span data-ttu-id="0f499-125">違反本指南可能會對性能產生負面影響，並可能導致模糊行為。</span><span class="sxs-lookup"><span data-stu-id="0f499-125">Violating this guidance may negatively affect performance and could lead to an obscure behavior.</span></span>
- <span data-ttu-id="0f499-126">使用[`ref struct`](language-reference/keywords/ref.md#ref-struct-types)或`readonly ref struct`等<xref:System.Span%601>或<xref:System.ReadOnlySpan%601>將記憶體用作位元組序列。</span><span class="sxs-lookup"><span data-stu-id="0f499-126">Use a [`ref struct`](language-reference/keywords/ref.md#ref-struct-types), or a `readonly ref struct` such as <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> to work with memory as a sequence of bytes.</span></span>

<span data-ttu-id="0f499-127">這些技術會強迫您考慮在**參考**及**實值**這兩個競爭目標之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="0f499-127">These techniques force you to balance two competing goals with regard to **references** and **values**.</span></span> <span data-ttu-id="0f499-128">[參考型別](programming-guide/types/index.md#reference-types)的變數會保留記憶體位置的參考。</span><span class="sxs-lookup"><span data-stu-id="0f499-128">Variables that are [reference types](programming-guide/types/index.md#reference-types) hold a reference to the location in memory.</span></span> <span data-ttu-id="0f499-129">[實值型別](programming-guide/types/index.md#value-types)的變數則會直接包含其值。</span><span class="sxs-lookup"><span data-stu-id="0f499-129">Variables that are [value types](programming-guide/types/index.md#value-types) directly contain their value.</span></span> <span data-ttu-id="0f499-130">這些差異凸顯管理記憶體資源時關鍵的不同點。</span><span class="sxs-lookup"><span data-stu-id="0f499-130">These differences highlight the key differences that are important for managing memory resources.</span></span> <span data-ttu-id="0f499-131">**實值型別**通常會在傳遞至方法，或是從方法傳回時複製。</span><span class="sxs-lookup"><span data-stu-id="0f499-131">**Value types** are typically copied when passed to a method or returned from a method.</span></span> <span data-ttu-id="0f499-132">此行為包含在呼叫實值型別成員時，複製 `this` 的值。</span><span class="sxs-lookup"><span data-stu-id="0f499-132">This behavior includes copying the value of `this` when calling members of a value type.</span></span> <span data-ttu-id="0f499-133">複製成本與型別的大小相關。</span><span class="sxs-lookup"><span data-stu-id="0f499-133">The cost of the copy is related to the size of the type.</span></span> <span data-ttu-id="0f499-134">**參考型別**則配置在受控堆積上。</span><span class="sxs-lookup"><span data-stu-id="0f499-134">**Reference types** are allocated on the managed heap.</span></span> <span data-ttu-id="0f499-135">每個新物件都需要新的配置，且之後都必須進行回收。</span><span class="sxs-lookup"><span data-stu-id="0f499-135">Each new object requires a new allocation, and subsequently must be reclaimed.</span></span> <span data-ttu-id="0f499-136">這些作業都需要時間。</span><span class="sxs-lookup"><span data-stu-id="0f499-136">Both these operations take time.</span></span> <span data-ttu-id="0f499-137">參考會在參考型別作為方法的引數或從方法傳回時複製。</span><span class="sxs-lookup"><span data-stu-id="0f499-137">The reference is copied when a reference type is passed as an argument to a method or returned from a method.</span></span>

<span data-ttu-id="0f499-138">本文使用下列 3D 點結構的範例概念來解釋這些建議：</span><span class="sxs-lookup"><span data-stu-id="0f499-138">This article uses the following example concept of the 3D-point structure to explain these recommendations:</span></span>

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

<span data-ttu-id="0f499-139">不同範例會使用此概念不同的實作。</span><span class="sxs-lookup"><span data-stu-id="0f499-139">Different examples use different implementations of this concept.</span></span>

## <a name="declare-readonly-structs-for-immutable-value-types"></a><span data-ttu-id="0f499-140">宣告固定實值型別的唯讀結構</span><span class="sxs-lookup"><span data-stu-id="0f499-140">Declare readonly structs for immutable value types</span></span>

<span data-ttu-id="0f499-141">使用 `readonly` 修飾詞宣告 `struct`，通知編譯器您的意圖是要建立固定型別。</span><span class="sxs-lookup"><span data-stu-id="0f499-141">Declaring a `struct` using the `readonly` modifier informs the compiler that your intent is to create an immutable type.</span></span> <span data-ttu-id="0f499-142">編譯器會實行包含下列規則的設計決策：</span><span class="sxs-lookup"><span data-stu-id="0f499-142">The compiler enforces that design decision with the following rules:</span></span>

- <span data-ttu-id="0f499-143">所有欄位成員都必須是 `readonly`</span><span class="sxs-lookup"><span data-stu-id="0f499-143">All field members must be `readonly`</span></span>
- <span data-ttu-id="0f499-144">所有屬性都必須是唯讀屬性，包含自動實作的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f499-144">All properties must be read-only, including auto-implemented properties.</span></span>

<span data-ttu-id="0f499-145">這兩項規則便足以確保沒有任何 `readonly struct` 的成員會修改該結構狀態。</span><span class="sxs-lookup"><span data-stu-id="0f499-145">These two rules are sufficient to ensure that no member of a `readonly struct` modifies the state of that struct.</span></span> <span data-ttu-id="0f499-146">`struct` 是固定的。</span><span class="sxs-lookup"><span data-stu-id="0f499-146">The `struct` is immutable.</span></span> <span data-ttu-id="0f499-147">`Point3D` 結構可定義為固定結構，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0f499-147">The `Point3D` structure could be defined as an immutable struct as shown in the following example:</span></span>

```csharp
readonly public struct ReadonlyPoint3D
{
    public ReadonlyPoint3D(double x, double y, double z)
    {
        this.X = x;
        this.Y = y;
        this.Z = z;
    }

    public double X { get; }
    public double Y { get; }
    public double Z { get; }
}
```

<span data-ttu-id="0f499-148">每當您的設計意圖是要建立固定實值型別時，請遵循此建議。</span><span class="sxs-lookup"><span data-stu-id="0f499-148">Follow this recommendation whenever your design intent is to create an immutable value type.</span></span> <span data-ttu-id="0f499-149">任何效能上的改善都會帶來效益。</span><span class="sxs-lookup"><span data-stu-id="0f499-149">Any performance improvements are an added benefit.</span></span> <span data-ttu-id="0f499-150">`readonly struct` 明確表達您的設計意圖。</span><span class="sxs-lookup"><span data-stu-id="0f499-150">The `readonly struct` clearly expresses your design intent.</span></span>

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a><span data-ttu-id="0f499-151">當結構不能不可變時，聲明唯讀成員</span><span class="sxs-lookup"><span data-stu-id="0f499-151">Declare readonly members when a struct can't be immutable</span></span>

<span data-ttu-id="0f499-152">在 C# 8.0 及更高版本中，當結構類型是可變的時，應聲明不導致突變的成員為`readonly`。</span><span class="sxs-lookup"><span data-stu-id="0f499-152">In C# 8.0 and later, when a struct type is mutable, you should declare members that don't cause mutation to be `readonly`.</span></span> <span data-ttu-id="0f499-153">考慮需要 3D 點結構但必須支援可變性的不同應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f499-153">Consider a different application that needs a 3D point structure, but must support mutability.</span></span> <span data-ttu-id="0f499-154">以下版本的 3D 點結構僅將`readonly`修改器添加到不修改結構的成員。</span><span class="sxs-lookup"><span data-stu-id="0f499-154">The following version of the 3D point structure adds the `readonly` modifier only to those members that don't modify the structure.</span></span> <span data-ttu-id="0f499-155">請按照此示例操作，此時您的設計必須支援某些成員對結構的修改，但您仍希望對某些成員強制實施唯讀的好處：</span><span class="sxs-lookup"><span data-stu-id="0f499-155">Follow this example when your design must support modifications to the struct by some members, but you still want the benefits of enforcing readonly on some members:</span></span>

```csharp
public struct Point3D
{
    public Point3D(double x, double y, double z)
    {
        _x = x;
        _y = y;
        _z = z;
    }

    private double _x;
    public double X
    {
        readonly get => _x;
        set => _x = value;
    }

    private double _y;
    public double Y
    {
        readonly get => _y;
        set => _y = value;
    }

    private double _z;
    public double Z
    {
        readonly get => _z;
        set => _z = value;
    }

    public readonly double Distance => Math.Sqrt(X * X + Y * Y + Z * Z);

    public readonly override string ToString() => $"{X}, {Y}, {Z}";
}
```

<span data-ttu-id="0f499-156">前面的示例顯示了可以應用`readonly`修改器的許多位置：方法、屬性和屬性訪問器。</span><span class="sxs-lookup"><span data-stu-id="0f499-156">The preceding sample shows many of the locations where you can apply the `readonly` modifier: methods, properties, and property accessors.</span></span> <span data-ttu-id="0f499-157">如果使用自動實現的屬性，編譯器將`readonly`修改器添加到`get`讀取寫入屬性的修飾器。</span><span class="sxs-lookup"><span data-stu-id="0f499-157">If you use auto-implemented properties, the compiler adds the `readonly` modifier to the `get` accessor for read-write properties.</span></span> <span data-ttu-id="0f499-158">編譯器將`readonly`修改器添加到僅具有`get`訪問器的屬性的自動實現屬性聲明中。</span><span class="sxs-lookup"><span data-stu-id="0f499-158">The compiler adds the `readonly` modifier to the auto-implemented property declarations for properties with only a `get` accessor.</span></span>

<span data-ttu-id="0f499-159">將`readonly`修改器添加到不突變狀態的成員提供了兩個相關好處。</span><span class="sxs-lookup"><span data-stu-id="0f499-159">Adding the `readonly` modifier to members that don't mutate state provides two related benefits.</span></span> <span data-ttu-id="0f499-160">首先，編譯器強制執行您的意圖。</span><span class="sxs-lookup"><span data-stu-id="0f499-160">First, the compiler enforces your intent.</span></span> <span data-ttu-id="0f499-161">該成員無法更改結構的狀態，也不能訪問未標記`readonly`的成員。</span><span class="sxs-lookup"><span data-stu-id="0f499-161">That member can't mutate the struct's state, nor can it access a member that isn't also marked `readonly`.</span></span> <span data-ttu-id="0f499-162">其次，編譯器在訪問`in``readonly`成員時不會創建參數的防禦性副本。</span><span class="sxs-lookup"><span data-stu-id="0f499-162">Second, the compiler won't create defensive copies of `in` parameters when accessing a `readonly` member.</span></span> <span data-ttu-id="0f499-163">編譯器可以安全地進行此優化，因為它保證`struct``readonly`成員不會修改 。</span><span class="sxs-lookup"><span data-stu-id="0f499-163">The compiler can make this optimization safely because it guarantees that the `struct` is not modified by a `readonly` member.</span></span>

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a><span data-ttu-id="0f499-164">在可能的情況下，針對大型結構使用 `ref readonly return` 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f499-164">Use `ref readonly return` statements for large structures when possible</span></span>

<span data-ttu-id="0f499-165">當所傳回值不屬於傳回方法的區域時，您可以以參考的型式傳回值。</span><span class="sxs-lookup"><span data-stu-id="0f499-165">You can return values by reference when the value being returned isn't local to the returning method.</span></span> <span data-ttu-id="0f499-166">以參考的型式傳回，表示只會複製參考，而非結構。</span><span class="sxs-lookup"><span data-stu-id="0f499-166">Returning by reference means that only the reference is copied, not the structure.</span></span> <span data-ttu-id="0f499-167">在下列範例中，`Origin` 屬性無法使用 `ref` 傳回，因為傳回的值是區域變數：</span><span class="sxs-lookup"><span data-stu-id="0f499-167">In the following example, the `Origin` property can't use a `ref` return because the value being returned is a local variable:</span></span>

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

<span data-ttu-id="0f499-168">但是，下列屬性定義則可以參考的型式傳回，因為傳回值是靜態成員：</span><span class="sxs-lookup"><span data-stu-id="0f499-168">However, the following property definition can be returned by reference because the returned value is a static member:</span></span>

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

<span data-ttu-id="0f499-169">您不希望呼叫者修改原點，因此您應以 `ref readonly` 的方式傳回值：</span><span class="sxs-lookup"><span data-stu-id="0f499-169">You don't want callers modifying the origin, so you should return the value by `ref readonly`:</span></span>

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

<span data-ttu-id="0f499-170">傳回 `ref readonly` 可讓您避免複製較大的結構，並保留您內部資料成員的不變性。</span><span class="sxs-lookup"><span data-stu-id="0f499-170">Returning `ref readonly` enables you to save copying larger structures and preserve the immutability of your internal data members.</span></span>

<span data-ttu-id="0f499-171">在呼叫位置，呼叫者會選擇使用 `Origin` 屬性作為 `ref readonly` 或作為值：</span><span class="sxs-lookup"><span data-stu-id="0f499-171">At the call site, callers make the choice to use the `Origin` property as a `ref readonly` or as a value:</span></span>

[!code-csharp[AssignRefReadonly](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

<span data-ttu-id="0f499-172">在上述程式碼中的第一項指派，會建立 `Origin` 常數的複本，並指派該複本。</span><span class="sxs-lookup"><span data-stu-id="0f499-172">The first assignment in the preceding code makes a copy of the `Origin` constant and assigns that copy.</span></span> <span data-ttu-id="0f499-173">第二項指派則會指派參考。</span><span class="sxs-lookup"><span data-stu-id="0f499-173">The second assigns a reference.</span></span> <span data-ttu-id="0f499-174">請注意，`readonly` 修飾詞必須是變數宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="0f499-174">Notice that the `readonly` modifier must be part of the declaration of the variable.</span></span> <span data-ttu-id="0f499-175">其參考項目無法修改。</span><span class="sxs-lookup"><span data-stu-id="0f499-175">The reference to which it refers can't be modified.</span></span> <span data-ttu-id="0f499-176">如果嘗試修改，會導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f499-176">Attempts to do so result in a compile-time error.</span></span>

<span data-ttu-id="0f499-177">`readonly` 修飾詞在 `originReference` 的宣告上是必要的。</span><span class="sxs-lookup"><span data-stu-id="0f499-177">The `readonly` modifier is required on the declaration of `originReference`.</span></span>

<span data-ttu-id="0f499-178">編譯器會強制呼叫者不可修改該參考。</span><span class="sxs-lookup"><span data-stu-id="0f499-178">The compiler enforces that the caller can't modify the reference.</span></span> <span data-ttu-id="0f499-179">若嘗試直接指派到值，則會產生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f499-179">Attempts to assign the value directly generate a compile-time error.</span></span> <span data-ttu-id="0f499-180">但是，編譯器無法得知是否有任何成員方法修改結構的狀態。</span><span class="sxs-lookup"><span data-stu-id="0f499-180">However, the compiler can't know if any member method modifies the state of the struct.</span></span>
<span data-ttu-id="0f499-181">為確保物件未經修改，編譯器會建立複本，並使用該複本呼叫成員參考。</span><span class="sxs-lookup"><span data-stu-id="0f499-181">To ensure that the object isn't modified, the compiler creates a copy and calls member references using that copy.</span></span> <span data-ttu-id="0f499-182">任何修改皆僅會修改防禦複本。</span><span class="sxs-lookup"><span data-stu-id="0f499-182">Any modifications are to that defensive copy.</span></span>

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a><span data-ttu-id="0f499-183">將 `in` 修飾詞套用到大於 `System.IntPtr.Size` 的 `readonly struct` 參數</span><span class="sxs-lookup"><span data-stu-id="0f499-183">Apply the `in` modifier to `readonly struct` parameters larger than `System.IntPtr.Size`</span></span>

<span data-ttu-id="0f499-184">`in` 關鍵字會補充現有的 `ref` 和 `out` 關鍵字，以參考型式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="0f499-184">The `in` keyword complements the existing `ref` and `out` keywords to pass arguments by reference.</span></span> <span data-ttu-id="0f499-185">`in` 關鍵字會指定以參考型式傳遞引數，但呼叫的方法不會修改值。</span><span class="sxs-lookup"><span data-stu-id="0f499-185">The `in` keyword specifies passing the argument by reference, but the called method doesn't modify the value.</span></span>

<span data-ttu-id="0f499-186">該新增功能提供完整的詞彙能表達您的設計目的。</span><span class="sxs-lookup"><span data-stu-id="0f499-186">This addition provides a full vocabulary to express your design intent.</span></span>
<span data-ttu-id="0f499-187">當您未在下列方法簽章中指定下列任一修飾詞時，會在傳遞至呼叫的方法時，複製實值型別。</span><span class="sxs-lookup"><span data-stu-id="0f499-187">Value types are copied when passed to a called method when you don't specify any of the following modifiers in the method signature.</span></span> <span data-ttu-id="0f499-188">每個修飾詞都會指定以參考型式來傳遞變數以避免複製。</span><span class="sxs-lookup"><span data-stu-id="0f499-188">Each of these modifiers specifies that a variable is passed by reference, avoiding the copy.</span></span> <span data-ttu-id="0f499-189">每個修飾詞皆表示不同之目的：</span><span class="sxs-lookup"><span data-stu-id="0f499-189">Each modifier expresses a different intent:</span></span>

- <span data-ttu-id="0f499-190">`out`：此方法會設定用作為此參數的引數值。</span><span class="sxs-lookup"><span data-stu-id="0f499-190">`out`: This method sets the value of the argument used as this parameter.</span></span>
- <span data-ttu-id="0f499-191">`ref`：此方法會設定用作為此參數的引數值。</span><span class="sxs-lookup"><span data-stu-id="0f499-191">`ref`: This method may set the value of the argument used as this parameter.</span></span>
- <span data-ttu-id="0f499-192">`in`：此方法不修改用作此參數的參數的值。</span><span class="sxs-lookup"><span data-stu-id="0f499-192">`in`: This method doesn't modify the value of the argument used as this parameter.</span></span>

<span data-ttu-id="0f499-193">當您新增 `in` 修飾詞來利用參考傳遞引數時，即表明您的設計目的是利用參考傳遞引數，來避免不必要的複製。</span><span class="sxs-lookup"><span data-stu-id="0f499-193">Add the `in` modifier to pass an argument by reference and declare your design intent to pass arguments by reference to avoid unnecessary copying.</span></span> <span data-ttu-id="0f499-194">您不打算修改用來作為該引數的物件。</span><span class="sxs-lookup"><span data-stu-id="0f499-194">You don't intend to modify the object used as that argument.</span></span>

<span data-ttu-id="0f499-195">這種做法常常會改善大於 <xref:System.IntPtr.Size?displayProperty=nameWithType> 唯讀實值型別的效能。</span><span class="sxs-lookup"><span data-stu-id="0f499-195">This practice often improves performance for readonly value types that are larger than <xref:System.IntPtr.Size?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0f499-196">針對簡單型別 (`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 及 `bool` 和 `enum` 型別)，任何潛在的效能增益都非常小。</span><span class="sxs-lookup"><span data-stu-id="0f499-196">For simple types (`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` and `bool`, and `enum` types), any potential performance gains are minimal.</span></span> <span data-ttu-id="0f499-197">事實上，針對小於 <xref:System.IntPtr.Size?displayProperty=nameWithType> 的型別使用以參考傳遞可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="0f499-197">In fact, performance may degrade by using pass-by-reference for types smaller than <xref:System.IntPtr.Size?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0f499-198">下列程式碼示範計算 3D 空間中不同兩點間距離的方法。</span><span class="sxs-lookup"><span data-stu-id="0f499-198">The following code shows an example of a method that calculates the distance between two points in 3D space.</span></span>

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

<span data-ttu-id="0f499-199">引數為雙結構，每個結構皆包含三個雙精度浮點數。</span><span class="sxs-lookup"><span data-stu-id="0f499-199">The arguments are two structures that each contain three doubles.</span></span> <span data-ttu-id="0f499-200">一個雙精度浮點數是 8 個位元組，因此每個引數是 24 個位元組。</span><span class="sxs-lookup"><span data-stu-id="0f499-200">A double is 8 bytes, so each argument is 24 bytes.</span></span> <span data-ttu-id="0f499-201">藉由指定 `in` 修飾詞，您會傳遞一個 4 位元組或 8 位元組參考至那些引數，取決於電腦的架構。</span><span class="sxs-lookup"><span data-stu-id="0f499-201">By specifying the `in` modifier, you pass a 4 byte or 8-byte reference to those arguments, depending on the architecture of the machine.</span></span> <span data-ttu-id="0f499-202">大小的差異很小，但是當您的應用程式使用許多不同值在緊密迴圈中呼叫此方法時，差異便會加大。</span><span class="sxs-lookup"><span data-stu-id="0f499-202">The difference in size is small, but it adds up when your application calls this method in a tight loop using many different values.</span></span>

<span data-ttu-id="0f499-203">`in` 修飾詞也可於其他方面補足 `out` 和 `ref`。</span><span class="sxs-lookup"><span data-stu-id="0f499-203">The `in` modifier complements `out` and `ref` in other ways as well.</span></span> <span data-ttu-id="0f499-204">您無法針對差異僅為是否出現 `in`、`out` 或 `ref` 的方法來建立其多載。</span><span class="sxs-lookup"><span data-stu-id="0f499-204">You can't create overloads of a method that differ only in the presence of `in`, `out`, or `ref`.</span></span> <span data-ttu-id="0f499-205">這些新規則沿用一直以來為 `out` 和 `ref` 參數所定義的相同行為。</span><span class="sxs-lookup"><span data-stu-id="0f499-205">These new rules extend the same behavior that had always been defined for `out` and `ref` parameters.</span></span> <span data-ttu-id="0f499-206">與 `out` 和 `ref` 修飾詞相似，實值型別並非 Boxed，因為已套用了 `in` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="0f499-206">Like the `out` and `ref` modifiers, value types aren't boxed because the `in` modifier is applied.</span></span>

<span data-ttu-id="0f499-207">`in` 修飾詞可套用至任何使用下列參數的成員：方法、委派、Lambda、區域函式、索引子、運算子。</span><span class="sxs-lookup"><span data-stu-id="0f499-207">The `in` modifier may be applied to any member that takes parameters: methods, delegates, lambdas, local functions, indexers, operators.</span></span>

<span data-ttu-id="0f499-208">`in` 參數另一項功能是您可以使用常值或常數來作為 `in` 參數的引數。</span><span class="sxs-lookup"><span data-stu-id="0f499-208">Another feature of `in` parameters is that you may use literal values or constants for the argument to an `in` parameter.</span></span> <span data-ttu-id="0f499-209">此外，不同於 `ref` 或 `out` 參數，您也不需要在呼叫位置套用 `in` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="0f499-209">Also, unlike a `ref` or `out` parameter, you don't need to apply the `in` modifier at the call site.</span></span> <span data-ttu-id="0f499-210">下列程式碼示範兩種呼叫 `CalculateDistance` 方法的範例。</span><span class="sxs-lookup"><span data-stu-id="0f499-210">The following code shows you two examples of calling the `CalculateDistance` method.</span></span> <span data-ttu-id="0f499-211">第一種使用兩個利用參考傳遞的區域變數。</span><span class="sxs-lookup"><span data-stu-id="0f499-211">The first uses two local variables passed by reference.</span></span> <span data-ttu-id="0f499-212">第二種則包含建立為方法呼叫之一部份的暫存變數。</span><span class="sxs-lookup"><span data-stu-id="0f499-212">The second includes a temporary variable created as part of the method call.</span></span>

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

<span data-ttu-id="0f499-213">編譯器強制 `in` 引數唯讀性質的方式有數種。</span><span class="sxs-lookup"><span data-stu-id="0f499-213">There are several ways in which the compiler enforces the read-only nature of an `in` argument.</span></span>  <span data-ttu-id="0f499-214">首先，呼叫的方法不可直接指派到 `in` 參數。</span><span class="sxs-lookup"><span data-stu-id="0f499-214">First of all, the called method can't directly assign to an `in` parameter.</span></span> <span data-ttu-id="0f499-215">當該值為 `struct` 類型時，該方法不可直接指派到 `in` 參數的任何欄位。</span><span class="sxs-lookup"><span data-stu-id="0f499-215">It can't directly assign to any field of an `in` parameter when that value is a `struct` type.</span></span> <span data-ttu-id="0f499-216">此外，您也無法使用 `ref` 或 `out` 修飾詞，將 `in` 參數傳遞至任何方法。</span><span class="sxs-lookup"><span data-stu-id="0f499-216">In addition, you can't pass an `in` parameter to any method using the `ref` or `out` modifier.</span></span>
<span data-ttu-id="0f499-217">這些規則適用於所有 `in` 參數的欄位，提供的欄位為 `struct` 類型，且參數也為 `struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="0f499-217">These rules apply to any field of an `in` parameter, provided the field is a `struct` type and the parameter is also a `struct` type.</span></span> <span data-ttu-id="0f499-218">實際上，這些規則適用於成員存取的多個層級，提供所有成員存取層級的類型為 `structs`。</span><span class="sxs-lookup"><span data-stu-id="0f499-218">In fact, these rules apply for multiple layers of member access provided the types at all levels of member access are `structs`.</span></span>
<span data-ttu-id="0f499-219">編譯器會強制 `struct` 類型作為 `in` 引數傳遞，且其 `struct` 成員在作為引數對其他方法使用時為唯讀變數。</span><span class="sxs-lookup"><span data-stu-id="0f499-219">The compiler enforces that `struct` types passed as  `in` arguments and their `struct` members are read-only variables when used as arguments to other methods.</span></span>

<span data-ttu-id="0f499-220">使用 `in` 參數可避免製作複本可能產生的效能成本。</span><span class="sxs-lookup"><span data-stu-id="0f499-220">The use of `in` parameters can avoid the potential performance costs of making copies.</span></span> <span data-ttu-id="0f499-221">這不會變更任何方法呼叫的語意。</span><span class="sxs-lookup"><span data-stu-id="0f499-221">It doesn't change the semantics of any method call.</span></span> <span data-ttu-id="0f499-222">因此，您不需要在呼叫位置指定 `in` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="0f499-222">Therefore, you don't need to specify the `in` modifier at the call site.</span></span> <span data-ttu-id="0f499-223">在呼叫位置忽略 `in` 修飾詞，會告知編譯器可以基於下列理由製作引數的複本：</span><span class="sxs-lookup"><span data-stu-id="0f499-223">Omitting the `in` modifier at the call site informs the compiler that it's allowed to make a copy of the argument for the following reasons:</span></span>

- <span data-ttu-id="0f499-224">從引數型別至參數型別存在隱含轉換，但沒有識別轉換。</span><span class="sxs-lookup"><span data-stu-id="0f499-224">There exists an implicit conversion but not an identity conversion from the argument type to the parameter type.</span></span>
- <span data-ttu-id="0f499-225">引數為運算式，但不具有已知的儲存體變數。</span><span class="sxs-lookup"><span data-stu-id="0f499-225">The argument is an expression but doesn't have a known storage variable.</span></span>
- <span data-ttu-id="0f499-226">存在受 `in` 存在與否影響的多載。</span><span class="sxs-lookup"><span data-stu-id="0f499-226">An overload exists that differs by the presence or absence of `in`.</span></span> <span data-ttu-id="0f499-227">在此情況下，傳值多載是最佳相符項目。</span><span class="sxs-lookup"><span data-stu-id="0f499-227">In that case, the by value overload is a better match.</span></span>

<span data-ttu-id="0f499-228">當您更新現有的程式碼以使用唯讀參考引數時，這些規則相當實用。</span><span class="sxs-lookup"><span data-stu-id="0f499-228">These rules are useful as you update existing code to use read-only reference arguments.</span></span> <span data-ttu-id="0f499-229">在呼叫的方法中，您可呼叫所有使用傳值參數的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="0f499-229">Inside the called method, you can call any instance method that uses by value parameters.</span></span> <span data-ttu-id="0f499-230">在那些執行個體中，會建立 `in` 參數的複本。</span><span class="sxs-lookup"><span data-stu-id="0f499-230">In those instances, a copy of the `in` parameter is created.</span></span> <span data-ttu-id="0f499-231">因為編譯器可為任何 `in` 參數建立暫存變數，所以您也可以為任何 `in` 參數指定預設值。</span><span class="sxs-lookup"><span data-stu-id="0f499-231">Because the compiler may create a temporary variable for any `in` parameter, you can also specify default values for any `in` parameter.</span></span> <span data-ttu-id="0f499-232">下列程式碼會將原點 (點 0,0) 指定為第二個點的預設值：</span><span class="sxs-lookup"><span data-stu-id="0f499-232">The following code specifies the origin (point 0,0) as the default value for the second point:</span></span>

[!code-csharp[InArgumentDefault](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

<span data-ttu-id="0f499-233">若要強制編譯器以參考型式來傳遞唯讀引數，請在呼叫位置於引數上指定 `in` 修飾詞，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="0f499-233">To force the compiler to pass read-only arguments by reference, specify the `in` modifier on the arguments at the call site, as shown in the following code:</span></span>

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

<span data-ttu-id="0f499-234">此行為能在可提升效能時，使在大型程式碼基底中採用 `in` 參數一段時間更加輕鬆。</span><span class="sxs-lookup"><span data-stu-id="0f499-234">This behavior makes it easier to adopt `in` parameters over time in large codebases where performance gains are possible.</span></span> <span data-ttu-id="0f499-235">您必須先將 `in` 修飾詞新增至方法簽章。</span><span class="sxs-lookup"><span data-stu-id="0f499-235">You add the `in` modifier to method signatures first.</span></span> <span data-ttu-id="0f499-236">隨後便可在呼叫位置新增 `in` 修飾詞並建立 `readonly struct` 型別，避免編譯器在更多位置建立 `in` 參數的防禦性複本。</span><span class="sxs-lookup"><span data-stu-id="0f499-236">Then, you can add the `in` modifier at call sites and create `readonly struct` types to enable the compiler to avoid creating defensive copies of `in` parameters in more locations.</span></span>

<span data-ttu-id="0f499-237">參考型別或數值也可使用 `in` 參數指定。</span><span class="sxs-lookup"><span data-stu-id="0f499-237">The `in` parameter designation can also be used with reference types or numeric values.</span></span> <span data-ttu-id="0f499-238">但這兩種用法的優點皆不彰顯 (若有的話)。</span><span class="sxs-lookup"><span data-stu-id="0f499-238">However, the benefits in both cases are minimal, if any.</span></span>

## <a name="avoid-mutable-structs-as-an-in-argument"></a><span data-ttu-id="0f499-239">避免將可變結構作為`in`參數</span><span class="sxs-lookup"><span data-stu-id="0f499-239">Avoid mutable structs as an `in` argument</span></span>

<span data-ttu-id="0f499-240">以上所述的技術解釋了如何透過傳回參考及以參考型式傳遞值來避免複製。</span><span class="sxs-lookup"><span data-stu-id="0f499-240">The techniques described above explain how to avoid copies by returning references and passing values by reference.</span></span> <span data-ttu-id="0f499-241">這些技術在引數型別宣告為 `readonly struct` 型別時的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="0f499-241">These techniques work best when the argument types are declared as `readonly struct` types.</span></span> <span data-ttu-id="0f499-242">否則，編譯器必須在許多情況中建立**防禦性複本**，強制實施任何引數的唯讀性。</span><span class="sxs-lookup"><span data-stu-id="0f499-242">Otherwise, the compiler must create **defensive copies** in many situations to enforce the readonly-ness of any arguments.</span></span> <span data-ttu-id="0f499-243">請考慮下列範例，該範例會計算原點至 3D 點的距離：</span><span class="sxs-lookup"><span data-stu-id="0f499-243">Consider the following example that calculates the distance of a 3D point from the origin:</span></span>

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

<span data-ttu-id="0f499-244">`Point3D` 結構「不是」\*\* 唯讀結構。</span><span class="sxs-lookup"><span data-stu-id="0f499-244">The `Point3D` structure is *not* a readonly struct.</span></span> <span data-ttu-id="0f499-245">此方法的主體中有六個不同屬性存取呼叫。</span><span class="sxs-lookup"><span data-stu-id="0f499-245">There are six different property access calls in the body of this method.</span></span> <span data-ttu-id="0f499-246">在第一次檢查中，您可能會認為這些存取都是安全的。</span><span class="sxs-lookup"><span data-stu-id="0f499-246">On first examination, you may have thought these accesses were safe.</span></span> <span data-ttu-id="0f499-247">畢竟，`get` 存取子應該不會修改物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="0f499-247">After all, a `get` accessor shouldn't modify the state of the object.</span></span> <span data-ttu-id="0f499-248">但是沒有任何語言規則強制該行為。</span><span class="sxs-lookup"><span data-stu-id="0f499-248">But there's no language rule that enforces that.</span></span> <span data-ttu-id="0f499-249">它只是一個常見的慣例。</span><span class="sxs-lookup"><span data-stu-id="0f499-249">It's only a common convention.</span></span> <span data-ttu-id="0f499-250">任何型別都可實作修改內部狀態的 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="0f499-250">Any type could implement a `get` accessor that modified the internal state.</span></span> <span data-ttu-id="0f499-251">如果沒有某些語言保證，編譯器必須先創建參數的臨時副本，然後才能調用未標記`readonly`修改器的任何成員。</span><span class="sxs-lookup"><span data-stu-id="0f499-251">Without some language guarantee, the compiler must create a temporary copy of the argument before calling any member not marked with the `readonly` modifier.</span></span> <span data-ttu-id="0f499-252">暫存位置會在堆疊上建立，引數的值則會複製到暫存位置，而該值則會針對每個成員存取，作為 `this` 引數複製到堆疊。</span><span class="sxs-lookup"><span data-stu-id="0f499-252">The temporary storage is created on the stack, the values of the argument are copied to the temporary storage, and the value is copied to the stack for each member access as the `this` argument.</span></span> <span data-ttu-id="0f499-253">在許多情況下，這些副本對性能的損害足夠大，當參數類型不是 ，`readonly struct`並且方法調用未標記`readonly`的成員 時，逐個值傳遞比逐讀引用更快。</span><span class="sxs-lookup"><span data-stu-id="0f499-253">In many situations, these copies harm performance enough that pass-by-value is faster than pass-by-readonly-reference when the argument type isn't a `readonly struct` and the method calls members that aren't marked `readonly`.</span></span> <span data-ttu-id="0f499-254">如果將不修改結構狀態的所有方法標記為`readonly`，編譯器可以安全地確定結構狀態未修改，並且不需要防禦性副本。</span><span class="sxs-lookup"><span data-stu-id="0f499-254">If you mark all methods that don't modify the struct state as `readonly`, the compiler can safely determine that the struct state isn't modified, and a defensive copy is not needed.</span></span>

<span data-ttu-id="0f499-255">相反，如果距離計算使用不可變結構，`ReadonlyPoint3D`則不需要 臨時物件：</span><span class="sxs-lookup"><span data-stu-id="0f499-255">Instead, if the distance calculation uses the immutable struct, `ReadonlyPoint3D`, temporary objects aren't needed:</span></span>

[!code-csharp[readonlyInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

<span data-ttu-id="0f499-256">當您調用`readonly struct`：`this`的成員時，編譯器會生成更高效的代碼，引用（而不是接收方的副本）始終是通過引用成員方法`in`傳遞的參數。</span><span class="sxs-lookup"><span data-stu-id="0f499-256">The compiler generates more efficient code when you call members of a `readonly struct`: The `this` reference, instead of a copy of the receiver, is always an `in` parameter passed by reference to the member method.</span></span> <span data-ttu-id="0f499-257">當您使用 `readonly struct` 作為 `in` 引數時，這項最佳化可避免進行複製。</span><span class="sxs-lookup"><span data-stu-id="0f499-257">This optimization saves copying when you use a `readonly struct` as an `in` argument.</span></span>

<span data-ttu-id="0f499-258">不應將空數值型別作為參數傳遞`in`。</span><span class="sxs-lookup"><span data-stu-id="0f499-258">You shouldn't pass a nullable value type as an `in` argument.</span></span> <span data-ttu-id="0f499-259">類型<xref:System.Nullable%601>未聲明為唯讀結構。</span><span class="sxs-lookup"><span data-stu-id="0f499-259">The <xref:System.Nullable%601> type isn't declared as a read-only struct.</span></span> <span data-ttu-id="0f499-260">這表示，編譯器編譯器必須針對使用參數宣告上 `in` 修飾詞傳遞給方法之任何可為 Null 的實值型別引數來產生防禦性複本。</span><span class="sxs-lookup"><span data-stu-id="0f499-260">That means the compiler must generate defensive copies for any nullable value type argument passed to a method using the `in` modifier on the parameter declaration.</span></span>

<span data-ttu-id="0f499-261">您可以在 GitHub 上的[示例存儲庫](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark)中看到使用[基準DotNet](https://www.nuget.org/packages/BenchmarkDotNet/)演示性能差異的示常式序。</span><span class="sxs-lookup"><span data-stu-id="0f499-261">You can see an example program that demonstrates the performance differences using [BenchmarkDotNet](https://www.nuget.org/packages/BenchmarkDotNet/) in our [samples repository](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) on GitHub.</span></span> <span data-ttu-id="0f499-262">它會比較以值型式和以參考型式傳遞可變動結構，以及以值型式和以參考型式傳遞固定結構的差異。</span><span class="sxs-lookup"><span data-stu-id="0f499-262">It compares passing a mutable struct by value and by reference with passing an immutable struct by value and by reference.</span></span> <span data-ttu-id="0f499-263">使用固定結構並以參考型式傳遞的速度最快。</span><span class="sxs-lookup"><span data-stu-id="0f499-263">The use of the immutable struct and pass by reference is fastest.</span></span>

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a><span data-ttu-id="0f499-264">使用 `ref struct` 型別來使用單一堆疊框架上的區塊或記憶體</span><span class="sxs-lookup"><span data-stu-id="0f499-264">Use `ref struct` types to work with blocks or memory on a single stack frame</span></span>

<span data-ttu-id="0f499-265">另一項相關語言功能是可宣告實值型別必須限制在單一堆疊框架的能力。</span><span class="sxs-lookup"><span data-stu-id="0f499-265">A related language feature is the ability to declare a value type that must be constrained to a single stack frame.</span></span> <span data-ttu-id="0f499-266">此限制可讓編譯器進行幾項最佳化。</span><span class="sxs-lookup"><span data-stu-id="0f499-266">This restriction enables the compiler to make several optimizations.</span></span> <span data-ttu-id="0f499-267">此功能的主要動機是 <xref:System.Span%601> 及相關的結構。</span><span class="sxs-lookup"><span data-stu-id="0f499-267">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span> <span data-ttu-id="0f499-268">您可以透過使用新的及已更新 .NET API，利用 <xref:System.Span%601> 型別以透過這些增強功能來改善效能。</span><span class="sxs-lookup"><span data-stu-id="0f499-268">You'll achieve performance improvements from these enhancements by using new and updated .NET APIs that make use of the <xref:System.Span%601> type.</span></span>

<span data-ttu-id="0f499-269">您可能有類似的要求，使用使用或使用[`stackalloc`](language-reference/operators/stackalloc.md)來自互通 API 的記憶體時創建的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0f499-269">You may have similar requirements working with memory created using [`stackalloc`](language-reference/operators/stackalloc.md) or when using memory from interop APIs.</span></span> <span data-ttu-id="0f499-270">您可依照那些需求定義自己的 `ref struct` 類型。</span><span class="sxs-lookup"><span data-stu-id="0f499-270">You can define your own `ref struct` types for those needs.</span></span>

## <a name="readonly-ref-struct-type"></a><span data-ttu-id="0f499-271">`readonly ref struct` 類型</span><span class="sxs-lookup"><span data-stu-id="0f499-271">`readonly ref struct` type</span></span>

<span data-ttu-id="0f499-272">宣告結構為 `readonly ref` 會結合 `ref struct` 與 `readonly struct` 宣告的優點與限制。</span><span class="sxs-lookup"><span data-stu-id="0f499-272">Declaring a struct as `readonly ref` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span> <span data-ttu-id="0f499-273">唯讀範圍所使用的記憶體會限制在單一堆疊框架，且唯讀範圍使用的記憶體無法修改。</span><span class="sxs-lookup"><span data-stu-id="0f499-273">The memory used by the readonly span is restricted to a single stack frame, and the memory used by the readonly span can't be modified.</span></span>

## <a name="conclusions"></a><span data-ttu-id="0f499-274">結論</span><span class="sxs-lookup"><span data-stu-id="0f499-274">Conclusions</span></span>

<span data-ttu-id="0f499-275">使用實值型別可將配置作業的次數降至最低：</span><span class="sxs-lookup"><span data-stu-id="0f499-275">Using value types minimizes the number of allocation operations:</span></span>

- <span data-ttu-id="0f499-276">實值型別儲存體是為區域變數和方法引數配置的堆疊。</span><span class="sxs-lookup"><span data-stu-id="0f499-276">Storage for value types is stack allocated for local variables and method arguments.</span></span>
- <span data-ttu-id="0f499-277">作為其他物件成員的實值型別，其儲存體會作為該物件的一部分進行配置，而非個別配置。</span><span class="sxs-lookup"><span data-stu-id="0f499-277">Storage for value types that are members of other objects is allocated as part of that object, not as a separate allocation.</span></span>
- <span data-ttu-id="0f499-278">實值型別傳回值的儲存體是所配置堆疊。</span><span class="sxs-lookup"><span data-stu-id="0f499-278">Storage for value type return values is stack allocated.</span></span>

<span data-ttu-id="0f499-279">在相同情況下，與參考型別的對比是：</span><span class="sxs-lookup"><span data-stu-id="0f499-279">Contrast that with reference types in those same situations:</span></span>

- <span data-ttu-id="0f499-280">參考型別儲存體是為區域變數和方法引數配置的堆積。</span><span class="sxs-lookup"><span data-stu-id="0f499-280">Storage for reference types are heap allocated for local variables and method arguments.</span></span> <span data-ttu-id="0f499-281">參考會儲存在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="0f499-281">The reference is stored on the stack.</span></span>
- <span data-ttu-id="0f499-282">作為其他物件成員的參考型別，其儲存體會在堆積上個別配置。</span><span class="sxs-lookup"><span data-stu-id="0f499-282">Storage for reference types that are members of other objects are separately allocated on the heap.</span></span> <span data-ttu-id="0f499-283">包含該型別的物件會儲存參考。</span><span class="sxs-lookup"><span data-stu-id="0f499-283">The containing object stores the reference.</span></span>
- <span data-ttu-id="0f499-284">參考型別傳回值的儲存體是所配置堆積。</span><span class="sxs-lookup"><span data-stu-id="0f499-284">Storage for reference type return values is heap allocated.</span></span> <span data-ttu-id="0f499-285">該儲存體的參考會儲存在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="0f499-285">The reference to that storage is stored on the stack.</span></span>

<span data-ttu-id="0f499-286">最小化配置也包含了取捨。</span><span class="sxs-lookup"><span data-stu-id="0f499-286">Minimizing allocations comes with tradeoffs.</span></span> <span data-ttu-id="0f499-287">您會在 `struct` 的大小大於參考的大小時複製更多記憶體。</span><span class="sxs-lookup"><span data-stu-id="0f499-287">You copy more memory when the size of the `struct` is larger than the size of a reference.</span></span> <span data-ttu-id="0f499-288">參考通常是 64 位元或 32 位元，取決於目標電腦的 CPU。</span><span class="sxs-lookup"><span data-stu-id="0f499-288">A reference is typically 64 bits or 32 bits, and depends on the target machine CPU.</span></span>

<span data-ttu-id="0f499-289">這些取捨通常只會對效能造成極小的影響。</span><span class="sxs-lookup"><span data-stu-id="0f499-289">These tradeoffs generally have minimal performance impact.</span></span> <span data-ttu-id="0f499-290">但是，針對大型結構或較大的集合，對效能產生的影響便會增加。</span><span class="sxs-lookup"><span data-stu-id="0f499-290">However, for large structs or larger collections, the performance impact increases.</span></span> <span data-ttu-id="0f499-291">在緊密迴圈或程式的最忙碌路徑中，影響可能會很大。</span><span class="sxs-lookup"><span data-stu-id="0f499-291">The impact can be large in tight loops and hot paths for programs.</span></span>

<span data-ttu-id="0f499-292">這些 C# 語言的增強功能專為注重效能的演算法設計，對於這些演算法來說，最小化記憶體配置在達到所需效能的過程中扮演了重要角色。</span><span class="sxs-lookup"><span data-stu-id="0f499-292">These enhancements to the C# language are designed for performance critical algorithms where minimizing memory allocations is a major factor in achieving the necessary performance.</span></span> <span data-ttu-id="0f499-293">您會發現到您不常在您撰寫的程式碼中使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="0f499-293">You may find that you don't often use these features in the code you write.</span></span> <span data-ttu-id="0f499-294">但是，您已透過 .NET 採用了這些增強功能。</span><span class="sxs-lookup"><span data-stu-id="0f499-294">However, these enhancements have been adopted throughout .NET.</span></span> <span data-ttu-id="0f499-295">隨著愈來愈多的 API 利用這些功能，您會發現自己的應用程式效能有所改善。</span><span class="sxs-lookup"><span data-stu-id="0f499-295">As more and more APIs make use of these features, you'll see the performance of your applications improve.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f499-296">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f499-296">See also</span></span>

- [<span data-ttu-id="0f499-297">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="0f499-297">ref keyword</span></span>](language-reference/keywords/ref.md)
- [<span data-ttu-id="0f499-298">ref 傳回值和 ref 區域變數</span><span class="sxs-lookup"><span data-stu-id="0f499-298">Ref returns and ref locals</span></span>](programming-guide/classes-and-structs/ref-returns.md)
