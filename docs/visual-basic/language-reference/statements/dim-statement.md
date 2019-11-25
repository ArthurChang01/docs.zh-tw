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
ms.openlocfilehash: ac66ffdba622673ef42017d147c05b2a2733dede
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343760"
---
# <a name="dim-statement-visual-basic"></a>Dim 陳述式 (Visual Basic)

Declares and allocates storage space for one or more variables.

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a>組件

- `attributelist`

  選擇項。 See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).

- `accessmodifier`

  選擇項。 可以是下列其中一項：

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

- `Shared`

  選擇項。 See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  選擇項。 See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Static`

  選擇項。 See [Static](../../../visual-basic/language-reference/modifiers/static.md).

- `ReadOnly`

  選擇項。 See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).

- `WithEvents`

選擇項。 Specifies that these are object variables that refer to instances of a class that can raise events. See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).

- `variablelist`

  必要項。 List of variables being declared in this statement.

  `variable [ , variable ... ]`

  每個 `variable` 都具有下列語法和組件：

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |組件|描述|
  |---|---|
  |`variablename`|必要項。 變數的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|
  |`boundslist`|選擇項。 List of bounds of each dimension of an array variable.|
  |`New`|選擇項。 Creates a new instance of the class when the `Dim` statement runs.|
  |`datatype`|選擇項。 Data type of the variable.|
  |`With`|選擇項。 Introduces the object initializer list.|
  |`propertyname`|選擇項。 The name of a property in the class you are making an instance of.|
  |`propinitializer`|Required after `propertyname` =. The expression that is evaluated and assigned to the property name.|
  |`initializer`|Optional if `New` is not specified. Expression that is evaluated and assigned to the variable when it is created.|

## <a name="remarks"></a>備註

The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable. The following example declares a variable to hold an `Integer` value.

```vb
Dim numberOfStudents As Integer
```

You can specify any data type or the name of an enumeration, structure, class, or interface.

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type. If you use `New`, you do not use an initializer expression. Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

You can declare a variable in a procedure, block, class, structure, or module. You cannot declare a variable in a source file, namespace, or interface. 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。

A variable that is declared at module level, outside any procedure, is a *member variable* or *field*. Member variables are in scope throughout their class, structure, or module. A variable that is declared at procedure level is a *local variable*. Local variables are in scope only within their procedure or block.

The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`. For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use. For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).

## <a name="specifying-an-initial-value"></a>Specifying an Initial Value

You can assign a value to a variable when it is created. For a value type, you use an *initializer* to supply an expression to be assigned to the variable. The expression must evaluate to a constant that can be calculated at compile time.

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer. In the following example, both `num1` and `num2` are strongly typed as integers. In the second declaration, type inference infers the type from the value 3.

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

Type inference applies at the procedure level. It does not apply outside a procedure in a class, structure, module, or interface. For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.

You can use an *object initializer* to declare instances of named and anonymous types. The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="declaring-multiple-variables"></a>Declaring Multiple Variables

You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses. 以逗號分隔多個變數。

```vb
Dim lastTime, nextTime, allTimes() As Date
```

If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.

You can specify different data types for different variables by using a separate `As` clause for each variable you declare. Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>陣列

You can declare a variable to hold an *array*, which can hold multiple values. To specify that a variable holds an array, follow its `variablename` immediately with parentheses. 如需陣列的詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。

You can specify the lower and upper bound of each dimension of an array. To do this, include a `boundslist` inside the parentheses. For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound. The lower bound is always zero, whether you specify it or not. Each index can vary from zero through its upper bound value.

The following two statements are equivalent. Each statement declares an array of 21 `Integer` elements. When you access the array, the index can vary from 0 through 20.

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

The following statement declares a two-dimensional array of type `Double`. The array has 4 rows (3 + 1) of 6 columns (5 + 1) each. Note that an upper bound represents the highest possible value for the index, not the length of the dimension. The length of the dimension is the upper bound plus one.

```vb
Dim matrix2(3, 5) As Double
```

An array can have from 1 to 32 dimensions.

You can leave all the bounds blank in an array declaration. If you do this, the array has the number of dimensions you specify, but it is uninitialized. It has a value of `Nothing` until you initialize at least some of its elements. The `Dim` statement must specify bounds either for all dimensions or for no dimensions.

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

You can declare a *zero-length array* by declaring one of the array's dimensions to be -1. A variable that holds a zero-length array does not have the value `Nothing`. Zero-length arrays are required by certain common language runtime functions. If you try to access such an array, a runtime exception occurs. 如需詳細資訊，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。

You can initialize the values of an array by using an array literal. To do this, surround the initialization values with braces (`{}`).

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension. The elements are specified in row-major order.

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="default"></a> Default Data Types and Values

下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。

|指定了資料類型？|指定了初始設定式？|範例|結果|
|---|---|---|---|
|否|否|`Dim qty`|If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時間錯誤。|
|否|[是]|`Dim qty = 5`|If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer. See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時間錯誤。|
|[是]|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 See the table later in this section.|
|[是]|[是]|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時期錯誤。|

If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type. The following table shows the default initialization values.

|資料類型|預設值|
|---|---|
|All numeric types (including `Byte` and `SByte`)|0|
|`Char`|Binary 0|
|All reference types (including `Object`, `String`, and all arrays)|`Nothing`|
|`Boolean`|`False`|
|`Date`|12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)|

Each element of a structure is initialized as if it were a separate variable. If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.

## <a name="static-local-variable-lifetime"></a>Static Local Variable Lifetime

A `Static` local variable has a longer lifetime than that of the procedure in which it is declared. The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.

|Procedure declaration|Variable initialized|Variable stops existing|
|---|---|---|
|In a module|The first time the procedure is called|When your program stops execution|
|In a class or structure, procedure is `Shared`|The first time the procedure is called either on a specific instance or on the class or structure itself|When your program stops execution|
|In a class or structure, procedure isn't `Shared`|The first time the procedure is called on a specific instance|When the instance is released for garbage collection (GC)|

## <a name="attributes-and-modifiers"></a>Attributes and Modifiers

You can apply attributes only to member variables, not to local variables. An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.

At module level, you cannot use the `Static` modifier to declare member variables. At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.

You can specify what code can access a variable by supplying an `accessmodifier`. Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access. You can adjust their access levels with the access modifiers. You cannot use access modifiers on local variables (inside a procedure).

You can specify `WithEvents` only on member variables, not on local variables inside a procedure. If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`. You cannot declare an array with `WithEvents`. For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).

> [!NOTE]
> Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module. Code outside a procedure or block cannot refer to any local variables within that procedure or block.

## <a name="releasing-managed-resources"></a>Releasing Managed Resources

The .NET Framework garbage collector disposes of managed resources without any extra coding on your part. However, you can force the disposal of a managed resource instead of waiting for the garbage collector.

If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use. A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection. A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.

The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource. However, the resource must implement the <xref:System.IDisposable> interface. 如需詳細資訊，請參閱 [Using 陳述式](../../../visual-basic/language-reference/statements/using-statement.md)。

## <a name="example"></a>範例

The following example declares variables by using the `Dim` statement with various options.

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>範例

The following example lists the prime numbers between 1 and 30. The scope of local variables is described in code comments.

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>範例

In the following example, the `speedValue` variable is declared at the class level. The `Private` keyword is used to declare the variable. The variable can be accessed by any procedure in the `Car` class.

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a>請參閱

- [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)
- [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [專案設計工具、編譯頁面 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [如何：使用物件初始設定式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
