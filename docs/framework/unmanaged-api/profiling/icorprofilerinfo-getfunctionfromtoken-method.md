---
title: ICorProfilerInfo::GetFunctionFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
ms.openlocfilehash: 72531dc4fa7a8afc3bd719d73389fac94e3363bb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439136"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="1169b-102">ICorProfilerInfo::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="1169b-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="1169b-103">Gets the ID of a function.</span><span class="sxs-lookup"><span data-stu-id="1169b-103">Gets the ID of a function.</span></span> <span data-ttu-id="1169b-104">This method is obsolete in the .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="1169b-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="1169b-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span><span class="sxs-lookup"><span data-stu-id="1169b-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1169b-106">語法</span><span class="sxs-lookup"><span data-stu-id="1169b-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="1169b-107">備註</span><span class="sxs-lookup"><span data-stu-id="1169b-107">Remarks</span></span>  
 <span data-ttu-id="1169b-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span><span class="sxs-lookup"><span data-stu-id="1169b-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="1169b-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span><span class="sxs-lookup"><span data-stu-id="1169b-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1169b-110">需求</span><span class="sxs-lookup"><span data-stu-id="1169b-110">Requirements</span></span>  
 <span data-ttu-id="1169b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1169b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1169b-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1169b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1169b-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1169b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1169b-114">**.NET Framework Versions:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="1169b-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1169b-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="1169b-115">See also</span></span>

- [<span data-ttu-id="1169b-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="1169b-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
