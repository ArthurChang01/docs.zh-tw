---
title: 操作說明：清除繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458872"
---
# <a name="how-to-clear-bindings"></a>操作說明：清除繫結
這個範例顯示如何清除物件的繫結。  
  
## <a name="example"></a>範例  
 若要清除物件上個別屬性的系結，請呼叫 <xref:System.Windows.Data.BindingOperations.ClearBinding%2A>，如下列範例所示。 下列範例會從*mytext*的 <xref:System.Windows.Controls.TextBlock.TextProperty> 中移除系結，<xref:System.Windows.Controls.TextBlock> 物件。  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 清除繫結會移除繫結，讓相依性屬性的值還原為沒有繫結時應該有的值。 這個值可以是預設值、繼承值或是資料範本繫結的值。  
  
 若要清除物件上所有可能屬性的系結，請使用 <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Data.BindingOperations>
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
