---
ms.openlocfilehash: 01bbc49cb0febc5a29dafc7c311b848387a4094a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803492"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a><span data-ttu-id="0762e-101">將 SelectionTextBrush 公用屬性新增至 TextBox/PasswordBox 非提示選取項目</span><span class="sxs-lookup"><span data-stu-id="0762e-101">Add SelectionTextBrush public property to TextBox/PasswordBox non-adorner selection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0762e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0762e-102">Details</span></span>|<span data-ttu-id="0762e-103">在針對 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.PasswordBox> 使用[非提示型文字選取項目](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md)的 WPF 應用程式中，開發人員現在可以設定新增的 SelectionTextBrush 屬性，以變更所選文字的轉譯。</span><span class="sxs-lookup"><span data-stu-id="0762e-103">In WPF applications using [non-adorner based text selection](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) for <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox>, developers may now set the newly added SelectionTextBrush property in order to alter the rendering of the selected text.</span></span>  <span data-ttu-id="0762e-104">根據預設，此色彩會隨著 <xref:System.Windows.SystemColors.HighlightTextBrushKey> 而變更。</span><span class="sxs-lookup"><span data-stu-id="0762e-104">By default, this color changes with <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span></span>  <span data-ttu-id="0762e-105">如果未啟用非提示型文字選取範圍，則會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="0762e-105">If non-adorner based text selection is not enabled, this property does nothing.</span></span>|
|<span data-ttu-id="0762e-106">建議</span><span class="sxs-lookup"><span data-stu-id="0762e-106">Suggestion</span></span>|<span data-ttu-id="0762e-107">啟用非提示型文字選取範圍後，您可以使用 <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> 屬性變更所選文字的外觀。</span><span class="sxs-lookup"><span data-stu-id="0762e-107">Once non-adorner based text selection is enabled, you can use the <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> property to change the appearance of the selected text.</span></span> <span data-ttu-id="0762e-108">此操作可以使用 XAML 完成：</span><span class="sxs-lookup"><span data-stu-id="0762e-108">This can be achieved using XAML:</span></span><pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="0762e-109">範圍</span><span class="sxs-lookup"><span data-stu-id="0762e-109">Scope</span></span>|<span data-ttu-id="0762e-110">主要</span><span class="sxs-lookup"><span data-stu-id="0762e-110">Major</span></span>|
|<span data-ttu-id="0762e-111">版本</span><span class="sxs-lookup"><span data-stu-id="0762e-111">Version</span></span>|<span data-ttu-id="0762e-112">4.8</span><span class="sxs-lookup"><span data-stu-id="0762e-112">4.8</span></span>|
|<span data-ttu-id="0762e-113">類型</span><span class="sxs-lookup"><span data-stu-id="0762e-113">Type</span></span>|<span data-ttu-id="0762e-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="0762e-114">Retargeting</span></span>|
|<span data-ttu-id="0762e-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0762e-115">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[<span data-ttu-id="0762e-116">System.Windows.Controls.TextBox</span><span class="sxs-lookup"><span data-stu-id="0762e-116">System.Windows.Controls.TextBox</span></span>](xref:System.Windows.Controls.TextBox)</li><li>[<span data-ttu-id="0762e-117">System.Windows.Controls.PasswordBox</span><span class="sxs-lookup"><span data-stu-id="0762e-117">System.Windows.Controls.PasswordBox</span></span>](xref:System.Windows.Controls.PasswordBox)</li></ul>|
