---
title: IMetaDataImport::EnumModuleRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: 66186d25e8fee0d6b25c0a2069d46ff9a104c625
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450041"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="8b55e-102">IMetaDataImport::EnumModuleRefs 方法</span><span class="sxs-lookup"><span data-stu-id="8b55e-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="8b55e-103">列舉代表已匯入的模組之 ModuleRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8b55e-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b55e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b55e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b55e-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b55e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8b55e-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="8b55e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8b55e-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="8b55e-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="8b55e-108">脫銷用來儲存 ModuleRef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="8b55e-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8b55e-109">[in] `rModuleRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="8b55e-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="8b55e-110">脫銷`rModuleRefs`中傳回的 ModuleRef token 數目。</span><span class="sxs-lookup"><span data-stu-id="8b55e-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b55e-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8b55e-111">Return Value</span></span>  
  
|<span data-ttu-id="8b55e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b55e-112">HRESULT</span></span>|<span data-ttu-id="8b55e-113">描述</span><span class="sxs-lookup"><span data-stu-id="8b55e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8b55e-114">已成功傳回 `EnumModuleRefs`。</span><span class="sxs-lookup"><span data-stu-id="8b55e-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8b55e-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="8b55e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="8b55e-116">在此情況下，`pcModuleRefs` 為零。</span><span class="sxs-lookup"><span data-stu-id="8b55e-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b55e-117">需求</span><span class="sxs-lookup"><span data-stu-id="8b55e-117">Requirements</span></span>  
 <span data-ttu-id="8b55e-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b55e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b55e-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8b55e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b55e-120">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8b55e-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b55e-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b55e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b55e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b55e-122">See also</span></span>

- [<span data-ttu-id="8b55e-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8b55e-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8b55e-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8b55e-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
