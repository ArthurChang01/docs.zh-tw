---
title: 2.0 版中 System.Uri 命名空間的變更
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 987010b8367069e8089df3f809d23f258bb68f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642759"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="2c4f5-102">2.0 版中 System.Uri 命名空間的變更</span><span class="sxs-lookup"><span data-stu-id="2c4f5-102">Changes to the System.Uri namespace in version 2.0</span></span>

<span data-ttu-id="2c4f5-103">已對 <xref:System.Uri?displayProperty=nameWithType> 類別進行數項變更。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2c4f5-104">這些變更已修正不正確的行為、增強可用性和增強式安全性。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>

## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="2c4f5-105">已淘汰和已取代的成員</span><span class="sxs-lookup"><span data-stu-id="2c4f5-105">Obsolete and deprecated Members</span></span>

 <span data-ttu-id="2c4f5-106">建構函式：</span><span class="sxs-lookup"><span data-stu-id="2c4f5-106">Constructors:</span></span>

- <span data-ttu-id="2c4f5-107">所有具有 `dontEscape` 參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-107">All constructors that have a `dontEscape` parameter.</span></span>

 <span data-ttu-id="2c4f5-108">方法:</span><span class="sxs-lookup"><span data-stu-id="2c4f5-108">Methods:</span></span>

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a><span data-ttu-id="2c4f5-109">變更</span><span class="sxs-lookup"><span data-stu-id="2c4f5-109">Changes</span></span>

- <span data-ttu-id="2c4f5-110">針對已知沒有查詢部分的 URI 配置 (file、ftp 和其他項目)，一律會逸出 '?' 字元，而且它不是 <xref:System.Uri.Query%2A> 部分的開頭。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>

- <span data-ttu-id="2c4f5-111">針對隱含檔案 URI (形式為 `c:\directory\file@name.txt`)，除非要求完整取消逸出，或 <xref:System.Uri.LocalPath%2A> 是 `true`，否則一律會逸出片段字元 ('#')。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-111">For implicit file URIs (of the form `c:\directory\file@name.txt`), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>

- <span data-ttu-id="2c4f5-112">已移除 UNC 主機名稱支援；已採用用於呈現國際主機名稱的 IDN 規格。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>

- <span data-ttu-id="2c4f5-113"><xref:System.Uri.LocalPath%2A> 一律會傳回完整未逸出的字串。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>

- <span data-ttu-id="2c4f5-114"><xref:System.Uri.ToString%2A> 不會取消逸出已逸出的 '%'、'?' 或 '#' 字元。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>

- <span data-ttu-id="2c4f5-115"><xref:System.Uri.Equals%2A> 現在會在相等檢查時包含 <xref:System.Uri.Query%2A> 部分。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>

- <span data-ttu-id="2c4f5-116">運算子 "==" 和 "!=" 會覆寫並連結至 <xref:System.Uri.Equals%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>

- <span data-ttu-id="2c4f5-117"><xref:System.Uri.IsLoopback%2A> 現在會產生一致的結果。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>

- <span data-ttu-id="2c4f5-118">URI "`file:///path`" 不再轉譯成 `file://path`。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-118">The URI "`file:///path`" is no longer translated into `file://path`.</span></span>

- <span data-ttu-id="2c4f5-119">"#" 現在會辨識為主機名稱結束字元。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="2c4f5-120">也就是 `http://contoso.com#fragment` 現在會轉換成 `http://contoso.com/#fragment`。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-120">That is, `http://contoso.com#fragment` is now converted to `http://contoso.com/#fragment`.</span></span>

- <span data-ttu-id="2c4f5-121">已修正合併基底 URI 與片段時的 Bug。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-121">A bug when combining a base URI with a fragment has been fixed.</span></span>

- <span data-ttu-id="2c4f5-122">已修正 <xref:System.Uri.HostNameType%2A> 中的 Bug。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>

- <span data-ttu-id="2c4f5-123">已修正 NNTP 剖析中的 Bug。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-123">A bug in NNTP parsing is fixed.</span></span>

- <span data-ttu-id="2c4f5-124">HTTP:contoso.com 形式的 URI 現在會擲回剖析例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>

- <span data-ttu-id="2c4f5-125">Framework 可正確處理 URI 中的 userinfo。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-125">The Framework correctly handles userinfo in a URI.</span></span>

- <span data-ttu-id="2c4f5-126">已修正 URI 路徑壓縮，因此中斷 URI 無法周遊檔案系統的根目錄。</span><span class="sxs-lookup"><span data-stu-id="2c4f5-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c4f5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c4f5-127">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
