---
title: ICorDebugModule3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
ms.openlocfilehash: 33acc4d9a0819c43d17c362fcbea2e7636521fd3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792939"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="b9df2-102">ICorDebugModule3 介面</span><span class="sxs-lookup"><span data-stu-id="b9df2-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="b9df2-103">建立動態模組的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="b9df2-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9df2-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9df2-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b9df2-105">方法</span><span class="sxs-lookup"><span data-stu-id="b9df2-105">Methods</span></span>  
  
|<span data-ttu-id="b9df2-106">方法</span><span class="sxs-lookup"><span data-stu-id="b9df2-106">Method</span></span>|<span data-ttu-id="b9df2-107">描述</span><span class="sxs-lookup"><span data-stu-id="b9df2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9df2-108">ICorDebugModule3::CreateReaderForInMemorySymbols 方法</span><span class="sxs-lookup"><span data-stu-id="b9df2-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="b9df2-109">建立動態模組的符號讀取器（通常是[ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)）。</span><span class="sxs-lookup"><span data-stu-id="b9df2-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9df2-110">備註</span><span class="sxs-lookup"><span data-stu-id="b9df2-110">Remarks</span></span>  
 <span data-ttu-id="b9df2-111">這個介面會以邏輯方式擴充 "ICorDebugModule" 和 "ICorDebugModule2" 介面。</span><span class="sxs-lookup"><span data-stu-id="b9df2-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9df2-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b9df2-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9df2-113">需求</span><span class="sxs-lookup"><span data-stu-id="b9df2-113">Requirements</span></span>  
 <span data-ttu-id="b9df2-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9df2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9df2-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9df2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9df2-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9df2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9df2-117">**.NET Framework 版本：** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b9df2-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b9df2-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9df2-118">See also</span></span>

- [<span data-ttu-id="b9df2-119">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="b9df2-119">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="b9df2-120">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="b9df2-120">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="b9df2-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b9df2-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
