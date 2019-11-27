---
title: 如何：移入和移出變數資料
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bc5a7377a5e2e4c7ebe7291fd5f0093c4d6e996d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346895"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="c107f-102">如何：移入和移出變數資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c107f-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>

<span data-ttu-id="c107f-103">您可以藉由將變數名稱放在指派語句的左邊，將值儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="c107f-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>

## <a name="putting-data-in-a-variable"></a><span data-ttu-id="c107f-104">將資料放入變數中</span><span class="sxs-lookup"><span data-stu-id="c107f-104">Putting Data in a Variable</span></span>

#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="c107f-105">將值儲存在變數中</span><span class="sxs-lookup"><span data-stu-id="c107f-105">To store a value in a variable</span></span>

- <span data-ttu-id="c107f-106">在指派語句的左邊使用變數名稱。</span><span class="sxs-lookup"><span data-stu-id="c107f-106">Use the variable name on the left side of an assignment statement.</span></span>

    <span data-ttu-id="c107f-107">下列範例會將變數的值設定 `alpha`。</span><span class="sxs-lookup"><span data-stu-id="c107f-107">The following example sets the value of the variable `alpha`.</span></span>

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    <span data-ttu-id="c107f-108">在指派語句的右邊產生的值會儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="c107f-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>

## <a name="getting-data-from-a-variable"></a><span data-ttu-id="c107f-109">從變數取得資料</span><span class="sxs-lookup"><span data-stu-id="c107f-109">Getting Data from a Variable</span></span>

<span data-ttu-id="c107f-110">您可以藉由在運算式中包含變數名稱，來取出變數的值。</span><span class="sxs-lookup"><span data-stu-id="c107f-110">You retrieve a variable's value by including the variable name in an expression.</span></span>

#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="c107f-111">若要從變數中取出值</span><span class="sxs-lookup"><span data-stu-id="c107f-111">To retrieve a value from a variable</span></span>

- <span data-ttu-id="c107f-112">在運算式中使用變數名稱。</span><span class="sxs-lookup"><span data-stu-id="c107f-112">Use the variable name in an expression.</span></span> <span data-ttu-id="c107f-113">除了定義常數值的運算式以外，您可以在任何可使用常數或常值的地方使用變數。</span><span class="sxs-lookup"><span data-stu-id="c107f-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>

  <span data-ttu-id="c107f-114">\-或-</span><span class="sxs-lookup"><span data-stu-id="c107f-114">\-or-</span></span>

- <span data-ttu-id="c107f-115">在指派語句中的等號（`=`）後面使用變數名稱。</span><span class="sxs-lookup"><span data-stu-id="c107f-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>

  <span data-ttu-id="c107f-116">下列範例會讀取 `startValue` 變數的值，然後在運算式中使用變數 `counter` 的值。</span><span class="sxs-lookup"><span data-stu-id="c107f-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  <span data-ttu-id="c107f-117">變數的值會以常數的形式參與運算式，然後儲存在指派語句左側的變數或屬性中。</span><span class="sxs-lookup"><span data-stu-id="c107f-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="c107f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="c107f-118">See also</span></span>

- [<span data-ttu-id="c107f-119">變數</span><span class="sxs-lookup"><span data-stu-id="c107f-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="c107f-120">變數宣告</span><span class="sxs-lookup"><span data-stu-id="c107f-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="c107f-121">物件變數</span><span class="sxs-lookup"><span data-stu-id="c107f-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
