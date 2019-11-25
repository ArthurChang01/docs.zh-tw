---
title: 如何：宣告混合存取層級的屬性
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349689"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>如何：宣告混合存取層級的屬性 (Visual Basic)
If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement. You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.  
  
 For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>To declare a property with mixed access levels  
  
1. Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.  
  
2. Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).  
  
3. Do not specify an access level on the other property procedure. It assumes the access level declared in the `Property` statement. You can restrict access on only one of the property procedures.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access. A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
