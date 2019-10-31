---
title: IAppIdAuthority 介面
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
ms.openlocfilehash: 004e4f70e3385e7a71c356cce38e64d0253dcfa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127126"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority 介面
提供方法，以產生並比較應用程式識別和參考的索引鍵。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|取得值，指出兩個指定的[IDefinitionAppId](idefinitionappid-interface.md)實例是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION 來忽略其各自的版本資訊。|  
|`IAppIdAuthority::AreReferencesEqual`|取得值，指出兩個指定的[IReferenceAppId](ireferenceappid-interface.md)實例是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION 來忽略其各自的版本資訊。|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|取得值，指出兩個指定的字串定義是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION 來忽略其各自的版本資訊。|  
|`IAppIdAuthority::AreTextualReferencesEqual`|取得值，指出兩個指定的字串參考是否相等。 您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION 來忽略其各自的版本資訊。|  
|`IAppIdAuthority::CreateDefinition`|取得新產生之 `IDefinitionAppId` 實例的介面指標，表示目前範圍中的元件。|  
|`IAppIdAuthority::CreateReference`|取得新建立之 `IReferenceAppId` 的介面指標，表示目前範圍中的元件。|  
|`IAppIdAuthority::DefinitionToText`|使用指定的旗標值，取得指定之 `IDefinitionAppId`的字串版本。|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|取得值，指出指定的 `IDefinitionAppId` 和 `IReferenceAppId` 是否代表相同的元件。|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|取得值，指出指定的定義字串和參考字串是否代表相同的元件。|  
|`IAppIdAuthority::GenerateDefinitionKey`|取得表示指定 `IDefinitionAppId` 實例的字串索引鍵。|  
|`IAppIdAuthority::GenerateReferenceKey`|取得表示指定 `IReferenceAppId` 實例的字串索引鍵。|  
|`IAppIdAuthority::HashDefinition`|取得指定之 `IDefinitionAppId` 實例的雜湊索引鍵。|  
|`IAppIdAuthority::HashReference`|取得指定之 `IReferenceAppId` 實例的雜湊索引鍵。|  
|`IAppIdAuthority::ReferenceToText`|使用指定的旗標值，取得指定之 `IReferenceAppId`的字串版本。|  
|`IAppIdAuthority::TextToDefinition`|取得 `IDefinitionAppId` 實例的介面指標，表示指定的字串索引鍵所參考的元件。|  
|`IAppIdAuthority::TextToReference`|取得 `IReferenceAppId` 實例的介面指標，表示指定的字串索引鍵所參考的元件。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [融合介面](fusion-interfaces.md)
