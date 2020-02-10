---
title: TypeConverter 和 XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 6b8b58228e94ed12557e97406e55cc4165753076
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095082"
---
# <a name="typeconverters-and-xaml"></a>TypeConverter 和 XAML
本主題介紹將字串的類型轉換當成一般 XAML 語言功能的目的。 在 .NET Framework 中，<xref:System.ComponentModel.TypeConverter> 類別可做為 managed 自訂類別的實作為執行的一部分，以便在 XAML 屬性使用方式中當做屬性值使用。 如果您撰寫自訂類別，而且想要讓類別的實例能夠當做 XAML 可設定的屬性值使用，您可能需要將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至您的類別、撰寫自訂的 <xref:System.ComponentModel.TypeConverter> 類別，或兩者都用。  

## <a name="type-conversion-concepts"></a>類型轉換概念  
  
### <a name="xaml-and-string-values"></a>XAML 和字串值  
 在 XAML 檔案中設定屬性值時，該值的初始類型是純文字的字串。 即使是其他基本專案（例如 <xref:System.Double>）是 XAML 處理器的一開始文字字串。  
  
 XAML 處理器需要兩項資訊才能處理屬性值。 第一項資訊是正在設定之屬性的實值類型。 任何定義屬性值並在 XAML 中處理的字串最後必須轉換或解析成該類型的值。 如果值是 XAML 剖析器可理解的基本類型 (例如數值)，則會嘗試直接轉換字串。 如果值是一個列舉，則用來檢查名稱的字串會符合該列舉中的具名常數。 如果值不是剖析器所辨識的基本類型，也不是列舉，則上述類型必須能夠根據已轉換的字串提供類型的執行個體或值。 您可以藉由指定類型轉換器類別來完成此動作。 類型轉換子實際上是一個 Helper 類別，可用於提供另一個類別的值，這兩者均適用於 XAML 案例，可能也適用於利用 .NET 程式碼進行程式碼呼叫。  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>在 XAML 中使用現有的類型轉換行為  
 根據您對基礎 XAML 概念的熟悉程度而定，您可能已經在基本應用程式 XAML 中使用類型轉換行為而不自知。 比方說，WPF 定義了數百個採用類型值 <xref:System.Windows.Point>的屬性。 <xref:System.Windows.Point> 是描述二維座標空間中座標的值，其實只有兩個重要的屬性： <xref:System.Windows.Point.X%2A> 和 <xref:System.Windows.Point.Y%2A>。 當您在 XAML 中指定點時，您會將它指定為字串，並在 <xref:System.Windows.Point.X%2A> 和您提供的 <xref:System.Windows.Point.Y%2A> 值之間加上分隔符號（通常是逗號）。 例如： `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>` 。  
  
 即使這種簡單的 <xref:System.Windows.Point> 類型和 XAML 中的簡單用法，也牽涉到類型轉換器。 在此情況下，這是類別 <xref:System.Windows.PointConverter>。  
  
 在類別層級定義之 <xref:System.Windows.Point> 的類型轉換子，可簡化接受 <xref:System.Windows.Point>之所有屬性的標記使用方式。 若未在此處使用類型轉換器，您就需要針對先前所示的同一個範例使用下列更多較為詳細的標記：  

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.StartPoint>
    <Point X="0" Y="0"/>
  </LinearGradientBrush.StartPoint>
  <LinearGradientBrush.EndPoint>
    <Point X="1" Y="1"/>
  </LinearGradientBrush.EndPoint>
