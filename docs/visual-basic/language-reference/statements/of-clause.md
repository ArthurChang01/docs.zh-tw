---
title: Of 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: c0cfbb5109d5b49f995028944e735c96440c9ab2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583513"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="479cd-102">Of 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="479cd-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="479cd-103">引進了一個 `Of` 子句，它會識別*泛型*類別、結構、介面、委派或程式上的*型別參數*。</span><span class="sxs-lookup"><span data-stu-id="479cd-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="479cd-104">如需泛型型別的詳細資訊，請參閱[Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="479cd-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="479cd-105">使用 of 關鍵字</span><span class="sxs-lookup"><span data-stu-id="479cd-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="479cd-106">下列程式碼範例會使用 `Of` 關鍵字來定義接受兩個型別參數之類別的外框。</span><span class="sxs-lookup"><span data-stu-id="479cd-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="479cd-107">它會*限制*<xref:System.IComparable> 介面的 `keyType` 參數，這表示取用的程式碼必須提供實作為 <xref:System.IComparable> 的型別引數。</span><span class="sxs-lookup"><span data-stu-id="479cd-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="479cd-108">這是必要的，因此 `add` 程式可以呼叫 <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="479cd-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="479cd-109">如需條件約束的詳細資訊，請參閱 [Type List](../../../visual-basic/language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="479cd-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```vb  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="479cd-110">如果您完成上述類別定義，您可以從它建立各種不同的 `dictionary` 類別。</span><span class="sxs-lookup"><span data-stu-id="479cd-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="479cd-111">您提供給 `entryType` 的型別，`keyType` 會決定類別所保存的專案類型，以及與每個專案相關聯的索引鍵類型。</span><span class="sxs-lookup"><span data-stu-id="479cd-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="479cd-112">由於條件約束的原因，您必須提供來 `keyType` 可執行 <xref:System.IComparable> 的類型。</span><span class="sxs-lookup"><span data-stu-id="479cd-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="479cd-113">下列程式碼範例會建立一個物件，它會保存 `String` 專案，並將 `Integer` 索引鍵與每一個金鑰相關聯。</span><span class="sxs-lookup"><span data-stu-id="479cd-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="479cd-114">`Integer` 會執行 <xref:System.IComparable>，因此滿足 `keyType` 上的條件約束。</span><span class="sxs-lookup"><span data-stu-id="479cd-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="479cd-115">`Of` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="479cd-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="479cd-116">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="479cd-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="479cd-117">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="479cd-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="479cd-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="479cd-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="479cd-119">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="479cd-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="479cd-120">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="479cd-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="479cd-121">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="479cd-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="479cd-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="479cd-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="479cd-123">類型清單</span><span class="sxs-lookup"><span data-stu-id="479cd-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="479cd-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="479cd-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="479cd-125">In</span><span class="sxs-lookup"><span data-stu-id="479cd-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="479cd-126">Out</span><span class="sxs-lookup"><span data-stu-id="479cd-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
