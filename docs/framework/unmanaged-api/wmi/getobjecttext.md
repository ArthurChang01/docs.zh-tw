---
title: GetObjectText 函式（非受控 API 參考）
description: GetObjectText 函數會以 MOF 語法傳回物件的文字呈現。
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 412e1ad503fa0e0b4f813298c0ac96ae80098c06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102460"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="cfb07-103">GetObjectText 函式</span><span class="sxs-lookup"><span data-stu-id="cfb07-103">GetObjectText function</span></span>
<span data-ttu-id="cfb07-104">以受控物件格式（MOF）語法傳回物件的文字呈現。</span><span class="sxs-lookup"><span data-stu-id="cfb07-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="cfb07-105">語法</span><span class="sxs-lookup"><span data-stu-id="cfb07-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="cfb07-106">參數</span><span class="sxs-lookup"><span data-stu-id="cfb07-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="cfb07-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="cfb07-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="cfb07-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="cfb07-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="cfb07-109">在通常是0。</span><span class="sxs-lookup"><span data-stu-id="cfb07-109">[in] Normally 0.</span></span> <span data-ttu-id="cfb07-110">如果指定 `WBEM_FLAG_NO_FLAVORS` （或0x1），則會包含不含傳播或類別資訊的限定詞。</span><span class="sxs-lookup"><span data-stu-id="cfb07-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="cfb07-111">脫銷專案上 `null` 的指標。</span><span class="sxs-lookup"><span data-stu-id="cfb07-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="cfb07-112">傳回時，是新配置的 `BSTR`，其中包含物件的 MOF 語法呈現。</span><span class="sxs-lookup"><span data-stu-id="cfb07-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="cfb07-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="cfb07-113">Return value</span></span>

<span data-ttu-id="cfb07-114">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="cfb07-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cfb07-115">常數</span><span class="sxs-lookup"><span data-stu-id="cfb07-115">Constant</span></span>  |<span data-ttu-id="cfb07-116">值</span><span class="sxs-lookup"><span data-stu-id="cfb07-116">Value</span></span>  |<span data-ttu-id="cfb07-117">描述</span><span class="sxs-lookup"><span data-stu-id="cfb07-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="cfb07-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="cfb07-118">0x80041001</span></span> | <span data-ttu-id="cfb07-119">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="cfb07-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="cfb07-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="cfb07-120">0x80041008</span></span> | <span data-ttu-id="cfb07-121">參數無效。</span><span class="sxs-lookup"><span data-stu-id="cfb07-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="cfb07-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="cfb07-122">0x80041006</span></span> | <span data-ttu-id="cfb07-123">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="cfb07-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cfb07-124">0</span><span class="sxs-lookup"><span data-stu-id="cfb07-124">0</span></span> | <span data-ttu-id="cfb07-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="cfb07-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="cfb07-126">備註</span><span class="sxs-lookup"><span data-stu-id="cfb07-126">Remarks</span></span>

<span data-ttu-id="cfb07-127">此函式會包裝對[IWbemClassObject：： GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="cfb07-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="cfb07-128">傳回的 MOF 文字未包含物件的所有相關資訊，但 MOF 編譯器只有足夠的資訊可以重新建立原始物件。</span><span class="sxs-lookup"><span data-stu-id="cfb07-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="cfb07-129">例如，未包含任何傳播的限定詞或父類別屬性。</span><span class="sxs-lookup"><span data-stu-id="cfb07-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="cfb07-130">下列演算法是用來重建方法的參數文字：</span><span class="sxs-lookup"><span data-stu-id="cfb07-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="cfb07-131">參數是以其識別碼值的順序 resequenced。</span><span class="sxs-lookup"><span data-stu-id="cfb07-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="cfb07-132">指定為 `[in]` 和 `[out]` 的參數會結合成單一參數。</span><span class="sxs-lookup"><span data-stu-id="cfb07-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="cfb07-133">呼叫函式時，`pstrObjectText` 必須是 `null` 的指標;它不得指向方法呼叫之前的有效字串，因為不會解除配置指標。</span><span class="sxs-lookup"><span data-stu-id="cfb07-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="cfb07-134">需求</span><span class="sxs-lookup"><span data-stu-id="cfb07-134">Requirements</span></span>  
<span data-ttu-id="cfb07-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cfb07-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb07-136">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="cfb07-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cfb07-137">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cfb07-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb07-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="cfb07-138">See also</span></span>

- [<span data-ttu-id="cfb07-139">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="cfb07-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
