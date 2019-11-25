---
title: Variable uses an Automation type not supported
ms.date: 07/20/2015
f1_keywords:
- vbrID458
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
ms.openlocfilehash: 944c0c63cd0d7ae7f9ff770fd123231464af1eaf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344834"
---
# <a name="variable-uses-an-automation-type-not-supported-in-visual-basic"></a>變數使用在 Visual Basic 中不支援的 Automation 類型

You tried to use a variable defined in a type library or object library that has a data type not supported by Visual Basic.

## <a name="to-correct-this-error"></a>更正這個錯誤

- Use a variable of a type recognized by Visual Basic.

     -或-

- If you encounter this error while using `FileGet` or `FileGetObject`, make sure the file you are trying to use was written to with `FilePut` or `FilePutObject`.

## <a name="see-also"></a>請參閱

- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
