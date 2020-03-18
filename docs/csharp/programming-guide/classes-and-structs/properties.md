---
title: 屬性 - C# 程式設計手冊
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: ee530e981e0c85302b2b11cc739d6c51d6650ddd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170100"
---
# <a name="properties-c-programming-guide"></a><span data-ttu-id="20b7f-102">屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="20b7f-102">Properties (C# Programming Guide)</span></span>

<span data-ttu-id="20b7f-103">屬性是提供彈性機制以讀取、寫入或計算私用欄位值的成員。</span><span class="sxs-lookup"><span data-stu-id="20b7f-103">A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field.</span></span> <span data-ttu-id="20b7f-104">使用屬性時可將其視為公用資料成員，但實際上屬性是名為「存取子」\*\* 的特殊方法。</span><span class="sxs-lookup"><span data-stu-id="20b7f-104">Properties can be used as if they are public data members, but they are actually special methods called *accessors*.</span></span> <span data-ttu-id="20b7f-105">如此可讓資料更容易存取，同時有助於提升方法的安全性和彈性。</span><span class="sxs-lookup"><span data-stu-id="20b7f-105">This enables data to be accessed easily and still helps promote the safety and flexibility of methods.</span></span>  

## <a name="properties-overview"></a><span data-ttu-id="20b7f-106">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="20b7f-106">Properties overview</span></span>  
  
- <span data-ttu-id="20b7f-107">屬性可讓類別公開取得和設定值的公用方式，同時隱藏實作或驗證程式碼。</span><span class="sxs-lookup"><span data-stu-id="20b7f-107">Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.</span></span>  
  
