---
title: 逐步解說：使用對齊線排列 Windows Form 上的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 04bef7162662f4fbefdaa151de13468d88530914
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460649"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>逐步解說：使用對齊線排列 Windows Forms 上的控制項

對許多應用程式而言，控制項在表單上的精確位置是高優先順序。 Windows Form 設計工具提供您許多版面組態工具來完成此動作。 其中一個最重要的是 <xref:System.Windows.Forms.Design.Behavior.SnapLine> 功能。

對齊線可讓您精確地顯示控制項與其他控制項的對齊位置。 它們也會顯示控制項之間的邊界建議距離，如[Windows 使用者介面指導方針](/windows/win32/uxguide/guidelines)所指定。

對齊線可讓您輕鬆對齊控制項，以提供清晰、專業的外觀和行為（外觀與風格）。

## <a name="create-the-project"></a>建立專案

1. 在 Visual Studio 中，建立名為 "SnaplineExample" 的 Windows 應用程式專案。

2. 在表單設計工具中選取表單。

## <a name="space-and-align-controls"></a>空間和對齊控制項

對齊線可讓您以精確且直覺的方式對齊表單上的控制項。 當您將選取的控制項或控制項移到靠近另一個控制項或一組控制項的位置附近時，就會顯示它們。 當您將它移到其他控制項之後，您的選擇就會「貼齊」到建議的位置。

### <a name="to-arrange-controls-using-snaplines"></a>使用對齊線排列控制項

1. 從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。

2. 將 [<xref:System.Windows.Forms.Button>] 控制項移到表單的右下角。 請注意，顯示為 <xref:System.Windows.Forms.Button> 控制項的對齊線會接近表單的底部和右側框線。 這些對齊線會顯示控制項框線與表單之間的建議距離。

3. 將 [<xref:System.Windows.Forms.Button>] 控制項移到表單的框線周圍，並記下對齊線的顯示位置。 當您完成時，請將 [<xref:System.Windows.Forms.Button>] 控制項移到表單的中央附近。

4. 將另一個 <xref:System.Windows.Forms.Button> 控制項從 [**工具箱**] 拖曳至表單上。

5. 移動第二個 <xref:System.Windows.Forms.Button> 控制項，直到接近第一個的層級為止。 請注意這兩個按鈕的文字基線上所顯示的對齊線，並請注意，您要移動的控制項會貼齊至與其他控制項完全層級的位置。

6. 移動第二個 <xref:System.Windows.Forms.Button> 控制項，直到它位於第一個位置的正上方。 請注意出現在兩個按鈕左右邊緣的對齊線，並請注意，您要移動的控制項會對齊與其他控制項完全一致的位置。

7. 選取其中一個 <xref:System.Windows.Forms.Button> 控制項，然後將其移到另一個，直到幾乎觸及為止。 請記下出現在其間的對齊線。 這個距離是控制項框線之間的建議距離。 另請注意，您要移動的控制項會貼齊此位置。

8. 將兩個 <xref:System.Windows.Forms.Panel> 控制項從 [**工具箱**] 拖曳至表單上。

9. 移動其中一個 <xref:System.Windows.Forms.Panel> 控制項，直到接近第一個的層級為止。 請注意顯示在這兩個控制項上下邊緣的對齊線，並請注意，您要移動的控制項會貼齊至與其他控制項完全層級的位置。

## <a name="align-to-form-and-container-margins"></a>對齊表單和容器邊界

對齊線可協助您以一致的方式讓控制項對齊表單和容器邊界。

1. 選取其中一個 <xref:System.Windows.Forms.Button> 控制項，然後將它移到靠近表單的右框線，直到對齊線出現為止。 對齊線與右框線的距離是控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性和表單的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值的總和。

   > [!NOTE]
   > 如果表單的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性設定為0，0，0，0，則 Windows Form 設計工具會提供陰影 <xref:System.Windows.Forms.Control.Padding%2A> 值9、9、9、9。 若要覆寫此行為，請指派0、0、0、0以外的值。

2. 藉由展開 [**屬性**] 視窗中的 [<xref:System.Windows.Forms.Control.Margin%2A>] 專案，並將 [<xref:System.Windows.Forms.Padding.All%2A>] 屬性設為0，來變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性值。 如需詳細資訊，請參閱[逐步解說：使用填補、邊界和 AutoSize 屬性配置 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)。

3. 將 [<xref:System.Windows.Forms.Button>] 控制項移到表單的右框線附近，直到對齊線出現為止。 這個距離現在是由表單的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值所提供。

4. 從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。

