---
title: 查詢物件集合 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 查詢集合。
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659804"
---
# <a name="query-a-collection-of-objects"></a>查詢物件的集合

這個範例示範如何對 `Student` 物件清單執行簡單查詢。 每個 `Student` 物件都包含學生的一些基本資訊，以及一份代表學生四次考試分數的清單。  
  
這個應用程式作為本節中使用相同 `students` 資料來源的許多其他範例的架構。  
  
## <a name="example"></a>範例

下列查詢會傳回第一次考試分數等於或高於 90 的學生。  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
此查詢是刻意簡單，好讓您進行體驗。 例如，您可以在 `where` 子句中嘗試多個條件，或使用 `orderby` 子句來排序結果。  
  
## <a name="see-also"></a>另請參閱

- [語言綜合查詢（LINQ）](index.md)
- [字串插補](../language-reference/tokens/interpolated.md)
