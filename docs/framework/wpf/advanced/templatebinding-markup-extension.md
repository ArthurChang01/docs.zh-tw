---
title: TemplateBinding 標記延伸
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 69698db8b51e3872d5941d4fba67271b1e61226e
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140451"
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding 標記延伸
將控制項樣板中的屬性值連結成為樣板化控制項上另一個屬性的值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xml  
<object property="{TemplateBinding sourceProperty}" ... />
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>XAML 屬性使用方式 (針對樣板或樣式中的 Setter 屬性)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" ... />  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`propertyName`|在 setter 語法中設定之屬性的 <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>。|  
|`sourceProperty`|存在於樣板化類型上的另一個相依性屬性，由其 <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> 所指定。<br /><br /> - 或 -<br /><br /> 「穿插句點」的屬性名稱，由樣板化目標類型以外的不同類型所定義。 這實際上是一個 <xref:System.Windows.PropertyPath>。 請參閱[PROPERTYPATH XAML 語法](propertypath-xaml-syntax.md)。|  
  
## <a name="remarks"></a>備註  
 是範本[案例的最佳](binding-markup-extension.md) `Binding`系結形式，類似于所建立的`{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}` `TemplateBinding` `TemplateBinding` 永遠是單向繫結，即使相關的屬性是預設為雙向繫結也一樣。 相關的兩個屬性必須是相依性屬性。 為了達成樣板化父系的雙向系結，請改用下列系結語句`{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`。
  
 [RelativeSource](relativesource-markupextension.md)是另一個標記延伸，有時會與或（而不`TemplateBinding`是）搭配使用，以便在範本內執行相對屬性系結。  
  
 此處未涵蓋以概念描述控制項範本;如需詳細資訊，請參閱[控制項樣式和範本](../controls/control-styles-and-templates.md)。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `TemplateBinding` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.TemplateBindingExtension.Property%2A> 延伸類別的 <xref:System.Windows.TemplateBindingExtension> 值。  
  
 物件項目語法雖然可行，但由於沒有實際的應用程式，所以這裡不加說明。 `TemplateBinding` 是用來以評估後的運算式填滿 setter 內的值，而使用 `TemplateBinding` 的物件項目語法來填滿 `<Setter.Property>` 屬性項目語法則太過繁瑣。  
  
 `TemplateBinding` 也可以用於會指定 <xref:System.Windows.TemplateBindingExtension.Property%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" ... />
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `TemplateBinding` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器執行中，此標記延伸模組的處理是由<xref:System.Windows.TemplateBindingExtension>類別所定義。  
  
 `TemplateBinding` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 XAML 中的`{`所有標記延伸都會在`}`其屬性語法中使用和字元，這是 xaml 處理器識別標記延伸必須處理屬性的慣例。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource 標記延伸](relativesource-markupextension.md)
- [繫結標記延伸](binding-markup-extension.md)
