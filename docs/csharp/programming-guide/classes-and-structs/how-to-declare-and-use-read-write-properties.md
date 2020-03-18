---
title: 如何聲明和使用讀寫屬性 - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 4b9db5f15746ab9a1f42239150c6783154723371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170282"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="7a3ef-102">如何聲明和使用讀寫屬性（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="7a3ef-102">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="7a3ef-103">屬性會提供公用資料成員的便利性，卻沒有不受保護、控制和驗證存取物件資料所附帶的風險。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="7a3ef-104">這是透過「存取子」\*\* 完成的：從基礎資料成員指派和擷取值的特殊方法。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="7a3ef-105">[set](../../language-reference/keywords/set.md) 存取子可讓資料成員被指派，而 [get](../../language-reference/keywords/get.md) 存取子可擷取資料成員值。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-105">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="7a3ef-106">這個範例會示範有兩個屬性的 `Person` 類別：`Name` (字串) 和 `Age` (整數)。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="7a3ef-107">這兩個屬性都提供 `get` 和 `set` 存取子，所以它們被視為讀取/寫入屬性。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a3ef-108">範例</span><span class="sxs-lookup"><span data-stu-id="7a3ef-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7a3ef-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="7a3ef-109">Robust Programming</span></span>  
 <span data-ttu-id="7a3ef-110">在上例中，`Name` 和 `Age` 屬性是[公用的](../../language-reference/keywords/public.md)，且同時包含 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-110">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="7a3ef-111">這可讓任何物件讀取和寫入這些屬性。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="7a3ef-112">但有時候會很想排除其中一個存取子。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="7a3ef-113">例如，省略 `set` 存取子會讓屬性變成唯讀的：</span><span class="sxs-lookup"><span data-stu-id="7a3ef-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="7a3ef-114">或者，您也可以向公眾公開某個存取子，但讓其他存取子為私用或受保護的。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="7a3ef-115">如需詳細資訊，請參閱[非對稱存取子的存取範圍](./restricting-accessor-accessibility.md)。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-115">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="7a3ef-116">屬性一旦宣告，即可當成類別的欄位使用。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="7a3ef-117">這在取得和設定屬性值時，可使用非常自然的語法，如下列陳述式所示：</span><span class="sxs-lookup"><span data-stu-id="7a3ef-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="7a3ef-118">請注意，在屬性 `set` 方法中提供特殊的 `value` 變數。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="7a3ef-119">此變數包含使用者指定的值，例如：</span><span class="sxs-lookup"><span data-stu-id="7a3ef-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="7a3ef-120">請注意在 `Person` 物件上遞增 `Age` 屬性的全新語法：</span><span class="sxs-lookup"><span data-stu-id="7a3ef-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="7a3ef-121">如果分別使用 `set` 和 `get` 方法建立了屬性模型，對等的程式碼可能看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="7a3ef-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="7a3ef-122">本例中覆寫 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="7a3ef-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="7a3ef-123">請注意，程式中未明確使用 `ToString`。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="7a3ef-124">預設會由 `WriteLine` 呼叫叫用。</span><span class="sxs-lookup"><span data-stu-id="7a3ef-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3ef-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a3ef-125">See also</span></span>

- [<span data-ttu-id="7a3ef-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7a3ef-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7a3ef-127">屬性</span><span class="sxs-lookup"><span data-stu-id="7a3ef-127">Properties</span></span>](./properties.md)
- [<span data-ttu-id="7a3ef-128">類別和結構</span><span class="sxs-lookup"><span data-stu-id="7a3ef-128">Classes and Structs</span></span>](./index.md)
