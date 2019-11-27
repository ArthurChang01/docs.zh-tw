---
title: 註冊用戶端提供者組件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: 72e1349eee90bbe5078fec037b5f29c51c84b8ec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438457"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="c729a-102">註冊用戶端提供者組件</span><span class="sxs-lookup"><span data-stu-id="c729a-102">Register a Client-Side Provider Assembly</span></span>
> [!NOTE]
> <span data-ttu-id="c729a-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="c729a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c729a-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="c729a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c729a-105">本主題說明如何註冊包含用戶端使用者介面自動化提供者的 DLL。</span><span class="sxs-lookup"><span data-stu-id="c729a-105">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c729a-106">範例</span><span class="sxs-lookup"><span data-stu-id="c729a-106">Example</span></span>  
 <span data-ttu-id="c729a-107">下列範例示範如何註冊包含主控台視窗提供者的組件。</span><span class="sxs-lookup"><span data-stu-id="c729a-107">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="c729a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c729a-108">See also</span></span>

- [<span data-ttu-id="c729a-109">建立用戶端 UI 自動化提供者</span><span class="sxs-lookup"><span data-stu-id="c729a-109">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
