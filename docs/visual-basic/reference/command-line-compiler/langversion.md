---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 72a5638a5c5364381ffd68604b0d44830d53f365
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344204"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.  
  
## <a name="syntax"></a>語法  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>引數  
 `version`  
 必要項。 The language version to be used during the compilation. Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` and `latest`.

 Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.

 You can see the list of all possible values by specifying `-langversion:?` on the command line.  
  
## <a name="remarks"></a>備註  
 The `-langversion` option specifies what syntax the compiler accepts. For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.  
  
 You can use this option when you develop applications that target different versions of the .NET Framework. For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.  
  
 You can set `-langversion` directly only by using the command line. 如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](/visualstudio/ide/visual-studio-multi-targeting-overview)。  
  
## <a name="example"></a>範例  
 The following code compiles `sample.vb` for Visual Basic 9.0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [以特定的 .NET Framework 版本為目標](/visualstudio/ide/visual-studio-multi-targeting-overview)
