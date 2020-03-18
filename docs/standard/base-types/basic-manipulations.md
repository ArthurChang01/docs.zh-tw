---
title: .NET 中的基底字元串操作
description: 請參閱呼叫許多字串方法的範例。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 87ce7a79ce18ca8f5579841ad9e52e2519d6ac73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187263"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="6f2bd-103">如何：在 .NET 中執行基本字串操作</span><span class="sxs-lookup"><span data-stu-id="6f2bd-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="6f2bd-104">下列範例會使用[基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)主題中所討論的一些方法，以一種可能在實際應用程式中發現的方式，來建構可執行字串操作的類別。</span><span class="sxs-lookup"><span data-stu-id="6f2bd-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="6f2bd-105">`MailToData` 類別會將個人的姓名和地址儲存在不同的屬性中，並允許您將 `City`、`State` 和 `Zip` 欄位組合成單一字串，以便顯示給使用者看。</span><span class="sxs-lookup"><span data-stu-id="6f2bd-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="6f2bd-106">此外，類別也可讓使用者將城市、省/市和郵遞區號當成單一字串來輸入；應用程式會自動剖析這個單一字串，然後將正確的資訊輸入對應的屬性中。</span><span class="sxs-lookup"><span data-stu-id="6f2bd-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
<span data-ttu-id="6f2bd-107">為了簡單起見，這個範例會使用具有命令列介面的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f2bd-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f2bd-108">範例</span><span class="sxs-lookup"><span data-stu-id="6f2bd-108">Example</span></span>  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
<span data-ttu-id="6f2bd-109">執行上述代碼時，將詢問使用者輸入其名稱和位址。</span><span class="sxs-lookup"><span data-stu-id="6f2bd-109">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="6f2bd-110">應用程式會將這項資訊放入適當的屬性中，並建立出顯示城市、省/市和郵遞區號資訊的單一字串，將資訊重新顯示給使用者看。</span><span class="sxs-lookup"><span data-stu-id="6f2bd-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f2bd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f2bd-111">See also</span></span>

- [<span data-ttu-id="6f2bd-112">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="6f2bd-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
