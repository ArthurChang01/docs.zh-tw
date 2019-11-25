---
title: 對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯
description: 了解如何對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯。
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 098c7519fe99ef04773c5e4b81685ca0f06f1272
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281521"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="7b6db-103">對 .NET for Apache Spark 應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="7b6db-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="7b6db-104">此操作說明提供對 Windows 上的 .NET for Apache Spark 應用程式和 Scala 程式碼進行偵錯時，所需執行的命令。</span><span class="sxs-lookup"><span data-stu-id="7b6db-104">This how-to provides the commands you need to run to debug your .NET for Apache Spark application and Scala code on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="7b6db-105">對應用程式進行 Debug</span><span class="sxs-lookup"><span data-stu-id="7b6db-105">Debug your application</span></span>

<span data-ttu-id="7b6db-106">開啟新的命令提示字元視窗，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7b6db-106">Open a new command prompt window, run the following:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="7b6db-107">當您執行命令時，您會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7b6db-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="7b6db-108">在此偵錯模式中，`DotnetRunner` 不會啟動 .NET 應用程式，而是會等待它連線。</span><span class="sxs-lookup"><span data-stu-id="7b6db-108">In this debug mode, `DotnetRunner` does not launch the .NET application, but it waits for it to connect.</span></span> <span data-ttu-id="7b6db-109">不要關閉此命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="7b6db-109">Leave this command prompt window open.</span></span>

<span data-ttu-id="7b6db-110">現在，您可以執行 .NET 應用程式，並搭配任何偵錯工具來對應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="7b6db-110">Now you can run your .NET application with any debugger to debug your application.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="7b6db-111">對 Scala 程式碼進行偵錯</span><span class="sxs-lookup"><span data-stu-id="7b6db-111">Debug Scala code</span></span>

<span data-ttu-id="7b6db-112">如果您需要對 Scala 端程式碼進行偵錯，例如 `DotnetRunner` 或 `DotnetBackendHandler`，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7b6db-112">If you need to debug the Scala side code, such as `DotnetRunner` or `DotnetBackendHandler`, run the following command:</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="7b6db-113">執行命令之後，請使用 [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html) 將偵錯工具附加至執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="7b6db-113">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7b6db-114">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7b6db-114">Next steps</span></span>

* [<span data-ttu-id="7b6db-115">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7b6db-115">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="7b6db-116">將 .NET for Apache Spark 應用程式部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="7b6db-116">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="7b6db-117">將 .NET for Apache Spark 應用程式部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="7b6db-117">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="7b6db-118">將 .NET for Apache Spark 應用程式部署到 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="7b6db-118">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
