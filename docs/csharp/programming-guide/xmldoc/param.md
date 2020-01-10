---
title: <param> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: f9613a7373a829d2a52f3f56b8ea1ab35ebdcf5f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711723"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="55a4c-102">\<param> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="55a4c-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="55a4c-103">語法</span><span class="sxs-lookup"><span data-stu-id="55a4c-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="55a4c-104">參數</span><span class="sxs-lookup"><span data-stu-id="55a4c-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="55a4c-105">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="55a4c-105">The name of a method parameter.</span></span> <span data-ttu-id="55a4c-106">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="55a4c-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="55a4c-107">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="55a4c-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55a4c-108">備註</span><span class="sxs-lookup"><span data-stu-id="55a4c-108">Remarks</span></span>  
 <span data-ttu-id="55a4c-109">\<param> 標記應該在方法宣告的註解中用來描述參數的其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="55a4c-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="55a4c-110">若要記錄多個參數，請使用多個 \<param > 標記。</span><span class="sxs-lookup"><span data-stu-id="55a4c-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="55a4c-111">\<param> 標記的文字將會顯示於 IntelliSense (即物件瀏覽器) 以及程式碼結構 Web 報告中。</span><span class="sxs-lookup"><span data-stu-id="55a4c-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="55a4c-112">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="55a4c-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55a4c-113">範例</span><span class="sxs-lookup"><span data-stu-id="55a4c-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="55a4c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="55a4c-114">See also</span></span>

- [<span data-ttu-id="55a4c-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="55a4c-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="55a4c-116">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="55a4c-116">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
