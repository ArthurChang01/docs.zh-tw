---
title: delegate 運算子 - C# 參考
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 9a78faaccffa9e7d4bf2829d8dfa0fa62a788bba
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039034"
---
# <a name="delegate-operator-c-reference"></a>delegate 運算子 (C# 參考)

`delegate` 運算子會建立可轉換成委派型別的匿名方法：

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> 從C# 3 開始，lambda 運算式提供更精簡且更具表達性的方式來建立匿名函數。 使用 [=> 運算子](lambda-operator.md)來建構 Lambda 運算式：
>
> [!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]
>
> 如需 Lambda 運算式功能的詳細資訊 (例如，捕捉外部變數)，請參閱 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。

當您使用 `delegate` 運算子時，您可以省略參數清單。 如果您這樣做，則可以將建立的匿名方法轉換成含任何參數清單的委派型別，如下列範例所示：

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

那是 Lambda 運算式不支援的唯一匿名方法功能。 在所有其他情況下，建議您以 Lambda 運算式的方式來撰寫內嵌程式碼。

您也可以使用 `delegate` 關鍵字來宣告[委派型別](../builtin-types/reference-types.md#the-delegate-type)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 運算子](index.md)
- [= > 運算子](lambda-operator.md)
