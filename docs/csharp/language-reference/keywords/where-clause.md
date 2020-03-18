---
title: where 子句 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 33616e4eacb484b9c6eda3862cd86fdd1e6df165
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173480"
---
# <a name="where-clause-c-reference"></a>where 子句 (C# 參考)

`where` 子句用於查詢運算式中，以指定將在查詢運算式中傳回資料來源中的項目。 它會將布林值條件 (*predicate*) 套用到每個來源項目 (透過範圍變數所參考)，並傳回所指定條件為 true 的項目。 單一查詢運算式可能會包含多個 `where` 子句，而單一子句可能會包含多個述詞子運算式。

## <a name="example"></a>範例

在下列範例中，`where` 子句會篩選掉不小於五的所有數字。 如果您移除 `where` 子句，則會傳回資料來源中的所有數字。 `num < 5` 運算式是套用至每個項目的述詞。

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>範例

在單個`where`子句中，可以使用[&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-)和[&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)運算子根據需要指定盡可能多的謂詞。 在下列範例中，查詢會指定兩個述詞，只選取小於五的偶數。

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>範例

`where` 子句可能包含一個或多個傳回布林值的方法。 在下列範例中，`where` 子句使用方法來判斷範圍變數的目前值是偶數還是奇數。

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>備註

`where` 子句是篩選機制。 它幾乎可以放在查詢運算式中的任何位置，但不能是第一個或最後一個子句。 `where` 子句可能出現在 [group](group-clause.md) 子句之前或之後，取決於必須在分組來源項目之前還是之後進行篩選。

如果指定的述詞不適用於資料來源中的項目，則會產生編譯時期錯誤。 這是 LINQ 提供的強型別檢查的一個優點。

在編譯時間，`where` 關鍵字會轉換為 <xref:System.Linq.Enumerable.Where%2A> 標準查詢運算子方法呼叫。

## <a name="see-also"></a>另請參閱

- [查詢關鍵字 （LINQ）](query-keywords.md)
- [從 條款](from-clause.md)
- [選擇子句](select-clause.md)
- [篩選資料](../../programming-guide/concepts/linq/filtering-data.md)
- [C# 中的 LINQ](../../linq/index.md)
- [語言綜合查詢（LINQ）](../../programming-guide/concepts/linq/index.md)
