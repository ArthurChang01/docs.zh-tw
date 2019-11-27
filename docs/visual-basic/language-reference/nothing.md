---
title: Nothing 關鍵字
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 3bd4681341a33cc8db4ecbc2b284be243db56549
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344170"
---
# <a name="nothing-keyword-visual-basic"></a><span data-ttu-id="84aa0-102">無關鍵詞（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="84aa0-102">Nothing keyword (Visual Basic)</span></span>

<span data-ttu-id="84aa0-103">表示任何資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="84aa0-103">Represents the default value of any data type.</span></span> <span data-ttu-id="84aa0-104">若是參考型別，預設值為 `null` 參考。</span><span class="sxs-lookup"><span data-stu-id="84aa0-104">For reference types, the default value is the `null` reference.</span></span> <span data-ttu-id="84aa0-105">對於實數值型別，預設值取決於實數值型別是否可為 null。</span><span class="sxs-lookup"><span data-stu-id="84aa0-105">For value types, the default value depends on whether the value type is nullable.</span></span>

> [!NOTE]
> <span data-ttu-id="84aa0-106">針對不可為 null 的實數值型別，Visual Basic 中的 `Nothing` 與C#中的 `null` 不同。</span><span class="sxs-lookup"><span data-stu-id="84aa0-106">For non-nullable value types, `Nothing` in Visual Basic differs from `null` in C#.</span></span> <span data-ttu-id="84aa0-107">在 Visual Basic 中，如果您將不可為 null 的實數值型別變數設定為 `Nothing`，則變數會設定為其宣告類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="84aa0-107">In Visual Basic, if you set a variable of a non-nullable value type to `Nothing`, the variable is set to the default value for its declared type.</span></span> <span data-ttu-id="84aa0-108">在C#中，如果您將不可為 null 的實數值型別的變數指派給 `null`，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="84aa0-108">In C#, if you assign a variable of a non-nullable value type to `null`, a compile-time error occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="84aa0-109">備註</span><span class="sxs-lookup"><span data-stu-id="84aa0-109">Remarks</span></span>

<span data-ttu-id="84aa0-110">`Nothing` 代表資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="84aa0-110">`Nothing` represents the default value of a data type.</span></span> <span data-ttu-id="84aa0-111">預設值取決於變數是實數值型別或參考型別。</span><span class="sxs-lookup"><span data-stu-id="84aa0-111">The default value depends on whether the variable is of a value type or of a reference type.</span></span>

