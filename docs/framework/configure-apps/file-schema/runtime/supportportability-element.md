---
title: <supportPortability> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 63c309a8a93c1d31ed8f73a495cf5154c3590d56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115646"
---
# <a name="supportportability-element"></a>\<supportPortability > 元素
指定應用程式可以在兩個不同的 .NET Framework 實作中參考相同的組件，方法是停用將組件視為同等的預設行為 (此預設行為是基於應用程式可攜性的考量)。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp; &nbsp; &nbsp; &nbsp;[ **\<assemblyBinding**](assemblybinding-element-for-runtime.md) > \
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \<supportPortability **>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|PKT|必要屬性。<br /><br /> 以字串的形式，指定受影響元件的公開金鑰 token。|  
|enabled|選擇性屬性。<br /><br /> 指定是否應該啟用指定之 .NET Framework 元件的執行之間的可攜性支援。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|true|啟用指定 .NET Framework 元件的執行之間的可攜性支援。 這是預設值。|  
|False|停用指定之 .NET Framework 元件的執行之間的可攜性支援。 這可讓應用程式參考指定元件的多個執行。|  
  
### <a name="child-elements"></a>子項目  

無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
  
## <a name="remarks"></a>備註  

從 .NET Framework 4 開始，會自動為可使用 .NET Framework 的兩個實作為之一的應用程式提供支援，例如，.NET Framework 的執行或 Silverlight 執行的 .NET Framework。 元件系結器會將這兩個特定 .NET Framework 元件的執行視為對等。 在少數情況下，此應用程式可攜性功能會造成問題。 在這些情況下，可以使用 `<supportPortability>` 元素來停用此功能。  
  
其中一個案例是必須同時參考 .NET Framework 執行的元件，以及特定參考元件的 Silverlight 執行 .NET Framework。 例如，以 Windows Presentation Foundation （WPF）撰寫的 XAML 設計工具可能需要參考 WPF 桌上型電腦的程式設計人員的使用者介面，以及包含在 Silverlight 執行中的 WPF 子集。 根據預設，不同的參考會導致編譯器錯誤，因為組件繫結關係會將兩個組件視為對等項目。 這個元素會停用預設行為，並允許編譯成功。  
  
> [!IMPORTANT]
> 為了讓編譯器將資訊傳遞給通用語言執行平臺的元件系結邏輯，您必須使用 `/appconfig` 編譯器選項來指定 app.config 檔案的位置，此檔案包含此元素。  
  
## <a name="example"></a>範例  

下列範例可讓應用程式同時參考同時存在於兩個執行中之任何 .NET Framework 元件的 .NET Framework 實和 .NET Framework。 `/appconfig` 編譯器選項必須用來指定此 app.config 檔案的位置。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱

- [-appconfig (C# 編譯器選項)](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [.NET Framework 元件統一總覽](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
