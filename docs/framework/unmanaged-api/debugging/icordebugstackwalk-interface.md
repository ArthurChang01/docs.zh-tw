---
title: ICorDebugStackWalk 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: a6283d699263dc9b79e457010f31923f77443129
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791883"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="2d988-102">ICorDebugStackWalk 介面</span><span class="sxs-lookup"><span data-stu-id="2d988-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="2d988-103">提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。</span><span class="sxs-lookup"><span data-stu-id="2d988-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d988-104">方法</span><span class="sxs-lookup"><span data-stu-id="2d988-104">Methods</span></span>  
  
|<span data-ttu-id="2d988-105">方法</span><span class="sxs-lookup"><span data-stu-id="2d988-105">Method</span></span>|<span data-ttu-id="2d988-106">描述</span><span class="sxs-lookup"><span data-stu-id="2d988-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d988-107">GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="2d988-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="2d988-108">傳回 `ICorDebugStackWalk` 物件中目前框架的內容。</span><span class="sxs-lookup"><span data-stu-id="2d988-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="2d988-109">SetContext 方法</span><span class="sxs-lookup"><span data-stu-id="2d988-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="2d988-110">將 `ICorDebugStackWalk` 物件的目前內容設定為執行緒的有效內容。</span><span class="sxs-lookup"><span data-stu-id="2d988-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="2d988-111">Next 方法</span><span class="sxs-lookup"><span data-stu-id="2d988-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="2d988-112">將 `ICorDebugStackWalk` 物件移至下一個畫面格。</span><span class="sxs-lookup"><span data-stu-id="2d988-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="2d988-113">GetFrame 方法</span><span class="sxs-lookup"><span data-stu-id="2d988-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="2d988-114">取得 `ICorDebugStackWalk` 物件中的目前框架。</span><span class="sxs-lookup"><span data-stu-id="2d988-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d988-115">備註</span><span class="sxs-lookup"><span data-stu-id="2d988-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d988-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="2d988-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d988-117">需求</span><span class="sxs-lookup"><span data-stu-id="2d988-117">Requirements</span></span>  
 <span data-ttu-id="2d988-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d988-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d988-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d988-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d988-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d988-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d988-121">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d988-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d988-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="2d988-122">See also</span></span>

- [<span data-ttu-id="2d988-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2d988-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2d988-124">偵錯</span><span class="sxs-lookup"><span data-stu-id="2d988-124">Debugging</span></span>](index.md)
