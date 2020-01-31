---
title: CreateCoreClrDebugTarget 函式
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: a7fed8cb70785f0ccfcadf1e16181db303ac98e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789188"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget 函式
建立連接至遠端電腦上執行的偵錯工具 proxy，並傳回可用來查詢執行中進程和載入的執行時間在遠端電腦上的[ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwAddress`  
 [in] 遠端目標電腦的 IPv4 位址。  
  
 `ppTarget`  
 脫銷將建立之[ICoreClrDebugTarget](icoreclrdebugtarget-interface.md)物件指標的指標。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。  
  
 E_OUTOFMEMORY  
 無法為 `ppTarget` 配置足夠的記憶體。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 其他失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CoreClrRemoteDebuggingInterfaces。h  
  
 連結**庫：** mscordbi_macx86 .dll  
  
 **.NET Framework 版本：** 3.5 SP1
