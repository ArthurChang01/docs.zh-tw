---
title: 使用兩個 DataGridView 控制項建立主版詳細資料表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: d317f4e592790c9b48b539b1601814569e14529f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737328"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="138c6-102">如何：使用兩個 Windows Form DataGridView 控制項建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="138c6-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="138c6-103">下列程式碼範例會使用兩個 <xref:System.Windows.Forms.DataGridView> 控制項繫結至兩個 <xref:System.Windows.Forms.BindingSource> 元件來建立主從式表單。</span><span class="sxs-lookup"><span data-stu-id="138c6-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="138c6-104">資料來源是 <xref:System.Data.DataSet>，包含來自 Northwind SQL Server 範例資料庫的 `Customers` 和 `Orders` 資料表，以及透過 `CustomerID` 資料行和這兩者產生關聯的 <xref:System.Data.DataRelation>。</span><span class="sxs-lookup"><span data-stu-id="138c6-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="138c6-105">一個 <xref:System.Windows.Forms.BindingSource> 會繫結至資料集中的父代 `Customers` 資料表。</span><span class="sxs-lookup"><span data-stu-id="138c6-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="138c6-106">此資料會顯示在 <xref:System.Windows.Forms.DataGridView> 主控制項。</span><span class="sxs-lookup"><span data-stu-id="138c6-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="138c6-107">其他 <xref:System.Windows.Forms.BindingSource> 會繫結程序至第一個資料連接器。</span><span class="sxs-lookup"><span data-stu-id="138c6-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="138c6-108">第二個 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性會設為 <xref:System.Data.DataRelation> 的名稱。</span><span class="sxs-lookup"><span data-stu-id="138c6-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="138c6-109">這會導致相關的 <xref:System.Windows.Forms.DataGridView> 詳細資料控制項顯示 `Orders` 子資料表的資料列，對應到 <xref:System.Windows.Forms.DataGridView> 主控制項中的目前資料列。</span><span class="sxs-lookup"><span data-stu-id="138c6-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="138c6-110">如需此程式碼範例的完整說明，請參閱[逐步解說：使用兩個 Windows Forms DataGridView 控制項建立主要/詳細表單](creating-a-master-detail-form-using-two-datagridviews.md)。</span><span class="sxs-lookup"><span data-stu-id="138c6-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="138c6-111">範例</span><span class="sxs-lookup"><span data-stu-id="138c6-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="138c6-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="138c6-112">Compiling the Code</span></span>  
 <span data-ttu-id="138c6-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="138c6-113">This example requires:</span></span>  
  
 <span data-ttu-id="138c6-114">System、System.Data、System.Windows.Forms 和 System.XML 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="138c6-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="138c6-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="138c6-115">.NET Framework Security</span></span>  
 <span data-ttu-id="138c6-116">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="138c6-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="138c6-117">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="138c6-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="138c6-118">如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="138c6-118">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="138c6-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="138c6-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="138c6-120">逐步解說：使用兩個 Windows Forms DataGridView 控制項建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="138c6-120">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)
- [<span data-ttu-id="138c6-121">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="138c6-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="138c6-122">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="138c6-122">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
