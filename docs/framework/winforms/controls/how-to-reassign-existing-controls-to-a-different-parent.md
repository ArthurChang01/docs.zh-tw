---
title: 如何：將現有控制項重新指派至不同的父代
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459205"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>如何：將現有控制項重新指派至不同的父系

您可以將表單上現有的控制項指派給新的容器控制項。

1. 在 Visual Studio 中，將三個 <xref:System.Windows.Forms.Button> 控制項從 [**工具箱**] 拖曳至表單上。 將它們放在相鄰的位置，但不要對齊。

2. 按一下 [工具箱]的 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。 （請勿將圖示拖曳到表單上。）

3. 將滑鼠指標靠近三個 <xref:System.Windows.Forms.Button> 控制項。

   指標會變成十字形狀並附有 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。

4. 按住滑鼠按鈕。

5. 拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的外框。

6. 繪製三個 <xref:System.Windows.Forms.Button> 控制項的外框。

7. 放開滑鼠按鈕。

   三個 <xref:System.Windows.Forms.Button> 控制項現在都已插入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [逐步解說：使用對齊線排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
