---
title: 自訂複合設計工具 - 工作流程項目展示器
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: d1047b8be35545e83eaa8788b53751b6b0056984
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338046"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="b04f8-102">自訂複合設計工具 - 工作流程項目展示器</span><span class="sxs-lookup"><span data-stu-id="b04f8-102">Custom Composite Designers - Workflow Item Presenter</span></span>

<span data-ttu-id="b04f8-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> 是 WF 設計工具程式設計模型中的金鑰類型，可讓您建立可以放置任意活動的「卸載區」。</span><span class="sxs-lookup"><span data-stu-id="b04f8-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="b04f8-104">這個範例示範如何建立一個顯示「卸載區」的活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="b04f8-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

<span data-ttu-id="b04f8-105">這個範例會示範下列情況：</span><span class="sxs-lookup"><span data-stu-id="b04f8-105">This sample demonstrates:</span></span>

- <span data-ttu-id="b04f8-106">建立具有 <xref:System.Activities.Presentation.WorkflowItemPresenter> 的自訂活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="b04f8-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="b04f8-107">使用中繼資料存放區登錄自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="b04f8-107">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="b04f8-108">以宣告和強制方式設計重新裝載之工具箱的程式。</span><span class="sxs-lookup"><span data-stu-id="b04f8-108">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="b04f8-109">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="b04f8-109">Sample Details</span></span>

<span data-ttu-id="b04f8-110">這個範例的程式碼會示範：</span><span class="sxs-lookup"><span data-stu-id="b04f8-110">The code for this sample shows:</span></span>

- <span data-ttu-id="b04f8-111">針對 `SimpleNativeActivity` 類別建置自訂活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="b04f8-111">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="b04f8-112">建立具有 <xref:System.Activities.Presentation.WorkflowItemPresenter> 的自訂活動設計工具</span><span class="sxs-lookup"><span data-stu-id="b04f8-112">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 <span data-ttu-id="b04f8-113">請注意繫結至 `ModelItem.Body` 的 WPF 資料繫結用法。</span><span class="sxs-lookup"><span data-stu-id="b04f8-113">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="b04f8-114">`ModelItem` 是 <xref:System.Activities.Presentation.ActivityDesigner> 上的屬性，其參考設計工具所使用的基礎物件，在此案例中為**命名為 simplenativeactivity**。</span><span class="sxs-lookup"><span data-stu-id="b04f8-114">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="b04f8-115">設定、建立和執行範例</span><span class="sxs-lookup"><span data-stu-id="b04f8-115">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="b04f8-116">在 Visual Studio 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="b04f8-116">Open the solution in Visual Studio.</span></span>

2. <span data-ttu-id="b04f8-117">按**F5**以編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b04f8-117">Press **F5** to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b04f8-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b04f8-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b04f8-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="b04f8-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b04f8-120">如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="b04f8-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b04f8-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="b04f8-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`

## <a name="see-also"></a><span data-ttu-id="b04f8-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="b04f8-122">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="b04f8-123">使用工作流程設計工具開發應用程式</span><span class="sxs-lookup"><span data-stu-id="b04f8-123">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
