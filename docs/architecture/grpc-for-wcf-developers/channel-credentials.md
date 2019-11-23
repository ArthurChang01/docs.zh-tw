---
title: 通道認證-適用于 WCF 開發人員的 gRPC
description: 如何在 ASP.NET Core 3.0 中執行和使用 gRPC 通道認證。
ms.date: 09/02/2019
ms.openlocfilehash: b424db49337a2dc6e3d0245d36349e3f408cdf6c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967954"
---
# <a name="channel-credentials"></a><span data-ttu-id="eb389-103">通道認證</span><span class="sxs-lookup"><span data-stu-id="eb389-103">Channel credentials</span></span>

<span data-ttu-id="eb389-104">如其名稱所示，通道認證會附加至基礎 gRPC 通道。</span><span class="sxs-lookup"><span data-stu-id="eb389-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="eb389-105">通道認證的標準形式使用用戶端憑證驗證，在此情況下，用戶端會在建立連線時提供 TLS 憑證，在允許進行任何呼叫之前，伺服器會先驗證該憑證。</span><span class="sxs-lookup"><span data-stu-id="eb389-105">The standard form of channel credentials uses Client Certificate authentication, where the client provides a TLS certificate when it's making the connection, which is verified by the server before allowing any calls to be made.</span></span>

<span data-ttu-id="eb389-106">通道認證可以與呼叫認證結合，以提供 gRPC 服務的完整安全性。</span><span class="sxs-lookup"><span data-stu-id="eb389-106">Channel credentials can be combined with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="eb389-107">通道認證會證明用戶端應用程式可以存取服務，而呼叫認證會提供使用用戶端應用程式之人員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eb389-107">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person using the client application.</span></span>

<span data-ttu-id="eb389-108">用戶端憑證驗證適用于 gRPC，其運作方式與 ASP.NET Core 的相同。</span><span class="sxs-lookup"><span data-stu-id="eb389-108">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="eb389-109">設定程式將在此摘要說明，但如需詳細資訊，請參閱在[ASP.NET Core 中設定憑證驗證](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0)一文。</span><span class="sxs-lookup"><span data-stu-id="eb389-109">The configuration process will be summarized here, but more information is available in the [Configure certificate authentication in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) article.</span></span>

<span data-ttu-id="eb389-110">基於開發目的，您可以使用自我簽署的憑證，但在生產環境中，您應該使用由受信任的授權單位所簽署的適當 HTTPS 憑證。</span><span class="sxs-lookup"><span data-stu-id="eb389-110">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="adding-certificate-authentication-to-the-server"></a><span data-ttu-id="eb389-111">將憑證驗證新增至伺服器</span><span class="sxs-lookup"><span data-stu-id="eb389-111">Adding certificate authentication to the server</span></span>

<span data-ttu-id="eb389-112">您必須在主機層級設定憑證驗證，例如在 Kestrel 伺服器上，以及在 ASP.NET Core 管線中。</span><span class="sxs-lookup"><span data-stu-id="eb389-112">You need to configure certificate authentication both at the host level, for example on the Kestrel server, and in the ASP.NET Core pipeline.</span></span>

### <a name="configuring-certificate-validation-on-kestrel"></a><span data-ttu-id="eb389-113">在 Kestrel 上設定憑證驗證</span><span class="sxs-lookup"><span data-stu-id="eb389-113">Configuring certificate validation on Kestrel</span></span>

<span data-ttu-id="eb389-114">您可以將 Kestrel （ASP.NET Core HTTP 伺服器）設定為需要用戶端憑證，並選擇性地在接受連入連線之前，先執行所提供憑證的一些驗證。</span><span class="sxs-lookup"><span data-stu-id="eb389-114">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate before accepting incoming connections.</span></span> <span data-ttu-id="eb389-115">這項設定是在 `Program` 類別的 `CreateWebHostBuilder` 方法中完成，而不是在 `Startup`中進行。</span><span class="sxs-lookup"><span data-stu-id="eb389-115">This configuration is done in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

