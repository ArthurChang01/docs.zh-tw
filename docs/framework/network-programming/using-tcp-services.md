---
title: 使用 TCP 服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
ms.openlocfilehash: 3678586647dcf9c47b4494197fbf56cab865b3d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039495"
---
# <a name="using-tcp-services"></a><span data-ttu-id="37511-102">使用 TCP 服務</span><span class="sxs-lookup"><span data-stu-id="37511-102">Using TCP Services</span></span>

<span data-ttu-id="37511-103"><xref:System.Net.Sockets.TcpClient> 類別會使用 TCP 向網際網路資源要求資料。</span><span class="sxs-lookup"><span data-stu-id="37511-103">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="37511-104">**TcpClient** 的屬性和方法取出的詳細資料，可用來建立 <xref:System.Net.Sockets.Socket> 以使用 TCP 要求和接收資料。</span><span class="sxs-lookup"><span data-stu-id="37511-104">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="37511-105">因為遠端裝置的連線是以資料流表示，所以可以使用 .NET Framework 資料流處理技術來讀取和寫入資料。</span><span class="sxs-lookup"><span data-stu-id="37511-105">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>

<span data-ttu-id="37511-106">TCP 通訊協定會建立與遠端端點的連線，然後使用該連接來傳送和接收資料封包。</span><span class="sxs-lookup"><span data-stu-id="37511-106">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="37511-107">TCP 負責確保將資料封包傳送到端點，並在送達時以正確的順序組合。</span><span class="sxs-lookup"><span data-stu-id="37511-107">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>

<span data-ttu-id="37511-108">若要建立 TCP 傳線，您必須知道裝載所需服務之網路裝置的位址，以及服務用來通訊的 TCP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="37511-108">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="37511-109">Internet Assigned Numbers Authority (Iana) 定義了通用服務的連接埠編號。(請參閱[服務名稱與傳輸通訊協定連接埠號碼登錄](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) \(英文\))。</span><span class="sxs-lookup"><span data-stu-id="37511-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="37511-110">不在 Iana 清單上之服務的連接埠編號範圍可以是 1,024 到 65,535。</span><span class="sxs-lookup"><span data-stu-id="37511-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="37511-111">下面的示例演示了設置**TcpClient**以連接到 TCP 埠 13 上的時間伺服器：</span><span class="sxs-lookup"><span data-stu-id="37511-111">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13:</span></span>

```vb
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeClient
    Private const portNum As Integer = 13
    Private const hostName As String = "host.contoso.com"

    ' Entry point  that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Try
            Dim client As New TcpClient(hostName, portNum)

            Dim ns As NetworkStream = client.GetStream()

            Dim bytes(1024) As Byte
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)

            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))

        Catch e As Exception
            Console.WriteLine(e.ToString())
        End Try

        client.Close()

        Return 0
    End Function
End Class
```

```csharp
using System;
using System.Net.Sockets;
using System.Text;

public class TcpTimeClient
{
    private const int portNum = 13;
    private const string hostName = "host.contoso.com";

    public static int Main(String[] args)
    {
        try
        {
            var client = new TcpClient(hostName, portNum);

            NetworkStream ns = client.GetStream();

            byte[] bytes = new byte[1024];
            int bytesRead = ns.Read(bytes, 0, bytes.Length);

            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));

            client.Close();

        }
        catch (Exception e)
        {
            Console.WriteLine(e.ToString());
        }

        return 0;
    }
}
```

<span data-ttu-id="37511-112"><xref:System.Net.Sockets.TcpListener>用於監視傳入請求的 TCP 埠，然後創建套**接字**或**TcpClient**來管理與用戶端的連接。</span><span class="sxs-lookup"><span data-stu-id="37511-112"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="37511-113"><xref:System.Net.Sockets.TcpListener.Start%2A> 方法可啟用接聽，而 <xref:System.Net.Sockets.TcpListener.Stop%2A> 方法則可停用連接埠上的接聽。</span><span class="sxs-lookup"><span data-stu-id="37511-113">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="37511-114"><xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> 方法會接受連入連線要求，並建立 **TcpClient** 來處理要求，而 <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> 方法會接受連入連線要求，並建立 **Socket** 來處理要求。</span><span class="sxs-lookup"><span data-stu-id="37511-114">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>

<span data-ttu-id="37511-115">下列範例示範如何建立使用 **TcpListener** 來監視 TCP 連接埠 13 的網路時間伺服器。</span><span class="sxs-lookup"><span data-stu-id="37511-115">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="37511-116">接受連入連線要求時，時間伺服器會回應主機伺服器的目前日期和時間。</span><span class="sxs-lookup"><span data-stu-id="37511-116">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeServer

    Private const portNum As Integer = 13

    ' Entry point that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Dim done As Boolean = False

        Dim listener As New TcpListener(IPAddress.Any, portNum)

        listener.Start()

        While Not done
            Console.Write("Waiting for connection...")
            Dim client As TcpClient = listener.AcceptTcpClient()

            Console.WriteLine("Connection accepted.")
            Dim ns As NetworkStream = client.GetStream()

            Dim byteTime As Byte() = _
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())

            Try
                ns.Write(byteTime, 0, byteTime.Length)
                ns.Close()
                client.Close()
            Catch e As Exception
                Console.WriteLine(e.ToString())
            End Try
        End While

        listener.Stop()

        Return 0
    End Function
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class TcpTimeServer
{

    private const int portNum = 13;

    public static int Main(String[] args)
    {
        bool done = false;

        var listener = new TcpListener(IPAddress.Any, portNum);

        listener.Start();

        while (!done)
        {
            Console.Write("Waiting for connection...");
            TcpClient client = listener.AcceptTcpClient();

            Console.WriteLine("Connection accepted.");
            NetworkStream ns = client.GetStream();

            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());

            try
            {
                ns.Write(byteTime, 0, byteTime.Length);
                ns.Close();
                client.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.ToString());
            }
        }

        listener.Stop();

        return 0;
    }

}
```
