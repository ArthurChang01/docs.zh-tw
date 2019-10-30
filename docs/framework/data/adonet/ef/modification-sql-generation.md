---
title: 修改 SQL 產生
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: b6c1b71effba17d33c035d0f1df386bf56d405b5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039890"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="21a20-102">修改 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="21a20-102">Modification SQL Generation</span></span>

<span data-ttu-id="21a20-103">本節將討論如何為您的 (SQL:1999 相容資料庫) 提供者開發修改 SQL 產生模組。</span><span class="sxs-lookup"><span data-stu-id="21a20-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="21a20-104">這個模組負責將修改命令樹轉譯為適當的 SQL INSERT、UPDATE 或 DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="21a20-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>

<span data-ttu-id="21a20-105">如需 select 語句之 SQL 產生的詳細資訊，請參閱[Sql 世代](sql-generation.md)。</span><span class="sxs-lookup"><span data-stu-id="21a20-105">For information about SQL generation for select statements, see [SQL Generation](sql-generation.md).</span></span>

## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="21a20-106">修改命令樹概觀</span><span class="sxs-lookup"><span data-stu-id="21a20-106">Overview of Modification Command Trees</span></span>

<span data-ttu-id="21a20-107">修改 SQL 產生模組會根據給定輸入 DbModificationCommandTree 來產生資料庫特有的修改 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="21a20-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>

<span data-ttu-id="21a20-108">DbModificationCommandTree 是修改 DML 作業 (插入、更新或刪除作業) 的物件模型表示法，繼承自 DbCommandTree。</span><span class="sxs-lookup"><span data-stu-id="21a20-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="21a20-109">DbModificationCommandTree 有三個實作：</span><span class="sxs-lookup"><span data-stu-id="21a20-109">There are three implementations of DbModificationCommandTree:</span></span>

- <span data-ttu-id="21a20-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="21a20-110">DbInsertCommandTree</span></span>

- <span data-ttu-id="21a20-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="21a20-111">DbUpdateCommandTree</span></span>

- <span data-ttu-id="21a20-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="21a20-112">DbDeleteCommandTree</span></span>

<span data-ttu-id="21a20-113">Entity Framework 所產生的 DbModificationCommandTree 及其實現，一律代表單一資料列作業。</span><span class="sxs-lookup"><span data-stu-id="21a20-113">DbModificationCommandTree and its implementations that are produced by the Entity Framework always represent a single row operation.</span></span> <span data-ttu-id="21a20-114">這一節會描述 .NET Framework 3.5 版中的這些型別以及其條件約束。</span><span class="sxs-lookup"><span data-stu-id="21a20-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>

