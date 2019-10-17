---
title: < （小於）（Entity SQL）
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: fb3f4a1c6bc0df6af3c27836f7b53b2701776366
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319686"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="aae46-102">\< (小於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="aae46-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="aae46-103">比較兩個運算式來判斷左運算式的值是否小於右運算式。</span><span class="sxs-lookup"><span data-stu-id="aae46-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aae46-104">語法</span><span class="sxs-lookup"><span data-stu-id="aae46-104">Syntax</span></span>  
  
```sql  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="aae46-105">引數</span><span class="sxs-lookup"><span data-stu-id="aae46-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="aae46-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="aae46-106">Any valid expression.</span></span> <span data-ttu-id="aae46-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="aae46-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="aae46-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="aae46-108">Result Types</span></span>  
 <span data-ttu-id="aae46-109">如果左運算式的值小於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="aae46-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aae46-110">範例</span><span class="sxs-lookup"><span data-stu-id="aae46-110">Example</span></span>  
 <span data-ttu-id="aae46-111">下列 Entity SQL 查詢使用 < 比較運算子來比較兩個運算式，以判斷左運算式的值是否小於右運算式。</span><span class="sxs-lookup"><span data-stu-id="aae46-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="aae46-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="aae46-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="aae46-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="aae46-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="aae46-114">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="aae46-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="aae46-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="aae46-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="aae46-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="aae46-116">See also</span></span>

- [<span data-ttu-id="aae46-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="aae46-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
