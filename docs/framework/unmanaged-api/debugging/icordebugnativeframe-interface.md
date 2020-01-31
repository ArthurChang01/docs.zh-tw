---
title: ICorDebugNativeFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: 41ac0b29ade2f78b893df72e8a17624373f6dd78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792796"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="b5ac3-102">ICorDebugNativeFrame 介面</span><span class="sxs-lookup"><span data-stu-id="b5ac3-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="b5ac3-103">用於原生框架的 ICorDebugFrame 特製化。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5ac3-104">方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-104">Methods</span></span>  
  
|<span data-ttu-id="b5ac3-105">方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-105">Method</span></span>|<span data-ttu-id="b5ac3-106">描述</span><span class="sxs-lookup"><span data-stu-id="b5ac3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5ac3-107">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-107">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="b5ac3-108">取得值，指出是否可以安全地將指令指標設定為機器碼中的指定位移位置。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="b5ac3-109">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-109">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="b5ac3-110">取得原生程式碼的堆疊框架位移。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="b5ac3-111">GetLocalDoubleRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-111">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="b5ac3-112">取得 ICorDebugValue 的指標，代表儲存在原生框架之兩個記憶體暫存器中的引數或區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="b5ac3-113">GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-113">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="b5ac3-114">取得 `ICorDebugValue` 的指標，表示本機變數的值，其中的低位會儲存在指定的暫存器中，而高位則儲存在指定的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="b5ac3-115">GetLocalMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-115">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="b5ac3-116">取得 `ICorDebugValue` 的指標，表示儲存在指定記憶體位址的本機變數值。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="b5ac3-117">GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-117">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="b5ac3-118">取得 `ICorDebugValue` 的指標，表示本機變數的值，其中的高位會儲存在指定的暫存器中，而低位則儲存在指定的記憶體位址</span><span class="sxs-lookup"><span data-stu-id="b5ac3-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="b5ac3-119">GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-119">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="b5ac3-120">取得 `ICorDebugValue` 的指標，表示引數或儲存在指定的原生暫存器中的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="b5ac3-121">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-121">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="b5ac3-122">取得[ICorDebugRegisterSet](icordebugregisterset-interface.md)的指標，表示此 `ICorDebugNativeFrame`的暫存器集。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-122">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="b5ac3-123">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="b5ac3-123">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="b5ac3-124">將指令指標設定為原生程式碼中指定的位移位置。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5ac3-125">備註</span><span class="sxs-lookup"><span data-stu-id="b5ac3-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5ac3-126">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5ac3-127">需求</span><span class="sxs-lookup"><span data-stu-id="b5ac3-127">Requirements</span></span>  
 <span data-ttu-id="b5ac3-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5ac3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5ac3-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5ac3-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5ac3-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5ac3-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5ac3-131">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5ac3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ac3-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5ac3-132">See also</span></span>

- [<span data-ttu-id="b5ac3-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b5ac3-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
