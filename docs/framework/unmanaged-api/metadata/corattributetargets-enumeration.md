---
title: CorAttributeTargets 列舉
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 5f83cb96e39b257a1d35786130cd5ed31d071de7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443878"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets 列舉
指定有效套用屬性的應用程式項目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =   
        catAssembly | catModule | catClass | catStruct |   
        catEnum | catConstructor | catMethod | catProperty |   
        catField | catEvent | catInterface | catParameter |   
        catDelegate | catGenericParameter,  
  
    catClassMembers        =   
        catClass | catStruct | catEnum | catConstructor |   
        catMethod | catProperty | catField | catEvent |   
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`catAssembly`|屬性可以套用至元件。|  
|`catModule`|屬性可以套用至可移植的可執行檔（.dll 或 .exe）模組。|  
|`catClass`|屬性可以套用至類別。|  
|`catStruct`|屬性可以套用至結構;也就是實值型別。|  
|`catEnum`|屬性可以套用至列舉。|  
|`catConstructor`|屬性可以套用至函式。|  
|`catMethod`|屬性可以套用至方法。|  
|`catProperty`|屬性可以套用至屬性。|  
|`catField`|屬性可以套用至欄位。|  
|`catEvent`|屬性可以套用至事件。|  
|`catInterface`|屬性可以套用至介面。|  
|`catParameter`|屬性可以套用至參數。|  
|`catDelegate`|屬性可以套用至委派。|  
|`catGenericParameter`|屬性可以套用至泛型參數。|  
|`catAll`|屬性可以套用至任何應用程式元素。|  
|`catClassMembers`|屬性可以套用至類別的成員。|  
  
## <a name="remarks"></a>備註  
 `CorAttributeTargets` 的列舉值可以與位 OR 運算結合，以取得慣用的組合。  
  
 `CorAttributeTargets` 等同于 managed <xref:System.AttributeTargets?displayProperty=nameWithType> 列舉。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
