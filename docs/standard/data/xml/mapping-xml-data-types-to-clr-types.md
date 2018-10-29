---
title: 將 XML 資料型別對應至 CLR 型別
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: cabdfcad-f359-479b-b71c-8b2fad42ca49
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a88d5bf99e2d9bb6465413cb5419058014d113a1
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839018"
---
# <a name="mapping-xml-data-types-to-clr-types"></a><span data-ttu-id="92690-102">將 XML 資料型別對應至 CLR 型別</span><span class="sxs-lookup"><span data-stu-id="92690-102">Mapping XML Data Types to CLR Types</span></span>

<span data-ttu-id="92690-103">下表說明 XML 資料型別及 Common Language Runtime (CLR) 型別之間的預設對應。</span><span class="sxs-lookup"><span data-stu-id="92690-103">The following table describes the default mapping between the XML data types and the common language runtime (CLR) types.</span></span>
  
> [!NOTE]
> <span data-ttu-id="92690-104">`xs` 和 `xdt` 前置詞分別對應至 <https://www.w3.org/2001/XMLSchema> 和 <https://www.w3.org/2003/05/xpath-datatypes> 命名空間 URI。</span><span class="sxs-lookup"><span data-stu-id="92690-104">The `xs` and the `xdt` prefixes are mapped to the <https://www.w3.org/2001/XMLSchema> and the <https://www.w3.org/2003/05/xpath-datatypes> namespace URIs respectively.</span></span>
  
|<span data-ttu-id="92690-105">XML 型別</span><span class="sxs-lookup"><span data-stu-id="92690-105">XML Type</span></span>|<span data-ttu-id="92690-106">CLR 型別</span><span class="sxs-lookup"><span data-stu-id="92690-106">CLR Type</span></span>|  
|--------------|--------------|  
|`xs:anyURI`|<xref:System.Uri>|  
|`xs:base64Binary`|`Byte[]`|  
|`xs:boolean`|<xref:System.Boolean>|  
|`xs:byte`|<xref:System.SByte>|  
|`xs:date`|<xref:System.DateTime>|  
|`xs:dateTime`|<xref:System.DateTime>|  
|`xs:decimal`|<xref:System.Decimal>|  
|`xs:double`|<xref:System.Double>|  
|`xs:duration`|<xref:System.TimeSpan>|  
|`xs:ENTITIES`|`String[]`|  
|`xs:ENTITY`|<xref:System.String>|  
|`xs:float`|<xref:System.Single>|  
|`xs:gDay`|<xref:System.DateTime>|  
|`xs:gMonthDay`|<xref:System.DateTime>|  
|`xs:gYear`|<xref:System.DateTime>|  
|`xs:gYearMonth`|<xref:System.DateTime>|  
|`xs:hexBinary`|`Byte[]`|  
|`xs:ID`|<xref:System.String>|  
|`xs:IDREF`|<xref:System.String>|  
|`xs:IDREFS`|`String[]`|  
|`xs:int`|<xref:System.Int32>|  
|`xs:integer`|<xref:System.Decimal>|  
|`xs:language`|<xref:System.String>|  
|`xs:long`|<xref:System.Int64>|  
|`xs:gMmonth`|<xref:System.DateTime>|  
|`xs:Name`|<xref:System.String>|  
|`xs:NCName`|<xref:System.String>|  
|`xs:negativeInteger`|<xref:System.Decimal>|  
|`xs:NMTOKEN`|<xref:System.String>|  
|`xs:NMTOKENS`|`String[]`|  
|`xs:nonNegativeInteger`|<xref:System.Decimal>|  
|`xs:nonPositiveInteger`|<xref:System.Decimal>|  
|`xs:normalizedString`|<xref:System.String>|  
|`xs:NOTATION`|<xref:System.Xml.XmlQualifiedName>|  
|`xs:positiveInteger`|<xref:System.Decimal>|  
|`xs:QName`|<xref:System.Xml.XmlQualifiedName>|  
|`xs:short`|<xref:System.Int16>|  
|`xs:string`|<xref:System.String>|  
|`xs:time`|<xref:System.DateTime>|  
|`xs:token`|<xref:System.String>|  
|`xs:unsignedByte`|<xref:System.Byte>|  
|`xs:unsignedInt`|<xref:System.UInt32>|  
|`xs:unsignedLong`|<xref:System.UInt64>|  
|`xs:unsignedShort`|<xref:System.UInt16>|  
|`xdt:dayTimeDuration`|<xref:System.TimeSpan>|  
|`xdt:yearMonthDuration`|<xref:System.TimeSpan>|  
|`xdt:untypedAtomic`|<xref:System.String>|  
|`xdt:anyAtomicType`|<xref:System.Object>|  
|`xs:anySimpleType`|<xref:System.String>|  
|<span data-ttu-id="92690-107">文件節點</span><span class="sxs-lookup"><span data-stu-id="92690-107">Document node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="92690-108">Element node</span><span class="sxs-lookup"><span data-stu-id="92690-108">Element node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="92690-109">Attribute node</span><span class="sxs-lookup"><span data-stu-id="92690-109">Attribute node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="92690-110">Namespace node</span><span class="sxs-lookup"><span data-stu-id="92690-110">Namespace node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="92690-111">Text node</span><span class="sxs-lookup"><span data-stu-id="92690-111">Text node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="92690-112">Comment node</span><span class="sxs-lookup"><span data-stu-id="92690-112">Comment node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="92690-113">Processing instruction node</span><span class="sxs-lookup"><span data-stu-id="92690-113">Processing instruction node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
  
## <a name="see-also"></a><span data-ttu-id="92690-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92690-114">See also</span></span>

- [<span data-ttu-id="92690-115">System.Xml 類別中的類型支援</span><span class="sxs-lookup"><span data-stu-id="92690-115">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
