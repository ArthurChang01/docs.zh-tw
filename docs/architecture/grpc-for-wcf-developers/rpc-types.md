---
title: WCF 開發人員的 RPC gRPC 類型
description: 瞭解 WCF 支援的遠端程序呼叫類型，以及它們在 gRPC 中的對等專案
ms.date: 09/02/2019
ms.openlocfilehash: 58f097bac61395e6810155e8ae9a6bbf2219ec5e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503438"
---
# <a name="types-of-rpc"></a>RPC 類型

身為 Windows Communication Foundation （WCF）開發人員，您可能會用來處理下列類型的遠端程序呼叫（RPC）：

- 要求/回復
- 雙面
  - 使用會話的單向雙工
  - 具有會話的全雙工
- 單向

您可以將這些 RPC 類型相當自然地對應到現有的 gRPC 概念。 本章將依次探討每個區域。 [第5章](migrate-wcf-to-grpc.md)將更深入探討類似的範例。

| WCF | gRPC |
| --- | ---- |
| 一般要求/回復 | 一元 (Unary) |
| 具有使用用戶端回呼介面之會話的雙工服務 | 伺服器串流 |
| 具有會話的全雙工服務 | 雙向串流 |
| 單向作業 | 用戶端串流 |

## <a name="requestreply"></a>要求/回復

針對採用並傳回少量資料的簡單要求/回復方法，請使用最簡單的 gRPC 模式（一元 RPC）。

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

如您所見，執行 gRPC 一元 RPC 服務方法與執行 WCF 作業類似。 其差異在於，使用 gRPC 時，您會覆寫基類方法，而不是執行介面。 在伺服器上，gRPC 基底方法一律會傳回 <xref:System.Threading.Tasks.Task%601>，雖然用戶端同時提供非同步和封鎖方法來呼叫服務。

## <a name="wcf-duplex-one-way-to-client"></a>WCF 雙工，一種用戶端

WCF 應用程式（具有特定系結）可以在用戶端與伺服器之間建立持續連線。 伺服器可以使用 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> 屬性中指定的*回呼介面*，以非同步方式將資料傳送至用戶端，直到關閉連接為止。

gRPC 服務提供與訊息資料流程類似的功能。 在執行方面，資料流程不會*完全*對應到 WCF 雙工服務，但您可以達到相同的結果。

### <a name="grpc-streaming"></a>gRPC 串流

gRPC 支援從用戶端到伺服器，以及從伺服器到用戶端的持續性資料流程建立。 這兩種類型的資料流程可以同時為作用中。 這種功能稱為雙向串流。 

您可以使用資料流程來處理一段時間的任意非同步訊息。 或者，您可以使用它們來傳遞太大的大型資料集，以便在單一要求或回應中產生和傳送。

下列範例顯示伺服器資料流程 RPC。

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

您可以從用戶端應用程式取用此伺服器資料流程，如下列程式碼所示：

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> 伺服器串流處理 Rpc 適用于訂用帳戶樣式服務。 當大型資料集在記憶體中建立整個資料集沒有效率或無法完成時，它們也很有用。 不過，串流回應與在單一訊息中傳送 `repeated` 欄位的速度一樣快。 作為規則，串流不應用於小型資料集。

### <a name="differences-from-wcf"></a>WCF 的差異

WCF 雙工服務使用的用戶端回呼介面可以有多個方法。 GRPC 伺服器串流服務只能透過單一資料流程傳送訊息。 如果您需要多個方法，請使用具有[任何欄位或欄位之一的](protobuf-any-oneof.md)訊息類型來傳送不同的訊息，並在用戶端中撰寫程式碼來處理它們。

在 WCF 中，具有會話的[ServiceContract](xref:System.ServiceModel.ServiceContractAttribute)類別會保持運作，直到連接關閉為止。 可以在會話內呼叫多個方法。 在 gRPC 中，執行方法傳回的 `Task` 不應完成，直到連接關閉為止。

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>WCF 單向作業和 gRPC 用戶端串流

WCF 提供單向作業（以 `[OperationContract(IsOneWay = true)]`標記），其會傳回傳輸特定的通知。 gRPC 服務方法一律會傳迴響應，即使它是空的也一樣。 用戶端應該一律等待該回應。 如需 gRPC 中的「暫時訊息」模式，您可以建立用戶端串流服務。

### <a name="thing_logproto"></a>thing_log. proto

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a>ThingLogService.cs

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a>ThingLog 用戶端範例

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

您可以使用用戶端串流 Rpc 來進行引發和忘記的訊息，如先前範例所示。 您也可以使用它們將非常大型的資料集傳送至伺服器。 適用于效能的相同警告：對於較小的資料集，請在一般訊息中使用 `repeated` 欄位。

## <a name="wcf-full-duplex-services"></a>WCF 全雙工服務

WCF 雙工系結支援服務介面和用戶端回呼介面上的多個單向作業。 這種支援可讓用戶端與伺服器之間進行進行中的交談。 gRPC 支援類似于雙向串流 Rpc 的專案，其中兩個參數都以 `stream` 修飾詞標記。

### <a name="chatproto"></a>聊天. proto

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a>ChatterService.cs

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

在上述範例中，您可以看到執行方法會同時收到要求資料流程（`IAsyncStreamReader<MessageRequest>`）和回應資料流程（`IServerStreamWriter<MessageResponse>`）。 方法可以讀取和寫入訊息，直到連接關閉為止。

### <a name="chatter-client"></a>Chatter 用戶端

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
>[上一頁](wcf-bindings.md)
>[下一頁](metadata.md)
