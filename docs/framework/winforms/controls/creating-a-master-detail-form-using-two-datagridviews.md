---
title: 逐步解說：使用兩個 DataGridView 控制項建立主版詳細表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: bb3da36430c7493b941f3711cb584b4517d5bd54
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740578"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>逐步解說：使用兩個 Windows Form DataGridView 控制項建立主要/詳細表單

使用 <xref:System.Windows.Forms.DataGridView> 控制項的其中一個最常見案例是*主要/詳細資料*形式，其中會顯示兩個資料庫資料表之間的父/子關聯性。 選取主資料表中的資料列，會使詳細資料表以對應的子資料進行更新。

使用 <xref:System.Windows.Forms.DataGridView> 控制項和 <xref:System.Windows.Forms.BindingSource> 元件之間的互動，可以輕鬆地執行主要/詳細資料表單。 在本逐步解說中，您將使用兩個 <xref:System.Windows.Forms.DataGridView> 控制項和兩個 <xref:System.Windows.Forms.BindingSource> 元件來建立表單。 表單會顯示 Northwind SQL Server 範例資料庫中的兩個相關資料表： `Customers` 和 `Orders`。 當您完成時，您將會有一個表單，其中顯示 master <xref:System.Windows.Forms.DataGridView> 資料庫中的所有客戶，以及詳細資料 <xref:System.Windows.Forms.DataGridView>中所選客戶的所有訂單。

若要將本主題中的程式碼複製成單一清單，請參閱[如何：使用兩個 Windows Forms DataGridView 控制項建立主要/詳細表單](create-a-master-detail-form-using-two-datagridviews.md)。

## <a name="prerequisites"></a>必要條件

為了完成這個逐步解說，您需要：

- 具有 Northwind SQL Server 範例資料庫之伺服器的存取權。

## <a name="creating-the-form"></a>建立表單

#### <a name="to-create-a-masterdetail-form"></a>若要建立主要/詳細資料表單

1. 建立衍生自 <xref:System.Windows.Forms.Form> 的類別，並包含兩個 <xref:System.Windows.Forms.DataGridView> 控制項和兩個 <xref:System.Windows.Forms.BindingSource> 元件。 下列程式碼提供基本表單初始化，並包含 `Main` 方法。 如果您使用 Visual Studio 設計工具來建立表單，您可以使用設計工具產生的程式碼，而不是這段程式碼，但請務必使用此處變數宣告中所顯示的名稱。

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. 在表單的類別定義中執行方法，以處理連接至資料庫的詳細資料。 這個範例會使用 `GetData` 方法來填入 <xref:System.Data.DataSet> 物件、將 <xref:System.Data.DataRelation> 物件加入至資料集，以及系結 <xref:System.Windows.Forms.BindingSource> 元件。 請務必將 `connectionString` 變數設定為適用於您資料庫的值。

    > [!IMPORTANT]
    > 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. 為表單的 <xref:System.Windows.Forms.Form.Load> 事件執行處理常式，以將 <xref:System.Windows.Forms.DataGridView> 控制項系結至 <xref:System.Windows.Forms.BindingSource> 元件，並呼叫 `GetData` 方法。 下列範例包含的程式碼會調整 <xref:System.Windows.Forms.DataGridView> 資料行的大小，以符合顯示的資料。

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>測試應用程式

您現在可以測試表單，以確定它會如預期般運作。

#### <a name="to-test-the-form"></a>測試表單

- 編譯並執行應用程式。

  您會看到兩個 <xref:System.Windows.Forms.DataGridView> 控制項，其中一個是在另一個上方。 最上面是 Northwind `Customers` 資料表的客戶，底部是對應到所選客戶的 `Orders`。 當您在上方 <xref:System.Windows.Forms.DataGridView>中選取不同的資料列時，較低 <xref:System.Windows.Forms.DataGridView> 的內容也會隨之變更。

## <a name="next-steps"></a>後續步驟

此應用程式可讓您對 <xref:System.Windows.Forms.DataGridView> 控制項的功能有基本瞭解。 您可以透過數種方式自訂 <xref:System.Windows.Forms.DataGridView> 控制項的外觀和行為：

- 變更框線和標題樣式。 如需詳細資訊，請參閱[如何：變更 Windows Forms DataGridView 控制項中的框線和格線樣式](change-the-border-and-gridline-styles-in-the-datagrid.md)。

- 啟用或限制 <xref:System.Windows.Forms.DataGridView> 控制項的使用者輸入。 如需詳細資訊，請參閱[如何：防止在 Windows Forms Datagridview 控制項中新增和刪除](prevent-row-addition-and-deletion-datagridview.md)資料[列和如何：將 Windows Forms DataGridView 控制項中](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)的資料行設為唯讀。

- 驗證 <xref:System.Windows.Forms.DataGridView> 控制項的使用者輸入。 如需詳細資訊，請參閱[逐步解說：驗證 Windows Forms DataGridView 控制項中的資料](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。

- 使用虛擬模式處理非常大型的資料集。 如需詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項中執行虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)。

- 自訂儲存格的外觀。 如需詳細資訊，請參閱[如何：在 Windows Forms Datagridview 控制項中自訂儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)和[如何：設定 Windows Forms DataGridView 控制項的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [操作說明：使用兩個 Windows Forms DataGridView 控制項建立主從式表單](create-a-master-detail-form-using-two-datagridviews.md)
- [保護連線資訊](../../data/adonet/protecting-connection-information.md)
