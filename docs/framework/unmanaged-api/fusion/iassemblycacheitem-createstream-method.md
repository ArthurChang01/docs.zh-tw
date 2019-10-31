---
title: IAssemblyCacheItem::CreateStream 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 0660621f465f2ba3610e06bd1df38baa1bc5c907
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134477"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="9e737-102">IAssemblyCacheItem::CreateStream 方法</span><span class="sxs-lookup"><span data-stu-id="9e737-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="9e737-103">建立具有指定之名稱和格式的資料流程。</span><span class="sxs-lookup"><span data-stu-id="9e737-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e737-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e737-104">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="9e737-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e737-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="9e737-106">在在融合 .idl 中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="9e737-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="9e737-107">在要建立之資料流程的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e737-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="9e737-108">在要進行資料流程處理之檔案的格式。</span><span class="sxs-lookup"><span data-stu-id="9e737-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="9e737-109">在在融合 .idl 中定義的格式特定旗標。</span><span class="sxs-lookup"><span data-stu-id="9e737-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="9e737-110">脫銷傳回之[IStream](/windows/desktop/api/objidl/nn-objidl-istream)實例位址的指標。</span><span class="sxs-lookup"><span data-stu-id="9e737-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="9e737-111">[in，optional]`ppIStream`所參考的資料流程大小上限。</span><span class="sxs-lookup"><span data-stu-id="9e737-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e737-112">需求</span><span class="sxs-lookup"><span data-stu-id="9e737-112">Requirements</span></span>

<span data-ttu-id="9e737-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e737-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9e737-114">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="9e737-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="9e737-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e737-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9e737-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e737-116">See also</span></span>

- [<span data-ttu-id="9e737-117">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="9e737-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
