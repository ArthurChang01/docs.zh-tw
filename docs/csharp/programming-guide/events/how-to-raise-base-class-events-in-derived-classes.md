---
title: 如何在衍生類別中引發基類事件-程式C#設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 6176b94b15edccb139ddd7de3101930b505d98a8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346297"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="f6598-102">如何在衍生類別中引發基類事件（C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="f6598-102">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="f6598-103">下列簡單的範例示範在基底類別中宣告事件的標準方式，讓事件也可以從衍生類別引發。</span><span class="sxs-lookup"><span data-stu-id="f6598-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="f6598-104">這個模式會在 .NET Framework 類別庫的 Windows Forms 類別中廣泛使用。</span><span class="sxs-lookup"><span data-stu-id="f6598-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="f6598-105">當您建立可作為其他類別之基底類別的類別時，您應該考慮到事件其實是一種特殊的委派類型，只能在宣告事件的類別內予以叫用。</span><span class="sxs-lookup"><span data-stu-id="f6598-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="f6598-106">衍生類別無法直接叫用在基底類別內宣告的事件。</span><span class="sxs-lookup"><span data-stu-id="f6598-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="f6598-107">雖然有時您可能需要只能由基底類別引發的事件，但大多時候，您應該啟用衍生類別來叫用基底類別事件。</span><span class="sxs-lookup"><span data-stu-id="f6598-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="f6598-108">若要這樣做，您可以在包裝事件的基底類別中建立受保護的叫用方法。</span><span class="sxs-lookup"><span data-stu-id="f6598-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="f6598-109">藉由呼叫或覆寫這個叫用方法，衍生類別便能夠間接叫用該事件。</span><span class="sxs-lookup"><span data-stu-id="f6598-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6598-110">請勿在基底類別中宣告虛擬事件並在衍生類別中加以覆寫。</span><span class="sxs-lookup"><span data-stu-id="f6598-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="f6598-111">C# 編譯器無法正確處理這些事件，而且無法預測衍生事件的訂閱者是否會實際訂閱基底類別事件。</span><span class="sxs-lookup"><span data-stu-id="f6598-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6598-112">範例</span><span class="sxs-lookup"><span data-stu-id="f6598-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f6598-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6598-113">See also</span></span>

- [<span data-ttu-id="f6598-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f6598-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f6598-115">事件</span><span class="sxs-lookup"><span data-stu-id="f6598-115">Events</span></span>](./index.md)
- [<span data-ttu-id="f6598-116">委派</span><span class="sxs-lookup"><span data-stu-id="f6598-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="f6598-117">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="f6598-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="f6598-118">在 Windows Forms 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="f6598-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
