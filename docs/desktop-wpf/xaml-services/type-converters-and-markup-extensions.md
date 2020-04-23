---
title: XAML 的類型轉換子和標記延伸
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: bee94b03d4fd6e6f5ef8571e83f554b381dd6582
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071651"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>XAML 的類型轉換子和標記延伸

類型轉換器和標記延伸是 XAML 類型系統和 XAML 寫入器用以產生物件圖形元件的兩項技術。 雖然兩者共用某些特性，但類型轉換器和標記延伸在 XAML 節點資料流中會以不同的方式表示。 在本文件集中，有時會將類型轉換器、標記延伸和類似的建構統稱為值轉換器。

## <a name="value-converters"></a>值轉換器

在 XAML 中，值轉換器可用於多種情節。 下列清單顯示 XAML 中不同類型的值轉換器：

- 類型轉換器

- 標記延伸

- 值序列化程式

- 為 XAML 文字語法提供邏輯的相關類別或支援類別

## <a name="type-converters"></a>類型轉換器

在 .NET XAML 服務定義中,類型轉換器是<xref:System.ComponentModel.TypeConverter>從 CLR 類派生的類。 <xref:System.ComponentModel.TypeConverter>是在 XAML 存在之前 .NET 中的類。 其原始目的是支援IDE屬性的屬性視窗和類似的基於文本的編輯隱喻。 XAML 引入 .NET 用於<xref:System.ComponentModel.TypeConverter>將文字語法(如屬性值或 XAML 值節點中找到)轉換為物件。 <xref:System.ComponentModel.TypeConverter> 也可用來將物件值序列化為文字語法。 <xref:System.ComponentModel.TypeConverter>也用於以前在 Windows 示範基礎 (WPF) 和 Windows 通訊基礎 (WCF) 中特定於框架的 XAML 實現。 如需在 XAML 中 <xref:System.ComponentModel.TypeConverter> 的詳細資訊，請參閱 [Type Converters for XAML Overview](type-converters-overview.md)。

## <a name="markup-extensions"></a>標記延伸

在 .NET XAML 服務實現中,標記擴展是從類<xref:System.Windows.Markup.MarkupExtension>派生的 類。 標記延伸是一種概念，在這種形式下的標記都是源自 XAML 語言。 您可以將標記延伸視為類似可延伸的逸出序列，這個序列會呼叫服務類別來提供其邏輯。 就標記而言，XAML 處理器普遍會將文字字串中以左大括號 ({) 開頭的文字序列視為標記延伸。

標記延伸與類型轉換器不同。 類型轉換器通常與類型或成員相關聯。 當物件圖形建立或序列化作業遇到與這些實體關聯的文字語法時，即會叫用類型轉換器。

標記延伸與單一支援服務類別相關聯，但可套用至任何成員值。 (但是,您可以使用服務上下文實現標記擴展,以故意將其使用限制為某些成員或目標類型。標記擴展可以覆蓋類型轉換器關聯。 或者，您可以使用標記延伸，為原本不支援文字語法的成員指定屬性值。

如需 XAML 之標記延伸實作模式的詳細資訊，請參閱 [Markup Extensions for XAML Overview](markup-extensions-overview.md)。

## <a name="value-serializers"></a>值序列化程式

<xref:System.Windows.Markup.ValueSerializer> 是為了以最佳方式將物件轉換成字串而特製化的類型轉換器。 XAML 的 <xref:System.Windows.Markup.ValueSerializer> 可能完全無法實作 `ConvertFrom` 方法。 <xref:System.Windows.Markup.ValueSerializer> 實作取得服務的方式與 <xref:System.ComponentModel.TypeConverter> 實作類似。 虛擬方法會提供輸入 `context` 參數。 `context` 參數屬於 <xref:System.Windows.Markup.IValueSerializerContext>類型，該類型繼承自 <xref:System.IServiceProvider> 介面並具有 <xref:System.IServiceProvider.GetService%2A> 方法。

在 XAML 類型系統中，以及針對使用 XAML 節點迴圈處理序列化的 XAML 寫入器實作，與類型或成員關聯的值轉換器會由其專屬的 <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> 屬性來報告。 這對執行序列化的 XAML 寫入器所代表的意義是，如果有 <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> 和 <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> ，則應針對載入路徑使用類型轉換器，並應針對儲存路徑使用值序列化程式。 如果有 <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> 但 <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> 為 `null`，也應針對儲存路徑使用類型轉換器。

## <a name="other-value-converters"></a>其他值轉換器

值轉換器可延伸至超出類型轉換器或標記延伸的特定模式。 但是,此自定義還需要重新定義 .NET XAML 服務提供的 XAML 類型系統。 現有 XAML 類型系統具有適用於類型轉換子、標記延伸和值序列化程式的表示和報告系統，但沒有適用於自訂形式之值轉換的表示和報告系統。 如果您想要建立自訂值轉換器，請使用 <xref:System.Xaml.Schema.XamlValueConverter%601> 類型。

## <a name="type-converters-and-markup-extensions-in-combination"></a>類型轉換器和標記延伸的組合

標記延伸和類型轉換器會用於 XAML 中的不同情況。 儘管有適合標記延伸使用的內容，但標記延伸負責提供值的屬性類型轉換行為在標記延伸實作中通常不會遭到檢查。 換句話說，即使標記延伸傳回文字字串做為其 `ProvideValue` 輸出，也不會在該字串上，叫用套用至特定屬性或屬性值類型的類型轉換行為。 一般來說，標記延伸的目的是在未涉及任何類型轉換器的情況下，處理字串及傳回物件。

## <a name="service-context-for-a-value-converter"></a>值轉換器的服務內容

當您實作值轉換器時，您通常會需要存取套用值轉換器的內容。 這個內容稱為服務內容。 服務上下文可能包括諸如活動 XAML 架構上下文、訪問 XAML 架構上下文和 XAML 物件編寫器提供的類型映射系統等資訊。 如需值轉換器的可用服務內容，以及如何存取服務內容可能提供之服務的詳細資訊，請參閱 [Service Contexts Available to Type Converters and Markup Extensions](service-contexts-with-type-converters-and-markup-extensions.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [XAML 標記延伸概觀](markup-extensions-overview.md)
- [XAML 類型轉換子概觀](type-converters-overview.md)
- [適用於類型轉換子和標記延伸的服務內容](service-contexts-with-type-converters-and-markup-extensions.md)
