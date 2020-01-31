---
title: ICorDebugMDA::GetFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 0c7b8dae756fbb9ab27ff187eeb83a931b016b7f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793279"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="1ebbc-102">ICorDebugMDA::GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="1ebbc-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="1ebbc-103">取得與[ICorDebugMDA](icordebugmda-interface.md)代表的 managed 偵錯工具（MDA）相關聯的旗標。</span><span class="sxs-lookup"><span data-stu-id="1ebbc-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ebbc-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ebbc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ebbc-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ebbc-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="1ebbc-106">在[CorDebugMDAFlags](cordebugmdaflags-enumeration.md)列舉值的位元組合，指定此 MDA 的旗標設定。</span><span class="sxs-lookup"><span data-stu-id="1ebbc-106">[in] A bitwise combination of the [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ebbc-107">需求</span><span class="sxs-lookup"><span data-stu-id="1ebbc-107">Requirements</span></span>  
 <span data-ttu-id="1ebbc-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ebbc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ebbc-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ebbc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ebbc-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ebbc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ebbc-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ebbc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ebbc-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ebbc-112">See also</span></span>

- [<span data-ttu-id="1ebbc-113">ICorDebugMDA 介面</span><span class="sxs-lookup"><span data-stu-id="1ebbc-113">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="1ebbc-114">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="1ebbc-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
