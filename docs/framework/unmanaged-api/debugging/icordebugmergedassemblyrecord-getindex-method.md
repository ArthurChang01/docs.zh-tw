---
title: ICorDebugMergedAssemblyRecord：： GetIndex 方法
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: 236bd8b22d6c3ec783d787f6c906ede3193cfc1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131413"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="4acd9-102">ICorDebugMergedAssemblyRecord：： GetIndex 方法</span><span class="sxs-lookup"><span data-stu-id="4acd9-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="4acd9-103">取得組件的前置詞索引。</span><span class="sxs-lookup"><span data-stu-id="4acd9-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4acd9-104">語法</span><span class="sxs-lookup"><span data-stu-id="4acd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4acd9-105">參數</span><span class="sxs-lookup"><span data-stu-id="4acd9-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="4acd9-106">[out] 指向前置詞索引的指標。</span><span class="sxs-lookup"><span data-stu-id="4acd9-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4acd9-107">備註</span><span class="sxs-lookup"><span data-stu-id="4acd9-107">Remarks</span></span>  
 <span data-ttu-id="4acd9-108">在合併中繼資料類型名稱中，前置詞索引用來避免發生名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="4acd9-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4acd9-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="4acd9-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4acd9-110">需求</span><span class="sxs-lookup"><span data-stu-id="4acd9-110">Requirements</span></span>  
 <span data-ttu-id="4acd9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4acd9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4acd9-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4acd9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4acd9-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4acd9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4acd9-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4acd9-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4acd9-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="4acd9-115">See also</span></span>

- [<span data-ttu-id="4acd9-116">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="4acd9-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="4acd9-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4acd9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
