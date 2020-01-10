---
title: 使用 XML 註解記錄您的程式碼
description: 了解如何使用 XML 文件註解記錄您的程式碼，並在編譯時期產生 XML 文件檔案。
ms.date: 02/14/2017
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 6aa52030e20f61b26311347a57629658ebe0e609
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713932"
---
# <a name="document-your-code-with-xml-comments"></a><span data-ttu-id="75c05-103">使用 XML 批註記錄您的程式碼</span><span class="sxs-lookup"><span data-stu-id="75c05-103">Document your code with XML comments</span></span>

<span data-ttu-id="75c05-104">XML 文件註解是一種特殊類型的註解，新增於任何使用者定義型別或成員的定義上方。</span><span class="sxs-lookup"><span data-stu-id="75c05-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="75c05-105">XML 文件註解具特殊性，因為編譯器可以處理它們以在編譯時期產生 XML 文件檔案。</span><span class="sxs-lookup"><span data-stu-id="75c05-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="75c05-106">編譯器所產生的 XML 檔案可以隨著 .NET 組件一起散發，因此 Visual Studio 和其他 IDE 可以使用 IntelliSense 來顯示類型或成員的快速資訊。</span><span class="sxs-lookup"><span data-stu-id="75c05-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="75c05-107">此外，可以透過 [DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類工具執行 XML 檔案來產生 API 參考網站。</span><span class="sxs-lookup"><span data-stu-id="75c05-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="75c05-108">編譯器會忽略 XML 文件註解 (例如所有其他註解)。</span><span class="sxs-lookup"><span data-stu-id="75c05-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="75c05-109">您可以執行下列其中一項動作，以在編譯時期產生 XML 檔案︰</span><span class="sxs-lookup"><span data-stu-id="75c05-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="75c05-110">如果您是從命令列使用 .NET Core 開發應用程式，您可以將 `GenerateDocumentationFile` 元素加入 .csproj 專案檔的 `<PropertyGroup>` 區段中。</span><span class="sxs-lookup"><span data-stu-id="75c05-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="75c05-111">您也可以使用[`DocumentationFile` 元素](/visualstudio/msbuild/common-msbuild-project-properties)直接指定檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="75c05-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="75c05-112">下列範例會在根檔案名稱與組件相同的專案目錄中產生 XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="75c05-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```
   
   <span data-ttu-id="75c05-113">這個運算式就相當於下列運算式：</span><span class="sxs-lookup"><span data-stu-id="75c05-113">This is equivalent to the following:</span></span>
   
   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="75c05-114">如果您正在使用 Visual Studio 開發應用程式，請以滑鼠右鍵按一下專案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="75c05-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="75c05-115">在屬性對話方塊中，選取 [建置] 索引標籤，然後檢查 [XML 文件檔案]。</span><span class="sxs-lookup"><span data-stu-id="75c05-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="75c05-116">您也可以變更編譯器寫入檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="75c05-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="75c05-117">如果您要從命令列編譯 .NET Framework 應用程式，請在編譯時新增[-doc 編譯器選項](language-reference/compiler-options/doc-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="75c05-117">If you are compiling a .NET Framework application from the command line, add the [-doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="75c05-118">XML 文件註解使用三個正斜線 (`///`) 和 XML 格式化註解主體。</span><span class="sxs-lookup"><span data-stu-id="75c05-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="75c05-119">例如：</span><span class="sxs-lookup"><span data-stu-id="75c05-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="75c05-120">逐步解說</span><span class="sxs-lookup"><span data-stu-id="75c05-120">Walkthrough</span></span>

<span data-ttu-id="75c05-121">讓我們逐步解說記錄非常基本的數學程式庫，讓新的開發人員可以輕鬆地瞭解/參與，並讓協力廠商開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="75c05-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third-party developers to use.</span></span>

<span data-ttu-id="75c05-122">以下是簡單數學程式庫的程式碼︰</span><span class="sxs-lookup"><span data-stu-id="75c05-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="75c05-123">範例程式庫支援 `int` 和 `double` 資料型別上的四個主要算術運算 `add`、`subtract`、`multiply` 和 `divide`。</span><span class="sxs-lookup"><span data-stu-id="75c05-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="75c05-124">現在您想要能夠使用您的程式庫但無法存取原始程式碼的協力廠商開發人員，從您的程式碼建立 API 參考檔。</span><span class="sxs-lookup"><span data-stu-id="75c05-124">Now you want to be able to create an API reference document from your code for third-party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="75c05-125">如先前所述，XML 文件標籤可以用來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="75c05-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="75c05-126">現在將向您介紹 C# 編譯器支援的標準 XML 標籤。</span><span class="sxs-lookup"><span data-stu-id="75c05-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## <a name="summary"></a><span data-ttu-id="75c05-127">\<summary></span><span class="sxs-lookup"><span data-stu-id="75c05-127">\<summary></span></span>