<span data-ttu-id="84aa0-112">實*值型*別的變數直接包含它的值。</span><span class="sxs-lookup"><span data-stu-id="84aa0-112">A variable of a *value type* directly contains its value.</span></span> <span data-ttu-id="84aa0-113">實值型別包括所有數值資料類型、`Boolean`、`Char`、`Date`、所有結構和所有列舉。</span><span class="sxs-lookup"><span data-stu-id="84aa0-113">Value types include all numeric data types, `Boolean`, `Char`, `Date`, all structures, and all enumerations.</span></span> <span data-ttu-id="84aa0-114">*參考型別*的變數會將物件實例的參考儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="84aa0-114">A variable of a *reference type* stores a reference to an instance of the object in memory.</span></span> <span data-ttu-id="84aa0-115">參考型別包括類別、陣列、委派和字串。</span><span class="sxs-lookup"><span data-stu-id="84aa0-115">Reference types include classes, arrays, delegates, and strings.</span></span> <span data-ttu-id="84aa0-116">如需詳細資訊，請參閱 [Value Types and Reference Types](../programming-guide/language-features/data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="84aa0-116">For more information, see [Value Types and Reference Types](../programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>

<span data-ttu-id="84aa0-117">如果變數是實值型別，則 `Nothing` 的行為取決於變數是否為可為 null 的資料型別。</span><span class="sxs-lookup"><span data-stu-id="84aa0-117">If a variable is of a value type, the behavior of `Nothing` depends on whether the variable is of a nullable data type.</span></span> <span data-ttu-id="84aa0-118">若要表示可為 null 的實值型別，請將 `?` 修飾詞加入至型別名稱。</span><span class="sxs-lookup"><span data-stu-id="84aa0-118">To represent a nullable value type, add a `?` modifier to the type name.</span></span> <span data-ttu-id="84aa0-119">將 `Nothing` 指派給可為 null 的變數會將值設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="84aa0-119">Assigning `Nothing` to a nullable variable sets the value to `null`.</span></span> <span data-ttu-id="84aa0-120">如需詳細資訊和範例，請參閱[可為 null 的實數值型別](../programming-guide/language-features/data-types/nullable-value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="84aa0-120">For more information and examples, see [Nullable Value Types](../programming-guide/language-features/data-types/nullable-value-types.md).</span></span>

<span data-ttu-id="84aa0-121">如果變數是不可為 null 的實數值型別，請將 `Nothing` 指派給它，將其設定為其宣告類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="84aa0-121">If a variable is of a value type that is not nullable, assigning `Nothing` to it sets it to the default value for its declared type.</span></span> <span data-ttu-id="84aa0-122">如果該類型包含變數成員，則會將它們全部設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="84aa0-122">If that type contains variable members, they are all set to their default values.</span></span> <span data-ttu-id="84aa0-123">下列範例會針對純量類型說明這種情況。</span><span class="sxs-lookup"><span data-stu-id="84aa0-123">The following example illustrates this for scalar types.</span></span>

[!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]

<span data-ttu-id="84aa0-124">如果變數是參考型別，將 `Nothing` 指派給變數，就會將它設定為變數類型的 `null` 參考。</span><span class="sxs-lookup"><span data-stu-id="84aa0-124">If a variable is of a reference type, assigning `Nothing` to the variable sets it to a `null` reference of the variable's type.</span></span> <span data-ttu-id="84aa0-125">設定為 `null` 參考的變數未與任何物件相關聯。</span><span class="sxs-lookup"><span data-stu-id="84aa0-125">A variable that is set to a `null` reference is not associated with any object.</span></span> <span data-ttu-id="84aa0-126">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="84aa0-126">The following example demonstrates this:</span></span>

[!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]

<span data-ttu-id="84aa0-127">檢查是否 `null`參考（或可為 null 的實數值型別）變數時，請勿使用 `= Nothing` 或 `<> Nothing`。</span><span class="sxs-lookup"><span data-stu-id="84aa0-127">When checking whether a reference (or nullable value type) variable is `null`, do not use `= Nothing` or `<> Nothing`.</span></span> <span data-ttu-id="84aa0-128">一律使用 `Is Nothing` 或 `IsNot Nothing`。</span><span class="sxs-lookup"><span data-stu-id="84aa0-128">Always use `Is Nothing` or `IsNot Nothing`.</span></span>

<span data-ttu-id="84aa0-129">對於 Visual Basic 中的字串，空字串等於 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="84aa0-129">For strings in Visual Basic, the empty string equals `Nothing`.</span></span> <span data-ttu-id="84aa0-130">因此，`"" = Nothing` 為 true。</span><span class="sxs-lookup"><span data-stu-id="84aa0-130">Therefore, `"" = Nothing` is true.</span></span>

<span data-ttu-id="84aa0-131">下列範例會顯示使用 `Is` 和 `IsNot` 運算子的比較：</span><span class="sxs-lookup"><span data-stu-id="84aa0-131">The following example shows comparisons that use the `Is` and `IsNot` operators:</span></span>

[!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]

<span data-ttu-id="84aa0-132">如果您在未使用 `As` 子句的情況下宣告變數，並將它設定為 `Nothing`，則變數的類型會是 `Object`。</span><span class="sxs-lookup"><span data-stu-id="84aa0-132">If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`.</span></span> <span data-ttu-id="84aa0-133">`Dim something = Nothing`的範例。</span><span class="sxs-lookup"><span data-stu-id="84aa0-133">An example of this is `Dim something = Nothing`.</span></span> <span data-ttu-id="84aa0-134">當 `Option Strict` 為 on，且 `Option Infer` 為 off 時，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="84aa0-134">A compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is off.</span></span>

<span data-ttu-id="84aa0-135">當您將 `Nothing` 指派給物件變數時，它就不會再參考任何物件實例。</span><span class="sxs-lookup"><span data-stu-id="84aa0-135">When you assign `Nothing` to an object variable, it no longer refers to any object instance.</span></span> <span data-ttu-id="84aa0-136">如果變數先前已參考實例，將其設定為 `Nothing` 不會終止實例本身。</span><span class="sxs-lookup"><span data-stu-id="84aa0-136">If the variable had previously referred to an instance, setting it to `Nothing` does not terminate the instance itself.</span></span> <span data-ttu-id="84aa0-137">實例會終止，而且只有在垃圾收集行程（GC）偵測到沒有任何使用中的參考之後，才會釋放與它相關聯的記憶體和系統資源。</span><span class="sxs-lookup"><span data-stu-id="84aa0-137">The instance is terminated, and the memory and system resources associated with it are released, only after the garbage collector (GC) detects that there are no active references remaining.</span></span>

<span data-ttu-id="84aa0-138">`Nothing` 不同于 <xref:System.DBNull> 物件，代表未初始化的 variant 或不存在的資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="84aa0-138">`Nothing` differs from the <xref:System.DBNull> object, which represents an uninitialized variant or a nonexistent database column.</span></span>

## <a name="see-also"></a><span data-ttu-id="84aa0-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="84aa0-139">See also</span></span>

- [<span data-ttu-id="84aa0-140">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="84aa0-140">Dim Statement</span></span>](./statements/dim-statement.md)
- [<span data-ttu-id="84aa0-141">物件存留期：物件的建立和終結</span><span class="sxs-lookup"><span data-stu-id="84aa0-141">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="84aa0-142">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="84aa0-142">Lifetime in Visual Basic</span></span>](../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="84aa0-143">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="84aa0-143">Is Operator</span></span>](./operators/is-operator.md)
- [<span data-ttu-id="84aa0-144">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="84aa0-144">IsNot Operator</span></span>](./operators/isnot-operator.md)
- [<span data-ttu-id="84aa0-145">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="84aa0-145">Nullable Value Types</span></span>](../programming-guide/language-features/data-types/nullable-value-types.md)
