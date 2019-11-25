---
title: 準備資料以建置模型
description: 了解如何在 ML.NET 中使用轉換來操縱及準備資料，以進行額外的處理或模型建置。
author: luisquintanilla
ms.author: luquinta
ms.date: 09/11/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: e9bfad4724b353b0f3bfc615a40f1d72b80a2cd4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976971"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="d6d6e-103">準備資料以建置模型</span><span class="sxs-lookup"><span data-stu-id="d6d6e-103">Prepare data for building a model</span></span>

<span data-ttu-id="d6d6e-104">了解如何使用 ML.NET 準備資料，以進行額外的處理或建置模型。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="d6d6e-105">資料通常都是未經處理且疏鬆的。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="d6d6e-106">ML.NET 機器學習演算法會預期輸入或特徵會在單一數值向量中。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="d6d6e-107">同樣地，要預測的值（標籤）（特別是當它的類別資料）必須經過編碼。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="d6d6e-108">因此，資料準備的其中一個目標就是將資料轉換成 ML.NET 演算法所預期格式。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="d6d6e-109">篩選資料</span><span class="sxs-lookup"><span data-stu-id="d6d6e-109">Filter data</span></span>

<span data-ttu-id="d6d6e-110">有時候，並非資料集中的所有資料都與分析有關。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="d6d6e-111">其中一個移除無關資料的方法便是篩選。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="d6d6e-112">[`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) 包含一組篩選作業，可接受一個包含所有資料的 [`IDataView`](xref:Microsoft.ML.IDataView)，並傳回僅包含相關資料的 [IDataView](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="d6d6e-113">請務必注意，因為篩選作業並非和 [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog) 中項目相似的 [`IEstimator`](xref:Microsoft.ML.IEstimator%601) 或 [`ITransformer`](xref:Microsoft.ML.ITransformer)，它們無法作為 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) 或 [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) 資料準備管線的一部分包含在其中。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="d6d6e-114">使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：</span><span class="sxs-lookup"><span data-stu-id="d6d6e-114">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="d6d6e-115">若要根據資料行的值篩選資料，請使用 [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) 方法。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="d6d6e-116">以上範例會擷取資料集中價格介於 200000 及 1000000 之間的資料列。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="d6d6e-117">套用此篩選的結果只會傳回資料中最後兩個資料列，並排除第一個資料列，因為其價格為 100000，而非介於指定的範圍。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="d6d6e-118">取代遺漏值</span><span class="sxs-lookup"><span data-stu-id="d6d6e-118">Replace missing values</span></span>

<span data-ttu-id="d6d6e-119">遺漏值在資料集中經常出現。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="d6d6e-120">其中一種處理遺漏值的方式是若資料中存在任何或其他有意義值 (例如平均數)，則將它們取代成指定類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="d6d6e-121">使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：</span><span class="sxs-lookup"><span data-stu-id="d6d6e-121">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=float.NaN
    }
};
```

<span data-ttu-id="d6d6e-122">請注意我們清單中的最後一個項目針對 `Price` 具有遺漏值。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="d6d6e-123">若要取代 `Price` 資料行中的遺漏值，請使用 [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) 方法來填入該遺漏值。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6d6e-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) 只能針對數字資料運作。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="d6d6e-125">ML.NET 支援各種[取代模式](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="d6d6e-126">以上範例使用 `Mean` 取代模式，這種模式會使用資料行的平均值填入遺漏值。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-126">The sample above uses the `Mean` replacement mode which will fill in the missing value with that column's average value.</span></span> <span data-ttu-id="d6d6e-127">取代之結果會將 200,000 填入我們資料中最後一個項目的 `Price` 屬性，因為它是 100,000 和 300,000 的平均。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="d6d6e-128">使用正規器</span><span class="sxs-lookup"><span data-stu-id="d6d6e-128">Use normalizers</span></span>

<span data-ttu-id="d6d6e-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) (正規化) 是一種資料處理技術，用來標準化規格不相同的特徵，協助演算法更快收斂。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to standardize features that are not on the same scale which helps algorithms converge faster.</span></span> <span data-ttu-id="d6d6e-130">例如，年齡值的範圍和收入值的範圍差異便非常大，因為年齡的範圍通常介於 0 到 100，收入的範圍則涵蓋零到數千不等。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-130">For example, the ranges for values like age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="d6d6e-131">請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及正規化轉換的描述。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="d6d6e-132">最小-最大正規化</span><span class="sxs-lookup"><span data-stu-id="d6d6e-132">Min-Max normalization</span></span>

<span data-ttu-id="d6d6e-133">使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：</span><span class="sxs-lookup"><span data-stu-id="d6d6e-133">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms = 2f,
        Price = 200000f
    },
    new HomeData
    {
        NumberOfBedrooms = 1f,
        Price = 100000f
    }
};
```

<span data-ttu-id="d6d6e-134">正規化可以套用至具有單一數值和向量的資料行。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="d6d6e-135">搭配 [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) 方法使用最小值和最大值正規化將 `Price` 資料行中的資料正規化。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="d6d6e-136">原始的價格值 `[200000,100000]` 會使用 `MinMax` 正規化公式轉換成 `[ 1, 0.5 ]`，該公式的輸出值範圍介於 0 到 1。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula which generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="d6d6e-137">資料收納</span><span class="sxs-lookup"><span data-stu-id="d6d6e-137">Binning</span></span>

<span data-ttu-id="d6d6e-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) (資料收納) 會將連續值轉換成輸入的離散表示。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="d6d6e-139">例如，假設您的其中一個特徵為年齡。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="d6d6e-140">資料收納會建立該值的範圍，而非使用實際的年齡值。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="d6d6e-141">其中一個收納可能是 0 到 18，另一收納則可能是 19 到 35 等。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="d6d6e-142">使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：</span><span class="sxs-lookup"><span data-stu-id="d6d6e-142">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="d6d6e-143">使用 [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) 方法將資料正規化成收納。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) method.</span></span> <span data-ttu-id="d6d6e-144">`maximumBinCount` 參數可讓您指定分類資料所需要的收納數。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="d6d6e-145">在此範例中，資料會放入兩個收納。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="d6d6e-146">資料收納的結果會建立 `[0,200000,Infinity]` 的收納界限。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="d6d6e-147">因此，結果產生的收納將會是 `[0,1,1]`，因為第一個觀察到的結果介於 0 到 200000，其他的則大於 200000，但小於無限大。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="d6d6e-148">使用類別資料</span><span class="sxs-lookup"><span data-stu-id="d6d6e-148">Work with categorical data</span></span>

<span data-ttu-id="d6d6e-149">非數字類別資料需要轉換成數字，才能用來建置機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-149">Non-numeric categorical data needs to be converted to a number before being used to build a machine learning model.</span></span>

<span data-ttu-id="d6d6e-150">使用下列輸入資料，這些資料會載入 [`IDataView`](xref:Microsoft.ML.IDataView)：</span><span class="sxs-lookup"><span data-stu-id="d6d6e-150">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
CarData[] cars = new CarData[]
{
    new CarData
    {
        Color="Red",
        VehicleType="SUV"
    },
    new CarData
    {
        Color="Blue",
        VehicleType="Sedan"
    },
    new CarData
    {
        Color="Black",
        VehicleType="SUV"
    }
};
```

