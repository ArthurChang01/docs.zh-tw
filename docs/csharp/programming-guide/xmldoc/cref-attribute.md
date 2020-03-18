---
title: cref 屬性 - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: b06d0c9d447124dec7d8cf3c0cbbfd0daca78fe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157009"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="35edd-102">cref 屬性（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="35edd-102">cref attribute (C# programming guide)</span></span>

<span data-ttu-id="35edd-103">`cref` 屬性在 XML 文件標記中表示「程式碼參考」。</span><span class="sxs-lookup"><span data-stu-id="35edd-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="35edd-104">它會指定標記的內部文字是程式碼項目，例如類型、方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="35edd-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="35edd-105">[DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類文件工具使用 `cref` 屬性自動產生記錄類型或成員的頁面超連結。</span><span class="sxs-lookup"><span data-stu-id="35edd-105">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>

## <a name="example"></a><span data-ttu-id="35edd-106">範例</span><span class="sxs-lookup"><span data-stu-id="35edd-106">Example</span></span>

<span data-ttu-id="35edd-107">下面的示例顯示了`cref`請參閱[\<>](./see.md)標記中使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="35edd-107">The following example shows `cref` attributes used in [\<see>](./see.md) tags.</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

<span data-ttu-id="35edd-108">編譯時，此程式會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="35edd-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="35edd-109">請注意，以 `GetZero` 方法的 `cref` 屬性為例，已被編譯器轉換成 `"M:TestNamespace.TestClass.GetZero"`。</span><span class="sxs-lookup"><span data-stu-id="35edd-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="35edd-110">"M:" 前置詞表示「方法」，而且是能為 DocFX 和 Sandcastle 這類文件工具識別的慣例。</span><span class="sxs-lookup"><span data-stu-id="35edd-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="35edd-111">如需前置詞的完整清單，請參閱[處理 XML 檔案](./processing-the-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="35edd-111">For a complete list of prefixes, see [Processing the XML File](./processing-the-xml-file.md).</span></span>

```xml  
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:TestNamespace.TestClass">
            <summary>
            TestClass contains several cref examples.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor">
            <summary>
            This sample shows how to specify the <see cref="T:TestNamespace.TestClass"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor(System.Int32)">
            <summary>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.#ctor(System.Int32)"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.GetZero">
            <summary>
            The GetZero method.
            </summary>
            <example>
            This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.
            <code>
            class TestClass
            {
                static int Main()
                {
                    return GetZero();
                }
            }
            </code>
            </example>
        </member>
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">
            <summary>
            The GetGenericValue method.
            </summary>
            <remarks>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.
            </remarks>
        </member>
        <member name="T:TestNamespace.GenericClass`1">
            <summary>
            GenericClass.
            </summary>
            <remarks>
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.
            </remarks>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="35edd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35edd-112">See also</span></span>

- [<span data-ttu-id="35edd-113">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="35edd-113">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="35edd-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="35edd-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
