---
title: QualifierSet_GetNames 函式（非受控 API 參考）
description: QualifierSet_GetNames 函數會從物件或屬性抓取限定詞的名稱。
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141701"
---
# <a name="qualifierset_getnames-function"></a>QualifierSet_GetNames 函式

抓取目前物件或屬性中可用的所有限定詞或特定限定詞的名稱。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>參數

`vFunc`\
在未使用此參數。

`ptr`\
在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。

`lFlags`\
在下列其中一個旗標或值，指定要包含在列舉中的名稱。

|常數  |值  |描述  |
|---------|---------|---------|
|  | 0 | 傳回所有限定詞的名稱。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 只傳回目前屬性或物件的特定限定詞名稱。 <br/> 對於屬性：只傳回屬性的特定限定詞（包括覆寫），而不是從類別定義傳播的限定詞。 <br/> 針對實例：只傳回實例特定的限定詞名稱。 <br/> 針對類別：只傳回所要衍生之類別的特定限定詞。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 只傳回從另一個物件傳播的限定詞名稱。 <br/> 對於屬性：只傳回從類別定義傳播到這個屬性的限定詞，而不是來自屬性本身的辨識符號。 <br/> 針對實例：只傳回從類別定義傳播的限定詞。 <br/> 針對類別：只傳回繼承自父類別的限定詞名稱。 |

`pstrNames`\
脫銷包含所要求名稱的新 `SAFEARRAY`。 陣列可以有0個元素。 如果發生錯誤，則不會傳回新的 `SAFEARRAY`。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可以開始新的列舉。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemQualifierSet：： GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames)方法的呼叫。

抓取限定詞名稱之後，您就可以藉由呼叫[QualifierSet_Get](qualifierset-get.md)函數，依名稱存取每個限定詞。

如果指定的物件沒有任何限定詞，則不會發生錯誤，因此，`pstrNames` 中的字串數目可以是0，即使函式傳回 `WBEM_S_NO_ERROR`也一樣。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils .idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
