---
title: CorSetENC 列舉
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 39f72e670ddc700c257f50f6bad6fab702ec21b6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432768"
---
# <a name="corsetenc-enumeration"></a>CorSetENC 列舉
包含值，可用來在中繼資料產生期間影響行為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`MDSetENCOn`|已經過時：|  
|`MDSetENCOff`|已經過時：|  
|`MDUpdateENC`|表示中繼資料可以更新，而無法移動權杖。|  
|`MDUpdateFull`|表示權杖可在更新期間移動。|  
|`MDUpdateExtension`|指出更新只能包含新增專案。 無法移動權杖。|  
|`MDUpdateIncremental`|表示編譯是累加的。|  
|`MDUpdateDelta`|指出只應儲存已變更的中繼資料。|  
|`MDUpdateMask`|包括 `MDUpdateENC`、`MDUpdateFull` 和 `MDUpdateIncremental`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
