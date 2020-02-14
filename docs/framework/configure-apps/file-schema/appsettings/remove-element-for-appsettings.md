---
title: <remove> 的 <appSettings> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215480"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="c09ae-102">\<移除 \<appSettings 的 > 元素 ></span><span class="sxs-lookup"><span data-stu-id="c09ae-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="c09ae-103">移除自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="c09ae-103">Removes custom application settings.</span></span>

<span data-ttu-id="c09ae-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c09ae-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c09ae-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="c09ae-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="c09ae-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="c09ae-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c09ae-107">語法</span><span class="sxs-lookup"><span data-stu-id="c09ae-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="c09ae-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c09ae-108">Attribute</span></span>

|         | <span data-ttu-id="c09ae-109">描述</span><span class="sxs-lookup"><span data-stu-id="c09ae-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="c09ae-110">**key**</span><span class="sxs-lookup"><span data-stu-id="c09ae-110">**key**</span></span> | <span data-ttu-id="c09ae-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c09ae-111">Required attribute.</span></span><br><br><span data-ttu-id="c09ae-112">指定要移除之索引鍵的名稱。</span><span class="sxs-lookup"><span data-stu-id="c09ae-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="c09ae-113">父元素</span><span class="sxs-lookup"><span data-stu-id="c09ae-113">Parent element</span></span>

|     | <span data-ttu-id="c09ae-114">描述</span><span class="sxs-lookup"><span data-stu-id="c09ae-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c09ae-115"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="c09ae-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="c09ae-116">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="c09ae-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c09ae-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c09ae-117">Child elements</span></span>

<span data-ttu-id="c09ae-118">無</span><span class="sxs-lookup"><span data-stu-id="c09ae-118">None</span></span>

## <a name="example"></a><span data-ttu-id="c09ae-119">範例</span><span class="sxs-lookup"><span data-stu-id="c09ae-119">Example</span></span>

<span data-ttu-id="c09ae-120">下列範例顯示如何移除 `ApplicationName`的自訂設定：</span><span class="sxs-lookup"><span data-stu-id="c09ae-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="c09ae-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c09ae-121">See also</span></span>

- [<span data-ttu-id="c09ae-122">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="c09ae-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
