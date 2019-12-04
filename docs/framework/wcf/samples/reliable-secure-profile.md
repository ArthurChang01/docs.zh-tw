---
title: 可靠的安全設定檔
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: ee94dc5be2c50f9e383a42d435996b2fd35df4a4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716496"
---
# <a name="reliable-secure-profile"></a><span data-ttu-id="c422e-102">可靠的安全設定檔</span><span class="sxs-lookup"><span data-stu-id="c422e-102">Reliable Secure Profile</span></span>
<span data-ttu-id="c422e-103">這個範例會示範如何撰寫 WCF 和[可靠的安全設定檔](https://go.microsoft.com/fwlink/?LinkId=178140)（.rsp）。</span><span class="sxs-lookup"><span data-stu-id="c422e-103">This sample demonstrates how to compose WCF and [Reliable Secure Profile](https://go.microsoft.com/fwlink/?LinkId=178140) (RSP).</span></span> <span data-ttu-id="c422e-104">這個範例會示範如何執行「[建立連接](https://go.microsoft.com/fwlink/?LinkId=178141)通道」，它可以與可靠的訊息結合在一起，並選擇性地建立安全的通道，以根據 RSP 規格建立可靠的安全系結。</span><span class="sxs-lookup"><span data-stu-id="c422e-104">This sample demonstrates the implementation of a [Make Connection](https://go.microsoft.com/fwlink/?LinkId=178141) channel which can be composed together with Reliable Messaging and optionally a secure channel to create a Reliable Secure Binding based on the RSP specification.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c422e-105">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c422e-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c422e-106">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="c422e-106">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c422e-107">如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="c422e-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c422e-108">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="c422e-108">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a><span data-ttu-id="c422e-109">討論</span><span class="sxs-lookup"><span data-stu-id="c422e-109">Discussion</span></span>  
 <span data-ttu-id="c422e-110">此範例示範可靠的非同步雙向訊息交換案例。</span><span class="sxs-lookup"><span data-stu-id="c422e-110">This sample demonstrates a reliable asynchronous two-way message exchange scenario.</span></span> <span data-ttu-id="c422e-111">此服務擁有雙工合約，而且用戶端會實作雙工回呼合約。</span><span class="sxs-lookup"><span data-stu-id="c422e-111">The service has a duplex contract and the client implements the duplex callback contract.</span></span> <span data-ttu-id="c422e-112">用戶端會向服務起始一個要求，這個要求預期在不同的連線上得到回應。</span><span class="sxs-lookup"><span data-stu-id="c422e-112">The client initiates a request to a service, for which a response is expected on a separate connection.</span></span> <span data-ttu-id="c422e-113">要求訊息是以可靠的方式傳送。</span><span class="sxs-lookup"><span data-stu-id="c422e-113">The request message is sent reliably.</span></span> <span data-ttu-id="c422e-114">用戶端不想在其結尾開啟接聽端點。</span><span class="sxs-lookup"><span data-stu-id="c422e-114">The client does not want to open a listening endpoint at its end.</span></span> <span data-ttu-id="c422e-115">因此，它會利用服務的「建立連線」要求輪詢服務，以便在這個「建立連線」要求的返回通道傳回回應。</span><span class="sxs-lookup"><span data-stu-id="c422e-115">Thus, it polls the service with ‘Make Connection’ requests for the service to send back the response on the back channel of this ‘Make Connection’ request.</span></span> <span data-ttu-id="c422e-116">此範例示範如何透過 HTTP 進行安全可靠的雙工通訊，而不讓用戶端公開接聽端點 (以及建立防火牆例外狀況)。</span><span class="sxs-lookup"><span data-stu-id="c422e-116">This sample demonstrates how to have secure reliable duplex communication over HTTP without the client exposing a listening endpoint (and creating a firewall exception).</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c422e-117">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="c422e-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c422e-118">開啟**ReliableSecureProfile**方案。</span><span class="sxs-lookup"><span data-stu-id="c422e-118">Open the **ReliableSecureProfile** solution.</span></span>  
  
2. <span data-ttu-id="c422e-119">以滑鼠右鍵按一下**方案總管**中的**服務**專案，並從內容功能表中選取 [ **Debug**]、[**啟動新實例**]。</span><span class="sxs-lookup"><span data-stu-id="c422e-119">Right click the **Service** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="c422e-120">這會啟動服務主機。</span><span class="sxs-lookup"><span data-stu-id="c422e-120">This starts up the service host.</span></span>  
  
3. <span data-ttu-id="c422e-121">以滑鼠右鍵按一下**方案總管**中的**用戶端**專案，並從內容功能表中選取 [ **Debug**]、[**啟動新實例**]。</span><span class="sxs-lookup"><span data-stu-id="c422e-121">Right click the **Client** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="c422e-122">這會啟動用戶端。</span><span class="sxs-lookup"><span data-stu-id="c422e-122">This starts up the client.</span></span>  
  
4. <span data-ttu-id="c422e-123">在用戶端主控台視窗的提示中輸入任何字串，然後按一下 ENTER。這會將輸入字串傳送到服務，然後計算此字串的雜湊。</span><span class="sxs-lookup"><span data-stu-id="c422e-123">Type in any string in the prompt on the client console window and click ENTER.This sends the input string to the service, which computes a hash of this string.</span></span>  
  
5. <span data-ttu-id="c422e-124">當服務回呼雙工回呼合約作業以顯示用戶端主控台視窗上的結果時，檢視用戶端視窗上的結果。</span><span class="sxs-lookup"><span data-stu-id="c422e-124">View the result on the client windows when the service calls back the duplex callback contract operation to display the result on the client console window.</span></span> <span data-ttu-id="c422e-125">在服務上會有一個刻意的延遲，以模擬處理資料的長期作業。</span><span class="sxs-lookup"><span data-stu-id="c422e-125">There is an intentional delay on the service to simulate a long running operation of processing the data.</span></span>  
  
6. <span data-ttu-id="c422e-126">監視 HTTP 流量 (透過 Network Monitor、Fiddler 等任何線上網路監視工具) 顯示通訊的順序是在可靠的安全設定檔制定之用戶端和服務之間建立的，並示範用戶端如何利用「建立連線」要求輪詢服務。</span><span class="sxs-lookup"><span data-stu-id="c422e-126">Monitoring the HTTP traffic (by any of the online network monitoring tools like Network Monitor, Fiddler and so on) shows that a sequence for communication is established between the client and the service as laid down by the Reliable Secure Profile, and how the client polls the service with ‘Make Connection’ requests.</span></span> <span data-ttu-id="c422e-127">當服務準備好傳回處理過的回應時，它會使用最後一個「建立連線」要求的返回通道傳回結果。</span><span class="sxs-lookup"><span data-stu-id="c422e-127">When the service gets ready to send back the processed response, it uses the back channel of the last ‘Make Connection’ request to send back the results.</span></span>  
  
7. <span data-ttu-id="c422e-128">在服務主控台視窗上按 ENTER 鍵，以關閉服務。</span><span class="sxs-lookup"><span data-stu-id="c422e-128">Press ENTER on the service console window to close the service.</span></span> <span data-ttu-id="c422e-129">在用戶端主控台視窗上按 ENTER 鍵，以關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="c422e-129">Press ENTER on the client console window to close the client.</span></span>
