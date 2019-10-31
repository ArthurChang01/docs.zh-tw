---
title: 發生未預期的錯誤，因為無法取得單一執行個體啟動所需要的作業系統資源
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 9643d14b3e94e814c492b362b9db3e37cff4ce9f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197369"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="09ae0-102">發生未預期的錯誤，因為無法取得單一執行個體啟動所需要的作業系統資源</span><span class="sxs-lookup"><span data-stu-id="09ae0-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="09ae0-103">應用程式無法取得必要的作業系統資源。</span><span class="sxs-lookup"><span data-stu-id="09ae0-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="09ae0-104">此問題的部分可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="09ae0-104">Some of the possible causes for this problem are:</span></span>  
  
- <span data-ttu-id="09ae0-105">應用程式沒有權限可建立具名的作業系統物件。</span><span class="sxs-lookup"><span data-stu-id="09ae0-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
- <span data-ttu-id="09ae0-106">通用語言執行平台沒有權限可建立記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="09ae0-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
- <span data-ttu-id="09ae0-107">應用程式需要存取作業系統物件，但另一個處理序正在使用它。</span><span class="sxs-lookup"><span data-stu-id="09ae0-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09ae0-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="09ae0-108">To correct this error</span></span>  
  
1. <span data-ttu-id="09ae0-109">檢查應用程式有足夠的權限可建立指名的作業系統物件。</span><span class="sxs-lookup"><span data-stu-id="09ae0-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="09ae0-110">檢查通用語言執行平台有足夠的權限可建立記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="09ae0-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="09ae0-111">重新啟動電腦，以清除可能正在使用連接到原始執行個體應用程式之所需資源的任何處理序。</span><span class="sxs-lookup"><span data-stu-id="09ae0-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="09ae0-112">記下錯誤發生時的情況，並致電 Microsoft 產品支援服務</span><span class="sxs-lookup"><span data-stu-id="09ae0-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ae0-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="09ae0-113">See also</span></span>

- [<span data-ttu-id="09ae0-114">專案設計工具、應用程式頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09ae0-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="09ae0-115">偵錯工具基礎</span><span class="sxs-lookup"><span data-stu-id="09ae0-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="09ae0-116">告訴我們</span><span class="sxs-lookup"><span data-stu-id="09ae0-116">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
