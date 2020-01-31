---
title: ICorDebugDataTarget2::GetImageFromPointer 方法
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 55c87731399cf1e7a6747720b8bb33de7e01906c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788837"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="3fd70-102">ICorDebugDataTarget2::GetImageFromPointer 方法</span><span class="sxs-lookup"><span data-stu-id="3fd70-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="3fd70-103">從模組中的位址傳回模組基底位址和大小。</span><span class="sxs-lookup"><span data-stu-id="3fd70-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd70-104">語法</span><span class="sxs-lookup"><span data-stu-id="3fd70-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fd70-105">參數</span><span class="sxs-lookup"><span data-stu-id="3fd70-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="3fd70-106">[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組中的位址。</span><span class="sxs-lookup"><span data-stu-id="3fd70-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="3fd70-107">脫銷[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="3fd70-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="3fd70-108">模組大小的指標。</span><span class="sxs-lookup"><span data-stu-id="3fd70-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fd70-109">備註</span><span class="sxs-lookup"><span data-stu-id="3fd70-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fd70-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="3fd70-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd70-111">需求</span><span class="sxs-lookup"><span data-stu-id="3fd70-111">Requirements</span></span>  
 <span data-ttu-id="3fd70-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3fd70-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd70-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fd70-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fd70-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fd70-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fd70-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd70-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd70-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="3fd70-116">See also</span></span>

- [<span data-ttu-id="3fd70-117">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="3fd70-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="3fd70-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3fd70-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
