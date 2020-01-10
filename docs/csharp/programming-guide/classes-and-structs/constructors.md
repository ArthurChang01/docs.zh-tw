---
title: 建構函式 - C# 程式設計手冊
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 9c57ff6dd9acd8a8bcff6de4fce7d898f1135703
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714958"
---
# <a name="constructors-c-programming-guide"></a>建構函式 (C# 程式設計手冊)

每當建立[類別](../../language-reference/keywords/class.md)或[結構](../../language-reference/keywords/struct.md)時，都會呼叫其建構函式。 類別或結構可有使用不同引數的多個建構函式。 建構函式能讓程式設計師可以設定預設值、限制具現化，以及撰寫彈性且容易閱讀的程式碼。 如需詳細資訊和範例，請參閱[使用建構函式](./using-constructors.md)和[執行個體建構函式](./instance-constructors.md)。  

## <a name="parameterless-constructors"></a>無參數建構函式
  
如不提供類別的建構函式，C# 預設會建立一個可具現化物件的建構函式，並將成員變數設定為預設值，如[預設值表](../../language-reference/keywords/default-values-table.md)中所列。 若未提供結構的建構函式，C# 會依賴「隱含無參數建構函式」 來自動將實值型別的每個欄位初始化為其預設值，如[預設值表](../../language-reference/keywords/default-values-table.md)中所列。 如需詳細資訊及範例，請參閱[執行個體建構函式](./instance-constructors.md)。  

## <a name="constructor-syntax"></a>建構函式語法

建構函式是名稱與其類型名稱相同的方法。 其方法簽章只包含方法名稱及其參數清單，不包含傳回的類型。 下例示範名為 `Person` 的類別建構函式。

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

如果建構函式可以實作為單一陳述式，您就可以使用[運算式主體定義](../statements-expressions-operators/expression-bodied-members.md)。 下列範例定義 `Location` 類別，這個類別的建構函式包含名為 *name* 的單一字串參數。 運算式主體定義會將引數指派給 `locationName` 欄位。

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>靜態建構函式

前例都已顯示建立新物件的執行個體建構函式。 類別或結構也可以有靜態建構函式，用來初始化類型的靜態成員。  靜態建構函式無參數。 若您未提供靜態建構函式來初始化靜態欄位，C# 編譯器會將靜態欄位初始化為其預設值，如[預設值表](../../language-reference/keywords/default-values-table.md)中所列。

下列範例會使用靜態建構函式來初始化靜態欄位。

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

您也可以使用運算式主體定義來定義靜態建構函式，如下例所示。 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

如需詳細資訊及範例，請參閱[靜態建構函式](./static-constructors.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [使用建構函式](./using-constructors.md)  
  
 [執行個體建構函式](./instance-constructors.md)  
  
 [私用建構函式](./private-constructors.md)  
  
 [靜態建構函式](./static-constructors.md)  
  
 [如何撰寫複製的構造函式](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](./index.md)
- [完成項](./destructors.md)
- [static](../../language-reference/keywords/static.md)
- [為什麼初始化運算式是以相反的循序執行，做為構造函式？第一部](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
