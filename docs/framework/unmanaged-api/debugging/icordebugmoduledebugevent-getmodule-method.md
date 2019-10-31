---
title: ICorDebugModuleDebugEvent：： GetModule 方法
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 5dc26d0367d01bc8da957c3ce648c3e529dddb08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096943"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="02fca-102">ICorDebugModuleDebugEvent：： GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="02fca-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="02fca-103">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="02fca-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02fca-104">語法</span><span class="sxs-lookup"><span data-stu-id="02fca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02fca-105">參數</span><span class="sxs-lookup"><span data-stu-id="02fca-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="02fca-106">脫銷ICorDebugModule 物件位址的指標，代表剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="02fca-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02fca-107">備註</span><span class="sxs-lookup"><span data-stu-id="02fca-107">Remarks</span></span>  
 <span data-ttu-id="02fca-108">您可以呼叫[GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法，以判斷模組是否已載入或卸載。</span><span class="sxs-lookup"><span data-stu-id="02fca-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02fca-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="02fca-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02fca-110">需求</span><span class="sxs-lookup"><span data-stu-id="02fca-110">Requirements</span></span>  
 <span data-ttu-id="02fca-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02fca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02fca-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02fca-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02fca-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02fca-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02fca-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02fca-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02fca-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="02fca-115">See also</span></span>

- [<span data-ttu-id="02fca-116">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="02fca-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="02fca-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="02fca-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
