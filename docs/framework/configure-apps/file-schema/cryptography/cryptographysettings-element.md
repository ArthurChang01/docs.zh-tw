---
title: <cryptographySettings> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: ca0a9a4b37f28eb03f58de4fd9b120cb7e654e0c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088647"
---
# <a name="cryptographysettings-element"></a>\<cryptographySettings > 元素
包含密碼編譯設定。  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptographySettings >**

## <a name="syntax"></a>語法  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<cryptoNameMapping >](cryptonamemapping-element.md)|包含易記名稱的類別對應。|  
|[\<oidMap >](oidmap-element.md)|包含對類別的 asn.1 物件識別元（OID）對應。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`mscorlib`|包含 `cryptographySettings` 元素。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用\<的**cryptographySettings >** 元素來包含密碼編譯名稱對應和 OID 對應。 這個範例會設定執行時間，讓 <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> 傳回 `MyHashClass` 物件，而 `MyCryptoClass` 類別則會對應至物件識別碼1.3.36.2.1。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱

- [組態檔結構描述](../index.md)
- [密碼編譯設定結構描述](index.md)
- [密碼編譯服務](../../../../standard/security/cryptographic-services.md)
