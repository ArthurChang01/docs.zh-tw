---
title: FontDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745700"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="4fe7b-102">FontDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="4fe7b-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="4fe7b-103">Windows Forms <xref:System.Windows.Forms.FontDialog> 元件是預先設定的對話方塊，這是標準的 Windows**字型** 對話方塊，用來公開目前安裝于系統上的字型。</span><span class="sxs-lookup"><span data-stu-id="4fe7b-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="4fe7b-104">在以 Windows 為基礎的應用程式中使用它做為字型選擇的簡單解決方案，而不是設定自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4fe7b-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="4fe7b-105">根據預設，對話方塊會顯示字型、字型樣式和大小的清單方塊;像是刪除線和底線等效果的核取方塊;腳本的下拉式清單;以及字型外觀的範例。</span><span class="sxs-lookup"><span data-stu-id="4fe7b-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="4fe7b-106">（腳本是指適用于指定字型的不同字元腳本，例如希伯來文或日文）。若要顯示 [字型] 對話方塊，請呼叫 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4fe7b-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="4fe7b-107">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="4fe7b-107">Key Properties</span></span>  
 <span data-ttu-id="4fe7b-108">元件有數個屬性可設定其外觀。</span><span class="sxs-lookup"><span data-stu-id="4fe7b-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="4fe7b-109">設定對話方塊選項的屬性會 <xref:System.Windows.Forms.FontDialog.Font%2A> 並 <xref:System.Windows.Forms.FontDialog.Color%2A>。</span><span class="sxs-lookup"><span data-stu-id="4fe7b-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="4fe7b-110"><xref:System.Windows.Forms.FontDialog.Font%2A> 屬性會設定字型、樣式、大小、腳本和效果;例如，`Arial, 10pt, style=Italic, Strikeout`。</span><span class="sxs-lookup"><span data-stu-id="4fe7b-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe7b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fe7b-111">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="4fe7b-112">FontDialog 元件</span><span class="sxs-lookup"><span data-stu-id="4fe7b-112">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