<span data-ttu-id="75c05-128">`<summary>` 標記會新增類型或成員的簡短資訊。</span><span class="sxs-lookup"><span data-stu-id="75c05-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="75c05-129">我會將它新增至 `Math` 類別定義和第一個 `Add` 方法來示範其使用方式。</span><span class="sxs-lookup"><span data-stu-id="75c05-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="75c05-130">請自由套用至您程式碼的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="75c05-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="75c05-131">`<summary>` 標記十分重要，因為它的內容是 IntelliSense 或 API 參考文件中類型或成員資訊的主要來源，所以建議您包含它。</span><span class="sxs-lookup"><span data-stu-id="75c05-131">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## <a name="remarks"></a><span data-ttu-id="75c05-132">\<remarks></span><span class="sxs-lookup"><span data-stu-id="75c05-132">\<remarks></span></span>

<span data-ttu-id="75c05-133">`<remarks>` 標記會補充 `<summary>` 標記所提供的類型或成員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="75c05-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="75c05-134">在此範例中，您只會將它新增至類別。</span><span class="sxs-lookup"><span data-stu-id="75c05-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a><span data-ttu-id="75c05-135">\<returns></span><span class="sxs-lookup"><span data-stu-id="75c05-135">\<returns></span></span>

<span data-ttu-id="75c05-136">`<returns>` 標記描述方法宣告的傳回值。</span><span class="sxs-lookup"><span data-stu-id="75c05-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="75c05-137">如前所示，下列範例說明第一個 `Add` 方法的 `<returns>` 標記。</span><span class="sxs-lookup"><span data-stu-id="75c05-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="75c05-138">您可以對其他方法執行相同作業。</span><span class="sxs-lookup"><span data-stu-id="75c05-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a><span data-ttu-id="75c05-139">\<值></span><span class="sxs-lookup"><span data-stu-id="75c05-139">\<value></span></span>

<span data-ttu-id="75c05-140">`<value>` 標記類似於 `<returns>` 標記，但將它用作屬性除外。</span><span class="sxs-lookup"><span data-stu-id="75c05-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="75c05-141">假設 `Math` 程式庫的靜態屬性稱為 `PI`，以下是使用這個標記的方式：</span><span class="sxs-lookup"><span data-stu-id="75c05-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a><span data-ttu-id="75c05-142">\<example></span><span class="sxs-lookup"><span data-stu-id="75c05-142">\<example></span></span>

<span data-ttu-id="75c05-143">您可以使用 `<example>` 標記，以在 XML 文件中包括範例。</span><span class="sxs-lookup"><span data-stu-id="75c05-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="75c05-144">這包含如何使用子 `<code>` 標記。</span><span class="sxs-lookup"><span data-stu-id="75c05-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="75c05-145">`code` 標記會保留分行符號以及較長範例的縮排。</span><span class="sxs-lookup"><span data-stu-id="75c05-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## <a name="para"></a><span data-ttu-id="75c05-146">\<para></span><span class="sxs-lookup"><span data-stu-id="75c05-146">\<para></span></span>

<span data-ttu-id="75c05-147">您可以使用 `<para>` 標記來格式化其父標記內的內容。</span><span class="sxs-lookup"><span data-stu-id="75c05-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="75c05-148">`<para>` 通常用於標記內 (例如 `<remarks>` 或 `<returns>`)，以將文字分成數個段落。</span><span class="sxs-lookup"><span data-stu-id="75c05-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="75c05-149">您可以格式化類別定義的 `<remarks>` 標記內容。</span><span class="sxs-lookup"><span data-stu-id="75c05-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a><span data-ttu-id="75c05-150">\<c></span><span class="sxs-lookup"><span data-stu-id="75c05-150">\<c></span></span>

