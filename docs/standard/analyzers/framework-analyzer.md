---
title: .NET Framework Analyzers - .NET
description: Learn how to use the .NET Framework Analyzers in the .NET Framework Analyzers package to find and address security risks
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 7e64b00eb6fd2c2dbb12c54a2c725590b4d22e15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345954"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="d818d-103">.NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="d818d-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="d818d-104">您可以使用 .NET Framework Analyzer 來尋找 .NET Framework 應用程式碼中的潛在問題。</span><span class="sxs-lookup"><span data-stu-id="d818d-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="d818d-105">此分析器會找出潛在問題並建議其修正程式。</span><span class="sxs-lookup"><span data-stu-id="d818d-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="d818d-106">當您撰寫程式碼時，或在 CI 組建期間，分析器會以互動方式在 Visual Studio 中執行。</span><span class="sxs-lookup"><span data-stu-id="d818d-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="d818d-107">您應該盡早在開發中將分析器新增至專案。</span><span class="sxs-lookup"><span data-stu-id="d818d-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="d818d-108">在程式碼中找到任何潛在問題的速度愈快，修正就愈容易。</span><span class="sxs-lookup"><span data-stu-id="d818d-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="d818d-109">不過，您可以在開發週期的任何時間新增它。</span><span class="sxs-lookup"><span data-stu-id="d818d-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="d818d-110">它會找到現有程式碼的任何問題，並在您持續開發時警告您發生新問題。</span><span class="sxs-lookup"><span data-stu-id="d818d-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="d818d-111">安裝和設定 .NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="d818d-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="d818d-112">The .NET Framework Analyzers must be installed as a NuGet package on every project where you want them to run.</span><span class="sxs-lookup"><span data-stu-id="d818d-112">The .NET Framework Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="d818d-113">只有一位開發人員必須將它們新增至專案。</span><span class="sxs-lookup"><span data-stu-id="d818d-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="d818d-114">分析器套件是一種專案相依性，而且會在具有已更新方案之後，於每位開發人員的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="d818d-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="d818d-115">[Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet 套件提供 .NET Framework Analyzer。</span><span class="sxs-lookup"><span data-stu-id="d818d-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="d818d-116">此套件只提供 .NET Framework 特有的分析器，包含安全性分析器。</span><span class="sxs-lookup"><span data-stu-id="d818d-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="d818d-117">在大部分情況下，您會想要有 [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="d818d-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="d818d-118">FxCopAnalyzers 彙總套件包含 Framework.Analyzers 套件中所含的所有架構分析器以及下列分析器：</span><span class="sxs-lookup"><span data-stu-id="d818d-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>

- <span data-ttu-id="d818d-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers)：提供一般指引和 .NET Standard API 指引</span><span class="sxs-lookup"><span data-stu-id="d818d-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="d818d-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers)：提供 .NET Core API 特有的分析器。</span><span class="sxs-lookup"><span data-stu-id="d818d-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="d818d-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers)：提供包含為程式碼之文字的指引，包含註解。</span><span class="sxs-lookup"><span data-stu-id="d818d-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="d818d-122">若要進行安裝，請以滑鼠右鍵按一下專案，然後選取 [管理相依性]。</span><span class="sxs-lookup"><span data-stu-id="d818d-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="d818d-123">從 NuGet 總管中，搜尋 "NetFramework Analyzer" 或視需要搜尋 "Fx Cop Analyzer"。</span><span class="sxs-lookup"><span data-stu-id="d818d-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="d818d-124">在您方案的所有專案中安裝最新穩定版本。</span><span class="sxs-lookup"><span data-stu-id="d818d-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="d818d-125">使用 .NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="d818d-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="d818d-126">安裝 NuGet 套件之後，請建置方案。</span><span class="sxs-lookup"><span data-stu-id="d818d-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="d818d-127">分析器將會報告它在您的程式碼基底中找到的任何問題。</span><span class="sxs-lookup"><span data-stu-id="d818d-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="d818d-128">在 Visual Studio [錯誤清單] 視窗中，這些問題回報為警告，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d818d-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![架構分析器回報的問題](./media/framework-analyzers-2.png)

<span data-ttu-id="d818d-130">當您撰寫程式碼時，會在程式碼的任何潛在問題下方看到曲線。</span><span class="sxs-lookup"><span data-stu-id="d818d-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="d818d-131">將游標暫留在任何問題上，就會看到該問題的詳細資料，以及任何可能修正程式的建議，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d818d-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![架構分析器所找到的互動式問題報表](./media/framework-analyzers-1.png)

<span data-ttu-id="d818d-133">分析器會檢查您方案中的程式碼，並提供所有這些問題的警告清單：</span><span class="sxs-lookup"><span data-stu-id="d818d-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="d818d-134">CA1058：類型不應該擴充特定的基底類型</span><span class="sxs-lookup"><span data-stu-id="d818d-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="d818d-135">您不應該直接衍生自 .NET Framework 中的少數類型。</span><span class="sxs-lookup"><span data-stu-id="d818d-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="d818d-136">**類別：** 設計</span><span class="sxs-lookup"><span data-stu-id="d818d-136">**Category:** Design</span></span>

<span data-ttu-id="d818d-137">**嚴重性：** 警告</span><span class="sxs-lookup"><span data-stu-id="d818d-137">**Severity:** Warning</span></span>

<span data-ttu-id="d818d-138">其他資訊：[CA:1058：類型不應該擴充特定基底類型](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="d818d-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="d818d-139">CA2153：不要攔截損毀狀態例外</span><span class="sxs-lookup"><span data-stu-id="d818d-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="d818d-140">攔截損毀狀態例外可能會遮罩錯誤 (例如存取違規)，導致不一致的執行狀態，或讓攻擊者更容易危害系統。</span><span class="sxs-lookup"><span data-stu-id="d818d-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="d818d-141">相反地，會攔截並處理一組更具體的例外狀況類型，或重新擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="d818d-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="d818d-142">**類別：** 安全性</span><span class="sxs-lookup"><span data-stu-id="d818d-142">**Category:** Security</span></span>

<span data-ttu-id="d818d-143">**嚴重性：** 警告</span><span class="sxs-lookup"><span data-stu-id="d818d-143">**Severity:** Warning</span></span>

<span data-ttu-id="d818d-144">其他資訊：[## CA2153：不要攔截損毀狀態例外](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="d818d-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="d818d-145">CA2229：請實作序列化建構函式</span><span class="sxs-lookup"><span data-stu-id="d818d-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="d818d-146">當您建立可實作 <xref:System.Runtime.Serialization.ISerializable> 介面但未定義必要序列化建構函式的類型時，分析器會產生這個警告。</span><span class="sxs-lookup"><span data-stu-id="d818d-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="d818d-147">若要修正此規則的違規情形，請實作序列化建構函式。</span><span class="sxs-lookup"><span data-stu-id="d818d-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="d818d-148">針對密封類別，讓建構函式成為 private，否則為 protected。</span><span class="sxs-lookup"><span data-stu-id="d818d-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="d818d-149">序列化建構函式具有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="d818d-149">The serialization constructor has the following signature:</span></span>

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

<span data-ttu-id="d818d-150">**類別：** 使用方式</span><span class="sxs-lookup"><span data-stu-id="d818d-150">**Category:** Usage</span></span>

<span data-ttu-id="d818d-151">**嚴重性：** 警告</span><span class="sxs-lookup"><span data-stu-id="d818d-151">**Severity:** Warning</span></span>

<span data-ttu-id="d818d-152">其他資訊：[CA2229：必須實作序列化建構函式](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="d818d-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="d818d-153">CA2235：必須標記所有不可序列化的欄位</span><span class="sxs-lookup"><span data-stu-id="d818d-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="d818d-154">可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。</span><span class="sxs-lookup"><span data-stu-id="d818d-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="d818d-155">您必須明確地以 <xref:System.NonSerializedAttribute> 標記該欄位，來修正這個警告。</span><span class="sxs-lookup"><span data-stu-id="d818d-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="d818d-156">**類別：** 使用方式</span><span class="sxs-lookup"><span data-stu-id="d818d-156">**Category:** Usage</span></span>

<span data-ttu-id="d818d-157">**嚴重性：** 警告</span><span class="sxs-lookup"><span data-stu-id="d818d-157">**Severity:** Warning</span></span>

<span data-ttu-id="d818d-158">其他資訊：[CA2235：必須標記所有不可序列化的欄位](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="d818d-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="d818d-159">CA2237：必須以可序列化標記 ISerializable 類型</span><span class="sxs-lookup"><span data-stu-id="d818d-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="d818d-160">若要讓通用語言執行平台辨識為可序列化，即使類型透過實作 <xref:System.Runtime.Serialization.ISerializable> 介面來使用自訂序列化常式，仍然必須使用 <xref:System.SerializableAttribute> 屬性來標記類型。</span><span class="sxs-lookup"><span data-stu-id="d818d-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="d818d-161">**類別：** 使用方式</span><span class="sxs-lookup"><span data-stu-id="d818d-161">**Category:** Usage</span></span>

<span data-ttu-id="d818d-162">**嚴重性：** 警告</span><span class="sxs-lookup"><span data-stu-id="d818d-162">**Severity:** Warning</span></span>

<span data-ttu-id="d818d-163">其他資訊：[CA2237：必須以可序列化標記 ISerializable 類型](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="d818d-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="d818d-164">CA3075：XML 中的不安全 DTD 處理</span><span class="sxs-lookup"><span data-stu-id="d818d-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="d818d-165">如果您使用不安全的 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> 執行個體或參考外部實體來源，剖析器可能會接受未受信任的輸入，而將機密資訊洩漏給攻擊者。</span><span class="sxs-lookup"><span data-stu-id="d818d-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="d818d-166">**類別：** 安全性</span><span class="sxs-lookup"><span data-stu-id="d818d-166">**Category:** Security</span></span>

<span data-ttu-id="d818d-167">**嚴重性：** 警告</span><span class="sxs-lookup"><span data-stu-id="d818d-167">**Severity:** Warning</span></span>

<span data-ttu-id="d818d-168">其他資訊：[CA3075: XML 中的不安全 DTD 處理](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="d818d-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="d818d-169">CA5350：請勿使用弱式密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="d818d-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="d818d-170">攻擊變得更為進階時，密碼編譯演算法的強度會在一段時間後下降。</span><span class="sxs-lookup"><span data-stu-id="d818d-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="d818d-171">根據此密碼編譯演算法的類型和應用程式，其密碼編譯強度的進一步下降可能可讓攻擊者讀取已譯成密碼的訊息、竄改已譯成密碼的訊息、偽造數位簽章、竄改雜湊內容，或根據此演算法洩露任何加密系統。</span><span class="sxs-lookup"><span data-stu-id="d818d-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="d818d-172">針對加密，使用金鑰長度大於或等於 128 位元的 AES 演算法 (可接受 AES-256、AES-192 和 AES-128)。</span><span class="sxs-lookup"><span data-stu-id="d818d-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="d818d-173">針對雜湊，在 SHA-2 系列 (例如 SHA-2 512、SHA-2 384 或 SHA-2 256) 中使用雜湊函式。</span><span class="sxs-lookup"><span data-stu-id="d818d-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="d818d-174">**類別：** 安全性</span><span class="sxs-lookup"><span data-stu-id="d818d-174">**Category:** Security</span></span>

<span data-ttu-id="d818d-175">**嚴重性：** 警告</span><span class="sxs-lookup"><span data-stu-id="d818d-175">**Severity:** Warning</span></span>

<span data-ttu-id="d818d-176">其他資訊：[CA5350：請勿使用弱式密碼編譯演算法](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="d818d-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="d818d-177">CA5351：不要使用中斷的密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="d818d-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="d818d-178">具有可透過運算方式中斷這個演算法的攻擊。</span><span class="sxs-lookup"><span data-stu-id="d818d-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="d818d-179">這可讓攻擊者中斷設計成提供的密碼編譯保證。</span><span class="sxs-lookup"><span data-stu-id="d818d-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="d818d-180">根據此密碼編譯演算法的類型和應用程式，這可能可讓攻擊者讀取已譯成密碼的訊息、竄改已譯成密碼的訊息、偽造數位簽章、竄改雜湊內容，或根據此演算法洩露任何加密系統。</span><span class="sxs-lookup"><span data-stu-id="d818d-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="d818d-181">針對加密，使用金鑰長度大於或等於 128 位元的 AES 演算法 (可接受 AES-256、AES-192 和 AES-128)。</span><span class="sxs-lookup"><span data-stu-id="d818d-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="d818d-182">針對雜湊，在 SHA-2 系列 (例如 SHA512、SHA384 或 SHA256) 中使用雜湊函式。</span><span class="sxs-lookup"><span data-stu-id="d818d-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="d818d-183">針對數位簽章，使用金鑰長度大於或等於 2048 位元的 RSA，或金鑰長度大於或等於 256 位元的 ECDSA。</span><span class="sxs-lookup"><span data-stu-id="d818d-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="d818d-184">**類別：** 安全性</span><span class="sxs-lookup"><span data-stu-id="d818d-184">**Category:** Security</span></span>

<span data-ttu-id="d818d-185">**嚴重性：** 警告</span><span class="sxs-lookup"><span data-stu-id="d818d-185">**Severity:** Warning</span></span>

<span data-ttu-id="d818d-186">其他資訊：[CA5351：不要使用中斷的密碼編譯演算法](/visualstudio/code-quality/ca5351)</span><span class="sxs-lookup"><span data-stu-id="d818d-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span></span>
