---
title: C# 陳述式 - C# 語言教學課程
description: 您將使用陳述式來建立 C# 程式的動作
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159100"
---
# <a name="statements"></a>陳述式

程式的動作是藉由*陳述式*來表達。 C# 支援數種不同類型的陳述式，其中一些是以內嵌陳述式來定義。

「區塊」** 可允許在許可單一陳述式的內容中撰寫多個陳述式。 區塊是由在 `{` 與 `}` 分隔符號之間撰寫的陳述式清單所組成。

「宣告陳述式」** 可用來宣告區域變數和常數。

「運算式陳述式」** 可用來評估運算式。 可用來作為陳述式的運算式包括方法叫用、使用 `new` 運算子的物件配置、使用 `=` 和複合指派運算子的指派、使用 `++` 和 `--` 運算子的遞增和遞減運算，以及 `await` 運算。

「選取範圍陳述式」** 可用來選取一些可能陳述式的其中之一，以根據某個運算式的值來執行。 此組包含 和`if``switch`語句。

「反覆運算陳述式」** 可用來重複執行內嵌的陳述式。 此組包含`while`、`do`和`for``foreach`語句。

「跳躍陳述式」** 可用來轉移控制項。 此組包含`break`、、、、、`return``yield``continue``goto``throw`和 語句。

`try`...`catch` 陳述式可用來攔截在執行區塊時發生的例外狀況，而 `try`...`finally` 陳述式則可用來指定不論是否發生例外狀況都一律會執行的最終處理程式碼。

`checked` 和 `unchecked` 陳述式可用來控制整數型別算術運算和轉換的溢位檢查內容。

`lock` 陳述式可用來取得所指定物件的互斥鎖定、執行陳述式，然後釋放鎖定。

`using` 陳述式可用來取得資源、執行陳述式，然後處置該資源。

以下列出可供使用的陳述式類型，並提供每個陳述式的範例。

* 區域變數宣告：

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* 區域常數宣告：

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* 運算式陳述式：

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* `if` 陳述式：

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* `switch` 陳述式：

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* `while` 陳述式：

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* `do` 陳述式：

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* `for` 陳述式：

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* `foreach` 陳述式：

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* `break` 陳述式：

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* `continue` 陳述式：

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* `goto` 陳述式：

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* `return` 陳述式：

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* `yield` 陳述式：

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* `throw` 陳述式和 `try` 陳述式：

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* `checked` 和 `unchecked` 陳述式：

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* `lock` 陳述式：

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* `using` 陳述式：

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[上一個](expressions.md)
>[下一個](classes-and-objects.md)
