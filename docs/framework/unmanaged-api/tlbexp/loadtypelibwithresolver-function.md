---
title: LoadTypeLibWithResolver 函式
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
ms.openlocfilehash: 82fa0903474ee04b767fd9c68812efe7f0cc4fa0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124165"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver 函式
載入類型程式庫，並使用提供的[ITypeLibResolver 介面](itypelibresolver-interface.md)來解析任何內部參考的類型程式庫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>參數  
 `szFile`  
 在類型程式庫的檔案路徑。  
  
 `regkind`  
 在[REGKIND 列舉](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind)旗標，可控制類型程式庫的註冊方式。 其可能的值為：  
  
- `REGKIND_DEFAULT`：使用預設的註冊行為。  
  
- `REGKIND_REGISTER`：註冊此類型程式庫。  
  
- `REGKIND_NONE`：不要註冊此類型程式庫。  
  
 `pTlbResolver`  
 在[ITypeLibResolver 介面](itypelibresolver-interface.md)之執行的指標。  
  
 `pptlib`  
 脫銷正在載入之類型程式庫的參考。  
  
## <a name="return-value"></a>傳回值  
 下表所列的其中一個 HRESULT 值。  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|記憶體不足。|  
|`E_POINTER`|一或多個指標無效。|  
|`E_INVALIDARG`|一或多個引數無效。|  
|`TYPE_E_IOERROR`|函數無法寫入檔案。|  
|`TYPE_E_REGISTRYACCESS`|無法開啟系統註冊資料庫。|  
|`TYPE_E_INVALIDSTATE`|無法開啟類型程式庫。|  
|`TYPE_E_CANTLOADLIBRARY`|無法載入類型程式庫或 DLL。|  
  
## <a name="remarks"></a>備註  
 [Tlbexp.exe （類型程式庫匯出工具）](../../tools/tlbexp-exe-type-library-exporter.md)會在元件對類型程式庫轉換過程中呼叫 `LoadTypeLibWithResolver` 函式。  
  
 此函式會以最少的登錄存取權來載入指定的類型程式庫。 接著，函式會檢查類型程式庫中是否有內部參考的類型程式庫，其中每一個都必須載入並加入至父類型程式庫。  
  
 在可以載入參考的類型程式庫之前，必須先將其參考檔案路徑解析成完整的檔案路徑。 這項作業是透過[ITypeLibResolver 介面](itypelibresolver-interface.md)所提供的[ResolveTypeLib 方法](resolvetypelib-method.md)來完成，這會在 `pTlbResolver` 參數中傳遞。  
  
 已知參考類型程式庫的完整檔案路徑時，`LoadTypeLibWithResolver` 函式會載入參考的類型程式庫，並將其加入至父類型程式庫，並建立組合的主要類型程式庫。  
  
 在函式解析並載入所有內部參考的類型程式庫之後，它會傳回 `pptlib` 參數中主要已解析之類型程式庫的參考。  
  
 `LoadTypeLibWithResolver` 函式通常是由[tlbexp.exe （類型程式庫匯出工具）](../../tools/tlbexp-exe-type-library-exporter.md)所呼叫，這會在 `pTlbResolver` 參數中提供自己的內部[ITypeLibResolver 介面](itypelibresolver-interface.md)實作為。  
  
 如果您直接呼叫 `LoadTypeLibWithResolver`，就必須提供自己的[ITypeLibResolver 介面](itypelibresolver-interface.md)執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** TlbRef。h  
  
 連結**庫：** TlbRef .lib  
  
 **.NET Framework 版本：** 3.5、3.0、2。0  
  
## <a name="see-also"></a>請參閱

- [Tlbexp Helper 函式](index.md)
- [LoadTypeLibEx 函式](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
