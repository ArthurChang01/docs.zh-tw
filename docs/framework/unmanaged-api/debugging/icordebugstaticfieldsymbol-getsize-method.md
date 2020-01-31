---
title: ICorDebugStaticFieldSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: deeb887dad38417e3ebb980f5ef2f89392388d65
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791813"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="2ff0e-102">ICorDebugStaticFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="2ff0e-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="2ff0e-103">取得靜態欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="2ff0e-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff0e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2ff0e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ff0e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2ff0e-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="2ff0e-106">[out] 欄位長度的指標。</span><span class="sxs-lookup"><span data-stu-id="2ff0e-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ff0e-107">備註</span><span class="sxs-lookup"><span data-stu-id="2ff0e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ff0e-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="2ff0e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff0e-109">需求</span><span class="sxs-lookup"><span data-stu-id="2ff0e-109">Requirements</span></span>  
 <span data-ttu-id="2ff0e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ff0e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff0e-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ff0e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ff0e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ff0e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ff0e-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff0e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff0e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ff0e-114">See also</span></span>

- [<span data-ttu-id="2ff0e-115">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="2ff0e-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="2ff0e-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2ff0e-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
