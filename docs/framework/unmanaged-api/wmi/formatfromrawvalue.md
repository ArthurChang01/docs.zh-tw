---
title: FormatFromRawValue 函式（非受控 API 參考）
description: FormatFromRawValue 函數會將原始效能資料轉換成指定的格式。
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5097cfe43ae785461a1e2af1217bcbd5e8c4b79c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120292"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="4c72e-103">FormatFromRawValue 函式</span><span class="sxs-lookup"><span data-stu-id="4c72e-103">FormatFromRawValue function</span></span>
<span data-ttu-id="4c72e-104">將一個原始效能資料值轉換為指定的格式，或轉換為兩個原始效能資料值 (若格式轉換是以時間為基礎)。</span><span class="sxs-lookup"><span data-stu-id="4c72e-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="4c72e-105">語法</span><span class="sxs-lookup"><span data-stu-id="4c72e-105">Syntax</span></span>

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```

## <a name="parameters"></a><span data-ttu-id="4c72e-106">參數</span><span class="sxs-lookup"><span data-stu-id="4c72e-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="4c72e-107">在計數器類型。</span><span class="sxs-lookup"><span data-stu-id="4c72e-107">[in] The counter type.</span></span> <span data-ttu-id="4c72e-108">如需計數器類型的清單，請參閱[WMI 效能計數器類型](/windows/desktop/WmiSdk/wmi-performance-counter-types)。</span><span class="sxs-lookup"><span data-stu-id="4c72e-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="4c72e-109">`dwCounterType` 可以是任何計數器類型，但 `PERF_LARGE_RAW_FRACTION` 和 `PERF_LARGE_RAW_BASE`除外。</span><span class="sxs-lookup"><span data-stu-id="4c72e-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="4c72e-110">在要轉換原始效能資料的格式。</span><span class="sxs-lookup"><span data-stu-id="4c72e-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="4c72e-111">它可以是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="4c72e-111">It can be one of the following values:</span></span>

|<span data-ttu-id="4c72e-112">常數</span><span class="sxs-lookup"><span data-stu-id="4c72e-112">Constant</span></span>  |<span data-ttu-id="4c72e-113">值</span><span class="sxs-lookup"><span data-stu-id="4c72e-113">Value</span></span>  |<span data-ttu-id="4c72e-114">描述</span><span class="sxs-lookup"><span data-stu-id="4c72e-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="4c72e-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="4c72e-115">0x00000200</span></span> | <span data-ttu-id="4c72e-116">傳回計算的值做為雙精確度浮點值。</span><span class="sxs-lookup"><span data-stu-id="4c72e-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="4c72e-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="4c72e-117">0x00000400</span></span> | <span data-ttu-id="4c72e-118">以64位整數傳回計算的值。</span><span class="sxs-lookup"><span data-stu-id="4c72e-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="4c72e-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="4c72e-119">0x00000100</span></span> | <span data-ttu-id="4c72e-120">以32位整數傳回計算的值。</span><span class="sxs-lookup"><span data-stu-id="4c72e-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="4c72e-121">先前的其中一個值可以使用下列其中一個調整旗標來 ORed：</span><span class="sxs-lookup"><span data-stu-id="4c72e-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="4c72e-122">常數</span><span class="sxs-lookup"><span data-stu-id="4c72e-122">Constant</span></span>  |<span data-ttu-id="4c72e-123">值</span><span class="sxs-lookup"><span data-stu-id="4c72e-123">Value</span></span>  |<span data-ttu-id="4c72e-124">描述</span><span class="sxs-lookup"><span data-stu-id="4c72e-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="4c72e-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="4c72e-125">0x00001000</span></span> | <span data-ttu-id="4c72e-126">請勿套用計數器的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="4c72e-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="4c72e-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="4c72e-127">0x00002000</span></span> | <span data-ttu-id="4c72e-128">將最後一個值乘以1000。</span><span class="sxs-lookup"><span data-stu-id="4c72e-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="4c72e-129">在如果需要格式轉換，則為時間基底的指標。</span><span class="sxs-lookup"><span data-stu-id="4c72e-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="4c72e-130">如果格式轉換不需要時間基底資訊，則會忽略這個參數的值。</span><span class="sxs-lookup"><span data-stu-id="4c72e-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="4c72e-131">`pRawValue1`\ [in] 代表原始效能值之[`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter)結構的指標。</span><span class="sxs-lookup"><span data-stu-id="4c72e-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="4c72e-132">在[`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter)結構的指標，表示第二個原始的效能值。</span><span class="sxs-lookup"><span data-stu-id="4c72e-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="4c72e-133">如果不需要第二個原始效能值，則應 `null`此參數。</span><span class="sxs-lookup"><span data-stu-id="4c72e-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="4c72e-134">脫銷接收格式化效能值之[`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue)結構的指標。</span><span class="sxs-lookup"><span data-stu-id="4c72e-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c72e-135">傳回值</span><span class="sxs-lookup"><span data-stu-id="4c72e-135">Return value</span></span>

<span data-ttu-id="4c72e-136">此函式會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="4c72e-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="4c72e-137">常數</span><span class="sxs-lookup"><span data-stu-id="4c72e-137">Constant</span></span>  |<span data-ttu-id="4c72e-138">值</span><span class="sxs-lookup"><span data-stu-id="4c72e-138">Value</span></span>  |<span data-ttu-id="4c72e-139">描述</span><span class="sxs-lookup"><span data-stu-id="4c72e-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="4c72e-140">0</span><span class="sxs-lookup"><span data-stu-id="4c72e-140">0</span></span> | <span data-ttu-id="4c72e-141">函數呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4c72e-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="4c72e-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="4c72e-142">0xC0000BBD</span></span> | <span data-ttu-id="4c72e-143">缺少必要的引數或其不正確。</span><span class="sxs-lookup"><span data-stu-id="4c72e-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="4c72e-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="4c72e-144">0xC0000BBC</span></span> | <span data-ttu-id="4c72e-145">控制碼不是有效的 PDH 物件。</span><span class="sxs-lookup"><span data-stu-id="4c72e-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4c72e-146">備註</span><span class="sxs-lookup"><span data-stu-id="4c72e-146">Remarks</span></span>

<span data-ttu-id="4c72e-147">此函式會包裝對[FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4c72e-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c72e-148">需求</span><span class="sxs-lookup"><span data-stu-id="4c72e-148">Requirements</span></span>

 <span data-ttu-id="4c72e-149">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c72e-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="4c72e-150">連結**庫：** PerfCounter .dll</span><span class="sxs-lookup"><span data-stu-id="4c72e-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="4c72e-151">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4c72e-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4c72e-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c72e-152">See also</span></span>

- [<span data-ttu-id="4c72e-153">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="4c72e-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