<span data-ttu-id="75c05-151">仍然，在有關格式化的主題，您可以使用 `<c>` 標記將一部分文字標記為程式碼。</span><span class="sxs-lookup"><span data-stu-id="75c05-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="75c05-152">它就像 `<code>` 標記，只是會內嵌。</span><span class="sxs-lookup"><span data-stu-id="75c05-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="75c05-153">這適用於您想要將快速程式碼範例顯示為標記內容的一部分時。</span><span class="sxs-lookup"><span data-stu-id="75c05-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="75c05-154">請更新 `Math` 類別的文件。</span><span class="sxs-lookup"><span data-stu-id="75c05-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a><span data-ttu-id="75c05-155">\<exception></span><span class="sxs-lookup"><span data-stu-id="75c05-155">\<exception></span></span>

<span data-ttu-id="75c05-156">使用 `<exception>` 標記，讓您的開發人員知道方法可以擲回特定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="75c05-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="75c05-157">查看 `Math` 程式庫，即可看到兩個 `Add` 方法在符合特定條件時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="75c05-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="75c05-158">雖然不明顯，但如果 `b` 參數為零，則也會擲回整數 `Divide` 方法。</span><span class="sxs-lookup"><span data-stu-id="75c05-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="75c05-159">現在將例外狀況文件新增至這個方法。</span><span class="sxs-lookup"><span data-stu-id="75c05-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="75c05-160">`cref` 屬性代表可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="75c05-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="75c05-161">這可以是專案或已參考組件中所定義的任何類型。</span><span class="sxs-lookup"><span data-stu-id="75c05-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="75c05-162">如果無法解析其值，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="75c05-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

## <a name="see"></a><span data-ttu-id="75c05-163">\<see></span><span class="sxs-lookup"><span data-stu-id="75c05-163">\<see></span></span>

<span data-ttu-id="75c05-164">`<see>` 標記可讓您建立另一個程式碼項目之文件頁面的可按式連結。</span><span class="sxs-lookup"><span data-stu-id="75c05-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="75c05-165">在下一個範例中，我們將在兩個 `Add` 方法之間建立可按式連結。</span><span class="sxs-lookup"><span data-stu-id="75c05-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="75c05-166">`cref` 為**必要**屬性，代表可從目前編譯環境取得的類型或其成員的參考。</span><span class="sxs-lookup"><span data-stu-id="75c05-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="75c05-167">這可以是專案或已參考組件中所定義的任何類型。</span><span class="sxs-lookup"><span data-stu-id="75c05-167">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="seealso"></a><span data-ttu-id="75c05-168">\<seealso></span><span class="sxs-lookup"><span data-stu-id="75c05-168">\<seealso></span></span>

<span data-ttu-id="75c05-169">`<seealso>` 標記的使用方式與 `<see>` 標記的使用方式相同。</span><span class="sxs-lookup"><span data-stu-id="75c05-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="75c05-170">唯一的差異在於它的內容一般會放在＜另請參閱＞一節中。</span><span class="sxs-lookup"><span data-stu-id="75c05-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="75c05-171">在這裡，我們將在整數 `Add` 方法上新增 `seealso` 標記，以參考類別中接受整數參數的其他方法：</span><span class="sxs-lookup"><span data-stu-id="75c05-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="75c05-172">`cref` 屬性代表可從目前編譯環境取得的類型或其成員的參考。</span><span class="sxs-lookup"><span data-stu-id="75c05-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="75c05-173">這可以是專案或已參考組件中所定義的任何類型。</span><span class="sxs-lookup"><span data-stu-id="75c05-173">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="param"></a><span data-ttu-id="75c05-174">\<param></span><span class="sxs-lookup"><span data-stu-id="75c05-174">\<param></span></span>

<span data-ttu-id="75c05-175">您可以使用 `<param>` 標記來描述方法的參數。</span><span class="sxs-lookup"><span data-stu-id="75c05-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="75c05-176">以下是 double `Add` 方法的範例：標記描述的參數是在**必要**的 `name` 屬性中指定。</span><span class="sxs-lookup"><span data-stu-id="75c05-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a><span data-ttu-id="75c05-177">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="75c05-177">\<typeparam></span></span>

<span data-ttu-id="75c05-178">您可以就像使用 `<param>` 標記一樣地使用 `<typeparam>` 標記，但針對泛型型別或方法宣告來描述泛型參數。</span><span class="sxs-lookup"><span data-stu-id="75c05-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="75c05-179">請將快速泛型方法新增至 `Math` 類別，以檢查其中一個數量是否大於另一個數量。</span><span class="sxs-lookup"><span data-stu-id="75c05-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a><span data-ttu-id="75c05-180">\<paramref></span><span class="sxs-lookup"><span data-stu-id="75c05-180">\<paramref></span></span>