<span data-ttu-id="21a20-115">![圖表](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="21a20-115">![Diagram](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>

<span data-ttu-id="21a20-116">DbModificationCommandTree 有一個目標屬性，此屬性代表針對修改作業設定的目標。</span><span class="sxs-lookup"><span data-stu-id="21a20-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="21a20-117">定義輸入集的目標運算式屬性一定是 DbScanExpression。</span><span class="sxs-lookup"><span data-stu-id="21a20-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="21a20-118">DbScanExpression 可以代表資料表或視圖，或如果其目標的中繼資料屬性「定義查詢」為非 null，則會使用查詢定義的一組資料。</span><span class="sxs-lookup"><span data-stu-id="21a20-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>

<span data-ttu-id="21a20-119">只有當集合是使用模型中的定義查詢所定義，但是未針對對應的修改作業提供任何功能時，代表查詢的 DbScanExpression 才能當做修改目標聯繫提供者。</span><span class="sxs-lookup"><span data-stu-id="21a20-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="21a20-120">提供者可能無法支援這種案例 (例如 SqlClient 就無法支援)。</span><span class="sxs-lookup"><span data-stu-id="21a20-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>

<span data-ttu-id="21a20-121">DbInsertCommandTree 代表以命令樹表示的單一資料列插入作業。</span><span class="sxs-lookup"><span data-stu-id="21a20-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

<span data-ttu-id="21a20-122">DbUpdateCommandTree 代表以命令樹表示的單一資料列更新作業。</span><span class="sxs-lookup"><span data-stu-id="21a20-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>

<span data-ttu-id="21a20-123">DbDeleteCommandTree 代表以命令樹表示的單一資料列刪除作業。</span><span class="sxs-lookup"><span data-stu-id="21a20-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>

### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="21a20-124">修改命令樹屬性的限制</span><span class="sxs-lookup"><span data-stu-id="21a20-124">Restrictions on Modification Command Tree Properties</span></span>

<span data-ttu-id="21a20-125">下列資訊和限制會套用到修改命令樹屬性。</span><span class="sxs-lookup"><span data-stu-id="21a20-125">The following information and restrictions apply to the modification command tree properties.</span></span>

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="21a20-126">DbInsertCommandTree 和 DbUpdateCommandTree 中的 Returning</span><span class="sxs-lookup"><span data-stu-id="21a20-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="21a20-127">當不是 null 時，Returning 表示命令會傳回讀取器。</span><span class="sxs-lookup"><span data-stu-id="21a20-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="21a20-128">否則，此命令應該會傳回純量值，表示受影響 (插入或更新) 的資料列數。</span><span class="sxs-lookup"><span data-stu-id="21a20-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>

<span data-ttu-id="21a20-129">Returning 值會根據插入或更新的資料列，指定要傳回的結果投影。</span><span class="sxs-lookup"><span data-stu-id="21a20-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="21a20-130">它的型別只能是代表資料列的 DbNewInstanceExpression，而它的每一個引數都是透過 DbVariableReferenceExpression 的 DbPropertyExpression，代表對應之 DbModificationCommandTree 的目標參考。</span><span class="sxs-lookup"><span data-stu-id="21a20-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="21a20-131">用於 Returning 屬性之 DbPropertyExpressions 所代表的屬性一定會是存放區所產生或計算的值。</span><span class="sxs-lookup"><span data-stu-id="21a20-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="21a20-132">在 DbInsertCommandTree 中，當至少有一個資料表屬性 (資料列插入之處) 指定為存放區所產生或計算時 (標示為 ssdl 中的 StoreGeneratedPattern.Identity 或 StoreGeneratedPattern.Computed)，Returning 不會是 null。</span><span class="sxs-lookup"><span data-stu-id="21a20-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="21a20-133">在 DbUpdateCommandTrees 中，當至少有一個資料表屬性 (資料列更新之處) 指定為存放區所計算時 (標示為 ssdl 中的 StoreGeneratedPattern.Computed)，Returning 不會是 null。</span><span class="sxs-lookup"><span data-stu-id="21a20-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="21a20-134">DbInsertCommandTree 和 DbUpdateCommandTree 中的 SetClauses</span><span class="sxs-lookup"><span data-stu-id="21a20-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="21a20-135">SetClauses 會指定可定義插入或更新作業的插入或更新 SET 子句清單。</span><span class="sxs-lookup"><span data-stu-id="21a20-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>

<span data-ttu-id="21a20-136">清單的元素會指定為類型 DbModificationClause，這會指定插入或更新修改作業中的單一子句。</span><span class="sxs-lookup"><span data-stu-id="21a20-136">The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation.</span></span> <span data-ttu-id="21a20-137">DbSetClause 繼承自 DbModificationClause，並在設定屬性值的修改作業中指定子句。</span><span class="sxs-lookup"><span data-stu-id="21a20-137">DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property.</span></span> <span data-ttu-id="21a20-138">從 .NET Framework 的3.5 版開始，SetClauses 中的所有元素都屬於 SetClause 類型。</span><span class="sxs-lookup"><span data-stu-id="21a20-138">Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.</span></span>

<span data-ttu-id="21a20-139">Property 會指定應該更新的屬性。</span><span class="sxs-lookup"><span data-stu-id="21a20-139">Property specifies the property that should be updated.</span></span> <span data-ttu-id="21a20-140">它一定是透過 DbVariableReferenceExpression 的 DbPropertyExpression，代表對應之 DbModificationCommandTree 的目標參考。</span><span class="sxs-lookup"><span data-stu-id="21a20-140">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

<span data-ttu-id="21a20-141">Value 會指定用來更新屬性的新值。</span><span class="sxs-lookup"><span data-stu-id="21a20-141">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="21a20-142">它的型別會是 DbConstantExpression 或 DbNullExpression。</span><span class="sxs-lookup"><span data-stu-id="21a20-142">It is either of type DbConstantExpression or DbNullExpression.</span></span>

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="21a20-143">DbUpdateCommandTree 和 DbDeleteCommandTree 中的 Predicate</span><span class="sxs-lookup"><span data-stu-id="21a20-143">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>

<span data-ttu-id="21a20-144">Predicate 會指定用來判斷所應該更新或刪除之目標集合成員的述詞。</span><span class="sxs-lookup"><span data-stu-id="21a20-144">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="21a20-145">它是從下列 DbExpressions 子集所建置的運算式樹狀架構：</span><span class="sxs-lookup"><span data-stu-id="21a20-145">It is an expression tree built of the following subset of DbExpressions:</span></span>

- <span data-ttu-id="21a20-146">類型等於的 DbComparisonExpression，右邊的子系是下面限制的 DbPropertyExpression，而左邊的子系是 DbConstantExpression。</span><span class="sxs-lookup"><span data-stu-id="21a20-146">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExpression as restricted below and the left child a DbConstantExpression.</span></span>

- <span data-ttu-id="21a20-147">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="21a20-147">DbConstantExpression</span></span>

- <span data-ttu-id="21a20-148">透過 DbPropertyExpression 的 DbIsNullExpression，如下所限制</span><span class="sxs-lookup"><span data-stu-id="21a20-148">DbIsNullExpression over a DbPropertyExpression as restricted below</span></span>

- <span data-ttu-id="21a20-149">透過 DbVariableReferenceExpression 的 DbPropertyExpression，代表對應之 DbModificationCommandTree 的目標參考。</span><span class="sxs-lookup"><span data-stu-id="21a20-149">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

- <span data-ttu-id="21a20-150">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="21a20-150">DbAndExpression</span></span>

- <span data-ttu-id="21a20-151">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="21a20-151">DbNotExpression</span></span>

- <span data-ttu-id="21a20-152">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="21a20-152">DbOrExpression</span></span>

## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="21a20-153">範例提供者中的修改 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="21a20-153">Modification SQL Generation in the Sample Provider</span></span>

<span data-ttu-id="21a20-154">[Entity Framework 範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)會示範支援 Entity Framework 的 ADO.NET 資料提供者元件。</span><span class="sxs-lookup"><span data-stu-id="21a20-154">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the components of ADO.NET Data Providers that support the Entity Framework.</span></span> <span data-ttu-id="21a20-155">它會以 SQL Server 2005 資料庫為目標，並且實作成 System.Data.SqlClient ADO.NET 2.0 資料提供者上層的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="21a20-155">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>

<span data-ttu-id="21a20-156">範例提供者的修改 SQL 產生模組 (位於 SQL Generation\DmlSqlGenerator.cs 檔案中) 會採用 DbModificationCommandTree 輸入，並產生單一修改 SQL 陳述式，後面可能接著 select 陳述式來傳回讀取器 (如果 DbModificationCommandTree 有指定)。</span><span class="sxs-lookup"><span data-stu-id="21a20-156">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="21a20-157">請注意，產生之命令的形狀會受到目標 SQL Server 資料庫所影響。</span><span class="sxs-lookup"><span data-stu-id="21a20-157">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>

### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="21a20-158">協助程式類別：ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="21a20-158">Helper Classes: ExpressionTranslator</span></span>

<span data-ttu-id="21a20-159">ExpressionTranslator 會當做 DbExpression 型別之所有修改命令樹屬性的常用輕量型轉譯程式。</span><span class="sxs-lookup"><span data-stu-id="21a20-159">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="21a20-160">它只支援修改命令樹屬性所限制之運算式型別的轉譯，而且會根據特定的條件約束來建置。</span><span class="sxs-lookup"><span data-stu-id="21a20-160">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>

<span data-ttu-id="21a20-161">下列資訊將討論特定運算式型別的瀏覽 (略過具有一般轉譯的節點)。</span><span class="sxs-lookup"><span data-stu-id="21a20-161">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>

### <a name="dbcomparisonexpression"></a><span data-ttu-id="21a20-162">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="21a20-162">DbComparisonExpression</span></span>

<span data-ttu-id="21a20-163">當使用 preserveMemberValues = true 來建構 ExpressionTranslator 而且右邊的常數是 DbConstantExpression (而不是 DbNullExpression) 時，它會將左邊運算元 (DbPropertyExpressions) 與該 DbConstantExpression 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="21a20-163">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="21a20-164">如果需要產生傳回 Select 陳述式來識別受影響的資料列，就會使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="21a20-164">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>

### <a name="dbconstantexpression"></a><span data-ttu-id="21a20-165">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="21a20-165">DbConstantExpression</span></span>

<span data-ttu-id="21a20-166">針對每一個瀏覽過的常數建立參數。</span><span class="sxs-lookup"><span data-stu-id="21a20-166">For each visited constant a parameter is created.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="21a20-167">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="21a20-167">DbPropertyExpression</span></span>

<span data-ttu-id="21a20-168">假設 DbPropertyExpression 的執行個體一定代表輸入資料表，則除非產生作業已經建立別名 (只發生在使用資料表變數時的更新案例中)，否則不需要為輸入指定別名。轉譯預設為屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="21a20-168">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>

## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="21a20-169">產生插入 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="21a20-169">Generating an Insert SQL Command</span></span>

<span data-ttu-id="21a20-170">如果範例提供者中有提供 DbInsertCommandTree，產生的插入命令會遵循底下的其中一個插入範本。</span><span class="sxs-lookup"><span data-stu-id="21a20-170">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>

<span data-ttu-id="21a20-171">第一個範本有一個命令可在提供 SetClauses 清單中的值時執行插入，也有一個 SELECT 陳述式，可在 Returning 屬性不是 null 時，傳回 Returning 屬性中針對插入的資料列所指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="21a20-171">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="21a20-172">如果插入資料列，則述詞元素 "\@@ROWCOUNT > 0" 為 true。</span><span class="sxs-lookup"><span data-stu-id="21a20-172">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="21a20-173">只有當 Scope_identity 是存放區產生&#124;的索引鍵時，述詞元素 "KeyMemberI = keyValueI scope_identity （）" 才會採用 "keyMemberI = keyMemberI （）" 圖形，因為 scope_identity （）會傳回插入至身分識別的最後一個識別值（儲存區產生的）資料行。</span><span class="sxs-lookup"><span data-stu-id="21a20-173">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="21a20-174">如果插入作業指定插入某個資料列 (這裡的主索引鍵為存放區所產生，但不是整數類型，所以不能搭配 scope_identity() 使用))，則需要第二個範本。</span><span class="sxs-lookup"><span data-stu-id="21a20-174">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="21a20-175">如果有存放區產生的複合索引鍵，也會使用它。</span><span class="sxs-lookup"><span data-stu-id="21a20-175">It is also used if there is a compound store-generated key.</span></span>

```sql
-- second insert template
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)

INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning_over_t>
 FROM @generated_keys  AS g
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN
 WHERE @@ROWCOUNT > 0
```

<span data-ttu-id="21a20-176">下列範例會使用範例提供者所隨附的模型。</span><span class="sxs-lookup"><span data-stu-id="21a20-176">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="21a20-177">它會從 DbInsertCommandTree 產生插入命令。</span><span class="sxs-lookup"><span data-stu-id="21a20-177">It generates an insert command from a DbInsertCommandTree.</span></span>

<span data-ttu-id="21a20-178">下列程式碼會插入分類：</span><span class="sxs-lookup"><span data-stu-id="21a20-178">The following code inserts a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="21a20-179">此程式碼會產生傳遞給提供者的下列命令樹：</span><span class="sxs-lookup"><span data-stu-id="21a20-179">This code produces the following command tree, which is passed to the provider:</span></span>

```output
DbInsertCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
| | |_Property
| | | |_Var(target).CategoryName
| | |_Value
| |   |_'Test Category'
| |_DbSetClause
| | |_Property
| | | |_Var(target).Description
| | |_Value
| |   |_'A new category for testing'
| |_DbSetClause
|   |_Property
|   | |_Var(target).Picture
|   |_Value
|     |_null
|_Returning
  |_NewInstance : Record['CategoryID'=Edm.Int32]
    |_Column : 'CategoryID'
      |_Var(target).CategoryID
```

<span data-ttu-id="21a20-180">範例提供者產生的存放區命令為下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="21a20-180">The store command that the sample provider produces is the following SQL statement:</span></span>

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a><span data-ttu-id="21a20-181">產生更新 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="21a20-181">Generating an Update SQL Command</span></span>

<span data-ttu-id="21a20-182">如果有提供 DbUpdateCommandTree，產生的更新命令會根據下列範本：</span><span class="sxs-lookup"><span data-stu-id="21a20-182">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="21a20-183">只有在未指定 set 子句的情況之下，set 子句才會有假的 set 子句（"@i = 0"）。</span><span class="sxs-lookup"><span data-stu-id="21a20-183">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="21a20-184">這是為了確保任何存放區計算的資料行都會重新計算。</span><span class="sxs-lookup"><span data-stu-id="21a20-184">This is to ensure that any store-computed columns are recomputed.</span></span>

<span data-ttu-id="21a20-185">只有當 Returning 屬性不是 null 時，才會產生 select 陳述式來傳回 Returning 屬性中指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="21a20-185">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>

<span data-ttu-id="21a20-186">下列範例會使用範例提供者所隨附的模型來產生更新命令。</span><span class="sxs-lookup"><span data-stu-id="21a20-186">The following example uses the model that is included with the sample provider to generate an update command.</span></span>

<span data-ttu-id="21a20-187">下列使用者程式碼會更新分類：</span><span class="sxs-lookup"><span data-stu-id="21a20-187">The following user code updates a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="21a20-188">此使用者程式碼會產生傳遞給提供者的下列命令樹：</span><span class="sxs-lookup"><span data-stu-id="21a20-188">This user code produces the following command tree, which is passed to the provider:</span></span>

```output
DbUpdateCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
|   |_Property
|   | |_Var(target).CategoryName
|   |_Value
|     |_'New test name'
|_Predicate
| |_
|   |_Var(target).CategoryID
|   |_=
|   |_10
|_Returning
```

<span data-ttu-id="21a20-189">範例提供者會產生下列存放區命令：</span><span class="sxs-lookup"><span data-stu-id="21a20-189">The sample provider produces the following store command:</span></span>

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="21a20-190">產生刪除 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="21a20-190">Generating a Delete SQL Command</span></span>

<span data-ttu-id="21a20-191">如果有提供 DbDeleteCommandTree，產生的 DELETE 命令會根據下列範本：</span><span class="sxs-lookup"><span data-stu-id="21a20-191">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

<span data-ttu-id="21a20-192">下列範例會使用範例提供者所隨附的模型來產生刪除命令。</span><span class="sxs-lookup"><span data-stu-id="21a20-192">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>

<span data-ttu-id="21a20-193">下列使用者程式碼會刪除分類：</span><span class="sxs-lookup"><span data-stu-id="21a20-193">The following user code deletes a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="21a20-194">此使用者程式碼會產生傳遞給提供者的下列命令樹。</span><span class="sxs-lookup"><span data-stu-id="21a20-194">This user code produces the following command tree, which is passed to the provider.</span></span>

```output
DbDeleteCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_Predicate
  |_
    |_Var(target).CategoryID
    |_=
    |_10
```

<span data-ttu-id="21a20-195">下列存放區命令是由範例提供者所產生：</span><span class="sxs-lookup"><span data-stu-id="21a20-195">The following store command is produced by the sample provider:</span></span>

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a><span data-ttu-id="21a20-196">請參閱</span><span class="sxs-lookup"><span data-stu-id="21a20-196">See also</span></span>

- [<span data-ttu-id="21a20-197">撰寫 Entity Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="21a20-197">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
