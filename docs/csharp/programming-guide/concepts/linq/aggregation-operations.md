---
title: 彙總作業 (C#)
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: ea32becbb7ad0d3944eaea7b1b5448342ed438a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347552"
---
# <a name="aggregation-operations-c"></a>彙總作業 (C#)
彙總運算會計算值集合中的單一值。 彙總運算的一個範例是，當您使用一個月中每天的溫度值來計算每天平均溫度時。  
  
 下圖顯示一系列數字之三個不同彙總作業的結果。 第一項作業會加總這些數字。 第二個作業會傳回序列中的最大值。  
  
 ![顯示 LINQ 彙總作業的圖例。](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 下節列出執行彙總作業的標準查詢運算子方法。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|相關資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Aggregate|對集合的值執行自訂彙總運算。|不適用。|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Average|計算值集合的平均值。|不適用。|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Count|計算集合中的項目，選擇性僅計算滿足述詞函式的項目。|不適用。|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|計算大型集合中的項目，選擇性僅計算滿足述詞函式的項目。|不適用。|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|最大值|決定集合中的最大值。|不適用。|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|最小值|決定集合中的最小值。|不適用。|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Sum|計算集合中值的總和。|不適用。|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)
- [如何計算 CSV 文字檔 （LINQ） （C#） 中的列值](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [如何查詢目錄樹 （LINQ） （C#） 中的最大檔或檔](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [如何查詢一組資料夾 （LINQ） （C#） 中的位元組總數](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