<span data-ttu-id="eb389-116">`ClientCertificateMode.RequireCertificate` 設定會導致 Kestrel 立即拒絕未提供用戶端憑證的任何連線要求，但它不會驗證憑證。</span><span class="sxs-lookup"><span data-stu-id="eb389-116">The `ClientCertificateMode.RequireCertificate` setting will cause Kestrel to immediately reject any connection request that doesn't provide a client certificate, but it won't validate the certificate.</span></span> <span data-ttu-id="eb389-117">新增 `ClientCertificateValidation` 回呼可讓 Kestrel 驗證用戶端憑證（在此案例中，確保它是由與伺服器憑證相同的*憑證授權單位*單位所發行），然後再執行 ASP.NET Core 管線。</span><span class="sxs-lookup"><span data-stu-id="eb389-117">Adding the `ClientCertificateValidation` callback enables Kestrel to validate the client certificate (in this case, ensuring that it was issued by the same *Certificate Authority* as the server certificate) at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span>

### <a name="adding-aspnet-core-certificate-authentication"></a><span data-ttu-id="eb389-118">新增 ASP.NET Core 憑證驗證</span><span class="sxs-lookup"><span data-stu-id="eb389-118">Adding ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="eb389-119">憑證驗證是由 AspNetCore 所提供。[憑證](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate)NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="eb389-119">Certificate authentication is provided by the [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package.</span></span>

<span data-ttu-id="eb389-120">在 `ConfigureServices` 方法中新增憑證驗證服務，然後在 `Configure` 方法中，將驗證和授權新增至 ASP.NET Core 管線。</span><span class="sxs-lookup"><span data-stu-id="eb389-120">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="providing-channel-credentials-in-the-client-application"></a><span data-ttu-id="eb389-121">在用戶端應用程式中提供通道認證</span><span class="sxs-lookup"><span data-stu-id="eb389-121">Providing channel credentials in the client application</span></span>

<span data-ttu-id="eb389-122">使用 `Grpc.Net.Client` 封裝時，會在提供給用於連接之 `GrpcChannel` 的 <xref:System.Net.Http.HttpClient> 實例上設定憑證。</span><span class="sxs-lookup"><span data-stu-id="eb389-122">With the `Grpc.Net.Client` package, certificates are configured on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combining-channelcredentials-and-callcredentials"></a><span data-ttu-id="eb389-123">結合 ChannelCredentials 和 CallCredentials</span><span class="sxs-lookup"><span data-stu-id="eb389-123">Combining ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="eb389-124">您可以將憑證變更套用至 Kestrel 伺服器，並在 ASP.NET Core 中使用 JWT 持有人中介軟體，將伺服器設定為使用憑證和權杖驗證。</span><span class="sxs-lookup"><span data-stu-id="eb389-124">You can configure your server to use both certificate and token authentication by applying the certificate changes to the Kestrel server and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="eb389-125">若要在用戶端上同時提供 ChannelCredentials 和 CallCredentials，請使用 `ChannelCredentials.Create` 方法來套用呼叫認證。</span><span class="sxs-lookup"><span data-stu-id="eb389-125">To provide both ChannelCredentials and CallCredentials on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="eb389-126">您仍然必須使用 <xref:System.Net.Http.HttpClient> 實例來套用憑證驗證：如果您將任何引數傳遞至 `SslCredentials` 的「檢查程式」，則內部用戶端程式代碼會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eb389-126">Certificate authentication still needs to be applied using the <xref:System.Net.Http.HttpClient> instance: if you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="eb389-127">`SslCredentials` 參數只會包含在 `Grpc.Net.Client` 套件的 `Create` 方法中，以維持與 `Grpc.Core` 套件的相容性。</span><span class="sxs-lookup"><span data-stu-id="eb389-127">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> <span data-ttu-id="eb389-128">您可以將 `ChannelCredentials.Create` 方法用於沒有憑證驗證的用戶端，這是使用通道上的每個呼叫來傳遞權杖認證的實用方法。</span><span class="sxs-lookup"><span data-stu-id="eb389-128">You can use the `ChannelCredentials.Create` method for a client without certificate authentication, as a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="eb389-129">GitHub 上已[加入憑證驗證的 FullStockTicker 範例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker)版本。</span><span class="sxs-lookup"><span data-stu-id="eb389-129">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="eb389-130">[上一頁](call-credentials.md)
>[下一頁](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="eb389-130">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
