---
title: 多維陣列 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: ee5fae36ff844fadad7e1b6a766020319b67a83c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021753"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>多維陣列 (C# 程式設計手冊)

陣列可以有多個維度。 例如，下列宣告會建立具有四個資料列和兩個資料行的二維陣列。  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 下列宣告會建立三維 (4、2 和 3) 陣列。  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>陣列初始化

 您可以在宣告後初始化陣列，如下列範例所示。  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 還可以初始化陣列,而無需指定排名。  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 如果選擇在不進行初始化的情況下宣告變數，則必須使用 `new` 運算子將陣列指派給變數。 下列範例會顯示 `new` 的用法。  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 下列範例會將值指派給特定的陣列元素。  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 同樣地，下列範例會取得特定陣列元素的值，並將它指派給 `elementValue` 變數。  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 下列程式碼範例會將陣列元素初始化為預設值 (除了不規則陣列外)。  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>另請參閱

- [C# 編程指南](../index.md)
- [陣列](./index.md)
- [一維陣列](./single-dimensional-arrays.md)
- [不規則陣列](./jagged-arrays.md)
