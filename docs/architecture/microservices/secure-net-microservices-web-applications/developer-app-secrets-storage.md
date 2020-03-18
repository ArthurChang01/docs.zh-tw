---
title: 在開發期間安全地儲存應用程式祕密
description: .NET 微服務和 Web 應用程式中的安全性 - 請勿將您的應用程式祕密 (例如密碼、連接字串或 API 金鑰) 儲存在原始檔控制中，請了解您可以在 ASP.NET Core 中使用的選項，尤其是必須了解如何處理「使用者祕密」。
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 1ef2246746b9165f1564fa7be64ff7eb28eb1d32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501790"
---
# <a name="store-application-secrets-safely-during-development"></a>在開發期間安全地儲存應用程式密碼

為了連接到受保護的資源和其他服務，ASP.NET Core 應用程式通常需要使用包含機密資訊的連接字串、密碼或其他認證。 這些機密資訊稱為「祕密」**。 最佳做法是不要在原始程式碼中包含祕密，而且絕不要在原始檔控制中儲存祕密。 相反地，您應該使用 ASP.NET Core 組態模型，從更安全的位置讀取秘密。

您必須將用於存取開發和暫存資源的祕密，與用於存取生產資源的祕密分開，因為不同的人需要存取不同組的祕密。 若要儲存在開發期間使用的秘密，常見的方法是將秘密儲存在環境變數中，或藉由使用 ASP.NET Core Secret Manager 工具來儲存。 為了在生產環境中更安全的儲存，微服務可以將秘密儲存在 Azure Key Vault 中。

## <a name="store-secrets-in-environment-variables"></a>將祕密儲存在環境變數中

將秘密與原始程式碼分開保存的一個方法，是由開發人員在其開發電腦上將字串型秘密設定為[環境變數](/aspnet/core/security/app-secrets#environment-variables)。 當您使用環境變數來儲存具有階層式名稱的祕密 (例如巢狀於組態區段中) 時，您必須將變數命名以包含其區段的完整階層 (以冒號 (:) 分隔)。

例如，將環境變數 `Logging:LogLevel:Default` 設定為 `Debug` 相當於下列 JSON 檔案中的設定值：

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

若要從環境變數存取這些值，應用程式只需要在建構 IConfigurationRoot 物件時在其 ConfigurationBuilder 上呼叫 AddEnvironmentVariables 即可。

請注意，環境變數通常會儲存為純文字，因此如果電腦或具有環境變數的處理序遭到入侵，就會顯示環境變數值。

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>使用 ASP.NET Core Secret Manager 儲存祕密

ASP.NET核心[金鑰管理器](/aspnet/core/security/app-secrets#secret-manager)工具提供了另一種在**開發過程中**將機密從原始程式碼中保存出來的方法。 若要使用 Secret Manager 工具，請在您的專案檔中安裝套件 **Microsoft.Extensions.Configuration.SecretManager**。 一旦該相依性存在並已還原，即可使用 `dotnet user-secrets` 命令從命令列設定祕密的值。 這些秘密會儲存在使用者設定檔目錄中的 JSON 檔案中 (細目會因 OS 而異)，並遠離原始程式碼。

Secret Manager 工具所設定的祕密會依使用祕密之專案的 `UserSecretsId` 屬性來組織。 因此，請務必在專案檔中設定 UserSecretsId 屬性，如下列程式碼片段所示。 預設值是 Visual Studio 指派的 GUID，但只要它在您電腦中是唯一的，則實際字串並不重要。

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

若要使用 Secret Manager 儲存在應用程式中的祕密，請在 ConfigurationBuilder 執行個體上呼叫 `AddUserSecrets<T>` 以在其設定中包含應用程式的祕密。 泛型參數 T 應該是已套用 UserSecretId 之組件的類型。 通常，使用 `AddUserSecrets<Startup>` 沒有問題。

在 *Program.cs* 中使用 `CreateDefaultBuilder` 方法時，`AddUserSecrets<Startup>()` 會包含在開發環境的預設選項中。

>[!div class="step-by-step"]
>[上一個](authorization-net-microservices-web-applications.md)
>[下一個](azure-key-vault-protects-secrets.md)
