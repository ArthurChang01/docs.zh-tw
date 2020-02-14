---
title: dllMainReturnsFalse MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 0b413521e0a2dc06c2ff0be642f080eaf541202f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216436"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="b08fb-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="b08fb-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="b08fb-103">如果以理由 DLL_PROCESS_ATTACH 呼叫的使用者組件 Managed `dllMainReturnsFalse` 函式，傳回 FALSE，就會啟動 `DllMain` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="b08fb-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b08fb-104">徵狀</span><span class="sxs-lookup"><span data-stu-id="b08fb-104">Symptoms</span></span>  
 <span data-ttu-id="b08fb-105">`DllMain` 函式傳回 FALSE，指出未正確執行。</span><span class="sxs-lookup"><span data-stu-id="b08fb-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="b08fb-106">因為 `DllMain` 函式通常會包含重要的初始化程式碼，所以這會造成未定的問題。</span><span class="sxs-lookup"><span data-stu-id="b08fb-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b08fb-107">原因</span><span class="sxs-lookup"><span data-stu-id="b08fb-107">Cause</span></span>  
 <span data-ttu-id="b08fb-108">因為在載入時 DLL 初始化發生 DLL_PROCESS_ATTACH，所以呼叫 `DllMain` 函式。</span><span class="sxs-lookup"><span data-stu-id="b08fb-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="b08fb-109">如果它傳回 FALSE，表示該 DLL 初始化失敗。</span><span class="sxs-lookup"><span data-stu-id="b08fb-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b08fb-110">解決方案</span><span class="sxs-lookup"><span data-stu-id="b08fb-110">Resolution</span></span>  
 <span data-ttu-id="b08fb-111">分析失敗 DLL 的 `DllMain` 函式程式碼，找出初始化失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="b08fb-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b08fb-112">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="b08fb-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="b08fb-113">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="b08fb-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="b08fb-114">它只報告 `DllMain` 傳回值的相關資料。</span><span class="sxs-lookup"><span data-stu-id="b08fb-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b08fb-115">輸出</span><span class="sxs-lookup"><span data-stu-id="b08fb-115">Output</span></span>  
 <span data-ttu-id="b08fb-116">訊息，指出因為 DLL_PROCESS_ATTACH 而呼叫的 `DllMain` 函式傳回 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b08fb-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="b08fb-117">請注意，只有在 Managed 程式碼中實作 `DllMain` 時，才會啟用這個 MDA。</span><span class="sxs-lookup"><span data-stu-id="b08fb-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b08fb-118">組態</span><span class="sxs-lookup"><span data-stu-id="b08fb-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b08fb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b08fb-119">See also</span></span>

- [<span data-ttu-id="b08fb-120">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="b08fb-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
