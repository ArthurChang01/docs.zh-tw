---
title: 布林值邏輯運算子 - C# 參考
description: 了解能搭配布林值運算元執行邏輯否定、結合 (AND) 及內含和互斥分離 (OR) 作業的 C# 運算子。
ms.date: 09/27/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 327a2a8a95809923446107e6ba1c4b331eee82b7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737889"
---
# <a name="boolean-logical-operators-c-reference"></a>布林值邏輯運算子 (C# 參考)

下列運算子會使用[bool](../keywords/bool.md)運算元執行邏輯作業：

- 一元 [`!` (邏輯否定)](#logical-negation-operator-) 運算子。
- 二元 [`&` (邏輯 AND)](#logical-and-operator-)、[`|` (邏輯 OR)](#logical-or-operator-) 及 [`^` (邏輯互斥 OR)](#logical-exclusive-or-operator-) 運算子。 那些運算子一律會評估兩個運算元。
- 二元 [`&&` (條件邏輯 AND)](#conditional-logical-and-operator-) 及 [`||` (條件邏輯 OR)](#conditional-logical-or-operator-) 運算子。 那些運算子只會在必要時才評估右邊的運算元。

對於[整數數數值型別](../builtin-types/integral-numeric-types.md)的運算元，`&`、`|`和 `^` 運算子會執行位邏輯運算。 如需詳細資訊，請參閱[位元與移位運算子](bitwise-and-shift-operators.md)。

## <a name="logical-negation-operator-"></a>邏輯否定運算子 !

一元前置詞 `!` 運算子會計算其運算元的邏輯否定。 也就是說，它會在運算元評估為 `false` 時產生 `true`，並在運算元評估為 `true` 時產生 `false`：

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

從C# 8.0 開始，一元後置`!`運算子是[null 容許運算子](null-forgiving.md)。

## <a name="logical-and-operator-"></a> 邏輯 AND 運算子 &amp;

`&` 運算子會計算其運算元的邏輯 AND。 若 `x` 及 `y` 皆求出 `true`，那麼 `x & y` 的結果會是 `true`。 否則，結果為 `false`。

即使左側運算元評估為 `false`，`&` 運算子也會評估這兩個運算元，如此一來，不論右邊運算元的值為何，都會 `false` 運算結果。

在下列範例中，`&` 運算子的右邊運算元是方法呼叫；無論左邊運算元的值為何，系統都會執行該呼叫：

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

[條件邏輯 AND 運算子](#conditional-logical-and-operator-) `&&` 也會計算其運算元的邏輯 AND，但如果右邊運算元的值評估為 `false`，系統便不會評估左邊運算元。

對於[整數數數值型別](../builtin-types/integral-numeric-types.md)的運算元，`&` 運算子會計算其運算元的[位邏輯 and](bitwise-and-shift-operators.md#logical-and-operator-) 。 一元的 `&` 運算子是 [address-of 運算子](pointer-related-operators.md#address-of-operator-)。

## <a name="logical-exclusive-or-operator-"></a>邏輯互斥 OR 運算子 ^

`^` 運算子會計算其運算元的邏輯互斥 OR，其也稱為邏輯 XOR。 如果 `x` 評估為 `true` 且 `y` 評估為 `false`，或是 `x` 評估為 `false` 且 `y` 評估為 `true` 時，`x ^ y` 的結果將會為 `true`。 否則，結果為 `false`。 也就是說，針對 `bool` 運算元，`^` 運算子的計算結果會與[不等比較運算子](equality-operators.md#inequality-operator-) `!=` 相同。

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

對於[整數數數值型別](../builtin-types/integral-numeric-types.md)的運算元，`^` 運算子會計算其運算元的[位邏輯互斥 OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) 。

## <a name="logical-or-operator-"></a>邏輯 OR 運算子 |

`|` 運算子會計算其運算元的邏輯 OR。 若 `x` 或 `y` 其中一項的值為 `true`，`x | y` 的結果會是 `true`。 否則，結果為 `false`。

即使左側運算元評估為 `true`，`|` 運算子也會評估這兩個運算元，如此一來，不論右邊運算元的值為何，都會 `true` 運算結果。

在下列範例中，`|` 運算子的右邊運算元是方法呼叫；無論左邊運算元的值為何，系統都會執行該呼叫：

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

[條件式邏輯 OR 運算子](#conditional-logical-or-operator-) `||` 也會計算其運算元的邏輯 OR，但如果左邊運算元的值評估為 `true`，系統便不會評估右邊運算元。

對於[整數數數值型別](../builtin-types/integral-numeric-types.md)的運算元，`|` 運算子會計算其運算元的[位邏輯 or](bitwise-and-shift-operators.md#logical-or-operator-) 。

## <a name="conditional-logical-and-operator-"></a> 條件式邏輯 AND 運算子 &amp;&amp;

條件邏輯 AND 運算子 `&&`，也稱為「捷徑運算」邏輯 AND 運算子，會計算其運算元的邏輯 AND。 若 `x` 及 `y` 皆求出 `true`，那麼 `x && y` 的結果會是 `true`。 否則，結果為 `false`。 如果 `x` 評估為 `false`，則不會評估 `y`。

在下列範例中，`&&` 運算子的右邊運算元是方法呼叫；如果左邊運算元的值評估為 `false`，系統便不會執行該呼叫：

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

[邏輯 AND 運算子](#logical-and-operator-) `&` 也會計算其運算元的邏輯 AND，但一律會求兩個運算元的值。

## <a name="conditional-logical-or-operator-"></a>條件邏輯 OR 運算子 ||

條件邏輯 OR 運算子 `||`，也稱為「捷徑運算」邏輯 OR 運算子，會計算其運算元的邏輯 OR。 若 `x` 或 `y` 其中一項的值為 `true`，`x || y` 的結果會是 `true`。 否則，結果為 `false`。 如果 `x` 評估為 `true`，則不會評估 `y`。

在下列範例中，`||` 運算子的右邊運算元是方法呼叫；如果左邊運算元的值評估為 `true`，系統便不會執行該呼叫：

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

[邏輯 OR 運算子](#logical-or-operator-) `|` 也會計算其運算元的邏輯 OR，但一律會求兩個運算元的值。

## <a name="nullable-boolean-logical-operators"></a>可為 Null 的布林值邏輯運算子

針對 `bool?` 運算元，`&` 和 `|` 運算子支援三值邏輯。 這些運算子的語意是由下列表格定義的：  
  
|x|Y|x&y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|False|False|true|  
|true|null|null|true|  
|False|true|False|true|  
|False|False|False|False|  
|False|null|False|null|  
|null|true|null|true|  
|null|False|False|null|  
|null|null|null|null|  

那些運算子的行為和具有可為 Null 實值類型之一般運算子的行為並不相同。 一般而言，已針對某個實值類型之運算元定義的運算子，也可以搭配相對應可為 Null 實值類型的運算元使用。 如果它的任何運算元評估為 `null`，這類運算子就會產生 `null`。 不過，即使其中一個運算元評估為 `null`，`&` 和 `|` 運算子也可以產生非 null。 如需可為 null 的實數值型別之運算子行為的詳細資訊，請參閱[可為 null 的實數值型別](../builtin-types/nullable-value-types.md)一文的「[提升運算子](../builtin-types/nullable-value-types.md#lifted-operators)」一節。

您也可以使用 `!` 和 `^` 運算子搭配 `bool?` 的運算元，如下列範例所示：

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

條件式邏輯運算子 `&&` 和 `||` 不支援 `bool?` 運算元。

## <a name="compound-assignment"></a>複合指派

若是二元運算子 `op`，表單的複合指派運算式

```csharp
x op= y
```

相當於

```csharp
x = x op y
```

但只會評估 `x` 一次。

`&`、`|` 和 `^` 運算子支援複合指派，如下列範例所示：

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

條件邏輯運算子 `&&` 和 `||` 不支援複合指派。

## <a name="operator-precedence"></a>運算子優先順序

下列清單會依優先順序將邏輯運算子排序 (從最高到最低)：

- 邏輯否定運算子 `!`
- 邏輯 AND 運算子 `&`
- 邏輯互斥 OR 運算子 `^`
- 邏輯 OR 運算子 `|`
- 條件邏輯 AND 運算子 `&&`
- 條件邏輯 OR 運算子 `||`

使用括號 `()` 來變更由運算子優先順序所強制執行的評估順序：

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

如需依優先順序層C#級排序的完整運算子清單，請參閱[ C#運算子](index.md)一文的[運算子優先順序](index.md#operator-precedence)一節。

## <a name="operator-overloadability"></a>運算子是否可多載

使用者定義類型可以[多載](operator-overloading.md) `!`、`&`、`|` 及 `^` 運算子。 當二元運算子多載時，對應的複合指派運算子也會隱含地多載。 使用者定義型別無法明確地多載複合指派運算子。

使用者定義類型無法多載條件邏輯運算子 `&&` 和 `||`。 不過，若使用者定義類型以某種方式多載 [True 和 False 運算子](true-false-operators.md)以及 `&` 或 `|` 運算子，就可以針對該類型的運算元個別評估 `&&` 或 `||` 作業。 如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [邏輯否定運算子](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [邏輯運算子](~/_csharplang/spec/expressions.md#logical-operators)
- [條件邏輯運算子](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [複合指派](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [位元與移位運算子](bitwise-and-shift-operators.md)
