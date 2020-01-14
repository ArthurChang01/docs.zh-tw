---
title: 快速入門 (WCF 資料服務)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: 43cd34ad02f1e2d212ff5e2ff4694591fbed52e5
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900953"
---
# <a name="quickstart-wcf-data-services"></a>快速入門 (WCF 資料服務)

本快速入門可協助您透過一系列支援[消費者入門](getting-started-with-wcf-data-services.md)主題的工作，熟悉 WCF Data Services 和開放式資料通訊協定（OData）。

## <a name="what-youll-learn"></a>您將了解

本快速入門中的第一個工作會示範如何建立資料服務，以公開 Northwind 範例資料庫中的 OData 摘要。 在後續的主題中，您將使用網頁瀏覽器來存取 OData 摘要，並使用用戶端程式庫建立使用 OData 摘要的 Windows Presentation Foundation （WPF）用戶端應用程式。

## <a name="prerequisites"></a>必要條件：

若要完成本快速入門，您必須安裝下列元件：

- Visual Studio

- SQL Server 的實例。 這包括 SQL Server Express （隨附于 Visual Studio 2015 的預設安裝中），或是 Visual Studio 2017 或更新版本中的**資料儲存和處理**工作負載的一部分。

- Northwind 範例資料庫。 若要下載此範例資料庫，請參閱下載頁面： [SQL Server 的範例資料庫](https://go.microsoft.com/fwlink/?linkid=24758)。

## <a name="wcf-data-services-quickstart-tasks"></a>WCF data services 快速入門工作

 [建立資料服務](creating-the-data-service.md)

 定義 ADO.NET 應用程式、定義資料模型、建立資料服務，並且啟用資源存取。

 [從網頁瀏覽器存取服務](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 從 Visual Studio 啟動服務，然後透過 Web 瀏覽器將 HTTP GET 要求提交至公開的摘要，以存取該服務。

 [建立 .NET Framework 用戶端應用程式](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 建立 WPF 應用程式來取用 OData 摘要、將資料系結至 Windows 控制項、變更繫結控制項中的資料，然後將變更傳回資料服務。

> [!NOTE]
> 您可以從[GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))下載已完成之快速入門版本中的專案檔案。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [開始快速入門](creating-the-data-service.md)

## <a name="see-also"></a>請參閱

- [ADO.NET Entity Framework](../adonet/ef/index.md)
