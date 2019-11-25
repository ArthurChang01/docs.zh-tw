---
title: 物件變數
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7eb860bc732f923316b8ce1d7b94ecdb368bfec3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351788"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="58b0d-102">Visual Basic 中的物件變數</span><span class="sxs-lookup"><span data-stu-id="58b0d-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="58b0d-103">In addition to storing values directly, a variable can refer to an object.</span><span class="sxs-lookup"><span data-stu-id="58b0d-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="58b0d-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span><span class="sxs-lookup"><span data-stu-id="58b0d-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="58b0d-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span><span class="sxs-lookup"><span data-stu-id="58b0d-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="58b0d-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span><span class="sxs-lookup"><span data-stu-id="58b0d-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="58b0d-107">You can change a variable to refer to other objects while your code is running.</span><span class="sxs-lookup"><span data-stu-id="58b0d-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="58b0d-108">Making Code Shorter</span><span class="sxs-lookup"><span data-stu-id="58b0d-108">Making Code Shorter</span></span>

<span data-ttu-id="58b0d-109">You can use object variables to shorten the code you have to type.</span><span class="sxs-lookup"><span data-stu-id="58b0d-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="58b0d-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span><span class="sxs-lookup"><span data-stu-id="58b0d-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="58b0d-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span><span class="sxs-lookup"><span data-stu-id="58b0d-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="58b0d-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span><span class="sxs-lookup"><span data-stu-id="58b0d-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="58b0d-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span><span class="sxs-lookup"><span data-stu-id="58b0d-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="58b0d-114">You can set or retrieve the properties of the object or use any of its methods.</span><span class="sxs-lookup"><span data-stu-id="58b0d-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="58b0d-115">The following example uses an object variable to simplify the code in the preceding example.</span><span class="sxs-lookup"><span data-stu-id="58b0d-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="58b0d-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="58b0d-116">See also</span></span>

- [<span data-ttu-id="58b0d-117">變數宣告</span><span class="sxs-lookup"><span data-stu-id="58b0d-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="58b0d-118">如何：加快存取具有限定性條件長路徑的物件</span><span class="sxs-lookup"><span data-stu-id="58b0d-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="58b0d-119">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="58b0d-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="58b0d-120">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="58b0d-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="58b0d-121">物件變數值</span><span class="sxs-lookup"><span data-stu-id="58b0d-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
