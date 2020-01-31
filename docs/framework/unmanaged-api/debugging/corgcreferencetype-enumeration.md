---
title: CorGCReferenceType 列舉
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: 17d47b6242bb12ff5ca3cfbde3e4ec183b9c19fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793868"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="176b0-102">CorGCReferenceType 列舉</span><span class="sxs-lookup"><span data-stu-id="176b0-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="176b0-103">識別要進行記憶體回收的物件來源。</span><span class="sxs-lookup"><span data-stu-id="176b0-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="176b0-104">語法</span><span class="sxs-lookup"><span data-stu-id="176b0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="176b0-105">Members</span><span class="sxs-lookup"><span data-stu-id="176b0-105">Members</span></span>  
  
|<span data-ttu-id="176b0-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="176b0-106">Member name</span></span>|<span data-ttu-id="176b0-107">描述</span><span class="sxs-lookup"><span data-stu-id="176b0-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="176b0-108">物件控制代碼資料表中的強式參考控制代碼。</span><span class="sxs-lookup"><span data-stu-id="176b0-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="176b0-109">物件控制碼資料表中釘選的強式參考的控制碼。</span><span class="sxs-lookup"><span data-stu-id="176b0-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="176b0-110">物件控制碼資料表中弱式參考的控制碼。</span><span class="sxs-lookup"><span data-stu-id="176b0-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="176b0-111">物件控制碼資料表中弱式參考計數物件的控制碼。</span><span class="sxs-lookup"><span data-stu-id="176b0-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="176b0-112">物件控制碼資料表中參考計數物件的控制碼。</span><span class="sxs-lookup"><span data-stu-id="176b0-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="176b0-113">物件控制碼資料表中相依物件的控制碼。</span><span class="sxs-lookup"><span data-stu-id="176b0-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="176b0-114">物件控制代碼資料表中的非同步固定物件。</span><span class="sxs-lookup"><span data-stu-id="176b0-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="176b0-115">強式控制代碼，保留記憶體回收時集體關閉之所有物件和根物件的估計大小。</span><span class="sxs-lookup"><span data-stu-id="176b0-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="176b0-116">Managed 堆疊中的參考。</span><span class="sxs-lookup"><span data-stu-id="176b0-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="176b0-117">完成項佇列的參考。</span><span class="sxs-lookup"><span data-stu-id="176b0-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="176b0-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="176b0-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="176b0-119">只傳回控制碼資料表中的強式參考。</span><span class="sxs-lookup"><span data-stu-id="176b0-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="176b0-120">此值僅供[ICorDebugProcess5：： EnumerateHandles](icordebugprocess5-enumeratehandles-method.md)方法使用。</span><span class="sxs-lookup"><span data-stu-id="176b0-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="176b0-121">只傳回控制碼資料表中的弱式參考。</span><span class="sxs-lookup"><span data-stu-id="176b0-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="176b0-122">此值僅供[ICorDebugProcess5：： EnumerateHandles](icordebugprocess5-enumeratehandles-method.md)方法使用。</span><span class="sxs-lookup"><span data-stu-id="176b0-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="176b0-123">傳回控制碼資料表中的所有參考。</span><span class="sxs-lookup"><span data-stu-id="176b0-123">Return all references from the handle table.</span></span> <span data-ttu-id="176b0-124">此值僅供[ICorDebugProcess5：： EnumerateHandles](icordebugprocess5-enumeratehandles-method.md)方法使用。</span><span class="sxs-lookup"><span data-stu-id="176b0-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="176b0-125">備註</span><span class="sxs-lookup"><span data-stu-id="176b0-125">Remarks</span></span>  
 <span data-ttu-id="176b0-126">`CorGCReferenceType` 列舉的使用方式如下：</span><span class="sxs-lookup"><span data-stu-id="176b0-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="176b0-127">做為[COR_GC_REFERENCE](cor-gc-reference-structure.md)結構的 [`type`] 欄位的值，它會指出參考或控制碼的來源。</span><span class="sxs-lookup"><span data-stu-id="176b0-127">As the value of the `type` field of the [COR_GC_REFERENCE](cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="176b0-128">做為[ICorDebugProcess5：： EnumerateHandles](icordebugprocess5-enumeratehandles-method.md)方法的 `types` 引數，它會指定要包含在列舉中的控制碼類型。</span><span class="sxs-lookup"><span data-stu-id="176b0-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="176b0-129">需求</span><span class="sxs-lookup"><span data-stu-id="176b0-129">Requirements</span></span>  
 <span data-ttu-id="176b0-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="176b0-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="176b0-131">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="176b0-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="176b0-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="176b0-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="176b0-133">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="176b0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176b0-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="176b0-134">See also</span></span>

- [<span data-ttu-id="176b0-135">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="176b0-135">Debugging Enumerations</span></span>](debugging-enumerations.md)
