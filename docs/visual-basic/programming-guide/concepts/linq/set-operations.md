---
title: 設定作業
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: fe9d910415f30fe672dc702f719fdefdb9c0b3d1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350622"
---
# <a name="set-operations-visual-basic"></a>Set Operations (Visual Basic)

LINQ 中的設定作業指的是產生結果集的查詢作業，而結果集是根據相同或不同集合 (集) 內是否有對等項目而定。

下節列出執行設定作業的標準查詢運算子方法。

## <a name="methods"></a>方法

|方法名稱|描述|Visual Basic Query Expression Syntax|更多資訊|
|-----------------|-----------------|------------------------------------------|----------------------|
|Distinct|移除集合中的重複值。|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|例外|傳回集差異，表示未出現在第二個集合中的某個集合中的項目。|不適用。|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|交集|傳回集交集，表示出現在這兩個集合中的項目。|不適用。|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|聯集|傳回集聯集，表示出現在兩個集合中任一集合的唯一項目。|不適用。|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a>比較設定作業

### <a name="distinct"></a>Distinct

下圖說明一連串字元的 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 方法行為。 所傳回的序列包含輸入序列中的唯一項目。

![顯示 Distinct&#40;&#41; 之行為的圖形。](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a>例外

下圖說明 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 的行為。 所傳回的序列只包含第一個輸入序列中不在第二個輸入序列中的項目。

![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")

### <a name="intersect"></a>交集

下圖說明 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 的行為。 所傳回的序列包含兩個輸入序列共有的項目。

![顯示兩種序列交集的圖形。](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a>聯集

下圖說明兩個字元序列的聯合作業。 所傳回的序列包含兩個輸入序列中的唯一項目。

![顯示兩個序列聯集的圖形。](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a>查詢運算式語法範例

The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a>請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Distinct 子句](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
