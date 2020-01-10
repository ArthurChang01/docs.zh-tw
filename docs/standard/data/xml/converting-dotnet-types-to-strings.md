---
title: 將 .NET Framework 型別轉換成字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: a63e0175f6660967eb4aa678c6731d353e44e2d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711073"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="aa49d-102">將 .NET Framework 型別轉換成字串</span><span class="sxs-lookup"><span data-stu-id="aa49d-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="aa49d-103">若要將 .NET Framework 型別轉換成字串，請使用 **ToString** 方法。</span><span class="sxs-lookup"><span data-stu-id="aa49d-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="aa49d-104">**ToString** 方法會傳回所傳入之型別的字串表示。</span><span class="sxs-lookup"><span data-stu-id="aa49d-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="aa49d-105">下表將列出 .NET Framework 型別，其所傳回的字串格式會對應至 XML 結構描述 (XSD) 規格。</span><span class="sxs-lookup"><span data-stu-id="aa49d-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="aa49d-106">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="aa49d-106">.NET Framework type</span></span>|<span data-ttu-id="aa49d-107">傳回的字串型別</span><span class="sxs-lookup"><span data-stu-id="aa49d-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="aa49d-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="aa49d-108">Boolean</span></span>|<span data-ttu-id="aa49d-109">"true"、"false"</span><span class="sxs-lookup"><span data-stu-id="aa49d-109">"true", "false"</span></span>|  
|<span data-ttu-id="aa49d-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="aa49d-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="aa49d-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="aa49d-111">"INF"</span></span>|  
|<span data-ttu-id="aa49d-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="aa49d-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="aa49d-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="aa49d-113">"-INF"</span></span>|  
|<span data-ttu-id="aa49d-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="aa49d-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="aa49d-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="aa49d-115">"INF"</span></span>|  
|<span data-ttu-id="aa49d-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="aa49d-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="aa49d-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="aa49d-117">"-INF"</span></span>|  
|<span data-ttu-id="aa49d-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="aa49d-118">DateTime</span></span>|<span data-ttu-id="aa49d-119">格式為 yyyy-MM-ddTHH:mm:sszzzzzz 及其子集。</span><span class="sxs-lookup"><span data-stu-id="aa49d-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="aa49d-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="aa49d-120">Timespan</span></span>|<span data-ttu-id="aa49d-121">格式為 PnYnMnTnHnMnS，例如 `P2Y10M15DT10H30M20S` 代表期間為 2 年 10 個月 15 天 10 小時 30 分鐘 20 秒。</span><span class="sxs-lookup"><span data-stu-id="aa49d-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa49d-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa49d-122">See also</span></span>

- [<span data-ttu-id="aa49d-123">XML 資料類型轉換</span><span class="sxs-lookup"><span data-stu-id="aa49d-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="aa49d-124">將字串轉換成 .NET Framework 資料類型</span><span class="sxs-lookup"><span data-stu-id="aa49d-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
