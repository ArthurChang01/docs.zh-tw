---
title: unchecked 關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712997"
---
# <a name="unchecked-c-reference"></a>unchecked (C# 參考)

`unchecked` 關鍵字是用來抑制整數類型算術運算和轉換的溢位檢查。

在未檢查的內容中，如果運算式產生不在目的類型範圍內的值，則不會標示溢位。 例如，因為是在 `unchecked` 區塊或運算式中執行下列範例中的計算，所以會忽略整數結果太大的事實，而且 `int1` 會獲指派 -2,147,483,639 值。

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

如果移除 `unchecked` 環境，則會發生編譯錯誤。 因為運算式的所有項目都是常數，所以會在編譯時期偵測到溢位。

預設不會在編譯時期和執行階段檢查包含非常數項目的運算式。 如需啟用已檢查環境的資訊，請參閱 [checked](checked.md)。

因為檢查溢位需要一些時間，所以在沒有溢位危險的情況下使用未檢查的程式碼可能會改善效能。 不過，如果可能會發生溢位，則應該使用已檢查過的環境。

## <a name="example"></a>範例

這個範例示範如何使用 `unchecked` 關鍵字。

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [Checked 與 Unchecked](checked-and-unchecked.md)
- [checked](checked.md)
