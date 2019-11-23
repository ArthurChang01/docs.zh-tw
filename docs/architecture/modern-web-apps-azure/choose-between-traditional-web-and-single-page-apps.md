---
title: 在傳統 Web 應用程式和單頁應用程式之間作選擇
description: 了解建置 Web 應用程式時，如何在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇。
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 9ede64249705aba3f22a9663b8a258e41f030aca
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739451"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a><span data-ttu-id="7ff9b-103">在傳統 Web 應用程式和單頁應用程式 (SPA) 之間作選擇</span><span class="sxs-lookup"><span data-stu-id="7ff9b-103">Choose Between Traditional Web Apps and Single Page Apps (SPAs)</span></span>

> <span data-ttu-id="7ff9b-104">「Atwood 定律：任何可以用 JavaScript 撰寫的應用程式，最後都將以 JavaScript 撰寫。」</span><span class="sxs-lookup"><span data-stu-id="7ff9b-104">"Atwood's Law: Any application that can be written in JavaScript, will eventually be written in JavaScript."</span></span>  
> <span data-ttu-id="7ff9b-105">_\- Jeff Atwood_</span><span class="sxs-lookup"><span data-stu-id="7ff9b-105">_\- Jeff Atwood_</span></span>

<span data-ttu-id="7ff9b-106">現在有兩種建置 Web 應用程式的通用方法：在伺服器上執行大多數應用程式邏輯的傳統 Web 應用程式，以及執行大多數使用者介面邏輯的單頁應用程式 (SPA)，主要使用 Web API 與 Web 伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-106">There are two general approaches to building web applications today: traditional web applications that perform most of the application logic on the server, and single page applications (SPAs) that perform most of the user interface logic in a web browser, communicating with the web server primarily using web APIs.</span></span> <span data-ttu-id="7ff9b-107">混合式方法也是可能的，最簡單方法為在較大的傳統 Web 應用程式中，裝載一或多個豐富、類似 SPA 的子應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-107">A hybrid approach is also possible, the simplest being host one or more rich SPA-like sub-applications within a larger traditional web application.</span></span>

<span data-ttu-id="7ff9b-108">您應該使用傳統 Web 應用程式的時機：</span><span class="sxs-lookup"><span data-stu-id="7ff9b-108">You should use traditional web applications when:</span></span>

- <span data-ttu-id="7ff9b-109">應用程式用戶端的需求簡單或甚至是唯讀。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-109">Your application's client-side requirements are simple or even read-only.</span></span>

- <span data-ttu-id="7ff9b-110">應用程式需要在不支援 JavaScript 的瀏覽器中運作。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-110">Your application needs to function in browsers without JavaScript support.</span></span>

- <span data-ttu-id="7ff9b-111">您的小組不熟悉 JavaScript 或 TypeScript 開發技術。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-111">Your team is unfamiliar with JavaScript or TypeScript development techniques.</span></span>

<span data-ttu-id="7ff9b-112">您應該使用 SPA 的時機：</span><span class="sxs-lookup"><span data-stu-id="7ff9b-112">You should use a SPA when:</span></span>

- <span data-ttu-id="7ff9b-113">應用程式必須公開具有許多功能的豐富使用者介面。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-113">Your application must expose a rich user interface with many features.</span></span>

- <span data-ttu-id="7ff9b-114">您的小組熟悉 JavaScript 及/或 TypeScript 開發。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-114">Your team is familiar with JavaScript and/or TypeScript development.</span></span>

- <span data-ttu-id="7ff9b-115">您的應用程式必須已針對其他 (內部或公開) 用戶端公開 API。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-115">Your application must already expose an API for other (internal or public) clients.</span></span>

<span data-ttu-id="7ff9b-116">此外，SPA 架構需要更多的架構和安全性專業知識。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-116">Additionally, SPA frameworks require greater architectural and security expertise.</span></span> <span data-ttu-id="7ff9b-117">由於頻繁的更新及新的架構，SPA 架構會經歷比傳統 Web 應用程式更大的變換。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-117">They experience greater churn due to frequent updates and new frameworks than traditional web applications.</span></span> <span data-ttu-id="7ff9b-118">設定自動化的建置和部署程序、使用容器等部署選項，比傳統 Web 應用程式更難用於 SPA 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-118">Configuring automated build and deployment processes and utilizing deployment options like containers are more difficult with SPA applications than traditional web apps.</span></span>

<span data-ttu-id="7ff9b-119">基於這些考量，必須權衡 SPA 模型使用者體驗的改善。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-119">Improvements in user experience made possible by SPA model must be weighed against these considerations.</span></span>

## <a name="blazor"></a><span data-ttu-id="7ff9b-120">Blazor</span><span class="sxs-lookup"><span data-stu-id="7ff9b-120">Blazor</span></span>

