---
title: 使用資料合同Jon序列化器實現獨立JSON序列化
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 36945f2d42f22ef3aa4f27bcbe403466f124a279
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184415"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>使用資料合同Jon序列化器實現獨立JSON序列化

> [!NOTE]
> 本文是關於<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>的。 對於大多數涉及序列化和反序列化 JSON 的方案，我們建議[在系統中使用 API。](../../../standard/serialization/system-text-json-overview.md)

JSON (JavaScript 物件標記法) 是專為在瀏覽器內的網頁上執行的 JavaScript 程式碼而設計的資料格式。 它是在 Windows 通信基礎 （WCF） 中創建的ASP.NET AJAX 服務所使用的預設資料格式。

此外，在未與 ASP.NET 整合的情況下建立 AJAX 服務時，也可以使用這個格式，在這種情況中，XML 是預設值，不過您也可以選擇 JSON。

最後，如果您需要 JSON 支援但不想建立 AJAX 服務，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 可讓您直接將 .NET 物件序列化為 JSON 資料，以及將這類資料還原序列化為 .NET 型別的執行個體。 有關如何執行此操作的說明，請參閱[如何：序列化和序列化 JSON 資料](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md)。

使用 JSON 時，相同的 .NET 型別會受到支援，不過有少數的例外情形，如同 <xref:System.Runtime.Serialization.DataContractSerializer> 所支援的一樣。 有關支援的類型的清單，請參閱[資料協定序列化器支援的類型](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)。 其中包括大部分的基本型別、大部分的陣列和集合型別，以及使用 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 的複雜型別。

## <a name="mapping-net-types-to-json-types"></a>將 .NET 型別對應至 JSON 型別

下表說明由序列化和還原序列化程序對應時，.NET 型別和 JSON/JavaScript 型別之間的對應關係。

|.NET 型別|JSON/JavaScript|注意|
|----------------|----------------------|-----------|
|所有數字型別，例如 <xref:System.Int32>、<xref:System.Decimal> 或 <xref:System.Double>|Number|`Double.NaN`、`Double.PositiveInfinity` 和 `Double.NegativeInfinity` 等特殊值不受支援，並且會造成無效的 JSON。|
|<xref:System.Enum>|Number|請參閱本主題稍後的＜列舉與 JSON＞。|
|<xref:System.Boolean>|Boolean|--|
|<xref:System.String>, <xref:System.Char>|String|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|String|JSON 中的這些類型的格式與 XML 格式相同（基本上，ISO 8601 持續時間格式為 TimeSpan，GUID 採用"12345678-ABCD-ABCD-ABCD-ABCD-ABCD-1234567890AB"格式，並且http://www.example.comURI 以其自然字串形式表示"""）。 有關準確資訊，請參閱[資料協定架構參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。|
|<xref:System.Xml.XmlQualifiedName>|String|格式為 "name:namespace" (第一個冒號前面的就是名稱)。 名稱或命名空間可能會遺失。 如果沒有命名空間，冒號也可以省略。|
|型別 <xref:System.Array> 的 <xref:System.Byte>|數字陣列|每個數字代表一個位元組值。|
|<xref:System.DateTime>|DateTime 或字串|請參閱本主題稍後的＜日期/時間與 JSON＞。|
|<xref:System.DateTimeOffset>|複雜類型|請參閱本主題稍後的＜日期/時間與 JSON＞。|
|XML 和 ADO.NET 型別 (<xref:System.Xml.XmlElement>、<br /><br /> <xref:System.Xml.Linq.XElement>. <xref:System.Xml.XmlNode> 的陣列、<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|請參閱本主題的＜XML 型別與 JSON＞一節。|
|<xref:System.DBNull>|空的複雜型別|--|
|集合、字典與陣列|Array|請參閱本主題的＜集合、字典與陣列＞一節。|
|複雜型別 (已套用 <xref:System.Runtime.Serialization.DataContractAttribute> 或 <xref:System.SerializableAttribute>)|複雜類型|資料成員成為 JavaScript 複雜類型的成員。|
|實作 <xref:System.Runtime.Serialization.ISerializable> 介面的複雜型別)|複雜類型|與其他複雜型別相同，但不支援某些 <xref:System.Runtime.Serialization.ISerializable> 型別，請參閱本主題的「進階資訊」一節中有關 ISerializable 支援的部分。|
|任何型別的 `Null` 值|Null|可為 Null 的型別也受支援，並且會以和不可為 Null 的型別相同的方式對應至 JSON。|

