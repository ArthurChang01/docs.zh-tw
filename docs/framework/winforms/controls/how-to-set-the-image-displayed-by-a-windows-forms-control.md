---
title: 設定控制項所顯示的影像
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 5df0068c8462bbaab0cb0135de1dd1b91ababe06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746866"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="12cd2-102">如何：設定 Windows Forms 控制項所顯示的影像</span><span class="sxs-lookup"><span data-stu-id="12cd2-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="12cd2-103">數個 Windows Forms 控制項可以顯示影像。</span><span class="sxs-lookup"><span data-stu-id="12cd2-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="12cd2-104">這些影像可以是用來闡明控制項用途的圖示，例如代表儲存命令的按鈕上的磁片圖示。</span><span class="sxs-lookup"><span data-stu-id="12cd2-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the Save command.</span></span> <span data-ttu-id="12cd2-105">或者，圖示可以是背景影像，為控制項提供您想要的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="12cd2-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="programmatic"></a><span data-ttu-id="12cd2-106">程式設計</span><span class="sxs-lookup"><span data-stu-id="12cd2-106">Programmatic</span></span>

<span data-ttu-id="12cd2-107">將控制項的 `Image` 或 `BackgroundImage` 屬性設定為 <xref:System.Drawing.Image>類型的物件。</span><span class="sxs-lookup"><span data-stu-id="12cd2-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="12cd2-108">一般來說，您會使用 <xref:System.Drawing.Image.FromFile%2A> 方法，從檔案載入影像。</span><span class="sxs-lookup"><span data-stu-id="12cd2-108">Generally, you'll be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

<span data-ttu-id="12cd2-109">在下列程式碼範例中，為影像位置設定的路徑是 [我的**圖片**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="12cd2-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="12cd2-110">大部分執行 Windows 作業系統的電腦都包含此目錄。</span><span class="sxs-lookup"><span data-stu-id="12cd2-110">Most computers running the Windows operating system include this directory.</span></span> <span data-ttu-id="12cd2-111">這也可讓具有最低系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="12cd2-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="12cd2-112">下列程式碼範例要求您已經有已加入 <xref:System.Windows.Forms.PictureBox> 控制項的表單。</span><span class="sxs-lookup"><span data-stu-id="12cd2-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a><span data-ttu-id="12cd2-113">設計師</span><span class="sxs-lookup"><span data-stu-id="12cd2-113">Designer</span></span>

1. <span data-ttu-id="12cd2-114">在 Visual Studio 的 [**屬性**] 視窗中，選取控制項的 [**影像**] 或 [ **BackgroundImage** ] 屬性，然後選取 [Visual Studio](./media/visual-studio-ellipsis-button.png)中的省略號] \ （![省略號按鈕）以顯示 [**選取資源**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="12cd2-114">In the **Properties** window of Visual Studio, select the **Image** or **BackgroundImage** property of the control, and then select the ellipsis (![Ellipsis button in Visual Studio](./media/visual-studio-ellipsis-button.png)) to display the **Select Resource** dialog box.</span></span>

2. <span data-ttu-id="12cd2-115">選取您想要顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="12cd2-115">Select the image you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="12cd2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12cd2-116">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
