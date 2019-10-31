---
title: 融合全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: ff94ed23f3e39888b4f7e255feece99898f8aa74
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108274"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="a2995-102">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="a2995-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="a2995-103">本節說明融合 API 所使用的非受控全域靜態函式。</span><span class="sxs-lookup"><span data-stu-id="a2995-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2995-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="a2995-104">In This Section</span></span>  
 [<span data-ttu-id="a2995-105">ClearDownloadCache 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-105">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="a2995-106">清除已下載元件的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="a2995-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="a2995-107">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-107">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="a2995-108">比較兩個元件識別，以判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="a2995-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="a2995-109">CreateApplicationContext 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-109">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="a2995-110">僅供內部之用。</span><span class="sxs-lookup"><span data-stu-id="a2995-110">Internal only.</span></span> <span data-ttu-id="a2995-111">（此函式支援 .NET Framework 的基礎結構，但不適合直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="a2995-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="a2995-112">CreateAssemblyCache 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-112">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="a2995-113">取得代表全域組件快取之新[IAssemblyCache](iassemblycache-interface.md)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="a2995-113">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="a2995-114">CreateAssemblyEnum 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-114">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="a2995-115">取得[IAssemblyEnum](iassemblyenum-interface.md)實例的指標，表示存在於指定元件中的物件清單。</span><span class="sxs-lookup"><span data-stu-id="a2995-115">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="a2995-116">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-116">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="a2995-117">取得[IAssemblyName](iassemblyname-interface.md)實例的指標，表示具有指定名稱之元件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="a2995-117">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="a2995-118">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-118">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="a2995-119">為指定的檔案建立記錄讀取器。</span><span class="sxs-lookup"><span data-stu-id="a2995-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="a2995-120">CreateInstallReferenceEnum 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-120">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="a2995-121">取得[IInstallReferenceEnum](iinstallreferenceenum-interface.md)實例的指標，表示應用程式對指定元件的參考清單。</span><span class="sxs-lookup"><span data-stu-id="a2995-121">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="a2995-122">GetAppIdAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-122">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="a2995-123">取得[IAppIdAuthority](iappidauthority-interface.md)實例的指標，它會管理應用程式識別和參考的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a2995-123">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="a2995-124">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-124">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="a2995-125">取得位於指定檔案路徑之元件中具有指定 `IID` 之 `IUnknown` 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="a2995-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="a2995-126">GetCachePath 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-126">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="a2995-127">使用指定的旗標，取得快取元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="a2995-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="a2995-128">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-128">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="a2995-129">抓取應用程式歷程記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="a2995-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="a2995-130">GetIdentityAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-130">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="a2995-131">取得[IIdentityAuthority](iidentityauthority-interface.md)實例的指標，它會管理程式碼物件的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a2995-131">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="a2995-132">IsFrameworkAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-132">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="a2995-133">取得值，指出指定的元件是否為 managed。</span><span class="sxs-lookup"><span data-stu-id="a2995-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="a2995-134">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-134">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="a2995-135">刪除 common language runtime 下載快取。</span><span class="sxs-lookup"><span data-stu-id="a2995-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="a2995-136">PreBindAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="a2995-136">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="a2995-137">取得元件的後置原則顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a2995-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2995-138">相關章節</span><span class="sxs-lookup"><span data-stu-id="a2995-138">Related Sections</span></span>  
 [<span data-ttu-id="a2995-139">融合介面</span><span class="sxs-lookup"><span data-stu-id="a2995-139">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="a2995-140">融合列舉</span><span class="sxs-lookup"><span data-stu-id="a2995-140">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="a2995-141">融合結構</span><span class="sxs-lookup"><span data-stu-id="a2995-141">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="a2995-142">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="a2995-142">Global Assembly Cache</span></span>](../../app-domains/gac.md)
