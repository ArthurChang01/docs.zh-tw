---
title: ICorDebugVirtualUnwinder：： GetCoNtext 方法
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: ce54bfd01abb8bd4efd5e46eff1ef831a9f0c8fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121904"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="d60a1-102">ICorDebugVirtualUnwinder：： GetCoNtext 方法</span><span class="sxs-lookup"><span data-stu-id="d60a1-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="d60a1-103">取得此回溯器的目前內容。</span><span class="sxs-lookup"><span data-stu-id="d60a1-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d60a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="d60a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d60a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="d60a1-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="d60a1-106">[in] 指定要傳回哪些內容的旗標 (在 WinNT.h 中定義)。</span><span class="sxs-lookup"><span data-stu-id="d60a1-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="d60a1-107">[in] `contextBuf` 中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="d60a1-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d60a1-108">[out] 實際寫入至 `contextBuf` 的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="d60a1-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="d60a1-109">[out] 包含此回溯器目前內容的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="d60a1-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d60a1-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="d60a1-110">Return Value</span></span>  
 <span data-ttu-id="d60a1-111">mscordbi 所接收之任何失敗 HRESULT 值會視為嚴重錯誤且會導致 ICorDebug 應用程式開發介面傳回 `CORDBG_E_DATA_TARGET_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="d60a1-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d60a1-112">備註</span><span class="sxs-lookup"><span data-stu-id="d60a1-112">Remarks</span></span>  
 <span data-ttu-id="d60a1-113">您可以藉由呼叫[ICorDebugStackWalk：： GetCoNtext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)方法，將 `contextBuf` 引數的初始值設定為傳回的內容緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d60a1-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d60a1-114">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="d60a1-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="d60a1-115">由於回溯可能只還原暫存器的子集 (例如只還原非暫時性暫存器)，所以在實際方法呼叫時內容可能不完全與暫存器狀態相同。</span><span class="sxs-lookup"><span data-stu-id="d60a1-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d60a1-116">需求</span><span class="sxs-lookup"><span data-stu-id="d60a1-116">Requirements</span></span>  
 <span data-ttu-id="d60a1-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d60a1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d60a1-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d60a1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d60a1-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d60a1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d60a1-120">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d60a1-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d60a1-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="d60a1-121">See also</span></span>

- [<span data-ttu-id="d60a1-122">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="d60a1-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="d60a1-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d60a1-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