</LinearGradientBrush>
 ```
  
 是否要使用類型轉換字串或較為詳細的對等語法，通常是編碼樣式的選擇。 您的 XAML 工具工作流程可能也會影響值的設定方式。 一些 XAML 工具傾向於發出最詳細格式的標記，因為較容易反覆存取設計工具檢視或它自己的序列化機制。  
  
 您通常可以藉由檢查類別（或屬性）是否存在已套用的 <xref:System.ComponentModel.TypeConverterAttribute>，在 WPF 和 .NET Framework 類型上探索現有的類型轉換器。 這個屬性將基於 XAML 用途以及其他可能的用途，針對該類型的值，為支援類型轉換器的類別命名。  
  
### <a name="type-converters-and-markup-extensions"></a>類型轉換器和標記延伸  
 標記延伸和類型轉換器會根據 XAML 處理器行為和套用它們的案例來填滿正交角色。 儘管有適合標記延伸使用的內容，但標記延伸負責提供值的屬性類型轉換行為在標記延伸實作中通常不會遭到檢查。 換句話說，即使標記延伸傳回文字字串做為其 `ProvideValue` 輸出，也不會在該字串上叫用套用至特定屬性或屬性值類型的類型轉換行為。一般來說，標記延伸的目的是在未涉及任何類型轉換器的情況下，處理字串並傳回物件。  
  
 需要標記延伸而不是類型轉換器的一個常見情況是參考現有的物件。 無狀態類型轉換器充其量只能產生新的執行個體，但這可能不是令人滿意的情況。 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
### <a name="native-type-converters"></a>原生類型轉換器  
 在 XAML 剖析器中的 WPF 和 .NET Framework 實作中，有些特定類型具有原生類型轉換處理，但卻不是依慣例會被視為基本類型的類型。 這類類型的範例是 <xref:System.DateTime>。 這是根據 .NET Framework 架構的運作方式：類型 <xref:System.DateTime> 定義于 mscorlib 中，這是 .NET 中最基本的程式庫。 <xref:System.DateTime> 不允許使用來自另一個引入相依性之元件（<xref:System.ComponentModel.TypeConverterAttribute> 來自系統）的屬性來進行屬性化，因此無法支援一般類型轉換器探索機制。 而是 XAML 剖析器會有一份需要這類原生處理的類型清單，這些類型的處理方式會與真正基本類型的處理方式類似 （在 <xref:System.DateTime> 的情況下，這牽涉到 <xref:System.DateTime.Parse%2A>的呼叫）。  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>實作類型轉換器  
  
### <a name="typeconverter"></a>TypeConverter  
 在先前提供的 <xref:System.Windows.Point> 範例中，已提及類別 <xref:System.Windows.PointConverter>。 針對 XAML 的 .NET 執行，所有用於 XAML 用途的類型轉換器都是衍生自基類 <xref:System.ComponentModel.TypeConverter>的類別。 <xref:System.ComponentModel.TypeConverter> 類別存在於存在 XAML 之前的 .NET Framework 版本中;其中一個原始用法是在視覺化設計工具中提供屬性對話方塊的字串轉換。 對於 XAML，<xref:System.ComponentModel.TypeConverter> 的角色會展開為包含在中的基類，以做為字串和字串的轉換，讓您能夠剖析字串屬性值，並可能將特定物件屬性的運行時間值處理回字串，以便序列化為屬性。  
  
 <xref:System.ComponentModel.TypeConverter> 會定義四個成員，以便在 XAML 處理時針對字串進行來回轉換：  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 在這些情況下，最重要的方法是 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>。 這個方法會將輸入字串轉換為所需的物件類型。 嚴格來說，<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 方法可以實作為將更廣泛的型別轉換成轉換器的預定目的地型別，進而提供超出 XAML （例如支援執行時間轉換）的用途，但針對 XAML，它只是可以處理重要 <xref:System.String> 輸入的程式碼路徑。  
  
 下一個最重要的方法是 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>。 如果應用程式轉換成標記標記法（例如，如果將它儲存至 XAML 做為檔案），<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 會負責產生標記標記法。 在此情況下，XAML 的重要程式碼路徑是當您傳遞 <xref:System.String> 的 `destinationType` 時。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 和 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 是服務查詢 <xref:System.ComponentModel.TypeConverter> 實作之功能時所使用的支援方法。 您必須實作這些方法來傳回轉換器對等轉換方法所支援類型特有案例的 `true`。 基於 XAML，這通常表示 <xref:System.String> 類型。  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>XAML 的文化特性資訊和類型轉換器  

 每個 <xref:System.ComponentModel.TypeConverter> 執行都可以有自己的轉譯，其中構成有效的轉換字串，而且也可以使用或忽略當做參數傳遞的類型描述。 有一個關於文化特性和 XAML 類型轉換的重要考量。 XAML 完全支援使用可當地語系化的字串做為屬性值。 但不支援使用那個可當地語系化的字串做為具有特定文化特性需求的類型轉換器輸入，因為 XAML 屬性值的類型轉換器會使用 `en-US` 文化特性，來包含必然的固定語言剖析行為。 如需這種限制之設計原因的詳細資訊，請參閱 XAML 語言規格（[\[MS-xaml\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf)。  
  
 在文化特性可能是問題的範例中，某些文化特性會使用逗號做為數字的小數點分隔符號。 這將與許多 WPF XAML 類型轉換器所具備的行為相衝突，該行為是使用逗號做為分隔符號 (根據歷程的前置參照，例如，常見的 X,Y 格式或逗號分隔清單)。 即使是在局部的 XAML 中傳遞文化特性 (將 `Language` 或 `xml:lang` 設為 `sl-SI` 文化特性，以這種方式使用逗號代表小數點的文化特性範例)，還是無法解決問題。  
  
### <a name="implementing-convertfrom"></a>實作 ConvertFrom  
 若要可做為支援 XAML 的 <xref:System.ComponentModel.TypeConverter> 實作來重複使用，該轉換器的 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 方法必須接受字串做為 `value` 參數。 如果字串是有效的格式，而且可以由 <xref:System.ComponentModel.TypeConverter> 的實作為轉換，則傳回的物件必須支援轉換成屬性所預期的類型。 否則， <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 實作必須傳回 `null`。  
  
 每個 <xref:System.ComponentModel.TypeConverter> 執行都可以有自己的轉譯，其中構成有效的轉換字串，而且也可以使用或忽略當做參數傳遞的類型描述或文化特性內容。 不過，WPF XAML 處理可能不會在所有情況下都將值傳遞至類型描述內容，也可能不會根據 `xml:lang` 來傳遞文化特性。  
  
> [!NOTE]
> 請勿使用大括號字元 (特別是 {)做為字串格式的可能元素。 這些字元保留做為標記延伸序列的進入及結束。  
  
### <a name="implementing-convertto"></a>實作 ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 可能用於序列化支援。 透過自訂類型和其類型轉換器之 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 的序列化支援不是絕對需求。 不過，如果您正在實作控制項，或使用功能某部分的序列化或類別設計，則應該實作 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>。  
  
 若要當做支援 XAML 的 <xref:System.ComponentModel.TypeConverter> 實作為使用，該轉換器的 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 方法必須接受支援的類型實例（或值）做為 `value` 參數。 當 `destinationType` 參數是 <xref:System.String>類型時，傳回的物件必須能夠轉換成 <xref:System.String>。 傳回的字串必須代表 `value` 的序列化值。 在理想的情況下，您選擇的序列化格式應該能夠產生相同的值，如果該字串已傳遞至相同轉換器的 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 執行，則不會有顯著的資訊遺失。  
  
 如果無法序列化值，或轉換子不支援序列化，則 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 執行必須傳回 `null`，而且在此情況下允許擲回例外狀況。 但是，如果您擲回例外狀況，您應該回報無法使用該轉換做為 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 執行的一部分，以便先檢查 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 以避免發生例外狀況的最佳作法。  
  
 如果 `destinationType` 參數不是 <xref:System.String>類型，您可以選擇自己的轉換器處理。 一般來說，您會還原為基底執行處理，而在 basemost <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 會引發特定的例外狀況。  
  
### <a name="implementing-canconvertto"></a>實作 CanConvertTo  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 實作應該傳回類型 `true` 之 `destinationType` 的 <xref:System.String>，否則會進行基底實作。  
  
### <a name="implementing-canconvertfrom"></a>實作 CanConvertFrom  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 實作應該傳回類型 `true` 之 `sourceType` 的 <xref:System.String>，否則會進行基底實作。  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>套用 TypeConverterAttribute  
 為了讓您的自訂類型轉換器當做 XAML 處理器用於自訂類別的作用中類型轉換器，您必須將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至您的類別定義。 您透過屬性指定的 <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> 必須是您自訂類型轉換器的類型名稱。 如果已套用這個屬性，當 XAML 處理器處理屬性類型使用您自訂類別類型的值時，就可以輸入字串並傳回物件執行個體。  
  
 您也可以提供每個屬性的類型轉換器。 不需要將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至類別定義，而是將它套用至屬性定義（主要定義，而不是 `get`/`set` 中的執行）。 屬性的類型必須符合您自訂類型轉換器所處理的類型。 如果已套用這個屬性，則在 XAML 處理器處理該屬性的值時，可以處理輸入字串，並傳回物件執行個體。 如果您選擇使用 Microsoft .NET Framework 的屬性類型，或從無法控制類別定義且無法在該處套用 <xref:System.ComponentModel.TypeConverterAttribute> 的其他文件庫，則每個屬性的類型轉換器技術特別有用。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.TypeConverter>
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML 語法詳細資料](xaml-syntax-in-detail.md)
