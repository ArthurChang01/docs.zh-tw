---
title: 公開伺服器端 UI 自動化提供者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expose a server-side UI Automation provider
- UI Automation, server-side provider, exposing
- server-side UI Automation provider, exposing
ms.assetid: 55d419c0-2201-4101-90c9-2888df4dbb47
ms.openlocfilehash: 49dcae6ccaf749bae8d8a90af850034bb9bd37fb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433614"
---
# <a name="expose-a-server-side-ui-automation-provider"></a><span data-ttu-id="55930-102">公開伺服器端 UI 自動化提供者</span><span class="sxs-lookup"><span data-stu-id="55930-102">Expose a Server-side UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="55930-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="55930-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="55930-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="55930-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="55930-105">本主題包含範例程式碼，顯示如何公開裝載在 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> 視窗中的伺服器端使用者介面自動化提供者。</span><span class="sxs-lookup"><span data-stu-id="55930-105">This topic contains example code that shows how to expose a server-side UI Automation provider that is hosted in a <xref:System.Windows.Forms.Control?displayProperty=nameWithType> window.</span></span>  
  
 <span data-ttu-id="55930-106">這段程式碼會覆寫視窗程序，在用戶端應用程式要求視窗相關資訊時，截取 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心服務所傳送的訊息 WM_GETOBJECT。</span><span class="sxs-lookup"><span data-stu-id="55930-106">The example overrides the window procedure to trap WM_GETOBJECT, which is the message sent by the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core service when a client application requests information about the window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55930-107">範例</span><span class="sxs-lookup"><span data-stu-id="55930-107">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#116](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#116)]
 [!code-vb[UIAFragmentProvider_snip#116](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#116)]  
  
## <a name="see-also"></a><span data-ttu-id="55930-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55930-108">See also</span></span>

- [<span data-ttu-id="55930-109">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="55930-109">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="55930-110">伺服器端 UI 自動化提供者實作</span><span class="sxs-lookup"><span data-stu-id="55930-110">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
