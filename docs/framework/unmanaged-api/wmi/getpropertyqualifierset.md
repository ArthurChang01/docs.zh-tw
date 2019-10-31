---
title: GetPropertyQualifierSet 函式（非受控 API 參考）
description: GetPropertyQualifierSet 函數會抓取屬性的限定詞集合。
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4133145c7bea1fb3c018d809b9fea3de38270619
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127461"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="f0d9f-103">GetPropertyQualifierSet 函式</span><span class="sxs-lookup"><span data-stu-id="f0d9f-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="f0d9f-104">擷取特定屬性的限定詞集合。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f0d9f-105">語法</span><span class="sxs-lookup"><span data-stu-id="f0d9f-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="f0d9f-106">參數</span><span class="sxs-lookup"><span data-stu-id="f0d9f-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="f0d9f-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="f0d9f-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="f0d9f-109">在屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-109">[in] The property  name.</span></span> <span data-ttu-id="f0d9f-110">`wszProperty` 必須指向有效的 `LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="f0d9f-111">脫銷接收介面指標，允許存取屬性的限定詞。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="f0d9f-112">`ppQualSet` 不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="f0d9f-113">如果發生錯誤，則不會傳回新的物件，而且指標會設定為指向 `null`。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f0d9f-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="f0d9f-114">Return value</span></span>

<span data-ttu-id="f0d9f-115">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="f0d9f-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f0d9f-116">常數</span><span class="sxs-lookup"><span data-stu-id="f0d9f-116">Constant</span></span>  |<span data-ttu-id="f0d9f-117">值</span><span class="sxs-lookup"><span data-stu-id="f0d9f-117">Value</span></span>  |<span data-ttu-id="f0d9f-118">描述</span><span class="sxs-lookup"><span data-stu-id="f0d9f-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="f0d9f-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f0d9f-119">0x80041001</span></span> | <span data-ttu-id="f0d9f-120">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f0d9f-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f0d9f-121">0x80041002</span></span> | <span data-ttu-id="f0d9f-122">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f0d9f-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f0d9f-123">0x80041006</span></span> | <span data-ttu-id="f0d9f-124">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f0d9f-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f0d9f-125">0x80041008</span></span> | <span data-ttu-id="f0d9f-126">參數為 `null`。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="f0d9f-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="f0d9f-127">0x80041030</span></span> | <span data-ttu-id="f0d9f-128">函數嘗試取得系統屬性的限定詞。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f0d9f-129">0</span><span class="sxs-lookup"><span data-stu-id="f0d9f-129">0</span></span> | <span data-ttu-id="f0d9f-130">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="f0d9f-131">備註</span><span class="sxs-lookup"><span data-stu-id="f0d9f-131">Remarks</span></span>

<span data-ttu-id="f0d9f-132">此函式會包裝對[IWbemClassObject：： GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="f0d9f-133">只有當目前的物件是 CIM 類別定義時，才支援呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="f0d9f-134">指向 CIM 實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標無法使用方法操作。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="f0d9f-135">因為每個方法都有自己的限定詞，所以[IWbemQualifierSet 指標](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)可讓呼叫者加入、編輯或刪除這些限定詞。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="f0d9f-136">由於系統屬性沒有限定詞，因此如果您嘗試取得系統屬性的[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標，此函式會傳回 `WBEM_E_SYSTEM_PROPERTY`。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0d9f-137">需求</span><span class="sxs-lookup"><span data-stu-id="f0d9f-137">Requirements</span></span>

<span data-ttu-id="f0d9f-138">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0d9f-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f0d9f-139">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="f0d9f-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="f0d9f-140">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d9f-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f0d9f-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0d9f-141">See also</span></span>

- [<span data-ttu-id="f0d9f-142">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="f0d9f-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
