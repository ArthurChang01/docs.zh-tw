---
title: 從 XML 載入資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151061"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="17595-102">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="17595-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="17595-103">可以從 XML 資料流或文件建立 ADO.NET <xref:System.Data.DataSet> 的內容。</span><span class="sxs-lookup"><span data-stu-id="17595-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="17595-104">此外，使用 .NET Framework 可讓您在決定從 XML 載入何種資訊，以及如何建立 <xref:System.Data.DataSet> 的結構描述或關聯式結構時，擁有相當大的彈性。</span><span class="sxs-lookup"><span data-stu-id="17595-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="17595-105">要用<xref:System.Data.DataSet>XML 的資料填充 ， 請使用<xref:System.Data.DataSet>物件的**ReadXml**方法。</span><span class="sxs-lookup"><span data-stu-id="17595-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="17595-106">**ReadXml**方法從檔、流或**XmlReader**讀取，並將 XML 的源加上可選的**XmlReadMode**參數作為參數。</span><span class="sxs-lookup"><span data-stu-id="17595-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="17595-107">有關**XmlReader**的詳細資訊，請參閱[使用 XmlTextReader 讀取 XML 資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="17595-107">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="17595-108">**ReadXml**方法讀取 XML 流或文檔的內容，並<xref:System.Data.DataSet>載入資料。</span><span class="sxs-lookup"><span data-stu-id="17595-108">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="17595-109">它還將根據指定的**XmlReadMode**以及關係<xref:System.Data.DataSet>架構是否存在創建 的關係架構。</span><span class="sxs-lookup"><span data-stu-id="17595-109">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="17595-110">下表描述了**XmlReadMode**參數的選項。</span><span class="sxs-lookup"><span data-stu-id="17595-110">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="17595-111">選項</span><span class="sxs-lookup"><span data-stu-id="17595-111">Option</span></span>|<span data-ttu-id="17595-112">描述</span><span class="sxs-lookup"><span data-stu-id="17595-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="17595-113">**Auto**</span><span class="sxs-lookup"><span data-stu-id="17595-113">**Auto**</span></span>|<span data-ttu-id="17595-114">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="17595-114">This is the default.</span></span> <span data-ttu-id="17595-115">檢查 XML 並依下列順序選擇最適當的選項：</span><span class="sxs-lookup"><span data-stu-id="17595-115">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="17595-116">- 如果 XML 是 DiffGram，則使用**DiffGram。**</span><span class="sxs-lookup"><span data-stu-id="17595-116">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="17595-117">- 如果<xref:System.Data.DataSet>包含架構或 XML 包含內聯架構，則使用**ReadSchema。**</span><span class="sxs-lookup"><span data-stu-id="17595-117">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="17595-118">- 如果<xref:System.Data.DataSet>不包含架構，並且 XML 不包含內聯架構，則使用**InferSchema。**</span><span class="sxs-lookup"><span data-stu-id="17595-118">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="17595-119">如果您知道正在讀取的 XML 的格式，建議您設置顯式**XmlReadMode，** 而不是接受**自動**預設值。</span><span class="sxs-lookup"><span data-stu-id="17595-119">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="17595-120">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="17595-120">**ReadSchema**</span></span>|<span data-ttu-id="17595-121">讀取任何內嵌結構描述，並載入資料和結構描述。</span><span class="sxs-lookup"><span data-stu-id="17595-121">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="17595-122">如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將新資料表從內嵌結構描述加入 <xref:System.Data.DataSet> 的現有結構描述中。</span><span class="sxs-lookup"><span data-stu-id="17595-122">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="17595-123">如果內嵌結構描述中的任何資料表已經存在於 <xref:System.Data.DataSet> 中，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="17595-123">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="17595-124">您將無法使用**XmlReadMode.ReadSchema**修改現有表的架構。</span><span class="sxs-lookup"><span data-stu-id="17595-124">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="17595-125">如果 <xref:System.Data.DataSet> 不包含結構描述，且沒有內嵌結構描述，則不會讀取任何資料。</span><span class="sxs-lookup"><span data-stu-id="17595-125">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="17595-126">內嵌結構描述可使用 XML 結構描述定義語言 (XSD) 的結構描述來定義。</span><span class="sxs-lookup"><span data-stu-id="17595-126">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="17595-127">有關將內聯架構編寫為 XML 架構的詳細資訊，請參閱[從 XML 架構 （XSD） 派生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="17595-127">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="17595-128">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="17595-128">**IgnoreSchema**</span></span>|<span data-ttu-id="17595-129">忽略任何內嵌結構描述，並將資料載入現有的 <xref:System.Data.DataSet> 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="17595-129">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="17595-130">任何與現有結構描述不相符的資料會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="17595-130">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="17595-131">如果 <xref:System.Data.DataSet> 中沒有結構描述，則不會載入任何資料。</span><span class="sxs-lookup"><span data-stu-id="17595-131">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="17595-132">如果資料是 DiffGram，**則忽略架構**具有與**DiffGram**相同的功能 *。*</span><span class="sxs-lookup"><span data-stu-id="17595-132">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="17595-133">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="17595-133">**InferSchema**</span></span>|<span data-ttu-id="17595-134">忽略任何內嵌結構描述，並推斷每個 XML 資料結構的結構描述，然後載入資料。</span><span class="sxs-lookup"><span data-stu-id="17595-134">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="17595-135">如果 <xref:System.Data.DataSet> 已經包含結構描述，則會將資料行加入現有的資料表來擴充目前的結構描述。</span><span class="sxs-lookup"><span data-stu-id="17595-135">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="17595-136">如果沒有現有的資料表，則不會加入額外的資料表。</span><span class="sxs-lookup"><span data-stu-id="17595-136">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="17595-137">如果推斷資料表已經存在但使用不同的命名空間，或者任何推斷的資料行與現有資料行衝突，便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="17595-137">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="17595-138">有關**ReadXmlSchema**如何從 XML 文檔中推斷架構的詳細資訊，請參閱[從 XML 推斷 DataSet 關聯式結構](inferring-dataset-relational-structure-from-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="17595-138">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="17595-139">**迪夫格拉姆**</span><span class="sxs-lookup"><span data-stu-id="17595-139">**DiffGram**</span></span>|<span data-ttu-id="17595-140">讀取 DiffGram 並將資料加入目前的結構描述。</span><span class="sxs-lookup"><span data-stu-id="17595-140">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="17595-141">**DiffGram**將新行與唯一識別碼值匹配的現有行合併。</span><span class="sxs-lookup"><span data-stu-id="17595-141">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="17595-142">請參閱這個主題結尾處＜從 XML 合併資料＞。</span><span class="sxs-lookup"><span data-stu-id="17595-142">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="17595-143">有關差異圖的更多資訊，請參閱[差異圖](diffgrams.md)。</span><span class="sxs-lookup"><span data-stu-id="17595-143">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="17595-144">**片段**</span><span class="sxs-lookup"><span data-stu-id="17595-144">**Fragment**</span></span>|<span data-ttu-id="17595-145">繼續讀取多個 XML 片段，直到到達資料流末。</span><span class="sxs-lookup"><span data-stu-id="17595-145">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="17595-146">與 <xref:System.Data.DataSet> 結構描述相符的片段會附加至適當的資料表。</span><span class="sxs-lookup"><span data-stu-id="17595-146">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="17595-147">與 <xref:System.Data.DataSet> 結構描述不相符的片段則會捨棄。</span><span class="sxs-lookup"><span data-stu-id="17595-147">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="17595-148">如果將**XmlReader**傳遞給將**XmlReader**定位到 XML 文檔中的一部分，**則 ReadXml**將讀取到下一個元素節點，並將其視為根項目，唯讀取到元素節點結束。</span><span class="sxs-lookup"><span data-stu-id="17595-148">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="17595-149">如果指定**XmlReadMode.片段**，則不適用。</span><span class="sxs-lookup"><span data-stu-id="17595-149">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="17595-150">DTD 實體</span><span class="sxs-lookup"><span data-stu-id="17595-150">DTD Entities</span></span>  
 <span data-ttu-id="17595-151">如果 XML 包含在文件類型定義 （DTD） 架構中定義的實體），則如果嘗試<xref:System.Data.DataSet>通過將檔案名、流或非驗證**XmlReader**傳遞到**ReadXml**來載入 ，將引發異常。</span><span class="sxs-lookup"><span data-stu-id="17595-151">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="17595-152">相反，您必須創建一個**Xml 驗證讀取器**，其中**實體處理**設置為**實體處理.展開實體**，並將**您的 Xml 驗證讀取器**傳遞給**ReadXml**。</span><span class="sxs-lookup"><span data-stu-id="17595-152">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="17595-153">在 讀取 之前 **，XmlValidingReader**將展開實體<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="17595-153">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="17595-154">下列程式碼範例顯示如何從 XML 資料流載入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="17595-154">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="17595-155">第一個示例顯示檔案名傳遞給**ReadXml**方法。</span><span class="sxs-lookup"><span data-stu-id="17595-155">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="17595-156">第二個範例顯示內含使用 <xref:System.IO.StringReader> 所載入之 XML 的字串。</span><span class="sxs-lookup"><span data-stu-id="17595-156">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
> <span data-ttu-id="17595-157">如果調用**ReadXml**載入非常大的檔，則可能會遇到性能降低的問題。</span><span class="sxs-lookup"><span data-stu-id="17595-157">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="17595-158">為了確保**ReadXml**在大型檔中的最佳性能，請調用 中<xref:System.Data.DataTable.BeginLoadData%2A>每個表<xref:System.Data.DataSet>的方法，然後調用**ReadXml**。</span><span class="sxs-lookup"><span data-stu-id="17595-158">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="17595-159">最後再針對 <xref:System.Data.DataTable.EndLoadData%2A> 的每個資料表呼叫 <xref:System.Data.DataSet> (如下列範例所示)。</span><span class="sxs-lookup"><span data-stu-id="17595-159">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
> <span data-ttu-id="17595-160">如果您的<xref:System.Data.DataSet>XSD 架構包含**目標命名空間**，則資料可能無法讀取，並且在調用**ReadXml**以載入<xref:System.Data.DataSet>包含沒有限定命名空間的元素時可能會遇到異常。</span><span class="sxs-lookup"><span data-stu-id="17595-160">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="17595-161">在這種情況下，要讀取非限定元素，請將**元素FormDefault**設置為 XSD 架構中的"合格"。</span><span class="sxs-lookup"><span data-stu-id="17595-161">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="17595-162">例如：</span><span class="sxs-lookup"><span data-stu-id="17595-162">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="17595-163">從 XML 合併資料</span><span class="sxs-lookup"><span data-stu-id="17595-163">Merging Data from XML</span></span>  
 <span data-ttu-id="17595-164">如果 <xref:System.Data.DataSet> 已經包含資料，則會將 XML 的新資料加入 <xref:System.Data.DataSet> 中已出現的資料中。</span><span class="sxs-lookup"><span data-stu-id="17595-164">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="17595-165">**ReadXml**不會從 XML 合併到<xref:System.Data.DataSet>具有匹配主鍵的任何行資訊中。</span><span class="sxs-lookup"><span data-stu-id="17595-165">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="17595-166">要用 XML 中的新資訊覆蓋現有行資訊，請使用**ReadXml**創建新<xref:System.Data.DataSet>的<xref:System.Data.DataSet.Merge%2A>，然後將<xref:System.Data.DataSet>新資訊寫入<xref:System.Data.DataSet>現有 。</span><span class="sxs-lookup"><span data-stu-id="17595-166">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="17595-167">請注意，使用**ReadXML**使用**DiffGram**的**XmlReadMode**載入 DiffGram 將合併具有相同唯一識別碼的行。</span><span class="sxs-lookup"><span data-stu-id="17595-167">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17595-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17595-168">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="17595-169">在資料集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="17595-169">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="17595-170">DiffGram</span><span class="sxs-lookup"><span data-stu-id="17595-170">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="17595-171">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="17595-171">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="17595-172">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="17595-172">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="17595-173">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="17595-173">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="17595-174">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="17595-174">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="17595-175">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="17595-175">[ADO.NET Overview](../ado-net-overview.md)</span></span>
