---
title: ISymUnmanagedReader::GetDocument 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
ms.openlocfilehash: 1fcb885b6e19457065c2ca9971f068b42f97147d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448339"
---
# <a name="isymunmanagedreadergetdocument-method"></a>ISymUnmanagedReader::GetDocument 方法
Finds a document. The document language, vendor, and type are optional.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `url`  
 [in] The URL that identifies the document.  
  
 `language`  
 [in] The document language. 這是選擇性參數。  
  
 `languageVendor`  
 [in] The identity of the vendor for the document language. 這是選擇性參數。  
  
 `documentType`  
 [in] The type of the document. 這是選擇性參數。  
  
 `pRetVal`  
 [out] A pointer to the returned interface.  
  
## <a name="return-value"></a>傳回值  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>需求  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>請參閱

- [ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
