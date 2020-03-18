---
title: 如何在查詢中使用 lambda 運算式 - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 92bdbf842c5c30b2f32e06f622f3e08f3c7a878f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711957"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a><span data-ttu-id="4e39a-102">如何在查詢中使用 lambda 運算式（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="4e39a-102">How to use lambda expressions in a query (C# Programming Guide)</span></span>
<span data-ttu-id="4e39a-103">您不會在查詢語法中直接使用 Lambda 運算式，而是在方法呼叫中使用它們，因此查詢運算式可以包含方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="4e39a-103">You do not use lambda expressions directly in query syntax, but you do use them in method calls, and query expressions can contain method calls.</span></span> <span data-ttu-id="4e39a-104">事實上，某些查詢作業只能以方法語法來表示。</span><span class="sxs-lookup"><span data-stu-id="4e39a-104">In fact, some query operations can only be expressed in method syntax.</span></span> <span data-ttu-id="4e39a-105">如需查詢語法與方法語法之間差異的詳細資訊，請參閱 [LINQ 中的查詢語法及方法語法](../concepts/linq/query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="4e39a-105">For more information about the difference between query syntax and method syntax, see [Query Syntax and Method Syntax in LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e39a-106">範例</span><span class="sxs-lookup"><span data-stu-id="4e39a-106">Example</span></span>  
 <span data-ttu-id="4e39a-107">下列範例示範如何透過 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 標準查詢運算子，在以方法為基礎的查詢中使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e39a-107">The following example demonstrates how to use a lambda expression in a method-based query by using the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standard query operator.</span></span> <span data-ttu-id="4e39a-108">請注意，此範例中的 <xref:System.Linq.Enumerable.Where%2A> 方法具有委派類型 <xref:System.Func%602> 的輸入參數，而且該委派會接受整數作為輸入並傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="4e39a-108">Note that the <xref:System.Linq.Enumerable.Where%2A> method in this example has an input parameter of the delegate type <xref:System.Func%602> and that delegate takes an integer as input and returns a Boolean.</span></span> <span data-ttu-id="4e39a-109">Lambda 運算式可轉換成該委派。</span><span class="sxs-lookup"><span data-stu-id="4e39a-109">The lambda expression can be converted to that delegate.</span></span> <span data-ttu-id="4e39a-110">如果這是使用 <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> 方法的 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查詢，參數類型就會是 `Expression<Func<int,bool>>`，但 Lambda 運算式看起來會完全相同。</span><span class="sxs-lookup"><span data-stu-id="4e39a-110">If this were a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query that used the <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> method, the parameter type would be an `Expression<Func<int,bool>>` but the lambda expression would look exactly the same.</span></span> <span data-ttu-id="4e39a-111">如需運算式類型的詳細資訊，請參閱 <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4e39a-111">For more information on the Expression type, see <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a><span data-ttu-id="4e39a-112">範例</span><span class="sxs-lookup"><span data-stu-id="4e39a-112">Example</span></span>  
 <span data-ttu-id="4e39a-113">下列範例示範如何在查詢運算式的方法呼叫中使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="4e39a-113">The following example demonstrates how to use a lambda expression in a method call of a query expression.</span></span> <span data-ttu-id="4e39a-114">因為無法使用查詢語法來叫用 <xref:System.Linq.Enumerable.Sum%2A> 標準查詢運算子，所以需要此 Lambda。</span><span class="sxs-lookup"><span data-stu-id="4e39a-114">The lambda is necessary because the <xref:System.Linq.Enumerable.Sum%2A> standard query operator cannot be invoked by using query syntax.</span></span>  
  
 <span data-ttu-id="4e39a-115">此查詢會先根據學生的年級 (已定義於 `GradeLevel` 列舉) 來進行分組。</span><span class="sxs-lookup"><span data-stu-id="4e39a-115">The query first groups the students according to their grade level, as defined in the `GradeLevel` enum.</span></span> <span data-ttu-id="4e39a-116">接著會針對每一組加總計算每個學生的總分數。</span><span class="sxs-lookup"><span data-stu-id="4e39a-116">Then for each group it adds the total scores for each student.</span></span> <span data-ttu-id="4e39a-117">這需要兩個 `Sum` 運算。</span><span class="sxs-lookup"><span data-stu-id="4e39a-117">This requires two `Sum` operations.</span></span> <span data-ttu-id="4e39a-118">內部的 `Sum` 會計算每個學生的總分數，而外部的 `Sum` 會不斷執行，以加總該群組中所有學生的總分數。</span><span class="sxs-lookup"><span data-stu-id="4e39a-118">The inner `Sum` calculates the total score for each student, and the outer `Sum` keeps a running, combined total for all students in the group.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4e39a-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4e39a-119">Compiling the Code</span></span>  
 <span data-ttu-id="4e39a-120">要運行此代碼，請將 該方法複製並粘貼到`StudentClass`Query 中提供[的物件集合](../../linq/query-a-collection-of-objects.md)中，並從 方法`Main`調用它。</span><span class="sxs-lookup"><span data-stu-id="4e39a-120">To run this code, copy and paste the method into the `StudentClass` that is provided in [Query a collection of objects](../../linq/query-a-collection-of-objects.md) and call it from the `Main` method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4e39a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e39a-121">See also</span></span>

- [<span data-ttu-id="4e39a-122">蘭姆達運算式</span><span class="sxs-lookup"><span data-stu-id="4e39a-122">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="4e39a-123">運算式樹狀架構 (C#)</span><span class="sxs-lookup"><span data-stu-id="4e39a-123">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
