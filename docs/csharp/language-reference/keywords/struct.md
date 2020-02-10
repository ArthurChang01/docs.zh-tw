---
title: struct - C# 參考
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 77d5c83dd4c81b96bc62ace6e609db8bc411dc41
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093158"
---
# <a name="struct-c-reference"></a><span data-ttu-id="15faf-102">struct (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="15faf-102">struct (C# Reference)</span></span>

<span data-ttu-id="15faf-103">`struct` 類型是實值類型，通常可用來封裝一小組相關變數，例如矩形的座標，或詳細目錄中某個項目的特性。</span><span class="sxs-lookup"><span data-stu-id="15faf-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="15faf-104">下列範例示範簡單結構宣告：</span><span class="sxs-lookup"><span data-stu-id="15faf-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="15faf-105">備註</span><span class="sxs-lookup"><span data-stu-id="15faf-105">Remarks</span></span>

<span data-ttu-id="15faf-106">結構還包含[建構函式](../../programming-guide/classes-and-structs/constructors.md)、[常數](../../programming-guide/classes-and-structs/constants.md)、[欄位](../../programming-guide/classes-and-structs/fields.md)、[方法](../../programming-guide/classes-and-structs/methods.md)、[屬性](../../programming-guide/classes-and-structs/properties.md)、[索引子](../../programming-guide/indexers/index.md)、[運算子](../operators/index.md)、[事件](../../programming-guide/events/index.md)和[巢狀型別](../../programming-guide/classes-and-structs/nested-types.md)，不過如果需要數個這類成員，您應該考慮以類別來取代類型。</span><span class="sxs-lookup"><span data-stu-id="15faf-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../operators/index.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="15faf-107">如需範例，請參閱[使用結構](../../programming-guide/classes-and-structs/using-structs.md)。</span><span class="sxs-lookup"><span data-stu-id="15faf-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="15faf-108">結構可以實作介面，但無法繼承自其他結構。</span><span class="sxs-lookup"><span data-stu-id="15faf-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="15faf-109">因此，結構成員無法宣告為 `protected`。</span><span class="sxs-lookup"><span data-stu-id="15faf-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="15faf-110">如需詳細資訊，請參閱[結構](../../programming-guide/classes-and-structs/structs.md)。</span><span class="sxs-lookup"><span data-stu-id="15faf-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="15faf-111">範例</span><span class="sxs-lookup"><span data-stu-id="15faf-111">Examples</span></span>

<span data-ttu-id="15faf-112">如需範例和詳細資訊，請參閱[使用結構](../../programming-guide/classes-and-structs/using-structs.md)。</span><span class="sxs-lookup"><span data-stu-id="15faf-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="15faf-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="15faf-113">C# language specification</span></span>

<span data-ttu-id="15faf-114">如需範例，請參閱[使用結構](../../programming-guide/classes-and-structs/using-structs.md)。</span><span class="sxs-lookup"><span data-stu-id="15faf-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15faf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15faf-115">See also</span></span>

- [<span data-ttu-id="15faf-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="15faf-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="15faf-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="15faf-117">C# keywords</span></span>](index.md)
- [<span data-ttu-id="15faf-118">值類型</span><span class="sxs-lookup"><span data-stu-id="15faf-118">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="15faf-119">class</span><span class="sxs-lookup"><span data-stu-id="15faf-119">class</span></span>](class.md)
- [<span data-ttu-id="15faf-120">interface</span><span class="sxs-lookup"><span data-stu-id="15faf-120">interface</span></span>](interface.md)
- [<span data-ttu-id="15faf-121">類別和結構</span><span class="sxs-lookup"><span data-stu-id="15faf-121">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
