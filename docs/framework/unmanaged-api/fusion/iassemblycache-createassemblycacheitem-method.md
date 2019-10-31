---
title: IAssemblyCache::CreateAssemblyCacheItem 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
ms.openlocfilehash: e3e50538bde8fe3509b49e3dbcb031875e6863e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127112"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a>IAssemblyCache::CreateAssemblyCacheItem 方法
取得新[IAssemblyCacheItem](iassemblycacheitem-interface.md)物件的參考。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwFlags`  
 在在融合 .idl 中定義的旗標。 支援下列值：  
  
- IASSEMBLYCACHE_INSTALL_FLAG_REFRESH （0x00000001）  
  
- IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH （0x00000002）  
  
 `pvReserved`  
 在保留以供未來擴充性之用。 `pvReserved` 必須是 null 參考。  
  
 `ppAsmItem`  
 脫銷傳回的 `IAssemblyCacheItem` 指標。  
  
 `pszAssemblyName`  
 [in，optional]Uncanonicalized，以逗號分隔的 `name=value` 組。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IAssemblyCache 介面](iassemblycache-interface.md)
- [IAssemblyCacheItem 介面](iassemblycacheitem-interface.md)
