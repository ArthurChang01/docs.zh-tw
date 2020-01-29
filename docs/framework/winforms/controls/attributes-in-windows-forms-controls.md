---
title: 控制項中的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: b32e4f87e953438a3bb11569445a9270e11c7922
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732136"
---
# <a name="attributes-in-windows-forms-controls"></a>Windows Form 控制項中的屬性
.NET Framework 提供各種不同的屬性，供您套用至自訂控制項和元件的成員。 其中一些屬性會影響類別的執行階段行為，有些則會影響設計階段行為。  
  
## <a name="attributes-for-control-and-component-properties"></a>控制項和元件屬性 (Property) 的屬性 (Attribute)  
 下表描述的屬性 (Attribute) 可套用至自訂控制項和元件的屬性 (Property) 或其他成員。 如需有關使用許多這些屬性的範例，請參閱[如何：在 Windows Forms 控制項中套用屬性](how-to-apply-attributes-in-windows-forms-controls.md)。  
  
|屬性|描述|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|指定要傳遞至屬性的值，讓屬性從其他來源取得其值。 這稱為「環境」。|  
|<xref:System.ComponentModel.BrowsableAttribute>|指定是否應該在 [屬性] 視窗中顯示屬性或事件。|  
|<xref:System.ComponentModel.CategoryAttribute>|指定在 <xref:System.Windows.Forms.PropertyGrid> 控制項中顯示設定為 <xref:System.Windows.Forms.PropertySort.Categorized> 模式時，要將屬性或事件分組的類別目錄名稱。|  
|<xref:System.ComponentModel.DefaultValueAttribute>|指定屬性的預設值。|  
|<xref:System.ComponentModel.DescriptionAttribute>|指定屬性或事件的描述。|  
|<xref:System.ComponentModel.DisplayNameAttribute>|指定不接受引數的屬性、事件或 `public void` 方法的顯示名稱。|  
|<xref:System.ComponentModel.EditorAttribute>|指定用來變更屬性的編輯器。|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|指定在編輯器中可檢視的屬性或方法。|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|指定類別或成員的內容關鍵字。|  
|<xref:System.ComponentModel.LocalizableAttribute>|指定是否應該當地語系化屬性。|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|指出以星號之類的字元來遮蔽物件的文字表示。|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|指定這個屬性 (Attribute) 所繫結的屬性 (Property) 在設計階段是唯讀或讀寫。|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|指出屬性方格應該在關聯的屬性值變更時重新整理。|  
|<xref:System.ComponentModel.TypeConverterAttribute>|指定要用來做為此屬性所繫結至物件的型別轉換子。|  
  
## <a name="attributes-for-data-binding-properties"></a>資料繫結屬性 (Property) 的屬性 (Attribute)  
 下表顯示您可以套用的屬性，以指定自訂控制項和元件如何資料繫結互動。  
  
|屬性|描述|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|指定屬性是否通常用於繫結。|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|指定元件的資料來源和資料成員屬性。|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|指定元件的預設繫結屬性。|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|指定元件的資料來源和資料成員屬性。|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|啟用屬性重新導向。|  
  
## <a name="attributes-for-classes"></a>類別的屬性  
 下表顯示您可以套用的屬性，以指定自訂控制項和元件在設計階段的行為。  
  
|屬性|描述|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|指定元件的預設事件。|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|指定元件的預設屬性。|  
|<xref:System.ComponentModel.DesignerAttribute>|指定用來實作元件之設計階段服務的類別。|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|指定類別的設計工具屬於特定的分類。|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|代表工具箱項目的屬性。|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|指定用於工具箱項目的篩選字串和篩選類型。|  
  
## <a name="see-also"></a>請參閱

- <xref:System.Attribute>
- [操作說明：在 Windows Forms 控制項中套用屬性](how-to-apply-attributes-in-windows-forms-controls.md)
- [擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [使用 .NET Framework 開發自訂的 Windows Forms 控制項](developing-custom-windows-forms-controls.md)
