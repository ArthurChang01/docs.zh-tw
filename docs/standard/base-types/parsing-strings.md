---
title: 在 .NET 中剖析字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 717022e5d2e292c1624e6155bd7571e4daa997b9
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523807"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="e17f9-102">在 .NET 中剖析字串</span><span class="sxs-lookup"><span data-stu-id="e17f9-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="e17f9-103">剖析作業會將代表 .NET 基底類型的字串轉換成該基底類型。</span><span class="sxs-lookup"><span data-stu-id="e17f9-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="e17f9-104">例如，剖析作業用來將字串轉換為浮點數或日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="e17f9-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="e17f9-105">最常用來執行剖析作業的方法是 `Parse` 方法。</span><span class="sxs-lookup"><span data-stu-id="e17f9-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="e17f9-106">因為剖析是格式設定的反向作業 (這牽涉到將基底類型別轉換成其字串表示)，所以會套用許多相同的規則和慣例。</span><span class="sxs-lookup"><span data-stu-id="e17f9-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="e17f9-107">就像格式化會使用實作 <xref:System.IFormatProvider> 介面的物件來提供區分文化特性的格式化資訊，剖析也會使用實作 <xref:System.IFormatProvider> 介面的物件來判斷如何解譯字串表示。</span><span class="sxs-lookup"><span data-stu-id="e17f9-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="e17f9-108">如需詳細資訊，請參閱[格式類型](../../../docs/standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e17f9-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e17f9-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="e17f9-109">In This Section</span></span>  
 [<span data-ttu-id="e17f9-110">剖析數值字串</span><span class="sxs-lookup"><span data-stu-id="e17f9-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="e17f9-111">描述如何將字串轉換成 .NET 數值類型。</span><span class="sxs-lookup"><span data-stu-id="e17f9-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="e17f9-112">剖析日期和時間字串</span><span class="sxs-lookup"><span data-stu-id="e17f9-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="e17f9-113">描述如何將字串轉換成 .NET **DateTime** 類型。</span><span class="sxs-lookup"><span data-stu-id="e17f9-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="e17f9-114">剖析其他字串</span><span class="sxs-lookup"><span data-stu-id="e17f9-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="e17f9-115">描述如何將字串轉換成 **Char**、**Boolean** 和 **Enum** 類型。</span><span class="sxs-lookup"><span data-stu-id="e17f9-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e17f9-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="e17f9-116">Related Sections</span></span>  
 [<span data-ttu-id="e17f9-117">格式化類型</span><span class="sxs-lookup"><span data-stu-id="e17f9-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="e17f9-118">描述基本的格式化概念，例如格式規範和格式提供者。</span><span class="sxs-lookup"><span data-stu-id="e17f9-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="e17f9-119">.NET 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="e17f9-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="e17f9-120">描述如何轉換類型。</span><span class="sxs-lookup"><span data-stu-id="e17f9-120">Describes how to convert types.</span></span>
