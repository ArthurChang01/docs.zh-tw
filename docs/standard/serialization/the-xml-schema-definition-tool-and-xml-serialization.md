---
title: XML 結構描述定義工具和 XML 序列化
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: b51b9a0112893d9a7838155f4af051e7079c8cdd
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588394"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a>XML 結構描述定義工具和 XML 序列化

XML 架構定義工具（[Xml 架構定義工具（xsd.exe）](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)）會隨「Windows&reg;軟體發展工具組」（SDK）中的 .NET Framework 工具一起安裝。 該工具的設計主要有兩個目的：  
  
- 產生符合特定 XML 結構描述定義語言 (XSD) 結構描述的 C# 或 Visual Basic 類別檔。 此工具以 XML 結構描述做為引數並輸出包含各種類別的檔案，在以 <xref:System.Xml.Serialization.XmlSerializer> 序列化時，符合結構描述。 如需如何使用此工具以產生符合特定結構描述之類別的資訊，請參閱[如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)。  
  
- 從 .dll 檔或 .exe 檔產生 XML 結構描述文件。 若要檢視您所建立或已修改其中屬性之檔案集的結構描述，請將 DLL 或 EXE 當成引數傳遞至工具以產生 XML 結構描述。 如需如何使用工具從類別集產生 XML 結構描述文件的資訊，請參閱[如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)。  
  
如需使用此工具的詳細資訊，請參閱[XML 架構定義工具（xsd.exe）](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataSet>
- [XML 序列化簡介](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [XML 架構定義工具（Xsd.exe）](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [HOW TO：序列化物件](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [如何：還原序列化物件](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [如何：使用 XML 結構描述定義工具產生類別和 XML 結構描述文件](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- [XML 結構描述繫結支援](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))
