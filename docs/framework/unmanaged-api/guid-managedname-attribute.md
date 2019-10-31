---
title: GUID_ManagedName 屬性
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
ms.openlocfilehash: 9d30c8fe71a0dfff7de9bb2f43b325cbb8016a23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123044"
---
# <a name="guid_managedname-attribute"></a><span data-ttu-id="65e24-102">GUID_ManagedName 屬性</span><span class="sxs-lookup"><span data-stu-id="65e24-102">GUID_ManagedName Attribute</span></span>
<span data-ttu-id="65e24-103">定義自訂介面屬性，指定元件物件模型（COM）程式庫的 managed 命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="65e24-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e24-104">語法</span><span class="sxs-lookup"><span data-stu-id="65e24-104">Syntax</span></span>  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a><span data-ttu-id="65e24-105">參數</span><span class="sxs-lookup"><span data-stu-id="65e24-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="65e24-106">程式庫的受控命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="65e24-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="65e24-107">定義</span><span class="sxs-lookup"><span data-stu-id="65e24-107">Definition</span></span>  
 <span data-ttu-id="65e24-108">`GUID_ManagedName` 定義于 Cor 中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="65e24-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="65e24-109">備註</span><span class="sxs-lookup"><span data-stu-id="65e24-109">Remarks</span></span>  
 <span data-ttu-id="65e24-110">自訂介面屬性會定義類型程式庫中物件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="65e24-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="65e24-111">使用 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> 或 <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType>，從屬性中取出受控名稱。</span><span class="sxs-lookup"><span data-stu-id="65e24-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="65e24-112">如需詳細資訊，請參閱 Visual C++ reference 檔中的[介面屬性](/cpp/windows/attributes/interface-attributes)。</span><span class="sxs-lookup"><span data-stu-id="65e24-112">For more information, see [Interface Attributes](/cpp/windows/attributes/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65e24-113">範例</span><span class="sxs-lookup"><span data-stu-id="65e24-113">Example</span></span>  
 <span data-ttu-id="65e24-114">下列範例顯示使用 `GUID_ManagedName` 屬性的程式庫定義。</span><span class="sxs-lookup"><span data-stu-id="65e24-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="65e24-115">需求</span><span class="sxs-lookup"><span data-stu-id="65e24-115">Requirements</span></span>  
 <span data-ttu-id="65e24-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="65e24-116">**Header:** Cor.h</span></span>
