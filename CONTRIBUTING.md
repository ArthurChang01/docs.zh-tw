---
ms.openlocfilehash: 469be53e14c42775f21ef1ef815becd5cad03a97
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75336715"
---
# <a name="contributing"></a>貢獻

感謝您對參與 .NET 文件感興趣！

> 我們正在將指導方針轉換成全網站參與指南。
> 若要查看新的指引，請瀏覽 [Microsoft Docs 參與者指南的概觀](https://docs.microsoft.com/contribute/)。

本文件涵蓋參與 [.NET 文件網站](https://docs.microsoft.com/dotnet)所裝載文章和程式碼範例的程序。 貢獻可以簡單到像錯字更正，或是複雜到像是新的文章。

- [使用規範](#dos-and-donts)
- [投稿程序](#process-for-contributing)
- [C# 互動式體驗](#the-c-interactive-experience)
- [參與者授權合約](#contributor-license-agreement)

此存放庫包含 .NET 的概念文件。 .NET 文件網站除了此存放庫之外，還使用多個存放庫作為建置基礎：

- 程式[代碼範例和程式碼片段](https://github.com/dotnet/samples)此存放庫的問題和工作會在[dotnet/檔/問題](https://github.com/dotnet/docs/issues)中進行追蹤。
- [.NET API 參考](https://github.com/dotnet/dotnet-api-docs)此存放庫的問題和工作會在[dotnet/dotnet-api-檔/問題](https://github.com/dotnet/dotnet-api-docs/issues)中進行追蹤。
- [.NET COMPILER PLATFORM SDK 參考](https://github.com/dotnet/roslyn-api-docs)此存放庫的問題和工作會在[dotnet/檔/問題](https://github.com/dotnet/docs/issues)中進行追蹤。

## <a name="dos-and-donts"></a>可進行及避免進行的事項

下列清單顯示您參與 .NET 文件時，應謹記在心的一些指導規則：

- 請**勿**以大量提取要求來讓我們大吃一驚。 而是請您先提出問題並開始討論，我們會在您投入大量的時間之前，先行確認方向。 若要進行大量變更，請將工作分成較小的 Pr （最多100個檔案）。 如果您的 PR 未遵循下列指導方針，則強烈建議使用此指導方針。
- **請**查看目前[的抓取](https://github.com/dotnet/docs/labels/up-for-grabs)問題，以取得有關工作的建議。
- **請**為每個工作建立一個 PR。 包含多個不相關變更的 Pr 比較難審視。 這會延遲評論和合併 Pr。 這項指導方針也適用于評論：我們不會在評論中建議不相關的變更。我們要求社區評論遵守此指導方針。
- **請**提供您 PR 中工作的清楚描述。 請告訴我們變更的內容和原因。 「更新 article.md」的預設描述對審核者而言並不實用。
- 請**不要**提交 pr 進行僅限樣式的變更，而不需要事先討論。 這些 Pr 需要花更多時間來審查準確度，而合併它們通常會造成與其他重要更新的合併衝突。 我們正努力遵循一致的風格，但我們正在進行平衡以處理其他工作。 當我們因其他原因而進行重大更新時，會將文章納入樣式一致性。
- **請務必**閱讀[樣式指南](./styleguide/template.md)與[語態和語氣](./styleguide/voice-tone.md)指導方針。 新的新增專案應遵循這些指導方針。
- **請務必**在對文章進行作業之前，先在分叉上建立您自己的分支。
- **請務必**遵循 [GitHub 流程的工作流程](https://guides.github.com/introduction/flow/)。
- **請務必**利用部落格及推特 (或任何其他形式)，頻繁地發表您的文章！

這些指導方針可協助我們尊重所有人的時間。 許多人都參與這些存放庫。 遵循這些指導方針，可讓我們更輕鬆地及時審查和合併您的 PR。 這些作法會將與其他社區成員和我們小組 Pr 的衝突降至最低。 由於未遵循這些指導方針的 Pr 通常會對美國和社區成員造成額外的工作，因此可能會拒絕這些 Pr。 如果您想要發生例外狀況，請先建立問題。

> 注意：您可能注意到某些主題目前並未依循這裡及[風格指南](./styleguide/template.md)上指定的所有指導方針。 我們目前正在努力達到整個網站的一致性。

## <a name="process-for-contributing"></a>投稿程序

您需要對 [Git 和 GitHub.com](https://guides.github.com/activities/hello-world/) 有基本了解。

**步驟1：** 針對小型變更略過此步驟（例如，如果您要更正錯誤或立即開啟提取要求，以解決您在檔中找到的問題）。 如果您有興趣撰寫新內容或徹底修訂現有的內容，請開立一個描述您所要執行動作的[問題](https://github.com/dotnet/docs/issues)。
[docs] 資料夾中的內容會組織成目錄 (TOC) 中所反映的各個小節。 請定義主題在 TOC 中的位置。 取得您提案的意見反應。

-或-

您也可以選擇歡迎社群參與的現有問題。 [適用於 .NET 社群參與者的專案](https://github.com/dotnet/docs/projects/35)列出許多可供社群參與者使用的工作項目。 視您的興趣和承諾層級而定，您可以選擇下列類別中的問題：

- **維護**。 此類別包括非常簡單的參與，例如修正中斷或不正確的連結、新增遺漏的程式碼範例，或處理有限的內容問題。 在某些情況下，這些問題可能會與大量的檔案有關。 在該情況下，您應該先讓我們知道您想要處理的項目，再開始進行。

- **內容更新**。 如果文件集相當龐大，內容很容易就會過期而需要修訂。 此外，基於各種原因，某些內容已重複或甚至是 triplicated。 更新內容牽涉到確認個別主題是否為最新，或修訂某個功能區域中的內容以去除重複項，並確保所有唯一內容都保存在較小的文件集內。

- **新內容撰寫**。 如果您有興趣撰寫自己的主題，這些問題列出了我們所知想要新增到文件集的主題。 不過，在您開始進行某個主題之前，請先讓我們知道。 如果您有興趣撰寫這裡未列出的主題，請開立問題。

您也可以查看我們的[待處理問題](https://github.com/dotnet/docs/issues) \(英文\) 清單，然後自願處理您有興趣的問題。 我們使用 [up-for-grabs](https://github.com/dotnet/docs/labels/up-for-grabs) \(開放取用\) 標籤來標記開放參與的問題。

**步驟 2：** 視需要將 `dotnet/docs`、`dotnet/samples` 或 `dotnet/dotnet-api-docs` 存放庫分叉，然後為您的變更建立分支。

若是進行少量變更，您可以使用 GitHub 的 Web 介面。 只需在您想要變更的檔案上按一下 [Edit the file in your fork of this project] \(編輯此專案分叉中的檔案\) 即可。 GitHub 會在您提交變更時，為您建立新的分支。

**步驟 3：** 對這個新的分支進行變更。

若此為新主題，您可使用這個[範本檔案](./styleguide/template.md)作為起點。 其包含撰寫指導方針，同時也會說明每篇文章所需的中繼資料，例如作者資訊。

請瀏覽至對應到步驟 1 中為您文章所決定的目錄位置資料夾。
該資料夾包含該章節中所有文章的 Markdown 檔案。
請視需要建立新的資料夾，以存放您內容的檔案。 該小節的主要文章稱為 *index.md*。
針對影像及其他靜態資源，請在包含您文章的資料夾內建立一個名為 *media* 的子資料夾 (如果此子資料夾尚未存在)。 在 [media] 資料夾內，使用文章名稱 (索引檔案除外) 建立一個子資料夾。
將較大型的範例納入存放庫根目錄底下的 [samples] 資料夾中。

請務必遵循正確的 Markdown 語法。 如需詳細資訊，請參閱[樣式指南](./styleguide/template.md)。

### <a name="example-structure"></a>範例結構

```
docs
  /about
  /core
    /porting
      porting-overview.md
      /media
        /porting-overview
            portability_report.png
```

**步驟4：** 從您的分支提交提取要求（PR）至 `dotnet/docs/master`、`dotnet/dotnet-api-docs/master`或 `dotnet/samples/master`。

您的 PR 應*一律*以存放庫的預設分支為目標（除非您正在使用發行分支）。 針對 dotnet/檔，主要分支是預設分支。 針對當地語系化的存放庫，live branch 是預設值。 您*絕對不*應該開啟以 dotnet/檔上的 live 分支為目標的 PR。

每個 PR 通常應該一次處理一個問題。 PR 可以修改一或多個檔案。 如果您要處理不同檔案上的多個修正，建議您使用個別的 PR。

如果您的 PR 要處理現有的問題，請在認可訊息或 PR 描述中新增 `Fixes #Issue_Number` 關鍵字。 如此一來，在合併 PR 時，就會自動關閉問題。 如需詳細資訊，請參閱[經由認可訊息結束問題](https://help.github.com/articles/closing-issues-via-commit-messages/)。

.NET 小組會檢閱您的 PR，並讓您知道是否需要任何其他更新/變更才能核准。

**步驟 5：** 依據與小組的討論，對分支進行任何必要的更新。

在套用意見反應且您的變更獲得核准之後，維護人員即會將您的 PR 合併到主要分支。

我們會依特定的頻率，將所有認可項目從主要分支至推送到即時分支，您如此即可即時於 https://docs.microsoft.com/dotnet/ 看到您所貢獻的內容。

### <a name="contributing-to-samples"></a>提供範例

我們會針對存在於存放庫中的程式碼進行下列區分：

- 範例：讀者可以下載並執行範例。 所有範例都應該是完整的應用程式或程式庫。 在範例建立程式庫的位置，應包含單元測試或可供讀者執行程式碼的應用程式。

- 程式碼片段：說明較小的概念或工作。 它們會進行編譯，但不會成為完整的應用程式。

程式碼都存在於 [dotnet/samples](https://github.com/dotnet/samples) 存放庫中。 我們正朝著建立一個讓範例資料夾結構符合文件資料夾結構的模型方向前進。 我們所依循的標準為：

- 最上層的 [snippets] 資料夾包含小型、重點範例的程式碼片段。
- API 參考範例一直以來都位於一個依循下列模式的資料夾中：*程式碼片段/\<語言>/api/\<命名空間>/\<API 名稱>* 。
- 其他最上層資料夾則與 *docs* 存放庫中的最上層資料夾相符。 例如，docs 存放庫包含一個 *machine-learning/tutorials* 資料夾，而機器學習教學課程的範例則位於 *samples/machine-learning/tutorials* 資料夾中。

此外，[core] 和 [standard] 資料夾底下的所有範例都應該在 .NET Core 支援的所有平台上建置並執行。 我們的 CI 建置系統將會強制執行該做法。 最上層 [framework] 資料夾則包含只會在 Windows 上建置並驗證的範例。

隨著 docs 存放庫新增新的內容，我們可能會擴充這些目錄。 舉例來說，我們將會新增 Xamarin 目錄，例如 `xamarin-ios` 和 `xamarin-android` 目錄。

您所建立的每個完整範例都應該包含 *readme.md* 檔案。 此檔案應該包含範例的簡短描述 (一或兩個段落)。 您的 *readme.md* 應該告訴使用者探索此範例將可學習到什麼。 *readme.md* 檔案應該包含一個 [.NET 文件網站](https://docs.microsoft.com/dotnet/welcome)上即時文件的連結。
若要決定存放庫中指定檔案與該網站對應的位置，請以 `https://docs.microsoft.com/dotnet` 取代存放庫路徑中的 `/docs`。

您的主題也會包含範例的連結。 請直接連結至 GitHub 上範例的資料夾。

如需詳細資訊，請參閱[範例讀我檔案](https://github.com/dotnet/samples/blob/master/README.md) \(英文\)。

## <a name="the-c-interactive-experience"></a>C# 互動式體驗

以 C# 撰寫的簡短程式碼範例可以使用 `csharp-interactive` 語言標記來指定在瀏覽器中執行的 C# 範例。 （內嵌程式碼範例會使用 `csharp-interactive` 標記，針對來源所包含的程式碼片段，請使用 `code-csharp-interactive` 標記）。這些程式碼範例會在文章中顯示程式碼視窗和 [輸出] 視窗。 在使用者執行範例之後，輸出視窗會顯示來自執行互動式程式碼的所有輸出。

C# 互動式體驗改變了我們使用範例的方式。 訪客可以執行範例來查看結果。 有一些因素可協助判斷範例或相對應的文字是否應該包含輸出的相關資訊。

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>何時該在無須執行範例的情況下顯示預期的輸出

- 文章如果是以初學者為對象，就應該提供輸出，以便讓讀者能夠將其工作輸出與預期的答案做比較。
- 範例的輸出如果是主題不可或缺的一部份，範例就應該顯示該輸出。 例如，有關格式化文字的文章應該在無須執行範例的情況下，便顯示文字格式。
- 當範例和預期的輸出都很簡短時，請考慮顯示輸出。 這樣可節省一些時間。
- 文章如果是說明目前文化特性 (Culture) 或不因文化特性而異會如何影響輸出，就應該說明預期的輸出。 互動式 REPL (「讀取、求值、輸出」迴圈) 會在 Linux 型主機上執行。 預設文化特性 (Culture) 和不因文化特性而異會在不同的作業系統與機器上，產生不同的輸出。 文章應該說明 Windows、Linux 及 Mac 系統中的輸出。

### <a name="when-to-exclude-expected-output-from-the-sample"></a>何時該從範例中排除預期的輸出

- 文章的範例如果會產生較大型的輸出，註解中就不應該包含該輸出。 一旦執行範例，它便會遮蔽程式碼。
- 當文章的範例會示範某個主題，但輸出並非理解該主題的必要部分時。 例如，執行 LINQ 查詢來說明查詢語法後再於輸出集合中顯示每個項目的程式碼。

## <a name="contributor-license-agreement"></a>參與者授權合約

您必須先簽署 [.NET Foundation 貢獻授權合約 (CLA)](https://cla.dotnetfoundation.org)，才能合併您的 PR。 這是針對 .NET Foundation 中專案的單次要求。 您可於 Wikipedia 上閱讀更多關於[貢獻授權合約 (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) 的資訊。

合約：[net-foundation-contribution-license-agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

您不必預先簽署合約。 您可以一如往常地複製、派生和提交 PR。 PR 建立後，CLA Bot 就會為其分類。 如果是不重要的變更 (例如修正了某個錯字)，則 PR 會標示為 `cla-not-required`。 否則，會歸類為 `cla-required`。 在您簽署 CLA 之後，目前及未來的所有提取要求都會標示為 `cla-signed`。
