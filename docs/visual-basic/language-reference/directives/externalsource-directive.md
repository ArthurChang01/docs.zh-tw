---
title: '#ExternalSource 指示詞'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343836"
---
# <a name="externalsource-directive"></a>#ExternalSource 指示詞

表示原始程式程式碼與來源外部文字之間的對應。  
  
## <a name="syntax"></a>語法  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>組件  

 `StringLiteral`  
 外部來源的路徑。  
  
 `IntLiteral`  
 外部來源第一行的行號。  
  
 `LogicalLine`  
 外部來源中發生錯誤的行。  
  
 `#End ExternalSource`  
 終止 `#ExternalSource` 區塊。  
  
## <a name="remarks"></a>備註  

 這個指示詞僅供編譯器和偵錯工具使用。  
  
 原始程式檔可能包含外部來源指示詞，這表示原始程式檔中的特定程式程式碼與來源外部的文字之間的對應，例如 .aspx 檔案。 如果在編譯期間于指定的原始程式碼中遇到錯誤，則會將它們識別為來自外部來源。  
  
 外部來源指示詞不會影響編譯，而且無法加以嵌套。 它們僅供應用程式內部使用。  
  
## <a name="see-also"></a>另請參閱

- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