5. 藉由展開 [**屬性**] 視窗中的 [<xref:System.Windows.Forms.Control.Padding%2A>] 專案，並將 [<xref:System.Windows.Forms.Padding.All%2A>] 屬性設定為 [10]，來變更 <xref:System.Windows.Forms.GroupBox> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值。

6. 將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至 [<xref:System.Windows.Forms.GroupBox>] 控制項。

7. 將 <xref:System.Windows.Forms.Button> 控制項移至靠近 <xref:System.Windows.Forms.GroupBox> 控制項的右框線，直到對齊線出現為止。 移動 <xref:System.Windows.Forms.GroupBox> 控制項內的 <xref:System.Windows.Forms.Button> 控制項，並注意對齊線的出現位置。

## <a name="align-to-grouped-controls"></a>對齊群組控制項

您可以使用對齊線來對齊群組控制項以及 <xref:System.Windows.Forms.GroupBox> 控制項內的控制項。

1. 選取表單上的兩個控制項。 移動選取範圍，並記下您的選取範圍與其他控制項之間出現的對齊線。

2. 從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。

3. 將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至 [<xref:System.Windows.Forms.GroupBox>] 控制項。

4. 選取其中一個 <xref:System.Windows.Forms.Button> 控制項，然後將它移至 <xref:System.Windows.Forms.GroupBox> 控制項。 請注意顯示在 <xref:System.Windows.Forms.GroupBox> 控制項邊緣的對齊線。 也請注意出現在 <xref:System.Windows.Forms.GroupBox> 控制項所包含的 <xref:System.Windows.Forms.Button> 控制項邊緣的對齊線。 屬於容器控制項子系的控制項也支援對齊線。

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>使用對齊線來放置控制項，方法是大綱其大小

1. 按一下 [工具箱]的 <xref:System.Windows.Forms.Button> 控制項圖示。 請勿拖曳到表單。

2. 將滑鼠指標移到表單的設計介面上。 請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。 另請注意，顯示的對齊線會建議 <xref:System.Windows.Forms.Button> 控制項的對齊位置。

3. 按住滑鼠按鈕。

4. 將滑鼠指標拖曳至表單的周圍。 請注意，會繪製外框，表示控制項的位置和大小。

5. 拖曳指標，直到它與表單上的另一個控制項對齊。 請注意，對齊線會出現以指出對齊方式。

6. 放開滑鼠按鈕。 控制項會建立在外框所指示的位置和大小。

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>從工具箱拖曳控制項時使用對齊線

1. 將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至表單上，但不要放開滑鼠按鍵。

2. 將滑鼠指標移到表單的設計介面上。 請注意，指標會變更以指出將建立新 <xref:System.Windows.Forms.Button> 控制項的位置。

3. 將滑鼠指標拖曳至表單的周圍。 請注意，顯示的對齊線會建議 <xref:System.Windows.Forms.Button> 控制項的對齊位置。 尋找與其他控制項對齊的位置。

4. 放開滑鼠按鈕。 會在對齊線所指示的位置建立控制項。

## <a name="resize-a-control-using-snaplines"></a>使用對齊線調整控制項大小

1. 從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。

2. 抓取其中一個角落調整大小控點和拖曳，以調整 <xref:System.Windows.Forms.Button> 控制項的大小。 如需詳細資訊，請參閱[如何：在 Windows Forms 上調整控制項大小](how-to-resize-controls-on-windows-forms.md)。

3. 拖曳調整大小控點，直到其中一個 <xref:System.Windows.Forms.Button> 控制項的框線與另一個控制項對齊為止。 請注意，對齊線隨即出現。 另請注意，調整大小控點會貼齊對齊線所指示的位置。

4. 以不同的方向調整 <xref:System.Windows.Forms.Button> 控制項的大小，並將調整大小控點對齊不同的控制項。 請注意對齊線如何顯示在各種方向，以表示對齊方式。

## <a name="align-a-label-to-a-controls-text"></a>將標籤對齊控制項的文字

1. 從 [工具箱] <xref:System.Windows.Forms.TextBox>**將** 控制項拖曳至表單。 當您將 [<xref:System.Windows.Forms.TextBox>] 控制項放到表單上時，請按一下智慧標籤圖像，然後選取 [**將文字設定為 textBox1** ] 選項。 如需詳細資訊，請參閱[逐步解說：使用 Windows Forms 控制項上的智慧標籤執行一般](performing-common-tasks-using-smart-tags-on-wf-controls.md)工作。

2. 從 [工具箱] <xref:System.Windows.Forms.Label>**將** 控制項拖曳至表單。

3. 變更 <xref:System.Windows.Forms.Label> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。 請注意，控制項的框線會調整以符合顯示文字。

