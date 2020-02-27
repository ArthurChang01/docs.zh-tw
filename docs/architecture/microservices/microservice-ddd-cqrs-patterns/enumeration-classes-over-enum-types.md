---
title: 使用列舉類別，而非列舉類型
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 了解如何使用列舉類別 (而非列舉) 來解決後者的一些限制。
ms.date: 10/08/2018
ms.openlocfilehash: 82bd80d19b3b73eb2f45ede8cc7ad4593c688277
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628458"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="fc98f-103">使用列舉類別，而非列舉類型</span><span class="sxs-lookup"><span data-stu-id="fc98f-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="fc98f-104">[列舉](../../../csharp/language-reference/builtin-types/enum.md) (簡稱「列舉類型」) 是整數型別的精簡語言包裝函式。</span><span class="sxs-lookup"><span data-stu-id="fc98f-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="fc98f-105">您可能會想要將其用途限制在儲存一組封閉值中的一個值時。</span><span class="sxs-lookup"><span data-stu-id="fc98f-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="fc98f-106">依大小 (小、中、大) 分類是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="fc98f-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="fc98f-107">使用列舉來控制流程或更強固的抽象概念可能會導致[程式碼異味](https://deviq.com/code-smells/) (Code Smell)。</span><span class="sxs-lookup"><span data-stu-id="fc98f-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="fc98f-108">這種使用方式會導致程式碼因為有許多查看列舉值的控制流程陳述式而變得很脆弱。</span><span class="sxs-lookup"><span data-stu-id="fc98f-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="fc98f-109">相反地，您可以建立列舉類別，以便利用物件導向語言的所有豐富功能。</span><span class="sxs-lookup"><span data-stu-id="fc98f-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="fc98f-110">不過，這個主題並不重要，而且在許多情況下，為了方便作業，您仍然可以使用標準[列舉類型](../../../csharp/language-reference/builtin-types/enum.md) (如果偏好這樣做)。</span><span class="sxs-lookup"><span data-stu-id="fc98f-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="fc98f-111">無論如何，使用列舉類別與商務相關概念比較有關。</span><span class="sxs-lookup"><span data-stu-id="fc98f-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="fc98f-112">實作列舉基底類別</span><span class="sxs-lookup"><span data-stu-id="fc98f-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="fc98f-113">eShopOnContainers 中的訂購微服務提供範例列舉基底類別實作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fc98f-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public |
                                         BindingFlags.Static |
                                         BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;

        if (otherValue == null)
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);

    // Other utility methods ...
}
```

<span data-ttu-id="fc98f-114">您可以使用此類別作為任何實體或值物件中的類型，如下列 `CardType` : `Enumeration` 類別所示：</span><span class="sxs-lookup"><span data-stu-id="fc98f-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="fc98f-115">其他資源</span><span class="sxs-lookup"><span data-stu-id="fc98f-115">Additional resources</span></span>

- <span data-ttu-id="fc98f-116">**Jimmy Bogard。列舉類別** </span><span class="sxs-lookup"><span data-stu-id="fc98f-116">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="fc98f-117">**Steve Smith。 \ 中的C#列舉替代**專案</span><span class="sxs-lookup"><span data-stu-id="fc98f-117">**Steve Smith. Enum Alternatives in C#** \</span></span>
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="fc98f-118">**Enumeration.cs：**</span><span class="sxs-lookup"><span data-stu-id="fc98f-118">**Enumeration.cs.**</span></span> <span data-ttu-id="fc98f-119">eShopOnContainers 中的基底列舉類別 </span><span class="sxs-lookup"><span data-stu-id="fc98f-119">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="fc98f-120">**CardType.cs**：</span><span class="sxs-lookup"><span data-stu-id="fc98f-120">**CardType.cs**.</span></span> <span data-ttu-id="fc98f-121">eShopOnContainers 中的範例列舉類別</span><span class="sxs-lookup"><span data-stu-id="fc98f-121">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="fc98f-122">**SmartEnum**：</span><span class="sxs-lookup"><span data-stu-id="fc98f-122">**SmartEnum**.</span></span> <span data-ttu-id="fc98f-123">Ardalis - 可協助在 .NET 中產生強型別且更聰明的列舉。</span><span class="sxs-lookup"><span data-stu-id="fc98f-123">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="fc98f-124">[上一頁](implement-value-objects.md)
>[下一頁](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="fc98f-124">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
