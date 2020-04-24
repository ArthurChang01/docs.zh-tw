---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005501"
---
# <a name="-main"></a>-main
指定包含 `Sub Main` 程序的類別或模組。  
  
## <a name="syntax"></a>語法  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a>引數  
 `location`  
 必要。 類別或模組的名稱，其中包含程式啟動`Sub Main`時要呼叫的程式。 此格式可能為 **-main： module**或 **-main： namespace. 模組**。  
  
## <a name="remarks"></a>備註  
 當您建立可執行檔或 Windows 可執行程式時，請使用此選項。 如果省略 **-main**選項，編譯器會搜尋所有公用類別和模組中`Sub Main`的有效共用。  
  
 如需程式各種形式的`Main`討論，請參閱[Visual Basic 中的主要](../../../visual-basic/programming-guide/program-structure/main-procedure.md)程式。  
  
 當`location`是繼承自<xref:System.Windows.Forms.Form>的類別時，編譯器會提供啟動應用`Main`程式的預設程式（如果該類別沒有`Main`程式）。 這可讓您在開發環境中建立的命令列編譯器代碼。  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>在 Visual Studio 整合式開發環境中設定-main  
  
1. 在 **方案總管**中選取專案。 按一下 [專案]**** 功能表上的 [屬性]****。  
  
2. 按一下 [應用程式] **** 索引標籤。  
  
3. 請確定未核取 [**啟用應用程式架構**] 核取方塊。  
  
4. 修改 [**啟始物件**] 方塊中的值。  
  
## <a name="example"></a>範例  
 下列程式碼會`T2.vb`編譯`T3.vb`和，並指定`Sub Main`要在`Test2`類別中找到該程式。  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Visual Basic 中的 Main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
