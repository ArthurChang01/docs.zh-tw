---
title: ICorDebugHeapValue2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2
helpviewer_keywords:
- ICorDebugHeapValue2 interface [.NET Framework debugging]
ms.assetid: 87360a52-90b1-4ada-80c0-589a556116d8
topic_type:
- apiref
ms.openlocfilehash: d7126222bd23548ec7013ba234c3f3eebbc8e374
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788637"
---
# <a name="icordebugheapvalue2-interface"></a><span data-ttu-id="33477-102">ICorDebugHeapValue2 介面</span><span class="sxs-lookup"><span data-stu-id="33477-102">ICorDebugHeapValue2 Interface</span></span>

<span data-ttu-id="33477-103">ICorDebugHeapValue 的延伸模組，可提供 common language runtime （CLR）控制碼的支援。</span><span class="sxs-lookup"><span data-stu-id="33477-103">An extension of ICorDebugHeapValue that provides support for common language runtime (CLR) handles.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33477-104">方法</span><span class="sxs-lookup"><span data-stu-id="33477-104">Methods</span></span>  
  
|<span data-ttu-id="33477-105">方法</span><span class="sxs-lookup"><span data-stu-id="33477-105">Method</span></span>|<span data-ttu-id="33477-106">描述</span><span class="sxs-lookup"><span data-stu-id="33477-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33477-107">CreateHandle 方法</span><span class="sxs-lookup"><span data-stu-id="33477-107">CreateHandle Method</span></span>](icordebugheapvalue2-createhandle-method.md)|<span data-ttu-id="33477-108">建立這個 `ICorDebugHeapValue2` 物件之指定類型的控制碼。</span><span class="sxs-lookup"><span data-stu-id="33477-108">Creates a handle of the specified type for this `ICorDebugHeapValue2` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33477-109">備註</span><span class="sxs-lookup"><span data-stu-id="33477-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33477-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="33477-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33477-111">需求</span><span class="sxs-lookup"><span data-stu-id="33477-111">Requirements</span></span>  
 <span data-ttu-id="33477-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33477-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33477-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33477-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33477-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33477-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33477-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33477-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33477-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="33477-116">See also</span></span>

- [<span data-ttu-id="33477-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="33477-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
