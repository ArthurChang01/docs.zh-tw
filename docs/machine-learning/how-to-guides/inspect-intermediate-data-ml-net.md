---
title: 在 ML.NET 處理期間檢查中繼資料
description: 了解如何在 ML.NET 中，於 ML.NET 機器學習服務管線載入、處理和模型定型步驟期間檢查中繼資料。
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977094"
---
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="39dd6-103">在處理期間檢查中繼資料</span><span class="sxs-lookup"><span data-stu-id="39dd6-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="39dd6-104">了解如何在 ML.NET 中，於載入、處理和模型定型步驟期間檢查中繼資料。</span><span class="sxs-lookup"><span data-stu-id="39dd6-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="39dd6-105">中繼資料是機器學習服務管線中每個階段的輸出。</span><span class="sxs-lookup"><span data-stu-id="39dd6-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="39dd6-106">您可以在 ML.NET 中透過各種方式檢查與以下內容相似且會載入 [`IDataView`](xref:Microsoft.ML.IDataView) 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="39dd6-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="39dd6-107">將 IDataView 轉換成 IEnumerable</span><span class="sxs-lookup"><span data-stu-id="39dd6-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="39dd6-108">其中一個檢查 [`IDataView`](xref:Microsoft.ML.IDataView) 最快速的方式便是將它轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)。</span><span class="sxs-lookup"><span data-stu-id="39dd6-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="39dd6-109">若要將 [`IDataView`](xref:Microsoft.ML.IDataView) 轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)，請使用 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 方法。</span><span class="sxs-lookup"><span data-stu-id="39dd6-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

<span data-ttu-id="39dd6-110">若要最佳化效能，請將 `reuseRowObject` 設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="39dd6-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="39dd6-111">如此會使用目前資料列的資料，在評估時才延遲填入相同的物件，而非為資料集中的每個資料列建立新物件。</span><span class="sxs-lookup"><span data-stu-id="39dd6-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

```csharp
// Create an IEnumerable of HousingData objects from IDataView
IEnumerable<HousingData> housingDataEnumerable =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: true);

// Iterate over each row
foreach (HousingData row in housingDataEnumerable)
{
    // Do something (print out Size property) with current Housing Data object being evaluated
    Console.WriteLine(row.Size);
}
```

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="39dd6-112">使用 IEnumerable 存取特定索引</span><span class="sxs-lookup"><span data-stu-id="39dd6-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="39dd6-113">若您只需要存取一部分的資料或特定索引，請使用 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)，並將 `reuseRowObject` 參數的值設為 `false`，為資料集中所要求的每個資料列建立新物件。</span><span class="sxs-lookup"><span data-stu-id="39dd6-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="39dd6-114">接著，將 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 轉換成陣列或清單。</span><span class="sxs-lookup"><span data-stu-id="39dd6-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="39dd6-115">將 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 的結果轉換成陣列或清單，會將所有要求的 [`IDataView`](xref:Microsoft.ML.IDataView) 資料列載入記憶體，而這可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="39dd6-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="39dd6-116">一旦所有集合都已建立完成，您便可以在資料上執行作業。</span><span class="sxs-lookup"><span data-stu-id="39dd6-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="39dd6-117">以下程式碼片段會擷取資料集中的前三個資料列，並計算目前的平均價格。</span><span class="sxs-lookup"><span data-stu-id="39dd6-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

```csharp
// Create an Array of HousingData objects from IDataView
HousingData[] housingDataArray =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: false)
        .Take(3)
        .ToArray();

// Calculate Average CurrentPrice of First Three Elements
HousingData firstRow = housingDataArray[0];
HousingData secondRow = housingDataArray[1];
HousingData thirdRow = housingDataArray[2];
float averageCurrentPrice = (firstRow.CurrentPrice + secondRow.CurrentPrice + thirdRow.CurrentPrice) / 3;
```

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="39dd6-118">檢查單一資料行中的值</span><span class="sxs-lookup"><span data-stu-id="39dd6-118">Inspect values in a single column</span></span>

