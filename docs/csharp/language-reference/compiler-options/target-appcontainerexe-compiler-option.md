---
title: -target:appcontainerexe (C# 編譯器選項)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204528"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="2e47d-102">-target:appcontainerexe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="2e47d-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="2e47d-103">如果您使用 **-target:appcontainerexe** 編譯器選項，編譯器會建立一個必須在應用程式容器中執行的 Windows 可執行檔 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="2e47d-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="2e47d-104">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span><span class="sxs-lookup"><span data-stu-id="2e47d-104">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e47d-105">語法</span><span class="sxs-lookup"><span data-stu-id="2e47d-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="2e47d-106">備註</span><span class="sxs-lookup"><span data-stu-id="2e47d-106">Remarks</span></span>  
 <span data-ttu-id="2e47d-107">這個選項會在 [Portable Executable](/windows/desktop/Debug/pe-format) (可攜式執行檔) (PE) 中設定一個位元，以要求應用程式在應用程式容器中執行。</span><span class="sxs-lookup"><span data-stu-id="2e47d-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="2e47d-108">當這個位元設定時，如果 CreateProcess 方法嘗試在應用程式容器之外啟動可執行檔，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e47d-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="2e47d-109">除非您使用 [-out](./out-compiler-option.md) 選項指定輸出檔案名稱，否則輸出檔案名稱會採用包含 [Main](../../programming-guide/main-and-command-args/index.md) 方法的輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="2e47d-109">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="2e47d-110">如果您在命令提示字元指定這個選項，下一個 **-out** 或 **-target** 選項之前的所有檔案都是用來建立可執行檔。</span><span class="sxs-lookup"><span data-stu-id="2e47d-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="2e47d-111">若要在 IDE 中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="2e47d-111">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="2e47d-112">在方案總管中，開啟專案的捷徑功能表，然後選擇 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="2e47d-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="2e47d-113">在 [應用程式] 索引標籤上，選擇 [輸出類型] 清單中的 [Windows 市集應用程式]。</span><span class="sxs-lookup"><span data-stu-id="2e47d-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="2e47d-114">This option is available only for Windows 8.x Store app templates.</span><span class="sxs-lookup"><span data-stu-id="2e47d-114">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="2e47d-115">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="2e47d-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e47d-116">範例</span><span class="sxs-lookup"><span data-stu-id="2e47d-116">Example</span></span>  
 <span data-ttu-id="2e47d-117">下列命令會將 `filename.cs` 編譯至一個只能在應用程式容器中執行的 Windows 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="2e47d-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e47d-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="2e47d-118">See also</span></span>

- [<span data-ttu-id="2e47d-119">-target (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="2e47d-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="2e47d-120">-target:winexe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="2e47d-120">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="2e47d-121">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="2e47d-121">C# Compiler Options</span></span>](./index.md)
