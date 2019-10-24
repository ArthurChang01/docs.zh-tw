---
title: 使用結構 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 8b2810af81a57cf21b9a2e2438f7f6aa2cb7a669
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772077"
---
# <a name="using-structs-c-programming-guide"></a><span data-ttu-id="9778a-102">使用結構（C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="9778a-102">Using structs (C# Programming Guide)</span></span>

<span data-ttu-id="9778a-103">`struct` 類型很適合用於代表輕量型物件，例如 `Point`、 `Rectangle`和 `Color`。</span><span class="sxs-lookup"><span data-stu-id="9778a-103">The `struct` type is suitable for representing lightweight objects such as `Point`, `Rectangle`, and `Color`.</span></span> <span data-ttu-id="9778a-104">雖然使用 [自動實作的屬性](../../language-reference/keywords/class.md) 可以輕鬆地將一個點表示為一個 [類別](./auto-implemented-properties.md)，但是在某些情節中 [結構](../../language-reference/keywords/struct.md) 可能會更有效率。</span><span class="sxs-lookup"><span data-stu-id="9778a-104">Although it is just as convenient to represent a point as a [class](../../language-reference/keywords/class.md) with [Auto-Implemented Properties](./auto-implemented-properties.md), a [struct](../../language-reference/keywords/struct.md) might be more efficient in some scenarios.</span></span> <span data-ttu-id="9778a-105">例如，如果您宣告含有 1000 個 `Point` 物件的陣列，您會配置額外的記憶體來參考每個物件；在此案例下，結構所耗用的記憶體會較少。</span><span class="sxs-lookup"><span data-stu-id="9778a-105">For example, if you declare an array of 1000 `Point` objects, you will allocate additional memory for referencing each object; in this case, a struct would be less expensive.</span></span> <span data-ttu-id="9778a-106">因為 .NET Framework 包含名為 <xref:System.Drawing.Point> 的物件，所以這個範例中的結構會改命名為 `Coords`。</span><span class="sxs-lookup"><span data-stu-id="9778a-106">Because the .NET Framework contains an object called <xref:System.Drawing.Point>, the struct in this example is named `Coords` instead.</span></span>

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

<span data-ttu-id="9778a-107">定義結構的無參數的函式是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="9778a-107">It is an error to define a parameterless constructor for a struct.</span></span> <span data-ttu-id="9778a-108">初始化結構主體中的執行個體欄位時也會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9778a-108">It is also an error to initialize an instance field in a struct body.</span></span> <span data-ttu-id="9778a-109">您只能透過使用參數化建構函式、隱含的無參數建構函式、[物件初始設定式](object-and-collection-initializers.md)，或在宣告結構後個別存取成員，初始化可外部存取的結構成員。</span><span class="sxs-lookup"><span data-stu-id="9778a-109">You can initialize externally accessible struct members only by using a parameterized constructor, the implicit, parameterless constructor, an [object initializer](object-and-collection-initializers.md), or by accessing the members individually after the struct is declared.</span></span> <span data-ttu-id="9778a-110">任何私用或無法以其他方式存取的成員都需要建構函式的專屬使用。</span><span class="sxs-lookup"><span data-stu-id="9778a-110">Any private or otherwise inaccessible members require the use of constructors exclusively.</span></span>

