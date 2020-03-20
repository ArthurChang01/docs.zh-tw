---
ms.openlocfilehash: 946096cb9510ca12bbd2cecd00099142308b072a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67856966"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="5cc88-101">已改進 WPF 中的按鍵提示行為</span><span class="sxs-lookup"><span data-stu-id="5cc88-101">Keytips behavior improved in WPF</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5cc88-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5cc88-102">Details</span></span>|<span data-ttu-id="5cc88-103">按鍵提示行為已經過修改，讓 Microsoft Word 與 Windows 檔案總管之間的行為趨於一致。</span><span class="sxs-lookup"><span data-stu-id="5cc88-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="5cc88-104">WPF 會藉由查看是否已啟用按鍵提示狀態，或是並非按下 <xref:System.Windows.Input.KeyEventArgs.SystemKey> (特別是 <xref:System.Windows.Input.Key> 或 <xref:System.Windows.Input.Key.F11>) 的情況，正確地處理按鍵提示的按鍵。</span><span class="sxs-lookup"><span data-stu-id="5cc88-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="5cc88-105">現在即使滑鼠已開啟了按鍵提示，其仍會關閉功能表。</span><span class="sxs-lookup"><span data-stu-id="5cc88-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>|
|<span data-ttu-id="5cc88-106">建議</span><span class="sxs-lookup"><span data-stu-id="5cc88-106">Suggestion</span></span>|<span data-ttu-id="5cc88-107">N/A</span><span class="sxs-lookup"><span data-stu-id="5cc88-107">N/A</span></span>|
|<span data-ttu-id="5cc88-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="5cc88-108">Scope</span></span>|<span data-ttu-id="5cc88-109">Edge</span><span class="sxs-lookup"><span data-stu-id="5cc88-109">Edge</span></span>|
|<span data-ttu-id="5cc88-110">版本</span><span class="sxs-lookup"><span data-stu-id="5cc88-110">Version</span></span>|<span data-ttu-id="5cc88-111">4.7.2</span><span class="sxs-lookup"><span data-stu-id="5cc88-111">4.7.2</span></span>|
|<span data-ttu-id="5cc88-112">類型</span><span class="sxs-lookup"><span data-stu-id="5cc88-112">Type</span></span>|<span data-ttu-id="5cc88-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="5cc88-113">Runtime</span></span>|
