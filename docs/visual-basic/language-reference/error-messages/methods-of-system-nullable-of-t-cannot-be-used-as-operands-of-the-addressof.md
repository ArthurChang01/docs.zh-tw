---
title: "'System.Nullable(Of T)' 的方法不可以當做 'AddressOf' 運算子的運算元使用。"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 54d66a60d20a6add4c2b4a160f87b58b5a1d00e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817262"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>'System.Nullable(Of T)' 的方法不可以當做 'AddressOf' 運算子的運算元使用。
陳述式會使用`AddressOf`運算子和運算元表示的程序<xref:System.Nullable%601>結構。  
  
 **錯誤 ID:** BC32126  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   取代中的程序名稱`AddressOf`子句和運算元，不是成員<xref:System.Nullable%601>。  
  
-   撰寫的類別，包裝的方法<xref:System.Nullable%601>您想要使用。 在下列範例中，`NullableWrapper`類別會定義名為的新方法`GetValueOrDefault`。 因為這個新的方法不是隸屬<xref:System.Nullable%601>，它可以套用至`nullInstance`，可為 null 的類型，以形成的引數的執行個體`AddressOf`。  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Nullable%601>
- [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
