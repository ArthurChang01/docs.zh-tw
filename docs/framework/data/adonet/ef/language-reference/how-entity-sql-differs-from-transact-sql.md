---
title: Entity SQL 與 Transact-SQL 的相異之處
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e0af0a415d812337d6abf449e9ee170526c3df0c
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833715"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Entity SQL 與 Transact-SQL 的相異之處
本主題描述 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 與 Transact-sql 之間的差異。  
  
## <a name="inheritance-and-relationships-support"></a>繼承和關聯性支援  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 直接與概念實體架構搭配運作，並且支援繼承和關聯性等概念模型功能。  
  
 當使用繼承時，從超型別執行個體的集合中選取子型別執行個體的作法通常會很實用。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的[oftype](oftype-entity-sql.md)運算子（類似于序列中C#的 `oftype`）提供這項功能。  
  
## <a name="support-for-collections"></a>集合的支援  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會將集合視為第一類實體。 例如，  
  
- 集合運算式在 `from` 子句中是有效的。  
  
- `in` 和 `exists` 子查詢已一般化，可允許任何集合。  
  
     子查詢是一種集合。 `e1 in e2` 和 `exists(e)` 是用來執行這些作業的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 結構。  
  
- Set 作業 (如 `union`、`intersect` 和 `except`) 現在都可針對集合來操作。  
  
- 聯結可針對集合操作。  
  
## <a name="support-for-expressions"></a>運算式的支援  
 Transact-sql 具有子查詢（資料表）和運算式（資料列和資料行）。  
  
 為了支援集合和嵌套集合，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 使所有專案成為運算式。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 比 Transact-sql 更具可組合，每個運算式都可以在任何地方使用。 查詢運算式一定會產生投影的型別集合，而且可在允許集合運算式的任何地方使用。 如需 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]中不支援之 Transact-sql 運算式的詳細資訊，請參閱[不](unsupported-expressions-entity-sql.md)支援的運算式。  
  
 下列全都是有效的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢：  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>子查詢的統一處理  
 基於資料表的強調，Transact-sql 會執行子查詢的內容相關轉譯。 例如，`from` 子句中的子查詢會被視為多重集（資料表）。 但是 `select` 子句中使用的相同子查詢會視為純量子查詢。 同樣地，在 `in` 運算子左邊使用的子查詢會被視為純量子查詢，而右側則應該是多重集子查詢。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 消除了這些差異。 運算式的統一解譯不依賴使用此運算式的內容。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會將所有子查詢視為多重集子查詢。 如果子查詢需要純量值，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會提供在集合（在此案例中為子查詢）運作的 `anyelement` 運算子，並從集合中抽取單一值。  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>避免子查詢的隱含強制型轉  
 統一的子查詢處理有一個相關的副作用，就是會隱含地將子查詢轉換成純量值。 具體而言，在 Transact-sql 中，資料列的多重集（具有單一欄位）會隱含地轉換成純量值，其資料類型是欄位。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不支援這種隱含強制型轉。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供 ANYELEMENT 運算子，以從集合中解壓縮單一值，並使用 `select value` 子句來避免在查詢運算式期間建立資料列包裝函式。  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Select Value：避免隱含資料列包裝函式  
 Transact-sql 子查詢中的 select 子句會以隱含方式，在子句中的專案周圍建立資料列包裝函式。 這意味我們無法建立純量或物件的集合。 Transact-sql 允許在具有一個欄位的 rowtype 與相同資料類型的單一值之間進行隱含強制型轉。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供 `select value` 子句來略過隱含資料列結構。 `select value` 子句中只能指定一個項目。 使用這類子句時，將不會建構包含 `select` 子句中這個項目的資料列包裝函式，並且可以產生所需形狀的集合，例如：`select value a`。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也會提供資料列的函數來建立任意資料列。 `select` 會採用投影中的一或多個專案，並產生具有欄位的資料記錄，如下所示：  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>左邊相互關聯與別名  
 在 Transact-sql 中，給定範圍內的運算式（`select` 或 `from`之類的單一子句）無法參考先前在相同範圍中定義的運算式。 某些 SQL （包括 Transact-sql）的方言在 `from` 子句中支援有限的形式。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 一般化 `from` 子句中的左相互關聯，並一致地加以處理。 `from` 子句中的運算式可參考相同子句中的先前定義 (左邊的定義)，而不需要其他語法。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也會對涉及 `group by` 子句的查詢施加額外的限制。 在這類查詢的 `select` 子句和 `having` 子句中的運算式，只能透過其別名來參考 `group by` 的索引鍵。 下列結構在 Transact-sql 中有效，但不在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]中：  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 若要在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中進行這項處理：  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>參考資料表 (集合) 的資料行 (屬性)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的所有資料行參考都必須以資料表別名來限定。 下列結構（假設 `a` 是資料表 `T`的有效資料行）在 Transact-sql 中有效，而不是在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]中。  
  
