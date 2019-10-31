---
title: GetTypeLibInfo 函式
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
ms.openlocfilehash: e64a0512e05965b3da2e7486e986ee34ca8a20d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104309"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="f2454-102">GetTypeLibInfo 函式</span><span class="sxs-lookup"><span data-stu-id="f2454-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="f2454-103">藉由檢查[TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr)結構，傳回指定之類型程式庫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f2454-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2454-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2454-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2454-105">參數</span><span class="sxs-lookup"><span data-stu-id="f2454-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="f2454-106">在類型程式庫的檔案名。</span><span class="sxs-lookup"><span data-stu-id="f2454-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="f2454-107">脫銷類型程式庫的 GUID。</span><span class="sxs-lookup"><span data-stu-id="f2454-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="f2454-108">脫銷類型程式庫的當地語系化識別碼。</span><span class="sxs-lookup"><span data-stu-id="f2454-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="f2454-109">脫銷[SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind)旗標，可識別類型程式庫的目標作業系統。</span><span class="sxs-lookup"><span data-stu-id="f2454-109">[out] A [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="f2454-110">常見的值為 SYS_WIN32 和 SYS_WIN64。</span><span class="sxs-lookup"><span data-stu-id="f2454-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="f2454-111">脫銷類型程式庫的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f2454-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="f2454-112">例如，針對版本*x. y*，主要版本號碼為*x*。</span><span class="sxs-lookup"><span data-stu-id="f2454-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="f2454-113">脫銷類型程式庫的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f2454-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="f2454-114">例如，針對版本*x. y*，次要版本號碼為*y*。</span><span class="sxs-lookup"><span data-stu-id="f2454-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2454-115">備註</span><span class="sxs-lookup"><span data-stu-id="f2454-115">Remarks</span></span>  
 <span data-ttu-id="f2454-116">`GetTypeLibInfo` 函式是由[tlbexp.exe （類型程式庫匯出工具）](../../tools/tlbexp-exe-type-library-exporter.md)所呼叫。</span><span class="sxs-lookup"><span data-stu-id="f2454-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="f2454-117">此工具會產生類型程式庫，以描述 common language runtime （CLR）元件中的類型。</span><span class="sxs-lookup"><span data-stu-id="f2454-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="f2454-118">如果有任何參數為 null，函數會傳回 `E_POINTER`的 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="f2454-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="f2454-119">否則它會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="f2454-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2454-120">需求</span><span class="sxs-lookup"><span data-stu-id="f2454-120">Requirements</span></span>  
 <span data-ttu-id="f2454-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2454-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2454-122">**標頭：** TlbRef。h</span><span class="sxs-lookup"><span data-stu-id="f2454-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="f2454-123">連結**庫：** TlbRef .lib</span><span class="sxs-lookup"><span data-stu-id="f2454-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="f2454-124">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2454-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2454-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2454-125">See also</span></span>

- [<span data-ttu-id="f2454-126">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="f2454-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="f2454-127">LoadTypeLibEx 函式</span><span class="sxs-lookup"><span data-stu-id="f2454-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
