---
title: C# 版本控制 - C# 手冊
description: 了解 C# 和 .NET 的版本控制運作方式
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: dc192337e4eaa5f9f1d6509ea8c15deeac34a48c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645461"
---
# <a name="versioning-in-c"></a>C\# 中的版本控制

在本教學課程中，您會了解版本控制在 .NET 中的意義。 您也會了解進行程式庫版本控制以及升級成新版程式庫時要考量的因素。

## <a name="authoring-libraries"></a>撰寫程式庫

身為已建立公用用途 .NET 程式庫的開發人員，您很可能經歷過必須推出新更新的情況。 如何執行此程序影響重大，因為您需要確保現有程式碼能夠順暢轉換到新版文件庫。 以下是建立新版本時要考量的幾件事︰

### <a name="semantic-versioning"></a>語意版本控制

[語意版本控制](https://semver.org/) (簡稱為 SemVer) 是文件庫各版本套用的命名慣例，表示特定的重大事件。
理想情況是，您提供給文件庫的版本資訊應該能幫助開發人員判斷其與使用同一文件庫舊版本的專案是否相容。

SemVer 最基本的方法是 3 元件格式 `MAJOR.MINOR.PATCH`，其中：

- 當您進行不相容的 API 變更時會遞增 `MAJOR`
- 當您以回溯相容方式新增功能時會遞增 `MINOR`
- 當您進行回溯相容的 Bug 修正時會遞增 `PATCH`

將版本資訊套用至您的 .NET 文件庫時，還有其他方式可以指定其他狀況，例如發行前版本等等。

### <a name="backwards-compatibility"></a>回溯相容性

當您發行新版文件庫時，與舊版相容會是您的主要考量之一。
如果相依於前一版的程式碼在重新編譯時，能在新版正常運作，新舊兩版的文件庫就是來源相容。
如果相依於舊版的應用程式在未重新編譯的情況下，能在新版正常運作，新舊兩版的文件庫就是二進位相容。

以下是嘗試維持與舊版文件庫的相容性時要考慮的一些事項︰

- 虛擬方法︰當您在新版本中將虛擬方法變成非虛擬，表示必須更新覆寫該方法的專案。 這是一項極重大的變更，強烈建議您不要這麼做。
- 方法簽名:當更新方法行為要求您更改其簽名時,應改為創建重載,以便調用該方法的代碼仍然有效。
您可以一直使用舊的方法簽章呼叫新方法簽章，讓實作保持一致。
- [Obsolete 屬性](language-reference/attributes/general.md#obsolete-attribute)︰您可以在程式碼中使用這個屬性，指定未來版本中要取代及可能移除的類別或類別成員。 這可確保使用您文件庫的開發人員在面對重大變更時有更完善的準備。
- 選擇性的方法引數︰當您將先前的選擇性方法引數變為強制，或是變更其預設值後，所有不提供這些引數的程式碼都需要更新。

> [!NOTE]
> 使強制參數可選應該沒有什麼效果,特別是如果它不改變方法的行為。

使用者升級至新版文件庫的過程愈簡單，他們就愈可能快速升級。

### <a name="application-configuration-file"></a>應用程式組態檔

身為 .NET 開發人員，您在大多數的專案類型中，有很大的機會遇到[`app.config` 檔案](../framework/configure-apps/file-schema/index.md)。
這個簡單的組態檔要很長時間才能改善推出新的更新。 通常,您應該以可能定期更改的資訊存儲`app.config`在 檔中的方式設計庫,這樣,當此類資訊更新時,舊版本的配置檔只需替換為新版本的配置檔,而無需重新編譯庫。

## <a name="consuming-libraries"></a>使用文件庫

身為使用其他開發人員所組建的 .NET 文件庫的開發人員，您很清楚新版文件庫可能無法與您的專案完全相容，而您可能必須經常更新自己的程式碼，才能使用這些變更。

幸運的是,C# 和 .NET 生態系統附帶了一些功能和技術,使我們能夠輕鬆更新應用,以便使用新版本的庫,這些庫可能會帶來重大更改。

### <a name="assembly-binding-redirection"></a>組件繫結重新導向

您可以使用*app.config*檔案更新應用使用的庫版本。 通過添加所謂的[*綁定重定向*](../framework/configure-apps/redirect-assembly-versions.md),可以使用新的庫版本,而無需重新編譯你的應用。 下面的範例展示如何更新應用的應用 *.config*檔,`1.0.1`以使用修`ReferencedLibrary`補程式 版本,而不是`1.0.0`最初編譯 的版本。

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> 新版 `ReferencedLibrary` 與您的應用程式必須是二進位相容，才能使用這個方法。
> 如需決定相容性時需要留意的變更，請參閱前文的[回溯相容性](#backwards-compatibility)一節。

### <a name="new"></a>new

您使用 `new` 修飾詞隱藏繼承的基底類別成員。 這是衍生類別可以回應基底類別更新的一種方式。

請使用以下範例：

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

**輸出**

```console
A base method
A derived method
```

您在上例中可以看到 `DerivedClass` 如何隱藏出現在 `BaseClass` 中的 `MyMethod` 方法。
這表示，當新版文件庫中的基底類別新增您衍生類別中已有的成員時，您只要對衍生類別成員使用 `new` 修飾詞，就可以隱藏基底類別成員。

未指定任何 `new` 修飾詞時，衍生類別預設會隱藏基底類別中發生衝突的成員，雖然會產生編譯器警告，但程式碼仍會編譯。 這表示，只要將新成員新增至現有的類別，即可讓新版文件庫與與相依於它的程式碼為來源和二進位相容。

### <a name="override"></a>override

`override` 修飾詞表示衍生的實作會擴充基底類別成員的實作，而非隱藏它。 基底類別成員需要套用 `virtual` 修飾詞。

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

**輸出**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` 修飾詞會在編譯期間評估，如果編譯器找不到要覆寫的虛擬成員，它會擲回錯誤。

您對所討論技術的瞭解以及您對使用它們的情況的理解,將大有作為,從而有助於緩解庫版本之間的過渡。
