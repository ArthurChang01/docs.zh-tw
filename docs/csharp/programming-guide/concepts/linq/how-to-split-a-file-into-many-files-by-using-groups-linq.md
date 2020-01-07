---
title: 如何使用群組將檔案分割成許多檔案（LINQ）（C#）
ms.date: 07/20/2015
ms.assetid: 8179b91c-d778-4e57-884f-77fe5a8e4e40
ms.openlocfilehash: 934b6385a8634c23a4e29098367c9aaa7355f11c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347311"
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-c"></a><span data-ttu-id="ef94a-102">如何使用群組將檔案分割成許多檔案（LINQ）（C#）</span><span class="sxs-lookup"><span data-stu-id="ef94a-102">How to split a file into many files by using groups (LINQ) (C#)</span></span>
<span data-ttu-id="ef94a-103">此範例示範如何合併兩個檔案的內容，然後建立一組以新方法組織資料的新檔案。</span><span class="sxs-lookup"><span data-stu-id="ef94a-103">This example shows one way to merge the contents of two files and then create a set of new files that organize the data in a new way.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="ef94a-104">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="ef94a-104">To create the data files</span></span>  
  
1. <span data-ttu-id="ef94a-105">將下列名稱複製到名為 names1.txt 的文字檔，並將它儲至專案資料夾：</span><span class="sxs-lookup"><span data-stu-id="ef94a-105">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```text  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2. <span data-ttu-id="ef94a-106">將下列名稱複製到名為 names2.txt 的文字檔，並將它儲至專案資料夾：請注意，這兩個檔案中有些名稱是相同的。</span><span class="sxs-lookup"><span data-stu-id="ef94a-106">Copy these names into a text file that is named names2.txt and save it in your project folder: Note that the two files have some names in common.</span></span>  
  
    ```text  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="ef94a-107">範例</span><span class="sxs-lookup"><span data-stu-id="ef94a-107">Example</span></span>  
  
```csharp  
class SplitWithGroups  
{  
    static void Main()  
    {  
        string[] fileA = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] fileB = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Concatenate and remove duplicate names based on  
        // default string comparer  
        var mergeQuery = fileA.Union(fileB);  
  
        // Group the names by the first letter in the last name.  
        var groupQuery = from name in mergeQuery  
                         let n = name.Split(',')  
                         group name by n[0][0] into g  
                         orderby g.Key  
                         select g;  
  
        // Create a new file for each group that was created  
        // Note that nested foreach loops are required to access  
        // individual items with each group.  
        foreach (var g in groupQuery)  
        {  
            // Create the new file name.  
            string fileName = @"../../../testFile_" + g.Key + ".txt";  
  
            // Output to display.  
            Console.WriteLine(g.Key);  
  
            // Write file.  
            using (System.IO.StreamWriter sw = new System.IO.StreamWriter(fileName))  
            {  
                foreach (var item in g)  
                {  
                    sw.WriteLine(item);  
                    // Output to console for example purposes.  
                    Console.WriteLine("   {0}", item);  
                }  
            }  
        }  
        // Keep console window open in debug mode.  
        Console.WriteLine("Files have been written. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:   
    A  
       Aw, Kam Foo  
    B  
       Bankov, Peter  
       Beebe, Ann  
    E  
       El Yassir, Mehdi  
    G  
       Garcia, Hugo  
       Guy, Wey Yuan  
       Garcia, Debra  
       Gilchrist, Beth  
       Giakoumakis, Leo  
    H  
       Holm, Michael  
    L  
       Liu, Jinghao  
    M  
       Myrcha, Jacek  
       McLin, Nkenge  
    N  
       Noriega, Fabricio  
    P  
       Potra, Cristina  
    T  
       Toyoshima, Tim  
 */  
```  
  
 <span data-ttu-id="ef94a-108">此程式會在與資料檔相同的資料夾中，寫入每個群組的個別檔案。</span><span class="sxs-lookup"><span data-stu-id="ef94a-108">The program writes a separate file for each group in the same folder as the data files.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef94a-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ef94a-109">Compiling the Code</span></span>

<span data-ttu-id="ef94a-110">建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef94a-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ef94a-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="ef94a-111">See also</span></span>

- [<span data-ttu-id="ef94a-112">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="ef94a-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="ef94a-113">LINQ 和檔案目錄 (C#)</span><span class="sxs-lookup"><span data-stu-id="ef94a-113">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
