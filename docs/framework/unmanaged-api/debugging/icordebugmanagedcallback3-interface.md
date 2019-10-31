---
title: ICorDebugManagedCallback3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: 8da04b0c620404e0dad8227c7a627f75507389a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128033"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="2394e-102">ICorDebugManagedCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="2394e-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="2394e-103">提供回呼方法，表示已引發啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="2394e-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2394e-104">方法</span><span class="sxs-lookup"><span data-stu-id="2394e-104">Methods</span></span>  
  
|<span data-ttu-id="2394e-105">方法</span><span class="sxs-lookup"><span data-stu-id="2394e-105">Method</span></span>|<span data-ttu-id="2394e-106">描述</span><span class="sxs-lookup"><span data-stu-id="2394e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2394e-107">CustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="2394e-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="2394e-108">表示已引發已啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="2394e-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2394e-109">備註</span><span class="sxs-lookup"><span data-stu-id="2394e-109">Remarks</span></span>  
 <span data-ttu-id="2394e-110">這個介面是[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)和[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="2394e-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2394e-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="2394e-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2394e-112">需求</span><span class="sxs-lookup"><span data-stu-id="2394e-112">Requirements</span></span>  
 <span data-ttu-id="2394e-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2394e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2394e-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2394e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2394e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2394e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2394e-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2394e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2394e-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="2394e-117">See also</span></span>

- [<span data-ttu-id="2394e-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2394e-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="2394e-119">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="2394e-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="2394e-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2394e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2394e-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="2394e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
