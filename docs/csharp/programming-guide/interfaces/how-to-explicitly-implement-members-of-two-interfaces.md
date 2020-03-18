---
title: 如何顯式實現兩個介面的成員 - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c7adc08f62a7f8a14b8e10f8b5ecdd6e37db811d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75701234"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="3b6d0-102">如何顯式實現兩個介面的成員（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="3b6d0-102">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="3b6d0-103">明確的[介面](../../language-reference/keywords/interface.md)實作也可讓程式設計人員實作具有相同成員名稱的兩個介面，並提供每個介面成員不同的實作。</span><span class="sxs-lookup"><span data-stu-id="3b6d0-103">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="3b6d0-104">此範例會顯示方塊尺寸的計量和英制單位。</span><span class="sxs-lookup"><span data-stu-id="3b6d0-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="3b6d0-105">Box [類別](../../language-reference/keywords/class.md)實作 IEnglishDimensions 和 IMetricDimensions 兩個介面，代表不同的量值系統。</span><span class="sxs-lookup"><span data-stu-id="3b6d0-105">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="3b6d0-106">這兩個介面具有相同的成員名稱，Length 和 Width。</span><span class="sxs-lookup"><span data-stu-id="3b6d0-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b6d0-107">範例</span><span class="sxs-lookup"><span data-stu-id="3b6d0-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3b6d0-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="3b6d0-108">Robust Programming</span></span>  
 <span data-ttu-id="3b6d0-109">如果您想要以英制單位建立預設的量值單位，請按一般方式實作 Length 和 Width 方法，並從 IMetricDimensions 介面明確實作 Length 和 Width 方法：</span><span class="sxs-lookup"><span data-stu-id="3b6d0-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="3b6d0-110">在本例中，您可以從類別執行個體存取英制單位，從介面執行個體存取計量單位：</span><span class="sxs-lookup"><span data-stu-id="3b6d0-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="3b6d0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b6d0-111">See also</span></span>

- [<span data-ttu-id="3b6d0-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3b6d0-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3b6d0-113">類別和結構</span><span class="sxs-lookup"><span data-stu-id="3b6d0-113">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="3b6d0-114">介面</span><span class="sxs-lookup"><span data-stu-id="3b6d0-114">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="3b6d0-115">如何明確實作介面成員</span><span class="sxs-lookup"><span data-stu-id="3b6d0-115">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
