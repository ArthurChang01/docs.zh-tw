---
title: ICorProfilerCallback::ThreadDestroyed 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
ms.openlocfilehash: 35b87b3a2c0230b26fb68af44dc1aa864a6449e0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439937"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="e8bb7-102">ICorProfilerCallback::ThreadDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="e8bb7-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="e8bb7-103">Notifies the profiler that a thread has been destroyed.</span><span class="sxs-lookup"><span data-stu-id="e8bb7-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8bb7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8bb7-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8bb7-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8bb7-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="e8bb7-106">[in] The ID of the thread that has been destroyed.</span><span class="sxs-lookup"><span data-stu-id="e8bb7-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8bb7-107">備註</span><span class="sxs-lookup"><span data-stu-id="e8bb7-107">Remarks</span></span>  
 <span data-ttu-id="e8bb7-108">The `threadId` value is no longer valid at the time of this call.</span><span class="sxs-lookup"><span data-stu-id="e8bb7-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8bb7-109">需求</span><span class="sxs-lookup"><span data-stu-id="e8bb7-109">Requirements</span></span>  
 <span data-ttu-id="e8bb7-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8bb7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8bb7-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8bb7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8bb7-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8bb7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8bb7-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8bb7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8bb7-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8bb7-114">See also</span></span>

- [<span data-ttu-id="e8bb7-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e8bb7-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e8bb7-116">ThreadCreated 方法</span><span class="sxs-lookup"><span data-stu-id="e8bb7-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
