---
title: <configuration> 的 <configSections> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6024144b6f12df22369366f04c3cbad02c5011d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119022"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="4a77d-102">\<設定的 \<configSections > 元素 ></span><span class="sxs-lookup"><span data-stu-id="4a77d-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="4a77d-103">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="4a77d-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="4a77d-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4a77d-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="4a77d-105">&nbsp;&nbsp; **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="4a77d-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="4a77d-106">屬性</span><span class="sxs-lookup"><span data-stu-id="4a77d-106">Attributes</span></span>

<span data-ttu-id="4a77d-107">None</span><span class="sxs-lookup"><span data-stu-id="4a77d-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="4a77d-108">父項目</span><span class="sxs-lookup"><span data-stu-id="4a77d-108">Parent element</span></span>

|     | <span data-ttu-id="4a77d-109">描述</span><span class="sxs-lookup"><span data-stu-id="4a77d-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4a77d-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="4a77d-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="4a77d-111">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4a77d-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4a77d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4a77d-112">Child elements</span></span>

|     | <span data-ttu-id="4a77d-113">描述</span><span class="sxs-lookup"><span data-stu-id="4a77d-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4a77d-114"> **\<區段 >** </span><span class="sxs-lookup"><span data-stu-id="4a77d-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="4a77d-115">包含設定區段宣告。</span><span class="sxs-lookup"><span data-stu-id="4a77d-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="4a77d-116"> **\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="4a77d-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="4a77d-117">定義設定區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4a77d-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="4a77d-118"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="4a77d-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="4a77d-119">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="4a77d-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="4a77d-120"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="4a77d-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="4a77d-121">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="4a77d-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4a77d-122">備註</span><span class="sxs-lookup"><span data-stu-id="4a77d-122">Remarks</span></span>

<span data-ttu-id="4a77d-123">如果這個元素是在設定檔中，它必須是 **\<設定 >** 元素的第一個子專案。</span><span class="sxs-lookup"><span data-stu-id="4a77d-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="4a77d-124">範例</span><span class="sxs-lookup"><span data-stu-id="4a77d-124">Example</span></span>

<span data-ttu-id="4a77d-125">下列範例顯示如何定義設定區段，並定義該區段的設定：</span><span class="sxs-lookup"><span data-stu-id="4a77d-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="4a77d-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="4a77d-126">Configuration file</span></span>

<span data-ttu-id="4a77d-127">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="4a77d-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a77d-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="4a77d-128">See also</span></span>

- [<span data-ttu-id="4a77d-129">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="4a77d-129">Configuration file schema for the .NET Framework</span></span>](index.md)
