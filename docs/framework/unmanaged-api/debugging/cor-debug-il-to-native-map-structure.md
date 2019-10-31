---
title: COR_DEBUG_IL_TO_NATIVE_MAP 結構
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
ms.openlocfilehash: 2a36c9808f29c038e3185157078c235959baf13c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132371"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="e4496-102">COR_DEBUG_IL_TO_NATIVE_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="e4496-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="e4496-103">包含用來將 Microsoft 中繼語言 (MSIL) 程式碼對應至機器碼的位移。</span><span class="sxs-lookup"><span data-stu-id="e4496-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4496-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4496-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="e4496-105">Members</span><span class="sxs-lookup"><span data-stu-id="e4496-105">Members</span></span>  
  
|<span data-ttu-id="e4496-106">成員</span><span class="sxs-lookup"><span data-stu-id="e4496-106">Member</span></span>|<span data-ttu-id="e4496-107">描述</span><span class="sxs-lookup"><span data-stu-id="e4496-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="e4496-108">MSIL 程式碼的位移。</span><span class="sxs-lookup"><span data-stu-id="e4496-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="e4496-109">機器碼開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="e4496-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="e4496-110">機器碼結尾的位移。</span><span class="sxs-lookup"><span data-stu-id="e4496-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4496-111">需求</span><span class="sxs-lookup"><span data-stu-id="e4496-111">Requirements</span></span>  
 <span data-ttu-id="e4496-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4496-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4496-113">**標頭：** Corprof.idl .idl，Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="e4496-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="e4496-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4496-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4496-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4496-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4496-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4496-116">See also</span></span>

- [<span data-ttu-id="e4496-117">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="e4496-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="e4496-118">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="e4496-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="e4496-119">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="e4496-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e4496-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="e4496-120">Debugging</span></span>](index.md)
