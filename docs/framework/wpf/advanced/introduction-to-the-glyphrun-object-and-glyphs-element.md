---
title: GlyphRun 物件和 Glyphs 項目簡介
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 9af07d48877fee0e94f8e5fa2556c4361795df6a
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740364"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>GlyphRun 物件和 Glyphs 項目簡介
本主題描述 <xref:System.Windows.Media.GlyphRun> 物件和 <xref:System.Windows.Documents.Glyphs> 元素。  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>GlyphRun 簡介  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供先進的文字支援（包括圖像層級標記），而且想要在格式化之後攔截並保存文字的客戶，可直接存取 <xref:System.Windows.Documents.Glyphs>。 這些功能可針對下列每個案例中的不同文字轉譯需求提供重要支援。  
  
1. 固定格式文件的螢幕顯示。  
  
2. 列印案例。  
  
    - 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 作為裝置印表機語言。  
  
    - Microsoft XPS 檔寫入器。  
  
    - 先前的印表機驅動程式，從 Win32 應用程式輸出為固定格式。  
  
    - 列印多工緩衝處理格式。  
  
3. 固定格式的檔標記法，包括舊版 Windows 和其他計算裝置的用戶端。  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> 和 <xref:System.Windows.Media.GlyphRun> 是針對固定格式的檔簡報和列印案例所設計。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 針對一般版面配置和 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 案例（例如 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.TextBlock>）提供數個元素。 如需配置和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例的詳細資訊，請參閱 [WPF 中的印刷樣式](typography-in-wpf.md)。  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>GlyphRun 物件  
 <xref:System.Windows.Media.GlyphRun> 物件代表單一字型單一字型的一系列字元，並以單一轉譯樣式呈現。  
  
 <xref:System.Windows.Media.GlyphRun> 包括字型的詳細資料，例如圖像 <xref:System.Windows.Documents.Glyphs.Indices%2A> 和個別的圖像位置。 它也包含從產生執行的原始 Unicode 程式碼點、字元到圖像緩衝區位移對應資訊，以及每個字元和每個字元的旗標。  
  
 <xref:System.Windows.Media.GlyphRun> 具有對應的高階 <xref:System.Windows.FrameworkElement>，<xref:System.Windows.Documents.Glyphs>。 <xref:System.Windows.Documents.Glyphs> 可以用於專案樹狀結構和 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記中，以代表 <xref:System.Windows.Media.GlyphRun> 的輸出。  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Glyphs 項目  
 <xref:System.Windows.Documents.Glyphs> 元素代表 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中 <xref:System.Windows.Media.GlyphRun> 的輸出。 下列標記語法是用來描述 <xref:System.Windows.Documents.Glyphs> 元素。  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 下列屬性定義對應至範例標記中的前四個屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|指定資源識別碼：檔案名、Web 統一資源識別元（URI），或應用程式 .exe 或容器中的資源參考。|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|指定字型大小 (以繪圖介面單位為單位) (預設值為 .96 英吋)。|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|指定粗體和斜體樣式的旗標。|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|指定雙向配置層級。 偶數值和零值表示由左至右的版面配置，奇數值則表示由右至左的版面配置。|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Indices 屬性  
 <xref:System.Windows.Documents.Glyphs.Indices%2A> 屬性是圖像規格的字串。 如果由一系列字符形成單一叢集，則會先指定叢集中的第一個字符，再指定合併多少字符和多少字碼指標來形成叢集。 <xref:System.Windows.Documents.Glyphs.Indices%2A> 屬性會在一個字串中收集下列屬性。  
  
- 字符索引  
  
- 字符遞增寬度  
  
- 合併字符附加向量  
  
- 從字碼指標到字符的叢集對應  
  
- 字符旗標  
  
 每個字符規格的形式如下。  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>字符度量  
 每個字元都會定義度量，以指定其與其他 <xref:System.Windows.Documents.Glyphs>的對齊方式。 下圖定義兩個不同字符字元的各種印刷品質。  
  
 ![字元測量繪圖器](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>字符標記  
 下列程式碼範例示範如何在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中使用 <xref:System.Windows.Documents.Glyphs> 元素的各種屬性。  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>請參閱

- [WPF 中的印刷樣式](typography-in-wpf.md)
- [WPF 中的文件](documents-in-wpf.md)
- [文字](optimizing-performance-text.md)
