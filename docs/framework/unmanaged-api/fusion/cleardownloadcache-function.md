---
title: ClearDownloadCache 函式
ms.date: 03/30/2017
api_name:
- ClearDownloadCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- ClearDownloadCache
helpviewer_keywords:
- ClearDownloadCache function [.NET Framework fusion]
ms.assetid: df7595d1-430f-44b4-8160-4c2ba9df70b1
topic_type:
- apiref
ms.openlocfilehash: 0648ba9a35290543f485a67719c6adfeba9114b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108959"
---
# <a name="cleardownloadcache-function"></a><span data-ttu-id="d39f7-102">ClearDownloadCache 函式</span><span class="sxs-lookup"><span data-stu-id="d39f7-102">ClearDownloadCache Function</span></span>
<span data-ttu-id="d39f7-103">清除已下載元件的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="d39f7-103">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d39f7-104">語法</span><span class="sxs-lookup"><span data-stu-id="d39f7-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearDownloadCache ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d39f7-105">需求</span><span class="sxs-lookup"><span data-stu-id="d39f7-105">Requirements</span></span>  
 <span data-ttu-id="d39f7-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d39f7-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d39f7-107">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="d39f7-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d39f7-108">連結**庫：** 融合 .dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="d39f7-108">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="d39f7-109">請使用 [Mscorwks.dll]，而不是 []，以確保您以正確的 .NET Framework 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="d39f7-109">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d39f7-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d39f7-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39f7-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="d39f7-111">See also</span></span>

- [<span data-ttu-id="d39f7-112">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d39f7-112">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="d39f7-113">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="d39f7-113">Global Assembly Cache</span></span>](../../app-domains/gac.md)
