---
title: ICorDebugCode::IsIL 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
ms.openlocfilehash: 77e55c4c3644ac4bd76f5c92152f4ee86cf5fa9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125570"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="95878-102">ICorDebugCode::IsIL 方法</span><span class="sxs-lookup"><span data-stu-id="95878-102">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="95878-103">取得值，指出這個 "ICorDebugCode" 是否代表以 Microsoft 中繼語言（MSIL）編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="95878-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="95878-104">語法</span><span class="sxs-lookup"><span data-stu-id="95878-104">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="95878-105">參數</span><span class="sxs-lookup"><span data-stu-id="95878-105">Parameters</span></span>

`pbIL`  
<span data-ttu-id="95878-106">[out] `true` 如果這個 `ICorDebugCode` 代表在 MSIL 中編譯的程式碼，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="95878-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="95878-107">需求</span><span class="sxs-lookup"><span data-stu-id="95878-107">Requirements</span></span>

<span data-ttu-id="95878-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95878-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="95878-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95878-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="95878-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95878-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="95878-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95878-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
