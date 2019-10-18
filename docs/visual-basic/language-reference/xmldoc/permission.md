---
title: <permission> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 904d573514bf35b773d47321b7fd3b6a86e90262
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524696"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="9372b-102">\<permission > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="9372b-102">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="9372b-103">指定成員的必要許可權。</span><span class="sxs-lookup"><span data-stu-id="9372b-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9372b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9372b-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9372b-105">參數</span><span class="sxs-lookup"><span data-stu-id="9372b-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="9372b-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="9372b-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="9372b-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="9372b-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="9372b-108">將 `member` 括在引號（""）中。</span><span class="sxs-lookup"><span data-stu-id="9372b-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="9372b-109">成員存取權的描述。</span><span class="sxs-lookup"><span data-stu-id="9372b-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9372b-110">備註</span><span class="sxs-lookup"><span data-stu-id="9372b-110">Remarks</span></span>  
 <span data-ttu-id="9372b-111">使用 `<permission>` 標記來記錄成員的存取。</span><span class="sxs-lookup"><span data-stu-id="9372b-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="9372b-112">使用 <xref:System.Security.PermissionSet> 類別來指定成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="9372b-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="9372b-113">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="9372b-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9372b-114">範例</span><span class="sxs-lookup"><span data-stu-id="9372b-114">Example</span></span>  
 <span data-ttu-id="9372b-115">這個範例會使用 `<permission>` 標記來描述 `ReadFile` 方法所需的 <xref:System.Security.Permissions.FileIOPermission>。</span><span class="sxs-lookup"><span data-stu-id="9372b-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="9372b-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="9372b-116">See also</span></span>

- [<span data-ttu-id="9372b-117">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="9372b-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
