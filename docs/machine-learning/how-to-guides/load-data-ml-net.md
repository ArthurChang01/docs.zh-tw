---
title: 從檔案和其他來源載入資料
description: Learn how to load data for processing and training into ML.NET using the API. Data is stored in files, databases, JSON, XML or in-memory collections.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344747"
---
# <a name="load-data-from-files-and-other-sources"></a>從檔案和其他來源載入資料

Learn how to load data for processing and training into ML.NET using the API. 資料原先是儲存在檔案或其他資料來源中，例如資料庫、JSON、XML 或記憶體內部集合。

If you're using Model Builder, see [Load training data into Model Builder](load-data-model-builder.md).

## <a name="create-the-data-model"></a>建立資料模型

ML.NET 可讓您透過類別定義資料模型。 例如，假設有下列的輸入資料：

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

建立資料模型以表示以下的程式碼片段：

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a>使用資料行屬性標註資料模型

屬性可提供 ML.NET 更多關於資料模型和資料來源的資訊。

[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 屬性會指定您屬性的資料行索引。

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 只有在從檔案載入資料時才需要。

將資料行作為以下項目載入：

- 個別資料行，像是 `HousingData` 類別中的 `Size` 和 `CurrentPrices`。
- 以類似 `HousingData` 類別中 `HistoricalPrices` 的向量形式，一次載入多個資料行。

若您擁有向量屬性，請將 [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 屬性套用到您資料模型中的屬性。 請務必注意，向量中的所有項目都必須是相同類型。 將資料行保持分離可讓您更輕易且具備彈性地進行特徵工程，但針對極為大量的資料行，在每一個資料行上進行作業會影響定型速度。

ML.NET 會透過資料行名稱運作。 若您想要將資料行名稱變更為屬性名稱之外的名稱，請使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性。 在建立記憶體內部物件時，您仍會使用屬性名稱建立物件。 但是，針對資料處理和建置機器學習模型，ML.NET 會使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性中提供的值來覆寫及參考屬性。

## <a name="load-data-from-a-single-file"></a>從單一檔案載入資料

若要從檔案載入資料，請搭配要載入其資料的資料模型使用 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) 方法。 因為 `separatorChar` 參數根據預設會以 Tab 鍵分隔，您可以視需要為您的資料檔案變更它。 若您的檔案擁有標頭，請將 `hasHeader` 參數設為 `true` 來忽略檔案中的第一行，並從第二行開始載入資料。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>從多個檔案載入資料

您的資料儲存在多個檔案，只要資料結構描述相同，ML.NET 可讓您將資料載入會在相同目錄中的多個檔案或多個目錄。

### <a name="load-from-files-in-a-single-directory"></a>從單一目錄中的檔案載入

當您所有的資料檔案都位於相同目錄時，請在 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) 方法中使用萬用字元。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>載入多個目錄中的檔案

若要從多個目錄載入資料，請使用 [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) 方法來建立 [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)。 然後，請使用 [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) 方法並指定個別檔案路徑 (無法使用萬用字元)。

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>Load data from a relational database

ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.

> [!NOTE]
> To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.

Given a database with a table named `House` and the following schema:

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

資料可由 `HouseData` 等類別建立模型。

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Then, inside of your application, create a `DatabaseLoader`.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance. This sample uses a LocalDB SQL Server database with a file path. However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType). The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms. In this sample, the `NumBed` column is an integer in the database. Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType). Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.

Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>從其他來源載入資料

除了載入儲存在檔案中的資料，ML.NET 支援從其他來源載入資料，其中包含但不限於：

- 記憶體內集合
- JSON/XML

請注意，當使用串流來源時，ML.NET 預期輸入的形式為記憶體內部集合。 因此，當使用像是 JSON/XML 等來源時，請務必將資料格式化成記憶體內部集合。

假設有下列記憶體內部集合：

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

請使用 [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 方法將記憶體內部集合載入 [`IDataView`](xref:Microsoft.ML.IDataView)：

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) 假設它載入的 [`IEnumerable`](xref:System.Collections.IEnumerable) 是安全執行緒。

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>後續步驟

- To clean or otherwise process data, see [Prepare data for building a model](prepare-data-ml-net.md).
- When you're ready to build a model, see [Train and evaluate a model](train-machine-learning-model-ml-net.md).
