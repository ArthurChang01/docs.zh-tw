---
title: ImageList 元件概觀
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: b46204375cb046d637f4c9e1d888f37d10ea1f57
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728097"
---
# <a name="imagelist-component-overview-windows-forms"></a><span data-ttu-id="a83d3-102">ImageList 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="a83d3-102">ImageList Component Overview (Windows Forms)</span></span>

<span data-ttu-id="a83d3-103">Windows Form <xref:System.Windows.Forms.ImageList> 元件可用來儲存影像，然後可以用控制項來顯示這些影像。</span><span class="sxs-lookup"><span data-stu-id="a83d3-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is used to store images, which can then be displayed by controls.</span></span> <span data-ttu-id="a83d3-104">影像清單可讓您針對單一且一致的影像目錄來撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="a83d3-104">An image list allows you to write code for a single, consistent catalog of images.</span></span> <span data-ttu-id="a83d3-105">例如，若要旋轉 <xref:System.Windows.Forms.Button> 控制項所顯示的影像，您只要變更按鈕的 <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> 或 <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> 屬性即可。</span><span class="sxs-lookup"><span data-stu-id="a83d3-105">For example, you can rotate images displayed by a <xref:System.Windows.Forms.Button> control simply by changing the button's <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> or <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> property.</span></span> <span data-ttu-id="a83d3-106">您也可以將相同的影像清單與多個控制項產生關聯。</span><span class="sxs-lookup"><span data-stu-id="a83d3-106">You can also associate the same image list with multiple controls.</span></span> <span data-ttu-id="a83d3-107">例如，如果您同時使用 <xref:System.Windows.Forms.ListView> 控制項和 <xref:System.Windows.Forms.TreeView> 控制項來顯示相同的檔案清單，在影像清單中變更檔案的圖示將會導致新的圖示同時出現在這兩個檢視中。</span><span class="sxs-lookup"><span data-stu-id="a83d3-107">For example, if you are using both a <xref:System.Windows.Forms.ListView> control and a <xref:System.Windows.Forms.TreeView> control to display the same list of files, changing a file's icon in the image list will cause the new icon to appear in both views.</span></span>

## <a name="using-imagelist-with-controls"></a><span data-ttu-id="a83d3-108">使用 ImageList 搭配控制項</span><span class="sxs-lookup"><span data-stu-id="a83d3-108">Using ImageList with Controls</span></span>

<span data-ttu-id="a83d3-109">您可以使用影像清單來搭配具有 `ImageList` 屬性的任何控制項，或者若是 <xref:System.Windows.Forms.ListView> 控制項，則為 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 和 <xref:System.Windows.Forms.ListView.LargeImageList%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a83d3-109">You can use an image list with any control that has an `ImageList` property — or in the case of the <xref:System.Windows.Forms.ListView> control, <xref:System.Windows.Forms.ListView.SmallImageList%2A> and <xref:System.Windows.Forms.ListView.LargeImageList%2A> properties.</span></span> <span data-ttu-id="a83d3-110">可與影像清單產生關聯的控制項包括：<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.ToolBar>、<xref:System.Windows.Forms.TabControl>、<xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.CheckBox>、<xref:System.Windows.Forms.RadioButton> 和 <xref:System.Windows.Forms.Label> 控制項。</span><span class="sxs-lookup"><span data-stu-id="a83d3-110">The controls that can be associated with an image list include: the <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, and <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="a83d3-111">若要將影像清單與控制項產生關聯，請將控制項的 `ImageList` 屬性設為 <xref:System.Windows.Forms.ImageList> 元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a83d3-111">To associate the image list with a control, set the control's `ImageList` property to the name of the <xref:System.Windows.Forms.ImageList> component.</span></span>

## <a name="key-properties"></a><span data-ttu-id="a83d3-112">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="a83d3-112">Key Properties</span></span>

<span data-ttu-id="a83d3-113"><xref:System.Windows.Forms.ImageList> 元件的索引鍵屬性是 <xref:System.Windows.Forms.ImageList.Images%2A>，其中包含要供相關聯控制項使用的圖片。</span><span class="sxs-lookup"><span data-stu-id="a83d3-113">The key property of the <xref:System.Windows.Forms.ImageList> component is <xref:System.Windows.Forms.ImageList.Images%2A>, which contains the pictures to be used by the associated control.</span></span> <span data-ttu-id="a83d3-114">每個個別影像都可以依其索引值或索引鍵來存取。</span><span class="sxs-lookup"><span data-stu-id="a83d3-114">Each individual image can be accessed by its index value or by its key.</span></span> <span data-ttu-id="a83d3-115"><xref:System.Windows.Forms.ImageList.ColorDepth%2A> 屬性可決定要用來呈現影像的色彩數目。</span><span class="sxs-lookup"><span data-stu-id="a83d3-115">The <xref:System.Windows.Forms.ImageList.ColorDepth%2A> property determines the number of colors that the images are rendered with.</span></span> <span data-ttu-id="a83d3-116">所有影像都會以 <xref:System.Windows.Forms.ImageList.ImageSize%2A> 屬性設定的相同大小來顯示。</span><span class="sxs-lookup"><span data-stu-id="a83d3-116">The images will all be displayed at the same size, set by the <xref:System.Windows.Forms.ImageList.ImageSize%2A> property.</span></span> <span data-ttu-id="a83d3-117">較大的影像會調整為符合此大小。</span><span class="sxs-lookup"><span data-stu-id="a83d3-117">Images that are larger will be scaled to fit.</span></span>

## <a name="see-also"></a><span data-ttu-id="a83d3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a83d3-118">See also</span></span>

- <xref:System.Windows.Forms.ImageList>
- [<span data-ttu-id="a83d3-119">操作說明：使用 Windows Forms ImageList 元件加入或移除影像</span><span class="sxs-lookup"><span data-stu-id="a83d3-119">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
