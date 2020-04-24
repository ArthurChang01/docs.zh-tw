---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 5cdc60888cd872940afc1b03febd879bb6d87c2e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350843"
---
# <a name="-utf8output-visual-basic"></a>-utf8output （Visual Basic）
使用 UTF-8 編碼顯示編譯器輸出。  
  
## <a name="syntax"></a>語法  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 這個選項的預設值是`-utf8output-`，這表示編譯器輸出不會使用 utf-8 編碼。 指定 `-utf8output` 等同於指定 `-utf8output+`。  
  
## <a name="remarks"></a>備註  
 在某些國際設定中，編譯器輸出無法正確地顯示在主控台中。 在這種情況下`-utf8output` ，請使用，並將編譯器輸出重新導向至檔案。  
  
> [!NOTE]
> 此`-utf8output`選項無法在 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。  
  
## <a name="example"></a>範例  
 下列程式碼會`In.vb`編譯並指示編譯器使用 utf-8 編碼來顯示輸出。  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
