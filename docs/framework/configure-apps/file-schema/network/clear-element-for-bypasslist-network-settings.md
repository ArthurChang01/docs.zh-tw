---
title: bypasslist 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 2ad6b16370f600299439d2e810dfefa1b5fa3c06
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087535"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="43b6b-102">\<清除 bypasslist 的 > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="43b6b-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="43b6b-103">清除 proxy 略過清單。</span><span class="sxs-lookup"><span data-stu-id="43b6b-103">Clears the proxy bypass list.</span></span>  
  
<span data-ttu-id="43b6b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="43b6b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43b6b-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="43b6b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="43b6b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="43b6b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="43b6b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="43b6b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>\
<span data-ttu-id="43b6b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="43b6b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="43b6b-109">語法</span><span class="sxs-lookup"><span data-stu-id="43b6b-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43b6b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="43b6b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="43b6b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="43b6b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43b6b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="43b6b-112">Attributes</span></span>  
 <span data-ttu-id="43b6b-113">無。</span><span class="sxs-lookup"><span data-stu-id="43b6b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43b6b-114">子項目</span><span class="sxs-lookup"><span data-stu-id="43b6b-114">Child Elements</span></span>  
 <span data-ttu-id="43b6b-115">無。</span><span class="sxs-lookup"><span data-stu-id="43b6b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43b6b-116">父項目</span><span class="sxs-lookup"><span data-stu-id="43b6b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="43b6b-117">**目**</span><span class="sxs-lookup"><span data-stu-id="43b6b-117">**Element**</span></span>|<span data-ttu-id="43b6b-118">**說明**</span><span class="sxs-lookup"><span data-stu-id="43b6b-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="43b6b-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="43b6b-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="43b6b-120">提供一組正則運算式，描述不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="43b6b-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43b6b-121">備註</span><span class="sxs-lookup"><span data-stu-id="43b6b-121">Remarks</span></span>  
 <span data-ttu-id="43b6b-122">`clear` 元素會清除略過清單中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="43b6b-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="43b6b-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="43b6b-123">Configuration Files</span></span>  
 <span data-ttu-id="43b6b-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="43b6b-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b6b-125">範例</span><span class="sxs-lookup"><span data-stu-id="43b6b-125">Example</span></span>  
 <span data-ttu-id="43b6b-126">下列範例會清除略過清單，然後將兩個位址新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="43b6b-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="43b6b-127">第一個會略過 contoso.com 網域中所有伺服器的 proxy;第二個會略過其 IP 位址開頭為192.168 的所有伺服器的 proxy。</span><span class="sxs-lookup"><span data-stu-id="43b6b-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="43b6b-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="43b6b-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="43b6b-129">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="43b6b-129">Network Settings Schema</span></span>](index.md)
