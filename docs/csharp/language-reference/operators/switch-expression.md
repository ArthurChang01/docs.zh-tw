---
title: 開關運算式 - C# 引用
description: 瞭解如何使用 C# 開關運算式進行模式匹配和其他資料內省
ms.date: 03/19/2020
ms.openlocfilehash: 9e609bcea0f92f492b5f9b07840e47f75c1b71e4
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249785"
---
# <a name="switch-expression-c-reference"></a><span data-ttu-id="ac8a6-103">開關運算式（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="ac8a6-103">switch expression (C# reference)</span></span>

<span data-ttu-id="ac8a6-104">本文介紹 C# 8.0 仲介紹的`switch`運算式。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-104">This article covers the `switch` expression, introduced in C# 8.0.</span></span> <span data-ttu-id="ac8a6-105">有關該`switch`語句的資訊，請參閱語句部分中[`switch`有關該語句](../keywords/switch.md)的文章。 [statements](../keywords/index.md)</span><span class="sxs-lookup"><span data-stu-id="ac8a6-105">For information on the `switch` statement, see the article on the [`switch` statement](../keywords/switch.md) in the [statements](../keywords/index.md) section.</span></span>

## <a name="basic-example"></a><span data-ttu-id="ac8a6-106">基本範例</span><span class="sxs-lookup"><span data-stu-id="ac8a6-106">Basic example</span></span>

<span data-ttu-id="ac8a6-107">該`switch`運算式在運算式`switch`上下文中提供類似語義。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-107">The `switch` expression provides for `switch`-like semantics in an expression context.</span></span> <span data-ttu-id="ac8a6-108">當開關臂產生值時，它提供了簡潔的語法。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-108">It provides a concise syntax when the switch arms produce a value.</span></span> <span data-ttu-id="ac8a6-109">下面的示例顯示了開關運算式的結構。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-109">The following example shows the structure of a switch expression.</span></span> <span data-ttu-id="ac8a6-110">它將線上地圖中`enum`表示視覺方向的值轉換為相應的基本方向：</span><span class="sxs-lookup"><span data-stu-id="ac8a6-110">It translates values from an `enum` representing visual directions in an online map to the corresponding cardinal direction:</span></span>

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

<span data-ttu-id="ac8a6-111">前面的示例顯示了交換器運算式的基本元素：</span><span class="sxs-lookup"><span data-stu-id="ac8a6-111">The preceding sample shows the basic elements of a switch expression:</span></span>

- <span data-ttu-id="ac8a6-112">*範圍運算式*： 前面的示例使用變數`direction`作為範圍運算式。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-112">The *range expression*: The preceding example uses the variable `direction` as the range expression.</span></span>
- <span data-ttu-id="ac8a6-113">*開關運算式臂*：每個開關運算式臂包含*一個模式*、一個可選*的大小寫保護、*`=>`權杖*和運算式*。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-113">The *switch expression arms*: Each switch expression arm contains a *pattern*, an optional *case guard*, the `=>` token, and an *expression*.</span></span>

<span data-ttu-id="ac8a6-114">*開關運算式*的結果是第一個*開關運算式臂*的運算式的值，其*模式*與*範圍運算式*匹配，其*原因保護*（如果存在）計算為`true`。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-114">The result of the *switch expression* is the value of the expression of the first *switch expression arm* whose *pattern* matches the *range expression* and whose *cause guard*, if present, evaluates to `true`.</span></span> <span data-ttu-id="ac8a6-115">權杖右側的運算式不能是運算式語句。 *expression* `=>`</span><span class="sxs-lookup"><span data-stu-id="ac8a6-115">The *expression* on the right of the `=>` token can't be an expression statement.</span></span>

<span data-ttu-id="ac8a6-116">按文本順序計算*開關運算式臂*。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-116">The *switch expression arms* are evaluated in text order.</span></span> <span data-ttu-id="ac8a6-117">當無法選擇較低的*開關運算式臂*時，編譯器會發出錯誤，因為較高的*開關運算式臂*與其所有值匹配。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-117">The compiler issues an error when a lower *switch expression arm* can't be chosen because a higher *switch expression arm* matches all its values.</span></span>

## <a name="patterns-and-case-guards"></a><span data-ttu-id="ac8a6-118">圖案和外殼防護裝置</span><span class="sxs-lookup"><span data-stu-id="ac8a6-118">Patterns and case guards</span></span>

