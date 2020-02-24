---
title: 教學課程：安裝和使用 .NET Core 本機工具
description: 瞭解如何安裝和使用 .NET 工具做為本機工具。
ms.date: 02/12/2020
ms.openlocfilehash: 6de620772cec1e9d1b1f57380b72c0163d68337c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543863"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a><span data-ttu-id="e49c6-103">教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 本機工具</span><span class="sxs-lookup"><span data-stu-id="e49c6-103">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>

<span data-ttu-id="e49c6-104">**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e49c6-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="e49c6-105">本教學課程會教您如何安裝和使用本機工具。</span><span class="sxs-lookup"><span data-stu-id="e49c6-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="e49c6-106">您會使用在[本系列的第一個教學](global-tools-how-to-create.md)課程中建立的工具。</span><span class="sxs-lookup"><span data-stu-id="e49c6-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e49c6-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e49c6-107">Prerequisites</span></span>

* <span data-ttu-id="e49c6-108">完成[此系列的第一個教學](global-tools-how-to-create.md)課程。</span><span class="sxs-lookup"><span data-stu-id="e49c6-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="e49c6-109">安裝 .NET Core 2.1 執行時間。</span><span class="sxs-lookup"><span data-stu-id="e49c6-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="e49c6-110">在本教學課程中，您會安裝並使用以 .NET Core 2.1 為目標的工具，因此您必須在電腦上安裝該執行時間。</span><span class="sxs-lookup"><span data-stu-id="e49c6-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="e49c6-111">若要安裝2.1 執行時間，請移至[.Net Core 2.1 下載頁面](https://dotnet.microsoft.com/download/dotnet-core/2.1)，並在 [**執行應用程式-運行**時間] 資料行中尋找執行時間安裝連結。</span><span class="sxs-lookup"><span data-stu-id="e49c6-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="e49c6-112">建立資訊清單檔</span><span class="sxs-lookup"><span data-stu-id="e49c6-112">Create a manifest file</span></span>

<span data-ttu-id="e49c6-113">若要安裝僅限本機存取的工具（針對目前的目錄和子目錄），必須將它新增至資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="e49c6-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span> 

<span data-ttu-id="e49c6-114">從*botsay\<名稱 >*  資料夾中，流覽至 存放*庫* 資料夾的一個層級：</span><span class="sxs-lookup"><span data-stu-id="e49c6-114">From the *botsay-\<name>* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="e49c6-115">藉由執行[dotnet new](dotnet-new.md)命令來建立資訊清單檔：</span><span class="sxs-lookup"><span data-stu-id="e49c6-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="e49c6-116">輸出表示檔案建立成功。</span><span class="sxs-lookup"><span data-stu-id="e49c6-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="e49c6-117">*.Config/dotnet-tools*檔案尚未提供任何工具：</span><span class="sxs-lookup"><span data-stu-id="e49c6-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="e49c6-118">資訊清單檔案中所列的工具可供目前的目錄和子目錄使用。</span><span class="sxs-lookup"><span data-stu-id="e49c6-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="e49c6-119">目前目錄是包含 *.config*目錄和資訊清單檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="e49c6-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="e49c6-120">當您使用參考本機工具的 CLI 命令時，SDK 會搜尋目前目錄和上層目錄中的資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="e49c6-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="e49c6-121">如果找到資訊清單檔案，但檔案未包含參考的工具，它會繼續透過父目錄進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="e49c6-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="e49c6-122">搜尋會在找到參考的工具或找到 `isRoot` 設定為 `true`的資訊清單檔案時結束。</span><span class="sxs-lookup"><span data-stu-id="e49c6-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="e49c6-123">以本機工具安裝 botsay</span><span class="sxs-lookup"><span data-stu-id="e49c6-123">Install botsay as a local tool</span></span>

