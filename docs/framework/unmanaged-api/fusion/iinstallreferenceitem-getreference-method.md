---
title: IInstallReferenceItem::GetReference 方法
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
ms.openlocfilehash: 014bd4f2b12c84790065f76a67765aaf35e8b2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131686"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference 方法
取得這個[IInstallReferenceItem](iinstallreferenceitem-interface.md)物件所表示之[FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md)結構的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppRefData`  
 脫銷傳回的 `FUSION_INSTALL_REFERENCE` 指標。  
  
 `dwFlags`  
 在保留以供未來擴充性之用。 `dwFlags` 必須是0（零）。  
  
 `pvReserved`  
 在保留以供未來擴充性之用。 `pvReserved` 必須是 null 參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IInstallReferenceItem 介面](iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE 結構](fusion-install-reference-structure.md)
