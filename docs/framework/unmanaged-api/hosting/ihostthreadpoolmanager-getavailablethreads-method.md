---
title: IHostThreadPoolManager::GetAvailableThreads 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
ms.openlocfilehash: 21449d9365e6260267d3c79f384f6136ce894821
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122089"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="ab6ce-102">IHostThreadPoolManager::GetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="ab6ce-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="ab6ce-103">取得執行緒集區中目前未處理工作專案的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab6ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab6ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab6ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab6ce-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="ab6ce-106">脫銷執行緒集區中目前未處理工作專案之執行緒數目的指標。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab6ce-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ab6ce-107">Return Value</span></span>  
  
|<span data-ttu-id="ab6ce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab6ce-108">HRESULT</span></span>|<span data-ttu-id="ab6ce-109">描述</span><span class="sxs-lookup"><span data-stu-id="ab6ce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ab6ce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab6ce-110">S_OK</span></span>|<span data-ttu-id="ab6ce-111">已成功傳回 `GetAvailableThreads`。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="ab6ce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ab6ce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ab6ce-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ab6ce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ab6ce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ab6ce-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-115">The call timed out.</span></span>|  
|<span data-ttu-id="ab6ce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ab6ce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ab6ce-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ab6ce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ab6ce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ab6ce-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ab6ce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ab6ce-120">E_FAIL</span></span>|<span data-ttu-id="ab6ce-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ab6ce-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ab6ce-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ab6ce-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ab6ce-124">E_NOTIMPL</span></span>|<span data-ttu-id="ab6ce-125">主機未提供 `GetAvailableThreads`的執行。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab6ce-126">備註</span><span class="sxs-lookup"><span data-stu-id="ab6ce-126">Remarks</span></span>  
 <span data-ttu-id="ab6ce-127">如果主機未提供 `GetAvailableThreads`的執行，它應該會傳回 E_NOTIMPL 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab6ce-128">需求</span><span class="sxs-lookup"><span data-stu-id="ab6ce-128">Requirements</span></span>  
 <span data-ttu-id="ab6ce-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab6ce-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab6ce-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ab6ce-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab6ce-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ab6ce-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab6ce-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab6ce-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6ce-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab6ce-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="ab6ce-134">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="ab6ce-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
