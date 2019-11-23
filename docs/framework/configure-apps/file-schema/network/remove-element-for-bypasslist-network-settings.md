---
title: bypasslist 的 <remove> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697899"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="1bbb4-102">\<移除 bypasslist 的 > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="1bbb4-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="1bbb4-103">從 proxy 略過清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[<span data-ttu-id="1bbb4-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="1bbb4-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="1bbb4-105">&nbsp;&nbsp;[ **\<system.web >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1bbb4-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="1bbb4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1bbb4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="1bbb4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1bbb4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="1bbb4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="1bbb4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="1bbb4-109">語法</span><span class="sxs-lookup"><span data-stu-id="1bbb4-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1bbb4-110">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="1bbb4-110">Attributes and Elements</span></span>

<span data-ttu-id="1bbb4-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1bbb4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1bbb4-112">Attributes</span></span>

|<span data-ttu-id="1bbb4-113">**屬性**</span><span class="sxs-lookup"><span data-stu-id="1bbb4-113">**Attribute**</span></span>|<span data-ttu-id="1bbb4-114">**說明**</span><span class="sxs-lookup"><span data-stu-id="1bbb4-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="1bbb4-115">描述 IP 位址或 DNS 名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1bbb4-116">子元素</span><span class="sxs-lookup"><span data-stu-id="1bbb4-116">Child Elements</span></span>

<span data-ttu-id="1bbb4-117">None。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1bbb4-118">父項目</span><span class="sxs-lookup"><span data-stu-id="1bbb4-118">Parent Elements</span></span>

|<span data-ttu-id="1bbb4-119">**目**</span><span class="sxs-lookup"><span data-stu-id="1bbb4-119">**Element**</span></span>|<span data-ttu-id="1bbb4-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="1bbb4-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="1bbb4-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="1bbb4-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="1bbb4-122">提供一組正則運算式，描述不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1bbb4-123">備註</span><span class="sxs-lookup"><span data-stu-id="1bbb4-123">Remarks</span></span>

<span data-ttu-id="1bbb4-124">`remove` 元素會從略過 proxy 伺服器的地址清單中，移除描述 IP 位址或 DNS 伺服器名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="1bbb4-125">先前已在設定檔或設定階層的較高層級定義位址。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="1bbb4-126">`address` 屬性的值應該是描述一組 IP 位址或主機名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="1bbb4-127">如需正則運算式的詳細資訊，請參閱。[.NET Framework 正則運算式](../../../../standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="1bbb4-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="1bbb4-128">Configuration Files</span></span>

<span data-ttu-id="1bbb4-129">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="1bbb4-130">範例</span><span class="sxs-lookup"><span data-stu-id="1bbb4-130">Example</span></span>

<span data-ttu-id="1bbb4-131">下列範例會移除 adventure-works.com 網域的任何先前定義，然後將 contoso.com 網域新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="1bbb4-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1bbb4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bbb4-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="1bbb4-133">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1bbb4-133">Network Settings Schema</span></span>](index.md)
