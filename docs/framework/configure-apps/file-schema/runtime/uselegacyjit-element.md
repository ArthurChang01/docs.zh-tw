---
title: <useLegacyJit> 項目
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: 47aacb629dc234d9aeaab1ef6e6844fbbe5dbfdb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115100"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="a0167-102">\<useLegacyJit> 項目</span><span class="sxs-lookup"><span data-stu-id="a0167-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="a0167-103">決定通用語言執行平台是否針對 Just-In-Time 編譯使用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="a0167-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="a0167-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0167-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a0167-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="a0167-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a0167-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<uselegacyjit> >**</span><span class="sxs-lookup"><span data-stu-id="a0167-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0167-107">語法</span><span class="sxs-lookup"><span data-stu-id="a0167-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="a0167-108">元素名稱 `useLegacyJit` 區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a0167-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0167-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="a0167-109">Attributes and elements</span></span>

<span data-ttu-id="a0167-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a0167-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0167-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a0167-111">Attributes</span></span>  
  
| <span data-ttu-id="a0167-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a0167-112">Attribute</span></span> | <span data-ttu-id="a0167-113">描述</span><span class="sxs-lookup"><span data-stu-id="a0167-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="a0167-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a0167-114">Required attribute.</span></span><br><br><span data-ttu-id="a0167-115">指定執行時間是否使用舊版64位 JIT 編譯程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="a0167-116">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="a0167-116">enabled attribute</span></span>  
  
| <span data-ttu-id="a0167-117">值</span><span class="sxs-lookup"><span data-stu-id="a0167-117">Value</span></span> | <span data-ttu-id="a0167-118">描述</span><span class="sxs-lookup"><span data-stu-id="a0167-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="a0167-119">0</span><span class="sxs-lookup"><span data-stu-id="a0167-119">0</span></span>     | <span data-ttu-id="a0167-120">通用語言執行時間會使用 .NET Framework 4.6 和更新版本中所包含的新64位 JIT 編譯程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="a0167-121">1</span><span class="sxs-lookup"><span data-stu-id="a0167-121">1</span></span>     | <span data-ttu-id="a0167-122">通用語言執行時間會使用舊版的64位 JIT 編譯程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="a0167-123">子元素</span><span class="sxs-lookup"><span data-stu-id="a0167-123">Child elements</span></span>

<span data-ttu-id="a0167-124">None</span><span class="sxs-lookup"><span data-stu-id="a0167-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="a0167-125">父元素</span><span class="sxs-lookup"><span data-stu-id="a0167-125">Parent elements</span></span>  
  
| <span data-ttu-id="a0167-126">項目</span><span class="sxs-lookup"><span data-stu-id="a0167-126">Element</span></span>         | <span data-ttu-id="a0167-127">描述</span><span class="sxs-lookup"><span data-stu-id="a0167-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="a0167-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a0167-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="a0167-129">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="a0167-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="a0167-130">備註</span><span class="sxs-lookup"><span data-stu-id="a0167-130">Remarks</span></span>  

<span data-ttu-id="a0167-131">從 .NET Framework 4.6 開始，通用語言執行時間預設會使用新的64位編譯器來進行即時（JIT）編譯。</span><span class="sxs-lookup"><span data-stu-id="a0167-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="a0167-132">在某些情況下，這可能會與舊版64位 JIT 編譯程式所 JIT 編譯的應用程式程式碼為有所差異。</span><span class="sxs-lookup"><span data-stu-id="a0167-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="a0167-133">藉由將 `<useLegacyJit>` 元素的 `enabled` 屬性設定為 [`1`]，您可以停用新的64位 JIT 編譯程式，並改為使用舊版64位 JIT 編譯程式來編譯您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0167-134">`<useLegacyJit>` 元素只會影響64位 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="a0167-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="a0167-135">使用32位 JIT 編譯程式的編譯不受影響。</span><span class="sxs-lookup"><span data-stu-id="a0167-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="a0167-136">除了使用設定檔設定之外，您還可以透過兩種方式啟用舊版的64位 JIT 編譯程式：</span><span class="sxs-lookup"><span data-stu-id="a0167-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="a0167-137">設定環境變數</span><span class="sxs-lookup"><span data-stu-id="a0167-137">Setting an environment variable</span></span>

  <span data-ttu-id="a0167-138">將 `COMPLUS_useLegacyJit` 環境變數設定為 `0` （使用新的64位 JIT 編譯程式）或 `1` （使用較舊的64位 JIT 編譯程式）：</span><span class="sxs-lookup"><span data-stu-id="a0167-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="a0167-139">環境變數具有*全域範圍*，這表示它會影響電腦上執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="a0167-140">如果設定，應用程式佈建檔設定可以覆寫它。</span><span class="sxs-lookup"><span data-stu-id="a0167-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="a0167-141">環境變數名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a0167-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="a0167-142">新增登錄機碼</span><span class="sxs-lookup"><span data-stu-id="a0167-142">Adding a registry key</span></span>

  <span data-ttu-id="a0167-143">您可以藉由將 `REG_DWORD` 值新增至登錄中的 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 或 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 機碼，來啟用舊版64位 JIT 編譯程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="a0167-144">此值的名稱為 `useLegacyJit`。</span><span class="sxs-lookup"><span data-stu-id="a0167-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="a0167-145">如果值為0，則會使用新的編譯器。</span><span class="sxs-lookup"><span data-stu-id="a0167-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="a0167-146">如果值為1，則會啟用舊版64位 JIT 編譯程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="a0167-147">登錄值名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a0167-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="a0167-148">將值新增至 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 金鑰會影響電腦上執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="a0167-149">將值新增至 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 金鑰會影響目前使用者執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="a0167-150">如果電腦已設定多個使用者帳戶，則只有目前使用者執行的應用程式會受到影響，除非其他使用者的值也已加入登錄機碼中。</span><span class="sxs-lookup"><span data-stu-id="a0167-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="a0167-151">將 `<useLegacyJit>` 元素新增至設定檔會覆寫登錄設定（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="a0167-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0167-152">範例</span><span class="sxs-lookup"><span data-stu-id="a0167-152">Example</span></span>  

<span data-ttu-id="a0167-153">下列設定檔會使用新的64位 JIT 編譯程式來停用編譯，而改用舊版的64位 JIT 編譯程式。</span><span class="sxs-lookup"><span data-stu-id="a0167-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0167-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0167-154">See also</span></span>

- [<span data-ttu-id="a0167-155">\<執行時間 > 元素</span><span class="sxs-lookup"><span data-stu-id="a0167-155">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="a0167-156">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="a0167-156">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="a0167-157">風險降低：新的 64 位元 JIT 編譯器</span><span class="sxs-lookup"><span data-stu-id="a0167-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
