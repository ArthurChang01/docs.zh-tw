---
title: IMetaDataFilter::IsTokenMarked 方法
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
ms.openlocfilehash: 10f31d56a9727e99157f49038c19781f12cd9958
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440426"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="ed816-102">IMetaDataFilter::IsTokenMarked 方法</span><span class="sxs-lookup"><span data-stu-id="ed816-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="ed816-103">取得值，指出指定的元資料標記是否已標示為已處理。</span><span class="sxs-lookup"><span data-stu-id="ed816-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed816-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed816-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed816-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed816-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ed816-106">在要檢查處理標記的 token。</span><span class="sxs-lookup"><span data-stu-id="ed816-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="ed816-107">脫銷如果已處理 `tk`，則為 `true` 的值;否則 `false`。</span><span class="sxs-lookup"><span data-stu-id="ed816-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed816-108">需求</span><span class="sxs-lookup"><span data-stu-id="ed816-108">Requirements</span></span>  
 <span data-ttu-id="ed816-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed816-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed816-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ed816-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed816-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ed816-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed816-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed816-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed816-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed816-113">See also</span></span>

- [<span data-ttu-id="ed816-114">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="ed816-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
