---
title: ICorProfilerObjectEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: 99778240afb7e296b93cd87ab91feeca20d02637
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428271"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="131a3-102">ICorProfilerObjectEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="131a3-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="131a3-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="131a3-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="131a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="131a3-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="131a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="131a3-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="131a3-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="131a3-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="131a3-107">The copy maintains its own enumeration state separately from this one.</span><span class="sxs-lookup"><span data-stu-id="131a3-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="131a3-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span><span class="sxs-lookup"><span data-stu-id="131a3-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="131a3-109">需求</span><span class="sxs-lookup"><span data-stu-id="131a3-109">Requirements</span></span>  
 <span data-ttu-id="131a3-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="131a3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="131a3-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="131a3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="131a3-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="131a3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="131a3-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="131a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131a3-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="131a3-114">See also</span></span>

- [<span data-ttu-id="131a3-115">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="131a3-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
