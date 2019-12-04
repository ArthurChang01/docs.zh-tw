---
title: 組態通道處理站
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1a236f1812d3124e83702a97e1877b7fec10be64
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715495"
---
# <a name="configuration-channel-factory"></a>組態通道處理站
此範例涵蓋 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 的使用方法。 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 可集中管理 WCF 用戶端設定。 如果在應用程式網域載入時間之後選取或變更組態，這可能也相當實用。

## <a name="demonstrates"></a>示範
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>討論
 此範例示範如何使用 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 將特定組態檔加入至用戶端應用程式，而不必使用預設的應用程式組態檔。

 此範例包含二個專案。 第一個專案是簡單服務，執行這個服務可回覆來自用戶端的訊息。 第二個專案是用戶端應用程式，這個應用程式可以針對 Test.config 組態檔使用 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 建立兩個 <xref:System.Configuration.ExeConfigurationFileMap> 物件，並使用這兩個物件與服務進行通訊。 兩個用戶端都會使用 Test.config 中指定的組態，與服務進行通訊。

 下列程式碼會將自訂組態檔加入至用戶端應用程式。

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 以系統管理員許可權開啟 Visual Studio 2012。

2. 以滑鼠右鍵按一下 [ConfigurationChannelFactory 方案（2個專案）]，然後選取 [**屬性**]。

3. 在 [**通用屬性**] 中，選取 [**啟始專案**]，然後按一下 [**多個啟始專案**]。

4. 將**服務**專案移至清單的開頭，並使用**動作「開始」** ，然後在**服務**專案之後移動**用戶端**專案，並同時執行 **「啟動」動作**，讓**用戶端**專案在**服務**專案之後執行。

5. 按一下 **[確定]** ，然後按 F5 （或 CTRL + F5）以執行範例。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