### <a name="enumerations-and-json"></a>列舉與 JSON

在 JSON 中，列舉成員值會被視為數字，它處理這些值的方式與資料合約不同。在資料合約中，這些值會包含為成員名稱。 有關資料協定處理的詳細資訊，請參閱[資料協定中的枚舉類型](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)。

- 例如，如果您具有 `public enum Color {red, green, blue, yellow, pink}`，則序列化 `yellow` 會產生數字 3，而不是字串 "yellow"。

- 所有 `enum` 成員都是可序列化的。 如果使用的話，<xref:System.Runtime.Serialization.EnumMemberAttribute> 和 <xref:System.NonSerializedAttribute> 屬性會被忽略。

- 您可以還原序列化不存在的 `enum` 值，例如，值 87 可以還原序列化為先前的 Color 列舉，即使沒有定義對應的色彩名稱亦然。

- `enum` 不是特殊旗標，且被視為和任何其他 `enum` 相同。

### <a name="datestimes-and-json"></a>日期/時間與 JSON

JSON 格式並未直接支援日期和時間。 然而，它們相當常用，因此，ASP.NET AJAX 為這些型別提供了特別支援。 使用 ASP.NET AJAX Proxy 時，.NET 中的 型別會完全對應至 JavaScript 中的  型別。

- 不使用 ASP.NET 時，<xref:System.DateTime> 型別在 JSON 中會以具有特殊格式的字串來表示，本主題的「進階資訊」一節中會加以說明。

- JSON 中的 <xref:System.DateTimeOffset> 將以複雜型別來表示：{"DateTime":dateTime,"OffsetMinutes":offsetMinutes}。 `offsetMinutes` 成員是與相關事件位置相關聯的格林威治時間 (GMT) 的本機時間位移，而格林威治時間現在也稱為 Coordinated Universal Time (UTC)。 `dateTime` 成員代表發生相關事件時的時間執行個體 (同樣地，當 ASP.NET AJAX 正在使用中時，它在 JavaScript 中會變成 `DateTime`，否則會變成字串)。 在序列化時，`dateTime` 成員永遠會序列化為 GMT。 因此，如果要描述紐約時間 3:00 AM，`dateTime` 會有 8:00 AM 的時間元件，而且 `offsetMinutes` 為 -300，即從 GMT 減去 300 分鐘或是 5 小時。

  > [!NOTE]
  > 在序列化為 JSON 時，<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 物件只會保存精確度到毫秒的資訊。 次毫秒值 (微/奈秒) 會在序列化期間遺失。

### <a name="xml-types-and-json"></a>XML 型別與 JSON

XML 型別成為 JSON 字串。

