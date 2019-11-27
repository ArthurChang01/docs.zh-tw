---
title: ICorProfilerCallback::ClassLoadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: c9faff2d616d03d823c80fb2d9cd71d5fd5759ae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445076"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="0bec4-102">ICorProfilerCallback::ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="0bec4-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="0bec4-103">通知分析工具，正在載入類別。</span><span class="sxs-lookup"><span data-stu-id="0bec4-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bec4-104">語法</span><span class="sxs-lookup"><span data-stu-id="0bec4-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bec4-105">參數</span><span class="sxs-lookup"><span data-stu-id="0bec4-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="0bec4-106">在識別要載入的類別。</span><span class="sxs-lookup"><span data-stu-id="0bec4-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bec4-107">備註</span><span class="sxs-lookup"><span data-stu-id="0bec4-107">Remarks</span></span>  
 <span data-ttu-id="0bec4-108">在呼叫[ICorProfilerCallback：： ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)方法之前，`classId` 的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="0bec4-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bec4-109">需求</span><span class="sxs-lookup"><span data-stu-id="0bec4-109">Requirements</span></span>  
 <span data-ttu-id="0bec4-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bec4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bec4-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0bec4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0bec4-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bec4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bec4-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bec4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bec4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bec4-114">See also</span></span>

- [<span data-ttu-id="0bec4-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0bec4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
