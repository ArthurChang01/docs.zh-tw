---
title: ICorProfilerCallback::ClassLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: e0ff90f99c1127b5a4626f47514ba7099b5d48af
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866594"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="0f2d9-102">ICorProfilerCallback::ClassLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="0f2d9-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="0f2d9-103">通知 profiler，類別已完成載入。</span><span class="sxs-lookup"><span data-stu-id="0f2d9-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f2d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f2d9-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f2d9-105">參數</span><span class="sxs-lookup"><span data-stu-id="0f2d9-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="0f2d9-106">中的 \[] 識別已載入的類別。</span><span class="sxs-lookup"><span data-stu-id="0f2d9-106">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="0f2d9-107">\[in]） HRESULT，指出類別是否已成功載入。</span><span class="sxs-lookup"><span data-stu-id="0f2d9-107">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f2d9-108">備註</span><span class="sxs-lookup"><span data-stu-id="0f2d9-108">Remarks</span></span>  
 <span data-ttu-id="0f2d9-109">在呼叫 `ClassLoadFinished` 方法之前，`classId` 的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="0f2d9-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="0f2d9-110">載入類別的某些部分可能會在 `ClassLoadFinished` 回呼之後繼續進行。</span><span class="sxs-lookup"><span data-stu-id="0f2d9-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="0f2d9-111">`hrStatus` 中的失敗 HRESULT 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="0f2d9-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="0f2d9-112">不過，`hrStatus` 中的成功 HRESULT 只會指出載入類別的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="0f2d9-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f2d9-113">需求</span><span class="sxs-lookup"><span data-stu-id="0f2d9-113">Requirements</span></span>  
 <span data-ttu-id="0f2d9-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f2d9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f2d9-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f2d9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f2d9-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f2d9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f2d9-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f2d9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f2d9-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f2d9-118">See also</span></span>

- [<span data-ttu-id="0f2d9-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0f2d9-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0f2d9-120">ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="0f2d9-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
