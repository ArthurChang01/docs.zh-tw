---
title: XAML 中的 xml:lang 處理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 98bfabba96e5805b96c63eb02233b15eae233cc0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740560"
---
# <a name="xmllang-handling-in-xaml"></a>XAML 中的 xml:lang 處理
`xml:lang` 屬性是 XML 定義的屬性，可宣告 XML 中專案的語言和文化特性資訊。 在 XAML 中有保存與這個屬性相同的意義，但仍須考量一些其他事項。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*rfc3066lang*|衍生自 [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) 標準的字串，這個字串會識別語言或語言地區。 如果是後者，則語言和區域會由單一連字號分隔。 如需值和格式的詳細資訊，請參閱 <xref:System.Windows.Markup.XmlLanguage> 。|  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 中 `xml:lang` 屬性的定義衍生自 `xml:lang`，如同全球資訊網協會（W3C） for XML 所定義的「特殊屬性」。 項目在處理語言和文化特性時，其方式可能隨著不同的實作而改變，但是 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 屬性並沒有預設的 `xml:lang` 處理。  
  
 `xml:lang` 屬性的預設值在屬性層級為空字串。  
  
 `xml:lang` 屬性效果和屬性的值，通常由對 `xml:lang` 值作用的系統解譯時，就會以子項目的形式永存。  
  
 由 .NET Framework XAML 服務的 XAML 寫入器解譯時， `xml:lang` 值可能會以基礎物件表示法建立 <xref:System.Windows.Markup.XmlLanguage> 或 <xref:System.Globalization.CultureInfo> 物件，但是該行為取決於對 `xml:lang` 指定的值是否為這些類別的有效建構。  
  
 藉由將 `xml:lang` 套用至屬性，架構即可在架構定義的屬性和 XML 中 <xref:System.Windows.Markup.XmlLangPropertyAttribute> 的意義之間建立關聯性。  
  
## <a name="wpf-usage-nodes"></a>WPF 使用量節點  
 若項目是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>的衍生類別，您可以使用對等的 <xref:System.Windows.FrameworkElement.Language%2A> 相依性屬性 (Property)，而非 `xml:lang` 屬性 (Attribute)。 根據預設，如果沒有透過屬性 (Property) 或是透過處理 <xref:System.Windows.FrameworkElement.Language%2A> 屬性 (Attribute) 另外設定，則 `xml:lang` 屬性會使用 "en-US"。  
  
## <a name="see-also"></a>請參閱

- [WPF 的全球化](../wpf/advanced/globalization-for-wpf.md)
