---
title: 針對 WCF 開發人員比較 WCF 與 gRPC-gRPC
description: 建立分散式應用程式的 WCF 和 gRPC 架構比較。
ms.date: 09/02/2019
ms.openlocfilehash: 312492dcce4bdef61feff0bf924c6df287b9c676
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966957"
---
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="06ccd-103">比較 WCF 與 gRPC</span><span class="sxs-lookup"><span data-stu-id="06ccd-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="06ccd-104">上一章應該讓您瞭解 Protobuf 以及 gRPC 如何處理訊息。</span><span class="sxs-lookup"><span data-stu-id="06ccd-104">The previous chapter should have given you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="06ccd-105">在進行從 WCF 到 gRPC 的詳細轉換之前，請務必查看 WCF 中目前可用的功能範圍如何在 gRPC 中處理，以及當沒有 gRPC 對等的情況時，您可以使用的因應措施。</span><span class="sxs-lookup"><span data-stu-id="06ccd-105">Before working through a detailed conversion from WCF to gRPC, it's important to look at how the range of features currently available in WCF are handled in gRPC and what workarounds you can use when there doesn't appear to be a gRPC equivalent.</span></span> <span data-ttu-id="06ccd-106">具體而言，本章將涵蓋下列主題：</span><span class="sxs-lookup"><span data-stu-id="06ccd-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="06ccd-107">作業和方法</span><span class="sxs-lookup"><span data-stu-id="06ccd-107">Operations and methods</span></span>
- <span data-ttu-id="06ccd-108">系結和傳輸</span><span class="sxs-lookup"><span data-stu-id="06ccd-108">Bindings and transports</span></span>
- <span data-ttu-id="06ccd-109">RPC 類型</span><span class="sxs-lookup"><span data-stu-id="06ccd-109">RPC types</span></span>
- <span data-ttu-id="06ccd-110">中繼資料</span><span class="sxs-lookup"><span data-stu-id="06ccd-110">Metadata</span></span>
- <span data-ttu-id="06ccd-111">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="06ccd-111">Error handling</span></span>
- <span data-ttu-id="06ccd-112">WS-\* 通訊協定</span><span class="sxs-lookup"><span data-stu-id="06ccd-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="06ccd-113">gRPC 範例</span><span class="sxs-lookup"><span data-stu-id="06ccd-113">gRPC example</span></span>

<span data-ttu-id="06ccd-114">當您從 Visual Studio 2019 或命令列建立新的 ASP.NET Core 3.0 gRPC 專案時，系統會為您產生 gRPC 對等的 "Hello World"。</span><span class="sxs-lookup"><span data-stu-id="06ccd-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="06ccd-115">其中包含定義服務和其訊息的 `greeter.proto` 檔案，以及含有服務執行的 `GreeterService.cs` 檔案。</span><span class="sxs-lookup"><span data-stu-id="06ccd-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

<span data-ttu-id="06ccd-116">本章節會在說明 gRPC 的各種概念和功能時，參考此範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="06ccd-116">This chapter will refer to this example code when explaining various concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="06ccd-117">[上一頁](protobuf-maps.md)
>[下一頁](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="06ccd-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
