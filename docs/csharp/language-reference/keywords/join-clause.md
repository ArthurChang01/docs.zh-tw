---
title: join 子句 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 8e52e9db241392b67818b7316767dd97bd38432a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713398"
---
# <a name="join-clause-c-reference"></a>join 子句 (C# 參考)

`join` 子句可用於將不同來源序列中的項目產生關聯，這些項目在物件模型中沒有直接關聯性。 唯一的需求是每個來源中的項目必須共用可比較是否相等的特定值。 例如，食品經銷商可能有一份特定產品的供應商清單，以及一份買家清單。 針對位於相同指定地區的所有供應商和買家，可使用 `join` 子句來建立該產品的供應商和買家清單。

`join` 子句接受兩個來源序列作為輸入。 每個序列中的項目必須是可與另一個序列中的對應屬性進行比較的屬性，或包含這類屬性。 `join` 子句使用特殊的 `equals` 關鍵字，來比較指定的索引鍵是否相等。 `join` 子句執行的所有聯結都是等聯結。 `join` 子句輸出的組織結構取決於您要執行之聯結的特定類型。 以下是三種最常見的聯結類型：

- 內部聯結

- 群組聯結

- 左方外部聯結

## <a name="inner-join"></a>內部聯結

下列範例顯示一個簡單的內部等聯結。 此查詢會產生「產品名稱/分類」配對的一般序列。 相同的分類字串會出現在多個項目中。 如果 `categories` 中有某個項目具有不相符的 `products`，則該分類不會出現在結果中。

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

如需詳細資訊，請參閱[執行內部聯結](../../linq/perform-inner-joins.md)。

## <a name="group-join"></a>群組聯結

具有 `into` 運算式的 `join` 子句稱為群組聯結。

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

群組聯結會產生階層式結果序列，將左側來源序列中的項目與右側來源序列中的一或多個相符項目產生關聯。 群組聯結從關聯式觀點來看沒有對等項目，它基本上是物件陣列的序列。

如果右側來源序列中找不到項目會符合左側來源的項目，`join` 子句會針對該項目產生空陣列。 因此，群組聯結基本上仍然是內部等聯結，不同之處在於結果序列會組織成群組。

如果您只選取群組聯結的結果，便可以存取項目，但無法識別比對的索引鍵。 因此，選取群組聯結成同時具有索引鍵名稱之新類型的結果，通常會比較有用 (如上述範例所示)。

您當然也可以使用群組聯結的結果，作為另一個子查詢的產生器：

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

如需詳細資訊，請參閱[執行群組聯結](../../linq/perform-grouped-joins.md)。

## <a name="left-outer-join"></a>左方外部聯結

在左方外部聯結中，會傳回左側來源序列中的所有項目，即使在右側序列中沒有相符項目亦然。 要在 LINQ 中執行左外部聯結，`DefaultIfEmpty`請使用 方法與組聯接結合使用，以指定在左側元素沒有匹配項時要生成預設的右側元素。 您可以使用 `null` 作為任何參考型別的預設值，也可以指定使用者定義的預設類型。 在下列範例中，會顯示使用者定義的預設類型：

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

如需詳細資訊，請參閱[執行左方外部聯結](../../linq/perform-left-outer-joins.md)。

## <a name="the-equals-operator"></a>等號運算子

`join` 子句會執行等聯結。 換句話說，您只能根據兩個索引鍵是否相等進行比對。 不支援其他比較類型，例如「大於」或「不等於」。 為了釐清所有聯結都是等聯結，`join` 子句使用 `equals` 關鍵字而非 `==` 運算子。 `equals` 關鍵字只能用於 `join` 子句，而且與 `==` 運算子有一個重要的差異。 使用 `equals` 時，左側索引鍵會取用外部來源序列，而右側索引鍵會取用內部來源。 外部來源只會在 `equals` 的左側範圍內，而內部來源序列只會在右側範圍內。

## <a name="non-equijoins"></a>非等聯結

您可以使用多個 `from` 子句單獨將新的序列引入查詢，以執行非等聯結、交叉聯結及其他自訂聯結作業。 如需詳細資訊，請參閱[執行自訂聯結作業](../../linq/perform-custom-join-operations.md)。

## <a name="joins-on-object-collections-vs-relational-tables"></a>物件集合上的聯結與關聯式資料表的比較

在 LINQ 查詢運算式中，聯接操作對物件集合執行。 物件集合無法以與兩個關聯式資料表完全相同的方式進行「聯結」。 在 LINQ`join`中，僅當兩個源序列不與任何關係綁定時，才需要顯式子句。 使用 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 時，外部索引鍵資料表在物件模型中會表示為主要資料表的屬性。 例如，在 Northwind 資料庫中，Customer 資料表與 Orders 資料表有外部索引鍵關聯性。 當您將資料表對應至物件模型時，Customer 類別會有 Orders 屬性，其中包含與 Customer 相關聯之 Orders 的集合。 實際上已為您完成此聯結。

如需在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 內容中查詢所有關聯資料表的詳細資訊，請參閱[如何︰對應資料庫關聯性](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md)。

## <a name="composite-keys"></a>複合索引鍵

您可以使用複合索引鍵來測試多個值是否相等。 如需詳細資訊，請參閱[使用複合索引鍵執行聯結](../../linq/join-by-using-composite-keys.md)。 複合索引鍵也可用於 `group` 子句。

## <a name="example"></a>範例

下列範例使用相同的比對索引鍵，來比較相同資料來源中內部聯結、群組聯結和左方外部聯結的結果。 這些範例中新增了一些額外的程式碼，以釐清主控台顯示中的結果。

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>備註

如果 `join` 子句沒有後接 `into`，則會將該子句轉譯為 <xref:System.Linq.Enumerable.Join%2A> 方法呼叫。 如果 `join` 子句後接 `into`，則會將該子句轉譯為 <xref:System.Linq.Enumerable.GroupJoin%2A> 方法呼叫。

## <a name="see-also"></a>另請參閱

- [查詢關鍵字 （LINQ）](query-keywords.md)
- [語言綜合查詢（LINQ）](../../linq/index.md)
- [加入操作](../../programming-guide/concepts/linq/join-operations.md)
- [group 子句](group-clause.md)
- [執行左方外部聯結](../../linq/perform-left-outer-joins.md)
- [執行內部聯結](../../linq/perform-inner-joins.md)
- [執行群組聯結](../../linq/perform-grouped-joins.md)
- [排序 join 子句的結果](../../linq/order-the-results-of-a-join-clause.md)
- [使用複合索引鍵執行聯結](../../linq/join-by-using-composite-keys.md)
- [適用於 Visual Studio 相容的資料庫系統](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
