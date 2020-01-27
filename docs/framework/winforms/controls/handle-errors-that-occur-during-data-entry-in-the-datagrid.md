---
title: 處理 DataGridView 控制項中的資料輸入期間所發生的錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: 03a13957c80b0ab62afb11efc57cf31e059e5942
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745608"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="982dc-102">如何：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="982dc-102">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="982dc-103">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 控制項，將資料輸入錯誤回報給使用者。</span><span class="sxs-lookup"><span data-stu-id="982dc-103">The following code example demonstrates how to use the <xref:System.Windows.Forms.DataGridView> control to report data entry errors to the user.</span></span>  
  
 <span data-ttu-id="982dc-104">如需此程式碼範例的完整說明，請參閱[逐步解說：處理在 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="982dc-104">For a complete explanation of this code example, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="982dc-105">範例</span><span class="sxs-lookup"><span data-stu-id="982dc-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="982dc-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="982dc-106">Compiling the Code</span></span>  
 <span data-ttu-id="982dc-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="982dc-107">This example requires:</span></span>  
  
- <span data-ttu-id="982dc-108">System、System.Data、System.Windows.Forms 和 System.XML 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="982dc-108">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="982dc-109">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="982dc-109">.NET Framework Security</span></span>  
 <span data-ttu-id="982dc-110">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="982dc-110">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="982dc-111">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="982dc-111">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="982dc-112">如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="982dc-112">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982dc-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="982dc-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="982dc-114">逐步解說：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="982dc-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="982dc-115">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="982dc-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="982dc-116">逐步解說：驗證 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="982dc-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="982dc-117">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="982dc-117">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
