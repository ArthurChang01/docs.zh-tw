---
title: '#Region 指示詞'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 4cf9b103486378d001b588aa285f590980b51bb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343785"
---
# <a name="region-directive"></a>#Region 指示詞

摺疊並隱藏 Visual Basic 檔案中的程式碼區段。  
  
## <a name="syntax"></a>語法  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`identifier_string`|必要。 做為摺疊區域標題的字串。 區域預設會摺疊。|  
|`#End Region`|終止 `#Region` 區塊。|  
  
## <a name="remarks"></a>備註  

 使用 `#Region` 指示詞來指定程式碼區段，以在使用 Visual Studio 程式碼編輯器的大綱功能時展開或摺疊。 您可以將區域放在其他區域中，或加以*嵌套*，將類似的區域群組在一起。  
  
## <a name="example"></a>範例  

 此範例使用 `#Region` 指示詞。  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>請參閱

- [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [大綱](/visualstudio/ide/outlining)
- [操作說明：摺疊和隱藏程式碼區段](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
