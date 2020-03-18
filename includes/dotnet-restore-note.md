---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632124"
---
> [!NOTE]
> <span data-ttu-id="b518e-101">從 .NET Core 2.0 SDK 開始，您不必[`dotnet restore`](~/docs/core/tools/dotnet-restore.md)運行，因為它由需要還原的所有命令（如`dotnet new`）`dotnet build`和`dotnet run`進行隱式運行。</span><span class="sxs-lookup"><span data-stu-id="b518e-101">Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`.</span></span>
> <span data-ttu-id="b518e-102">它在執行明確還原有意義的某些情況下仍然是有效的命令，例如 [Azure DevOps Services 中的持續整合組建](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core)，或在需要明確控制還原進行時間的建置系統中。</span><span class="sxs-lookup"><span data-stu-id="b518e-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
