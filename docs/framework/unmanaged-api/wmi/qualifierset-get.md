---
title: QualifierSet_Get 函式（非受控 API 參考）
description: QualifierSet_Get 函數會取得已命名的限定詞。
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: dc09cd30c43647fa00cccc1dc00da4f8de367e84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127268"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="a64a7-103">QualifierSet_Get 函式</span><span class="sxs-lookup"><span data-stu-id="a64a7-103">QualifierSet_Get function</span></span>
<span data-ttu-id="a64a7-104">取得指定的具名限定詞。</span><span class="sxs-lookup"><span data-stu-id="a64a7-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a64a7-105">語法</span><span class="sxs-lookup"><span data-stu-id="a64a7-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="a64a7-106">參數</span><span class="sxs-lookup"><span data-stu-id="a64a7-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="a64a7-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="a64a7-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="a64a7-108">在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="a64a7-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="a64a7-109">在要求其值的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="a64a7-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="a64a7-110">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="a64a7-110">[in] Reserved.</span></span> <span data-ttu-id="a64a7-111">這個參數必須是0。</span><span class="sxs-lookup"><span data-stu-id="a64a7-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="a64a7-112">脫銷如果成功，則為限定詞的正確類型和值。</span><span class="sxs-lookup"><span data-stu-id="a64a7-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="a64a7-113">如果函式失敗，`pVal` 所指向的 `VARIANT` 不會修改。</span><span class="sxs-lookup"><span data-stu-id="a64a7-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="a64a7-114">如果 `null`此參數，則會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="a64a7-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="a64a7-115">脫銷長的指標，接收所要求辨識符號的限定詞類別位。</span><span class="sxs-lookup"><span data-stu-id="a64a7-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="a64a7-116">如果不想要的是類別資訊，可以 `null`此參數。</span><span class="sxs-lookup"><span data-stu-id="a64a7-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="a64a7-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="a64a7-117">Return value</span></span>

<span data-ttu-id="a64a7-118">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="a64a7-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a64a7-119">常數</span><span class="sxs-lookup"><span data-stu-id="a64a7-119">Constant</span></span>  |<span data-ttu-id="a64a7-120">值</span><span class="sxs-lookup"><span data-stu-id="a64a7-120">Value</span></span>  |<span data-ttu-id="a64a7-121">描述</span><span class="sxs-lookup"><span data-stu-id="a64a7-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a64a7-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a64a7-122">0x80041008</span></span> | <span data-ttu-id="a64a7-123">參數無效。</span><span class="sxs-lookup"><span data-stu-id="a64a7-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a64a7-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a64a7-124">0x80041002</span></span> | <span data-ttu-id="a64a7-125">指定的限定詞不存在。</span><span class="sxs-lookup"><span data-stu-id="a64a7-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a64a7-126">0</span><span class="sxs-lookup"><span data-stu-id="a64a7-126">0</span></span> | <span data-ttu-id="a64a7-127">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a64a7-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a64a7-128">備註</span><span class="sxs-lookup"><span data-stu-id="a64a7-128">Remarks</span></span>

<span data-ttu-id="a64a7-129">此函式會包裝對[IWbemQualifierSet：： Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a64a7-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a64a7-130">需求</span><span class="sxs-lookup"><span data-stu-id="a64a7-130">Requirements</span></span>  
 <span data-ttu-id="a64a7-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a64a7-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a64a7-132">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="a64a7-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a64a7-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a64a7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a64a7-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="a64a7-134">See also</span></span>

- [<span data-ttu-id="a64a7-135">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="a64a7-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