<span data-ttu-id="e49c6-124">從您在第一個教學課程中建立的套件安裝此工具：</span><span class="sxs-lookup"><span data-stu-id="e49c6-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./botsay-<name>/nupkg botsay-<name>
```

<span data-ttu-id="e49c6-125">此命令會將工具新增至您在上一個步驟中建立的資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="e49c6-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="e49c6-126">命令輸出會顯示新安裝工具所在的資訊清單檔案：</span><span class="sxs-lookup"><span data-stu-id="e49c6-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="e49c6-127">*.Config/dotnet-tools*檔案現在有一項工具：</span><span class="sxs-lookup"><span data-stu-id="e49c6-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay-<name>": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a><span data-ttu-id="e49c6-128">使用工具</span><span class="sxs-lookup"><span data-stu-id="e49c6-128">Use the tool</span></span>

<span data-ttu-id="e49c6-129">從存放*庫*資料夾執行 `dotnet tool run` 命令來叫用工具：</span><span class="sxs-lookup"><span data-stu-id="e49c6-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="e49c6-130">還原其他人所安裝的本機工具</span><span class="sxs-lookup"><span data-stu-id="e49c6-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="e49c6-131">您通常會在存放庫的根目錄中安裝本機工具。</span><span class="sxs-lookup"><span data-stu-id="e49c6-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="e49c6-132">將資訊清單檔簽入至存放庫之後，其他開發人員就可以取得最新的資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="e49c6-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="e49c6-133">若要安裝資訊清單檔案中列出的所有工具，可以執行單一 `dotnet tool restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="e49c6-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="e49c6-134">開啟 *.config/dotnet-tools*檔案，並將內容取代為下列 json：</span><span class="sxs-lookup"><span data-stu-id="e49c6-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "botsay-<name>": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. <span data-ttu-id="e49c6-135">以您用來建立專案的名稱取代 `<name>`。</span><span class="sxs-lookup"><span data-stu-id="e49c6-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="e49c6-136">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="e49c6-136">Save your changes.</span></span>

   <span data-ttu-id="e49c6-137">進行這種變更的方式與從存放庫取得最新版本，在其他人安裝了專案目錄的封裝 `dotnetsay`。</span><span class="sxs-lookup"><span data-stu-id="e49c6-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span> 

1. <span data-ttu-id="e49c6-138">執行 `dotnet tool restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="e49c6-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="e49c6-139">命令會產生如下列範例所示的輸出：</span><span class="sxs-lookup"><span data-stu-id="e49c6-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'botsay-<name>' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="e49c6-140">確認工具可供使用：</span><span class="sxs-lookup"><span data-stu-id="e49c6-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="e49c6-141">輸出是封裝和命令的清單，類似于下列範例：</span><span class="sxs-lookup"><span data-stu-id="e49c6-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   -------------------------------------------------------------------------------------------
   botsay-<name>   1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="e49c6-142">測試控管：</span><span class="sxs-lookup"><span data-stu-id="e49c6-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="e49c6-143">更新本機工具</span><span class="sxs-lookup"><span data-stu-id="e49c6-143">Update a local tool</span></span>

<span data-ttu-id="e49c6-144">已安裝的本機工具 `dotnetsay` 版本為2.1.3。</span><span class="sxs-lookup"><span data-stu-id="e49c6-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="e49c6-145">最新版本是2.1.4。</span><span class="sxs-lookup"><span data-stu-id="e49c6-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="e49c6-146">使用[dotnet tool update](dotnet-tool-update.md)命令將工具更新為最新版本。</span><span class="sxs-lookup"><span data-stu-id="e49c6-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="e49c6-147">輸出會顯示新的版本號碼：</span><span class="sxs-lookup"><span data-stu-id="e49c6-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="e49c6-148">Update 命令會尋找包含封裝識別碼的第一個資訊清單檔案，並加以更新。</span><span class="sxs-lookup"><span data-stu-id="e49c6-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="e49c6-149">如果在搜尋範圍內的任何資訊清單檔案中沒有此類套件識別碼，SDK 就會將新專案新增至最接近的資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="e49c6-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="e49c6-150">搜尋範圍會透過父目錄來啟動，直到找到具有 `isRoot = true` 的資訊清單檔案為止。</span><span class="sxs-lookup"><span data-stu-id="e49c6-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="e49c6-151">移除本機工具</span><span class="sxs-lookup"><span data-stu-id="e49c6-151">Remove local tools</span></span>

<span data-ttu-id="e49c6-152">執行[dotnet tool uninstall](dotnet-tool-uninstall.md)命令以移除已安裝的工具：</span><span class="sxs-lookup"><span data-stu-id="e49c6-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall botsay-<name>
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="e49c6-153">疑難排解</span><span class="sxs-lookup"><span data-stu-id="e49c6-153">Troubleshoot</span></span>

<span data-ttu-id="e49c6-154">如果您在教學課程之後收到錯誤訊息，請參閱針對[.Net Core 工具使用問題進行疑難排解](troubleshoot-usage-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="e49c6-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e49c6-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e49c6-155">See also</span></span>

<span data-ttu-id="e49c6-156">如需詳細資訊，請參閱[.Net Core 工具](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="e49c6-156">For more information, see [.NET Core tools](global-tools.md)</span></span>