<span data-ttu-id="9778a-111">當您使用 [new](../../language-reference/operators/new-operator.md) 運算子建立結構物件時，不僅會建立物件，還會根據[建構函式的簽章](constructors.md#constructor-syntax)呼叫適當的建構函式。</span><span class="sxs-lookup"><span data-stu-id="9778a-111">When you create a struct object using the [new](../../language-reference/operators/new-operator.md) operator, it gets created and the appropriate constructor is called according to the [constructor's signature](constructors.md#constructor-syntax).</span></span> <span data-ttu-id="9778a-112">不同於類別，結構不需要使用 `new` 運算子就能具現化。</span><span class="sxs-lookup"><span data-stu-id="9778a-112">Unlike classes, structs can be instantiated without using the `new` operator.</span></span> <span data-ttu-id="9778a-113">在此案例下，不會有建構函式呼叫，因此配置會更有效率。</span><span class="sxs-lookup"><span data-stu-id="9778a-113">In such a case, there is no constructor call, which makes the allocation more efficient.</span></span> <span data-ttu-id="9778a-114">不過，欄位會維持未指派狀態，而且必須等到所有欄位都初始化後才能使用物件。</span><span class="sxs-lookup"><span data-stu-id="9778a-114">However, the fields will remain unassigned and the object cannot be used until all of the fields are initialized.</span></span> <span data-ttu-id="9778a-115">這包括無法透過屬性取得或設定值。</span><span class="sxs-lookup"><span data-stu-id="9778a-115">This includes the inability to get or set values through properties.</span></span>

<span data-ttu-id="9778a-116">如果您使用無參數的函式來具現化結構物件，則會根據[預設值](../../language-reference/keywords/default-values-table.md)來指派所有成員。</span><span class="sxs-lookup"><span data-stu-id="9778a-116">If you instantiate a struct object using the parameterless constructor, all members are assigned according to their [default values](../../language-reference/keywords/default-values-table.md).</span></span>

<span data-ttu-id="9778a-117">撰寫具有結構參數的處理常式時，您必須明確初始化所有成員;否則，一或多個成員會維持未指派狀態，而且無法使用結構，因而產生編譯器錯誤[CS0171](../../misc/cs0171.md)。</span><span class="sxs-lookup"><span data-stu-id="9778a-117">When writing a constructor with parameters for a struct, you must explicitly initialize all members; otherwise one or more members remain unassigned and the struct cannot be used, producing compiler error [CS0171](../../misc/cs0171.md).</span></span>

<span data-ttu-id="9778a-118">不同於類別，結構沒有繼承。</span><span class="sxs-lookup"><span data-stu-id="9778a-118">There is no inheritance for structs as there is for classes.</span></span> <span data-ttu-id="9778a-119">結構無法繼承自另一個結構或類別，而且不能作為類別的基底。</span><span class="sxs-lookup"><span data-stu-id="9778a-119">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="9778a-120">不過，結構可以繼承自基底類別 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="9778a-120">Structs, however, inherit from the base class <xref:System.Object>.</span></span> <span data-ttu-id="9778a-121">結構可以實作介面，而且其作法就跟類別一樣。</span><span class="sxs-lookup"><span data-stu-id="9778a-121">A struct can implement interfaces, and it does that exactly as classes do.</span></span>

<span data-ttu-id="9778a-122">您無法使用關鍵字 `struct`宣告類別。</span><span class="sxs-lookup"><span data-stu-id="9778a-122">You cannot declare a class using the keyword `struct`.</span></span> <span data-ttu-id="9778a-123">在 C# 中，類別和結構在語意上是不同的。</span><span class="sxs-lookup"><span data-stu-id="9778a-123">In C#, classes and structs are semantically different.</span></span> <span data-ttu-id="9778a-124">結構是實值類型，而類別是參考類型。</span><span class="sxs-lookup"><span data-stu-id="9778a-124">A struct is a value type, while a class is a reference type.</span></span> <span data-ttu-id="9778a-125">如需詳細資訊，請參閱實[數值型別](../../language-reference/keywords/value-types.md)和[參考型別](../../language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9778a-125">For more information, see [Value types](../../language-reference/keywords/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>

<span data-ttu-id="9778a-126">除非您需要參考類型語意，否則系統處理小型類別可能會更有效率 (如果您改為將其宣告為結構)。</span><span class="sxs-lookup"><span data-stu-id="9778a-126">Unless you need reference-type semantics, a small class may be more efficiently handled by the system if you declare it as a struct instead.</span></span>

## <a name="example-1"></a><span data-ttu-id="9778a-127">範例 1</span><span class="sxs-lookup"><span data-stu-id="9778a-127">Example 1</span></span>

<span data-ttu-id="9778a-128">這個範例示範如何使用無參數和參數化的函式來 `struct` 初始化。</span><span class="sxs-lookup"><span data-stu-id="9778a-128">This example demonstrates `struct` initialization using both parameterless and parameterized constructors.</span></span>

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]

## <a name="example-2"></a><span data-ttu-id="9778a-129">範例 2</span><span class="sxs-lookup"><span data-stu-id="9778a-129">Example 2</span></span>

<span data-ttu-id="9778a-130">此範例示範結構特有的功能。</span><span class="sxs-lookup"><span data-stu-id="9778a-130">This example demonstrates a feature that is unique to structs.</span></span> <span data-ttu-id="9778a-131">其無須使用 `new` 運算子就能建立 Coords 物件。</span><span class="sxs-lookup"><span data-stu-id="9778a-131">It creates a Coords object without using the `new` operator.</span></span> <span data-ttu-id="9778a-132">如果您以 `class` 一字取代 `struct` 一字，將不會編譯程式。</span><span class="sxs-lookup"><span data-stu-id="9778a-132">If you replace the word `struct` with the word `class`, the program will not compile.</span></span>

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]

## <a name="see-also"></a><span data-ttu-id="9778a-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="9778a-133">See also</span></span>

- [<span data-ttu-id="9778a-134">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9778a-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9778a-135">類別和結構</span><span class="sxs-lookup"><span data-stu-id="9778a-135">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="9778a-136">結構</span><span class="sxs-lookup"><span data-stu-id="9778a-136">Structs</span></span>](structs.md)
