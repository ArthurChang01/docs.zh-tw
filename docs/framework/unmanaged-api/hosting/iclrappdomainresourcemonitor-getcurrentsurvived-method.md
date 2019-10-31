---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
ms.openlocfilehash: 62fcdb60b83c88738ebe2e39455b8eae60fb705e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126774"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="74ba8-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法</span><span class="sxs-lookup"><span data-stu-id="74ba8-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="74ba8-103">取得最後一次完整、封鎖垃圾收集以及目前應用程式域所參考的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="74ba8-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ba8-104">語法</span><span class="sxs-lookup"><span data-stu-id="74ba8-104">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74ba8-105">參數</span><span class="sxs-lookup"><span data-stu-id="74ba8-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="74ba8-106">在要求之應用程式域的識別碼。</span><span class="sxs-lookup"><span data-stu-id="74ba8-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="74ba8-107">脫銷這個應用程式域所持有的最後一次垃圾收集之後，被回收的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="74ba8-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="74ba8-108">在完整集合之後，此數位會正確且完整。</span><span class="sxs-lookup"><span data-stu-id="74ba8-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="74ba8-109">在暫時集合之後，此數位可能不完整。</span><span class="sxs-lookup"><span data-stu-id="74ba8-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="74ba8-110">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="74ba8-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="74ba8-111">脫銷從上一次垃圾收集中未被回收之位元組總數的指標。</span><span class="sxs-lookup"><span data-stu-id="74ba8-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="74ba8-112">在完整集合之後，此數位代表保留在受控堆積中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="74ba8-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="74ba8-113">在暫時集合之後，此數位代表暫時層代中存留的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="74ba8-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="74ba8-114">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="74ba8-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74ba8-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="74ba8-115">Return Value</span></span>  
 <span data-ttu-id="74ba8-116">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="74ba8-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="74ba8-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74ba8-117">HRESULT</span></span>|<span data-ttu-id="74ba8-118">描述</span><span class="sxs-lookup"><span data-stu-id="74ba8-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74ba8-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="74ba8-119">S_OK</span></span>|<span data-ttu-id="74ba8-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="74ba8-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="74ba8-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="74ba8-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="74ba8-122">應用程式域已卸載或不存在。</span><span class="sxs-lookup"><span data-stu-id="74ba8-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74ba8-123">備註</span><span class="sxs-lookup"><span data-stu-id="74ba8-123">Remarks</span></span>  
 <span data-ttu-id="74ba8-124">只有在完整的封鎖垃圾收集之後，才會更新統計資料。也就是包含所有層代的集合，而且會在收集時停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="74ba8-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="74ba8-125">例如，<xref:System.GC.Collect?displayProperty=nameWithType> 方法多載會執行完整的封鎖集合。</span><span class="sxs-lookup"><span data-stu-id="74ba8-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="74ba8-126">並行垃圾收集會在背景進行，而且不會封鎖應用程式。</span><span class="sxs-lookup"><span data-stu-id="74ba8-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="74ba8-127">`GetCurrentSurvived` 方法是 managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> 屬性的不受管理對等。</span><span class="sxs-lookup"><span data-stu-id="74ba8-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74ba8-128">需求</span><span class="sxs-lookup"><span data-stu-id="74ba8-128">Requirements</span></span>  
 <span data-ttu-id="74ba8-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74ba8-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ba8-130">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="74ba8-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="74ba8-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="74ba8-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74ba8-132">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74ba8-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ba8-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="74ba8-133">See also</span></span>

- [<span data-ttu-id="74ba8-134">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="74ba8-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="74ba8-135">應用程式定義域資源監視</span><span class="sxs-lookup"><span data-stu-id="74ba8-135">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="74ba8-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="74ba8-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="74ba8-137">裝載</span><span class="sxs-lookup"><span data-stu-id="74ba8-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