<span data-ttu-id="d6d6e-151">類別 `VehicleType` 屬性可使用 [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) 方法轉換成數字。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-151">The categorical `VehicleType` property can be converted into a number using the [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) method.</span></span>

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

<span data-ttu-id="d6d6e-152">產生的轉換會將 `VehicleType` 文字值轉換成數字。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-152">The resulting transform converts the text value of `VehicleType` to a number.</span></span> <span data-ttu-id="d6d6e-153">`VehicleType` 資料行中的項目會在套用轉換時成為下列項目：</span><span class="sxs-lookup"><span data-stu-id="d6d6e-153">The entries in the `VehicleType` column become the following when the transform is applied:</span></span>

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a><span data-ttu-id="d6d6e-154">使用文字資料</span><span class="sxs-lookup"><span data-stu-id="d6d6e-154">Work with text data</span></span>

<span data-ttu-id="d6d6e-155">文字資料需要轉換成數字，才能用來建置機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-155">Text data needs to be transformed into numbers before using it to build a machine learning model.</span></span> <span data-ttu-id="d6d6e-156">請前往[轉換頁面](../resources/transforms.md)以取得詳細清單及文字轉換的描述。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-156">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="d6d6e-157">使用如下的資料，該資料已載入 [`IDataView`](xref:Microsoft.ML.IDataView)：</span><span class="sxs-lookup"><span data-stu-id="d6d6e-157">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
ReviewData[] reviews = new ReviewData[]
{
    new ReviewData
    {
        Description="This is a good product",
        Rating=4.7f
    },
    new ReviewData
    {
        Description="This is a bad product",
        Rating=2.3f
    }
};
```

<span data-ttu-id="d6d6e-158">將文字轉換成數字向量表示的最少步驟是使用 [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) 方法。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-158">The minimum step to convert text to a numerical vector representation is to use the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="d6d6e-159">透過使用 [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) 轉換，會將一系列的轉換套用到輸入文字資料行，產生表示 lp-normalized 文字及字元 ngrams 的數字向量。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-159">By using the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transform, a series of transformations is applied to the input text column resulting in a numerical vector representing the lp-normalized word and character ngrams.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="d6d6e-160">產生的轉換會將 `Description` 資料行中文字值轉換成數字向量，且看起來會和以下輸出相似：</span><span class="sxs-lookup"><span data-stu-id="d6d6e-160">The resulting transform would convert the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="d6d6e-161">將複雜的文字處理步驟合併成一個 [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)，移除干擾並可能可以視需要降低所需要的處理資源數。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-161">Combine complex text processing steps into an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) to remove noise and potentially reduce the amount of required processing resources as needed.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="d6d6e-162">`textEstimator` 包含 [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) 方法所執行作業的子集。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-162">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="d6d6e-163">更複雜管線之優點是對套用到資料的轉換進行控制和其可見度。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-163">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="d6d6e-164">使用第一個項目作為範例，下列是由 `textEstimator` 所定義轉換步驟產生結果的詳細描述：</span><span class="sxs-lookup"><span data-stu-id="d6d6e-164">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="d6d6e-165">**原始文字：這是很好的產品**</span><span class="sxs-lookup"><span data-stu-id="d6d6e-165">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="d6d6e-166">資料轉換</span><span class="sxs-lookup"><span data-stu-id="d6d6e-166">Transform</span></span> | <span data-ttu-id="d6d6e-167">描述</span><span class="sxs-lookup"><span data-stu-id="d6d6e-167">Description</span></span> | <span data-ttu-id="d6d6e-168">結果</span><span class="sxs-lookup"><span data-stu-id="d6d6e-168">Result</span></span>
|--|--|--|
|<span data-ttu-id="d6d6e-169">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="d6d6e-169">1. NormalizeText</span></span> | <span data-ttu-id="d6d6e-170">根據預設，將所有字母轉換成小寫</span><span class="sxs-lookup"><span data-stu-id="d6d6e-170">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="d6d6e-171">this is a good product</span><span class="sxs-lookup"><span data-stu-id="d6d6e-171">this is a good product</span></span>
|<span data-ttu-id="d6d6e-172">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="d6d6e-172">2. TokenizeWords</span></span> | <span data-ttu-id="d6d6e-173">將字串分割成個別的字組</span><span class="sxs-lookup"><span data-stu-id="d6d6e-173">Splits string into individual words</span></span> | <span data-ttu-id="d6d6e-174">["this","is","a","good","product"]</span><span class="sxs-lookup"><span data-stu-id="d6d6e-174">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="d6d6e-175">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="d6d6e-175">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="d6d6e-176">移除停用字詞，例如 *is* 和 *a*。</span><span class="sxs-lookup"><span data-stu-id="d6d6e-176">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="d6d6e-177">["good","product"]</span><span class="sxs-lookup"><span data-stu-id="d6d6e-177">["good","product"]</span></span>
|<span data-ttu-id="d6d6e-178">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="d6d6e-178">4. MapValueToKey</span></span> | <span data-ttu-id="d6d6e-179">根據輸入資料，將值對應到索引鍵 (類別)</span><span class="sxs-lookup"><span data-stu-id="d6d6e-179">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="d6d6e-180">[1,2]</span><span class="sxs-lookup"><span data-stu-id="d6d6e-180">[1,2]</span></span>
|<span data-ttu-id="d6d6e-181">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="d6d6e-181">5. ProduceNGrams</span></span> | <span data-ttu-id="d6d6e-182">將文字轉換成連續字組的序列</span><span class="sxs-lookup"><span data-stu-id="d6d6e-182">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="d6d6e-183">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="d6d6e-183">[1,1,1,0,0]</span></span>
|<span data-ttu-id="d6d6e-184">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="d6d6e-184">6. NormalizeLpNorm</span></span> | <span data-ttu-id="d6d6e-185">使用輸入的 lp-norm 縮放輸入</span><span class="sxs-lookup"><span data-stu-id="d6d6e-185">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="d6d6e-186">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="d6d6e-186">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
