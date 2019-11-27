---
title: ISymUnmanagedWriter3::Commit 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
ms.openlocfilehash: 5985257a186839a297c245b23f093f0b18a798fe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438275"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="02196-102">ISymUnmanagedWriter3::Commit 方法</span><span class="sxs-lookup"><span data-stu-id="02196-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="02196-103">認可到目前為止寫入資料流程的變更。</span><span class="sxs-lookup"><span data-stu-id="02196-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02196-104">語法</span><span class="sxs-lookup"><span data-stu-id="02196-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="02196-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="02196-105">Return Value</span></span>  
 <span data-ttu-id="02196-106">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="02196-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02196-107">需求</span><span class="sxs-lookup"><span data-stu-id="02196-107">Requirements</span></span>  
 <span data-ttu-id="02196-108">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="02196-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02196-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02196-109">See also</span></span>

- [<span data-ttu-id="02196-110">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="02196-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
