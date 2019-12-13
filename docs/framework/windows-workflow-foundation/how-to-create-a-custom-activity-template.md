---
title: 作法：建立自訂活動範本
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: f910d1367c941dbc319421d402cae8f4194872e5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715246"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="0233b-102">作法：建立自訂活動範本</span><span class="sxs-lookup"><span data-stu-id="0233b-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="0233b-103">自訂活動範本是用來自訂活動的組態，包括自訂複合活動，因此使用者不需要個別建立每個活動以及手動設定其所有屬性和其他設定。</span><span class="sxs-lookup"><span data-stu-id="0233b-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="0233b-104">這些自訂範本可在 Windows 工作流程設計工具的 [工具箱] 或從重新裝載設計**工具**中取得，使用者可以從中將其拖曳至預先設定的設計介面。</span><span class="sxs-lookup"><span data-stu-id="0233b-104">These custom templates can be made available in the **Toolbox** on the Windows Workflow Designer or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> <span data-ttu-id="0233b-105">工作流程設計工具隨附此類範本的良好範例： [[訊息活動設計](/visualstudio/workflow-designer/messaging-activity-designers)工具] 分類中的 [ [sendandreceivereply 範本設計](/visualstudio/workflow-designer/sendandreceivereply-template-designer)工具] 和 [ [receiveandsendreply 範本設計](/visualstudio/workflow-designer/receiveandsendreply-template-designer)工具]。</span><span class="sxs-lookup"><span data-stu-id="0233b-105">Workflow Designer ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="0233b-106">本主題中的第一個程式描述如何建立**Delay**活動的自訂活動範本，而第二個程式說明如何讓它在工作流程設計工具中提供，以驗證自訂範本是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="0233b-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a Workflow Designer to verify that the custom template works.</span></span>

 <span data-ttu-id="0233b-107">自訂活動範本必須實作 <xref:System.Activities.Presentation.IActivityTemplateFactory>。</span><span class="sxs-lookup"><span data-stu-id="0233b-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="0233b-108">此介面有單一 <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> 方法，您可以用它來建立及設定範本中所用的活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="0233b-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="0233b-109">若要建立 Delay 活動範本</span><span class="sxs-lookup"><span data-stu-id="0233b-109">To create a template for the Delay activity</span></span>

