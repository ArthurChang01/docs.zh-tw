---
title: ICeeGen::ComputePointer 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
ms.openlocfilehash: 01be6c30e16e4abdd6002fc8207b33a9c76a2eef
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448750"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="b96cf-102">ICeeGen::ComputePointer 方法</span><span class="sxs-lookup"><span data-stu-id="b96cf-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="b96cf-103">判斷指定之程式碼區段的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b96cf-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="b96cf-104">這個方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="b96cf-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b96cf-105">語法</span><span class="sxs-lookup"><span data-stu-id="b96cf-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b96cf-106">參數</span><span class="sxs-lookup"><span data-stu-id="b96cf-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="b96cf-107">在要傳回緩衝區的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="b96cf-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="b96cf-108">在要取得指標之方法的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="b96cf-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="b96cf-109">脫銷傳回之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="b96cf-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b96cf-110">需求</span><span class="sxs-lookup"><span data-stu-id="b96cf-110">Requirements</span></span>  
 <span data-ttu-id="b96cf-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b96cf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b96cf-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b96cf-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b96cf-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="b96cf-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b96cf-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b96cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96cf-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="b96cf-115">See also</span></span>

- [<span data-ttu-id="b96cf-116">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="b96cf-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