<span data-ttu-id="75c05-181">您有時可能正在描述方法在 `<summary>` 標記中所執行的作業，而且您可能會想要參考參數。</span><span class="sxs-lookup"><span data-stu-id="75c05-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="75c05-182">則 `<paramref>` 標記最適合這麼做。</span><span class="sxs-lookup"><span data-stu-id="75c05-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="75c05-183">讓我們更新雙 `Add` 方法的摘要。</span><span class="sxs-lookup"><span data-stu-id="75c05-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="75c05-184">如同 `<param>` 標記，參數名稱是在**必要**的 `name` 屬性中指定。</span><span class="sxs-lookup"><span data-stu-id="75c05-184">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a><span data-ttu-id="75c05-185">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="75c05-185">\<typeparamref></span></span>

<span data-ttu-id="75c05-186">您可以就像使用 `<paramref>` 標記一樣地使用 `<typeparamref>` 標記，但針對泛型型別或方法宣告來描述泛型參數。</span><span class="sxs-lookup"><span data-stu-id="75c05-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="75c05-187">您可以使用先前建立的相同泛型方法。</span><span class="sxs-lookup"><span data-stu-id="75c05-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a><span data-ttu-id="75c05-188">\<list></span><span class="sxs-lookup"><span data-stu-id="75c05-188">\<list></span></span>

<span data-ttu-id="75c05-189">您可以使用 `<list>` 標記，將文件資訊格式化為已排序清單、未排序清單或資料表。</span><span class="sxs-lookup"><span data-stu-id="75c05-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="75c05-190">建立 `Math` 程式庫所支援的未排序數學運算清單。</span><span class="sxs-lookup"><span data-stu-id="75c05-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="75c05-191">您可以分別將 `type` 屬性變更為 `number` 或 `table`，以建立排序過的清單或表格。</span><span class="sxs-lookup"><span data-stu-id="75c05-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="put-it-all-together"></a><span data-ttu-id="75c05-192">組合在一起</span><span class="sxs-lookup"><span data-stu-id="75c05-192">Put it all together</span></span>

<span data-ttu-id="75c05-193">如已遵循本教學課程，並已在必要時將標記套用至程式碼，則程式碼現在看起來應該如下︰</span><span class="sxs-lookup"><span data-stu-id="75c05-193">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="75c05-194">從程式碼中，您可以產生使用可按式交互參照完成的詳細文件網站。</span><span class="sxs-lookup"><span data-stu-id="75c05-194">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="75c05-195">但您會面臨另一個問題︰您的程式碼變得難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="75c05-195">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="75c05-196">因為有太多資訊需要仔細檢查，這會是想要參與這個程式碼之開發人員的夢魘。</span><span class="sxs-lookup"><span data-stu-id="75c05-196">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="75c05-197">還好有 XML 標記可協助您處理這個問題︰</span><span class="sxs-lookup"><span data-stu-id="75c05-197">Thankfully there's an XML tag that can help you deal with this:</span></span>

## <a name="include"></a><span data-ttu-id="75c05-198">\<include></span><span class="sxs-lookup"><span data-stu-id="75c05-198">\<include></span></span>