<span data-ttu-id="7ff9b-121">ASP.NET Core 3.0 推出了新的模型，用以建置豐富的互動式可組合 UI，該模型稱為 Blazor。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-121">ASP.NET Core 3.0 introduces a new model for building rich, interactive, and composable UI called Blazor.</span></span> <span data-ttu-id="7ff9b-122">Blazor 伺服器端可以讓開發人員在伺服器上建立含有 Razor 的 UI，並將此程式碼傳遞至瀏覽器，並使用[WebAssembly](https://webassembly.org/)來執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-122">Blazor server-side allows developers to build UI with Razor on the server and for this code to be delivered to the browser and executed client-side using [WebAssembly](https://webassembly.org/).</span></span> <span data-ttu-id="7ff9b-123">ASP.NET Core 3.0 仍在開發，但您將會在此電子書的 3.0 更新中看到這項技術的更多功能。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-123">ASP.NET Core 3.0 is still under development, but you should expect to see more on this technology in the 3.0 update to this e-book.</span></span> <span data-ttu-id="7ff9b-124">如需 Blazor 的詳細資訊，請參閱[開始使用 Blazor](https://blazor.net/docs/get-started.html)。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-124">For more information about Blazor, see [Get started with Blazor](https://blazor.net/docs/get-started.html).</span></span>

## <a name="when-to-choose-traditional-web-apps"></a><span data-ttu-id="7ff9b-125">選擇傳統 Web 應用程式的時機</span><span class="sxs-lookup"><span data-stu-id="7ff9b-125">When to choose traditional web apps</span></span>

<span data-ttu-id="7ff9b-126">以下將更詳盡說明前述挑選傳統 Web 應用程式的理由。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-126">The following is a more detailed explanation of the previously stated reasons for picking traditional web applications.</span></span>

<span data-ttu-id="7ff9b-127">**您的應用程式具有簡單且可能是唯讀的用戶端需求**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-127">**Your application has simple, possibly read-only, client-side requirements**</span></span>

<span data-ttu-id="7ff9b-128">許多 Web 應用程式主要以唯讀方式供絕大多數使用者使用。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-128">Many web applications are primarily consumed in a read-only fashion by the vast majority of their users.</span></span> <span data-ttu-id="7ff9b-129">唯讀 (或主要為讀取) 的應用程式往往比維護和操作大量狀態的應用程式簡單許多。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-129">Read-only (or read-mostly) applications tend to be much simpler than those that maintain and manipulate a great deal of state.</span></span> <span data-ttu-id="7ff9b-130">例如，搜尋引擎可能包含文字方塊的單一進入點，和用於顯示搜尋結果的第二個頁面。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-130">For example, a search engine might consist of a single entry point with a textbox and a second page for displaying search results.</span></span> <span data-ttu-id="7ff9b-131">匿名使用者可以輕鬆發出要求，且幾乎不需要用戶端邏輯。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-131">Anonymous users can easily make requests, and there is little need for client-side logic.</span></span> <span data-ttu-id="7ff9b-132">同樣地，部落格或內容管理系統的公開應用程式，通常主要由幾乎沒有用戶端行為的內容所組成。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-132">Likewise, a blog or content management system's public-facing application usually consists mainly of content with little client-side behavior.</span></span> <span data-ttu-id="7ff9b-133">這類應用程式很容易建立為伺服器型的傳統 Web 應用程式；在 Web 伺服器上執行邏輯並轉譯 HTML 使其顯示於瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-133">Such applications are easily built as traditional server-based web applications which perform logic on the web server and render HTML to be displayed in the browser.</span></span> <span data-ttu-id="7ff9b-134">網站的每個獨特頁面都有自己的 URL，可透過搜尋引擎加上書籤並編製索引 (此為預設，不需另外將此新增為應用程式的個別功能)，在此情況下也是明顯的優勢。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-134">The fact that each unique page of the site has its own URL that can be bookmarked and indexed by search engines (by default, without having to add this as a separate feature of the application) is also a clear benefit in such scenarios.</span></span>

<span data-ttu-id="7ff9b-135">**應用程式需要在不支援 JavaScript 的瀏覽器中運作**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-135">**Your application needs to function in browsers without JavaScript support**</span></span>

<span data-ttu-id="7ff9b-136">需要在有限或不支援 JavaScript 之瀏覽器中運作的 Web 應用程式，應該使用傳統 Web 應用程式工作流程來撰寫 (或至少能夠改為使用這種行為)。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-136">Web applications that need to function in browsers with limited or no JavaScript support should be written using traditional web app workflows (or at least be able to fall back to such behavior).</span></span> <span data-ttu-id="7ff9b-137">SPA 需要用戶端 JavaScript 才能運作；如果不可用，則 SPA 就不是好選擇。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-137">SPAs require client-side JavaScript in order to function; if it's not available, SPAs are not a good choice.</span></span>

<span data-ttu-id="7ff9b-138">**您的小組不熟悉 JavaScript 或 TypeScript 開發技術**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-138">**Your team is unfamiliar with JavaScript or TypeScript development techniques**</span></span>

<span data-ttu-id="7ff9b-139">如果您的小組不熟悉 JavaScript 或 TypeScript 但熟悉伺服器端 Web 應用程式開發，那麼比起 SPA 應用程式，他們可能可以更快交付傳統 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-139">If your team is unfamiliar with JavaScript or TypeScript, but is familiar with server-side web application development, then they will probably be able to deliver a traditional web app more quickly than a SPA.</span></span> <span data-ttu-id="7ff9b-140">除非目標是學習編程 SPA 或是需要 SPA 提供的使用者體驗，否則對於已經熟悉建置傳統 Web 應用程式的小組而言，傳統 Web 應用程式是更具生產力的選擇。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-140">Unless learning to program SPAs is a goal, or the user experience afforded by a SPA is required, traditional web apps are a more productive choice for teams who are already familiar with building them.</span></span>

## <a name="when-to-choose-spas"></a><span data-ttu-id="7ff9b-141">選擇 SPA 的時機</span><span class="sxs-lookup"><span data-stu-id="7ff9b-141">When to choose SPAs</span></span>

<span data-ttu-id="7ff9b-142">以下將詳細說明應何時為您的 Web 應用程式選擇單頁應用程式開發樣式。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-142">The following is a more detailed explanation of when to choose a Single Page Applications style of development for your web app.</span></span>

<span data-ttu-id="7ff9b-143">**應用程式必須公開具有許多功能的豐富使用者介面**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-143">**Your application must expose a rich user interface with many features**</span></span>

<span data-ttu-id="7ff9b-144">SPAs 可以支援豐富的用戶端功能，且當使用者採取動作或在應用程式各區域間巡覽時，也不需重新載入頁面。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-144">SPAs can support rich client-side functionality that doesn't require reloading the page as users take actions or navigate between areas of the app.</span></span> <span data-ttu-id="7ff9b-145">SPA 可以更快速載入、在背景擷取資料、對個別使用者的動作回應更快，因為重新載入完整頁面的情況很少。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-145">SPAs can load more quickly, fetching data in the background, and individual user actions are more responsive since full page reloads are rare.</span></span> <span data-ttu-id="7ff9b-146">SPA 可支援增量更新，不需使用者按一下按鈕來提交表單即可儲存部分完成的表單或文件。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-146">SPAs can support incremental updates, saving partially completed forms or documents without the user having to click a button to submit a form.</span></span> <span data-ttu-id="7ff9b-147">SPA 比傳統應用程式更容易支援豐富的用戶端行為，例如拖放操作。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-147">SPAs can support rich client-side behaviors, such as drag-and-drop, much more readily than traditional applications.</span></span> <span data-ttu-id="7ff9b-148">SPA 可以設計為以離線模式執行；對用戶端模型進行的更新在其重新建立連線之後，最終會同步回伺服器。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-148">SPAs can be designed to run in a disconnected mode, making updates to a client-side model that are eventually synchronized back to the server once a connection is re-established.</span></span> <span data-ttu-id="7ff9b-149">如果您的應用程式需要包含豐富的功能，超出了典型 HTML 表單能提供的範圍，則應選擇 SPA 樣式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-149">You should choose a SPA style application if your app's requirements include rich functionality that goes beyond what typical HTML forms offer.</span></span>

<span data-ttu-id="7ff9b-150">請注意，SPA 經常需要實作內建於傳統 Web 應用程式的功能，例如在反映目前作業之網址列中顯示有意義的 URL (允許使用者將此 URL 加上書籤或深層連結以返回至此 URL)。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-150">Note that frequently SPAs need to implement features that are built-in to traditional web apps, such as displaying a meaningful URL in the address bar reflecting the current operation (and allowing users to bookmark or deep link to this URL to return to it).</span></span> <span data-ttu-id="7ff9b-151">SPA 也應允許使用者使用瀏覽器的 [上一頁] 和 [下一頁] 按鈕，且不產生意外的結果。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-151">SPAs also should allow users to use the browser's back and forward buttons with results that won't surprise them.</span></span>

<span data-ttu-id="7ff9b-152">**您的小組熟悉 JavaScript 及/或 TypeScript 開發**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-152">**Your team is familiar with JavaScript and/or TypeScript development**</span></span>

<span data-ttu-id="7ff9b-153">撰寫 SPA 需要熟悉 JavaScript 及/或 TypeScript，以及用戶端程式設計技術與程式庫。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-153">Writing SPAs requires familiarity with JavaScript and/or TypeScript and client-side programming techniques and libraries.</span></span> <span data-ttu-id="7ff9b-154">您的小組應能夠使用 Angular 等 SPA 架構來撰寫現代化 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-154">Your team should be competent in writing modern JavaScript using a SPA framework like Angular.</span></span>

> ### <a name="references--spa-frameworks"></a><span data-ttu-id="7ff9b-155">參考資料 – SPA 架構</span><span class="sxs-lookup"><span data-stu-id="7ff9b-155">References – SPA Frameworks</span></span>
>
> - <span data-ttu-id="7ff9b-156">**Angular**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-156">**Angular**</span></span>  
>   <https://angular.io>
> - <span data-ttu-id="7ff9b-157">**JavaScript 架構的比較**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-157">**Comparison of JavaScript Frameworks**</span></span>  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

<span data-ttu-id="7ff9b-158">**您的應用程式必須已針對其他 (內部或公開) 用戶端公開 API**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-158">**Your application must already expose an API for other (internal or public) clients**</span></span>

<span data-ttu-id="7ff9b-159">如果您已經支援其他用戶端使用的 Web API，則建立利用這些 API 的 SPA 實作會較容易，不用重現伺服器端格式中的邏輯。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-159">If you're already supporting a web API for use by other clients, it may require less effort to create a SPA implementation that leverages these APIs rather than reproducing the logic in server-side form.</span></span> <span data-ttu-id="7ff9b-160">當使用者與應用程式互動時，SPA 大量使用 Web API 來查詢及更新資料。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-160">SPAs make extensive use of web APIs to query and update data as users interact with the application.</span></span>

## <a name="decision-table--traditional-web-or-spa"></a><span data-ttu-id="7ff9b-161">決策表 – 傳統 Web 或 SPA</span><span class="sxs-lookup"><span data-stu-id="7ff9b-161">Decision table – Traditional Web or SPA</span></span>

<span data-ttu-id="7ff9b-162">下列決策表摘要列出在傳統 Web 應用程式和 SPA 之間作選擇時需要考慮的一些基本因素。</span><span class="sxs-lookup"><span data-stu-id="7ff9b-162">The following decision table summarizes some of the basic factors to consider when choosing between a traditional web application and a SPA.</span></span>

| <span data-ttu-id="7ff9b-163">**因素**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-163">**Factor**</span></span>                                           | <span data-ttu-id="7ff9b-164">**傳統 Web 應用程式**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-164">**Traditional Web App**</span></span> | <span data-ttu-id="7ff9b-165">**單一頁面應用程式**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-165">**Single Page Application**</span></span> |
| ---------------------------------------------------- | ----------------------- | --------------------------- |
| <span data-ttu-id="7ff9b-166">小組必須熟悉 JavaScript/TypeScript</span><span class="sxs-lookup"><span data-stu-id="7ff9b-166">Required Team Familiarity with JavaScript/TypeScript</span></span> | <span data-ttu-id="7ff9b-167">**最少**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-167">**Minimal**</span></span>             | <span data-ttu-id="7ff9b-168">**必要**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-168">**Required**</span></span>                |
| <span data-ttu-id="7ff9b-169">支援無指令碼的瀏覽器</span><span class="sxs-lookup"><span data-stu-id="7ff9b-169">Support Browsers without Scripting</span></span>                   | <span data-ttu-id="7ff9b-170">**支援**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-170">**Supported**</span></span>           | <span data-ttu-id="7ff9b-171">**不支援**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-171">**Not Supported**</span></span>           |
| <span data-ttu-id="7ff9b-172">最少的用戶端應用程式行為</span><span class="sxs-lookup"><span data-stu-id="7ff9b-172">Minimal Client-Side Application Behavior</span></span>             | <span data-ttu-id="7ff9b-173">**適用**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-173">**Well-Suited**</span></span>         | <span data-ttu-id="7ff9b-174">**大材小用**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-174">**Overkill**</span></span>                |
| <span data-ttu-id="7ff9b-175">內容豐富且複雜的使用者介面需求</span><span class="sxs-lookup"><span data-stu-id="7ff9b-175">Rich, Complex User Interface Requirements</span></span>            | <span data-ttu-id="7ff9b-176">**有限**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-176">**Limited**</span></span>             | <span data-ttu-id="7ff9b-177">**適用**</span><span class="sxs-lookup"><span data-stu-id="7ff9b-177">**Well-Suited**</span></span>             |

>[!div class="step-by-step"]
><span data-ttu-id="7ff9b-178">[上一頁](modern-web-applications-characteristics.md)
>[下一頁](architectural-principles.md)</span><span class="sxs-lookup"><span data-stu-id="7ff9b-178">[Previous](modern-web-applications-characteristics.md)
[Next](architectural-principles.md)</span></span>
