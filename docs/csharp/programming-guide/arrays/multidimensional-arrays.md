---
title: 多維陣列 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: eb49f4386b6106328f1613b5ec70794ac26fc9b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715043"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="1e2df-102">多維陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1e2df-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="1e2df-103">陣列可以有多個維度。</span><span class="sxs-lookup"><span data-stu-id="1e2df-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="1e2df-104">例如，下列宣告會建立具有四列和兩行的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="1e2df-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="1e2df-105">下列宣告會建立三維 (4、2 和 3) 陣列。</span><span class="sxs-lookup"><span data-stu-id="1e2df-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="1e2df-106">陣列初始化</span><span class="sxs-lookup"><span data-stu-id="1e2df-106">Array Initialization</span></span>

 <span data-ttu-id="1e2df-107">您可以在宣告後初始化陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1e2df-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="1e2df-108">也可以初始化陣列，而不指定順位。</span><span class="sxs-lookup"><span data-stu-id="1e2df-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="1e2df-109">如果選擇在不進行初始化的情況下宣告變數，則必須使用 `new` 運算子將陣列指派給變數。</span><span class="sxs-lookup"><span data-stu-id="1e2df-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="1e2df-110">下列範例會顯示 `new` 的用法。</span><span class="sxs-lookup"><span data-stu-id="1e2df-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="1e2df-111">下列範例會將值指派給特定的陣列元素。</span><span class="sxs-lookup"><span data-stu-id="1e2df-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="1e2df-112">同樣地，下列範例會取得特定陣列元素的值，並將它指派給 `elementValue` 變數。</span><span class="sxs-lookup"><span data-stu-id="1e2df-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="1e2df-113">下列程式碼範例會將陣列元素初始化為預設值 (除了不規則陣列外)。</span><span class="sxs-lookup"><span data-stu-id="1e2df-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="1e2df-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="1e2df-114">See also</span></span>

- [<span data-ttu-id="1e2df-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1e2df-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1e2df-116">陣列</span><span class="sxs-lookup"><span data-stu-id="1e2df-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="1e2df-117">一維陣列</span><span class="sxs-lookup"><span data-stu-id="1e2df-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="1e2df-118">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="1e2df-118">Jagged Arrays</span></span>](./jagged-arrays.md)