<span data-ttu-id="39dd6-119">在模型建置流程的任何一個時間點，[`IDataView`](xref:Microsoft.ML.IDataView) 單一資料行中的值可透過使用 [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) 方法進行存取。</span><span class="sxs-lookup"><span data-stu-id="39dd6-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="39dd6-120">[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) 方法會將單一資料行中的所有值作為 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) 傳回。</span><span class="sxs-lookup"><span data-stu-id="39dd6-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="39dd6-121">一次檢查一列 IDataView 值</span><span class="sxs-lookup"><span data-stu-id="39dd6-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="39dd6-122">[`IDataView`](xref:Microsoft.ML.IDataView) 會延遲評估。</span><span class="sxs-lookup"><span data-stu-id="39dd6-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="39dd6-123">若要逐一查看 [`IDataView`](xref:Microsoft.ML.IDataView)，而不將其轉換成 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)(如本文件先前章節所示範)，請使用 [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) 方法並將您 [`IDataView`](xref:Microsoft.ML.IDataView) 的 [DataViewSchema](xref:Microsoft.ML.DataViewSchema) 作為參數傳遞，來建立 [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor)。</span><span class="sxs-lookup"><span data-stu-id="39dd6-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="39dd6-124">然後，若要逐一查看資料列，請使用 [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) 指標方法，搭配 [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) 委派來從每個資料行擷取個別的值。</span><span class="sxs-lookup"><span data-stu-id="39dd6-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39dd6-125">基於效能考量，ML.NET 中的向量會使用 [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601)，而非原生集合類型 (即 `Vector`、`float[]` 等)。</span><span class="sxs-lookup"><span data-stu-id="39dd6-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span>

```csharp
// Get DataViewSchema of IDataView
DataViewSchema columns = data.Schema;

// Create DataViewCursor
using (DataViewRowCursor cursor = data.GetRowCursor(columns))
{
    // Define variables where extracted values will be stored to
    float size = default;
    VBuffer<float> historicalPrices = default;
    float currentPrice = default;

    // Define delegates for extracting values from columns
    ValueGetter<float> sizeDelegate = cursor.GetGetter<float>(columns[0]);
    ValueGetter<VBuffer<float>> historicalPriceDelegate = cursor.GetGetter<VBuffer<float>>(columns[1]);
    ValueGetter<float> currentPriceDelegate = cursor.GetGetter<float>(columns[2]);

    // Iterate over each row
    while (cursor.MoveNext())
    {
        //Get values from respective columns
        sizeDelegate.Invoke(ref size);
        historicalPriceDelegate.Invoke(ref historicalPrices);
        currentPriceDelegate.Invoke(ref currentPrice);
    }
}
```

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="39dd6-126">預覽預先處理結果或針對資料子集的定型結果</span><span class="sxs-lookup"><span data-stu-id="39dd6-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="39dd6-127">請不要在生產程式碼中使用 `Preview`，因為它旨在用於偵錯，可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="39dd6-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="39dd6-128">模型建置流程是實驗性且反覆性的。</span><span class="sxs-lookup"><span data-stu-id="39dd6-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="39dd6-129">若要預覽預先處理之後或針對資料子集定型機器學習模型之後資料的結果，請使用 [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) 方法，該方法會傳回 [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview)。</span><span class="sxs-lookup"><span data-stu-id="39dd6-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="39dd6-130">結果是一個具備 `ColumnView` 和 `RowView` 屬性的物件，這兩個屬性都是 [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)，且包含特定資料行或資料列中的值。</span><span class="sxs-lookup"><span data-stu-id="39dd6-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="39dd6-131">使用 `maxRows` 參數指定要套用轉換的資料列數。</span><span class="sxs-lookup"><span data-stu-id="39dd6-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![資料偵錯工具預覽物件](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="39dd6-133">檢查 [`IDataView`](xref:Microsoft.ML.IDataView) 的結果看起來會與下列內容相似：</span><span class="sxs-lookup"><span data-stu-id="39dd6-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![資料偵錯工具預覽資料列檢視](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
