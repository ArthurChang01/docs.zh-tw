---
title: ICorProfilerCallback::ExceptionCLRCatcherExecute 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
ms.openlocfilehash: 165981627337c562dd3721b7d93cb2027d0a0c37
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444936"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="1722a-102">ICorProfilerCallback::ExceptionCLRCatcherExecute 方法</span><span class="sxs-lookup"><span data-stu-id="1722a-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="1722a-103">在 common language runtime （CLR）本身內執行例外狀況的 `catch` 區塊時呼叫。</span><span class="sxs-lookup"><span data-stu-id="1722a-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="1722a-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="1722a-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1722a-105">語法</span><span class="sxs-lookup"><span data-stu-id="1722a-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="1722a-106">需求</span><span class="sxs-lookup"><span data-stu-id="1722a-106">Requirements</span></span>  
 <span data-ttu-id="1722a-107">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1722a-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1722a-108">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1722a-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1722a-109">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1722a-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1722a-110">**.NET Framework 版本：** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="1722a-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1722a-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="1722a-111">See also</span></span>

- [<span data-ttu-id="1722a-112">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1722a-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1722a-113">ExceptionCLRCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="1722a-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
