---
title: IMetaDataEmit::SetParent 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: a73afaebc2943190eeeee50367ecd31f1fb59df1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432448"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="dd639-102">IMetaDataEmit::SetParent 方法</span><span class="sxs-lookup"><span data-stu-id="dd639-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="dd639-103">建立指定的成員（如先前呼叫[IMetaDataEmit：:D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)所定義）是指定類型的成員，如先前的[IMetaDataEmit：:D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)呼叫所定義。</span><span class="sxs-lookup"><span data-stu-id="dd639-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd639-104">語法</span><span class="sxs-lookup"><span data-stu-id="dd639-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd639-105">參數</span><span class="sxs-lookup"><span data-stu-id="dd639-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="dd639-106">在要接收新父系的 `mdMemberRef` token。</span><span class="sxs-lookup"><span data-stu-id="dd639-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="dd639-107">在新父系的 `mdToken`。</span><span class="sxs-lookup"><span data-stu-id="dd639-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd639-108">需求</span><span class="sxs-lookup"><span data-stu-id="dd639-108">Requirements</span></span>  
 <span data-ttu-id="dd639-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dd639-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd639-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="dd639-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd639-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="dd639-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd639-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd639-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd639-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd639-113">See also</span></span>

- [<span data-ttu-id="dd639-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="dd639-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dd639-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="dd639-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