- <span data-ttu-id="20b7f-108">[get](../../language-reference/keywords/get.md) 屬性存取子可用來傳回屬性值，而 [set](../../language-reference/keywords/set.md) 屬性存取子則用來指派新值。</span><span class="sxs-lookup"><span data-stu-id="20b7f-108">A [get](../../language-reference/keywords/get.md) property accessor is used to return the property value, and a [set](../../language-reference/keywords/set.md) property accessor is used to assign a new value.</span></span> <span data-ttu-id="20b7f-109">這些存取子可以有不同的存取層級。</span><span class="sxs-lookup"><span data-stu-id="20b7f-109">These accessors can have different access levels.</span></span> <span data-ttu-id="20b7f-110">如需詳細資訊，請參閱[限制存取子的存取範圍](./restricting-accessor-accessibility.md)。</span><span class="sxs-lookup"><span data-stu-id="20b7f-110">For more information, see [Restricting Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
- <span data-ttu-id="20b7f-111">[value`set` 關鍵字是用來定義 ](../../language-reference/keywords/value.md) 存取子要指派的值。</span><span class="sxs-lookup"><span data-stu-id="20b7f-111">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` accessor.</span></span>  
- <span data-ttu-id="20b7f-112">屬性可以是「讀寫」**(同時具有 `get` 和 `set` 存取子)、「唯讀」**(具有 `get` 存取子但沒有 `set` 存取子) 或「唯寫」\*\*(具有 `set` 存取子但沒有 `get` 存取子)。</span><span class="sxs-lookup"><span data-stu-id="20b7f-112">Properties can be *read-write* (they have both a `get` and a `set` accessor), *read-only* (they have a `get` accessor but no `set` accessor), or *write-only* (they have a `set` accessor, but no `get` accessor).</span></span> <span data-ttu-id="20b7f-113">唯寫屬性很少見，而且最常用來限制對機密資料的存取。</span><span class="sxs-lookup"><span data-stu-id="20b7f-113">Write-only properties are rare and are most commonly used to restrict access to sensitive data.</span></span>

- <span data-ttu-id="20b7f-114">不需要自訂存取子程式碼的簡單屬性，則可以實作為運算式主體定義或[自動實作屬性](./auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="20b7f-114">Simple properties that require no custom accessor code can be implemented either as expression body definitions or as [auto-implemented properties](./auto-implemented-properties.md).</span></span>

## <a name="properties-with-backing-fields"></a><span data-ttu-id="20b7f-115">含有支援欄位的屬性</span><span class="sxs-lookup"><span data-stu-id="20b7f-115">Properties with backing fields</span></span>

<span data-ttu-id="20b7f-116">實作屬性的一種基本模式需要使用私用支援欄位，來設定和擷取屬性值。</span><span class="sxs-lookup"><span data-stu-id="20b7f-116">One basic pattern for implementing a property involves using a private backing field for setting and retrieving the property value.</span></span> <span data-ttu-id="20b7f-117">`get` 存取子會傳回私用欄位的值，而 `set` 存取子則可能會執行一些資料驗證，再將值指派給私用欄位。</span><span class="sxs-lookup"><span data-stu-id="20b7f-117">The `get` accessor returns the value of the private field, and the `set` accessor may perform some data validation before assigning a value to the private field.</span></span> <span data-ttu-id="20b7f-118">這兩個存取子也可能會對資料執行一些轉換或計算，再儲存或傳回資料。</span><span class="sxs-lookup"><span data-stu-id="20b7f-118">Both accessors may also perform some conversion or computation on the data before it is stored or returned.</span></span>

<span data-ttu-id="20b7f-119">下列範例將示範這個模式。</span><span class="sxs-lookup"><span data-stu-id="20b7f-119">The following example illustrates this pattern.</span></span> <span data-ttu-id="20b7f-120">在此範例中，`TimePeriod` 類別代表時間間隔。</span><span class="sxs-lookup"><span data-stu-id="20b7f-120">In this example, the `TimePeriod` class represents an interval of time.</span></span> <span data-ttu-id="20b7f-121">就內部而言，此類別會將時間間隔 (秒) 儲存在名為 `_seconds` 的私用欄位中。</span><span class="sxs-lookup"><span data-stu-id="20b7f-121">Internally, the class stores the time interval in seconds in a private field named `_seconds`.</span></span> <span data-ttu-id="20b7f-122">名為 `Hours` 的讀寫屬性可讓客戶以小時為單位指定時間間隔。</span><span class="sxs-lookup"><span data-stu-id="20b7f-122">A read-write property named `Hours` allows the customer to specify the time interval in hours.</span></span> <span data-ttu-id="20b7f-123">`get` 和 `set` 存取子都會執行小時與秒之間的必要轉換。</span><span class="sxs-lookup"><span data-stu-id="20b7f-123">Both the `get` and the `set` accessors perform the necessary conversion between hours and seconds.</span></span> <span data-ttu-id="20b7f-124">此外，`set` 存取子會驗證資料，並在小時數無效時擲回 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="20b7f-124">In addition, the `set` accessor validates the data and throws an <xref:System.ArgumentOutOfRangeException> if the number of hours is invalid.</span></span>

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="20b7f-125">運算式主體定義</span><span class="sxs-lookup"><span data-stu-id="20b7f-125">Expression body definitions</span></span>  

 <span data-ttu-id="20b7f-126">屬性存取子通常是由只會指派或傳回運算式結果的單行陳述式所組成。</span><span class="sxs-lookup"><span data-stu-id="20b7f-126">Property accessors often consist of single-line statements that just assign or return the result of an expression.</span></span> <span data-ttu-id="20b7f-127">您可以將這些屬性實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="20b7f-127">You can implement these properties as expression-bodied members.</span></span> <span data-ttu-id="20b7f-128">運算式主體定義包含 `=>` 符號，後面接著要從屬性指派或擷取的運算式。</span><span class="sxs-lookup"><span data-stu-id="20b7f-128">Expression body definitions consist of the `=>` symbol followed by the expression to assign to or retrieve from the property.</span></span>

 <span data-ttu-id="20b7f-129">從 C# 6 開始，唯讀屬性可將 `get` 存取子實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="20b7f-129">Starting with C# 6, read-only properties can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="20b7f-130">在此情況下，不會使用 `get` 存取子關鍵字和 `return` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="20b7f-130">In this case, neither the `get` accessor keyword nor the `return` keyword is used.</span></span> <span data-ttu-id="20b7f-131">下列範例會將唯讀 `Name` 屬性實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="20b7f-131">The following example implements the read-only `Name` property as an expression-bodied member.</span></span>

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 <span data-ttu-id="20b7f-132">從 C# 7.0 開始，可同時將 `get` 和 `set` 存取子實作為運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="20b7f-132">Starting with C# 7.0, both the `get` and the `set` accessor can be implemented as expression-bodied members.</span></span> <span data-ttu-id="20b7f-133">在此情況下，必須同時有 `get` 和 `set` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="20b7f-133">In this case, the `get` and `set` keywords must be present.</span></span> <span data-ttu-id="20b7f-134">下列範例說明如何使用運算式主體定義來表示這兩個存取子。</span><span class="sxs-lookup"><span data-stu-id="20b7f-134">The following example illustrates the use of expression body definitions for both accessors.</span></span> <span data-ttu-id="20b7f-135">請注意，`return` 關鍵字不能搭配 `get` 存取子使用。</span><span class="sxs-lookup"><span data-stu-id="20b7f-135">Note that the `return` keyword is not used with the `get` accessor.</span></span>

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a><span data-ttu-id="20b7f-136">自動實作屬性</span><span class="sxs-lookup"><span data-stu-id="20b7f-136">Auto-implemented properties</span></span>

<span data-ttu-id="20b7f-137">在某些情況下，屬性 `get` 和 `set` 存取子只會指派值給支援欄位，或從支援欄位中擷取值，而不會包含任何其他邏輯。</span><span class="sxs-lookup"><span data-stu-id="20b7f-137">In some cases, property `get` and `set` accessors just assign a value to or retrieve a value from a backing field without including any additional logic.</span></span> <span data-ttu-id="20b7f-138">藉由使用自動實作屬性，您可以簡化程式碼，同時讓 C# 編譯器無障礙地為您提供支援欄位。</span><span class="sxs-lookup"><span data-stu-id="20b7f-138">By using auto-implemented properties, you can simplify your code while having the C# compiler transparently provide the backing field for you.</span></span>

<span data-ttu-id="20b7f-139">如果屬性具有 `get` 和 `set` 存取子，這兩者都必須自動實作。</span><span class="sxs-lookup"><span data-stu-id="20b7f-139">If a property has both a `get` and a `set` accessor, both must be auto-implemented.</span></span> <span data-ttu-id="20b7f-140">您可以使用 `get` 和 `set` 關鍵字，但不提供任何實作，來定義自動實作屬性。</span><span class="sxs-lookup"><span data-stu-id="20b7f-140">You define an auto-implemented property by using the `get` and `set` keywords without providing any implementation.</span></span> <span data-ttu-id="20b7f-141">下列範例會重複上一個範例，不同之處在於 `Name` 和 `Price` 為自動實作屬性。</span><span class="sxs-lookup"><span data-stu-id="20b7f-141">The following example repeats the previous one, except that `Name` and `Price` are auto-implemented properties.</span></span> <span data-ttu-id="20b7f-142">請注意，此範例也會移除參數化建構函式，因此 `SaleItem` 物件現在會透過呼叫無參數建構函式和[物件初始設定式](object-and-collection-initializers.md)來初始化。</span><span class="sxs-lookup"><span data-stu-id="20b7f-142">Note that the example also removes the parameterized constructor, so that `SaleItem` objects are now initialized with a call to the parameterless constructor and an [object initializer](object-and-collection-initializers.md).</span></span>

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a><span data-ttu-id="20b7f-143">相關章節</span><span class="sxs-lookup"><span data-stu-id="20b7f-143">Related sections</span></span>  
  
- [<span data-ttu-id="20b7f-144">使用屬性</span><span class="sxs-lookup"><span data-stu-id="20b7f-144">Using Properties</span></span>](./using-properties.md)  
  
- [<span data-ttu-id="20b7f-145">介面屬性</span><span class="sxs-lookup"><span data-stu-id="20b7f-145">Interface Properties</span></span>](./interface-properties.md)  
  
- [<span data-ttu-id="20b7f-146">屬性與索引子之間的比較</span><span class="sxs-lookup"><span data-stu-id="20b7f-146">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="20b7f-147">限制存取子的存取範圍</span><span class="sxs-lookup"><span data-stu-id="20b7f-147">Restricting Accessor Accessibility</span></span>](./restricting-accessor-accessibility.md)  
  
- [<span data-ttu-id="20b7f-148">自動實現屬性</span><span class="sxs-lookup"><span data-stu-id="20b7f-148">Auto-Implemented Properties</span></span>](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="20b7f-149">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="20b7f-149">C# Language Specification</span></span>  

<span data-ttu-id="20b7f-150">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[屬性](~/_csharplang/spec/classes.md#properties)。</span><span class="sxs-lookup"><span data-stu-id="20b7f-150">For more information, see [Properties](~/_csharplang/spec/classes.md#properties) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="20b7f-151">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="20b7f-151">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="20b7f-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20b7f-152">See also</span></span>

- [<span data-ttu-id="20b7f-153">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="20b7f-153">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="20b7f-154">使用屬性</span><span class="sxs-lookup"><span data-stu-id="20b7f-154">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="20b7f-155">索引子</span><span class="sxs-lookup"><span data-stu-id="20b7f-155">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="20b7f-156">get 關鍵字</span><span class="sxs-lookup"><span data-stu-id="20b7f-156">get keyword</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="20b7f-157">set 關鍵字</span><span class="sxs-lookup"><span data-stu-id="20b7f-157">set keyword</span></span>](../../language-reference/keywords/set.md)