1. <span data-ttu-id="0233b-110">啟動 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="0233b-110">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="0233b-111">在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。</span><span class="sxs-lookup"><span data-stu-id="0233b-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="0233b-112">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0233b-112">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="0233b-113">在 [**專案類型**] 窗格中，根據您的語言喜好設定，從 [**視覺效果C#** 專案] 或 [ **Visual Basic** ] 群組選取 [**工作流程**]。</span><span class="sxs-lookup"><span data-stu-id="0233b-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4. <span data-ttu-id="0233b-114">在 [**範本**] 窗格中，選取 [**活動程式庫**]。</span><span class="sxs-lookup"><span data-stu-id="0233b-114">In the **Templates** pane, select **Activity Library**.</span></span>

5. <span data-ttu-id="0233b-115">在 [**名稱**] 方塊中，輸入 `DelayActivityTemplate`。</span><span class="sxs-lookup"><span data-stu-id="0233b-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6. <span data-ttu-id="0233b-116">接受 [**位置**] 和 [**方案名稱**] 文字方塊中的預設值，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0233b-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7. <span data-ttu-id="0233b-117">在**方案總管**中，以滑鼠右鍵按一下 DelayActivityTemplate 專案的 [參考] 目錄，然後選擇 [**加入參考**] 以開啟 [**加入參考**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0233b-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8. <span data-ttu-id="0233b-118">移至 [ **.net** ] 索引標籤，然後從左側的 [**元件名稱**] 欄中選取 [ **PresentationFramework** ]，然後按一下 **[確定]** ，將參考加入至 PresentationFramework 檔。</span><span class="sxs-lookup"><span data-stu-id="0233b-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="0233b-119">重複此程序，加入 System.Activities.Presentation.dll 和 WindowsBase.dll 檔案的參考。</span><span class="sxs-lookup"><span data-stu-id="0233b-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="0233b-120">以滑鼠右鍵按一下**方案總管**中的 DelayActivityTemplate 專案，然後依序選擇 [**加入**] 和 [**新增專案**]，開啟 [**加入新專案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0233b-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="0233b-121">選取 [**類別**] 範本，將它命名為 MyDelayTemplate，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0233b-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="0233b-122">開啟 MyDelayTemplate.cs 檔案，然後加入下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="0233b-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="0233b-123">使用具有下列程式碼的 <xref:System.Activities.Presentation.IActivityTemplateFactory> 類別來實作 `MyDelayActivity`。</span><span class="sxs-lookup"><span data-stu-id="0233b-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="0233b-124">這會將延遲設定擁有 10 秒持續時間。</span><span class="sxs-lookup"><span data-stu-id="0233b-124">This configures the delay to have a duration of 10 seconds.</span></span>

    ```csharp
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. <span data-ttu-id="0233b-125">從 [**建立**] 功能表中選取 [**建立方案**]，以產生 DelayActivityTemplate 檔案。</span><span class="sxs-lookup"><span data-stu-id="0233b-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="0233b-126">若要在工作流程設計工具中提供範本</span><span class="sxs-lookup"><span data-stu-id="0233b-126">To make the template available in a Workflow Designer</span></span>

1. <span data-ttu-id="0233b-127">以滑鼠右鍵按一下**方案總管**中的 [DelayActivityTemplate] 方案，然後依序選擇 [**加入**] 和 [**新增專案**]，開啟 [**加入新的專案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0233b-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="0233b-128">選取 **工作流程主控台應用程式** 範本，將它命名為 `CustomActivityTemplateApp`，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0233b-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3. <span data-ttu-id="0233b-129">在**方案總管**中，以滑鼠右鍵按一下 CustomActivityTemplateApp 專案的 [參考] 目錄，然後選擇 [**加入參考**] 以開啟 [**加入參考**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0233b-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4. <span data-ttu-id="0233b-130">移至 [**專案**] 索引標籤，然後從左側的 [**專案名稱**] 欄中選取 [ **DelayActivityTemplate** ]，然後按一下 **[確定]** ，將參考新增至您在第一個程式中建立的 DelayActivityTemplate 檔案。</span><span class="sxs-lookup"><span data-stu-id="0233b-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5. <span data-ttu-id="0233b-131">以滑鼠右鍵按一下**方案總管**中的 CustomActivityTemplateApp 專案，然後選擇 [**組建**] 以編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="0233b-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6. <span data-ttu-id="0233b-132">以滑鼠右鍵按一下**方案總管**中的 CustomActivityTemplateApp 專案，然後選擇 [**設定為啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="0233b-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7. <span data-ttu-id="0233b-133">從 [**調試**] 功能表中選取 [**啟動但不進行調試**]，然後在 cmd.exe 視窗中出現提示時，按任意鍵繼續進行。</span><span class="sxs-lookup"><span data-stu-id="0233b-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8. <span data-ttu-id="0233b-134">開啟 [Workflow1.xaml] 檔案，然後開啟 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="0233b-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="0233b-135">在 [ **DelayActivityTemplate** ] 類別中找出 [ **MyDelayActivity** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="0233b-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="0233b-136">將它拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="0233b-136">Drag it onto the design surface.</span></span> <span data-ttu-id="0233b-137">在 [**屬性**] 視窗中確認 `Duration` 屬性已設定為10秒。</span><span class="sxs-lookup"><span data-stu-id="0233b-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="0233b-138">範例</span><span class="sxs-lookup"><span data-stu-id="0233b-138">Example</span></span>
 <span data-ttu-id="0233b-139">MyDelayActivity.cs 檔案應該會包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="0233b-139">The MyDelayActivity.cs file should contain the following code.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="0233b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0233b-140">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="0233b-141">自訂工作流程設計體驗</span><span class="sxs-lookup"><span data-stu-id="0233b-141">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
