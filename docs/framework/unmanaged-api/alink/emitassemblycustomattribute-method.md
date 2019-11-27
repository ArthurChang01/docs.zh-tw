---
title: EmitAssemblyCustomAttribute 方法
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: ec0a86e3396ad42152bc0a244f74ad13deba16e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446515"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="0b35d-102">EmitAssemblyCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="0b35d-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="0b35d-103">呼叫以設定元件層級的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="0b35d-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b35d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b35d-104">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b35d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0b35d-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0b35d-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0b35d-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0b35d-107">定義屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="0b35d-107">File that defiles the attribute.</span></span> <span data-ttu-id="0b35d-108">如果 `AssemblyID` 未指出未系結的 .netmodule，則可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="0b35d-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="0b35d-109">自訂屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="0b35d-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="0b35d-110">自訂值資料。</span><span class="sxs-lookup"><span data-stu-id="0b35d-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="0b35d-111">自訂值資料的長度。</span><span class="sxs-lookup"><span data-stu-id="0b35d-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="0b35d-112">如果自訂屬性與元件簽署有關，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0b35d-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="0b35d-113">如果要發出多個屬性，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="0b35d-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b35d-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="0b35d-114">Return Value</span></span>  
 <span data-ttu-id="0b35d-115">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="0b35d-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b35d-116">需求</span><span class="sxs-lookup"><span data-stu-id="0b35d-116">Requirements</span></span>  
 <span data-ttu-id="0b35d-117">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="0b35d-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b35d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b35d-118">See also</span></span>

- [<span data-ttu-id="0b35d-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="0b35d-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0b35d-120">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="0b35d-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0b35d-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="0b35d-121">ALink API</span></span>](index.md)
