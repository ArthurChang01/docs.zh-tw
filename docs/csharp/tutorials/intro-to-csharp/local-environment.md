---
title: C# 簡介 - 熟悉開發工具
description: 此文章提供您將用來在電腦上開發 C# 與 .NET 應用程式的工具基本簡介。
ms.date: 10/23/2018
ms.openlocfilehash: 0b1df9e733eef92b1eeb0a7f3ba3ba49602f219d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156567"
---
# <a name="become-familiar-with-the-net-development-tools"></a><span data-ttu-id="5b5cb-103">熟悉 .NET 開發工具</span><span class="sxs-lookup"><span data-stu-id="5b5cb-103">Become familiar with the .NET development tools</span></span>

<span data-ttu-id="5b5cb-104">在電腦上執行教學課程的第一步是設定開發環境。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-104">The first step in running a tutorial on your machine is to set up a development environment.</span></span>
<span data-ttu-id="5b5cb-105">.NET 教程[Hello World 在 10 分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)提供了在 Windows、Linux 或 macOS 上設置本地開發環境的說明。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span>

<span data-ttu-id="5b5cb-106">或者，您可以安裝 [.NET Core SDK](https://dotnet.microsoft.com/download) \(英文\) 和 [Visual Studio Code](https://code.visualstudio.com/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-106">Alternatively, you can install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="5b5cb-107">基本應用程式開發流程</span><span class="sxs-lookup"><span data-stu-id="5b5cb-107">Basic application development flow</span></span>

<span data-ttu-id="5b5cb-108">您將使用 命令[`dotnet new`](../../../core/tools/dotnet-new.md)創建應用程式。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-108">You'll create applications using the [`dotnet new`](../../../core/tools/dotnet-new.md) command.</span></span> <span data-ttu-id="5b5cb-109">此命令會產生應用程式所需的檔案和資產。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-109">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="5b5cb-110">C# 教學課程簡介都是使用 `console` 應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-110">The introduction to C# tutorials all use the `console` application type.</span></span> <span data-ttu-id="5b5cb-111">一旦您掌握基本概念，就可以擴展到其他應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-111">Once you've got the basics, you can expand to other application types.</span></span>

<span data-ttu-id="5b5cb-112">您將使用的其他命令是[`dotnet build`](../../../core/tools/dotnet-build.md)生成可執行檔並[`dotnet run`](../../../core/tools/dotnet-run.md)運行可執行檔。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-112">The other commands you'll use are [`dotnet build`](../../../core/tools/dotnet-build.md) to build the executable, and [`dotnet run`](../../../core/tools/dotnet-run.md) to run the executable.</span></span>

## <a name="pick-your-tutorial"></a><span data-ttu-id="5b5cb-113">挑選教學課程</span><span class="sxs-lookup"><span data-stu-id="5b5cb-113">Pick your tutorial</span></span>

<span data-ttu-id="5b5cb-114">您可以從下列任何一個教學課程開始：</span><span class="sxs-lookup"><span data-stu-id="5b5cb-114">You can start with any of the following tutorials:</span></span>

## <a name="numbers-in-c"></a>[<span data-ttu-id="5b5cb-115">C# 中的數字</span><span class="sxs-lookup"><span data-stu-id="5b5cb-115">Numbers in C#</span></span>](numbers-in-csharp-local.md)

<span data-ttu-id="5b5cb-116">在 [C# 中的數字](numbers-in-csharp-local.md)教學課程中，您將會學習電腦儲存數字的方式，以及如何使用不同的數值型別來執行計算。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-116">In the [Numbers in C#](numbers-in-csharp-local.md) tutorial, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="5b5cb-117">您將會學習進位的基本概念，以及如何使用 C# 執行數學計算。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-117">You'll learn the basics of rounding and how to perform mathematical calculations using C#.</span></span>

<span data-ttu-id="5b5cb-118">此教學課程假設您已完成 [Hello World](hello-world.yml) 課程。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-118">This tutorial assumes that you have finished the [Hello world](hello-world.yml) lesson.</span></span>

## <a name="branches-and-loops"></a>[<span data-ttu-id="5b5cb-119">分支和迴圈</span><span class="sxs-lookup"><span data-stu-id="5b5cb-119">Branches and loops</span></span>](branches-and-loops-local.md)

<span data-ttu-id="5b5cb-120">[分支和迴圈](branches-and-loops-local.md)教學課程會指導您如何根據儲存在變數中的值選取不同程式碼執行路徑的基本概念。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-120">The [Branches and loops](branches-and-loops-local.md) tutorial teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="5b5cb-121">您將會學習控制流程的基本概念，也就是程式做出決定並選擇不同動作的基礎機制。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-121">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span>

<span data-ttu-id="5b5cb-122">此教學課程假設您已完成 [Hello World](hello-world.yml) 與 [C# 中的數字](numbers-in-csharp-local.md)課程。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-122">This tutorial assumes that you have finished the [Hello world](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collection"></a>[<span data-ttu-id="5b5cb-123">清單集合</span><span class="sxs-lookup"><span data-stu-id="5b5cb-123">List collection</span></span>](arrays-and-collections.md)

<span data-ttu-id="5b5cb-124">[List 集合](arrays-and-collections.md)課程會為您說明可儲存資料序列的「List 集合」類型。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-124">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="5b5cb-125">您將會學習如何新增及移除項目、搜尋項目，以及對清單進行排序。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-125">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="5b5cb-126">您會探索各種不同的清單。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-126">You'll explore different kinds of lists.</span></span>

<span data-ttu-id="5b5cb-127">此教學課程假設您已完成上述課程。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-127">This tutorial assumes that you have finished the lessons listed above.</span></span>

## <a name="introduction-to-classes"></a>[<span data-ttu-id="5b5cb-128">類別簡介</span><span class="sxs-lookup"><span data-stu-id="5b5cb-128">Introduction to classes</span></span>](introduction-to-classes.md)

<span data-ttu-id="5b5cb-129">這個最後的 C# 教學課程簡介只能使用您自己的本機開發環境與 .NET Core 在您的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-129">This final introduction to C# tutorial is only available to run on your machine, using your own local development environment and .NET Core.</span></span>
<span data-ttu-id="5b5cb-130">您會建置一個主控台應用程式，並了解 C# 語言的基本物件導向功能。</span><span class="sxs-lookup"><span data-stu-id="5b5cb-130">You'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>
