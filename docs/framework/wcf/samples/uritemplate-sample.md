---
title: UriTemplate 範例
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: c9dd8bdd21a075dca590c9446808860c006c18f8
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715416"
---
# <a name="uritemplate-sample"></a>UriTemplate 範例
<xref:System.UriTemplate> 類別提供可使用一組共用通用結構之 URI 的方法。 本範例會示範下列與 `UriTemplate` 有關的主要概念：  
  
- 建立範本的語法。  
  
- 從使用 `UriTemplate` 和 <xref:System.UriTemplate.BindByName%2A> 的 <xref:System.UriTemplate.BindByPosition%2A> 產生 URI。  
  
- <xref:System.UriTemplateTable.Match%2A> 是 `BindByName` 和 `BindByPosition` 的反向作業。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
2. 若要在單一或跨電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a>請參閱

- [UriTemplate 資料表](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [UriTemplate 資料表發送器](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
