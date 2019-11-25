---
title: XML 的函式轉換
ms.date: 07/20/2015
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
ms.openlocfilehash: 7e029fd562ae3f221a8aaef40f332a1e3fa896eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353430"
---
# <a name="functional-transformation-of-xml-visual-basic"></a>Functional Transformation of XML (Visual Basic)
本主題討論修改 XML 文件的純功能性轉換方法，並與程序性方法對照。  
  
## <a name="modifying-an-xml-document"></a>修改 XML 文件  
 XML 程式設計人員其中一個最常見的工做為，將 XML 從一個組織結構轉換為另一個組織結構。 XML 文件的組織結構就是文件的結構，其中包括：  
  
- 以文件表示的階層。  
  
- 項目和屬性名稱。  
  
- 項目和屬性的資料型別。  
  
 一般而言，將 XML 從一個組織結構轉換為另一個組織結構最有效的方法是，純功能性轉換的方法。 以此種方法，程式設計人員的主要工做為建立適用於整個 XML 文件 (或者一或多個嚴格定義的程式碼) 的轉換。 在論證上，功能性轉換對程式碼而言是最簡單的 (在程式設計人員熟悉方法之後)，它會產生最容易維護的程式碼，而且通常比替代方法更精簡。  
  
### <a name="xml-functional-transformational-technologies"></a>XML 功能性轉換技術  
 Microsoft 提供兩個可用於 XML 文件的功能性轉換技術：XSLT 和 LINQ to XML。 在 <xref:System.Xml.Xsl> Managed 命名空間與 MSXML 的原始 COM 實作中支援 XSLT。 雖然 XSLT 是強大的管理 XML 文件技術，但是它需要特殊領域的專業知識，也就是 XSLT 語言及其支援的 API。  
  
 LINQ to XML 在 C# 或 Visual Basic 程式碼中，提供以明確而且強大的方式撰寫純功能性轉換之程式碼所需的工具。 例如，LINQ to XML 文件中的許多範例都使用純功能性方法。 Also, in the [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial, we use LINQ to XML in a functional approach to manipulate information in a Microsoft Word document.  
  
 For a more complete comparison of LINQ to XML with other Microsoft XML technologies, see [LINQ to XML vs. Other XML Technologies](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 當來源文件具有不規則的結構時，XSLT 是文件中心轉換的建議工具。 不過，LINQ to XML 也可以執行文件中心的轉換。 For more information, see [How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>請參閱

- [Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [LINQ to XML vs. Other XML Technologies](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
