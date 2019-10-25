---
title: If 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 483b58dd9c79c716fdc3d272cf699e33dec9c671
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799008"
---
# <a name="if-operator-visual-basic"></a>If 運算子 (Visual Basic)

使用短路評估來有條件地傳回兩個值的其中一個。 您可以使用三個引數或兩個引數來呼叫 `If` 運算子。

## <a name="syntax"></a>語法

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>如果呼叫了具有三個引數的運算子

使用三個引數呼叫 `If` 時，第一個引數必須評估為可轉換為 `Boolean`的值。 該 `Boolean` 值會決定要評估和傳回的兩個引數中的哪一個。 下列清單只有在使用三個引數呼叫 `If` 運算子時才適用。

### <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`argument1`|必要項。 `Boolean` 決定要評估和傳回的其他引數。|
|`argument2`|必要項。 `Object` 如果 `argument1` 評估為 `True`，則評估並傳回。|
|`argument3`|必要項。 `Object` 如果 `argument1` 評估為 `False`，或如果 `argument1` 是評估為[無](../../../visual-basic/language-reference/nothing.md)的[可為 null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` 變數，則評估並傳回。|

使用三個引數呼叫的 `If` 運算子，其運作方式類似 `IIf` 函數，不同之處在于它會使用最少運算。 `IIf` 函式一律會評估它的全部三個引數，而具有三個引數的 `If` 運算子只會評估其中兩個。 第一個 `If` 引數會進行評估，並將結果轉換為 `Boolean` 值 `True` 或 `False`。 如果 `True`值，則會評估 `argument2`，並傳回其值，但不會評估 `argument3`。 如果 `Boolean` 運算式的值為 `False`，`argument3` 會進行評估，並傳回其值，但不會評估 `argument2`。 下列範例說明使用三個引數時的 `If` 用法：

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

下列範例說明最少運算評估的值。 此範例會顯示兩個嘗試除以變數 `number` 的變數 `divisor` 但 `divisor` 為零時除外。 在此情況下，應該會傳回0，而且不會嘗試執行除法，因為執行階段錯誤會產生。 由於 `If` 運算式使用的是最少運算，因此它會評估第二個或第三個引數，視第一個引數的值而定。 如果第一個引數為 true，則除數不是零，而且可以安全地評估第二個引數並執行除法。 如果第一個引數為 false，則只會評估第三個引數，並傳回0。 因此，當除數為0時，不會嘗試執行除法，也不會產生錯誤結果。 不過，因為 `IIf` 不會使用最少運算，所以即使第一個引數為 false，也會評估第二個引數。 這會導致執行時間零除的錯誤。

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>如果使用兩個引數呼叫運算子

可以省略 `If` 的第一個引數。 這可讓您只使用兩個引數來呼叫運算子。 下列清單只適用于使用兩個引數呼叫 `If` 運算子時。

### <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`argument2`|必要項。 `Object` 必須是參考或可為 null 的類型。 評估並傳回（當它評估為 `Nothing`以外的任何專案時）。|
|`argument3`|必要項。 `Object` 如果 `argument2` 評估為 `Nothing`，則評估並傳回。|

當省略 `Boolean` 引數時，第一個引數必須是參考或可為 null 的類型。 如果第一個引數評估為 `Nothing`，則會傳回第二個引數的值。 在所有其他情況下，會傳回第一個引數的值。 下列範例說明此評估的運作方式：

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [可為 Null 的值類型](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)
