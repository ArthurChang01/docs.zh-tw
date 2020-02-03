---
title: 將資料表和資料行加入至 DataGrid 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: 2db2e38c326cbcd78c58ee4fe00cd9ed20ae0e8a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747215"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="12b17-102">如何：將資料表和資料行加入至 Windows Form DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="12b17-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>

> [!NOTE]
> <span data-ttu-id="12b17-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="12b17-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="12b17-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="12b17-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

<span data-ttu-id="12b17-105">您可以藉由建立**DataGridTableStyle**物件並將其加入至**system.windows.forms.gridtablestylescollection>** 物件（可透過 <xref:System.Windows.Forms.DataGrid> 控制項的**system.windows.forms.datagrid.tablestyles**屬性存取），在 [資料表和資料行] 的 [Windows Forms <xref:System.Windows.Forms.DataGrid>] 控制項中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="12b17-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="12b17-106">每個資料表樣式都會顯示在**DataGridTableStyle**物件的**MappingName**屬性中指定之任何資料表的內容。</span><span class="sxs-lookup"><span data-stu-id="12b17-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="12b17-107">根據預設，未指定資料行樣式的資料表樣式，將會顯示該資料表中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="12b17-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="12b17-108">您可以藉由將**system.windows.forms.datagridcolumnstyle>** 物件新增至**system.windows.forms.gridcolumnstylescollection>** 物件（透過每個**DataGridTableStyle**物件的**system.windows.forms.datagridtablestyle.gridcolumnstyles**屬性存取），來限制資料表中的哪些資料行出現。</span><span class="sxs-lookup"><span data-stu-id="12b17-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="12b17-109">以程式設計方式將資料表和資料行加入至 DataGrid</span><span class="sxs-lookup"><span data-stu-id="12b17-109">To add a table and column to a DataGrid programmatically</span></span>

1. <span data-ttu-id="12b17-110">若要在資料表中顯示資料，您必須先將 <xref:System.Windows.Forms.DataGrid> 控制項系結至資料集。</span><span class="sxs-lookup"><span data-stu-id="12b17-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="12b17-111">如需詳細資訊，請參閱[如何：將 Windows Forms DataGrid 控制項系結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="12b17-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>

    > [!CAUTION]
    > <span data-ttu-id="12b17-112">以程式設計方式指定資料行樣式時，請一律先建立**system.windows.forms.datagridcolumnstyle>** 物件，並將它們加入至**system.windows.forms.gridcolumnstylescollection>** 物件，然後再將**DataGridTableStyle**物件新增至**system.windows.forms.gridtablestylescollection>** 物件。</span><span class="sxs-lookup"><span data-stu-id="12b17-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="12b17-113">當您將空的**DataGridTableStyle**物件新增至集合時，系統會自動為您產生**system.windows.forms.datagridcolumnstyle>** 物件。</span><span class="sxs-lookup"><span data-stu-id="12b17-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="12b17-114">因此，如果您嘗試將具有重複**MappingName**值的新**System.windows.forms.datagridcolumnstyle>** 物件加入**system.windows.forms.gridcolumnstylescollection>** 物件，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="12b17-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>

2. <span data-ttu-id="12b17-115">宣告新的資料表樣式，並設定其對應名稱。</span><span class="sxs-lookup"><span data-stu-id="12b17-115">Declare a new table style and set its mapping name.</span></span>

    ```vb
    Dim ts1 As New DataGridTableStyle()
    ts1.MappingName = "Customers"
    ```

    ```csharp
    DataGridTableStyle ts1 = new DataGridTableStyle();
    ts1.MappingName = "Customers";
    ```

    ```cpp
    DataGridTableStyle* ts1 = new DataGridTableStyle();
    ts1->MappingName = S"Customers";
    ```

3. <span data-ttu-id="12b17-116">宣告新的資料行樣式，並設定其對應名稱和其他屬性。</span><span class="sxs-lookup"><span data-stu-id="12b17-116">Declare a new column style and set its mapping name and other properties.</span></span>

    ```vb
    Dim myDataCol As New DataGridBoolColumn()
    myDataCol.HeaderText = "My New Column"
    myDataCol.MappingName = "Current"
    ```

    ```csharp
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();
    myDataCol.HeaderText = "My New Column";
    myDataCol.MappingName = "Current";
    ```

    ```cpp
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();
    myDataCol->HeaderText = "My New Column";
    myDataCol->MappingName = "Current";
    ```

4. <span data-ttu-id="12b17-117">呼叫**system.windows.forms.gridcolumnstylescollection>** 物件的**add**方法，將該資料行加入至資料表樣式</span><span class="sxs-lookup"><span data-stu-id="12b17-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>

    ```vb
    ts1.GridColumnStyles.Add(myDataCol)
    ```

    ```csharp
    ts1.GridColumnStyles.Add(myDataCol);
    ```

    ```cpp
    ts1->GridColumnStyles->Add(myDataCol);
    ```

5. <span data-ttu-id="12b17-118">呼叫**system.windows.forms.gridtablestylescollection>** 物件的**add**方法，將資料表樣式加入至資料方格。</span><span class="sxs-lookup"><span data-stu-id="12b17-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>

    ```vb
    DataGrid1.TableStyles.Add(ts1)
    ```

    ```csharp
    dataGrid1.TableStyles.Add(ts1);
    ```

    ```cpp
    dataGrid1->TableStyles->Add(ts1);
    ```

## <a name="see-also"></a><span data-ttu-id="12b17-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12b17-119">See also</span></span>

- [<span data-ttu-id="12b17-120">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="12b17-120">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="12b17-121">如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="12b17-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
