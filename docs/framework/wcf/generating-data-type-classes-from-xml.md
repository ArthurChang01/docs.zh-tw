---
title: 從 XML 產生資料型別類型
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: d66cbd1806b90d21a483d0c470f953ddfb9c4fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184126"
---
# <a name="generating-data-type-classes-from-xml"></a>從 XML 產生資料型別類型
.NET 框架 4.5 包括一個新功能，用於從 XML 生成資料類型類。 本主題介紹如何自動為 .NET 博客 RSS 源生成資料類型。  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>從 .NET 博客 RSS 源獲取 XML  
  
1. 在 Internet 資源管理器中，導航到[.NET 博客 RSS 源](https://devblogs.microsoft.com/dotnet/feed/)。  
  
2. 按右鍵頁面並選擇 **"查看源**"。  
  
3. 通過按**Ctrl_A**以選擇所有文本複製源的文本，然後**按 Ctrl_C**進行複製。  
  
### <a name="creating-the-data-types"></a>建立資料類型  
  
1. 開啟要使用 Proxy 的程式碼檔。 此檔應是 .NET 框架 4.5 專案的一部分。  
  
2. 將游標放在檔案中任何現有類別以外的位置。  
  
3. 選擇 **"編輯**"、"**粘貼特殊**"、"**粘貼XML為類**"。  
  
4. 使用訪問`link` `rss`RSS 源中的元素的必要成員`rssChannel`創建名為 、、`rssChannelImage``rssChannelItem`和`rssChannelItemGuid`的類。  
  
### <a name="using-the-generated-classes"></a>使用產生的類別  
  
1. 這些類別一旦產生，就可以像其他類別一樣在程式碼中使用。 下列程式碼範例會傳回 `rssChannelImage` 類別的新執行個體。  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
