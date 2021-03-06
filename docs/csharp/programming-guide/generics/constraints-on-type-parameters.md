---
title: 型別參數的條件約束 - C# 程式設計指南
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 0035f7d8aa862b4bd1b09a6f122a89786a6e295b
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738257"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>型別參數的條件約束 (C# 程式設計手冊)

條件約束會通知編譯器有關型別引數必須要有的功能。 如果沒有任何條件約束，則型別引數可以是任何型別。 編譯器只能採用 <xref:System.Object?displayProperty=nameWithType> 成員，這是任何 .NET 型別的最終基底類別。 如需詳細資訊，請參閱[為什麼使用條件約束](#why-use-constraints)。 如果用戶端代碼使用的類型不符合約束,編譯器將發出錯誤。 條件約束是使用 `where` 內容關鍵字所指定。 下表列出七種類型的條件約束：

|條件約束|描述|
|----------------|-----------------|
|`where T : struct`|類型參數必須是非空值類型。 關於空值型態的資訊,請參考[空數型態 。](../../language-reference/builtin-types/nullable-value-types.md) 由於所有值類型都有可訪問的無參數構造函數,因此`struct`約束意味著`new()`約束,並且不能與`new()`約束組合。 不能將`struct`約束與`unmanaged`約束合併。|
|`where T : class`|型別引數必須是參考型別。 此條件約束也適用於任何類別、介面、委派或陣列型別。 在 C# 8.0 或更高`T`版本中的空 上下文中,必須是不可取消的引用類型。 |
|`where T : class?`|類型參數必須是引用類型,可以是 null 或非空。 此條件約束也適用於任何類別、介面、委派或陣列型別。|
|`where T : notnull`|類型參數必須是非空類型。 該參數可以是 C# 8.0 或更高版本中的非空引用類型,也可以是非空值類型。 |
|`where T : unmanaged`|類型參數必須是非空[的非託管型態](../../language-reference/builtin-types/unmanaged-types.md)。 約束`unmanaged`意味著`struct`約束,不能與`struct`或`new()`約束組合。|
|`where T : new()`|型別引數必須有公用無參數建構函式。 與其他條件約束搭配使用時，`new()` 條件約束必須是最後一個指定的。 約束`new()`不能`struct`與`unmanaged`和約束結合使用。|
|`where T :` *基底類別名稱>\<*|型別引數必須是或衍生自指定的基底類別。 在 C# 8.0 及更高`T`版本中的空 上下文中,必須是派生自指定基類的非空引用類型。 |
|`where T :`基類名稱>? * \<*|型別引數必須是或衍生自指定的基底類別。 在 C# 8.0 及更高`T`版本中的可 空上下文中,可能是從指定基類派生的可空類型或非空類型。 |
|`where T :`*\<介面名稱>*|型別引數必須是或實作指定的介面。 您可以指定多個介面條件約束。 條件約束介面也是泛型。 在 C# 8.0 及更高`T`版本中的空 上下文中,必須是實現指定介面的非空類型。|
|`where T :`*\<介面名稱>?*|型別引數必須是或實作指定的介面。 您可以指定多個介面條件約束。 條件約束介面也是泛型。 在 C# 8.0 中的空`T`上下文中,可以是空引用類型、不可取消的引用類型或值類型。 `T`可能不是空值類型。|
|`where T : U`|提供`T`的類型參數必須為 或派生自`U`為 提供的參數。 在可 null 上下文`U`中, 如果為不可空`T`引用類型, 則必須是不可空的引用類型。 如果是`U`空引用類型,`T`則可以是空引用類型,也可以是非空引用類型。 |

## <a name="why-use-constraints"></a>為什麼使用條件約束

約束指定類型參數的功能和期望值。 聲明這些約束意味著您可以使用約束類型的操作和方法調用。 如果泛型類或方法對泛型成員使用任何操作,超出簡單賦值或調用任何不支援的方法<xref:System.Object?displayProperty=nameWithType>,則必須對類型參數應用約束。 例如，基底類別條件約束會告知編譯器只有這個類型的物件或衍生自這個類型的物件才會用作型別引數。 編譯器具有這項保證之後，就可以允許在泛型類別中呼叫該類型的方法。 下列程式碼範例示範您可以套用基底類別條件約束來新增至 `GenericList<T>` 類別的功能 (在[泛型簡介](../../../standard/generics/index.md)中)。

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

條件約束可讓泛型類別使用 `Employee.Name` 屬性。 條件約束指定 `T` 型別的所有項目保證都是 `Employee` 物件或繼承自 `Employee` 的物件。

多個條件約束可以套用至相同的型別參數，而且條件約束本身可以是泛型型別，如下所示：

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

套用 `where T : class` 條件約束時，請避免在型別參數上使用 `==` 和 `!=` 運算子，因為這些運算子只會測試參考識別是否相等，但不會測試值是否相等。 即使在用作引數的型別中多載這些運算子，也會發生這種行為。 下列程式碼說明這點；輸出為 false，即使 <xref:System.String> 類別多載 `==` 運算子也是一樣。

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

編譯器只知道它是`T`編譯時的引用類型,並且必須使用對所有引用類型有效的默認運算符。 如果您必須測試值是否相等，則建議同時套用 `where T : IEquatable<T>` 或 `where T : IComparable<T>` 條件約束，並在任何將用來建構泛型類別的類別中實作介面。

## <a name="constraining-multiple-parameters"></a>限制多個參數

您可以將條件約束套用至多個參數，以及將多個條件約束套用至單一參數，如下列範例所示：

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>未繫結的型別參數

 沒有條件約束的型別參數 (例如公用類別 `SampleClass<T>{}` 中的 T) 稱為「未繫結的型別參數」。 未繫結的型別參數具有下列規則：

- 不能`!=`使用`==`和運算符,因為不能保證具體類型參數將支援這些運算符。
- 它們可以與 `System.Object` 進行來回轉換，或明確轉換成任何介面類型。
- 您可以將它們與 [Null](../../language-reference/keywords/null.md) 比較。 如果未繫結的參數與 `null` 進行比較，則型別引數是實值型別時，比較一律會傳回 false。

## <a name="type-parameters-as-constraints"></a>作為條件約束的型別參數

具有專屬型別參數的成員函式需要將該參數限制為包含類型的型別參數時，將泛型型別參數用作條件約束十分有用，如下列範例所示：

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

在上述範例中，`T` 是 `Add` 方法內容中的類型條件約束，以及 `List` 類別內容中的未繫結型別參數。

型別參數也可以在泛型類別定義中用作條件約束。 型別參數必須與任何其他型別參數一起宣告於角括弧內：

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

型別參數作為條件約束對泛型類別來說不實用，因為編譯器除了會假設型別參數衍生自 `System.Object` 之外，不會再做其他任何假設。 如果您要強制兩個型別參數之間具有繼承關係，請在泛型類別上將型別參數用作條件約束。

## <a name="notnull-constraint"></a>非無限定

從空上下文中的 C# 8.0 開始`notnull`,可以使用 約束指定類型參數必須是不可空的值類型或不可空的引用類型。 約束`notnull`只能`nullable enable`在上下文中使用。 如果在可忽略的上下文中添加約束,`notnull`編譯器將生成警告。

與其他約束不同,當類型參數違反`notnull`約束時,編譯器`nullable enable`會在 上下文中編譯該代碼時發出警告。 如果代碼是在無虛無的上下文中編譯的,編譯器不會生成任何警告或錯誤。

從空上下文中的 C# 8.0`class`開始, 限制指定類型參數必須是不可空的引用類型。 在可無效上下文中,當類型參數為空引用類型時,編譯器將生成警告。

## <a name="unmanaged-constraint"></a>非受控條件約束

從 C# 7.3 開始`unmanaged`,可以使用限制指定類型參數必須是不可空[的非託管型態](../../language-reference/builtin-types/unmanaged-types.md)。 `unmanaged` 條件約束可讓您撰寫可重複使用的常式來使用型別，而型別可以操作為記憶體區塊，如下列範例所示：

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

上述方法必須在 `unsafe` 內容中進行編譯，因為它在不知道是內建型別的型別上使用 `sizeof` 運算子。 如果沒有 `unmanaged` 條件約束，則 `sizeof` 運算子無法使用。

約束`unmanaged`意味著`struct`約束,不能與它結合。 由於`struct`約束意味著`new()`約束,`unmanaged`因此也不能將約束`new()`與約束組合。

## <a name="delegate-constraints"></a>委派條件約束

而且，從 C# 7.3 開始，您可以使用 <xref:System.Delegate?displayProperty=nameWithType> 或 <xref:System.MulticastDelegate?displayProperty=nameWithType> 作為基底類別條件約束。 CLR 一律允許這個條件約束，但 C# 語言不允許它。 `System.Delegate` 條件約束可讓您撰寫程式碼，以型別安全方式使用委派。 以下代碼定義一種擴充方法,該方法合併了兩個委託,前提是它們的類型相同:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

您可以使用上述方法來結合型別相同的委派：

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

如果您將最後一行取消註解，則不會編譯它。 和`first``test`都是委託類型,但它們是不同的委託類型。

## <a name="enum-constraints"></a>列舉條件約束

從 C# 7.3 開始，您也可以指定 <xref:System.Enum?displayProperty=nameWithType> 型別作為基底類別條件約束。 CLR 一律允許這個條件約束，但 C# 語言不允許它。 使用 `System.Enum` 的泛型提供型別安全程式設計，以快取在 `System.Enum` 中使用靜態方法的結果。 下列範例會尋找列舉型別的所有有效值，然後建置將這些值對應至其字串表示法的字典。

[!code-csharp[using the enum constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

用於使用反射的方法,具有性能影響。 您可以呼叫這個方法來建置可快取和重複使用的集合，而不是重複需要反映的呼叫。

您可以如下列範例所示使用它來建立列舉，並建置其值和名稱的字典：

[!code-csharp[enum definition](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic>
- [C# 編程指南](../index.md)
- [泛型簡介](./index.md)
- [泛型類別](./generic-classes.md)
- [新的約束](../../language-reference/keywords/new-constraint.md)
