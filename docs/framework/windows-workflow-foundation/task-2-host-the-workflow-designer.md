---
title: 工作 2：裝載工作流程設計工具
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 8e4c17ed182cec7748b9a1f11f76ff90aa60c39e
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715782"
---
# <a name="task-2-host-the-workflow-designer"></a>工作 2：裝載工作流程設計工具

本主題描述在 Windows Presentation Foundation （WPF）應用程式中裝載 Windows 工作流程設計工具實例的程式。

此程式會設定包含設計工具的**方格**控制項，以程式設計方式建立包含預設 <xref:System.Activities.Statements.Sequence> 活動之 <xref:System.Activities.Presentation.WorkflowDesigner> 的實例，註冊設計工具中繼資料以提供所有內建活動的設計工具支援，並將工作流程設計工具裝載于 WPF 應用程式中。

## <a name="to-host-the-workflow-designer"></a>若要裝載工作流程設計工具

1. 開啟您在工作[1：建立新的 Windows Presentation Foundation 應用程式](task-1-create-a-new-wpf-app.md)中建立的 HostingApplication 專案。

2. 調整視窗大小，讓使用工作流程設計工具變得更容易。 若要這麼做，請在設計工具中選取 [ **mainwindow.xaml** ]，按 F4 顯示 [**屬性**] 視窗，然後**在 [配置**] 區段中，將 [**寬度**] 設定為600，並將 [**高度**] 設為 [350] 的值。

3. 選取設計工具中的 [**方格**] 面板（按一下**mainwindow.xaml**內的方塊），然後將 [**屬性**] 視窗頂端的 [**名稱**] 屬性設定為 "grid1"，以設定格線名稱。

4. 在 [**屬性**] 視窗中，按一下 [`ColumnDefinitions`] 屬性旁的省略號（ **...** ），以開啟 [**集合編輯器**] 對話方塊。

5. 在 [**集合編輯器**] 對話方塊中，按一下 [**加入**] 按鈕三次，將三個數據行插入配置中。 第一個資料行會包含 [**工具箱**]，第二個數據行會裝載工作流程設計工具，而第三個數據行則用於屬性偵測器。

6. 將中間資料行的 `Width` 屬性設定為 "4 *" 值。

7. 按一下 [確定] 儲存變更。 下列 XAML 會新增至您的*mainwindow.xaml*檔案：

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. 在**方案總管**中，以滑鼠右鍵按一下*mainwindow.xaml* ，然後選取 [ **View Code**]。 遵循下列步驟修改程式碼：

    1. 加入下列命名空間：

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. 若要宣告私用成員欄位以保存 <xref:System.Activities.Presentation.WorkflowDesigner>的實例，請將下列程式碼新增至 `MainWindow` 類別：

        ```csharp
        public partial class MainWindow : Window
        {
            private WorkflowDesigner wd;

            public MainWindow()
            {
                InitializeComponent();
            }
        }
        ```

    3. 將下列 `AddDesigner` 方法加入至 `MainWindow` 類別。 此執行會建立 <xref:System.Activities.Presentation.WorkflowDesigner>的實例、在其中加入 <xref:System.Activities.Statements.Sequence> 活動，並將它放在 grid1**方格**的中間資料行中。

        ```csharp
        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. 註冊設計工具中繼資料，為所有內建活動加入設計工具支援。 這可讓您將工具箱中的活動拖放到工作流程設計工具中的原始 <xref:System.Activities.Statements.Sequence> 活動。 若要這麼做，請將 `RegisterMetadata` 方法新增至 `MainWindow` 類別：

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        如需註冊活動設計工具的詳細資訊，請參閱[如何：建立自訂活動設計](how-to-create-a-custom-activity-designer.md)工具。

    5. 在 `MainWindow` 類別建構函式中，將呼叫加入至先前宣告的方法，為中繼資料註冊設計工具支援，以建立 <xref:System.Activities.Presentation.WorkflowDesigner>。

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > `RegisterMetadata` 方法會註冊內建活動 (包括 <xref:System.Activities.Statements.Sequence> 活動) 的設計工具中繼資料。 由於 `AddDesigner` 方法會使用 <xref:System.Activities.Statements.Sequence> 活動，因此必須先呼叫 `RegisterMetadata` 方法。

9. 按<kbd>F5</kbd>以建立並執行方案。

10. 請參閱工作[3：建立工具箱和 PropertyGrid 窗格](task-3-create-the-toolbox-and-propertygrid-panes.md)，以瞭解如何在重新裝載工作流程設計工具中加入 [**工具箱**] 和 [ **PropertyGrid** ] 支援。

## <a name="see-also"></a>請參閱

- [重新裝載工作流程設計工具](rehosting-the-workflow-designer.md)
- [工作 1：建立新的 Windows Presentation Foundation 應用程式](task-1-create-a-new-wpf-app.md)
- [工作 3：建立工具箱與 PropertyGrid 窗格](task-3-create-the-toolbox-and-propertygrid-panes.md)
