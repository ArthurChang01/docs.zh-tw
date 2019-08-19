---
title: 無伺服器架構-無伺服器應用程式
description: 探索無伺服器架構支援的各種架構和應用程式, 包括 web 應用程式、行動裝置和 IoT。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3b22fecfdc693154dbdeb3e872e0e246e8ca41f9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577351"
---
# <a name="serverless-architecture"></a><span data-ttu-id="8331a-103">無伺服器架構</span><span class="sxs-lookup"><span data-stu-id="8331a-103">Serverless architecture</span></span>

<span data-ttu-id="8331a-104">使用[無伺服器](https://azure.com/serverless)架構的方法有很多種。</span><span class="sxs-lookup"><span data-stu-id="8331a-104">There are many approaches to using [serverless](https://azure.com/serverless) architectures.</span></span> <span data-ttu-id="8331a-105">本章會探索整合無伺服器的常見架構範例。</span><span class="sxs-lookup"><span data-stu-id="8331a-105">This chapter explores examples of common architectures that integrate serverless.</span></span> <span data-ttu-id="8331a-106">它也涵蓋在執行無伺服器時可能會造成額外挑戰或需要額外考慮的顧慮。</span><span class="sxs-lookup"><span data-stu-id="8331a-106">It also covers concerns that may pose additional challenges or require extra consideration when implementing serverless.</span></span> <span data-ttu-id="8331a-107">最後會提供幾個說明各種無伺服器使用案例的設計範例。</span><span class="sxs-lookup"><span data-stu-id="8331a-107">Finally, several design examples are provided that illustrate various serverless use cases.</span></span>

<span data-ttu-id="8331a-108">無伺服器主機通常會使用現有的容器型或 PaaS 層來管理無伺服器實例。</span><span class="sxs-lookup"><span data-stu-id="8331a-108">Serverless hosts often use an existing container-based or PaaS layer to manage the serverless instances.</span></span> <span data-ttu-id="8331a-109">例如, Azure Functions 是以[Azure App Service](https://docs.microsoft.com/azure/app-service/)為基礎。</span><span class="sxs-lookup"><span data-stu-id="8331a-109">For example, Azure Functions is based on [Azure App Service](https://docs.microsoft.com/azure/app-service/).</span></span> <span data-ttu-id="8331a-110">App Service 可用來向外延展實例, 以及管理執行 Azure Functions 程式碼的執行時間。</span><span class="sxs-lookup"><span data-stu-id="8331a-110">The App Service is used to scale out instances and manage the runtime that executes Azure Functions code.</span></span> <span data-ttu-id="8331a-111">對於以 Windows 為基礎的函式, 主機會以 PaaS 的形式執行, 並相應放大 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="8331a-111">For Windows-based functions, the host runs as PaaS and scales out the .NET runtime.</span></span> <span data-ttu-id="8331a-112">對於以 Linux 為基礎的函式, 主機會利用容器。</span><span class="sxs-lookup"><span data-stu-id="8331a-112">For Linux-based functions, the host leverages containers.</span></span>

![Azure Functions 架構](./media/azure-functions-architecture.png)

<span data-ttu-id="8331a-114">Webjob 核心會提供函數的執行內容。</span><span class="sxs-lookup"><span data-stu-id="8331a-114">The WebJobs Core provides an execution context for the function.</span></span> <span data-ttu-id="8331a-115">語言執行時間會執行腳本、執行程式庫, 並裝載目的語言的架構。</span><span class="sxs-lookup"><span data-stu-id="8331a-115">The Language Runtime runs scripts, executes libraries and hosts the framework for the target language.</span></span> <span data-ttu-id="8331a-116">例如, node.js 是用來執行 JavaScript 函式, 而 .NET Framework 則是用來執行C#函數。</span><span class="sxs-lookup"><span data-stu-id="8331a-116">For example, Node.js is used to run JavaScript functions and the .NET Framework is used to run C# functions.</span></span> <span data-ttu-id="8331a-117">您將會在本章稍後進一步瞭解語言和平臺選項。</span><span class="sxs-lookup"><span data-stu-id="8331a-117">You'll learn more about language and platform options later in this chapter.</span></span>

<span data-ttu-id="8331a-118">有些專案可能受益于對無伺服器採取「全功能」的方法。</span><span class="sxs-lookup"><span data-stu-id="8331a-118">Some projects may benefit from taking an "all-in" approach to serverless.</span></span> <span data-ttu-id="8331a-119">依賴微服務的應用程式可能會使用無伺服器技術來執行所有微服務。</span><span class="sxs-lookup"><span data-stu-id="8331a-119">Applications that rely heavily on microservices may implement all microservices using serverless technology.</span></span> <span data-ttu-id="8331a-120">大部分的應用程式都是混合式, 遵循多層式設計, 並針對有意義的元件使用無伺服器, 因為元件是模組化且可獨立擴充。</span><span class="sxs-lookup"><span data-stu-id="8331a-120">The majority of apps are hybrid, following an N-tier design and using serverless for the components that make sense because the components are modular and independently scalable.</span></span> <span data-ttu-id="8331a-121">為了説明您瞭解這些案例, 本節將逐步解說一些使用無伺服器的常見架構範例。</span><span class="sxs-lookup"><span data-stu-id="8331a-121">To help make sense of these scenarios, this section walks through some common architecture examples that use serverless.</span></span>

## <a name="full-serverless-back-end"></a><span data-ttu-id="8331a-122">完整無伺服器後端</span><span class="sxs-lookup"><span data-stu-id="8331a-122">Full serverless back end</span></span>

<span data-ttu-id="8331a-123">完整無伺服器後端適用于數種類型的案例, 特別是在建立新的或「環保欄位」應用程式時。</span><span class="sxs-lookup"><span data-stu-id="8331a-123">The full serverless back end is ideal for several types of scenarios, especially when building new or "green field" applications.</span></span> <span data-ttu-id="8331a-124">具有大型 Api 介面區的應用程式, 可能會受益于將每個 API 實作為無伺服器功能。</span><span class="sxs-lookup"><span data-stu-id="8331a-124">An application with a large surface area of APIs may benefit from implementing each API as a serverless function.</span></span> <span data-ttu-id="8331a-125">以微服務架構為基礎的應用程式是另一個可實作為完整無伺服器後端的範例。</span><span class="sxs-lookup"><span data-stu-id="8331a-125">Apps that are based on microservices architecture are another example that could be implemented as a full serverless back end.</span></span> <span data-ttu-id="8331a-126">微服務會透過各種不同的通訊協定彼此溝通。</span><span class="sxs-lookup"><span data-stu-id="8331a-126">The microservices communicate over various protocols with each other.</span></span> <span data-ttu-id="8331a-127">特定案例包括:</span><span class="sxs-lookup"><span data-stu-id="8331a-127">Specific scenarios include:</span></span>

* <span data-ttu-id="8331a-128">以 API 為基礎的 SaaS 產品 (例如: 財務付款處理器)。</span><span class="sxs-lookup"><span data-stu-id="8331a-128">API-based SaaS products (example: financial payments processor).</span></span>
* <span data-ttu-id="8331a-129">訊息驅動的應用程式 (例如: 裝置監視解決方案)。</span><span class="sxs-lookup"><span data-stu-id="8331a-129">Message-driven applications (example: device monitoring solution).</span></span>
* <span data-ttu-id="8331a-130">著重于服務間整合的應用程式 (例如: 航空公司預約應用程式)。</span><span class="sxs-lookup"><span data-stu-id="8331a-130">Apps focused on integration between services (example: airline booking application).</span></span>
* <span data-ttu-id="8331a-131">定期執行的進程 (例如: 以計時器為基礎的資料庫清理)。</span><span class="sxs-lookup"><span data-stu-id="8331a-131">Processes that run periodically (example: timer-based database clean-up).</span></span>
* <span data-ttu-id="8331a-132">著重于資料轉換的應用程式 (例如: 檔案上傳所觸發的匯入)。</span><span class="sxs-lookup"><span data-stu-id="8331a-132">Apps focused on data transformation (example: import triggered by file upload).</span></span>
* <span data-ttu-id="8331a-133">解壓縮轉換和載入 (ETL) 進程。</span><span class="sxs-lookup"><span data-stu-id="8331a-133">Extract Transform and Load (ETL) processes.</span></span>

<span data-ttu-id="8331a-134">本檔稍後會涵蓋其他更具體的使用案例。</span><span class="sxs-lookup"><span data-stu-id="8331a-134">There are other, more specific use cases that are covered later in this document.</span></span>

## <a name="monoliths-and-starving-the-beast"></a><span data-ttu-id="8331a-135">是開化「和 "starvation the beast"</span><span class="sxs-lookup"><span data-stu-id="8331a-135">Monoliths and "starving the beast"</span></span>

<span data-ttu-id="8331a-136">常見的挑戰是將現有的整合型應用程式遷移至雲端。</span><span class="sxs-lookup"><span data-stu-id="8331a-136">A common challenge is migrating an existing monolithic application to the cloud.</span></span> <span data-ttu-id="8331a-137">最具風險的方法是將「隨即轉移」完全放在虛擬機器上。</span><span class="sxs-lookup"><span data-stu-id="8331a-137">The least risky approach is to "lift and shift" entirely onto virtual machines.</span></span> <span data-ttu-id="8331a-138">許多商店偏好使用遷移來將其程式碼基底現代化。</span><span class="sxs-lookup"><span data-stu-id="8331a-138">Many shops prefer to use the migration as an opportunity to modernize their code base.</span></span> <span data-ttu-id="8331a-139">實際的遷移方法稱為「starvation beast」。</span><span class="sxs-lookup"><span data-stu-id="8331a-139">A practical approach to migration is called "starving the beast."</span></span> <span data-ttu-id="8331a-140">在此案例中, 單體會以「原樣」進行遷移, 以開始使用。</span><span class="sxs-lookup"><span data-stu-id="8331a-140">In this scenario, the monolith is migrated "as is" to start with.</span></span> <span data-ttu-id="8331a-141">然後, 會現代化選取的服務。</span><span class="sxs-lookup"><span data-stu-id="8331a-141">Then, selected services are modernized.</span></span> <span data-ttu-id="8331a-142">在某些情況下, 服務的簽章等同于原始的: 它只會裝載為函式。</span><span class="sxs-lookup"><span data-stu-id="8331a-142">In some cases, the signature of the service is identical to the original: it simply is hosted as a function.</span></span> <span data-ttu-id="8331a-143">用戶端會更新為使用新的服務, 而不是單體端點。</span><span class="sxs-lookup"><span data-stu-id="8331a-143">Clients are updated to use the new service rather than the monolith endpoint.</span></span> <span data-ttu-id="8331a-144">在過渡期間, 諸如資料庫複寫之類的步驟可讓微服務裝載自己的儲存體, 即使單體仍在處理交易時也一樣。</span><span class="sxs-lookup"><span data-stu-id="8331a-144">In the interim, steps such as database replication enable microservices to host their own storage even when transactions are still handled by the monolith.</span></span> <span data-ttu-id="8331a-145">最後, 所有用戶端都會遷移到新的服務。</span><span class="sxs-lookup"><span data-stu-id="8331a-145">Eventually, all clients are migrated onto the new services.</span></span> <span data-ttu-id="8331a-146">單體是 "耗盡" (其服務不再被呼叫), 直到所有功能都已被取代為止。</span><span class="sxs-lookup"><span data-stu-id="8331a-146">The monolith is "starved" (its services no longer called) until all functionality has been replaced.</span></span> <span data-ttu-id="8331a-147">無伺服器和 proxy 的組合可加速此項遷移。</span><span class="sxs-lookup"><span data-stu-id="8331a-147">The combination of serverless and proxies can facilitate much of this migration.</span></span>

![無伺服器單體遷移](./media/serverless-monolith-migration.png)

<span data-ttu-id="8331a-149">若要深入瞭解這種方法, 請觀看影片:透過[無伺服器 Azure Functions 將您的應用程式帶入雲端](https://channel9.msdn.com/Events/Connect/2017/E102)。</span><span class="sxs-lookup"><span data-stu-id="8331a-149">To learn more about this approach, watch the video: [Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/Events/Connect/2017/E102).</span></span>

## <a name="web-apps"></a><span data-ttu-id="8331a-150">Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="8331a-150">Web apps</span></span>

<span data-ttu-id="8331a-151">Web apps 是無伺服器應用程式的絕佳候選項目。</span><span class="sxs-lookup"><span data-stu-id="8331a-151">Web apps are great candidates for serverless applications.</span></span> <span data-ttu-id="8331a-152">現在 web 應用程式有兩種常見的方法: 伺服器驅動和用戶端驅動 (例如單一頁面應用程式或 SPA)。</span><span class="sxs-lookup"><span data-stu-id="8331a-152">There are two common approaches to web apps today: server-driven, and client-driven (such as Single Page Application or SPA).</span></span> <span data-ttu-id="8331a-153">伺服器導向的 web 應用程式通常會使用中介軟體層來發出 API 呼叫來呈現 web UI。</span><span class="sxs-lookup"><span data-stu-id="8331a-153">Server-driven web apps typically use a middleware layer to issue API calls to render the web UI.</span></span> <span data-ttu-id="8331a-154">SPA 應用程式會直接從瀏覽器進行 REST API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="8331a-154">SPA applications make REST API calls directly from the browser.</span></span> <span data-ttu-id="8331a-155">在這兩種情況下, 無伺服器可以提供必要的商務邏輯來容納中介軟體或 REST API 要求。</span><span class="sxs-lookup"><span data-stu-id="8331a-155">In both scenarios, serverless can accommodate the middleware or REST API request by providing the necessary business logic.</span></span> <span data-ttu-id="8331a-156">常見的架構是建立輕量靜態 web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8331a-156">A common architecture is to stand up a lightweight static web server.</span></span> <span data-ttu-id="8331a-157">單一頁面應用程式 (SPA) 可提供 HTML、CSS、JavaScript 和其他瀏覽器資產。</span><span class="sxs-lookup"><span data-stu-id="8331a-157">The Single Page Application (SPA) serves HTML, CSS, JavaScript, and other browser assets.</span></span> <span data-ttu-id="8331a-158">然後, web 應用程式會連線到微服務後端。</span><span class="sxs-lookup"><span data-stu-id="8331a-158">The web app then connects to a microservices back end.</span></span>

## <a name="mobile-back-ends"></a><span data-ttu-id="8331a-159">行動後端</span><span class="sxs-lookup"><span data-stu-id="8331a-159">Mobile back ends</span></span>

<span data-ttu-id="8331a-160">無伺服器應用程式的事件驅動架構, 使其成為行動後端的理想選擇。</span><span class="sxs-lookup"><span data-stu-id="8331a-160">The event-driven paradigm of serverless apps makes them ideal as mobile back ends.</span></span> <span data-ttu-id="8331a-161">行動裝置會觸發事件, 並執行無伺服器程式碼以滿足要求。</span><span class="sxs-lookup"><span data-stu-id="8331a-161">The mobile device triggers the events and the serverless code executes to satisfy requests.</span></span> <span data-ttu-id="8331a-162">利用無伺服器模型可讓開發人員增強商務邏輯, 而不需要部署完整的應用程式更新。</span><span class="sxs-lookup"><span data-stu-id="8331a-162">Taking advantage of a serverless model enables developers to enhance business logic without having to deploy a full application update.</span></span> <span data-ttu-id="8331a-163">無伺服器方法也可讓小組同時共用端點和工作。</span><span class="sxs-lookup"><span data-stu-id="8331a-163">The serverless approach also enables teams to share endpoints and work in parallel.</span></span>

<span data-ttu-id="8331a-164">行動開發人員可以建立商務邏輯, 而不需要成為伺服器端的專家。</span><span class="sxs-lookup"><span data-stu-id="8331a-164">Mobile developers can build business logic without becoming experts on the server side.</span></span> <span data-ttu-id="8331a-165">傳統上, 連接到內部部署服務的 mobile apps。</span><span class="sxs-lookup"><span data-stu-id="8331a-165">Traditionally, mobile apps connected to on-premises services.</span></span> <span data-ttu-id="8331a-166">建立服務層需要瞭解伺服器平臺和程式設計範例。</span><span class="sxs-lookup"><span data-stu-id="8331a-166">Building the service layer required understanding the server platform and programming paradigm.</span></span> <span data-ttu-id="8331a-167">開發人員使用作業來布建伺服器並適當地進行設定。</span><span class="sxs-lookup"><span data-stu-id="8331a-167">Developers worked with operations to provision servers and configure them appropriately.</span></span> <span data-ttu-id="8331a-168">有時候在建立部署管線時, 會花費數天或甚至數周的時間。</span><span class="sxs-lookup"><span data-stu-id="8331a-168">Sometimes days or even weeks were spent on building a deployment pipeline.</span></span> <span data-ttu-id="8331a-169">所有這些挑戰都是由無伺服器來解決。</span><span class="sxs-lookup"><span data-stu-id="8331a-169">All of these challenges are addressed by serverless.</span></span>

<span data-ttu-id="8331a-170">無伺服器會將伺服器端相依性抽象化, 並可讓開發人員專注于商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="8331a-170">Serverless abstracts the server-side dependencies and enables the developer to focus on business logic.</span></span> <span data-ttu-id="8331a-171">例如, 使用 JavaScript 架構來建立應用程式的行動開發人員, 也可以使用 JavaScript 建立無伺服器功能。</span><span class="sxs-lookup"><span data-stu-id="8331a-171">For example, a mobile developer who builds apps using a JavaScript framework can build serverless functions with JavaScript as well.</span></span> <span data-ttu-id="8331a-172">無伺服器主機會管理作業系統、裝載程式碼的 node.js 實例、封裝相依性等等。</span><span class="sxs-lookup"><span data-stu-id="8331a-172">The serverless host manages the operating system, a Node.js instance to host the code, package dependencies, and more.</span></span> <span data-ttu-id="8331a-173">開發人員會提供一組簡單的輸入和標準的輸出範本。</span><span class="sxs-lookup"><span data-stu-id="8331a-173">The developer is provided a simple set of inputs and a standard template for outputs.</span></span> <span data-ttu-id="8331a-174">然後他們可以專注于建立和測試商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="8331a-174">They then can focus on building and testing the business logic.</span></span> <span data-ttu-id="8331a-175">因此, 他們可以使用現有的技能來建立行動應用程式的後端邏輯, 而不需要學習新的平臺或成為「伺服器端開發人員」。</span><span class="sxs-lookup"><span data-stu-id="8331a-175">They're therefore able to use existing skills to build the back-end logic for the mobile app without having to learn new platforms or become a "server-side developer."</span></span>

![無伺服器行動後端](./media/serverless-mobile-backend.png)

<span data-ttu-id="8331a-177">大部分的雲端提供者都提供以行動為基礎的無伺服器產品, 可簡化整個行動開發生命週期。</span><span class="sxs-lookup"><span data-stu-id="8331a-177">Most cloud providers offer mobile-based serverless products that simplify the entire mobile development lifecycle.</span></span> <span data-ttu-id="8331a-178">這些產品可以自動布建資料庫以保存資料、處理 DevOps 考慮、提供雲端式組建和測試架構, 以及使用開發人員慣用的語言撰寫商務程式腳本的能力。</span><span class="sxs-lookup"><span data-stu-id="8331a-178">The products may automate the provisioning of databases to persist data, handle DevOps concerns, provide cloud-based builds and testing frameworks and the ability to script business processes using the developer's preferred language.</span></span> <span data-ttu-id="8331a-179">遵循以行動為中心的無伺服器方法, 可以簡化程式。</span><span class="sxs-lookup"><span data-stu-id="8331a-179">Following a mobile-centric serverless approach can streamline the process.</span></span> <span data-ttu-id="8331a-180">無伺服器會移除布建、設定和維護行動後端伺服器的巨大負擔。</span><span class="sxs-lookup"><span data-stu-id="8331a-180">Serverless removes the tremendous overhead of provisioning, configuring, and maintaining servers for the mobile back end.</span></span>

## <a name="internet-of-things-iot"></a><span data-ttu-id="8331a-181">物聯網 (IoT)</span><span class="sxs-lookup"><span data-stu-id="8331a-181">Internet of Things (IoT)</span></span>

<span data-ttu-id="8331a-182">IoT 指的是與網路在一起的實體物件。</span><span class="sxs-lookup"><span data-stu-id="8331a-182">IoT refers to physical objects that are networked together.</span></span> <span data-ttu-id="8331a-183">它們有時稱為「已連線的裝置」或「智慧型裝置」。</span><span class="sxs-lookup"><span data-stu-id="8331a-183">They're sometimes referred to as "connected devices" or "smart devices."</span></span> <span data-ttu-id="8331a-184">來自車輛和自動販賣機器的所有內容都可以連接, 並將資訊從清查範圍傳送到感應器資料, 例如溫度和濕度。</span><span class="sxs-lookup"><span data-stu-id="8331a-184">Everything from cars and vending machines may be connected and send information ranging from inventory to sensor data such as temperature and humidity.</span></span> <span data-ttu-id="8331a-185">在企業中, IoT 透過監控和自動化來供應商務程式改善。</span><span class="sxs-lookup"><span data-stu-id="8331a-185">In the enterprise, IoT provides business process improvements through monitoring and automation.</span></span> <span data-ttu-id="8331a-186">IoT 資料可用來調節大型倉儲中的氣候, 或透過供應鏈來追蹤清查。</span><span class="sxs-lookup"><span data-stu-id="8331a-186">IoT data may be used to regulate the climate in a large warehouse or track inventory through the supply chain.</span></span> <span data-ttu-id="8331a-187">IoT 可以在偵測到冒煙時, 有意義的潑濺並呼叫火災部門。</span><span class="sxs-lookup"><span data-stu-id="8331a-187">IoT can sense chemical spills and call the fire department when smoke is detected.</span></span>

<span data-ttu-id="8331a-188">大量的裝置和資訊通常會指示事件驅動架構來路由傳送和處理訊息。</span><span class="sxs-lookup"><span data-stu-id="8331a-188">The sheer volume of devices and information often dictates an event-driven architecture to route and process messages.</span></span> <span data-ttu-id="8331a-189">無伺服器是理想的解決方案, 原因如下:</span><span class="sxs-lookup"><span data-stu-id="8331a-189">Serverless is an ideal solution for several reasons:</span></span>

* <span data-ttu-id="8331a-190">可在裝置和資料量增加時進行調整。</span><span class="sxs-lookup"><span data-stu-id="8331a-190">Enables scale as the volume of devices and data increases.</span></span>
* <span data-ttu-id="8331a-191">配合新增端點, 以支援新的裝置和感應器。</span><span class="sxs-lookup"><span data-stu-id="8331a-191">Accommodates adding new endpoints to support new devices and sensors.</span></span>
* <span data-ttu-id="8331a-192">有助於獨立的版本控制, 讓開發人員可以更新特定裝置的商務邏輯, 而不需要部署整個系統。</span><span class="sxs-lookup"><span data-stu-id="8331a-192">Facilitates independent versioning so developers can update the business logic for a specific device without having to deploy the entire system.</span></span>
* <span data-ttu-id="8331a-193">復原能力和較少的停機時間。</span><span class="sxs-lookup"><span data-stu-id="8331a-193">Resiliency and less downtime.</span></span>

<span data-ttu-id="8331a-194">IoT 的普及率產生了數個無伺服器產品, 特別著重于 IoT 考慮, 例如[Azure IoT 中樞](https://docs.microsoft.com/azure/iot-hub)。</span><span class="sxs-lookup"><span data-stu-id="8331a-194">The pervasiveness of IoT has resulted in several serverless products that focus specifically on IoT concerns, such as [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub).</span></span> <span data-ttu-id="8331a-195">無伺服器會自動化工作, 例如裝置註冊、原則強制執行、追蹤, 甚至是將程式碼部署到*邊緣*裝置。</span><span class="sxs-lookup"><span data-stu-id="8331a-195">Serverless automates tasks such as device registration, policy enforcement, tracking, and even deployment of code to devices at *the edge*.</span></span> <span data-ttu-id="8331a-196">邊緣是指連線到網際網路的感應器和傳動器等裝置, 而不是作用中的部分。</span><span class="sxs-lookup"><span data-stu-id="8331a-196">The edge refers to devices like sensors and actuators that are connected to, but not an active part of, the Internet.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8331a-197">[上一頁](architecture-approaches.md)
>[下一頁](serverless-architecture-considerations.md)</span><span class="sxs-lookup"><span data-stu-id="8331a-197">[Previous](architecture-approaches.md)
[Next](serverless-architecture-considerations.md)</span></span>