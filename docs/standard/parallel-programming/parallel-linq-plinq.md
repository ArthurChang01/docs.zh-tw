---
title: 平行 LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
ms.openlocfilehash: 1ea880c6403a5fc8b26ba67fe21dfce79c4683db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140032"
---
# <a name="parallel-linq-plinq"></a>平行 LINQ (PLINQ)
Parallel LINQ (PLINQ) 是平行實作的 LINQ to Objects。 PLINQ 實作了一組完整的 LINQ 標準查詢運算子來作為 <xref:System.Linq> 命名空間的擴充方法，並具有其他運算子可供平行作業使用。 PLINQ 結合了 LINQ 語法簡單易懂的特性以及平行程式設計的威力。 和以工作平行程式庫為目標的程式碼一樣，PLINQ 查詢會根據主機電腦的能力來以並行程度縮放。  
  
 在許多情況下，PLINQ 可以更有效率地使用主機電腦上的所有可用核心，來大幅增加 LINQ to Objects 查詢的速度。 提升效能可為桌面帶來高效能的運算能力。  
  
## <a name="in-this-section"></a>本節內容  
 [PLINQ 簡介](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [PLINQ 中的順序保留](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [PLINQ 中的合併選項](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [如何：建立並執行簡單的 PLINQ 查詢](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [如何：控制 PLINQ 查詢中的順序](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [如何：結合平行和循序 LINQ 查詢](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [如何：處理 PLINQ 查詢中的例外狀況](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [如何：取消 PLINQ 查詢](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [如何：撰寫自訂 PLINQ 彙總函式](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [操作說明：在 PLINQ 中指定執行模式](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [操作說明：在 PLINQ 中指定合併選項](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [操作說明：使用 PLINQ 逐一查看檔案目錄](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [如何：測量 PLINQ 查詢效能](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [PLINQ 資料範例](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq.ParallelEnumerable>
- [並行程式設計](../../../docs/standard/parallel-programming/index.md)
- [Language-Integrated Query (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md)  
- [Language-Integrated Query (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md)  
