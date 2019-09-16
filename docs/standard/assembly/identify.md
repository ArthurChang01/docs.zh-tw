---
title: 作法：判斷檔案是否為元件
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: f9bff86ac559e40136ed016b862eef8ba0863ce3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973219"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="4fc0e-102">HOW TO：判斷檔案是否為元件</span><span class="sxs-lookup"><span data-stu-id="4fc0e-102">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="4fc0e-103">檔案只有受管理時才是組件，而且其中繼資料會包含組件項目。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="4fc0e-104">如需元件和中繼資料的詳細資訊，請參閱[組件資訊清單](manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-104">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="4fc0e-105">如何以手動方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="4fc0e-105">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="4fc0e-106">啟動 [Ildasm.exe (IL 反組譯工具)](../../framework/tools/ildasm-exe-il-disassembler.md)。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-106">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="4fc0e-107">載入您要測試的檔案。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-107">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="4fc0e-108">如果 **ILDASM** 回報該檔案並非可攜式執行檔 (PE)，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="4fc0e-109">如需詳細資訊，請參閱主題[如何：視圖元件內容](view-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-109">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="4fc0e-110">如何以程式設計方式判斷檔案是否為組件</span><span class="sxs-lookup"><span data-stu-id="4fc0e-110">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="4fc0e-111">呼叫 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> 方法，並傳遞您要測試之檔案的完整檔案路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="4fc0e-112">如果擲回 <xref:System.BadImageFormatException> 例外狀況，則檔案不是組件。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fc0e-113">範例</span><span class="sxs-lookup"><span data-stu-id="4fc0e-113">Example</span></span>  
<span data-ttu-id="4fc0e-114">此範例會測試一個 DLL 以查看其是否為組件。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-114">This example tests a DLL to see if it is an assembly.</span></span>  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```
 
<span data-ttu-id="4fc0e-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法會載入測試檔案，然後在讀取資訊之後釋放它。</span><span class="sxs-lookup"><span data-stu-id="4fc0e-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc0e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fc0e-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="4fc0e-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4fc0e-117">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4fc0e-118">程式設計概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4fc0e-118">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="4fc0e-119">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="4fc0e-119">Assemblies in .NET</span></span>](index.md)