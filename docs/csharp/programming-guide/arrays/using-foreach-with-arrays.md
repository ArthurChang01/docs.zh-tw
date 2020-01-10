---
title: 搭配陣列使用 foreach - C# 程式設計手冊
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705674"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>搭配陣列使用 foreach (C# 程式設計手冊)

[foreach](../../language-reference/keywords/foreach-in.md) 陳述式提供了一個簡單且清楚的方法來逐一查看陣列中的元素。

針對一維陣列，`foreach` 陳述式會以遞增索引順序處理元素，從索引 0 開始並於索引 `Length - 1` 結束：

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

針對多維陣列，元素的周遊方式是先遞增最右側維度的索引，然後下一個左側的維度，以此類推向繼續左：

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

但是在使用多維陣列時，使用巢狀 [for](../../language-reference/keywords/for.md) 迴圈能夠讓您進一步控制處理陣列元素的順序。

## <a name="see-also"></a>請參閱

- <xref:System.Array>
- [C# 程式設計指南](../index.md)
- [陣列](index.md)
- [一維陣列](single-dimensional-arrays.md)
- [多維陣列](multidimensional-arrays.md)
- [不規則陣列](jagged-arrays.md)
