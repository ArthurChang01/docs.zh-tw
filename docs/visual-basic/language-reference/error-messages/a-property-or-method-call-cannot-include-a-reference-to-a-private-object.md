---
title: 屬性或方法呼叫不能包含 private 物件的參考，也不可以當做引數或傳回值
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 53f9052555555a5b9dcb038dfee9cd54dc2b4251
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976205"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="41f64-102">屬性或方法呼叫不能包含 private 物件的參考，也不可以當做引數或傳回值</span><span class="sxs-lookup"><span data-stu-id="41f64-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>

<span data-ttu-id="41f64-103">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="41f64-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="41f64-104">用戶端已叫用跨處理序元件的屬性或方法，並嘗試將 private 物件的參考傳遞為其中一個引數。</span><span class="sxs-lookup"><span data-stu-id="41f64-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
- <span data-ttu-id="41f64-105">跨處理序元件已在其用戶端上叫用回撥方法，並嘗試傳遞 private 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="41f64-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
- <span data-ttu-id="41f64-106">跨處理序元件已嘗試將 private 物件的參考傳遞為所引發事件的引數。</span><span class="sxs-lookup"><span data-stu-id="41f64-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
- <span data-ttu-id="41f64-107">用戶端已嘗試將 private 物件參考指派給所處理事件的 `ByRef` 引數。</span><span class="sxs-lookup"><span data-stu-id="41f64-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41f64-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="41f64-108">To correct this error</span></span>  
  
1. <span data-ttu-id="41f64-109">請移除參考。</span><span class="sxs-lookup"><span data-stu-id="41f64-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f64-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="41f64-110">See also</span></span>

- [<span data-ttu-id="41f64-111">Private</span><span class="sxs-lookup"><span data-stu-id="41f64-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
