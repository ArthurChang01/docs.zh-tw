---
title: 如何將物件資料寫入 XML 檔案（C#）
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 475e9398f20a2a4db9fb537d0b8d44f0273e980b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346440"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>如何將物件資料寫入 XML 檔案（C#）
此範例會使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將來自某個類別的物件寫入 XML 檔案。  
  
## <a name="example"></a>範例  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 正在序列化的類別必須有不具參數的公用建構函式。  
  
## <a name="robust-programming"></a>最佳化程式設計  
 以下條件可能會造成例外狀況：  
  
- 正在序列化的類別沒有公用的無參數建構函式。  
  
- 該檔案存在且為唯讀 (<xref:System.IO.IOException>)。  
  
- 路徑太長 (<xref:System.IO.PathTooLongException>)。  
  
- 磁碟已滿 (<xref:System.IO.IOException>)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果檔案不存在，此範例就會建立新的檔案。 如果應用程式需要建立檔案，該應用程式就需要資料夾的 `Create` 權限。 如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。 若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 `Read` 權限，而不授與資料夾的 `Create` 權限。  
  
## <a name="see-also"></a>請參閱

- <xref:System.IO.StreamWriter>
- [如何從 XML 檔案讀取物件資料（C#）](./how-to-read-object-data-from-an-xml-file.md)
- [序列化 (C#)](./index.md)
