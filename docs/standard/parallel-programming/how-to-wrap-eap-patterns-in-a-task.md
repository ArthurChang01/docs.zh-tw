---
title: 如何：將 EAP 模式包裝在工作中
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: ac7436892c644340286bb4670bf75c9cd63a8ce5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106827"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>如何：將 EAP 模式包裝在工作中
下列範例將示範如何使用 <xref:System.Threading.Tasks.TaskCompletionSource%601>，將事件式非同步模式 (EAP) 的任意序列公開為單一工作。 此範例也示範如何使用 <xref:System.Threading.CancellationToken> 在 <xref:System.Net.WebClient> 物件上叫用內建的取消方法。  
  
## <a name="example"></a>範例  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>另請參閱

- [TPL 和傳統 .NET Framework 非同步程式設計](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
