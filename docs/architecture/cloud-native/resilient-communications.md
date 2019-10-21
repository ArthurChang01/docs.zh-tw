---
title: 具有復原性的通訊
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |復原通訊
ms.date: 06/30/2019
ms.openlocfilehash: 324f5426af1c892db73aa6fc2336a19b7a8e499e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315800"
---
# <a name="resilient-communications"></a><span data-ttu-id="19243-103">復原通訊</span><span class="sxs-lookup"><span data-stu-id="19243-103">Resilient communications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="19243-104">在本書中，我們 evangelized 了超越傳統整合型應用程式設計的優勢，並採用以微服務為基礎的架構，其中一組分散、獨立的服務獨立執行，並與每個伺服器通訊其他使用標準通訊協定，例如 HTTP 和 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="19243-104">Throughout this book, we've evangelized the merits of moving beyond traditional monolithic application design and embracing a microservice-based architecture where a set of distributed, self-contained services run independently and communicate with each other using standard communication protocols such as HTTP and HTTPS.</span></span> <span data-ttu-id="19243-105">雖然這類架構會為您購買許多重要的好處，但它也有許多挑戰。</span><span class="sxs-lookup"><span data-stu-id="19243-105">While such an architecture buys you many important benefits, it also presents many challenges.</span></span> <span data-ttu-id="19243-106">例如，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="19243-106">Consider, for example, the following concerns:</span></span>

- <span data-ttu-id="19243-107">*跨進程的網路通訊。*</span><span class="sxs-lookup"><span data-stu-id="19243-107">*Out-of-process network communication.*</span></span> <span data-ttu-id="19243-108">每個服務都會透過網路通訊協定進行通訊，這會引進網路擁塞、延遲和暫時性錯誤。</span><span class="sxs-lookup"><span data-stu-id="19243-108">Each service communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>
- <span data-ttu-id="19243-109">*服務探索。*</span><span class="sxs-lookup"><span data-stu-id="19243-109">*Service discovery.*</span></span> <span data-ttu-id="19243-110">當每個服務在具有自己 IP 位址和埠的機器叢集上執行時，服務如何彼此探索及通訊？</span><span class="sxs-lookup"><span data-stu-id="19243-110">With each service running across a cluster of machines with its own IP address and port, how do services discover and communicate with each other?</span></span>
- <span data-ttu-id="19243-111">*恢復.*</span><span class="sxs-lookup"><span data-stu-id="19243-111">*Resiliency.*</span></span> <span data-ttu-id="19243-112">如何管理短期失敗並讓系統穩定？</span><span class="sxs-lookup"><span data-stu-id="19243-112">How do you manage short-lived failures and keep the system stable?</span></span>
- <span data-ttu-id="19243-113">*負載平衡。*</span><span class="sxs-lookup"><span data-stu-id="19243-113">*Load balancing.*</span></span> <span data-ttu-id="19243-114">輸入流量如何分散到服務的多個實例？</span><span class="sxs-lookup"><span data-stu-id="19243-114">How does inbound traffic get distributed across multiple instances of a service?</span></span>
- <span data-ttu-id="19243-115">*安全性。*</span><span class="sxs-lookup"><span data-stu-id="19243-115">*Security.*</span></span> <span data-ttu-id="19243-116">如何強制執行傳輸層級加密和憑證管理等安全性考慮？</span><span class="sxs-lookup"><span data-stu-id="19243-116">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>
- <span data-ttu-id="19243-117">*分散式監視。*</span><span class="sxs-lookup"><span data-stu-id="19243-117">*Distributed Monitoring.*</span></span> <span data-ttu-id="19243-118">-如何讓多個取用服務的單一要求相互關聯和捕捉追蹤性和監視？</span><span class="sxs-lookup"><span data-stu-id="19243-118">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming services?</span></span>

<span data-ttu-id="19243-119">雖然這些問題可以透過各種程式庫和架構來處理，但在程式碼基底中執行它們可能既昂貴又複雜又耗時。</span><span class="sxs-lookup"><span data-stu-id="19243-119">While these concerns can be addressed with various libraries and frameworks, implementing them inside your codebase can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="19243-120">此外，您最後會得到一個解決方案，其中的基礎結構顧慮會結合商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="19243-120">Moreover, you end up with a solution where infrastructure concerns are coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="19243-121">服務網格</span><span class="sxs-lookup"><span data-stu-id="19243-121">Service mesh</span></span>

