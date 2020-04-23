---
title: 如何：建立 .NET Framework 單一檔案元件
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: b7cb06da74a21dab6f60f0d4c3ac1748fcbe4526
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644307"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="f286e-102">如何：建立 .NET Framework 單一檔案元件</span><span class="sxs-lookup"><span data-stu-id="f286e-102">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="f286e-103">單一檔案組件，是最簡單的組件類型，包含類型資訊和實作，以及[組件資訊清單](../../standard/assembly/manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="f286e-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="f286e-104">您可以使用命令列編譯器或 Visual Studio 來建立以 .NET Framework 為目標的單一檔案元件。</span><span class="sxs-lookup"><span data-stu-id="f286e-104">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="f286e-105">根據預設，編譯器會建立副檔名為 *.exe*的元件檔。</span><span class="sxs-lookup"><span data-stu-id="f286e-105">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="f286e-106">Visual Studio for C# 和 Visual Basic 只能用於建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="f286e-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="f286e-107">如果想建立多檔案組件，您必須使用命令列編譯器或 Visual C++。</span><span class="sxs-lookup"><span data-stu-id="f286e-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="f286e-108">下列程序示範如何使用命令列編譯器建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="f286e-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="f286e-109">建立具有 .exe 副檔名的元件</span><span class="sxs-lookup"><span data-stu-id="f286e-109">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="f286e-110">在命令提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="f286e-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="f286e-111">\<*編譯器命令*> \<*模組名稱*></span><span class="sxs-lookup"><span data-stu-id="f286e-111">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="f286e-112">在這個命令中，「編譯器命令」\*\* 是您程式碼模組所用語言的編譯器命令，而「模組名稱」\*\* 則是編譯至組件的程式碼模組名稱。</span><span class="sxs-lookup"><span data-stu-id="f286e-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="f286e-113">下列範例會從名`myCode`為的程式碼模組建立名為*myCode*的元件。</span><span class="sxs-lookup"><span data-stu-id="f286e-113">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="f286e-114">建立副檔名為 .exe 的元件，並指定輸出檔名稱</span><span class="sxs-lookup"><span data-stu-id="f286e-114">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="f286e-115">在命令提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="f286e-115">At the command prompt, type the following command:</span></span>

<span data-ttu-id="f286e-116">\<*編譯器命令*> **/out：**\<*file name*> 檔案名\<*模組名稱*></span><span class="sxs-lookup"><span data-stu-id="f286e-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="f286e-117">在這個命令中，「編譯器命令」\*\* 是您程式碼模組所用語言的編譯器命令、「檔案名稱」\*\* 是輸出檔名稱，而「模組名稱」\*\* 則是編譯至組件的程式碼模組名稱。</span><span class="sxs-lookup"><span data-stu-id="f286e-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="f286e-118">下列範例會從名`myCode`為的程式碼模組建立名為*myAssembly*的元件。</span><span class="sxs-lookup"><span data-stu-id="f286e-118">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="f286e-119">建立程式庫元件</span><span class="sxs-lookup"><span data-stu-id="f286e-119">Create library assemblies</span></span>
 <span data-ttu-id="f286e-120">程式庫組件類似類別庫。</span><span class="sxs-lookup"><span data-stu-id="f286e-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="f286e-121">它包含其他組件會參考的類型，但沒有可開始執行的進入點。</span><span class="sxs-lookup"><span data-stu-id="f286e-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="f286e-122">若要建立程式庫元件，請在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="f286e-122">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="f286e-123">\<*編譯器命令*> **-t:library** \<*模組名稱*></span><span class="sxs-lookup"><span data-stu-id="f286e-123">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="f286e-124">在這個命令中，「編譯器命令」\*\* 是您程式碼模組所用語言的編譯器命令，而「模組名稱」\*\* 則是編譯至組件的程式碼模組名稱。</span><span class="sxs-lookup"><span data-stu-id="f286e-124">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="f286e-125">您也可以使用其他編譯器選項，例如 **out:** 選項。</span><span class="sxs-lookup"><span data-stu-id="f286e-125">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="f286e-126">下列範例會從名`myCode`為的程式碼模組建立名為 myCodeAssembly 的*連結*庫元件。</span><span class="sxs-lookup"><span data-stu-id="f286e-126">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="f286e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f286e-127">See also</span></span>

- [<span data-ttu-id="f286e-128">建立組件</span><span class="sxs-lookup"><span data-stu-id="f286e-128">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="f286e-129">多檔案組件</span><span class="sxs-lookup"><span data-stu-id="f286e-129">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="f286e-130">如何：建立多檔案元件</span><span class="sxs-lookup"><span data-stu-id="f286e-130">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="f286e-131">具有組件的程式</span><span class="sxs-lookup"><span data-stu-id="f286e-131">Program with assemblies</span></span>](../../standard/assembly/index.md)
