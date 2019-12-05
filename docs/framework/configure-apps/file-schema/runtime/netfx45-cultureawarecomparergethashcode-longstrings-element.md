---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802120"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a>\<NetFx45_CultureAwareComparerGetHashCode_LongStrings > 元素

指定執行階段是否使用固定的記憶體數量計算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的雜湊碼。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<** NetFx45_CultureAwareComparerGetHashCode_LongStrings >  

## <a name="syntax"></a>語法

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a>屬性和元素

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br /> 指定通用語言執行平台是否會在計算雜湊碼時配置固定數量的記憶體。|

## <a name="enabled-attribute"></a>啟用屬性

|{2&gt;值&lt;2}|描述|
|-----------|-----------------|
|0|通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法配置可變的記憶體數量來計算雜湊碼。 這是預設設定。|
|1|通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法配置固定的記憶體數量來計算雜湊碼。|

### <a name="child-elements"></a>子項目

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關執行階段初始化選項的資訊。|

## <a name="remarks"></a>備註

根據預設，通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法配置可變的記憶體數量，因此，當方法嘗試計算長度超過數百萬個字元的超大型字串雜湊碼時，就可能擲回 <xref:System.ArgumentException> 。 藉由將這個項目加入至應用程式組態檔，並將其 `enabled` 屬性設定為 "1"，就可以指定 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法使用替代演算法配置固定的記憶體數量來計算雜湊碼。

> [!IMPORTANT]
> Windows 8 和更新版本中不會使用 `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` 元素。

## <a name="see-also"></a>請參閱

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