<span data-ttu-id="19243-122">較好的方法是考慮採用*服務網格*的全新且快速進化技術。</span><span class="sxs-lookup"><span data-stu-id="19243-122">A better approach is to consider a new and rapidly evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="19243-123">[服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是一個可設定的基礎結構層，具有可處理服務通訊的內建功能，以及上述許多挑戰。</span><span class="sxs-lookup"><span data-stu-id="19243-123">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and many of the challenges mentioned above.</span></span> <span data-ttu-id="19243-124">它會將這些疑慮與您的商務程式碼分開，並將其移至服務 proxy 中，這是每個服務隨附的實例。</span><span class="sxs-lookup"><span data-stu-id="19243-124">It decouples these concerns from your business code and moves them into a service proxy, an instance of which accompanies each of your services.</span></span> <span data-ttu-id="19243-125">通常稱為[側車模式](https://docs.microsoft.com/azure/architecture/patterns/sidecar)，服務網格 proxy 會部署到個別的進程，以供應商務程式碼的隔離和封裝。</span><span class="sxs-lookup"><span data-stu-id="19243-125">Often referred to as the [Sidecar pattern](https://docs.microsoft.com/azure/architecture/patterns/sidecar), the service mesh proxy is deployed into a separate process to provide isolation and encapsulation from your business code.</span></span> <span data-ttu-id="19243-126">不過，proxy 會與建立的服務緊密連結，並共用其生命週期。</span><span class="sxs-lookup"><span data-stu-id="19243-126">However, the proxy is closely linked to the service being created along with it and sharing its lifecycle.</span></span> <span data-ttu-id="19243-127">圖6-9 顯示這種情況。</span><span class="sxs-lookup"><span data-stu-id="19243-127">Figure 6-9 shows this scenario.</span></span>

![具有側車的服務網格](./media/service-mesh-with-side-car.png)

<span data-ttu-id="19243-129">**圖 6-9**。</span><span class="sxs-lookup"><span data-stu-id="19243-129">**Figure 6-9**.</span></span> <span data-ttu-id="19243-130">具有側車的服務網格</span><span class="sxs-lookup"><span data-stu-id="19243-130">Service mesh with a side car</span></span>

<span data-ttu-id="19243-131">在上圖中，請注意 proxy 如何攔截及管理微服務與叢集之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="19243-131">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="19243-132">服務網格會以邏輯方式分割成兩個不同的元件：[資料平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)和[控制平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)。</span><span class="sxs-lookup"><span data-stu-id="19243-132">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="19243-133">圖6-10 顯示這些元件及其責任。</span><span class="sxs-lookup"><span data-stu-id="19243-133">Figure 6-10 shows these components and their responsibilities.</span></span>

![服務網格控制項和資料平面](./media/istio-control-and-data-plane.png)

<span data-ttu-id="19243-135">**圖6-10。**</span><span class="sxs-lookup"><span data-stu-id="19243-135">**Figure 6-10.**</span></span> <span data-ttu-id="19243-136">服務網格控制項和資料平面</span><span class="sxs-lookup"><span data-stu-id="19243-136">Service mesh control and data plane</span></span>

<span data-ttu-id="19243-137">設定好之後，服務網格就能發揮高功能。</span><span class="sxs-lookup"><span data-stu-id="19243-137">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="19243-138">它可以從服務探索端點取得對應的實例集區。</span><span class="sxs-lookup"><span data-stu-id="19243-138">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="19243-139">然後，它可以將要求傳送至特定實例，並記錄結果的延遲和回應類型。</span><span class="sxs-lookup"><span data-stu-id="19243-139">It can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="19243-140">網格可以根據許多因素（包括觀察到最近要求的延遲），選擇最有可能傳回快速回應的實例。</span><span class="sxs-lookup"><span data-stu-id="19243-140">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="19243-141">如果實例沒有回應或失敗，則網格可以重試另一個實例上的要求。</span><span class="sxs-lookup"><span data-stu-id="19243-141">If an instance is unresponsive or fails, the mesh can retry the request on another instance.</span></span> <span data-ttu-id="19243-142">如果集區一致地傳回錯誤，則網格可以將其從負載平衡集區收回，以便稍後在修復後定期重試。</span><span class="sxs-lookup"><span data-stu-id="19243-142">If a pool consistently returns errors, a mesh can evict it from the load-balancing pool to be retried periodically later after it heals.</span></span> <span data-ttu-id="19243-143">如果要求超時，網格可能會失敗，然後重試要求。</span><span class="sxs-lookup"><span data-stu-id="19243-143">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="19243-144">網格會以計量和分散式追蹤的形式來捕捉行為，然後可以發出至集中式計量系統。</span><span class="sxs-lookup"><span data-stu-id="19243-144">A mesh captures behavior in the form of metrics and distributed tracing, which then can be emitted to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="19243-145">Istio 和 Envoy</span><span class="sxs-lookup"><span data-stu-id="19243-145">Istio and Envoy</span></span>

<span data-ttu-id="19243-146">雖然目前有一些服務網格選項存在，但[Istio](https://istio.io/docs/concepts/what-is-istio/)是在撰寫本文時最受歡迎的。</span><span class="sxs-lookup"><span data-stu-id="19243-146">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular as of the time of this writing.</span></span> <span data-ttu-id="19243-147">IBM、Google 和 Lyft 司機的聯合風險，是一個開放原始碼的供應專案，可以整合到新的或現有的分散式應用程式中。</span><span class="sxs-lookup"><span data-stu-id="19243-147">A joint venture from IBM, Google, and Lyft, it's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="19243-148">它提供一致且完整的解決方案來保護、連接和監視微服務。</span><span class="sxs-lookup"><span data-stu-id="19243-148">It provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="19243-149">其功能包括：</span><span class="sxs-lookup"><span data-stu-id="19243-149">Its features include:</span></span>

- <span data-ttu-id="19243-150">在具有強式身分識別型驗證和授權的叢集中，保護服務對服務的通訊。</span><span class="sxs-lookup"><span data-stu-id="19243-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="19243-151">HTTP、 [gRPC](https://grpc.io/)、WEBSOCKET 和 TCP 流量的自動負載平衡。</span><span class="sxs-lookup"><span data-stu-id="19243-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="19243-152">使用豐富的路由規則、重試、容錯移轉和錯誤插入來精細控制流量行為。</span><span class="sxs-lookup"><span data-stu-id="19243-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="19243-153">可插入的原則層和設定 API，支援存取控制、速率限制和配額。</span><span class="sxs-lookup"><span data-stu-id="19243-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="19243-154">叢集中所有流量的自動計量、記錄和追蹤，包括叢集輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="19243-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="19243-155">Istio 執行的主要元件是具有[Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)資格的 proxy 服務。</span><span class="sxs-lookup"><span data-stu-id="19243-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="19243-156">從 Lyft 司機開始，並提供給[雲端原生運算基礎](https://www.cncf.io/)（在第1章中討論），Envoy proxy 會與每個服務一起執行，並為下列功能提供不受平臺限制的基礎：</span><span class="sxs-lookup"><span data-stu-id="19243-156">Originating from Lyft and subsequently contributed to the [Cloud Native Computing Foundation](https://www.cncf.io/) (discussed in chapter 1), the Envoy proxy runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="19243-157">動態服務探索。</span><span class="sxs-lookup"><span data-stu-id="19243-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="19243-158">負載平衡。</span><span class="sxs-lookup"><span data-stu-id="19243-158">Load balancing.</span></span>
- <span data-ttu-id="19243-159">TLS 終止。</span><span class="sxs-lookup"><span data-stu-id="19243-159">TLS termination.</span></span>
- <span data-ttu-id="19243-160">HTTP 和 gRPC proxy。</span><span class="sxs-lookup"><span data-stu-id="19243-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="19243-161">斷路器復原功能。</span><span class="sxs-lookup"><span data-stu-id="19243-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="19243-162">健康情況檢查。</span><span class="sxs-lookup"><span data-stu-id="19243-162">Health checks.</span></span>
- <span data-ttu-id="19243-163">[使用未](https://martinfowler.com/bliki/CanaryRelease.html)通過部署的輪流更新。</span><span class="sxs-lookup"><span data-stu-id="19243-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="19243-164">如先前所討論，Envoy 會以側車的形式部署至叢集中的每個微服務。</span><span class="sxs-lookup"><span data-stu-id="19243-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="19243-165">與 Azure Kubernetes Services 整合</span><span class="sxs-lookup"><span data-stu-id="19243-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="19243-166">Azure 雲端採用 Istio，並在 Azure Kubernetes Services 中提供對其的直接支援。</span><span class="sxs-lookup"><span data-stu-id="19243-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="19243-167">下列連結可協助您開始使用：</span><span class="sxs-lookup"><span data-stu-id="19243-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="19243-168">在 AKS 中安裝 Istio</span><span class="sxs-lookup"><span data-stu-id="19243-168">Installing Istio in AKS</span></span>](https://docs.microsoft.com/azure/aks/istio-install)
- [<span data-ttu-id="19243-169">使用 AKS 和 Istio</span><span class="sxs-lookup"><span data-stu-id="19243-169">Using AKS and Istio</span></span>](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

>[!div class="step-by-step"]
><span data-ttu-id="19243-170">[上一頁](infrastructure-resiliency-azure.md)
>[下一頁](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="19243-170">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>
