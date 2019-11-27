---
title: ICorProfilerCallback::JITCompilationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 1bbdfa93913b9fdf8aa164c8ca6c35cd33a228df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449914"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="72b25-102">ICorProfilerCallback::JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="72b25-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="72b25-103">通知分析工具，及時（JIT）編譯器已完成編譯函式。</span><span class="sxs-lookup"><span data-stu-id="72b25-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72b25-104">語法</span><span class="sxs-lookup"><span data-stu-id="72b25-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72b25-105">參數</span><span class="sxs-lookup"><span data-stu-id="72b25-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="72b25-106">在已編譯之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="72b25-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="72b25-107">在值，指出編譯是否成功。</span><span class="sxs-lookup"><span data-stu-id="72b25-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="72b25-108">在值，表示封鎖器是否會影響執行時間的作業。</span><span class="sxs-lookup"><span data-stu-id="72b25-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="72b25-109">如果封鎖可能會導致執行時間等候呼叫執行緒從這個回呼傳回，則此值為 `true`。否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="72b25-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="72b25-110">雖然 `true` 的值不會傷害執行時間，但它可能會扭曲分析結果。</span><span class="sxs-lookup"><span data-stu-id="72b25-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72b25-111">需求</span><span class="sxs-lookup"><span data-stu-id="72b25-111">Requirements</span></span>  
 <span data-ttu-id="72b25-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72b25-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72b25-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72b25-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72b25-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72b25-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72b25-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72b25-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b25-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72b25-116">See also</span></span>

- [<span data-ttu-id="72b25-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="72b25-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="72b25-118">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="72b25-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
