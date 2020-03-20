---
title: 巡覽拓撲概觀
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 08f6342095706e5ffe9479f5236457d21474152a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174195"
---
# <a name="navigation-topologies-overview"></a>巡覽拓撲概觀
<a name="introduction"></a>本概述介紹了 WPF 中的導航拓撲。 並接著說明三種常見的巡覽拓撲及其範例。  
  
> [!NOTE]
> 在閱讀本主題之前，您應該熟悉使用頁面函數在 WPF 中進行結構化導航的概念。 有關這兩個主題的詳細資訊，請參閱[結構化導航概述](structured-navigation-overview.md)。  
  
 本主題包含下列幾節：  
  
- [巡覽拓撲](#Navigation_Topologies)  
  
- [結構化巡覽拓撲](#Structured_Navigation_Topologies)  
  
- [透過固定線性拓撲進行巡覽](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [透過固定的階層式拓撲進行動態巡覽](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [透過動態產生的拓撲進行巡覽](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a>巡覽拓撲  
 在 WPF 中，導航通常由<xref:System.Windows.Controls.Page>具有超連結 （<xref:System.Windows.Documents.Hyperlink>） 的頁面組成，這些頁面在按一下時導航到其他頁面。 導航到的頁面由統一的資源識別碼 （URI） 標識（請參閱[WPF 中的 Pack URI）。](pack-uris-in-wpf.md) 請考慮以下顯示頁面、超連結和統一資源識別項 （URI） 的簡單示例：  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 這些頁面排列在*導航拓撲*中，其結構取決於如何在頁面之間導航。 這種特定巡覽拓撲適合簡單的案例，不過巡覽可能需要更複雜的拓撲，其中有些只能在應用程式執行時定義。  
  
 本主題涵蓋三種常見的導航拓撲：*固定線性*、*固定分層*和*動態生成*。 每個導航拓撲都使用示例進行演示，該示例具有[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]下圖所示的示例：  
  
 ![包含資料項目和導覽按鈕的任務頁。](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a>結構化巡覽拓撲  
 巡覽拓撲有下列兩種廣泛的類型：  
  
- **固定拓撲**：在編譯時期定義，且不會在執行階段變更。 固定拓撲適用於以線性或階層式順序的固定順序來瀏覽頁面。  
  
- **動態拓撲**：根據從使用者、應用程式，或系統收集而得的輸入，在執行階段定義。 如果要以不同的順序瀏覽頁面，動態拓撲就十分實用。  
  
 雖然您可以使用頁面來建立巡覽拓撲，但本範例會使用頁面函式來提供額外的支援，藉此簡化透過拓撲頁面傳遞和傳回資料的支援。  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a>透過固定線性拓撲進行巡覽  
 固定線性拓撲類似於含有一個或多個精靈頁面，並以固定順序巡覽的精靈結構。 下圖顯示了具有固定線性拓撲的嚮導的高級結構和流程：  
  
 ![顯示固定線性拓撲的圖表。](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 透過固定線性拓撲進行巡覽的一般行為包括以下：  
  
- 從呼叫頁面巡覽至啟動器頁面，其可初始化精靈，並巡覽至精靈的第一頁。 啟動器頁 （[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]無<xref:System.Windows.Navigation.PageFunction%601>-） 不是必需的，因為調用頁可以直接調用第一個嚮導頁。 不過，如果精靈的初始化作業特別複雜，則可以使用啟動程式頁面來簡化這項作業。  
  
- 使用者可以利用 [向後] 和 [向前] 按鈕 (或超連結)，在頁面之間巡覽。  
  
- 使用者可以利用日誌，在頁面之間巡覽。  
  
- 使用者可以按 [取消] 按鈕，取消任何精靈頁面中的精靈。  
  
- 使用者可以按 [結束] 按鈕，接受最後一個精靈頁面中的精靈。  
  
- 如果取消精靈，精靈會傳回適當的結果，但不會傳回任何資料。  
  
- 如果使用者接受精靈，精靈會傳回適當的結果，並傳回它所收集的資料。  
  
- 完成精靈時 (已接受或取消)，即會從日誌中移除精靈所含的頁面。 這可將精靈的每個執行個體隔離，以避免潛在的資料或狀態異常。  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>透過固定的階層式拓撲進行動態巡覽  
 在某些應用程式中，頁面允許導航到兩個或多個其他頁面，如下圖所示：
  
 ![顯示可導航到多個頁面的頁面的圖表。](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 這個結構稱為固定的階層式拓撲，而周遊階層的順序通常是在執行階段由應用程式或使用者決定。 階層中每個可巡覽至兩個以上其他頁面的頁面，皆會在執行階段收集必要資料以判斷可巡覽至哪些頁面。 下圖說明瞭基於上圖的幾種可能的導航序列之一：  
  
 ![顯示可能的導航序列的圖表。](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 雖然固定階層式結構中的頁面巡覽順序是在執行階段決定，但使用者體驗仍和固定線性拓撲的使用者體驗相同：  
  
- 從呼叫頁面巡覽至啟動器頁面，其可初始化精靈，並巡覽至精靈的第一頁。 啟動器頁 （[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]無<xref:System.Windows.Navigation.PageFunction%601>-） 不是必需的，因為調用頁可以直接調用第一個嚮導頁。 不過，如果精靈的初始化作業特別複雜，則可以使用啟動程式頁面來簡化這項作業。  
  
- 使用者可以利用 [向後] 和 [向前] 按鈕 (或超連結)，在頁面之間巡覽。  
  
- 使用者可以利用日誌，在頁面之間巡覽。  
  
- 如果使用者向後巡覽日誌，即可變更巡覽順序。  
  
- 使用者可以按 [取消] 按鈕，取消任何精靈頁面中的精靈。  
  
- 使用者可以按 [結束] 按鈕，接受最後一個精靈頁面中的精靈。  
  
- 如果取消精靈，精靈會傳回適當的結果，但不會傳回任何資料。  
  
- 如果使用者接受精靈，精靈會傳回適當的結果，並傳回它所收集的資料。  
  
- 完成精靈時 (已接受或取消)，即會從日誌中移除精靈所含的頁面。 這可將精靈的每個執行個體隔離，以避免潛在的資料或狀態異常。  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a>透過動態產生的拓撲進行巡覽  
 在某些應用程式中，兩個以上頁面的巡覽順序只能在執行階段由使用者、應用程式或外部資料決定。 下圖說明瞭一組具有不確定導航序列的頁面：  
  
 ![具有不確定導航序列的一組頁面。](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 下圖顯示了使用者在運行時選擇的導航序列：  
  
 ![顯示運行時選擇的導航序列的圖表。](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 巡覽順序也稱為動態產生的拓撲。 對使用者來說，即使使用另一種巡覽拓撲，其使用者體驗和上一個拓撲是一樣的：  
  
- 從呼叫頁面巡覽至啟動器頁面，其可初始化精靈，並巡覽至精靈的第一頁。 啟動器頁 （[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]無<xref:System.Windows.Navigation.PageFunction%601>-） 不是必需的，因為調用頁可以直接調用第一個嚮導頁。 不過，如果精靈的初始化作業特別複雜，則可以使用啟動程式頁面來簡化這項作業。  
  
- 使用者可以利用 [向後] 和 [向前] 按鈕 (或超連結)，在頁面之間巡覽。  
  
- 使用者可以利用日誌，在頁面之間巡覽。  
  
- 使用者可以按 [取消] 按鈕，取消任何精靈頁面中的精靈。  
  
- 使用者可以按 [結束] 按鈕，接受最後一個精靈頁面中的精靈。  
  
- 如果取消精靈，精靈會傳回適當的結果，但不會傳回任何資料。  
  
- 如果使用者接受精靈，精靈會傳回適當的結果，並傳回它所收集的資料。  
  
- 完成精靈時 (已接受或取消)，即會從日誌中移除精靈所含的頁面。 這可將精靈的每個執行個體隔離，以避免潛在的資料或狀態異常。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [結構化巡覽概觀](structured-navigation-overview.md)
