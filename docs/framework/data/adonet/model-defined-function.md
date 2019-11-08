---
title: 模型定義函式
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 973d7ff9f7b76650782d62dcdcab60c8cedde18f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735573"
---
# <a name="model-defined-function"></a>模型定義函式
*模型定義函式*是在概念模型中定義的函數。 模型定義函式的主體會以[Entity SQL](./ef/language-reference/entity-sql-language.md)表示，讓函數可以獨立于資料來源中支援的規則或語言來表示。  
  
 模型定義函式的定義包含下列資訊：  
  
- 函式名稱。 (必要項)  
  
- 傳回值的型別。 (選擇項)  
  
    > [!NOTE]
    > 若未指定任何傳回型別，則傳回值為 void。  
  
- 參數資訊。 (選擇項)  
  
- 定義函數主體的[Entity SQL](./ef/language-reference/entity-sql-language.md)運算式。  
  
 請注意，模型定義函式不支援輸出參數。 有此限制後才能夠撰寫模型定義函式。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。  
  
 ![顯示具有發行日期之模型的螢幕擷取畫面。](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的特定領域語言（DSL）來定義概念模型。 下列 CSDL 定義概念模型中的函式，會傳回上圖中 `Book` 執行個體發行年度以來的年份。  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
- [實體資料模型：基本資料類型](entity-data-model-primitive-data-types.md)
