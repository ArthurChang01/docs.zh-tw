---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: a977bc4cff822de551bf82d0f31707e9b2b6ea41
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348541"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="970cf-102">-subsystemversion （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="970cf-102">-subsystemversion (Visual Basic)</span></span>

<span data-ttu-id="970cf-103">指定產生的可執行檔可在其上執行的最小子系統版本，進而決定可執行檔可在其上執行的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="970cf-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="970cf-104">大多數情況下，此選項可確保可執行檔可以利用舊版 Windows 未提供的特定安全性功能。</span><span class="sxs-lookup"><span data-stu-id="970cf-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="970cf-105">若要指定子系統本身，請使用 [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="970cf-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="970cf-106">語法</span><span class="sxs-lookup"><span data-stu-id="970cf-106">Syntax</span></span>

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="970cf-107">參數</span><span class="sxs-lookup"><span data-stu-id="970cf-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="970cf-108">最小必要版本的子系統，以點標記法表示主要和次要版本。</span><span class="sxs-lookup"><span data-stu-id="970cf-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="970cf-109">例如，如果您將此選項的值設定為 6.01，則可以指定應用程式無法在 Windows 7 之前的作業系統上執行，如本主題稍後的表格所述。</span><span class="sxs-lookup"><span data-stu-id="970cf-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="970cf-110">您必須將 `major` 和 `minor` 的值指定為整數。</span><span class="sxs-lookup"><span data-stu-id="970cf-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="970cf-111">`minor` 版本中的前置零不會變更版本，但尾端零則會。</span><span class="sxs-lookup"><span data-stu-id="970cf-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="970cf-112">例如，6.1 和 6.01 參照相同版本，但 6.10 參照不同版本。</span><span class="sxs-lookup"><span data-stu-id="970cf-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="970cf-113">建議您將次要版本表示為兩位數，以避免混淆。</span><span class="sxs-lookup"><span data-stu-id="970cf-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="970cf-114">備註</span><span class="sxs-lookup"><span data-stu-id="970cf-114">Remarks</span></span>

<span data-ttu-id="970cf-115">下表列出常見的 Windows 子系統版本。</span><span class="sxs-lookup"><span data-stu-id="970cf-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="970cf-116">Windows 版本</span><span class="sxs-lookup"><span data-stu-id="970cf-116">Windows version</span></span>|<span data-ttu-id="970cf-117">子系統版本</span><span class="sxs-lookup"><span data-stu-id="970cf-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="970cf-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="970cf-118">Windows 2000</span></span>|<span data-ttu-id="970cf-119">5.00</span><span class="sxs-lookup"><span data-stu-id="970cf-119">5.00</span></span>|
|<span data-ttu-id="970cf-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="970cf-120">Windows XP</span></span>|<span data-ttu-id="970cf-121">5.01</span><span class="sxs-lookup"><span data-stu-id="970cf-121">5.01</span></span>|
|<span data-ttu-id="970cf-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="970cf-122">Windows Server 2003</span></span>|<span data-ttu-id="970cf-123">5.02</span><span class="sxs-lookup"><span data-stu-id="970cf-123">5.02</span></span>|
|<span data-ttu-id="970cf-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="970cf-124">Windows Vista</span></span>|<span data-ttu-id="970cf-125">6.00</span><span class="sxs-lookup"><span data-stu-id="970cf-125">6.00</span></span>|
|<span data-ttu-id="970cf-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="970cf-126">Windows 7</span></span>|<span data-ttu-id="970cf-127">6.01</span><span class="sxs-lookup"><span data-stu-id="970cf-127">6.01</span></span>|
|<span data-ttu-id="970cf-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="970cf-128">Windows Server 2008</span></span>|<span data-ttu-id="970cf-129">6.01</span><span class="sxs-lookup"><span data-stu-id="970cf-129">6.01</span></span>|
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="970cf-130">6.02</span><span class="sxs-lookup"><span data-stu-id="970cf-130">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="970cf-131">預設值</span><span class="sxs-lookup"><span data-stu-id="970cf-131">Default values</span></span>

<span data-ttu-id="970cf-132">**-subsystemversion** 編譯器選項的預設值取決於下列清單中的條件︰</span><span class="sxs-lookup"><span data-stu-id="970cf-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="970cf-133">如果設定下列清單中的任何編譯器選項，則預設值為 6.02：</span><span class="sxs-lookup"><span data-stu-id="970cf-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="970cf-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="970cf-134">-target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="970cf-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="970cf-135">-target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="970cf-136">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="970cf-136">-platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)

- <span data-ttu-id="970cf-137">如果您使用的是 MSBuild、以 .NET Framework 4.5 為目標，且尚未設定稍早在此清單中指定的任何編譯器選項，則預設值為 6.00。</span><span class="sxs-lookup"><span data-stu-id="970cf-137">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="970cf-138">如果先前的條件均非為 true，則預設值是 4.00。</span><span class="sxs-lookup"><span data-stu-id="970cf-138">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="970cf-139">設定這個選項</span><span class="sxs-lookup"><span data-stu-id="970cf-139">Setting this option</span></span>

<span data-ttu-id="970cf-140">若要在 Visual Studio 中設定 **-subsystemversion**編譯器選項，您必須開啟 vbproj 檔案，並在 MSBuild XML 中指定 `SubsystemVersion` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="970cf-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="970cf-141">您不能在 Visual Studio IDE 中設定此選項。</span><span class="sxs-lookup"><span data-stu-id="970cf-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="970cf-142">如需詳細資訊，請參閱本主題稍早的＜預設值＞或[通用的 MSBuild 專案屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="970cf-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="970cf-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="970cf-143">See also</span></span>

- [<span data-ttu-id="970cf-144">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="970cf-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

- [<span data-ttu-id="970cf-145">MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="970cf-145">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
