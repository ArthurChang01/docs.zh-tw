---
title: 如何：從 XML 檔案讀取物件資料
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: c997af4729a24a6b5bd5b22d0153860cff3282d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346428"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="cd925-102">如何：從 XML 檔案讀取物件資料（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="cd925-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="cd925-103">此範例會讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。</span><span class="sxs-lookup"><span data-stu-id="cd925-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd925-104">範例</span><span class="sxs-lookup"><span data-stu-id="cd925-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd925-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="cd925-105">Compiling the Code</span></span>  
 <span data-ttu-id="cd925-106">以內含序列化資料之檔案的名稱取代檔案名稱 "c:\temp\SerializationOverview.xml"。</span><span class="sxs-lookup"><span data-stu-id="cd925-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="cd925-107">如需序列化資料的詳細資訊，請參閱[如何：將物件資料寫入 XML 檔案（Visual Basic）](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="cd925-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="cd925-108">此類別必須有不具參數的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="cd925-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="cd925-109">只會還原序列化公用屬性和欄位。</span><span class="sxs-lookup"><span data-stu-id="cd925-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cd925-110">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="cd925-110">Robust Programming</span></span>  
 <span data-ttu-id="cd925-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="cd925-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cd925-112">正在序列化的類別沒有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="cd925-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="cd925-113">檔案中的資料不是來自要還原序列化之類別的資料。</span><span class="sxs-lookup"><span data-stu-id="cd925-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="cd925-114">檔案不存在 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="cd925-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cd925-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="cd925-115">.NET Framework Security</span></span>  
 <span data-ttu-id="cd925-116">永遠會驗證輸入，而且絕不會還原序列化來自未受信任來源的資料。</span><span class="sxs-lookup"><span data-stu-id="cd925-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="cd925-117">重新建立的物件會以還原序列化該物件之程式碼的權限，在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="cd925-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="cd925-118">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="cd925-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd925-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd925-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="cd925-120">如何：將物件資料寫入 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd925-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="cd925-121">序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd925-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="cd925-122">Visual Basic 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cd925-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
