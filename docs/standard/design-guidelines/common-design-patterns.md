---
title: 通用設計模式
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- design patterns in class libraries
- class library design guidelines [.NET Framework], design patterns
ms.assetid: f7bd1361-4ab2-4132-972d-a044b8f197e1
ms.openlocfilehash: 2c51b1c9bc970d6ff143fa5986eade4a8b69f25a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709500"
---
# <a name="common-design-patterns"></a><span data-ttu-id="071c0-102">通用設計模式</span><span class="sxs-lookup"><span data-stu-id="071c0-102">Common Design Patterns</span></span>
<span data-ttu-id="071c0-103">有許多關於軟體模式、模式語言和反模式的書籍，可解決廣泛的模式主題。</span><span class="sxs-lookup"><span data-stu-id="071c0-103">There are numerous books on software patterns, pattern languages, and antipatterns that address the very broad subject of patterns.</span></span> <span data-ttu-id="071c0-104">因此，本章提供與一組非常有限的模式相關的指導方針和討論，在 .NET Framework Api 的設計中經常使用。</span><span class="sxs-lookup"><span data-stu-id="071c0-104">Thus, this chapter provides guidelines and discussion related to a very limited set of patterns that are used frequently in the design of the .NET Framework APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="071c0-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="071c0-105">In This Section</span></span>  
 [<span data-ttu-id="071c0-106">相依性屬性</span><span class="sxs-lookup"><span data-stu-id="071c0-106">Dependency Properties</span></span>](../../../docs/standard/design-guidelines/dependency-properties.md)  
 [<span data-ttu-id="071c0-107">Dispose 模式</span><span class="sxs-lookup"><span data-stu-id="071c0-107">Dispose Pattern</span></span>](../garbage-collection/implementing-dispose.md)  
 <span data-ttu-id="071c0-108">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="071c0-108">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="071c0-109">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="071c0-109">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="071c0-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="071c0-110">See also</span></span>

- [<span data-ttu-id="071c0-111">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="071c0-111">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
