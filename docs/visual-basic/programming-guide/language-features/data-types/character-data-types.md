---
title: 字元資料類型
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: edd1d3a41dd878649aa422256b7858d7bce366e1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346387"
---
# <a name="character-data-types-visual-basic"></a>字元資料類型 (Visual Basic)
Visual Basic 提供*字元資料類型*，以處理可列印和可顯示的字元。 雖然兩者都處理 Unicode 字元，但 `Char` 保留單一字元，而 `String` 包含不限數目的字元。  
  
 如需顯示 Visual Basic 資料類型並存比較的資料表，請參閱[資料類型](../../../../visual-basic/language-reference/data-types/index.md)。  
  
## <a name="char-type"></a>Char 類型  
 `Char` 資料類型是單一的雙位元組（16位） Unicode 字元。 如果變數一律只儲存一個字元，請將它宣告為 `Char`。 例如：  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 `Char` 或 `String` 變數中的每個可能值都是 Unicode 字元集中的程式*代碼點*或字元碼。 Unicode 字元包括基本 ASCII 字元集、其他各種字母字母、重音、貨幣符號、分數、變音符號和數學和技術符號。  
  
> [!NOTE]
> Unicode 字元集會針對*代理配對*保留 D800 到 DFFF （55296到 55551 decimal）的程式碼點，其需要 2 16 位值來表示單一程式碼點。 `Char` 變數不能保存代理配對，而 `String` 使用兩個位置來保存這種配對。  
  
 如需詳細資訊，請參閱[Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)。  
  
## <a name="string-type"></a>字串類型  
 `String` 資料類型是零個或多個兩個位元組（16位） Unicode 字元的序列。 如果變數可以包含不限數量的字元，請將它宣告為 `String`。 例如：  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 如需詳細資訊，請參閱[String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)。  
  
## <a name="see-also"></a>另請參閱

- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
