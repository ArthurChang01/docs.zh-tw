---
title: BeginEnumeration 函式（非受控 API 參考）
description: BeginEnumeration 函數會將枚舉器重設為列舉的開頭
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 9e467234a45ae702a5b77a5f0fa8b75d4ff03c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124137"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="a0efc-103">BeginEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="a0efc-103">BeginEnumeration function</span></span>
<span data-ttu-id="a0efc-104">將列舉值重設回列舉的開頭。</span><span class="sxs-lookup"><span data-stu-id="a0efc-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a0efc-105">語法</span><span class="sxs-lookup"><span data-stu-id="a0efc-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="a0efc-106">參數</span><span class="sxs-lookup"><span data-stu-id="a0efc-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a0efc-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="a0efc-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a0efc-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="a0efc-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="a0efc-109">在在 [[備註](#remarks)] 區段中所描述的旗標或值的位元組合，可控制列舉中包含的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a0efc-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="a0efc-110">Return value</span></span>

<span data-ttu-id="a0efc-111">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="a0efc-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a0efc-112">常數</span><span class="sxs-lookup"><span data-stu-id="a0efc-112">Constant</span></span>  |<span data-ttu-id="a0efc-113">值</span><span class="sxs-lookup"><span data-stu-id="a0efc-113">Value</span></span>  |<span data-ttu-id="a0efc-114">描述</span><span class="sxs-lookup"><span data-stu-id="a0efc-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a0efc-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a0efc-115">0x80041008</span></span> | <span data-ttu-id="a0efc-116">`lEnumFlags` 中的旗標組合無效，或指定了不正確引數。</span><span class="sxs-lookup"><span data-stu-id="a0efc-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="a0efc-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="a0efc-117">0x8004101d</span></span> | <span data-ttu-id="a0efc-118">對 `BeginEnumeration` 進行第二次呼叫，而不需要呼叫[`EndEnumeration`](endenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="a0efc-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a0efc-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a0efc-119">0x80041006</span></span> | <span data-ttu-id="a0efc-120">沒有足夠的記憶體可以開始新的列舉。</span><span class="sxs-lookup"><span data-stu-id="a0efc-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a0efc-121">0</span><span class="sxs-lookup"><span data-stu-id="a0efc-121">0</span></span> | <span data-ttu-id="a0efc-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a0efc-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a0efc-123">備註</span><span class="sxs-lookup"><span data-stu-id="a0efc-123">Remarks</span></span>

<span data-ttu-id="a0efc-124">此函式會包裝對[IWbemClassObject：： BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a0efc-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="a0efc-125">可以當做 `lEnumFlags` 引數傳遞的旗標會定義在*WbemCli*標頭檔中，或者您可以在程式碼中將它們定義為常數。</span><span class="sxs-lookup"><span data-stu-id="a0efc-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="a0efc-126">您可以將每個群組中的一個旗標與任何其他群組中的任何旗標結合。</span><span class="sxs-lookup"><span data-stu-id="a0efc-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="a0efc-127">不過，來自相同群組的旗標是互斥的。</span><span class="sxs-lookup"><span data-stu-id="a0efc-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="a0efc-128">**群組1**</span><span class="sxs-lookup"><span data-stu-id="a0efc-128">**Group 1**</span></span>

|<span data-ttu-id="a0efc-129">常數</span><span class="sxs-lookup"><span data-stu-id="a0efc-129">Constant</span></span>  |<span data-ttu-id="a0efc-130">值</span><span class="sxs-lookup"><span data-stu-id="a0efc-130">Value</span></span>  |<span data-ttu-id="a0efc-131">描述</span><span class="sxs-lookup"><span data-stu-id="a0efc-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="a0efc-132">0x4</span><span class="sxs-lookup"><span data-stu-id="a0efc-132">0x4</span></span> | <span data-ttu-id="a0efc-133">包含僅構成金鑰的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="a0efc-134">0x8</span><span class="sxs-lookup"><span data-stu-id="a0efc-134">0x8</span></span> | <span data-ttu-id="a0efc-135">包含僅為物件參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="a0efc-136">**群組2**</span><span class="sxs-lookup"><span data-stu-id="a0efc-136">**Group 2**</span></span>

<span data-ttu-id="a0efc-137">常數</span><span class="sxs-lookup"><span data-stu-id="a0efc-137">Constant</span></span>  |<span data-ttu-id="a0efc-138">值</span><span class="sxs-lookup"><span data-stu-id="a0efc-138">Value</span></span>  |<span data-ttu-id="a0efc-139">描述</span><span class="sxs-lookup"><span data-stu-id="a0efc-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="a0efc-140">0x30</span><span class="sxs-lookup"><span data-stu-id="a0efc-140">0x30</span></span> | <span data-ttu-id="a0efc-141">僅將列舉限制為系統屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="a0efc-142">0x40</span><span class="sxs-lookup"><span data-stu-id="a0efc-142">0x40</span></span> | <span data-ttu-id="a0efc-143">包含本機和傳播的屬性，但從列舉中排除系統屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="a0efc-144">針對類別：</span><span class="sxs-lookup"><span data-stu-id="a0efc-144">For classes:</span></span>

<span data-ttu-id="a0efc-145">常數</span><span class="sxs-lookup"><span data-stu-id="a0efc-145">Constant</span></span>  |<span data-ttu-id="a0efc-146">值</span><span class="sxs-lookup"><span data-stu-id="a0efc-146">Value</span></span>  |<span data-ttu-id="a0efc-147">描述</span><span class="sxs-lookup"><span data-stu-id="a0efc-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="a0efc-148">0x100</span><span class="sxs-lookup"><span data-stu-id="a0efc-148">0x100</span></span> | <span data-ttu-id="a0efc-149">將列舉限制為在類別定義中覆寫的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="a0efc-150">0x100</span><span class="sxs-lookup"><span data-stu-id="a0efc-150">0x100</span></span> | <span data-ttu-id="a0efc-151">將列舉限制為在目前類別定義中覆寫的屬性，以及加入至類別中定義的新屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="a0efc-152">0x300</span><span class="sxs-lookup"><span data-stu-id="a0efc-152">0x300</span></span> | <span data-ttu-id="a0efc-153">要針對 `lEnumFlags` 值套用的遮罩（而不是旗標），以檢查是否已設定 `WBEM_FLAG_CLASS_OVERRIDES_ONLY` 或 `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`。</span><span class="sxs-lookup"><span data-stu-id="a0efc-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="a0efc-154">0x10</span><span class="sxs-lookup"><span data-stu-id="a0efc-154">0x10</span></span> | <span data-ttu-id="a0efc-155">將列舉限制為在類別本身中定義或修改的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="a0efc-156">0x20</span><span class="sxs-lookup"><span data-stu-id="a0efc-156">0x20</span></span> | <span data-ttu-id="a0efc-157">將列舉限制為繼承自基類的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="a0efc-158">針對實例：</span><span class="sxs-lookup"><span data-stu-id="a0efc-158">For instances:</span></span>

<span data-ttu-id="a0efc-159">常數</span><span class="sxs-lookup"><span data-stu-id="a0efc-159">Constant</span></span>  |<span data-ttu-id="a0efc-160">值</span><span class="sxs-lookup"><span data-stu-id="a0efc-160">Value</span></span>  |<span data-ttu-id="a0efc-161">描述</span><span class="sxs-lookup"><span data-stu-id="a0efc-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="a0efc-162">0x10</span><span class="sxs-lookup"><span data-stu-id="a0efc-162">0x10</span></span> | <span data-ttu-id="a0efc-163">將列舉限制為在類別本身中定義或修改的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="a0efc-164">0x20</span><span class="sxs-lookup"><span data-stu-id="a0efc-164">0x20</span></span> | <span data-ttu-id="a0efc-165">將列舉限制為繼承自基類的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0efc-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a0efc-166">需求</span><span class="sxs-lookup"><span data-stu-id="a0efc-166">Requirements</span></span>  
 <span data-ttu-id="a0efc-167">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0efc-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0efc-168">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="a0efc-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a0efc-169">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a0efc-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0efc-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0efc-170">See also</span></span>

- [<span data-ttu-id="a0efc-171">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="a0efc-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
