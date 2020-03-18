---
title: 邏輯架構與實體架構
description: 了解邏輯架構與實體架構之間的差異。
ms.date: 09/20/2018
ms.openlocfilehash: 8d1bfca190eb9b18d46625fa4afdec963eb07054
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834407"
---
# <a name="logical-architecture-versus-physical-architecture"></a>邏輯架構與實體架構

現在適合停下來討論邏輯架構與實體架構之間的差異，以及如何將這點應用在微服務架構應用程式的設計。

首先要知道的是，建置微服務並不需要使用任何特定技術。 例如，並非一定要有 Docker 容器，才能建立微服務架構。 這些微服務也可以當做一般處理序來執行。 微服務是邏輯架構。

此外，即使微服務可實際實作為單一服務、處理序或容器 (為了方便作業，這是 [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) 的初始版本中所採取的方法)，每當您建置由數十個或甚至是數百個服務所組成的大型複雜應用程式時，商務微服務與實體服務或容器之間也不一定需要有此同位。

這就是應用程式邏輯架構與實體架構之間的差異所在。 系統的邏輯架構和邏輯界限不一定會以一對一的方式對應至實體或部署架構。 這有可能發生，但並不常見。

雖然您可能已識別特定商務微服務或限定內容，但不表示為每個商務微服務建立單一服務 (例如 ASP.NET Web API) 或單一 Docker 容器一律為最佳實作方式。 以規則指出每個商務微服務必須使用單一服務或容器來實作會太嚴格。

因此，商務微服務或限定內容是邏輯架構，不一定會與實體架構一致。 重點是商務微服務或限定內容必須是自主的，這可藉由允許對程式碼和狀態獨立建立版本、進行部署和擴充來達成。

如圖 4-8 所示，目錄商務微服務可能是由數個服務或處理序所組成。 這些服務可以是多個 ASP.NET Web API 服務，或是使用 HTTP 或任何其他通訊協定的任何其他服務類型。 更重要的是，只要這些服務與相同的業務領域相關，就可以共用相同的資料。

![帶物理伺服器的目錄業務微服務圖。](./media/logical-versus-physical-architecture/multiple-physical-services.png)

**圖4-8**。 具有數項實體服務的商務微服務

範例中的服務會共用相同的資料模型，因為 Web API 服務與 Search 服務是以相同的資料為目標。 因此，實際實作商務微服務時，您會分割該功能，因此可視需要縮放每個內部服務。 Web API 服務通常可能需要比 Search 服務更多的執行個體，也可能相反。

簡單來說，微服務的邏輯架構不一定會與實體部署架構一致。 在本指南中，每當我們提到微服務時，指的是無法對應至一或多個 (實體) 服務的商務或邏輯微服務。 在大部分情況下，這會是單一服務，但可能更多。

>[!div class="step-by-step"]
>[上一個](data-sovereignty-per-microservice.md)
>[下一個](distributed-data-management.md)
