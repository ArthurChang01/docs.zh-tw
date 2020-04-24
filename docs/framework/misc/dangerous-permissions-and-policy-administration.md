---
title: 危險使用權限和原則管理
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: 15d28ff7d11b5d15ce44d9ab1f56548256850ff8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645751"
---
# <a name="dangerous-permissions-and-policy-administration"></a>危險使用權限和原則管理
.NET Framework 為幾個受保護作業提供了使用權限，這些受保護作業也可能會讓安全性系統受到危害。 您只能在必要時將這些危險的使用權限授與給可靠的程式碼。 如果將這些使用權限授與給惡意程式碼，通常就沒有任何方法可以抵禦這些惡意程式碼。  
  
> [!NOTE]
> 在 .NET 框架 4 中,對 .NET 框架安全模型和術語進行了重要更改。 有關這些更改的詳細資訊,請參閱[安全變更](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)。  
  
 下表說明危險的使用權限。  
  
|權限|潛在風險|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|允許 Managed 程式碼呼叫進入 Unmanaged 程式碼，後者通常具有危險。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|不用進行驗證，程式碼就可以執行任何動作。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|失效的辨識項可以騙過安全性原則。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|修改安全性原則的能力可以使安全性停用。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|使用序列化可能會規避存取範圍機制。 如需詳細資訊，請參閱 [安全性和序列化](security-and-serialization.md)。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|設定目前主體的能力可以欺騙以角色為基礎的安全性。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|執行緒的操作有危險，因為安全性狀態與執行緒有關聯。|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|可以使用私用成員使存取範圍機制無效。|  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../standard/security/secure-coding-guidelines.md)
