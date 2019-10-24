---
title: C#證明
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 4fed33272dbed50100a37aa9fcd30befc46435f9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771831"
---
# <a name="c-reference"></a><span data-ttu-id="a6331-102">C#證明</span><span class="sxs-lookup"><span data-stu-id="a6331-102">C# reference</span></span>

<span data-ttu-id="a6331-103">本節提供有關 C# 關鍵字、運算子、特殊字元、前置處理器指示詞、編譯器選項以及編譯器錯誤和警告的參考資料。</span><span class="sxs-lookup"><span data-stu-id="a6331-103">This section provides reference material about C# keywords, operators, special characters, preprocessor directives, compiler options, and compiler errors and warnings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6331-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="a6331-104">In this section</span></span>

 [<span data-ttu-id="a6331-105">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a6331-105">C# Keywords</span></span>](./keywords/index.md)  
 <span data-ttu-id="a6331-106">提供有關 C# 關鍵字和語法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="a6331-106">Provides links to information about C# keywords and syntax.</span></span>  
  
 [<span data-ttu-id="a6331-107">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="a6331-107">C# Operators</span></span>](./operators/index.md)  
 <span data-ttu-id="a6331-108">提供有關 C# 運算子和語法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="a6331-108">Provides links to information about C# operators and syntax.</span></span>  

 [<span data-ttu-id="a6331-109">C# 特殊字元</span><span class="sxs-lookup"><span data-stu-id="a6331-109">C# Special Characters</span></span>](./tokens/index.md)  
 <span data-ttu-id="a6331-110">提供有關 C# 中特殊內容字元及其使用方式之相關資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="a6331-110">Provides links to information about special contextual characters in C# and their usage.</span></span>  

 [<span data-ttu-id="a6331-111">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="a6331-111">C# Preprocessor Directives</span></span>](./preprocessor-directives/index.md)  
 <span data-ttu-id="a6331-112">提供有關 C# 原始程式碼內嵌之編譯器命令的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="a6331-112">Provides links to information about compiler commands for embedding in C# source code.</span></span>  
  
 [<span data-ttu-id="a6331-113">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="a6331-113">C# Compiler Options</span></span>](./compiler-options/index.md)  
 <span data-ttu-id="a6331-114">包含編譯器選項及其使用方式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a6331-114">Includes information about compiler options and how to use them.</span></span>  
  
 [<span data-ttu-id="a6331-115">C# 編譯器錯誤</span><span class="sxs-lookup"><span data-stu-id="a6331-115">C# Compiler Errors</span></span>](./compiler-messages/index.md)  
 <span data-ttu-id="a6331-116">包含示範 C# 編譯器錯誤和警告之原因和修正的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="a6331-116">Includes code snippets that demonstrate the cause and correction of C# compiler errors and warnings.</span></span>  
  
 [<span data-ttu-id="a6331-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a6331-117">C# Language Specification</span></span>](../../../_csharplang/spec/introduction.md)  
 <span data-ttu-id="a6331-118">C# 6.0 語言規格。</span><span class="sxs-lookup"><span data-stu-id="a6331-118">The C# 6.0 language specification.</span></span> <span data-ttu-id="a6331-119">這是 C# 6.0 語言的草稿提案。</span><span class="sxs-lookup"><span data-stu-id="a6331-119">This is a draft proposal for the C# 6.0 language.</span></span> <span data-ttu-id="a6331-120">本檔將透過使用 ECMA C#標準委員會的方式進行精簡。</span><span class="sxs-lookup"><span data-stu-id="a6331-120">This document will be refined through work with the ECMA C# standards committee.</span></span> <span data-ttu-id="a6331-121">版本 5.0 已在 2017年 12 月發行為[標準 ECMA-334 第 5 版](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) \(英文\) 文件。</span><span class="sxs-lookup"><span data-stu-id="a6331-121">Version 5.0 has been released in December 2017 as the [Standard ECMA-334 5th Edition](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) document.</span></span>

<span data-ttu-id="a6331-122">語言規格提案中會說明已在 C# 6.0 之後版本中實作的功能。</span><span class="sxs-lookup"><span data-stu-id="a6331-122">The features that have been implemented in C# versions after 6.0 are represented in language specification proposals.</span></span> <span data-ttu-id="a6331-123">這些文件會描述為了新增這些功能，而產生的語言規格差異。</span><span class="sxs-lookup"><span data-stu-id="a6331-123">These documents describe the deltas to the language spec in order to add these new features.</span></span> <span data-ttu-id="a6331-124">這些都是草稿提案表單。</span><span class="sxs-lookup"><span data-stu-id="a6331-124">These are in draft proposal form.</span></span> <span data-ttu-id="a6331-125">這些規格將會調整並提交給 ECMA 標準委員會，以進行正式審查，並將其合併至未來C#的標準版本。</span><span class="sxs-lookup"><span data-stu-id="a6331-125">These specifications will be refined and submitted to the ECMA standards committee for formal review and incorporation into a future version of the C# Standard.</span></span>

 [<span data-ttu-id="a6331-126">C#7.0 規格提案</span><span class="sxs-lookup"><span data-stu-id="a6331-126">C# 7.0 Specification Proposals</span></span>](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 <span data-ttu-id="a6331-127">C# 7.0 中實作了一些新功能。</span><span class="sxs-lookup"><span data-stu-id="a6331-127">There are a number of new features implemented in C# 7.0.</span></span> <span data-ttu-id="a6331-128">它們包括模式比對、區域函式、out 變數宣告、擲回例外狀況、二進位常值，以及數字分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a6331-128">They include pattern matching, local functions, out variable declarations, throw expressions, binary literals, and digit separators.</span></span> <span data-ttu-id="a6331-129">此資料夾包含這些功能中每個功能的規格。</span><span class="sxs-lookup"><span data-stu-id="a6331-129">This folder contains the specifications for each of those features.</span></span>
  
 [<span data-ttu-id="a6331-130">C#7.1 規格提案</span><span class="sxs-lookup"><span data-stu-id="a6331-130">C# 7.1 Specification Proposals</span></span>](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 <span data-ttu-id="a6331-131">C# 7.1 中有新增的功能。</span><span class="sxs-lookup"><span data-stu-id="a6331-131">There are new features added in C# 7.1.</span></span> <span data-ttu-id="a6331-132">首先，您可以撰寫會傳回 `Task` 或 `Task<int>`的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="a6331-132">First, you can write a `Main` method that returns `Task` or `Task<int>`.</span></span> <span data-ttu-id="a6331-133">這可讓您將 `async` 修飾詞新增到 `Main`。</span><span class="sxs-lookup"><span data-stu-id="a6331-133">This enables you to add the `async` modifier to `Main`.</span></span> <span data-ttu-id="a6331-134">`default` 運算式在能夠推斷類型的位置，可以不搭配類型使用。</span><span class="sxs-lookup"><span data-stu-id="a6331-134">The `default` expression can be used without a type in locations where the type can be inferred.</span></span> <span data-ttu-id="a6331-135">Tuple 成員名稱也可推斷。</span><span class="sxs-lookup"><span data-stu-id="a6331-135">Also, tuple member names can be inferred.</span></span> <span data-ttu-id="a6331-136">最後一點，模式比對可用於泛型。</span><span class="sxs-lookup"><span data-stu-id="a6331-136">Finally, pattern matching can be used with generics.</span></span>

 [<span data-ttu-id="a6331-137">C#7.2 規格提案</span><span class="sxs-lookup"><span data-stu-id="a6331-137">C# 7.2 Specification Proposals</span></span>](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 <span data-ttu-id="a6331-138">C# 7.2 新增了數個次要功能。</span><span class="sxs-lookup"><span data-stu-id="a6331-138">C# 7.2 added a number of small features.</span></span> <span data-ttu-id="a6331-139">您可以使用 `in` 關鍵字隨機參考，以此方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="a6331-139">You can pass arguments by readonly reference using the `in` keyword.</span></span> <span data-ttu-id="a6331-140">為了支援 `Span` 及相關類型的編譯時間安全性，而進行了數項細微的變更。</span><span class="sxs-lookup"><span data-stu-id="a6331-140">There are a number of low-level changes to support compile-time safety for `Span` and related types.</span></span> <span data-ttu-id="a6331-141">在某些情況下，您可在後續引數為位置引數的地方使用具名引數。</span><span class="sxs-lookup"><span data-stu-id="a6331-141">You can use named arguments where later arguments are positional, in some situations.</span></span> <span data-ttu-id="a6331-142">`private protected` 存取修飾詞可讓您指定呼叫者僅限於相同組件中實作的衍生類型。</span><span class="sxs-lookup"><span data-stu-id="a6331-142">The `private protected` access modifier enables you to specify that callers are limited to derived types implemented in the same assembly.</span></span> <span data-ttu-id="a6331-143">`?:` 運算子可以解析成變數的參考。</span><span class="sxs-lookup"><span data-stu-id="a6331-143">The `?:` operator can resolve to a reference to a variable.</span></span> <span data-ttu-id="a6331-144">您也可以使用前置的數字分隔符號來設定十六進位與二進位數字的格式。</span><span class="sxs-lookup"><span data-stu-id="a6331-144">You can also format hexadecimal and binary numbers using a leading digit separator.</span></span>

 [<span data-ttu-id="a6331-145">C#7.3 規格提案</span><span class="sxs-lookup"><span data-stu-id="a6331-145">C# 7.3 Specification Proposals</span></span>](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 <span data-ttu-id="a6331-146">C# 7.3 是另一個包含數項次要更新的小數點版本。</span><span class="sxs-lookup"><span data-stu-id="a6331-146">C# 7.3 is another point release that includes several small updates.</span></span> <span data-ttu-id="a6331-147">您可以在泛型型別參數使用新的限制式。</span><span class="sxs-lookup"><span data-stu-id="a6331-147">You can use new constraints on generic type parameters.</span></span> <span data-ttu-id="a6331-148">另有幾項變更可讓您更輕鬆地使用 `fixed` 欄位，包括使用 [`stackalloc`](./operators/stackalloc.md) 配置。</span><span class="sxs-lookup"><span data-stu-id="a6331-148">Other changes make it easier to work with `fixed` fields, including using [`stackalloc`](./operators/stackalloc.md) allocations.</span></span> <span data-ttu-id="a6331-149">使用 `ref` 關鍵字宣告的區域變數可以重新指派，以參考新的儲存體。</span><span class="sxs-lookup"><span data-stu-id="a6331-149">Local variables declared with the `ref` keyword may be reasssigned to refer to new storage.</span></span> <span data-ttu-id="a6331-150">您可以將屬性放在自動實作的屬性，該屬性以編譯器產生的支援欄位為目標。</span><span class="sxs-lookup"><span data-stu-id="a6331-150">You can place attributes on auto-implemented properties that target the compiler-generated backing field.</span></span> <span data-ttu-id="a6331-151">運算式變數可用於初始設定式。</span><span class="sxs-lookup"><span data-stu-id="a6331-151">Expression variables can be used in initializers.</span></span> <span data-ttu-id="a6331-152">Tuple 可用於比較是否相等 (或不相等)。</span><span class="sxs-lookup"><span data-stu-id="a6331-152">Tuples can be compared for equality (or inequality).</span></span> <span data-ttu-id="a6331-153">多載解析也有幾項功能改進。</span><span class="sxs-lookup"><span data-stu-id="a6331-153">There have also been some improvements to overload resolution.</span></span>
  
 [<span data-ttu-id="a6331-154">C#8.0 規格提案</span><span class="sxs-lookup"><span data-stu-id="a6331-154">C# 8.0 Specification Proposals</span></span>](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 <span data-ttu-id="a6331-155">C#8.0 適用 .NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="a6331-155">C# 8.0 is available with .NET Core 3.0.</span></span> <span data-ttu-id="a6331-156">這些功能包括可為 null 的參考型別、遞迴模式比對、預設介面方法、非同步資料流程、範圍和索引、使用和 using 宣告的模式、null 聯合指派，以及 readonly 實例成員。</span><span class="sxs-lookup"><span data-stu-id="a6331-156">The features include nullable reference types, recursive pattern matching, default interface methods, async streams, ranges and indexes, pattern based using and using declarations, null coalescing assignment, and readonly instance members.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="a6331-157">相關章節</span><span class="sxs-lookup"><span data-stu-id="a6331-157">Related Sections</span></span>  

 [<span data-ttu-id="a6331-158">C# 指南</span><span class="sxs-lookup"><span data-stu-id="a6331-158">C# Guide</span></span>](../index.md)  
 <span data-ttu-id="a6331-159">提供 Visual C# 文件入口網站。</span><span class="sxs-lookup"><span data-stu-id="a6331-159">Provides a portal to Visual C# documentation.</span></span>  
  
 [<span data-ttu-id="a6331-160">使用 C# 的 Visual Studio 開發環境</span><span class="sxs-lookup"><span data-stu-id="a6331-160">Using the Visual Studio Development Environment for C#</span></span>](/visualstudio/get-started/csharp)  
 <span data-ttu-id="a6331-161">提供描述 IDE 和編輯器的概念和工作主題連結。</span><span class="sxs-lookup"><span data-stu-id="a6331-161">Provides links to conceptual and task topics that describe the IDE and Editor.</span></span>  
  
 [<span data-ttu-id="a6331-162">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a6331-162">C# Programming Guide</span></span>](../programming-guide/index.md)  
 <span data-ttu-id="a6331-163">包含如何使用 C# 程式設計語言的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a6331-163">Includes information about how to use the C# programming language.</span></span>
