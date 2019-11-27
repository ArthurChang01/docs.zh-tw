---
title: 串連運算子
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: f86245c649647be4e040a61083d8b93eee4d7422
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353681"
---
# <a name="concatenation-operators-in-visual-basic"></a>Visual Basic 中的串連運算子

串連運算子會將多個字串連成單一字串。 串連運算子有兩種：`+` 和 `&`。 兩者都會進行基本的串連作業，如下例所示。

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

這些運算子也可以串連 `String` 變數，如下列所示。

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a>兩種串連運算子之間的差異

[+ 運算子](../../../../visual-basic/language-reference/operators/addition-operator.md)的主要目的是要加入兩個數字。 不過，它也可以串連數值運算元與字串運算元。 `+` 運算子有一組複雜的規則，可判斷是要相加、串連、通知編譯器錯誤，還是擲回執行階段 <xref:System.InvalidCastException> 例外狀況。

[& 運算子](../../../../visual-basic/language-reference/operators/concatenation-operator.md)只會針對 `String` 的運算元定義，而不論 `Option Strict`的設定為何，它一律會將其運算元擴大至 `String`。 建議使用 `&` 運算元進行字串串連，因為它的定義為專門針對字串，且能減少您產生意外轉換的機會。

## <a name="performance-string-and-stringbuilder"></a>效能：String 和 StringBuilder

如果您對字串進行大量的操作，例如串連、刪除和取代，可能可以藉由 <xref:System.Text.StringBuilder> 命名空間中的 <xref:System.Text> 類別而使效能獲得助益。 建立和初始化 <xref:System.Text.StringBuilder> 物件需要額外的指令，將其最終值轉換成 `String` 又再需要一個指令，但您可以彌補這個時間，因為 <xref:System.Text.StringBuilder> 執行地更快速。

## <a name="see-also"></a>請參閱

- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Visual Basic 中的字串操作方法類型](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic 中的邏輯和位運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
