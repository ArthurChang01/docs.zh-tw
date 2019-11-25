---
title: 'Tutorial: Categorize iris flowers - k-means clustering'
description: 了解如何在群集案例中使用 ML.NET
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: a7199ce2e5217eaadfa10893eb1fbb3417e9be20
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204828"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a>Tutorial: Categorize iris flowers using k-means clustering with ML.NET

本教學課程說明如何使用 ML.NET 為[鳶尾花資料集](https://en.wikipedia.org/wiki/Iris_flower_data_set)建立一個[群集模型](../resources/tasks.md#clustering)。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 了解問題
> - 選取適當的機器學習工作
> - 準備資料
> - 載入並轉換資料
> - 選擇學習演算法
> - 將模型定型
> - 使用模型來進行預測

## <a name="prerequisites"></a>Prerequisites

- [Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.

## <a name="understand-the-problem"></a>了解問題

這個問題是關於將一組鳶尾花按照花卉特徵分成不同的群組。 這些特徵是萼片的長度和寬度以及花瓣的長度和寬度。 本教學課程中假設不知道每個花卉的類型。 您想要從特徵了解資料集的結構，還要預測資料執行個體如何符合此結構。

## <a name="select-the-appropriate-machine-learning-task"></a>選取適當的機器學習工作

因為您不知道每個花卉屬於哪個群組，所以您選擇[非監督式機器學習](../resources/glossary.md#unsupervised-machine-learning)工作。 若要按照類似元素歸於同一群組中的方式來分割群組中的資料集，請使用[群集](../resources/tasks.md#clustering)機器學習工作。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 開啟 Visual Studio。 從功能表列中選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。 然後選取 [主控台應用程式 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，鍵入 "IrisFlowerClustering"，然後選取 [確定] 按鈕。

1. 在您的專案中建立一個名為 *Data* 的目錄以儲存資料集和模型檔案：

    在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新增資料夾]。 輸入 "Data"，然後按 Enter。

1. 安裝 **Microsoft.ML** NuGet 套件：

    在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。 Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button. 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

## <a name="prepare-the-data"></a>準備資料

1. 下載 [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) 資料集，並將它儲存到上一個步驟中建立的 *Data* 資料夾。 如需有關鳶尾花資料集的詳細資訊，請參閱[鳶尾花資料集](https://en.wikipedia.org/wiki/Iris_flower_data_set)維基百科頁面和[鳶尾花資料集](https://archive.ics.uci.edu/ml/datasets/Iris)頁面 (也就是資料集的來源)。

1. 以滑鼠右鍵按一下 [方案總管] 中的 *iris.data* 檔案，然後選取 [內容]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

*Iris.data* 檔案包含五個資料行，分別表示：

- 萼片長度 (以公分為單位)
- 萼片寬度 (以公分為單位)
- 花瓣長度 (以公分為單位)
- 花瓣寬度 (以公分為單位)
- 鳶尾花的類型

為了示範群集方法，本教學課程會略過最後一個資料行。

## <a name="create-data-classes"></a>建立資料類別

為輸入資料和預測建立類別：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *IrisData.cs*。 接著，選取 [新增] 按鈕。
1. 將下列的 `using` 指示詞加入新檔案：

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

移除現有的類別定義，然後將下列程式碼 (定義 `IrisData` 和 `ClusterPrediction` 這兩個類別) 新增至 *IrisData.cs* 檔案：

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

`IrisData` 是輸入資料類別，它含有資料集中每個特徵的定義。 請使用 [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) 屬性來指定資料集檔案中來源資料行的索引。

`ClusterPrediction` 類別代表套用至 `IrisData` 執行個體的群集模型結果。 使用 [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性分別將 `PredictedClusterId` 和 `Distances` 欄位繫結至 **PredictedLabel** 和 **Score** 資料行。 群集這些資料行的工作具有下列意義：

- **PredictedLabel** 資料行包含預測群集的 ID。
- **Score** 資料行包含平方歐幾里得距離到群集矩心的陣列。 陣列長度等於群集數目。

> [!NOTE]
> 使用 `float` 型別表示輸入和預測資料類別中的浮點值。

## <a name="define-data-and-model-paths"></a>定義資料和模型路徑

返回 *Program.cs* 檔案並新增兩個欄位，保存資料集檔案的路徑以及儲存模型之檔案的路徑：

- `_dataPath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。
- `_modelPath` 會針對儲存定型模型的檔案，包含檔案的路徑。

將下列程式碼加入 `Main` 方法的緊鄰上方，以指定這些路徑：

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

若要將上述的程式碼進行編譯，請在 *Program.cs* 檔案頂端加入下列 `using` 指示詞：

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>建立 ML 內容

在 *Program.cs* 檔案頂端加入下列額外的 `using` 指示詞：

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

在 `Console.WriteLine("Hello World!");` 方法中，以下列程式碼取代 `Main` 行：

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<xref:Microsoft.ML.MLContext?displayProperty=nameWithType> 類別表示機器學習環境，並為資料載入、模型定型、預測和其他工作提供記錄機制和進入點。 這在概念上類似於在 Entity Framework 中使用的 `DbContext`。

## <a name="setup-data-loading"></a>設定資料載入

將下列程式碼新增至 `Main` 方法，以設定資料載入方式：

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

泛型的 [`MLContext.Data.LoadFromTextFile` 擴充方法](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29)會從所提供的 `IrisData` 類型推斷資料集結構描述，並傳回 <xref:Microsoft.ML.IDataView>，其可作為轉換器的輸入使用。

## <a name="create-a-learning-pipeline"></a>建立學習管線

在本教學課程中，叢集工作的學習管線包含下列兩個步驟：

- 將載入的資料行串連成一個 [特徵] 資料行，以供叢集定型器使用；
- 使用 <xref:Microsoft.ML.Trainers.KMeansTrainer> 定型器透過 k-means++ 叢集演算法將模型定型。

將下列程式碼加入 `Main` 方法：

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

此程式碼指定應該將資料集分成三個叢集。

## <a name="train-the-model"></a>將模型定型

上述小節中加入的步驟已準備好訓練的管道，不過，還沒有開始執行。 將下列程式碼行新增至 `Main` 方法，以執行資料載入和模型定型：

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a>儲存模型

此時，您已有一個可整合至任何現有或新 .NET 應用程式的模型。 若要將您的模型儲存成 .zip 檔案，請將下列程式碼新增至 `Main` 方法：

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>使用模型來進行預測

為了進行預測，請使用 <xref:Microsoft.ML.PredictionEngine%602> 類別，其帶領輸入類型的執行個體通過轉換程式管線，並產生輸出類型的執行個體。 將下列程式碼行新增至 `Main` 方法，以建立該類別的執行個體：

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。 It's acceptable to use in single-threaded or prototype environments. For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application. See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

> [!NOTE]
> `PredictionEnginePool` 服務延伸模組目前處於預覽狀態。

建立 `TestIrisData` 類型以容納測試資料執行個體：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TestIrisData.cs*。 接著，選取 [新增] 按鈕。
1. 將類別修改成靜態，如以下範例所示：

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

本教學課程介紹此類別內一個鳶尾花資料執行個體。 您可以新增其他案例來對此模型進行實驗。 將下列程式碼新增至 `TestIrisData` 類別：

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

若要找出指定項目所屬的群集，請返回 *Program.cs* 檔案，然後將下列程式碼加入至 `Main` 方法：

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

執行程式，以查看哪些群集包含指定的資料執行個體以及從該執行個體到群集矩心的平方距離。 您的結果應該與以下類似：

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

恭喜您！ 您現在已成功建置用來群集鳶尾花並進行預測的機器學習模型。 您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub 存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 了解問題
> - 選取適當的機器學習工作
> - 準備資料
> - 載入並轉換資料
> - 選擇學習演算法
> - 將模型定型
> - 使用模型來進行預測

請查看我們的 GitHub 存放庫來繼續學習及尋找更多範例。
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/)
