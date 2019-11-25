---
title: 將資料當做服務公開 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 71f26d7d41d112e13e6a77f0927c61d51b176b27
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975300"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a><span data-ttu-id="46fce-102">以服務形式公開您的資料（WCF Data Services）</span><span class="sxs-lookup"><span data-stu-id="46fce-102">Expose Your Data as a Service (WCF Data Services)</span></span>

<span data-ttu-id="46fce-103">WCF Data Services 與 Visual Studio 整合，可讓您更輕鬆地定義服務，以將您的資料公開為開放式資料通訊協定（OData）摘要。</span><span class="sxs-lookup"><span data-stu-id="46fce-103">WCF Data Services integrates with Visual Studio to enable you to more easily define services to expose your data as Open Data Protocol (OData) feeds.</span></span> <span data-ttu-id="46fce-104">建立公開 OData 摘要的資料服務包含下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="46fce-104">Creating a data service that exposes an OData feed involves the following basic steps:</span></span>

1. <span data-ttu-id="46fce-105">**定義資料模型。**</span><span class="sxs-lookup"><span data-stu-id="46fce-105">**Define the data model.**</span></span> <span data-ttu-id="46fce-106">WCF Data Services 原本就支援以[ADO.NET Entity Framework](../adonet/ef/index.md)為基礎的資料模型。</span><span class="sxs-lookup"><span data-stu-id="46fce-106">WCF Data Services natively supports data models that are based on the [ADO.NET Entity Framework](../adonet/ef/index.md).</span></span> <span data-ttu-id="46fce-107">如需詳細資訊，請參閱[如何：使用 ADO.NET 建立資料服務 Entity Framework 資料來源](create-a-data-service-using-an-adonet-ef-data-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="46fce-107">For more information, see [How to: Create a Data Service Using an ADO.NET Entity Framework Data Source](create-a-data-service-using-an-adonet-ef-data-wcf.md).</span></span>

     <span data-ttu-id="46fce-108">WCF Data Services 也支援以 common language runtime （CLR）物件為基礎的資料模型，其會傳回 <xref:System.Linq.IQueryable%601> 介面的實例。</span><span class="sxs-lookup"><span data-stu-id="46fce-108">WCF Data Services also supports data models that are based on common language runtime (CLR) objects that return an instance of the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="46fce-109">這樣可以讓您部署 .NET Framework 中以清單、陣列和集合為基礎的資料服務。</span><span class="sxs-lookup"><span data-stu-id="46fce-109">This enables you to deploy data services that are based on lists, arrays, and collections in the .NET Framework.</span></span> <span data-ttu-id="46fce-110">若要透過這些資料結構啟用建立、更新及刪除作業，您必須同時實作 <xref:System.Data.Services.IUpdatable> 介面。</span><span class="sxs-lookup"><span data-stu-id="46fce-110">To enable create, update, and delete operations over these data structures, you must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="46fce-111">如需詳細資訊，請參閱[如何：使用反映提供者建立資料服務](create-a-data-service-using-rp-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="46fce-111">For more information, see [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md).</span></span>

     <span data-ttu-id="46fce-112">針對更先進的案例，WCF Data Services 包含一組提供者，可讓您根據晚期繫結的資料類型來定義資料模型。</span><span class="sxs-lookup"><span data-stu-id="46fce-112">For more advanced scenarios, WCF Data Services includes a set of providers that enable you to define a data model based on late-bound data types.</span></span> <span data-ttu-id="46fce-113">如需詳細資訊，請參閱[自訂資料服務提供者](custom-data-service-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="46fce-113">For more information, see [Custom Data Service Providers](custom-data-service-providers-wcf-data-services.md).</span></span>

2. <span data-ttu-id="46fce-114">**建立資料服務。**</span><span class="sxs-lookup"><span data-stu-id="46fce-114">**Create the data service.**</span></span> <span data-ttu-id="46fce-115">最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱 `T` 型別。</span><span class="sxs-lookup"><span data-stu-id="46fce-115">The most basic data service exposes a class that inherits from the <xref:System.Data.Services.DataService%601> class, with a type `T` that is the namespace-qualified name of the entity container.</span></span> <span data-ttu-id="46fce-116">如需詳細資訊，請參閱 [Defining WCF Data Services](defining-wcf-data-services.md)的資訊。</span><span class="sxs-lookup"><span data-stu-id="46fce-116">For more information, see [Defining WCF Data Services](defining-wcf-data-services.md).</span></span>

3. <span data-ttu-id="46fce-117">**設定資料服務。**</span><span class="sxs-lookup"><span data-stu-id="46fce-117">**Configure the data service.**</span></span> <span data-ttu-id="46fce-118">根據預設，WCF Data Services 會停用實體容器所公開的資源存取權。</span><span class="sxs-lookup"><span data-stu-id="46fce-118">By default, WCF Data Services disables access to resources that are exposed by an entity container.</span></span> <span data-ttu-id="46fce-119"><xref:System.Data.Services.DataServiceConfiguration> 介面可讓您設定對資源和服務作業的存取、指定支援的 OData 版本，以及定義其他整個服務的行為，例如，批次行為或在單一回應中可傳回的最大實體數目。</span><span class="sxs-lookup"><span data-stu-id="46fce-119">The <xref:System.Data.Services.DataServiceConfiguration> interface enables you to configure access to resources and service operations, specify the supported version of OData, and to define other service-wide behaviors, such as batching behaviors or the maximum number of entities that can be returned in a single response.</span></span> <span data-ttu-id="46fce-120">如需詳細資訊，請參閱設定[資料服務](configuring-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="46fce-120">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

<span data-ttu-id="46fce-121">如需如何建立以 Northwind 範例資料庫為基礎的簡單資料服務的範例，請參閱[快速入門](quickstart-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="46fce-121">For an example of how to create a simple data service that is based on the Northwind sample database, see [Quickstart](quickstart-wcf-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46fce-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="46fce-122">See also</span></span>

- [<span data-ttu-id="46fce-123">使用者入門</span><span class="sxs-lookup"><span data-stu-id="46fce-123">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="46fce-124">概觀</span><span class="sxs-lookup"><span data-stu-id="46fce-124">Overview</span></span>](wcf-data-services-overview.md)