4. 將 [<xref:System.Windows.Forms.Label>] 控制項移至 [<xref:System.Windows.Forms.TextBox>] 控制項的左側，使其與 <xref:System.Windows.Forms.TextBox> 控制項的下邊緣對齊。 請注意沿著兩個控制項的下邊緣顯示的對齊線。

5. 將 <xref:System.Windows.Forms.Label> 控制項稍微向上移動，直到 <xref:System.Windows.Forms.Label> 文字和 <xref:System.Windows.Forms.TextBox> 文字對齊為止。 請注意出現的不同樣式對齊線，表示兩個控制項的文字欄位何時對齊。

## <a name="use-snaplines-with-keyboard-navigation"></a>搭配鍵盤導覽使用對齊線

1. 從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。 將它放在表單的左上角。

2. 按**Ctrl**+**向下**鍵。 請注意，控制項會向下移動到第一個可用的水準對齊位置。

3. 按**Ctrl**+**向下鍵**，直到控制項到達表單的底部為止。 請注意它在表單向下移動時所佔用的位置。

4. 按**Ctrl**+**向右箭**號。 請注意，控制項會在表單上移動到第一個可用的垂直對齊位置。

5. 按**Ctrl**+**向右箭**號，直到控制項到達表單的側邊為止。 請注意它在表單上移動時所佔用的位置。

6. 使用方向鍵的組合來移動表單周圍的控制項。 請注意控制項所佔用的位置以及伴隨的對齊線。

7. 按**Shift**+**方向鍵**，藉由一個圖元的遞增來調整 <xref:System.Windows.Forms.Button> 控制項的大小。

8. 按**Ctrl**+**Shift**+**方向鍵**，以調整 <xref:System.Windows.Forms.Button> 控制項的對齊方式遞增。

## <a name="selectively-disable-snaplines"></a>選擇性停用對齊線

1. 從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。

2. 在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。 請注意，新的按鈕控制項會出現在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的第一個儲存格。

3. 按兩下 [**工具箱**] 中的 [<xref:System.Windows.Forms.Button> 控制項] 圖示，再按兩次。 這會在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中留下一個空白儲存格。

4. 將 [<xref:System.Windows.Forms.Button>] 控制項從 [**工具箱**] 拖曳至 [<xref:System.Windows.Forms.TableLayoutPanel>] 控制項的空白儲存格。 請注意，不會顯示對齊線。

5. 將 [<xref:System.Windows.Forms.Button>] 控制項拖曳至 [<xref:System.Windows.Forms.TableLayoutPanel>] 控制項，並將它移到 [<xref:System.Windows.Forms.TableLayoutPanel>] 控制項周圍。 請注意，對齊線會再次出現。

## <a name="disable-snaplines"></a>停用對齊線

按**Alt**鍵，並在表單周圍移動控制項。

不會顯示對齊線，而且控制項不會貼齊任何可能的對齊位置。

### <a name="to-disable-snaplines-in-the-design-environment"></a>停用設計環境中的對齊線

1. 從 [**工具**] 功能表中，開啟 [**選項**] 對話方塊。 選取 [ **Windows Form 設計工具**]。

2. 選取 [**一般**] 節點。 在 [**版面配置模式]** 區段中，將選取專案從**對齊線**變更為**對齊**。

3. 選取 **[確定]** 以套用設定。

4. 選取表單上的控制項，並將它移到其他控制項的周圍。 請注意，對齊線不會出現。

## <a name="next-steps"></a>後續步驟

對齊線提供直覺的方式來對齊表單上的控制項。 進一步的探索建議包括：

- 嘗試在另一個 <xref:System.Windows.Forms.GroupBox> 控制項內嵌套 <xref:System.Windows.Forms.GroupBox> 控制項。 將 <xref:System.Windows.Forms.Button> 控制項放在子 <xref:System.Windows.Forms.GroupBox> 控制項內，另一個在父 <xref:System.Windows.Forms.GroupBox> 控制項內。 四處移動 <xref:System.Windows.Forms.Button> 控制項，以查看對齊線如何跨容器界限。

- 建立 <xref:System.Windows.Forms.TextBox> 控制項的資料行，以及 <xref:System.Windows.Forms.Label> 控制項的對應資料行。 將 [<xref:System.Windows.Forms.Label> 控制項] 的 [<xref:System.Windows.Forms.Control.AutoSize%2A>] 屬性值設定為 [`true`]。 使用對齊線來移動 <xref:System.Windows.Forms.Label> 控制項，使其顯示的文字與 <xref:System.Windows.Forms.TextBox> 控制項中的文字對齊。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)
