---
title: 介面 - C# 程式設計手冊
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: f4ee269f41e79562c113a7627816f797b083095e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79157074"
---
# <a name="interfaces-c-programming-guide"></a>介面 (C# 程式設計手冊)

介面包含非抽象[類](../../language-reference/keywords/class.md)或[結構](../../language-reference/builtin-types/struct.md)必須實現的一組相關功能的定義。 介面可以定義`static`方法，這些方法必須具有實現。 介面可以為其聲明的任何或所有實例成員提供預設實現。 介面不得聲明實例資料，如欄位、自動實現的屬性或類似屬性的事件。

例如，您可以藉由使用介面，在類別中包含多個來源的行為。 這項功能在 C# 中是很重要的，因為語言不支援類別的多重繼承。 此外，如果您要模擬結構繼承，則必須使用介面，因為它們實際上無法繼承自另一個結構或類別。

使用[介面](../../language-reference/keywords/interface.md)關鍵字定義介面，如以下示例所示。

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

介面的名稱必須是有效的 C#[識別碼名稱](../inside-a-program/identifier-names.md)。 依慣例，介面名稱的開頭是大寫的|capital `I`。

任何實作 <xref:System.IEquatable%601> 介面的類別或結構，必須包含 <xref:System.IEquatable%601.Equals%2A> 方法的定義，該方法符合介面指定的簽章。 如此一來，您可以倚賴實作 `IEquatable<T>` 的類別，以包含 `Equals` 方法，類別的執行個體可以使用該方法判斷它是否等於相同類別的另一個執行個體。

`IEquatable<T>` 的定義不提供 `Equals` 的實作。 類或結構可以實現多個介面，但類只能從單個類繼承。

如需抽象類別的詳細資訊，請參閱[抽象和密封類別以及類別成員](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。

介面可以包含實例方法、屬性、事件、索引子或這四個成員類型的任意組合。 介面可能包含靜態建構函式、欄位、常量或運算子。 如需範例的連結，請參閱[相關章節](./index.md#BKMK_RelatedSections)。 介面不能包含實例欄位、實例建構函式或終端子。 預設情況下，介面成員是公共的。

若要實作介面成員，實作類別的對應成員必須是公用、非靜態，且具有與介面成員相同的名稱和簽章。

當類或結構實現介面時，類或結構必須為介面聲明但不提供預設實現的所有成員提供實現。 不過，如果基底類別實作介面，則衍生自基底類別的任何類別都會繼承該實作。

下列範例會示範 <xref:System.IEquatable%601> 介面的實作。 實作類別 `Car` 必須提供 <xref:System.IEquatable%601.Equals%2A> 方法的實作。

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

類別的屬性與索引子可以針對介面中定義的屬性或索引子定義額外的存取子。 例如，介面可能會宣告具有 [get](../../language-reference/keywords/get.md) 存取子的屬性。 實作介面的類別可以宣告具有 `get` 和 [set](../../language-reference/keywords/set.md) 存取子的相同屬性。 不過，如果屬性或索引子使用明確的實作，則存取子必須相符。 如需明確實作的詳細資訊，請參閱[明確介面實作](explicit-interface-implementation.md)和[介面屬性](../classes-and-structs/interface-properties.md)。

介面可以從一個或多個介面繼承。 派生介面從其基本介面繼承成員。 實現派生介面的類必須實現派生介面中的所有成員，包括派生介面基介面的所有成員。 該類可以隱式轉換為派生介面或其任何基本介面。 類別可能透過基底類別包含介面多次，繼承或透過其他介面繼承的介面。 不過，類別只能提供介面實作一次，而且只有在類別將介面宣告為類別 (`class ClassName : InterfaceName`) 定義的一部分時。 如果因為您繼承實作介面的基底類別而繼承介面，則基底類別會提供介面成員的實作。 不過，衍生的類別可以實作任何虛擬介面成員，而不使用繼承的實作。 當介面聲明方法的預設實現時，該介面的任何實現類都將繼承該實現。 在介面中定義的實現是虛擬的，實現類可以覆蓋該實現。

基底類別也可以使用虛擬成員來實作介面成員。 在此情況下，衍生的類別可以藉由覆寫虛擬成員來變更介面行為。 如需虛擬成員的詳細資訊，請參閱[多型](../classes-and-structs/polymorphism.md)。

## <a name="interfaces-summary"></a>介面摘要

介面具有下列屬性：

- 介面通常類似于只有抽象成員的抽象基類。 任何實作介面的類別或結構必須實作它的所有成員。 或者，介面可以為其部分或全部成員定義預設實現。
- 介面無法直接具現化。 其成員是由實作介面的任何類別或結構實作。
- 類別或結構可以實作多個介面。 類別可以繼承基底類別，也會實作一或多個介面。

## <a name="BKMK_RelatedSections"></a>相關部分

- [介面屬性](../classes-and-structs/interface-properties.md)  
- [介面中的索引子](../indexers/indexers-in-interfaces.md)  
- [如何實作介面事件](../events/how-to-implement-interface-events.md)
- [類別和結構](../classes-and-structs/index.md)  
- [繼承](../classes-and-structs/inheritance.md)  
- [方法](../classes-and-structs/methods.md)  
- [Polymorphism](../classes-and-structs/polymorphism.md)  
- [抽象和密封類別以及類別成員](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [屬性](../classes-and-structs/properties.md)  
- [事件](../events/index.md)  
- [索引子](../indexers/index.md)  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [繼承](../classes-and-structs/inheritance.md)
- [識別碼名稱](../inside-a-program/identifier-names.md)
