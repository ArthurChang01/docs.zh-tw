---
title: 使用適用於 .NET 的 Azure 程式庫來進行驗證
description: 使用適用於 .NET 的 Azure 程式庫來進行驗證
ms.date: 08/22/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: f6af813cd1423be8784b769b272756b2c8258392
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072148"
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a>使用適用於 .NET 的 Azure 程式庫來進行驗證

## <a name="connect-to-services-with-connection-strings"></a>使用連接字串來連線到服務

Azure 服務程式庫大多會要求連接字串或金鑰來進行驗證。 例如，SQL Database 會使用標準 SQL 連接字串：

```csharp
var builder = new SqlConnectionStringBuilder();
builder.DataSource = "example.database.windows.net";
builder.InitialCatalog = "MyDatabase";
builder.UserID = "sampleuser@example"; // Format user ID as "user@server"
builder.Password = password;
builder.Encrypt = true;
builder.TrustServerCertificate = true;

using (var conn = new SqlConnection(builder.ConnectionString))
{
    conn.Open();
    // Do things with the connection...
    // ...
}
```

Azure 儲存體會使用儲存體金鑰：

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

服務連接字串會在其他 Azure 服務中使用，例如[CosmosDB](https://docs.microsoft.com/azure/cosmos-db/)、 [Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)和[服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues)。 您可以使用 Azure 入口網站、CLI 或 PowerShell 來取得這些字串。 您也可以使用適用於 .NET 的 Azure 管理程式庫來查詢資源，從而在程式碼中建置連接字串。

此程式碼片段會使用管理程式庫來建立儲存體帳戶的連接字串：

```csharp
// Get a storage account
var storage = azure.StorageAccounts.GetByResourceGroup("myResourceGroup", "myStorageAccount");

// Extract the keys
var storageKeys = storage.GetKeys();

// Build the connection string
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

// Connect
var account = CloudStorageAccount.Parse(storageConnectionString);

// Do things with the account here...
```

對於其他程式庫，應用程式就必須使用[服務主體](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects)來執行，這個服務主體要授權應用程式使用獲授與的認證來執行。 這項設定很類似下面所列管理程式庫中的物件型驗證步驟。

## <a name="azure-management-libraries-for-net-authentication"></a><a name="mgmt-auth"></a>適用於 .NET 驗證的 Azure 管理程式庫

[!include[Create service principal](../includes/create-sp.md)]

現在您已建立服務主體，有兩個選項可用來驗證服務主體，從而建立和管理資源。

針對這兩個選項，您必須將下列 NuGet 套件新增至您的專案。

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>使用權杖認證進行驗證

第一個方法是在程式碼中建置權杖認證物件。 您應該在組態檔、登錄或 Azure Key Vault 中安全地儲存認證。

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId,
    AzureEnvironment.AzureGlobalCloud);
```

使用 *clientId*、*clientSecret*和 *tenantId* 等值，這些值來自已建立服務主體處的 JSON 輸出。

然後，建立進入點 `Azure` 物件來開始使用 API：

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a>以檔案作為基礎的驗證

以檔案作為基礎的驗證可讓您將服務主體認證放在純文字檔案，並在檔案系統內加以保護。

[!include[File-based authentication](../includes/file-based-auth.md)]

讀取檔案的內容，並建立進入點 `Azure` 物件來開始使用 API：

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
