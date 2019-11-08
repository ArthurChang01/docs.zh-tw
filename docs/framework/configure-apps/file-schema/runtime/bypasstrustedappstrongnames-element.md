---
title: <bypassTrustedAppStrongNames> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739092"
---
# <a name="bypasstrustedappstrongnames-element"></a>\<bypassTrustedAppStrongNames> 項目

指定是否要在完全信任的元件上略過強式名稱驗證，並將其載入至完全信任的 <xref:System.AppDomain>。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<bypasstrustedappstrongnames> >**

## <a name="syntax"></a>語法

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br /> 指定是否啟用避免為完全信任元件驗證強式名稱的略過功能。 啟用這項功能時，在載入元件時，不會驗證強式名稱是否正確。 預設為 `true`。|

## <a name="enabled-attribute"></a>啟用屬性

|值|描述|
|-----------|-----------------|
|`true`|當元件載入到完全信任的 <xref:System.AppDomain>時，不會驗證完全信任元件上的強式名稱簽章。 這是預設值。|
|`false`|將元件載入到完全信任的 <xref:System.AppDomain>時，會驗證完全信任元件上的強式名稱簽章。 強式名稱簽章只會檢查簽名碼正確性;它不會與另一個強式名稱進行比較，以符合相符項。|

### <a name="child-elements"></a>子項目

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|

## <a name="remarks"></a>備註

強式名稱略過功能可避免完全信任元件的強式名稱簽章驗證的額外負荷。

略過功能適用於任何以強式名稱簽署並具有下列特性的組件：

- 完全信任，沒有 <xref:System.Security.Policy.StrongName> 辨識項（例如，具有 `MyComputer` 區域辨識項）。

- 載入到完全信任的 <xref:System.AppDomain>。

- 從 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性下的位置載入。

- 不延遲簽署。

> [!NOTE]
> 若已使用登錄機碼為電腦上的所有應用程式關閉略過功能，此設定檔案設定就不會有任何作用。 如需詳細資訊，請參閱[如何：停用強式名稱略過功能](../../../../standard/assembly/disable-strong-name-bypass-feature.md)。

## <a name="example"></a>範例

下列範例顯示如何指定行為，以驗證完全信任元件上的強式名稱簽章。

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [如何：停用強式名稱略過功能](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
