---
title: 將陣列當做物件 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715096"
---
# <a name="arrays-as-objects-c-programming-guide"></a>將陣列當做物件 (C# 程式設計手冊)

在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。 <xref:System.Array> 是所有陣列類型的抽象基底類型。 您可以使用<xref:System.Array>具有的屬性和其他類成員。 例如，使用 屬性<xref:System.Array.Length%2A>獲取陣列的長度。 下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。

## <a name="example"></a>範例

這個範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [陣 列](./index.md)
- [一維陣列](./single-dimensional-arrays.md)
- [多維陣列](./multidimensional-arrays.md)
- [鋸齒狀陣列](./jagged-arrays.md)
