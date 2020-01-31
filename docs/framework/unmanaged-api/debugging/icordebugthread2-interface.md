---
title: ICorDebugThread2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: fdaad46b739721ff95b712d4b6461a793ae0a480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791424"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="be821-102">ICorDebugThread2 介面</span><span class="sxs-lookup"><span data-stu-id="be821-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="be821-103">作為 ICorDebugThread 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="be821-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be821-104">方法</span><span class="sxs-lookup"><span data-stu-id="be821-104">Methods</span></span>  
  
|<span data-ttu-id="be821-105">方法</span><span class="sxs-lookup"><span data-stu-id="be821-105">Method</span></span>|<span data-ttu-id="be821-106">描述</span><span class="sxs-lookup"><span data-stu-id="be821-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be821-107">GetActiveFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="be821-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="be821-108">取得 COR_ACTIVE_FUNCTION 實例的陣列，其中包含執行緒框架中作用中函式的相關資料。</span><span class="sxs-lookup"><span data-stu-id="be821-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="be821-109">GetConnectionID 方法</span><span class="sxs-lookup"><span data-stu-id="be821-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="be821-110">取得此 `ICorDebugThread2`的連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="be821-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="be821-111">GetTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="be821-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="be821-112">取得此 `ICorDebugThread2`的工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="be821-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="be821-113">GetVolatileOSThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="be821-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="be821-114">取得此 `ICorDebugThread2`的作業系統執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="be821-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="be821-115">InterceptCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="be821-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="be821-116">允許偵錯工具攔截執行緒上目前的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="be821-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be821-117">備註</span><span class="sxs-lookup"><span data-stu-id="be821-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be821-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="be821-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be821-119">需求</span><span class="sxs-lookup"><span data-stu-id="be821-119">Requirements</span></span>  
 <span data-ttu-id="be821-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be821-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be821-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be821-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be821-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be821-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be821-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be821-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be821-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="be821-124">See also</span></span>

- [<span data-ttu-id="be821-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="be821-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
