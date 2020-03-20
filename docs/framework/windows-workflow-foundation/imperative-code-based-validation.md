---
title: 命令式的程式碼式驗證
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: f3b07d0ab06b3753286c929b90e713a6941684ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143092"
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="3a1c1-102">命令式的程式碼式驗證</span><span class="sxs-lookup"><span data-stu-id="3a1c1-102">Imperative Code-Based Validation</span></span>

<span data-ttu-id="3a1c1-103">命令式的程式碼驗證提供一個簡單的方式，可讓活動提供與其本身相關的驗證，而且適用於衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 的活動。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-103">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="3a1c1-104">活動中會加入用來判斷任何驗證錯誤或警告的驗證程式碼。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-104">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="3a1c1-105">使用程式碼驗證</span><span class="sxs-lookup"><span data-stu-id="3a1c1-105">Using Code-Based Validation</span></span>

<span data-ttu-id="3a1c1-106">由衍生自 <xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 的活動可支援程式碼驗證。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-106">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="3a1c1-107">驗證碼可以放在 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫中，而且可以將驗證錯誤或警告加入至中繼資料引數。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-107">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="3a1c1-108">在下列範例中，如果 `Cost` 大於 `Price`，就會將驗證錯誤加入至中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-108">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a1c1-109">請注意，`Cost`和 `Price` 不是活動的引數，而是在設計階段設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-109">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="3a1c1-110">這就是為什麼可以在 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 覆寫中驗證其值的原因。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-110">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="3a1c1-111">在設計階段不能驗證流經引數的資料值，因為在執行階段之前，資料不會流過，但是可以驗證活動引數，以確保已使用 `RequiredArgument` 屬性和多載群組來繫結這些引數。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-111">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="3a1c1-112">此程式碼範例會查看 `RequiredArgument` 引數的 `Description` 屬性，如果未繫結，則會產生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-112">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="3a1c1-113">必需參數在["必需參數"和"重載組](required-arguments-and-overload-groups.md)"仲介紹。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-113">Required arguments are covered in [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 <span data-ttu-id="3a1c1-114">根據預設，當呼叫 <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> 時，會將驗證錯誤加入至中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-114">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="3a1c1-115">若要加入驗證警告，請使用採取 <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> 的 <xref:System.Activities.Validation.ValidationError> 多載，並設定 <xref:System.Activities.Validation.ValidationError> 屬性來指定 <xref:System.Activities.Validation.ValidationError.IsWarning%2A> 表示警告。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-115">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="3a1c1-116">在工作流程設計工具中修改工作流程時，若工作流程設計工具中顯示任何驗證錯誤或警告，就會進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-116">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="3a1c1-117">叫用工作流程時，也會在執行階段進行驗證，而且如果發生任何驗證錯誤，預設驗證邏輯會擲回 <xref:System.Activities.InvalidWorkflowException>。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-117">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="3a1c1-118">有關調用驗證和訪問任何驗證警告或錯誤的詳細資訊，請參閱[調用活動驗證](invoking-activity-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-118">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="3a1c1-119">從 <xref:System.Activities.CodeActivity.CacheMetadata%2A> 擲回的任何例外狀況都不會被視為驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-119">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="3a1c1-120">這些例外狀況會從 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> 的呼叫中逸出，而且必須由呼叫端處理。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-120">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="3a1c1-121">程式碼驗證對於驗證包含程式碼的活動很有用，但工作流程中的其他活動並不會顯示出來。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-121">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="3a1c1-122">聲明約束驗證提供了驗證活動與工作流中其他活動之間的關係的能力，並在["聲明約束"](declarative-constraints.md)主題仲介紹。</span><span class="sxs-lookup"><span data-stu-id="3a1c1-122">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](declarative-constraints.md) topic.</span></span>
