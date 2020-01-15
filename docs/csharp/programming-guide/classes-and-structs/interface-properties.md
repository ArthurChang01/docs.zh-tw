---
title: 介面屬性 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: ff892a35f4be6600c00bc0c72c2f789ef6eb4408
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705531"
---
# <a name="interface-properties-c-programming-guide"></a>介面屬性 (C# 程式設計手冊)

屬性可以宣告於 [interface](../../language-reference/keywords/interface.md) 上。 介面屬性存取子的範例如下：

[!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]

介面屬性的存取子沒有主體。 因此，存取子的目的是指出屬性是讀寫、唯讀還是唯寫。

## <a name="example"></a>範例

在此範例中，`IEmployee` 介面具有讀寫屬性 `Name` 和唯讀屬性 `Counter`。 `Employee` 類別會實作 `IEmployee` 介面，並使用這兩個屬性。 程式會讀取新員工的姓名和目前員工人數，並顯示員工姓名和計算的員工人數。

您可以使用屬性的完整名稱，而屬性參考在其中宣告成員的介面。 例如：

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

這稱為[明確介面實作](../interfaces/explicit-interface-implementation.md)。 例如，如果 `Employee` 類別實作 `ICitizen` 和 `IEmployee` 這兩個介面，而且這兩個介面都具有 `Name` 屬性，則需要明確介面成員實作。 也就是說，下列屬性宣告：

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

在 `IEmployee` 介面上實作 `Name` 屬性，而下列宣告：

[!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]

在 `ICitizen` 介面上實作 `Name` 屬性。

[!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a>範例輸出

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [屬性](./properties.md)
- [使用屬性](./using-properties.md)
- [屬性與索引子之間的比較](../indexers/comparison-between-properties-and-indexers.md)
- [索引子](../indexers/index.md)
- [介面](../interfaces/index.md)
