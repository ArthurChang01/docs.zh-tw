---
title: Init 方法
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
ms.openlocfilehash: 986ae69e7ebb8f607be5d37fab426bcc787abb26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445635"
---
# <a name="init-method"></a><span data-ttu-id="76967-102">Init 方法</span><span class="sxs-lookup"><span data-stu-id="76967-102">Init Method</span></span>
<span data-ttu-id="76967-103">準備物件，以執行[IALink 介面](ialink-interface.md)以供使用。</span><span class="sxs-lookup"><span data-stu-id="76967-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76967-104">語法</span><span class="sxs-lookup"><span data-stu-id="76967-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="76967-105">參數</span><span class="sxs-lookup"><span data-stu-id="76967-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="76967-106">中繼資料分配器的[IMetaDataDispenserEx 介面](../metadata/imetadatadispenserex-interface.md)指標。</span><span class="sxs-lookup"><span data-stu-id="76967-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="76967-107">選擇性錯誤處理介面的[IMetaDataError 介面](../metadata/imetadataerror-interface.md)指標。</span><span class="sxs-lookup"><span data-stu-id="76967-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76967-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="76967-108">Return Value</span></span>  
 <span data-ttu-id="76967-109">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="76967-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76967-110">需求</span><span class="sxs-lookup"><span data-stu-id="76967-110">Requirements</span></span>  
 <span data-ttu-id="76967-111">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="76967-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76967-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76967-112">See also</span></span>

- [<span data-ttu-id="76967-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="76967-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="76967-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="76967-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="76967-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="76967-115">ALink API</span></span>](index.md)
