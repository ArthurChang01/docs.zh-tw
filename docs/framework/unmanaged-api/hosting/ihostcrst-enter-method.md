---
title: IHostCrst::Enter 方法
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
ms.openlocfilehash: 757fb996b268892818a54a3f80a54edfd89c7630
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124435"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="156c8-102">IHostCrst::Enter 方法</span><span class="sxs-lookup"><span data-stu-id="156c8-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="156c8-103">輸入目前[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)實例所代表的重要區段。</span><span class="sxs-lookup"><span data-stu-id="156c8-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="156c8-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="156c8-105">參數</span><span class="sxs-lookup"><span data-stu-id="156c8-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="156c8-106">在其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，指出當作業封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="156c8-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="156c8-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="156c8-107">Return Value</span></span>  
  
|<span data-ttu-id="156c8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="156c8-108">HRESULT</span></span>|<span data-ttu-id="156c8-109">描述</span><span class="sxs-lookup"><span data-stu-id="156c8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="156c8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="156c8-110">S_OK</span></span>|<span data-ttu-id="156c8-111">已成功傳回 `Enter`。</span><span class="sxs-lookup"><span data-stu-id="156c8-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="156c8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="156c8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="156c8-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="156c8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="156c8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="156c8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="156c8-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="156c8-115">The call timed out.</span></span>|  
|<span data-ttu-id="156c8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="156c8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="156c8-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="156c8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="156c8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="156c8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="156c8-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="156c8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="156c8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="156c8-120">E_FAIL</span></span>|<span data-ttu-id="156c8-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="156c8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="156c8-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="156c8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="156c8-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="156c8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="156c8-124">備註</span><span class="sxs-lookup"><span data-stu-id="156c8-124">Remarks</span></span>  
 <span data-ttu-id="156c8-125">`Enter` 鏡像 Win32 `EnterCriticalSection` 函數。</span><span class="sxs-lookup"><span data-stu-id="156c8-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="156c8-126">在輸入重要區段之前，這個方法不會傳回。</span><span class="sxs-lookup"><span data-stu-id="156c8-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="156c8-127">需求</span><span class="sxs-lookup"><span data-stu-id="156c8-127">Requirements</span></span>  
 <span data-ttu-id="156c8-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="156c8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="156c8-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="156c8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="156c8-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="156c8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="156c8-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="156c8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156c8-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="156c8-132">See also</span></span>

- [<span data-ttu-id="156c8-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="156c8-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="156c8-134">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="156c8-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="156c8-135">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="156c8-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
