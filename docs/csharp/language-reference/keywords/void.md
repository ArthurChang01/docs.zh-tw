---
title: void - C# 參考
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 0624b547ee2586334ac35d366ae3c8dfd14963ee
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742768"
---
# <a name="void-c-reference"></a><span data-ttu-id="db0e1-102">void (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="db0e1-102">void (C# Reference)</span></span>

<span data-ttu-id="db0e1-103">當 `void` 作為方法的傳回型別時，其可指定方法不要傳回值。</span><span class="sxs-lookup"><span data-stu-id="db0e1-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="db0e1-104">方法的參數清單中不允許 `void`。</span><span class="sxs-lookup"><span data-stu-id="db0e1-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="db0e1-105">如果某方法不採用任何參數，且不傳回任何值，其宣告方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="db0e1-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="db0e1-106">`void` 也可用於不安全的內容中，以宣告未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="db0e1-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="db0e1-107">如需詳細資訊，請參閱[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="db0e1-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="db0e1-108">`void` 是 .NET Framework <xref:System.Void?displayProperty=nameWithType> 類型的別名。</span><span class="sxs-lookup"><span data-stu-id="db0e1-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="db0e1-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="db0e1-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="db0e1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db0e1-110">See also</span></span>

- [<span data-ttu-id="db0e1-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="db0e1-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="db0e1-112">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="db0e1-112">C# keywords</span></span>](index.md)
- [<span data-ttu-id="db0e1-113">參考型別</span><span class="sxs-lookup"><span data-stu-id="db0e1-113">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="db0e1-114">值類型</span><span class="sxs-lookup"><span data-stu-id="db0e1-114">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="db0e1-115">方法</span><span class="sxs-lookup"><span data-stu-id="db0e1-115">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="db0e1-116">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="db0e1-116">Unsafe code and pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
