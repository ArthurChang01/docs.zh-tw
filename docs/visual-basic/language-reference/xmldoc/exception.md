---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 16ffb4f6b57dabb3650376c913a7d7608a00646d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523928"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="a5c8a-102">\<exception > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a5c8a-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="a5c8a-103">指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a5c8a-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5c8a-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5c8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a5c8a-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="a5c8a-106">可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="a5c8a-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="a5c8a-107">編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="a5c8a-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="a5c8a-108">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="a5c8a-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="a5c8a-109">描述。</span><span class="sxs-lookup"><span data-stu-id="a5c8a-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5c8a-110">備註</span><span class="sxs-lookup"><span data-stu-id="a5c8a-110">Remarks</span></span>  
 <span data-ttu-id="a5c8a-111">使用 `<exception>` 標記來指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a5c8a-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="a5c8a-112">此標記會套用到方法定義。</span><span class="sxs-lookup"><span data-stu-id="a5c8a-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="a5c8a-113">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="a5c8a-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5c8a-114">範例</span><span class="sxs-lookup"><span data-stu-id="a5c8a-114">Example</span></span>  
 <span data-ttu-id="a5c8a-115">這個範例會使用 `<exception>` 標記來描述 `IntDivide` 函數可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a5c8a-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a5c8a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5c8a-116">See also</span></span>

- [<span data-ttu-id="a5c8a-117">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="a5c8a-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
