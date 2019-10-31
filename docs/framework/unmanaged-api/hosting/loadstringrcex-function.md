---
title: LoadStringRCEx 函式
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: 68332aee895f012bcf6ab6a72936c8dddc7f28a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122040"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="c8691-102">LoadStringRCEx 函式</span><span class="sxs-lookup"><span data-stu-id="c8691-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="c8691-103">針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c8691-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="c8691-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="c8691-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8691-105">語法</span><span class="sxs-lookup"><span data-stu-id="c8691-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8691-106">參數</span><span class="sxs-lookup"><span data-stu-id="c8691-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="c8691-107">在文化特性識別碼。</span><span class="sxs-lookup"><span data-stu-id="c8691-107">[in] A culture identifier.</span></span> <span data-ttu-id="c8691-108">傳遞-1 表示 `lcid` 使用預設文化特性。</span><span class="sxs-lookup"><span data-stu-id="c8691-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="c8691-109">在HRESULT。</span><span class="sxs-lookup"><span data-stu-id="c8691-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="c8691-110">脫銷一個緩衝區，其中包含成功完成時的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c8691-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="c8691-111">在錯誤訊息緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="c8691-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="c8691-112">在忽略.</span><span class="sxs-lookup"><span data-stu-id="c8691-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="c8691-113">脫銷錯誤訊息長度的指標。</span><span class="sxs-lookup"><span data-stu-id="c8691-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8691-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="c8691-114">Return Value</span></span>  
 <span data-ttu-id="c8691-115">這個方法會傳回標準 COM 錯誤碼（如 Winerror.h 中所定義），以及下列值。</span><span class="sxs-lookup"><span data-stu-id="c8691-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c8691-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="c8691-116">Return code</span></span>|<span data-ttu-id="c8691-117">描述</span><span class="sxs-lookup"><span data-stu-id="c8691-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c8691-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8691-118">S_OK</span></span>|<span data-ttu-id="c8691-119">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="c8691-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="c8691-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c8691-120">E_INVALIDARG</span></span>|<span data-ttu-id="c8691-121">`szBuffer` 為 null，或 `iMax` 為零（0）。</span><span class="sxs-lookup"><span data-stu-id="c8691-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8691-122">備註</span><span class="sxs-lookup"><span data-stu-id="c8691-122">Remarks</span></span>  
 <span data-ttu-id="c8691-123">如果方法未順利完成，`szBuffer` 會包含空字串。</span><span class="sxs-lookup"><span data-stu-id="c8691-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8691-124">需求</span><span class="sxs-lookup"><span data-stu-id="c8691-124">Requirements</span></span>  
 <span data-ttu-id="c8691-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8691-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8691-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c8691-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8691-127">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="c8691-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8691-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8691-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8691-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8691-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c8691-130">LoadStringRC 函式</span><span class="sxs-lookup"><span data-stu-id="c8691-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="c8691-131">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="c8691-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
