---
title: 如何：在程式碼中中斷和合併陳述式
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: f1a24c001cd20acc7663fb4cbe60e7e35a9c8fc3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347430"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>如何：在程式碼中中斷和合併陳述式 (Visual Basic)

撰寫程式碼時，您有時可能會在程式碼編輯器中建立需要水準滾動的冗長語句。 雖然這並不會影響您的程式碼執行方式，但它會讓您或其他人難以在監視器上看到該程式碼。 在這種情況下，您應該考慮將單一長語句細分成數行。

## <a name="to-break-a-single-statement-into-multiple-lines"></a>將單一語句分成多行

使用行接續字元，也就是底線（`_`），這是您想要行中斷的位置。 底線的前面必須加上空格，並緊接在行結束字元（回車）或（從16.0 版開始）後面加上一個加上回車的批註。

  > [!NOTE]
  > 在某些情況下，如果您省略行接續字元，Visual Basic 編譯器會隱含地繼續下一行程式碼上的語句。 如需可省略行接續字元的語法元素清單，請參閱[語句](../../../visual-basic/programming-guide/language-features/statements.md)中的「隱含行接續」。

  在下列範例中，語句會分成四行，其中行接續字元會終止所有但最後一行。

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  使用此順序可讓您的程式碼在線上和列印時更容易閱讀。

  行接續字元必須是該行的最後一個字元。 您不能在同一行上以其他任何專案來追蹤。

  有一些限制可供您使用行接續字元;例如，您無法將它用在引數名稱的中間。 您可以使用行接續字元來中斷引數清單，但引數的個別名稱必須維持不變。

  您無法使用行接續字元來繼續留言。 編譯器不會檢查批註中的字元是否有特殊意義。 對於多行批註，請在每一行重複批註符號（`'`）。

 雖然建議的方法是將每個語句放在不同的行上，但 Visual Basic 也可以讓您將多個語句放在同一行。

## <a name="to-place-multiple-statements-on-the-same-line"></a>若要將多個語句放在同一行

以冒號（`:`）分隔語句，如下列範例所示：

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a>請參閱

- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
