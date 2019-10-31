---
title: 使用 WPF 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e05ec7fc503565333a4d05662a4e40d8d1193af
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197472"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>在 Windows Forms 應用程式中使用 WPF 控制項

您可以在 Windows Forms 架構的應用程式中使用 Windows Presentation Foundation （WPF）控制項。 雖然這些是兩個不同的視圖技術，但它們可以順暢地互通。

Visual Studio 中的 Windows Form 設計工具提供用於裝載 Windows Presentation Foundation 控制項的視覺化設計環境。 WPF 控制項是由名為 <xref:System.Windows.Forms.Integration.ElementHost>的特殊 Windows Forms 控制項所主控。 這個控制項可讓 WPF 控制項參與表單的版面配置，並接收鍵盤和滑鼠訊息。 在設計階段，您可以排列 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，就像任何 Windows Forms 控制項一樣。

您也可以在以 WPF 為基礎的應用程式中使用 Windows Forms 控制項。 如需詳細資訊，請參閱[在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)。

## <a name="see-also"></a>請參閱

- [WPF 和 Windows Forms 交互操作](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
