---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ac385880f8c13c23dffff67fc2a1ecc5609fd189
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581409"
---
# <a name="-optioncompare"></a><span data-ttu-id="94a1d-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="94a1d-102">-optioncompare</span></span>

<span data-ttu-id="94a1d-103">指定如何進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="94a1d-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="94a1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="94a1d-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="94a1d-105">備註</span><span class="sxs-lookup"><span data-stu-id="94a1d-105">Remarks</span></span>

<span data-ttu-id="94a1d-106">您可以指定`-optioncompare`兩種形式的其中一`-optioncompare:binary`種：使用二進位字串比較， `-optioncompare:text`並使用文字字串比較。</span><span class="sxs-lookup"><span data-stu-id="94a1d-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="94a1d-107">根據預設，編譯器會使用`-optioncompare:binary`。</span><span class="sxs-lookup"><span data-stu-id="94a1d-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="94a1d-108">在 Microsoft Windows 中，目前的字碼頁會決定二進位排序次序。</span><span class="sxs-lookup"><span data-stu-id="94a1d-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="94a1d-109">典型的二進位排序次序如下所示：</span><span class="sxs-lookup"><span data-stu-id="94a1d-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="94a1d-110">以文字為基礎的字串比較是以您系統的地區設定所決定的不區分大小寫文字排序次序為基礎。</span><span class="sxs-lookup"><span data-stu-id="94a1d-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="94a1d-111">一般文字排序次序如下所示：</span><span class="sxs-lookup"><span data-stu-id="94a1d-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="94a1d-112">若要在 Visual Studio IDE 中設定-optioncompare</span><span class="sxs-lookup"><span data-stu-id="94a1d-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="94a1d-113">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="94a1d-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="94a1d-114">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94a1d-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="94a1d-115">按一下 [編譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="94a1d-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="94a1d-116">修改 [**選項比較**] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="94a1d-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="94a1d-117">以程式設計方式設定-optioncompare</span><span class="sxs-lookup"><span data-stu-id="94a1d-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="94a1d-118">請參閱[Option Compare 語句](../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="94a1d-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="94a1d-119">範例</span><span class="sxs-lookup"><span data-stu-id="94a1d-119">Example</span></span>

<span data-ttu-id="94a1d-120">下列程式碼會`ProjFile.vb`編譯並使用二進位字串比較。</span><span class="sxs-lookup"><span data-stu-id="94a1d-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="94a1d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94a1d-121">See also</span></span>

- [<span data-ttu-id="94a1d-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="94a1d-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="94a1d-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="94a1d-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="94a1d-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="94a1d-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="94a1d-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="94a1d-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="94a1d-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="94a1d-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="94a1d-127">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="94a1d-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="94a1d-128">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="94a1d-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
