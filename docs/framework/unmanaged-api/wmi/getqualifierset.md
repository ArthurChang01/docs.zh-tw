---
title: GetQualifierSet 函式（非受控 API 參考）
description: GetQualifierSet 函數會抓取類別或實例的限定詞集合。
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 489e240af3f26e82f2459ac4b4dbd944639f78fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127444"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="b6fb8-103">GetQualifierSet 函式</span><span class="sxs-lookup"><span data-stu-id="b6fb8-103">GetQualifierSet function</span></span>
<span data-ttu-id="b6fb8-104">擷取類別執行個體或類別定義的限定詞集合。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b6fb8-105">語法</span><span class="sxs-lookup"><span data-stu-id="b6fb8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="b6fb8-106">參數</span><span class="sxs-lookup"><span data-stu-id="b6fb8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b6fb8-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b6fb8-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="b6fb8-109">脫銷接收介面指標，允許存取 class 物件的限定詞。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="b6fb8-110">`ppQualSet` 不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="b6fb8-111">如果發生錯誤，則不會傳回新的物件，且會將指標保留為未修改。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="b6fb8-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6fb8-112">Return value</span></span>

<span data-ttu-id="b6fb8-113">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="b6fb8-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b6fb8-114">常數</span><span class="sxs-lookup"><span data-stu-id="b6fb8-114">Constant</span></span>  |<span data-ttu-id="b6fb8-115">值</span><span class="sxs-lookup"><span data-stu-id="b6fb8-115">Value</span></span>  |<span data-ttu-id="b6fb8-116">描述</span><span class="sxs-lookup"><span data-stu-id="b6fb8-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="b6fb8-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b6fb8-117">0x80041001</span></span> | <span data-ttu-id="b6fb8-118">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="b6fb8-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="b6fb8-119">0x80041002</span></span> | <span data-ttu-id="b6fb8-120">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b6fb8-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b6fb8-121">0x80041006</span></span> | <span data-ttu-id="b6fb8-122">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b6fb8-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b6fb8-123">0x80041008</span></span> | <span data-ttu-id="b6fb8-124">參數為 `null`。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b6fb8-125">0</span><span class="sxs-lookup"><span data-stu-id="b6fb8-125">0</span></span> | <span data-ttu-id="b6fb8-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b6fb8-127">備註</span><span class="sxs-lookup"><span data-stu-id="b6fb8-127">Remarks</span></span>

<span data-ttu-id="b6fb8-128">此函式會包裝對[IWbemClassObject：： GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span> 

<span data-ttu-id="b6fb8-129">[IWbemQualifierSet 指標](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)可讓呼叫者加入、編輯或刪除這些限定詞。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="b6fb8-130">這類新增、編輯或刪除的限定詞適用于整個實例或類別定義。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="b6fb8-131">需求</span><span class="sxs-lookup"><span data-stu-id="b6fb8-131">Requirements</span></span>  
<span data-ttu-id="b6fb8-132">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6fb8-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6fb8-133">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="b6fb8-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b6fb8-134">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b6fb8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6fb8-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6fb8-135">See also</span></span>

- [<span data-ttu-id="b6fb8-136">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="b6fb8-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