- 例如，如果 XElement 類型的資料成員"q"包含\<abc/>，則 JSON 是 {"q"："abc/>}。\<

- 還有一些指定如何包裝 XML 的特殊規則。如需詳細資訊，請參閱本主題稍後的「進階資訊」一節。

- 如果您要使用 ASP.NET AJAX 且不想在 JavaScript 中使用字串，希望改用 XML DOM，請在 上將  屬性設定為 XML，或在  上將  屬性設定為 XML。

### <a name="collections-dictionaries-and-arrays"></a>集合、字典與陣列

所有的集合、字典與陣列在 JSON 中都會以陣列來表示。

- JSON 表示法會忽略任何使用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 的自訂。

- 您不可以直接使用字典來搭配 JSON。 字典\<字串、物件>在 WCF 中可能不支援與其他 JSON 技術一樣。 例如，如果字典中 "abc" 是對應至 "xyz" 而 "def" 是對應至 42，則 JSON 表示法不是 {"abc":"xyz","def":42}，而是 [{"Key":"abc","Value":"xyz"},{"Key":"def","Value":42}]。

- 如果您希望直接使用 JSON (動態存取索引鍵和值，而不需預先定義嚴謹的合約)，可以選擇數個選項：

  - 請考慮使用[弱類型 JSON 序列化 （AJAX）](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md)示例。

  - 請考慮使用 <xref:System.Runtime.Serialization.ISerializable> 介面和還原序列化建構函式，這兩種機制可讓您分別在序列化和還原序列化時存取 JSON 索引鍵/值組，但不適用於部分信任案例中。

  - 請考慮使用[JSON 和 XML 之間的映射](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)，而不是使用序列化程式。

  - 序列化上下文中的*多態性*是指序列化預期其基類型派生類型的能力。 以多型方式使用集合時，例如，將集合指派至 <xref:System.Object> 時，有幾個 JSON 特定的特殊規則。 在本主題稍後的「進階資訊」一節中，將會更詳細地討論這個議題。

## <a name="additional-details"></a>其他詳細資料

### <a name="order-of-data-members"></a>資料成員的順序

使用 JSON 時，資料成員的順序並不重要。 特別是，即使設定 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>，仍然可以依照任何順序來還原序列化 JSON 資料。

### <a name="json-types"></a>JSON 型別

在還原序列化時，JSON 型別不必符合上述表格。 例如，`Int` 通常會對應至 JSON 數字，但是它也可以成功地從 JSON 字串還原序列化，只要該字串包含有效數字。 也就是說，只要有一個 `Int` 資料成員稱為 "q"，{"q":42} 和 {"q":"42"} 兩者皆為有效。

### <a name="polymorphism"></a>Polymorphism

多型序列化是由可序列化必須是基底型別之衍生型別的能力所組成。 WCF 支援 JSON 序列化，這與支援 XML 序列化的方式類似。 例如，`MyDerivedType`您可以序列化預期位置`MyBaseType`，也可以序列化`Int`預期位置。 `Object`

如果必須是基底型別，則在還原序列化衍生型別時可能會遺失型別資訊，除非您還原序列化複雜型別。 例如，如果序列化必須是 <xref:System.Uri> 的 <xref:System.Object>，則會產生 JSON 字串。 如果這個字串接著再還原序列化為 <xref:System.Object>，則會傳回 .NET <xref:System.String>。 還原序列化程式並不知道字串初始的型別為 <xref:System.Uri>。 一般而言，當必須是 <xref:System.Object> 時，所有的 JSON 字串都會還原序列化為 .NET 字串，並且所有用於序列化 .NET 集合、字典和陣列的 JSON 陣列都會還原序列化為 <xref:System.Array> 型別的 .NET <xref:System.Object>，不論實際的原始型別為何。 JSON 布林值會對應至 .NET <xref:System.Boolean>。 然而，當必須是 <xref:System.Object> 時，JSON 數字會還原序列化為 .NET <xref:System.Int32>、<xref:System.Decimal> 或 <xref:System.Double>，其中會自動選取最適合的型別。

在還原序列化為介面型別時，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 會將宣告型別視為物件來還原序列化。

在使用您自己的基底型別和衍生型別時，通常需要使用 <xref:System.Runtime.Serialization.KnownTypeAttribute>、<xref:System.ServiceModel.ServiceKnownTypeAttribute> 或相等的機制。 `Animal`例如，如果操作具有傳回值，並且它實際上返回 （派生自`Cat``Animal`） 的實例，則應將 的<xref:System.Runtime.Serialization.KnownTypeAttribute>實例應用於`Animal`該操作的類型或 ，<xref:System.ServiceModel.ServiceKnownTypeAttribute>並指定這些屬性中`Cat`的類型。 有關詳細資訊，請參閱[資料協定已知類型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。

如需多型序列化運作方式的詳細資訊，以及使用時必須遵守的一些限制說明，請參閱本主題稍後的「進階資訊」一節。

### <a name="versioning"></a>版本控制

在 JSON 中完全支援資料合約版本控制功能，包括 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面。 此外，在大部分的情況中，可能可以在一種格式中還原序列化型別 (例如 XML)，然後再序列化成另一種格式 (例如 JSON)，而且仍然保有 <xref:System.Runtime.Serialization.IExtensibleDataObject> 中的資料。 如需詳細資訊，請參閱[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。 請記住，JSON 並未循序，因此，任何順序資訊都會遺失。 此外，JSON 不支援多個具有相同索引鍵名稱的索引鍵/值組。 最後，<xref:System.Runtime.Serialization.IExtensibleDataObject> 上的所有作業原本就是多型的，也就是說，它們的衍生型別會指派給 <xref:System.Object> (所有型別的基底型別)。

## <a name="json-in-urls"></a>URL 中的 JSON

當以 HTTP GET 動詞命令來使用 ASP.NET AJAX 端點時 (使用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性)，傳入參數會出現在要求 URL 中而非訊息本文。 即使在請求 URL 中也支援 JSON，因此，如果您有一個`Int`操作，該操作採用稱為"數位`Person`"和稱為"p"的複雜類型，則 URL 可能類似于以下 URL。

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

如果您是使用 ASP.NET AJAX 指令碼管理員控制項與 Proxy 來呼叫服務，這個 URL 就會由 Proxy 自動產生且不會被看到。 JSON 無法在非 ASP.NET AJAX 端點的 URL 上使用。

## <a name="advanced-information"></a>進階資訊

### <a name="iserializable-support"></a>ISerializable 支援

#### <a name="supported-and-unsupported-iserializable-types"></a>支援和不支援的 ISerializable 型別

一般而言，當序列化/還原序列化 JSON 時，會完全支援實作 <xref:System.Runtime.Serialization.ISerializable> 介面的型別。 然而，其中有些型別 (包括一些 .NET Framework 型別) 的實作方式會讓 JSON 特定的序列化造成它們無法正確地還原序列化：

- 使用 <xref:System.Runtime.Serialization.ISerializable>，永遠無法預先知道個別資料成員的型別。 這導致多型情況與將型別還原序列化成物件很類似。 如前所述，這可能會導致遺失 JSON 中的型別資訊。 例如，在其 `enum` 實作中序列化 <xref:System.Runtime.Serialization.ISerializable> 並嘗試直接再還原序列化成 `enum` (沒有正確轉換) 的型別失敗，因為 `enum` 是使用 JSON 中的數字進行序列化，而 JSON 數字還原序列化成內建的 .NET 數字型別 (Int32、Decimal 或 Double)。 因此用於做為 `enum` 值的數字會遺失。

- 依賴其還原序列化建構函式中的還原序列化特定順序的 <xref:System.Runtime.Serialization.ISerializable> 型別可能也會無法還原序列化某些 JSON 資料，因為大部分的 JSON 序列化程式都不會保證任何特定順序。

#### <a name="factory-types"></a>處理站型別

雖然一般而言，在 JSON 中會支援 <xref:System.Runtime.Serialization.IObjectReference> 介面，但是不會支援任何需要「處理站型別」功能 (從與實作介面的型別不同的 <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> 型別傳回執行個體) 的型別。

### <a name="datetime-wire-format"></a>DateTime Wire 格式

<xref:System.DateTime> 值會以 "/Date(700000+0500)/" 的格式顯示為 JSON 字串，其中第一個數字 (範例中為 700000) 是 GMT 時區中毫秒的數字，自 1970 年 1 月 1 日午夜起的固定 (非日光節約時間) 時間。 該數字可能是負數，以代表較早的時間。 範例中組成 "+0500" 的部分是選擇性的，並指出時間的類型是 <xref:System.DateTimeKind.Local>，也就是說，應在還原序列化時轉換為本地時區。 如果沒有，時間便會還原序列化為 <xref:System.DateTimeKind.Utc>。 實際數字 (這個範例中為 "0500") 和其符號 (+ 或 -) 會被忽略。

當序列化 <xref:System.DateTime> 時，<xref:System.DateTimeKind.Local> 和 <xref:System.DateTimeKind.Unspecified> 時間是以位移寫入，而 <xref:System.DateTimeKind.Utc> 則不是。

ASP.NET AJAX 用戶端 JavaScript 程式碼會將此類字串自動轉換成 JavaScript `DateTime` 執行個體。 如果在 .NET 中有其他字串有不是 <xref:System.DateTime> 型別的類似格式，它們也會被轉換。

僅當"/"字元轉義時（即 JSON 看起來像"/Date（700000+0500）/"，\\\\並且出於此原因，WCF 的 JSON 編碼器（由 啟用<xref:System.ServiceModel.WebHttpBinding>）始終轉義為"/"字元。

### <a name="xml-in-json-strings"></a>JSON 字串中的 XML

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement> 是依現狀序列化，沒有包裝。 例如，包含<xref:System.Xml.XmlElement>\<abc/>類型的資料成員"x"表示如下：

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>XmlNode 的陣列

型別 <xref:System.Array> 的 <xref:System.Xml.XmlNode> 物件是包裝在型別的標準資料合約命名空間中稱為 ArrayOfXmlNode 的項目中。 如果 "x" 是陣列，在包含 "value" 和空白項目節點 "M" 的命名空間 "ns" 中包含屬性節點 "N"，表示如下所示。

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 在 XmlNode 陣列開頭的空白命名空間中的屬性 (在其他項目之前) 會不受支援。

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>IXmlSerializable 型別包括 XElement 和 DataSet

<xref:System.Runtime.Serialization.ISerializable> 型別分為「內容型別」、「DataSet 型別」和「項目型別」。 有關這些類型的定義，請參閱[資料協定 中的 XML 和ADO.NET類型](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)。

「內容」和「DataSet」型別的序列化類似前一節中所討論的 <xref:System.Array> 的 <xref:System.Xml.XmlNode> 物件。 它們會包裝在一個項目中，該項目的名稱和命名空間對應至所討論的型別的資料合約名稱和命名空間。

如 <xref:System.Xml.Linq.XElement> 等「項目」型別會依現狀進行序列化，類似本主題之前所討論的 <xref:System.Xml.XmlElement>。

### <a name="polymorphism"></a>Polymorphism

#### <a name="preserving-type-information"></a>保留型別資訊

如前所述，在 JSON 中支援多型有一些限制。 JavaScript 是弱型別語言，而型別身分識別通常不是問題。 然而，當使用 JSON 在強型別系統 (.NET) 和弱型別系統 (JavaScript) 之間進行通訊時，保留型別身分識別是很有用的。 例如，資料合約名稱為 "Square" 和 "Circle" 的型別衍生自資料合約名稱為 "Shape" 的型別。 如果 "Circle" 是從 .NET 傳送至 JavaScript，稍後再傳回至應該有 "Shape" 的 .NET 方法，讓 .NET 端知道所討論的物件原本是 "Circle" 會很有用，否則衍生型別的特定資訊 (例如，"Circle" 上的 "radius" 資料成員) 可能會遺失。

若要保留型別身分識別，在將複雜型別序列化至 JSON 時可以新增「型別提示」，還原序列化程式便可辨識提示並執行適當的動作。 "類型提示"是一個 JSON 鍵/值對，其鍵名稱\_\_為"類型"（兩個底線後跟單詞"type"）。 值是格式 "DataContractName:DataContractNamespace" (第一個冒號之前是名稱) 的 JSON 字串。 使用之前的範例，"Circle" 可以進行序列化，如下所示。

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

型別提示與 XML 結構描述執行個體標準所定義的 `xsi:type` 屬性十分類似，並且是在序列化/還原序列化 XML 時使用。

由於與類型提示\_\_的潛在衝突，禁止稱為"類型"的資料成員。

#### <a name="reducing-the-size-of-type-hints"></a>縮小型別提示的大小

為了減小 JSON 消息的大小，預設資料協定命名空間首碼`http://schemas.datacontract.org/2004/07/`（ ） 將替換為"*"字元。 （為了使此替換可逆，使用轉義規則：如果命名空間以"*"或""\\字元開頭，則附加它們與額外的""\\字元"。 因此，如果"圓"是 .NET 命名空間"MyApp.Shape"中的一種類型，則其預設資料協定`http://schemas.datacontract.org/2004/07/MyApp`命名空間為 。 Shapes 和 JSON 表示如下所示。

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

截斷 （#MyApp.Shape） 和完整（http://schemas.datacontract.org/2004/07/MyApp.Shapes)名稱在反序列化時都理解）。

#### <a name="type-hint-position-in-json-objects"></a>JSON 物件中的型別提示位置

請注意，型別提示必須最先出現在 JSON 表示中。 只有在這種情況中，索引鍵/值組的順序在 JSON 處理中才會十分重要。 例如，下列不是指定型別提示的有效方法。

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

WCF<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>和 ASP.NET AJAX 用戶端頁都始終首先發出類型提示。

#### <a name="type-hints-apply-only-to-complex-types"></a>型別提示只套用至複雜型別

非複雜型別是無法發出型別提示的。 例如，如果作業有 <xref:System.Object> 傳回型別但傳回 Circle，JSON 表示可以如稍早所示，並保留型別資訊。 然而，如果傳回 URI，JSON 表示就是字串，而用於代表 URI 的字串會遺失。 這不僅適用於基本型別，也適用於集合和陣列。

#### <a name="when-are-type-hints-emitted"></a>何時會發出型別提示

型別提示可能會大幅增加訊息大小 (改善這種情況的方法之一是盡量使用較短的資料合約命名空間)。 因此，下列規則會管理是否發出型別提示：

- 當使用 ASP.NET AJAX 時，即使沒有基底/衍生指派 (例如，即使 Circle 指派至 Circle)，只要可以，還是永遠會發出型別提示 (如果要完整啟用從弱型別 JSON 環境至強型別 .NET 環境的呼叫處理，而不會意外遺失資訊，這是必要的)。

- 如果使用沒有 ASP.NET 整合的 AJAX 服務，只有在有基底/衍生指派時，才會發出型別提示 - 也就是說，在 Circle 指派至 Shape 或 <xref:System.Object> 但不是在指派至 Circle 時發出。 這會提供正確實作 JavaScript 用戶端所需的最少必要資訊，因而增進效能，但無法防止設計錯誤的用戶端中的型別資訊遺失。 如果您要避免在用戶端上處理這個問題，請避免在伺服器上使用基底/衍生指派。

- 當使用 <xref:System.Runtime.Serialization.DataContractSerializer> 型別時，`alwaysEmitTypeInformation` 建構函式參數可讓您在前述兩種模式中做選擇，且預設為 "`false`" (只在有需要時發出型別提示)。

#### <a name="duplicate-data-member-names"></a>重複資料成員名稱

衍生型別資訊會和基底型別資訊一起存在相同的 JSON 物件中，且可能會以各種順序出現。 例如，`Shape`可以表示如下。

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

其中 Circle 可能會表示如下。

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

如果基`Shape`類型還包含名為""`radius`的資料成員，則會導致序列化（因為 JSON 物件不能具有重複按鍵名）和反序列化（因為不清楚"半徑"是否是指`Shape.radius`或`Circle.radius`）。 因此，通常並不建議在資料合約類別中使用「屬性隱藏」的概念 (基底和衍生類別上相同名稱的資料成員)，而實際上在 JSON 的案例中是禁止的。

#### <a name="polymorphism-and-ixmlserializable-types"></a>多型和 IXmlSerializable 型別

根據一般的資料合約規則，只要符合「已知型別」需求。<xref:System.Xml.Serialization.IXmlSerializable> 型別就可能會如往常般以多型方式指派給彼此。 然而，序列化 <xref:System.Xml.Serialization.IXmlSerializable> 型別以取代 <xref:System.Object> 會造成型別資訊遺失，因為結果是 JSON 字串。

#### <a name="polymorphism-and-certain-interface-types"></a>多型和特定介面型別

禁止序列化集合型別或實作 <xref:System.Xml.Serialization.IXmlSerializable> 的型別，其中應該有不是 <xref:System.Xml.Serialization.IXmlSerializable> (除了 <xref:System.Object>) 的非集合型別。 例如，稱為`IMyInterface``MyType`自訂介面和實現類型<xref:System.Collections.Generic.IEnumerable%601>`int`和`IMyInterface`的類型。 禁止從返回類型為`MyType``IMyInterface`的操作返回。 這是因為`MyType`必須序列化為 JSON 陣列，並且需要類型提示，並且如之前所述，您不能包含包含陣列的類型提示，只能包含複雜類型。

#### <a name="known-types-and-configuration"></a>已知型別和組態

<xref:System.Runtime.Serialization.DataContractSerializer> 也以相同的方法支援 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 所使用的所有已知型別機制。 兩個序列化器讀取相同的配置元素，[\<資料合同序列化器>](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)[\<系統.運行時.序列化>，](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)以發現通過設定檔添加的已知類型。

#### <a name="collections-assigned-to-object"></a>指派給物件的集合

指派給物件的集合的序列化方式就如同實作 的集合一般：如果是複雜型別，則為每一個項目都有型別提示的 JSON 陣列。 例如，<xref:System.Collections.Generic.List%601>`Shape`分配給的類型<xref:System.Object>如下所示。

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

當再還原序列化成 <xref:System.Object> 時：

- `Shape`必須位於"已知類型"清單中。 在<xref:System.Collections.Generic.List%601>已知類型`Shape`中具有類型不起作用。 請注意，在這種情況下，您不必在序列`Shape`化方面添加到已知類型 - 這是自動完成的。

- 集合被反序列化為包含<xref:System.Array><xref:System.Object>`Shape`實例的類型。

#### <a name="derived-collections-assigned-to-base-collections"></a>指派給基底集合的衍生集合

當將衍生集合指派給基底集合時，集合的序列化方式通常就如同基底型別的集合一般。 然而，如果無法將衍生集合的項目型別指派給基底集合的項目型別，便會擲回例外狀況。

#### <a name="type-hints-and-dictionaries"></a>型別提示和字典

當字典指派給 <xref:System.Object> 時，字典中每個索引鍵和值項目的處理方式都如同指派給 <xref:System.Object> 一般，並會取得型別提示。

當序列化字典型別時，包含 "Key" 和 "Value" 成員的 JSON 物件不受 `alwaysEmitTypeInformation` 設定的影響，且只有在前述集合規則需要時才包含型別提示。

### <a name="valid-json-key-names"></a>有效的 JSON 索引鍵名稱

序列化程式 XML 會編碼不是有效的 XML 名稱的索引鍵名稱。 例如，名稱為"123"的資料成員將\_具有編碼名稱，如"x0031\_\_x0032\_\_x0033"，\_因為"123"是不正確 XML 元素名稱（以數位開頭）。 有些在 XML 名稱中無效的國際字元集可能會引起類似的情況。 有關 XML 對 JSON 處理的這種影響的說明，請參閱[JSON 和 XML 之間的映射](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)。

## <a name="see-also"></a>另請參閱

- [JSON 和其他資料傳輸格式的支援](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
