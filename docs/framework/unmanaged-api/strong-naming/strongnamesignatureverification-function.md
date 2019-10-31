---
title: StrongNameSignatureVerification 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
ms.openlocfilehash: 7dd61be008ba08ca2b28ae3e7e8ff6326f8a41d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129238"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification 函式
取得指出位於所指定路徑之組件資訊清單是否包含強式名稱簽章的值 (會根據指定的旗標驗證此值)。  
  
 這個函數已被取代。 請改用[ICLRStrongName：： StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszFilePath`  
 在要驗證之元件的可攜式可執行檔（.dll 或 .exe）的路徑。  
  
 `dwInFlags`  
 在用來修改驗證行為的旗標。 支援下列值：  
  
- `SN_INFLAG_FORCE_VER` （0x00000001）-即使需要覆寫登錄設定，也會強制執行驗證。  
  
- `SN_INFLAG_INSTALL` （0x00000002）-指定這是第一次驗證資訊清單。  
  
- `SN_INFLAG_ADMIN_ACCESS` （0x00000004）-指定快取只允許具有系統管理許可權的使用者進行存取。  
  
- `SN_INFLAG_USER_ACCESS` （0x00000008）-指定只有目前使用者可以存取元件。  
  
- `SN_INFLAG_ALL_ACCESS` （0x00000010）-指定快取不會提供存取限制的保證。  
  
- `SN_INFLAG_RUNTIME` （0x80000000）-保留供內部偵錯工具之用。  
  
 `pdwOutFlags`  
 脫銷旗標，指出是否已驗證強式名稱簽章。 支援下列值：  
  
- `SN_OUTFLAG_WAS_VERIFIED` （0x00000001）-此值設定為 `false`，指定驗證是因為登錄設定而成功。  
  
## <a name="return-value"></a>傳回值  
 如果驗證成功，則 `true`;否則，`false`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Stackexchange.redis.strongname。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [StrongNameSignatureVerification 方法](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx 方法](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName 介面](../hosting/iclrstrongname-interface.md)