<span data-ttu-id="ac8a6-119">交換器運算式臂中支援許多模式。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-119">Many patterns are supported in switch expression arms.</span></span> <span data-ttu-id="ac8a6-120">前面的示例使用了*值模式*。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-120">The preceding example used a *value pattern*.</span></span> <span data-ttu-id="ac8a6-121">*值模式*將範圍運算式與值進行比較。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-121">A *value pattern* compares the range expression to a value.</span></span> <span data-ttu-id="ac8a6-122">該值必須是編譯時間常量。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-122">That value must be a compile time constant.</span></span> <span data-ttu-id="ac8a6-123">*類型模式*將範圍運算式與已知類型進行比較。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-123">The *type pattern* compares the range expression to a known type.</span></span> <span data-ttu-id="ac8a6-124">以下示例從序列中檢索第三個元素。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-124">The following example retrieves the third element from a sequence.</span></span> <span data-ttu-id="ac8a6-125">它根據序列的類型使用不同的方法：</span><span class="sxs-lookup"><span data-stu-id="ac8a6-125">It uses different methods based on the type of the sequence:</span></span>

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

<span data-ttu-id="ac8a6-126">模式可以是遞迴的，其中模式測試類型，如果該類型匹配，則模式與範圍運算式上的一個或多個屬性值匹配。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-126">Patterns can be recursive, where a pattern tests a type, and if that type matches, the pattern matches one or more property values on the range expression.</span></span> <span data-ttu-id="ac8a6-127">可以使用遞迴模式擴展前面的示例。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-127">You can use recursive patterns to extend the preceding example.</span></span> <span data-ttu-id="ac8a6-128">為元素少於 3 的陣列添加開關運算式臂。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-128">You add switch expression arms for arrays that have fewer than 3 elements.</span></span> <span data-ttu-id="ac8a6-129">遞迴模式顯示在以下示例中：</span><span class="sxs-lookup"><span data-stu-id="ac8a6-129">Recursive patterns are shown in the following example:</span></span>

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

<span data-ttu-id="ac8a6-130">遞迴模式可以檢查範圍運算式的屬性，但不能執行任意代碼。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-130">Recursive patterns can examine properties of the range expression, but can't execute arbitrary code.</span></span> <span data-ttu-id="ac8a6-131">可以使用`when`子句中指定的*大小寫保護*為其他序列類型提供類似的檢查：</span><span class="sxs-lookup"><span data-stu-id="ac8a6-131">You can use a *case guard*, specified in a `when` clause, to provide similar checks for other sequence types:</span></span>

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

<span data-ttu-id="ac8a6-132">最後，您可以添加`_`模式和`null`模式來捕獲任何其他交換器運算式臂未處理的參數。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-132">Finally, you can add the `_` pattern and the `null` pattern to catch arguments that aren't processed by any other switch expression arm.</span></span> <span data-ttu-id="ac8a6-133">這使得 switch 運算式*詳盡無遺*，這意味著可以處理範圍運算式的任何可能值。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-133">That makes the switch expression *exhaustive*, meaning any possible value of the range expression is handled.</span></span> <span data-ttu-id="ac8a6-134">下面的示例添加這些運算式臂：</span><span class="sxs-lookup"><span data-stu-id="ac8a6-134">The following example adds those expression arms:</span></span>

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

<span data-ttu-id="ac8a6-135">前面的示例添加一個`null`模式，並將`IEnumerable<T>`類型模式更改為`_`模式。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-135">The preceding example adds a `null` pattern, and changes the `IEnumerable<T>` type pattern to a `_` pattern.</span></span> <span data-ttu-id="ac8a6-136">該`null`模式提供作為開關運算式臂的空檢查。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-136">The `null` pattern provides a null check as a switch expression arm.</span></span> <span data-ttu-id="ac8a6-137">該臂的運算式引發一個<xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-137">The expression for that arm throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="ac8a6-138">該`_`模式與以前臂未匹配的所有輸入匹配。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-138">The `_` pattern matches all inputs that haven't been matched by previous arms.</span></span> <span data-ttu-id="ac8a6-139">它必須在`null`檢查後出現，否則與輸入匹配`null`。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-139">It must come after the `null` check, or it would match `null` inputs.</span></span>

<span data-ttu-id="ac8a6-140">你可以閱讀更多在C#語言規格建議遞[歸模式](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)。</span><span class="sxs-lookup"><span data-stu-id="ac8a6-140">You can read more in the C# language spec proposal for [recursive patterns](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac8a6-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac8a6-141">See also</span></span>

- [<span data-ttu-id="ac8a6-142">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ac8a6-142">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ac8a6-143">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="ac8a6-143">C# operators</span></span>](index.md)
- [<span data-ttu-id="ac8a6-144">模式比對</span><span class="sxs-lookup"><span data-stu-id="ac8a6-144">Pattern matching</span></span>](../../pattern-matching.md)