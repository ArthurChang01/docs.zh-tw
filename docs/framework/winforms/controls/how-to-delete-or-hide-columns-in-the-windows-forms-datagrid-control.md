---
title: 刪除或隱藏 DataGrid 控制項中的資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: c730be934e9b978bdaf09bc7e668b4318077fba5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743292"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="9b36a-102">如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="9b36a-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="9b36a-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="9b36a-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="9b36a-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="9b36a-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="9b36a-105">您可以使用 <xref:System.Windows.Forms.GridColumnStylesCollection> 和 <xref:System.Windows.Forms.DataGridColumnStyle> 物件（其為 <xref:System.Windows.Forms.DataGridTableStyle> 類別的成員）的屬性和方法，以程式設計方式刪除或隱藏 Windows Forms <xref:System.Windows.Forms.DataGrid> 控制項中的資料行。</span><span class="sxs-lookup"><span data-stu-id="9b36a-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="9b36a-106">已刪除或隱藏的資料行仍然存在於方格所系結的資料來源中，而且仍然可以透過程式設計方式存取。</span><span class="sxs-lookup"><span data-stu-id="9b36a-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="9b36a-107">它們就不會再顯示在 datagrid 中。</span><span class="sxs-lookup"><span data-stu-id="9b36a-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b36a-108">如果您的應用程式不會存取某些資料行，而且您不想要在 datagrid 中顯示它們，則可能不需要先將它們包含在資料來源中。</span><span class="sxs-lookup"><span data-stu-id="9b36a-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="9b36a-109">以程式設計方式刪除 DataGrid 中的資料行</span><span class="sxs-lookup"><span data-stu-id="9b36a-109">To delete a column from the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="9b36a-110">在表單的宣告區域中，宣告 <xref:System.Windows.Forms.DataGridTableStyle> 類別的新實例。</span><span class="sxs-lookup"><span data-stu-id="9b36a-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="9b36a-111">將 [<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType>] 屬性設定為您要套用樣式之資料來源中的資料表。</span><span class="sxs-lookup"><span data-stu-id="9b36a-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="9b36a-112">下列範例會使用其假設已設定的 <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b36a-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="9b36a-113">將新的 <xref:System.Windows.Forms.DataGridTableStyle> 物件加入至 datagrid 的資料表樣式集合。</span><span class="sxs-lookup"><span data-stu-id="9b36a-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="9b36a-114">呼叫 <xref:System.Windows.Forms.DataGrid>的 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> 集合的 <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> 方法，並指定要刪除之資料行的資料行索引。</span><span class="sxs-lookup"><span data-stu-id="9b36a-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="9b36a-115">以程式設計方式隱藏 DataGrid 中的資料行</span><span class="sxs-lookup"><span data-stu-id="9b36a-115">To hide a column in the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="9b36a-116">在表單的宣告區域中，宣告 <xref:System.Windows.Forms.DataGridTableStyle> 類別的新實例。</span><span class="sxs-lookup"><span data-stu-id="9b36a-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="9b36a-117">將 <xref:System.Windows.Forms.DataGridTableStyle> 的 <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> 屬性設定為您要套用樣式之資料來源中的資料表。</span><span class="sxs-lookup"><span data-stu-id="9b36a-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="9b36a-118">下列程式碼範例會使用其假設已設定的 <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b36a-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="9b36a-119">將新的 <xref:System.Windows.Forms.DataGridTableStyle> 物件加入至 datagrid 的資料表樣式集合。</span><span class="sxs-lookup"><span data-stu-id="9b36a-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="9b36a-120">將資料行的 `Width` 屬性設為0，並指定要隱藏之資料行的資料行索引，藉以隱藏資料行。</span><span class="sxs-lookup"><span data-stu-id="9b36a-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9b36a-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b36a-121">See also</span></span>

- [<span data-ttu-id="9b36a-122">如何：在執行階段時變更 Windows Forms DataGrid 控制項中顯示的資料</span><span class="sxs-lookup"><span data-stu-id="9b36a-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="9b36a-123">如何：將資料表和資料行新增至 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="9b36a-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
