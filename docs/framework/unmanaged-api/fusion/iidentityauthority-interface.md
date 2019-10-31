---
title: IIdentityAuthority 介面
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
ms.openlocfilehash: 3e2d2335e37ced9139ea44092f10b19566894681
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127085"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="527fc-102">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="527fc-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="527fc-103">管理程式碼物件的識別索引鍵。</span><span class="sxs-lookup"><span data-stu-id="527fc-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="527fc-104">方法</span><span class="sxs-lookup"><span data-stu-id="527fc-104">Methods</span></span>

|<span data-ttu-id="527fc-105">方法</span><span class="sxs-lookup"><span data-stu-id="527fc-105">Method</span></span>|<span data-ttu-id="527fc-106">描述</span><span class="sxs-lookup"><span data-stu-id="527fc-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="527fc-107">取得值，指出兩個指定的[IDefinitionIdentity](idefinitionidentity-interface.md)實例是否相等。</span><span class="sxs-lookup"><span data-stu-id="527fc-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="527fc-108">取得值，指出兩個指定的[IReferenceIdentity](ireferenceidentity-interface.md)實例是否相等。</span><span class="sxs-lookup"><span data-stu-id="527fc-108">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="527fc-109">取得值，指出兩個指定的字串定義識別表示是否相等。</span><span class="sxs-lookup"><span data-stu-id="527fc-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="527fc-110">取得值，指出兩個指定的字串參考身分識別表示是否相等。</span><span class="sxs-lookup"><span data-stu-id="527fc-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="527fc-111">取得新 `IDefinitionIdentity` 實例的指標，表示目前範圍中的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="527fc-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="527fc-112">取得新 `IReferenceIdentity` 實例的指標，表示目前範圍中的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="527fc-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="527fc-113">取得指定之 `IDefinitionIdentity`的格式化字串版本。</span><span class="sxs-lookup"><span data-stu-id="527fc-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="527fc-114">使用指定之 `IDefinitionIdentity`的字串版本，填滿指定的寬字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="527fc-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="527fc-115">取得值，指出指定的 `IDefinitionIdentity` 和 `IReferenceIdentity` 實例是否參考相同的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="527fc-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="527fc-116">取得值，指出指定的字串是否參考相同的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="527fc-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="527fc-117">取得指定之 `IDefinitionIdentity`的新建立字串索引鍵的指標。</span><span class="sxs-lookup"><span data-stu-id="527fc-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="527fc-118">取得指定之 `IReferenceIdentity`的新建立字串索引鍵的指標。</span><span class="sxs-lookup"><span data-stu-id="527fc-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="527fc-119">取得指定之 `IDefinitionIdentity`的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="527fc-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="527fc-120">取得指定之 `IReferenceIdentity`的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="527fc-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="527fc-121">取得指定之 `IReferenceIdentity`的格式化字串版本。</span><span class="sxs-lookup"><span data-stu-id="527fc-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="527fc-122">使用指定之 `IReferenceIdentity`的字串版本，填滿指定的寬字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="527fc-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="527fc-123">取得從指定的格式化字串產生之 `IDefinitionIdentity` 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="527fc-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="527fc-124">取得從指定的格式化字串產生之 `IReferenceIdentity` 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="527fc-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="527fc-125">需求</span><span class="sxs-lookup"><span data-stu-id="527fc-125">Requirements</span></span>

<span data-ttu-id="527fc-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="527fc-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="527fc-127">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="527fc-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="527fc-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="527fc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="527fc-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="527fc-129">See also</span></span>

- [<span data-ttu-id="527fc-130">融合介面</span><span class="sxs-lookup"><span data-stu-id="527fc-130">Fusion Interfaces</span></span>](fusion-interfaces.md)