<span data-ttu-id="75c05-199">`<include>` 標記可讓您參考個別 XML 檔案中描述原始程式碼中類型和成員的註解，這與直接在原始程式碼檔中放置文件註解相反。</span><span class="sxs-lookup"><span data-stu-id="75c05-199">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="75c05-200">您現在要將所有 XML 標記移至名為 `docs.xml` 的個別 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="75c05-200">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="75c05-201">請放心以您想要的名稱來命名檔案。</span><span class="sxs-lookup"><span data-stu-id="75c05-201">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="75c05-202">在上述 XML 中，每個成員的文件註解都會直接顯示在執行動作之後所命名的標記內。</span><span class="sxs-lookup"><span data-stu-id="75c05-202">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="75c05-203">您可以選擇自己的策略。</span><span class="sxs-lookup"><span data-stu-id="75c05-203">You can choose your own strategy.</span></span>
<span data-ttu-id="75c05-204">現在，您的 XML 註解位於在不同的檔案中，請查看如何使用 `<include>` 標記讓您的程式碼更容易閱讀：</span><span class="sxs-lookup"><span data-stu-id="75c05-204">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="75c05-205">目前您已經準備好了：我們的程式碼又再次為可讀，而且未遺失文件資訊。</span><span class="sxs-lookup"><span data-stu-id="75c05-205">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="75c05-206">`file` 屬性代表包含文件的 XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="75c05-206">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="75c05-207">`path` 屬性代表存在於所指定 `file` 中之 `tag name` 的 [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) 查詢。</span><span class="sxs-lookup"><span data-stu-id="75c05-207">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="75c05-208">`name` 屬性代表標記中位在註解前面的名稱規範。</span><span class="sxs-lookup"><span data-stu-id="75c05-208">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="75c05-209">可用來取代 `name` 的 `id` 屬性代表位在註解前面之標記的識別碼。</span><span class="sxs-lookup"><span data-stu-id="75c05-209">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="75c05-210">使用者定義的標記</span><span class="sxs-lookup"><span data-stu-id="75c05-210">User-defined tags</span></span>

<span data-ttu-id="75c05-211">以上所述的所有標記都代表 C# 編譯器所辨識的標記。</span><span class="sxs-lookup"><span data-stu-id="75c05-211">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="75c05-212">不過，使用者可以定義自己的標記。</span><span class="sxs-lookup"><span data-stu-id="75c05-212">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="75c05-213">Sandcastle 這類之類的工具可支援額外的標記，例如[\<事件 >](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm)和[\<附注 >](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm)，甚至支援[記錄命名空間](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm)。</span><span class="sxs-lookup"><span data-stu-id="75c05-213">Tools like Sandcastle bring support for extra tags like [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) and [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="75c05-214">自訂或內部文件產生工具也可以與標準標記搭配使用，而且可以支援從 HTML 到 PDF 的多個輸出格式。</span><span class="sxs-lookup"><span data-stu-id="75c05-214">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="75c05-215">建議</span><span class="sxs-lookup"><span data-stu-id="75c05-215">Recommendations</span></span>

<span data-ttu-id="75c05-216">有許多原因，建議您記錄程式碼。</span><span class="sxs-lookup"><span data-stu-id="75c05-216">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="75c05-217">接下來是一些最佳做法、一般使用案例，以及在 C# 程式碼中使用 XML 文件標記時應該知道的事項。</span><span class="sxs-lookup"><span data-stu-id="75c05-217">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="75c05-218">為保持一致性，應該記錄所有公開可見的類型和其成員。</span><span class="sxs-lookup"><span data-stu-id="75c05-218">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="75c05-219">如果您必須執行它，則請執行。</span><span class="sxs-lookup"><span data-stu-id="75c05-219">If you must do it, do it all.</span></span>
- <span data-ttu-id="75c05-220">也可以使用 XML 註解記錄私用成員。</span><span class="sxs-lookup"><span data-stu-id="75c05-220">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="75c05-221">不過，這樣會公開您程式庫的內部 (可能是機密) 運作。</span><span class="sxs-lookup"><span data-stu-id="75c05-221">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="75c05-222">類型和其成員最少應該具有 `<summary>` 標記，因為 IntelliSense 需要其內容。</span><span class="sxs-lookup"><span data-stu-id="75c05-222">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="75c05-223">應該使用結尾為句號的完整句子來撰寫文件文字。</span><span class="sxs-lookup"><span data-stu-id="75c05-223">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="75c05-224">完全支援部分類別，而且文件資訊將會串連為該類型的單一項目。</span><span class="sxs-lookup"><span data-stu-id="75c05-224">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="75c05-225">編譯器會驗證 `<exception>`、`<include>`、`<param>`、`<see>`、`<seealso>`和 `<typeparam>` 標記的語法。</span><span class="sxs-lookup"><span data-stu-id="75c05-225">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`, and `<typeparam>` tags.</span></span>
- <span data-ttu-id="75c05-226">編譯器會驗證包含程式碼其他部分的檔案路徑和參考的參數。</span><span class="sxs-lookup"><span data-stu-id="75c05-226">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="75c05-227">請參閱</span><span class="sxs-lookup"><span data-stu-id="75c05-227">See also</span></span>

- [<span data-ttu-id="75c05-228">XML 文件註解 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="75c05-228">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="75c05-229">建議使用的文件註解標記 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="75c05-229">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