```sql  
SELECT a FROM T
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 格式如下：  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 資料表別名在 `from` 子句中為選擇性。 資料表名稱會當做隱含別名使用。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也允許下列表單：  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>導覽物件  
 Transact-sql 會使用 "." 標記法來參考資料表（之資料列）的資料行。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會擴充這個標記法（從程式語言借用）來支持對象屬性的導覽。  
  
 例如，如果 `p` 是 Person 型別的運算式，下列是用來參考這個人之地址所在城市的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 語法。  
  
```sql  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>\* 表示不支援  
 Transact-sql 支援不合格的 * 語法做為整個資料列的別名，以及限定的 \* 語法（t.\*）做為該資料表之欄位的快捷方式。 此外，Transact-sql 允許特殊的 count （\*）匯總，其中包含 null。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不支援 * 結構。 `select * from T` 和 `select T1.* from T1, T2...` 形式的 transact-SQL 查詢可以分別以 `select value t from T as t` 和 `select value t1 from T1 as t1, T2 as t2...`的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 表示。 此外，這些建構會處理繼承 (值的可替代性)，而 `select *` Variant 則限制為宣告之型別的最上層屬性。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不支援 `count(*)` 匯總。 請改用 `count(0)` 。  
  
## <a name="changes-to-group-by"></a>變更成 Group By  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援 `group by` 金鑰的別名。 `select` 子句和 `having` 子句中的運算式必須透過這些別名參考 `group by` 的索引鍵。 例如，這個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 語法：  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ...相當於下列 Transact-sql：  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>以集合為基礎的彙總  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援兩種類型的匯總。  
  
 以集合為基礎的彙總會針對集合運作，並產生彙總的結果。 這些可以出現在查詢中的任何地方，而且不需要 `group by` 子句。 例如，  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 也支援 SQL 樣式的匯總。 例如，  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY 子句使用方式  
Transact-sql 只允許在最上層的 `SELECT .. FROM .. WHERE` 區塊中指定 `ORDER BY` 子句。 在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 您可以使用嵌套的 `ORDER BY` 運算式，而且它可以放在查詢中的任何位置，但不會保留在巢狀查詢中的順序。  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>識別項  
 在 Transact-sql 中，識別碼比較是以目前資料庫的定序為基礎。 在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中，識別項一律不會區分大小寫，但是會區分腔調字 (Accent Sensitive) (亦即，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會區別有腔調和無腔調字元。例如，'a' 不等於 'ấ')。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會將出現相同但來自不同字碼頁的字母版本視為不同的字元。 如需詳細資訊，請參閱[輸入字元集](input-character-set-entity-sql.md)。  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Entity SQL 中無法使用 Transact-SQL 功能  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]中無法使用下列 Transact-sql 功能。  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 目前不提供 DML 語句（insert、update、delete）的支援。  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 在目前版本中不提供 DDL 的支援。  
  
 命令式程式設計  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不會提供命令式程式設計的支援，與 Transact-sql 不同。 請改用程式語言。  
  
 群組函式  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 尚未提供群組函式的支援（例如 CUBE、ROLLUP 和 GROUPING_SET）。  
  
 分析函式  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 尚未提供分析函數的支援。  
  
 內建函式，運算子  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援 Transact-sql 內建函數和運算子的子集。 主要存放區提供者可能會支援這些運算子和函式。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 會使用在提供者資訊清單中宣告的存放區特有函式。 此外，Entity Framework 可讓您宣告內建和使用者定義的現有存放區函式，以供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 使用。  
  
 提示  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不提供查詢提示的機制。  
  
 批次處理查詢結果  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不支援批次處理查詢結果。 例如，下列是有效的 Transact-sql （以批次傳送）：  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 但是，同等的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 未受到支援：  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 只支援每個命令產生一個結果的查詢語句。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
- [不支援的運算式](unsupported-expressions-entity-sql.md)
