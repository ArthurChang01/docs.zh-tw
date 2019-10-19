---
title: 區域類型推斷 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 26df91229f7c640f53fcc018d881f7d24baf7e42
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582458"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="26ec4-102">區域類型推斷 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26ec4-102">Local Type Inference (Visual Basic)</span></span>

<span data-ttu-id="26ec4-103">Visual Basic 編譯器會使用*型別推斷*來判斷未使用 `As` 子句所宣告的本機變數資料類型。</span><span class="sxs-lookup"><span data-stu-id="26ec4-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="26ec4-104">編譯器會從初始化運算式的類型推斷變數的類型。</span><span class="sxs-lookup"><span data-stu-id="26ec4-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="26ec4-105">這可讓您宣告變數，而不需要明確陳述型別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="26ec4-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="26ec4-106">做為宣告的結果，`num1` 和 `num2` 都是強型別做為整數。</span><span class="sxs-lookup"><span data-stu-id="26ec4-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="26ec4-107">如果您不想要將上一個範例中的 `num2` 輸入 `Integer`，您可以使用 `Dim num3 As Object = 3` 或 `Dim num4 As Double = 3` 之類的宣告來指定另一個型別。</span><span class="sxs-lookup"><span data-stu-id="26ec4-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>

> [!NOTE]
> <span data-ttu-id="26ec4-108">型別推斷只能用於非靜態的區域變數;它不能用來判斷類別欄位、屬性或函數的類型。</span><span class="sxs-lookup"><span data-stu-id="26ec4-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>

<span data-ttu-id="26ec4-109">區欄位型別推斷適用于程式層級。</span><span class="sxs-lookup"><span data-stu-id="26ec4-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="26ec4-110">它不能用來宣告模組層級的變數（在類別、結構、模組或介面中，而不是在程式或區塊內）。</span><span class="sxs-lookup"><span data-stu-id="26ec4-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="26ec4-111">如果上一個範例中的 `num2` 是類別的欄位，而不是程式中的區域變數，則宣告會造成 `Option Strict` 的錯誤，並將 `num2` 分類為 `Option Strict` 關閉的 `Object`。</span><span class="sxs-lookup"><span data-stu-id="26ec4-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="26ec4-112">同樣地，區欄位型別推斷不適用於宣告為 `Static` 的程式層級變數。</span><span class="sxs-lookup"><span data-stu-id="26ec4-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>

## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="26ec4-113">型別推斷與晚期繫結的比較</span><span class="sxs-lookup"><span data-stu-id="26ec4-113">Type Inference vs. Late Binding</span></span>

<span data-ttu-id="26ec4-114">使用型別推斷的程式碼類似依賴晚期繫結的程式碼。</span><span class="sxs-lookup"><span data-stu-id="26ec4-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="26ec4-115">不過，類型推斷會強型別變數，而不是將它保留為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="26ec4-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="26ec4-116">編譯器會在編譯時期使用變數的初始化運算式來判斷變數的類型，以產生早期繫結程式碼。</span><span class="sxs-lookup"><span data-stu-id="26ec4-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="26ec4-117">在上述範例中，`num2` （例如 `num1`）會輸入為 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="26ec4-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>

<span data-ttu-id="26ec4-118">早期繫結變數的行為與晚期繫結變數的行為不同，只有在執行時間才會知道該類型。</span><span class="sxs-lookup"><span data-stu-id="26ec4-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="26ec4-119">早期瞭解型別可讓編譯器在執行之前找出問題、精確配置記憶體，以及執行其他優化。</span><span class="sxs-lookup"><span data-stu-id="26ec4-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="26ec4-120">早期繫結也會啟用 Visual Basic 的整合式開發環境（IDE），以提供有關物件成員的 IntelliSense 協助。</span><span class="sxs-lookup"><span data-stu-id="26ec4-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="26ec4-121">早期繫結也是效能的慣用選項。</span><span class="sxs-lookup"><span data-stu-id="26ec4-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="26ec4-122">這是因為儲存在晚期繫結變數中的所有資料都必須包裝為類型 `Object`，而且在執行時間存取類型的成員會使程式變慢。</span><span class="sxs-lookup"><span data-stu-id="26ec4-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>

## <a name="examples"></a><span data-ttu-id="26ec4-123">範例</span><span class="sxs-lookup"><span data-stu-id="26ec4-123">Examples</span></span>

<span data-ttu-id="26ec4-124">在未使用 `As` 子句來宣告區域變數並初始化時，就會發生型別推斷。</span><span class="sxs-lookup"><span data-stu-id="26ec4-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="26ec4-125">編譯器會使用指派之初始值的類型做為變數的類型。</span><span class="sxs-lookup"><span data-stu-id="26ec4-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="26ec4-126">例如，下列每一行程式碼都會宣告 `String` 類型的變數。</span><span class="sxs-lookup"><span data-stu-id="26ec4-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

<span data-ttu-id="26ec4-127">下列程式碼示範兩個對等的方式，以建立整數陣列。</span><span class="sxs-lookup"><span data-stu-id="26ec4-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

<span data-ttu-id="26ec4-128">使用型別推斷來判斷迴圈控制變數的型別是很方便的。</span><span class="sxs-lookup"><span data-stu-id="26ec4-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="26ec4-129">在下列程式碼中，編譯器會推斷 `number` 是 `Integer`，因為上一個範例中的 `someNumbers2` 是整數陣列。</span><span class="sxs-lookup"><span data-stu-id="26ec4-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

<span data-ttu-id="26ec4-130">區欄位型別推斷可以在 `Using` 語句中使用，以建立資源名稱的類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="26ec4-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

<span data-ttu-id="26ec4-131">您也可以從函式的傳回值推斷變數的類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="26ec4-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="26ec4-132">@No__t_0 和 `pList2` 都是進程陣列，因為 `Process.GetProcesses` 會傳回進程的陣列。</span><span class="sxs-lookup"><span data-stu-id="26ec4-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a><span data-ttu-id="26ec4-133">選項推斷</span><span class="sxs-lookup"><span data-stu-id="26ec4-133">Option Infer</span></span>

<span data-ttu-id="26ec4-134">`Option Infer` 可讓您指定是否允許在特定檔案中使用區欄位型別推斷。</span><span class="sxs-lookup"><span data-stu-id="26ec4-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="26ec4-135">若要啟用或封鎖選項，請在檔開頭輸入下列其中一個語句。</span><span class="sxs-lookup"><span data-stu-id="26ec4-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>

`Option Infer On`

`Option Infer Off`

<span data-ttu-id="26ec4-136">如果您未在程式碼中指定 `Option Infer` 的值，則編譯器預設為 `Option Infer On`。</span><span class="sxs-lookup"><span data-stu-id="26ec4-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span>

<span data-ttu-id="26ec4-137">如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。</span><span class="sxs-lookup"><span data-stu-id="26ec4-137">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="26ec4-138">如需詳細資訊，請參閱[選項推斷語句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[編譯頁面、專案設計工具（Visual Basic）](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="26ec4-138">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

## <a name="see-also"></a><span data-ttu-id="26ec4-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="26ec4-139">See also</span></span>

- [<span data-ttu-id="26ec4-140">匿名類型</span><span class="sxs-lookup"><span data-stu-id="26ec4-140">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="26ec4-141">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="26ec4-141">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="26ec4-142">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="26ec4-142">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="26ec4-143">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="26ec4-143">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="26ec4-144">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="26ec4-144">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="26ec4-145">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="26ec4-145">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="26ec4-146">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="26ec4-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
