---
title: DataGrid 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
ms.openlocfilehash: efcc8770232f657c13135cefb4027f814d4d7d19
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742522"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="536d8-102">DataGrid 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="536d8-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="536d8-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 `DataGrid` 控制項並加入其他功能，不過您也可以選擇保留 `DataGrid` 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="536d8-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="536d8-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="536d8-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="536d8-105">Windows Forms `DataGrid` 控制項提供 ADO.NET 資料集、顯示表格式資料，以及啟用資料來源更新的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="536d8-105">The Windows Forms `DataGrid` control provides a user interface to ADO.NET datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="536d8-106">將 `DataGrid` 控制項設定為有效資料來源時，會自動填入控制項，並根據資料的形狀來建立資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="536d8-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="536d8-107">`DataGrid` 控制項可以用來顯示單一資料表，或一組資料表之間的階層關聯性。</span><span class="sxs-lookup"><span data-stu-id="536d8-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="536d8-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="536d8-108">In This Section</span></span>  
 [<span data-ttu-id="536d8-109">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="536d8-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="536d8-110">描述 `DataGrid` 控制項的基本功能。</span><span class="sxs-lookup"><span data-stu-id="536d8-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="536d8-111">如何：使用設計工具在 Windows Forms DataGrid 控制項中新增資料表和資料行</span><span class="sxs-lookup"><span data-stu-id="536d8-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="536d8-112">描述如何使用設計工具在 `DataGrid` 控制項中新增資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="536d8-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="536d8-113">操作說明：將資料表和資料行新增至 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="536d8-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="536d8-114">描述如何透過程式設計方式在 `DataGrid` 控制項中新增資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="536d8-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="536d8-115">操作說明：使用設計工具將 Windows Forms DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="536d8-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="536d8-116">描述如何使用設計工具，將 ADO.NET 資料集系結至 `DataGrid` 控制項。</span><span class="sxs-lookup"><span data-stu-id="536d8-116">Describes how to bind an ADO.NET dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="536d8-117">如何：將 Windows Forms DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="536d8-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="536d8-118">描述如何將 ADO.NET 資料集系結至 `DataGrid` 控制項。</span><span class="sxs-lookup"><span data-stu-id="536d8-118">Describes how to bind an ADO.NET dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="536d8-119">操作說明：在執行階段時變更 Windows Forms DataGrid 控制項中顯示的資料</span><span class="sxs-lookup"><span data-stu-id="536d8-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="536d8-120">描述如何透過程式設計方式在 `DataGrid` 控制項中變更資料。</span><span class="sxs-lookup"><span data-stu-id="536d8-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="536d8-121">如何：使用設計工具搭配 Windows Forms DataGrid 控制項建立主版詳細資料清單</span><span class="sxs-lookup"><span data-stu-id="536d8-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="536d8-122">描述如何使用設計工具在兩個不同的 `DataGrid` 控制項中顯示兩個透過父子式關係繫結在一起的資料表。</span><span class="sxs-lookup"><span data-stu-id="536d8-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="536d8-123">如何：使用 Windows Forms DataGrid 控制項建立主版詳細資料清單</span><span class="sxs-lookup"><span data-stu-id="536d8-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="536d8-124">描述如何在兩個不同的 `DataGrid` 控制項中顯示兩個透過父子式關係繫結在一起的資料表。</span><span class="sxs-lookup"><span data-stu-id="536d8-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="536d8-125">如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="536d8-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="536d8-126">描述如何移除 `DataGrid` 控制項中的資料行。</span><span class="sxs-lookup"><span data-stu-id="536d8-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="536d8-127">操作說明：使用設計工具格式化 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="536d8-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="536d8-128">描述如何使用設計工具變更 `DataGrid` 控制項的外觀相關屬性。</span><span class="sxs-lookup"><span data-stu-id="536d8-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="536d8-129">如何：格式化 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="536d8-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="536d8-130">描述如何變更 `DataGrid` 控制項的外觀相關屬性。</span><span class="sxs-lookup"><span data-stu-id="536d8-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="536d8-131">Windows Forms DataGrid 控制項的鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="536d8-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="536d8-132">列出用於巡覽 `DataGrid` 控制項的捷徑。</span><span class="sxs-lookup"><span data-stu-id="536d8-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="536d8-133">如何：回應 Windows Forms DataGrid 控制項中的按選動作</span><span class="sxs-lookup"><span data-stu-id="536d8-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="536d8-134">描述如何判斷使用者在 `DataGrid` 控制項中所按的儲存格。</span><span class="sxs-lookup"><span data-stu-id="536d8-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="536d8-135">如何：使用 Windows Forms DataGrid 控制項驗證輸入</span><span class="sxs-lookup"><span data-stu-id="536d8-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="536d8-136">描述如何驗證繫結至 `DataGrid` 控制項之資料集中的輸入。</span><span class="sxs-lookup"><span data-stu-id="536d8-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="536d8-137">參考</span><span class="sxs-lookup"><span data-stu-id="536d8-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="536d8-138">提供 <xref:System.Windows.Forms.DataGrid> 類別的總覽。</span><span class="sxs-lookup"><span data-stu-id="536d8-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="536d8-139">提供有關使用此屬性將 <xref:System.Windows.Forms.DataGrid> 控制項系結至資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="536d8-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="536d8-140">相關章節</span><span class="sxs-lookup"><span data-stu-id="536d8-140">Related Sections</span></span>  
 [<span data-ttu-id="536d8-141">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="536d8-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="536d8-142">提供 Windows Forms 中資料繫結主題的連結。</span><span class="sxs-lookup"><span data-stu-id="536d8-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536d8-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="536d8-143">See also</span></span>

- [<span data-ttu-id="536d8-144">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="536d8-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="536d8-145">Windows Forms DataGridView 和 DataGrid 控制項之間的差異</span><span class="sxs-lookup"><span data-stu-id="536d8-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
