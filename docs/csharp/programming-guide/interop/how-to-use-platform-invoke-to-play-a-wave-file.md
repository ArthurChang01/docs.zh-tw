---
title: 如何：使用平台叫用播放 Wave 檔案程式C#設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 6c2313f7b600bc1670c944f6a93868c1bc4c7c16
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039332"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="6be80-102">如何：使用平台叫用播放 WAV 檔 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="6be80-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>

<span data-ttu-id="6be80-103">下列 C# 程式碼範例說明如何在 Windows 作業系統上使用平台叫用服務來播放 .wav 音效檔。</span><span class="sxs-lookup"><span data-stu-id="6be80-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="6be80-104">範例</span><span class="sxs-lookup"><span data-stu-id="6be80-104">Example</span></span>

<span data-ttu-id="6be80-105">這個範例程式碼會使用 <xref:System.Runtime.InteropServices.DllImportAttribute>，以將 `winmm.dll` 的 `PlaySound` 方法進入點匯入為 `Form1 PlaySound()`。</span><span class="sxs-lookup"><span data-stu-id="6be80-105">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="6be80-106">這個範例包含具有按鈕的簡單 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="6be80-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="6be80-107">按一下按鈕會開啟標準視窗 <xref:System.Windows.Forms.OpenFileDialog> 對話方塊，讓您可以開啟要播放的檔案。</span><span class="sxs-lookup"><span data-stu-id="6be80-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="6be80-108">選取 wave 檔案時，會使用*winmm.dll 連結*庫的 `PlaySound()` 方法來播放該檔案。</span><span class="sxs-lookup"><span data-stu-id="6be80-108">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="6be80-109">如需此方法的詳細資訊，請參閱 [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files) (於波形音訊檔案使用 PlaySound 函式)。</span><span class="sxs-lookup"><span data-stu-id="6be80-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="6be80-110">瀏覽並選取副檔名為 .wav 的檔案，然後按一下 [開啟]，以使用平台叫用來播放音訊檔案。</span><span class="sxs-lookup"><span data-stu-id="6be80-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="6be80-111">文字方塊會顯示所選取檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="6be80-111">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="6be80-112">透過篩選設定來篩選 [開啟檔案] 對話方塊，使其只顯示副檔名為 .wav 的檔案︰</span><span class="sxs-lookup"><span data-stu-id="6be80-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="6be80-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6be80-113">Compiling the code</span></span>

1. <span data-ttu-id="6be80-114">在 Visual Studio 中C#建立新的 Windows Forms 應用程式專案，並將其命名為**WinSound**。</span><span class="sxs-lookup"><span data-stu-id="6be80-114">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="6be80-115">複製上述程式碼，並將它貼到*Form1.cs*檔案的內容上。</span><span class="sxs-lookup"><span data-stu-id="6be80-115">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="6be80-116">複製下列程式碼，並將它貼入*Form1.Designer.cs*檔案中的 [`InitializeComponent()`] 方法中，在任何現有的程式碼之後。</span><span class="sxs-lookup"><span data-stu-id="6be80-116">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="6be80-117">編譯並執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="6be80-117">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="6be80-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="6be80-118">See also</span></span>

- [<span data-ttu-id="6be80-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6be80-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6be80-120">互通性概觀</span><span class="sxs-lookup"><span data-stu-id="6be80-120">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="6be80-121">詳述平台叫用</span><span class="sxs-lookup"><span data-stu-id="6be80-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="6be80-122">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="6be80-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
