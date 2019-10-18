---
title: .NET Core 使用者入門
description: 尋找資源以了解如何在 Windows、Linux 和 macOS 上建置 .NET Core 應用程式。
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 9dbc3ebc8d43fe2570a90f4e10fd155a5b114351
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521634"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="d0f68-103">.NET Core 使用者入門</span><span class="sxs-lookup"><span data-stu-id="d0f68-103">Get started with .NET Core</span></span>

<span data-ttu-id="d0f68-104">本文提供 .NET Core 使用者入門的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d0f68-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="d0f68-105">.NET Core 可以安裝在 Windows、Linux 和 macOS 上。</span><span class="sxs-lookup"><span data-stu-id="d0f68-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="d0f68-106">您可以在慣用的文字編輯器中撰寫程式碼，然後產生跨平台的程式庫和應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0f68-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="d0f68-107">如果您不確定 .NET Core 為何，或不確定它與其他 .NET 技術的關聯，請從 [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) (什麼是 .NET) 概觀開始。</span><span class="sxs-lookup"><span data-stu-id="d0f68-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="d0f68-108">簡單來說，.NET Core 是 .NET 的開放原始碼跨平台實作。</span><span class="sxs-lookup"><span data-stu-id="d0f68-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="d0f68-109">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="d0f68-109">Create an application</span></span>

<span data-ttu-id="d0f68-110">首先，在您的電腦上下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="d0f68-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="d0f68-111">接下來，開啟終端機，例如 **PowerShell**、**命令提示字元**或 **bash**。</span><span class="sxs-lookup"><span data-stu-id="d0f68-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="d0f68-112">輸入下列 `dotnet` 命令來建立和執行C#應用程式：</span><span class="sxs-lookup"><span data-stu-id="d0f68-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="d0f68-113">您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d0f68-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="d0f68-114">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="d0f68-114">Congratulations!</span></span> <span data-ttu-id="d0f68-115">您已建立簡單的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0f68-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="d0f68-116">您也可以使用 [Visual Studio Code](tutorials/with-visual-studio-code.md)、[Visual Studio](tutorials/with-visual-studio.md) (僅限 Windows) 或 [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (僅限 macOS) 建立 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0f68-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="d0f68-117">教學課程</span><span class="sxs-lookup"><span data-stu-id="d0f68-117">Tutorials</span></span>

<span data-ttu-id="d0f68-118">遵循這些逐步教學課程就可以開始開發 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0f68-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="d0f68-119">Windows</span><span class="sxs-lookup"><span data-stu-id="d0f68-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="d0f68-120">在 Visual Studio 2017 中使用 .NET Core 建置 C# "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0f68-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="d0f68-121">在 Visual Studio 2017 中使用 .NET Core 建置 C# 類別庫。</span><span class="sxs-lookup"><span data-stu-id="d0f68-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="d0f68-122">在 Visual Studio 2017 中使用 .NET Core 建置 Visual Basic "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0f68-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)
- [<span data-ttu-id="d0f68-123">在 Visual Studio 2017 中使用 Visual Basic 和 .NET Core 建置類別庫。</span><span class="sxs-lookup"><span data-stu-id="d0f68-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  
- <span data-ttu-id="d0f68-124">觀看影片以了解[如何安裝及使用 Visual Studio Code 和 .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/)。</span><span class="sxs-lookup"><span data-stu-id="d0f68-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>
- <span data-ttu-id="d0f68-125">觀看影片以了解[如何安裝及使用 Visual Studio 2017 和 .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/)。</span><span class="sxs-lookup"><span data-stu-id="d0f68-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>
- [<span data-ttu-id="d0f68-126">使用命令列開始使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d0f68-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

<span data-ttu-id="d0f68-127">如需支援的 Windows 版本清單，請參閱 [Windows 開發的必要條件](windows-prerequisites.md)一文。</span><span class="sxs-lookup"><span data-stu-id="d0f68-127">See the [Prerequisites for Windows development](windows-prerequisites.md) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="d0f68-128">Linux</span><span class="sxs-lookup"><span data-stu-id="d0f68-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="d0f68-129">依照下列逐步教學課程，您可以開始開發 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="d0f68-129">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="d0f68-130">使用命令列開始使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d0f68-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)
- <span data-ttu-id="d0f68-131">觀看影片以了解[使用 C# 和 .NET Core 在 Ubuntu 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)。</span><span class="sxs-lookup"><span data-stu-id="d0f68-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="d0f68-132">如需支援的 Linux 發行和版本清單，請參閱 [Linux 開發的必要條件](linux-prerequisites.md)一文。</span><span class="sxs-lookup"><span data-stu-id="d0f68-132">See the [Prerequisites for Linux development](linux-prerequisites.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="d0f68-133">macOS</span><span class="sxs-lookup"><span data-stu-id="d0f68-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="d0f68-134">依照下列逐步教學課程，您可以開始開發 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="d0f68-134">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- <span data-ttu-id="d0f68-135">觀看影片以了解[使用 C# 和 .NET Core 在 macOS 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)。</span><span class="sxs-lookup"><span data-stu-id="d0f68-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>
- [<span data-ttu-id="d0f68-136">使用 Visual Studio Code 在 macOS 上開始使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d0f68-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)
- [<span data-ttu-id="d0f68-137">使用命令列開始使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d0f68-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)
- [<span data-ttu-id="d0f68-138">使用 Visual Studio for Mac 在 macOS 上開始使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d0f68-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="d0f68-139">使用 Visual Studio for Mac 在 macOS 上建置完整的 .NET Core 方案。</span><span class="sxs-lookup"><span data-stu-id="d0f68-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="d0f68-140">如需支援的 OS X/macOS 版本清單，請參閱 [macOS 開發的必要條件](macos-prerequisites.md)一文。</span><span class="sxs-lookup"><span data-stu-id="d0f68-140">See the [Prerequisites for macOS development](macos-prerequisites.md) article for a list of the supported OS X / macOS versions.</span></span>

---
