---
title: "'Class' 陳述式之後必須搭配相對應的 'End Class'"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 559595e9902ec2f0a19fd6b13e2c89fa1c2b52d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602408"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a>'Class' 陳述式之後必須搭配相對應的 'End Class'
`Class` 用來起始`Class`區塊，因此它只能出現在區塊中，搭配相對應的開頭`End Class`結束區塊的陳述式。 您有多餘`Class`陳述式，或您有未結束您`Class`含有區塊`End Class`。  
  
 **錯誤 ID:** BC30481  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 找到並移除不必要的 `Class` 陳述式。  
  
- 結束`Class`搭配相對應的區塊`End Class`。  
  
## <a name="see-also"></a>另請參閱

- [結束\<關鍵字 > 陳述式](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)
