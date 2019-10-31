---
title: ICorProfilerInfo7 介面
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4c7e94ffa60bcfaead009e1a8baa9b54b2e8ab7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125059"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="78e78-102">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="78e78-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="78e78-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="78e78-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="78e78-104">[ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)的子類別，提供方法來將新定義的中繼資料套用至模組，並提供記憶體內部符號資料流程的存取權。</span><span class="sxs-lookup"><span data-stu-id="78e78-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78e78-105">方法</span><span class="sxs-lookup"><span data-stu-id="78e78-105">Methods</span></span>  
  
|<span data-ttu-id="78e78-106">方法</span><span class="sxs-lookup"><span data-stu-id="78e78-106">Method</span></span>|<span data-ttu-id="78e78-107">描述</span><span class="sxs-lookup"><span data-stu-id="78e78-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78e78-108">ApplyMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="78e78-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="78e78-109">將 `IMetadataEmit::Define*` 方法新定義的中繼資料套用至指定的模組。</span><span class="sxs-lookup"><span data-stu-id="78e78-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="78e78-110">GetInMemorySymbolsLength 方法</span><span class="sxs-lookup"><span data-stu-id="78e78-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="78e78-111">傳回記憶體中符號資料流程的長度。</span><span class="sxs-lookup"><span data-stu-id="78e78-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="78e78-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="78e78-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="78e78-113">從記憶體中的符號資料流程讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="78e78-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78e78-114">需求</span><span class="sxs-lookup"><span data-stu-id="78e78-114">Requirements</span></span>  
 <span data-ttu-id="78e78-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78e78-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78e78-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78e78-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78e78-117">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78e78-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e78-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="78e78-118">See also</span></span>

- [<span data-ttu-id="78e78-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="78e78-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
