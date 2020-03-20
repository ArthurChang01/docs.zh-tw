---
title: 將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150840"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束
在 XML 架構定義語言 （XSD） 架構中，**唯一**元素指定元素或屬性的唯一性約束。 在將 XML 結構描述轉譯到關聯式結構描述的處理序中，會將 XML 結構描述內項目或屬性上指定的唯一的條件約束 (Constraint)，對應到所產生的對應 <xref:System.Data.DataTable> 內 <xref:System.Data.DataSet> 的唯一的條件約束。  
  
 下表概述了可以在**唯一**元素中指定的**msdata**屬性。  
  
|屬性名稱|描述|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|如果指定這個屬性，則它的值會被當成條件約束名稱使用。 否則，**名稱**屬性提供約束名稱的值。|  
|**msdata:PrimaryKey**|如果`PrimaryKey="true"`存在**唯**一元素中，則使用**IsPrimaryKey**屬性設置為**true**時將創建唯一約束。|  
  
 下面的示例顯示了使用**唯**一元素指定唯一性約束的 XML 架構。  
  
```xml  
<xs:schema id="SampleDataSet"
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 架構中**的唯一**元素指定，對於文檔實例中的所有**客戶**元素 **，CustomerID**子項目的值必須是唯一的。 在構建**DataSet**時，映射過程讀取此架構並生成下表：  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 映射過程還會在**CustomerID**列上創建唯一的約束，如下**DataSet**所示。 (為了便於了解，此處僅顯示相關屬性)。  
  
```text  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID
      IsPrimaryKey: False  
```  
  
 在生成的**DataSet**中 **，IsPrimaryKey**屬性設置為唯一約束的**False。** 列上**的唯**一屬性指示**CustomerID**列值必須是唯一的（但它們可以是空引用，由列的**AllowDBNull**屬性指定）。  
  
 如果修改架構並將可選**msdata：主鍵**屬性值設置為**True，** 則在表上創建唯一約束。 **AllowDBNull**列屬性設置為**False**，約束的**IsPrimaryKey**屬性設置為**True，** 從而使**CustomerID**列成為主鍵列。  
  
 您可以在 XML 結構描述中，將唯一的條件約束指定給合併的項目或屬性。 下面的示例演示如何通過在架構中添加另一個**xs：field**元素來指定**客戶 ID** **和公司名稱**值的組合在任何情況下對所有**客戶**都是唯一的。  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 這是在生成的**DataSet**中創建的約束。  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>另請參閱

- [將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
