---
title: ICorProfilerInfo2::GetCodeInfo2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 5149e3fab023de42d03673ec5d3e5ae888a9ed5a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433283"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="e5cf9-102">ICorProfilerInfo2::GetCodeInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="e5cf9-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="e5cf9-103">取得與指定 `FunctionID` 相關聯的原生程式碼範圍。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5cf9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5cf9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5cf9-105">參數</span><span class="sxs-lookup"><span data-stu-id="e5cf9-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="e5cf9-106">[in] 與機器碼關聯的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="e5cf9-107">[in] `codeInfos` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="e5cf9-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span><span class="sxs-lookup"><span data-stu-id="e5cf9-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="e5cf9-109">[out] 呼叫者提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="e5cf9-110">方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5cf9-111">備註</span><span class="sxs-lookup"><span data-stu-id="e5cf9-111">Remarks</span></span>  
 <span data-ttu-id="e5cf9-112">範圍是以遞增的 Microsoft 中繼語言 (MSIL) 位移順序來排序。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="e5cf9-113">`GetCodeInfo2` 傳回之後，您必須確認 `codeInfos` 緩衝區夠大，可以包含所有 `COR_PRF_CODE_INFO` 結構。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="e5cf9-114">若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e5cf9-115">如果 `cCodeInfos` 除以 `COR_PRF_CODE_INFO` 結構的大小之後小於`pcCodeInfos`，請配置較大的 `codeInfos` 緩衝區，以新的較大大小更新 `cCodeInfos`，然後重新呼叫 `GetCodeInfo2`。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="e5cf9-116">或者，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo2`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e5cf9-117">您可以將 `codeInfos` 緩衝區大小設定為 `pcCodeInfos` 中傳回的值，乘以 `COR_PRF_CODE_INFO` 結構的大小，然後重新呼叫 `GetCodeInfo2`。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5cf9-118">需求</span><span class="sxs-lookup"><span data-stu-id="e5cf9-118">Requirements</span></span>  
 <span data-ttu-id="e5cf9-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5cf9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5cf9-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5cf9-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5cf9-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5cf9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5cf9-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5cf9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5cf9-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5cf9-123">See also</span></span>

- [<span data-ttu-id="e5cf9-124">GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="e5cf9-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="e5cf9-125">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="e5cf9-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="e5cf9-126">分析介面</span><span class="sxs-lookup"><span data-stu-id="e5cf9-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="e5cf9-127">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="e5cf9-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
