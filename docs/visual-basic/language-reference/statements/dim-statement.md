---
title: Dim 陳述式
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: 1b0c3089c366c417af926c8c0703cea021674432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744733"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="4d4e2-102">Dim 語句（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4d4e2-102">Dim statement (Visual Basic)</span></span>

<span data-ttu-id="4d4e2-103">宣告並配置一或多個變數的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-103">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d4e2-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d4e2-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="4d4e2-105">組件</span><span class="sxs-lookup"><span data-stu-id="4d4e2-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="4d4e2-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-106">Optional.</span></span> <span data-ttu-id="4d4e2-107">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="4d4e2-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-108">Optional.</span></span> <span data-ttu-id="4d4e2-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="4d4e2-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="4d4e2-110">公開</span><span class="sxs-lookup"><span data-stu-id="4d4e2-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="4d4e2-111">Protected</span><span class="sxs-lookup"><span data-stu-id="4d4e2-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="4d4e2-112">Friend</span><span class="sxs-lookup"><span data-stu-id="4d4e2-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="4d4e2-113">私用</span><span class="sxs-lookup"><span data-stu-id="4d4e2-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="4d4e2-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="4d4e2-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="4d4e2-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="4d4e2-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="4d4e2-116">請參閱 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="4d4e2-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-117">Optional.</span></span> <span data-ttu-id="4d4e2-118">請參閱[共用](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-118">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="4d4e2-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-119">Optional.</span></span> <span data-ttu-id="4d4e2-120">請參閱[Shadows](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-120">See [Shadows](../modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="4d4e2-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-121">Optional.</span></span> <span data-ttu-id="4d4e2-122">請參閱[靜態](../modifiers/static.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-122">See [Static](../modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="4d4e2-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-123">Optional.</span></span> <span data-ttu-id="4d4e2-124">請參閱[ReadOnly](../modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-124">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WithEvents`

  <span data-ttu-id="4d4e2-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-125">Optional.</span></span> <span data-ttu-id="4d4e2-126">指定這些是參考可引發事件之類別實例的物件變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="4d4e2-127">請參閱[WithEvents](../modifiers/withevents.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-127">See [WithEvents](../modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="4d4e2-128">必要。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-128">Required.</span></span> <span data-ttu-id="4d4e2-129">在此語句中宣告的變數清單。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-129">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="4d4e2-130">每個 `variable` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="4d4e2-130">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="4d4e2-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="4d4e2-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="4d4e2-132">部分</span><span class="sxs-lookup"><span data-stu-id="4d4e2-132">Part</span></span>|<span data-ttu-id="4d4e2-133">描述</span><span class="sxs-lookup"><span data-stu-id="4d4e2-133">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="4d4e2-134">必要。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-134">Required.</span></span> <span data-ttu-id="4d4e2-135">變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-135">Name of the variable.</span></span> <span data-ttu-id="4d4e2-136">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-136">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="4d4e2-137">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-137">Optional.</span></span> <span data-ttu-id="4d4e2-138">陣列變數的每個維度的界限清單。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-138">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="4d4e2-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-139">Optional.</span></span> <span data-ttu-id="4d4e2-140">當 `Dim` 語句執行時，建立類別的新實例。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="4d4e2-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-141">Optional.</span></span> <span data-ttu-id="4d4e2-142">變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-142">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="4d4e2-143">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-143">Optional.</span></span> <span data-ttu-id="4d4e2-144">引進物件初始化運算式清單。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-144">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="4d4e2-145">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-145">Optional.</span></span> <span data-ttu-id="4d4e2-146">您要做為實例之類別中的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-146">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="4d4e2-147">`propertyname` = 之後才需要。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-147">Required after `propertyname` =.</span></span> <span data-ttu-id="4d4e2-148">評估並指派給屬性名稱的運算式。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-148">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="4d4e2-149">如果未指定 `New`，則為選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="4d4e2-150">建立時，評估並指派給變數的運算式。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4d4e2-151">備註</span><span class="sxs-lookup"><span data-stu-id="4d4e2-151">Remarks</span></span>

<span data-ttu-id="4d4e2-152">Visual Basic 編譯器會使用 `Dim` 語句來判斷變數的資料類型和其他資訊，例如可存取變數的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="4d4e2-153">下列範例會宣告用來保存 `Integer` 值的變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-153">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="4d4e2-154">您可以指定任何資料類型，或是列舉、結構、類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="4d4e2-155">對於參考型別，您可以使用 `New` 關鍵字來建立由資料類型所指定之類別或結構的新實例。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="4d4e2-156">如果您使用 `New`，就不會使用初始化運算式運算式。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="4d4e2-157">相反地，您會提供引數（如有需要）到您要在其中建立變數之類別的函式。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="4d4e2-158">您可以在程式、區塊、類別、結構或模組中宣告變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="4d4e2-159">您無法在原始檔、命名空間或介面中宣告變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="4d4e2-160">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-160">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="4d4e2-161">在任何程式之外，于模組層級宣告的變數是*成員變數*或*欄位*。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="4d4e2-162">成員變數在其類別、結構或模組的範圍內。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="4d4e2-163">在程式層級宣告的變數是*本機變數*。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="4d4e2-164">區域變數僅限於其程式或區塊內的範圍。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-164">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="4d4e2-165">下列存取修飾詞是用來在程式之外宣告變數： `Public`、`Protected`、`Friend`、`Protected Friend`和 `Private`。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="4d4e2-166">如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-166">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="4d4e2-167">`Dim` 關鍵字是選擇性的，而且如果您指定下列任何修飾詞，通常會省略： `Public`、`Protected`、`Friend`、`Protected Friend`、`Private`、`Shared`、`Shadows`、`Static`、`ReadOnly`或 `WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="4d4e2-168">如果 `Option Explicit` 是 on （預設值），則編譯器需要您所使用之每個變數的宣告。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="4d4e2-169">如需詳細資訊，請參閱[Option Explicit 語句](option-explicit-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-169">For more information, see [Option Explicit Statement](option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="4d4e2-170">指定初始值</span><span class="sxs-lookup"><span data-stu-id="4d4e2-170">Specifying an initial value</span></span>

<span data-ttu-id="4d4e2-171">建立變數時，您可以將值指派給它。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="4d4e2-172">對於實值型別，您可以使用*初始化*運算式來提供要指派給變數的運算式。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="4d4e2-173">運算式必須評估為可在編譯時期計算的常數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="4d4e2-174">如果指定了初始化運算式，而且未在 `As` 子句中指定資料類型，則會使用*型別推斷*來推斷初始化運算式的資料型別。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="4d4e2-175">在下列範例中，`num1` 和 `num2` 都是強型別做為整數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="4d4e2-176">在第二個宣告中，型別推斷會從值3推斷型別。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-176">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="4d4e2-177">型別推斷適用于程式層級。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="4d4e2-178">不適用於類別、結構、模組或介面中的程式之外。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="4d4e2-179">如需型別推斷的詳細資訊，請參閱[Option 推斷語句](option-infer-statement.md)和[區欄位型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-179">For more information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="4d4e2-180">如需未指定資料類型或初始化運算式時，會發生什麼情況的詳細資訊，請參閱本主題稍後的[預設資料類型和值](dim-statement.md#default)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="4d4e2-181">您可以使用*物件初始化運算式*，宣告名為和匿名型別的實例。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="4d4e2-182">下列程式碼會建立 `Student` 類別的實例，並使用物件初始化運算式來初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="4d4e2-183">如需物件初始化運算式的詳細資訊，請參閱[如何：使用物件初始化運算式宣告物件](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)、[物件初始化運算式：命名和匿名型別](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)和[匿名型別](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="4d4e2-184">宣告多個變數</span><span class="sxs-lookup"><span data-stu-id="4d4e2-184">Declaring multiple variables</span></span>

<span data-ttu-id="4d4e2-185">您可以在一個宣告語句中宣告數個變數，為每一個宣告指定變數名稱，並在每個陣列名稱稱後面加上括弧。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="4d4e2-186">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-186">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="4d4e2-187">如果您使用一個 `As` 子句來宣告一個以上的變數，就無法為該變數群組提供初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="4d4e2-188">您可以針對您所宣告的每個變數使用個別的 `As` 子句，為不同的變數指定不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="4d4e2-189">每個變數都會接受在其 `variablename` 部分之後遇到的第一個 `As` 子句中指定的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="4d4e2-190">陣列</span><span class="sxs-lookup"><span data-stu-id="4d4e2-190">Arrays</span></span>

<span data-ttu-id="4d4e2-191">您可以宣告變數來保存*陣列*，其中可以保留多個值。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="4d4e2-192">若要指定變數保存陣列，請在其後面加上括弧的 `variablename`。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="4d4e2-193">如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-193">For more information about arrays, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="4d4e2-194">您可以指定陣列的每個維度的下限和上限。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="4d4e2-195">若要這麼做，請在括弧內包含 `boundslist`。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="4d4e2-196">`boundslist` 指定每個維度的上限和下限。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="4d4e2-197">下限一律為零，不論您是否指定。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="4d4e2-198">每個索引的上限值可能會從零開始。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-198">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="4d4e2-199">下列兩個語句是相等的。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-199">The following two statements are equivalent.</span></span> <span data-ttu-id="4d4e2-200">每個語句都會宣告21個 `Integer` 元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="4d4e2-201">當您存取陣列時，索引可能會從0到20。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-201">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="4d4e2-202">下列語句會宣告 `Double`類型的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="4d4e2-203">陣列有4個數據列（3 + 1），分別為6個數據行（5 + 1）。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="4d4e2-204">請注意，上限代表索引的最大可能值，而不是維度的長度。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="4d4e2-205">維度的長度是上限加一。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-205">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="4d4e2-206">陣列可以有1到32個維度。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-206">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="4d4e2-207">您可以在陣列宣告中將所有界限保留空白。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="4d4e2-208">如果您這樣做，陣列就會包含您指定的維度數目，但它是未初始化的。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="4d4e2-209">它的值為 `Nothing`，直到您至少初始化其中的部分元素為止。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="4d4e2-210">`Dim` 語句必須為所有維度或沒有維度指定界限。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="4d4e2-211">如果陣列有多個維度，您必須在括弧之間包含逗號，以指示維度的數目。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="4d4e2-212">您可以宣告陣列的其中一個維度為-1，以宣告*長度為零的陣列*。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="4d4e2-213">持有長度為零之陣列的變數沒有值 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="4d4e2-214">特定的 common language runtime 函式需要長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="4d4e2-215">如果您嘗試存取這類陣列，就會發生執行時間例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="4d4e2-216">如需詳細資訊，請參閱[陣列](../../programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-216">For more information, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="4d4e2-217">您可以使用陣列常值來初始化陣列的值。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="4d4e2-218">若要這麼做，請使用大括弧（`{}`）來括住初始化值。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-218">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="4d4e2-219">若是多維陣列，每個不同維度的初始化都會以大括弧括住在外部維度中。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="4d4e2-220">元素會以資料列主要順序來指定。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-220">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="4d4e2-221">如需陣列常值的詳細資訊，請參閱[陣列](../../programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-221">For more information about array literals, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default"></a><span data-ttu-id="4d4e2-222">預設資料類型和值</span><span class="sxs-lookup"><span data-stu-id="4d4e2-222">Default data types and values</span></span>

<span data-ttu-id="4d4e2-223">下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="4d4e2-224">指定了資料類型？</span><span class="sxs-lookup"><span data-stu-id="4d4e2-224">Data type specified?</span></span>|<span data-ttu-id="4d4e2-225">指定了初始設定式？</span><span class="sxs-lookup"><span data-stu-id="4d4e2-225">Initializer specified?</span></span>|<span data-ttu-id="4d4e2-226">範例</span><span class="sxs-lookup"><span data-stu-id="4d4e2-226">Example</span></span>|<span data-ttu-id="4d4e2-227">結果</span><span class="sxs-lookup"><span data-stu-id="4d4e2-227">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="4d4e2-228">否</span><span class="sxs-lookup"><span data-stu-id="4d4e2-228">No</span></span>|<span data-ttu-id="4d4e2-229">否</span><span class="sxs-lookup"><span data-stu-id="4d4e2-229">No</span></span>|`Dim qty`|<span data-ttu-id="4d4e2-230">如果[Option Strict](option-strict-statement.md)為 off （預設值），則變數會設定為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-230">If [Option Strict](option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="4d4e2-231">如果 `Option Strict` 已開啟，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="4d4e2-232">否</span><span class="sxs-lookup"><span data-stu-id="4d4e2-232">No</span></span>|<span data-ttu-id="4d4e2-233">是</span><span class="sxs-lookup"><span data-stu-id="4d4e2-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="4d4e2-234">如果[Option 推斷](option-infer-statement.md)為 on （預設值），則變數會採用初始化運算式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-234">If [Option Infer](option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="4d4e2-235">請參閱[區欄位型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-235">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="4d4e2-236">如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="4d4e2-237">如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="4d4e2-238">是</span><span class="sxs-lookup"><span data-stu-id="4d4e2-238">Yes</span></span>|<span data-ttu-id="4d4e2-239">否</span><span class="sxs-lookup"><span data-stu-id="4d4e2-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="4d4e2-240">變數會初始化為資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="4d4e2-241">請參閱本節稍後的表格。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-241">See the table later in this section.</span></span>|
|<span data-ttu-id="4d4e2-242">是</span><span class="sxs-lookup"><span data-stu-id="4d4e2-242">Yes</span></span>|<span data-ttu-id="4d4e2-243">是</span><span class="sxs-lookup"><span data-stu-id="4d4e2-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="4d4e2-244">如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="4d4e2-245">如果您指定資料類型，但未指定初始化運算式，Visual Basic 會將變數初始化為其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="4d4e2-246">下表顯示預設的初始化值。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-246">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="4d4e2-247">資料類型</span><span class="sxs-lookup"><span data-stu-id="4d4e2-247">Data type</span></span>|<span data-ttu-id="4d4e2-248">預設值</span><span class="sxs-lookup"><span data-stu-id="4d4e2-248">Default value</span></span>|
|---|---|
|<span data-ttu-id="4d4e2-249">所有數數值型別（包括 `Byte` 和 `SByte`）</span><span class="sxs-lookup"><span data-stu-id="4d4e2-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="4d4e2-250">0</span><span class="sxs-lookup"><span data-stu-id="4d4e2-250">0</span></span>|
|`Char`|<span data-ttu-id="4d4e2-251">二進位0</span><span class="sxs-lookup"><span data-stu-id="4d4e2-251">Binary 0</span></span>|
|<span data-ttu-id="4d4e2-252">所有參考型別（包括 `Object`、`String`和所有陣列）</span><span class="sxs-lookup"><span data-stu-id="4d4e2-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="4d4e2-253">每年1月1日上午12:00 （01/01/0001 12:00:00 AM）</span><span class="sxs-lookup"><span data-stu-id="4d4e2-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="4d4e2-254">結構的每個元素都會初始化為另一個變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="4d4e2-255">如果您宣告陣列的長度，但不初始化其元素，則每個專案都會初始化為個別的變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="4d4e2-256">靜態區域變數存留期</span><span class="sxs-lookup"><span data-stu-id="4d4e2-256">Static local variable lifetime</span></span>

<span data-ttu-id="4d4e2-257">`Static` 本機變數的存留期比宣告它的程式還長。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="4d4e2-258">變數存留期的界限取決於程式的宣告位置，以及是否 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="4d4e2-259">過程聲明</span><span class="sxs-lookup"><span data-stu-id="4d4e2-259">Procedure declaration</span></span>|<span data-ttu-id="4d4e2-260">變數已初始化</span><span class="sxs-lookup"><span data-stu-id="4d4e2-260">Variable initialized</span></span>|<span data-ttu-id="4d4e2-261">變數停止現有的</span><span class="sxs-lookup"><span data-stu-id="4d4e2-261">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="4d4e2-262">在模組中</span><span class="sxs-lookup"><span data-stu-id="4d4e2-262">In a module</span></span>|<span data-ttu-id="4d4e2-263">第一次呼叫程式時</span><span class="sxs-lookup"><span data-stu-id="4d4e2-263">The first time the procedure is called</span></span>|<span data-ttu-id="4d4e2-264">當程式停止執行時</span><span class="sxs-lookup"><span data-stu-id="4d4e2-264">When your program stops execution</span></span>|
|<span data-ttu-id="4d4e2-265">在類別或結構中，程式是 `Shared`</span><span class="sxs-lookup"><span data-stu-id="4d4e2-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="4d4e2-266">第一次在特定實例或類別或結構本身上呼叫程式時</span><span class="sxs-lookup"><span data-stu-id="4d4e2-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="4d4e2-267">當程式停止執行時</span><span class="sxs-lookup"><span data-stu-id="4d4e2-267">When your program stops execution</span></span>|
|<span data-ttu-id="4d4e2-268">在類別或結構中，程式不 `Shared`</span><span class="sxs-lookup"><span data-stu-id="4d4e2-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="4d4e2-269">第一次在特定實例上呼叫程式時</span><span class="sxs-lookup"><span data-stu-id="4d4e2-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="4d4e2-270">釋放實例以進行垃圾收集（GC）時</span><span class="sxs-lookup"><span data-stu-id="4d4e2-270">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="4d4e2-271">屬性和修飾詞</span><span class="sxs-lookup"><span data-stu-id="4d4e2-271">Attributes and modifiers</span></span>

<span data-ttu-id="4d4e2-272">您只能將屬性套用至成員變數，而不能套用至本機變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="4d4e2-273">屬性會將資訊提供給元件的中繼資料，這對暫存儲存體（例如區域變數）沒有意義。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="4d4e2-274">在模組層級，您無法使用 `Static` 修飾詞來宣告成員變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="4d4e2-275">在程式層級上，您不能使用 `Shared`、`Shadows`、`ReadOnly`、`WithEvents`或任何存取修飾詞來宣告本機變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="4d4e2-276">您可以藉由提供 `accessmodifier`，指定可以存取變數的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="4d4e2-277">類別和模組成員變數（在任何程式之外）預設為私用存取，而結構成員變數預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="4d4e2-278">您可以使用存取修飾詞來調整其存取層級。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="4d4e2-279">您不能在本機變數上使用存取修飾詞（在程式內）。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="4d4e2-280">您只能在成員變數上指定 `WithEvents`，而不是在程式內的區域變數上指定。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="4d4e2-281">如果您指定 `WithEvents`，變數的資料類型必須是特定的類別類型，而不是 `Object`。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="4d4e2-282">您無法使用 `WithEvents`宣告陣列。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="4d4e2-283">如需事件的詳細資訊，請參閱[事件](../../programming-guide/language-features/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-283">For more information about events, see [Events](../../programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4d4e2-284">類別、結構或模組之外的程式碼必須使用該類別、結構或模組的名稱來限定成員變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="4d4e2-285">程式或區塊外的程式碼無法參考該程式或區塊中的任何區域變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="4d4e2-286">釋放受控資源</span><span class="sxs-lookup"><span data-stu-id="4d4e2-286">Releasing managed resources</span></span>

<span data-ttu-id="4d4e2-287">.NET Framework 垃圾收集行程會處置受控資源，而不需任何額外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="4d4e2-288">不過，您可以強制處置受管理的資源，而不是等候垃圾收集行程。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="4d4e2-289">如果類別持有特別寶貴的資源（例如資料庫連接或檔案控制代碼），您可能不想要等到下一次垃圾收集，就能清除不再使用的類別實例。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="4d4e2-290">類別可以執行 <xref:System.IDisposable> 介面，以提供在垃圾收集之前釋放資源的方式。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="4d4e2-291">實作為介面的類別會公開可呼叫的 `Dispose` 方法，以強制立即釋放寶貴的資源。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="4d4e2-292">`Using` 語句會自動化取得資源、執行一組語句，然後處置資源的程式。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="4d4e2-293">不過，資源必須執行 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="4d4e2-294">如需詳細資訊，請參閱 [Using 陳述式](using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-294">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="4d4e2-295">範例</span><span class="sxs-lookup"><span data-stu-id="4d4e2-295">Example</span></span>

<span data-ttu-id="4d4e2-296">下列範例會使用 `Dim` 語句搭配各種選項來宣告變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-296">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="4d4e2-297">範例</span><span class="sxs-lookup"><span data-stu-id="4d4e2-297">Example</span></span>

<span data-ttu-id="4d4e2-298">下列範例會列出介於1到30之間的質數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="4d4e2-299">本機變數的範圍會在程式碼批註中說明。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-299">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="4d4e2-300">範例</span><span class="sxs-lookup"><span data-stu-id="4d4e2-300">Example</span></span>

<span data-ttu-id="4d4e2-301">在下列範例中，會在類別層級宣告 `speedValue` 變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="4d4e2-302">`Private` 關鍵字是用來宣告變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="4d4e2-303">`Car` 類別中的任何程式都可以存取變數。</span><span class="sxs-lookup"><span data-stu-id="4d4e2-303">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="4d4e2-304">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d4e2-304">See also</span></span>

- [<span data-ttu-id="4d4e2-305">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="4d4e2-305">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="4d4e2-306">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="4d4e2-306">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="4d4e2-307">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="4d4e2-307">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="4d4e2-308">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="4d4e2-308">Option Infer Statement</span></span>](option-infer-statement.md)
- [<span data-ttu-id="4d4e2-309">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="4d4e2-309">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="4d4e2-310">專案設計工具、編譯頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d4e2-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="4d4e2-311">變數宣告</span><span class="sxs-lookup"><span data-stu-id="4d4e2-311">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="4d4e2-312">陣列</span><span class="sxs-lookup"><span data-stu-id="4d4e2-312">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="4d4e2-313">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="4d4e2-313">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="4d4e2-314">匿名類型</span><span class="sxs-lookup"><span data-stu-id="4d4e2-314">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="4d4e2-315">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="4d4e2-315">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="4d4e2-316">如何：使用物件初始設定式宣告物件</span><span class="sxs-lookup"><span data-stu-id="4d4e2-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="4d4e2-317">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="4d4e2-317">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
