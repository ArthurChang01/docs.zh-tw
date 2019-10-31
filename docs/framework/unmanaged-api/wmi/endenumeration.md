---
title: EndEnumeration 函式（非受控 API 參考）
description: EndEnumeration 函數會終止列舉。
ms.date: 11/06/2017
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b9fd1f094c8fb56c94421a07437aa25a3549c487
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132050"
---
# <a name="endenumeration-function"></a><span data-ttu-id="22cd4-103">EndEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="22cd4-103">EndEnumeration function</span></span>

<span data-ttu-id="22cd4-104">結束通話[BeginEnumeration 函數](beginenumeration.md)所啟動的列舉序列。</span><span class="sxs-lookup"><span data-stu-id="22cd4-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="22cd4-105">語法</span><span class="sxs-lookup"><span data-stu-id="22cd4-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="22cd4-106">參數</span><span class="sxs-lookup"><span data-stu-id="22cd4-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="22cd4-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="22cd4-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="22cd4-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="22cd4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="22cd4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="22cd4-109">Return value</span></span>

<span data-ttu-id="22cd4-110">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="22cd4-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="22cd4-111">常數</span><span class="sxs-lookup"><span data-stu-id="22cd4-111">Constant</span></span>  |<span data-ttu-id="22cd4-112">值</span><span class="sxs-lookup"><span data-stu-id="22cd4-112">Value</span></span>  |<span data-ttu-id="22cd4-113">描述</span><span class="sxs-lookup"><span data-stu-id="22cd4-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="22cd4-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="22cd4-114">0x80041001</span></span> | <span data-ttu-id="22cd4-115">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="22cd4-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="22cd4-116">0</span><span class="sxs-lookup"><span data-stu-id="22cd4-116">0</span></span> | <span data-ttu-id="22cd4-117">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="22cd4-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="22cd4-118">備註</span><span class="sxs-lookup"><span data-stu-id="22cd4-118">Remarks</span></span>

<span data-ttu-id="22cd4-119">此函式會包裝對[IWbemClassObject：： EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="22cd4-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="22cd4-120">不需要呼叫 `EndEnumeration` 函式，但建議您這樣做，因為它會釋放與列舉相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="22cd4-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="22cd4-121">不過，系統會在下一個列舉啟動或釋放物件時，自動解除配置資源。</span><span class="sxs-lookup"><span data-stu-id="22cd4-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="22cd4-122">需求</span><span class="sxs-lookup"><span data-stu-id="22cd4-122">Requirements</span></span>

<span data-ttu-id="22cd4-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22cd4-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="22cd4-124">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="22cd4-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="22cd4-125">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="22cd4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="22cd4-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="22cd4-126">See also</span></span>

- [<span data-ttu-id="22cd4-127">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="22cd4-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
