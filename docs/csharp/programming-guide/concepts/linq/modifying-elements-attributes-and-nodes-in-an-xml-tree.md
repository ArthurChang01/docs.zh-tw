---
title: 修改 XML 樹狀結構中的項目、屬性和節點
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484228"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="1a09e-102">修改 XML 樹狀中的項目、屬性和節點</span><span class="sxs-lookup"><span data-stu-id="1a09e-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="1a09e-103">下表摘要說明您可以用於修改項目、其子項目或其屬性的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="1a09e-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="1a09e-104">下列方法會修改 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="1a09e-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="1a09e-105">方法</span><span class="sxs-lookup"><span data-stu-id="1a09e-105">Method</span></span>|<span data-ttu-id="1a09e-106">描述</span><span class="sxs-lookup"><span data-stu-id="1a09e-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-107">以剖析的 XML 取代項目。</span><span class="sxs-lookup"><span data-stu-id="1a09e-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-108">移除項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="1a09e-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-109">移除項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="1a09e-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-110">取代項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="1a09e-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-111">取代項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="1a09e-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-112">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1a09e-112">Sets the value of an attribute.</span></span> <span data-ttu-id="1a09e-113">建立屬性 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="1a09e-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="1a09e-114">如果值設定為 `null`，移除屬性。</span><span class="sxs-lookup"><span data-stu-id="1a09e-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-115">設定子項目的值。</span><span class="sxs-lookup"><span data-stu-id="1a09e-115">Sets the value of a child element.</span></span> <span data-ttu-id="1a09e-116">建立項目 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="1a09e-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="1a09e-117">如果值設定為 `null`，移除項目。</span><span class="sxs-lookup"><span data-stu-id="1a09e-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-118">以指定的文字取代項目的內容 (子節點)。</span><span class="sxs-lookup"><span data-stu-id="1a09e-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-119">設定項目的值。</span><span class="sxs-lookup"><span data-stu-id="1a09e-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="1a09e-120">下列方法會修改 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="1a09e-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="1a09e-121">方法</span><span class="sxs-lookup"><span data-stu-id="1a09e-121">Method</span></span>|<span data-ttu-id="1a09e-122">描述</span><span class="sxs-lookup"><span data-stu-id="1a09e-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-123">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1a09e-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-124">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1a09e-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="1a09e-125">下列方法會修改 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。</span><span class="sxs-lookup"><span data-stu-id="1a09e-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="1a09e-126">方法</span><span class="sxs-lookup"><span data-stu-id="1a09e-126">Method</span></span>|<span data-ttu-id="1a09e-127">描述</span><span class="sxs-lookup"><span data-stu-id="1a09e-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-128">以新內容取代節點。</span><span class="sxs-lookup"><span data-stu-id="1a09e-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="1a09e-129">下列方法會修改 <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。</span><span class="sxs-lookup"><span data-stu-id="1a09e-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="1a09e-130">方法</span><span class="sxs-lookup"><span data-stu-id="1a09e-130">Method</span></span>|<span data-ttu-id="1a09e-131">描述</span><span class="sxs-lookup"><span data-stu-id="1a09e-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="1a09e-132">以新的內容取代子節點。</span><span class="sxs-lookup"><span data-stu-id="1a09e-132">Replaces the children nodes with new content.</span></span>|  
