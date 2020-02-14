---
title: openGenericCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
ms.openlocfilehash: de1735103314dfedbabe27623f579ce2c1e728af
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217270"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="b9bfb-102">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="b9bfb-102">openGenericCERCall MDA</span></span>

<span data-ttu-id="b9bfb-103">啟用 `openGenericCERCall` Managed 偵錯助理，警告根方法有泛型型別變數的限制執行區域 (CER) 圖形將在 JIT 編譯或原生映像產生時間處理，而且至少一個泛型型別變數是物件參考型別。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>

## <a name="symptoms"></a><span data-ttu-id="b9bfb-104">徵狀</span><span class="sxs-lookup"><span data-stu-id="b9bfb-104">Symptoms</span></span>

<span data-ttu-id="b9bfb-105">中止執行緒或卸載應用程式定義域時，未執行 CER。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>

## <a name="cause"></a><span data-ttu-id="b9bfb-106">原因</span><span class="sxs-lookup"><span data-stu-id="b9bfb-106">Cause</span></span>

<span data-ttu-id="b9bfb-107">在 JIT 編譯期間，包含物件參考型別的具現化僅具有代表性，因為共用產生的程式碼，而且每個物件參考型別變數都可能是任何物件參考型別。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="b9bfb-108">這可以避免事先準備一些執行階段資源。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>

<span data-ttu-id="b9bfb-109">特別的是，具有泛型型別變數的方法可以在背景緩慢地配置資源。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="b9bfb-110">這些稱為泛型字典項目。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="b9bfb-111">比方說，對於 `T` 是泛型型別變數的語句 `List<T> list = new List<T>();`，執行時間必須查閱，而且可能會在執行時間建立確切的具現化，例如 `List<Object>, List<String>`等等。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`, and so forth.</span></span> <span data-ttu-id="b9bfb-112">這可能會因超出開發人員控制的各種原因而失敗，例如記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>

<span data-ttu-id="b9bfb-113">只應該在 JIT 編譯期間啟用此 MDA，而不是有確切的具現化時。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>

<span data-ttu-id="b9bfb-114">啟用此 MDA 時，可能的徵兆是 CER 不會針對不正確的具現化作用。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="b9bfb-115">事實上，執行階段尚未嘗試在造成 MDA 啟用的情況下實作 CER。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="b9bfb-116">因此，如果開發人員使用 CER 的共用具現化，則攔截不到預定 CER 區域內的 JIT 編譯錯誤、泛型型別載入錯誤或執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>

## <a name="resolution"></a><span data-ttu-id="b9bfb-117">解決方案</span><span class="sxs-lookup"><span data-stu-id="b9bfb-117">Resolution</span></span>

<span data-ttu-id="b9bfb-118">請不要使用泛型型別變數，而這些變數是可能包含 CER 之方法的物件參考型別。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="b9bfb-119">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="b9bfb-119">Effect on the Runtime</span></span>

<span data-ttu-id="b9bfb-120">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-120">This MDA has no effect on the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="b9bfb-121">輸出</span><span class="sxs-lookup"><span data-stu-id="b9bfb-121">Output</span></span>

<span data-ttu-id="b9bfb-122">以下是此 MDA 的輸出範例：</span><span class="sxs-lookup"><span data-stu-id="b9bfb-122">The following is a sample of output from this MDA:</span></span>
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution. 
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a><span data-ttu-id="b9bfb-123">組態</span><span class="sxs-lookup"><span data-stu-id="b9bfb-123">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a><span data-ttu-id="b9bfb-124">範例</span><span class="sxs-lookup"><span data-stu-id="b9bfb-124">Example</span></span>

<span data-ttu-id="b9bfb-125">未執行 CER 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b9bfb-125">The CER code is not executed.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.CompilerServices;

class Program
{
    static void Main(string[] args)
    {
        CallGenericMethods();
    }
    static void CallGenericMethods()
    {
        // This call is correct. The instantiation of the method
        // contains only nonreference types.
        MyClass.GenericMethodWithCer<int>();

        // This call is incorrect. A shared version of the method that
        // cannot be completely analyzed will be JIT-compiled. The 
        // MDA will be activated at JIT-compile time, not at run time.
        MyClass.GenericMethodWithCer<String>();
    }
}

class MyClass
{
    public static void GenericMethodWithCer<T>()
    {
        RuntimeHelpers.PrepareConstrainedRegions();
        try
        {

        }
        finally
        {
            // This is the start of the CER.
            Console.WriteLine("In finally block.");
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="b9bfb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9bfb-126">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="b9bfb-127">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="b9bfb-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
