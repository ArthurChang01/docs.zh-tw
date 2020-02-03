---
title: 使用 BindingSource 元件排序和篩選 ADO.NET 資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742970"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="e4d35-102">如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料</span><span class="sxs-lookup"><span data-stu-id="e4d35-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="e4d35-103">您可以透過 <xref:System.Windows.Forms.BindingSource.Sort%2A> 和 <xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性，公開 <xref:System.Windows.Forms.BindingSource> 控制的排序和篩選功能。</span><span class="sxs-lookup"><span data-stu-id="e4d35-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="e4d35-104">當基礎資料來源是 <xref:System.ComponentModel.IBindingList>時，您可以套用簡單排序，而且當資料來源為 <xref:System.ComponentModel.IBindingListView>時，您可以套用篩選和先進排序。</span><span class="sxs-lookup"><span data-stu-id="e4d35-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="e4d35-105"><xref:System.Windows.Forms.BindingSource.Sort%2A> 屬性需要標準 ADO.NET 語法：字串，代表資料來源中的資料行名稱，後面接著 `ASC` 或 `DESC`，以指出清單是否應該以遞增或遞減順序排序。</span><span class="sxs-lookup"><span data-stu-id="e4d35-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard ADO.NET syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="e4d35-106">您可以使用逗號分隔字元來分隔每個資料行，以設定高階排序或多重資料行排序。</span><span class="sxs-lookup"><span data-stu-id="e4d35-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="e4d35-107"><xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性會接受字串運算式。</span><span class="sxs-lookup"><span data-stu-id="e4d35-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4d35-108">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="e4d35-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="e4d35-109">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="e4d35-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="e4d35-110">如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="e4d35-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="e4d35-111">使用 BindingSource 來篩選資料</span><span class="sxs-lookup"><span data-stu-id="e4d35-111">To filter data with the BindingSource</span></span>  
  
- <span data-ttu-id="e4d35-112">將 [<xref:System.Windows.Forms.BindingSource.Filter%2A>] 屬性設為您想要的運算式。</span><span class="sxs-lookup"><span data-stu-id="e4d35-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="e4d35-113">在下列程式碼範例中，運算式是資料行名稱，後面接著您想要用於資料行的值。</span><span class="sxs-lookup"><span data-stu-id="e4d35-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="e4d35-114">使用 BindingSource 排序資料</span><span class="sxs-lookup"><span data-stu-id="e4d35-114">To sort data with the BindingSource</span></span>  
  
1. <span data-ttu-id="e4d35-115">將 [<xref:System.Windows.Forms.BindingSource.Sort%2A>] 屬性設為您想要的資料行名稱，後面接著 `ASC` 或 `DESC` 以指示遞增或遞減順序。</span><span class="sxs-lookup"><span data-stu-id="e4d35-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2. <span data-ttu-id="e4d35-116">以逗號分隔多個資料行。</span><span class="sxs-lookup"><span data-stu-id="e4d35-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="e4d35-117">範例</span><span class="sxs-lookup"><span data-stu-id="e4d35-117">Example</span></span>  
 <span data-ttu-id="e4d35-118">下列程式碼範例會將資料從 Northwind 範例資料庫的 Customers 資料表載入至 <xref:System.Windows.Forms.DataGridView> 控制項，並篩選並排序顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="e4d35-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4d35-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e4d35-119">Compiling the Code</span></span>  
 <span data-ttu-id="e4d35-120">若要執行此範例，請將程式碼貼入包含名為 `BindingSource1` 之 <xref:System.Windows.Forms.BindingSource> 的表單中，以及名為 `dataGridView1`的 <xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="e4d35-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="e4d35-121">處理表單的 <xref:System.Windows.Forms.Form.Load> 事件，並在 load 事件處理常式方法中呼叫 `InitializeSortedFilteredBindingSource`。</span><span class="sxs-lookup"><span data-stu-id="e4d35-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d35-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4d35-122">See also</span></span>

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- <span data-ttu-id="e4d35-123">[如何：安裝範例資料庫](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e4d35-123">[How to: Install Sample Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span></span>
- [<span data-ttu-id="e4d35-124">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="e4d35-124">BindingSource Component</span></span>](bindingsource-component.md)
