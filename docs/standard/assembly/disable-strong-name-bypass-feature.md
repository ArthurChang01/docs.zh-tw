---
title: 如何：停用強式名稱略過功能
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141114"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="d3799-102">如何：停用強式名稱略過功能</span><span class="sxs-lookup"><span data-stu-id="d3799-102">How to: Disable the strong-name bypass feature</span></span>
<span data-ttu-id="d3799-103">從 .NET Framework 3.5 版 Service Pack 1 (SP1) 開始，當組件載入到完全信任的 <xref:System.AppDomain> 物件 (例如適用於 `MyComputer` 區域的預設 <xref:System.AppDomain>) 時，不會驗證強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="d3799-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="d3799-104">這是指強式名稱略過功能。</span><span class="sxs-lookup"><span data-stu-id="d3799-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="d3799-105">在完全信任環境中，不論簽章為何，已簽署、完全信任的組件要求 <xref:System.Security.Permissions.StrongNameIdentityPermission> 一律會成功。</span><span class="sxs-lookup"><span data-stu-id="d3799-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="d3799-106">唯一的限制是組件必須是完全受信任的，因為它的區域是完全信任的。</span><span class="sxs-lookup"><span data-stu-id="d3799-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="d3799-107">因為強式名稱不是這些情況下的決定因素，所以不需要進行驗證。</span><span class="sxs-lookup"><span data-stu-id="d3799-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="d3799-108">略過強式名稱簽章驗證可大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="d3799-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="d3799-109">略過功能適用於任何完全信任的組件，該組件非延遲簽署，且已從其 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性指定的目錄載入至所有完全信任的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="d3799-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="d3799-110">您可以設定登錄機碼值，覆寫電腦上所有應用程式的略過功能。</span><span class="sxs-lookup"><span data-stu-id="d3799-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="d3799-111">您可以使用應用程式組態檔覆寫單一應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="d3799-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="d3799-112">如果登錄機碼已停用該功能，您即無法恢復單一應用程式的略過功能。</span><span class="sxs-lookup"><span data-stu-id="d3799-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="d3799-113">當您覆寫略過功能時，只會驗證強式名稱的正確性，不檢查 <xref:System.Security.Permissions.StrongNameIdentityPermission>。</span><span class="sxs-lookup"><span data-stu-id="d3799-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="d3799-114">如果您想要確認特定的強式名稱，您必須另外執行檢查。</span><span class="sxs-lookup"><span data-stu-id="d3799-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d3799-115">能否強制執行強式名稱驗證，視登錄機碼而定，如下列程序所述。</span><span class="sxs-lookup"><span data-stu-id="d3799-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="d3799-116">如果在沒有存取控制清單 (ACL) 權限的帳戶下，執行應用程式存取該登錄機碼，則設定為無效。</span><span class="sxs-lookup"><span data-stu-id="d3799-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="d3799-117">您必須確定此機碼已設定 ACL 權限，它才能為所有組件讀取。</span><span class="sxs-lookup"><span data-stu-id="d3799-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="d3799-118">停用所有應用程式的強式名稱略過功能</span><span class="sxs-lookup"><span data-stu-id="d3799-118">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="d3799-119">在 32 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 機碼下，建立值為 0、名為 `AllowStrongNameBypass` 的 DWORD 項目。</span><span class="sxs-lookup"><span data-stu-id="d3799-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="d3799-120">在 64 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 和 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 機碼下，建立值為 0、名為 `AllowStrongNameBypass` 的 DWORD 項目。</span><span class="sxs-lookup"><span data-stu-id="d3799-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="d3799-121">停用單一應用程式的強式名稱略過功能</span><span class="sxs-lookup"><span data-stu-id="d3799-121">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="d3799-122">開啟或建立應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="d3799-122">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="d3799-123">如需此檔案的詳細資訊，請參閱[設定應用](../../framework/configure-apps/index.md)程式中的應用程式佈建檔一節。</span><span class="sxs-lookup"><span data-stu-id="d3799-123">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="d3799-124">新增下列項目：</span><span class="sxs-lookup"><span data-stu-id="d3799-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="d3799-125">您可以藉由移除設定檔設定，或將屬性設定為 `true`，來還原應用程式的略過功能。</span><span class="sxs-lookup"><span data-stu-id="d3799-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3799-126">只有啟用電腦的略過功能，您才可以開啟或關閉應用程式的強式名稱驗證。</span><span class="sxs-lookup"><span data-stu-id="d3799-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="d3799-127">如已關閉電腦的略過功能，即會驗證所有應用程式的強式名稱，而您無法略過單一應用程式的驗證。</span><span class="sxs-lookup"><span data-stu-id="d3799-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3799-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="d3799-128">See also</span></span>

- [<span data-ttu-id="d3799-129">Sn.exe (強式名稱工具)</span><span class="sxs-lookup"><span data-stu-id="d3799-129">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="d3799-130">\<Bypasstrustedappstrongnames> > 元素</span><span class="sxs-lookup"><span data-stu-id="d3799-130">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="d3799-131">建立和使用強式名稱的元件</span><span class="sxs-lookup"><span data-stu-id="d3799-131">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
