---
title: GetHashFromBlob 函式
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: d1027aea1d800bda1654b223fec992aa70efd4b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140718"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="2d48d-102">GetHashFromBlob 函式</span><span class="sxs-lookup"><span data-stu-id="2d48d-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="2d48d-103">使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="2d48d-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="2d48d-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="2d48d-104">This function has been deprecated.</span></span> <span data-ttu-id="2d48d-105">請改用[ICLRStrongName：： GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2d48d-105">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="2d48d-106">語法</span><span class="sxs-lookup"><span data-stu-id="2d48d-106">Syntax</span></span>

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a><span data-ttu-id="2d48d-107">參數</span><span class="sxs-lookup"><span data-stu-id="2d48d-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="2d48d-108">在要雜湊的記憶體區塊位址的指標。</span><span class="sxs-lookup"><span data-stu-id="2d48d-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="2d48d-109">在記憶體區塊的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d48d-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="2d48d-110">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="2d48d-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2d48d-111">預設演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="2d48d-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="2d48d-112">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2d48d-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="2d48d-113">在`pbHash`的要求大小上限。</span><span class="sxs-lookup"><span data-stu-id="2d48d-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="2d48d-114">脫銷傳回之 `pbHash`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d48d-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d48d-115">需求</span><span class="sxs-lookup"><span data-stu-id="2d48d-115">Requirements</span></span>

<span data-ttu-id="2d48d-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d48d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2d48d-117">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="2d48d-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="2d48d-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2d48d-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="2d48d-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d48d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2d48d-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="2d48d-120">See also</span></span>

- [<span data-ttu-id="2d48d-121">GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="2d48d-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="2d48d-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="2d48d-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
