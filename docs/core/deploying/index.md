---
title: .NET Core 應用程式部署
description: 了解部署 .NET Core 應用程式的方式。
ms.date: 12/03/2018
ms.openlocfilehash: 425f0d5bf11fd0572825d2025005aacf65d7d2cd
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920881"
---
# <a name="net-core-application-deployment"></a>.NET Core 應用程式部署

您可以建立三種類型的 .NET Core 應用程式部署︰

- 與 Framework 相依的部署。 正如其名，與 Framework 相依的部署 (framework-dependent deployment, FDD) 仰賴存在於目標系統上的全系統共用 .NET Core 版本。 因為 .NET Core 已存在，所以應用程式也可以在 .NET Core 安裝之間攜帶。 您的應用程式僅包含其自有程式碼和 .NET Core 程式庫以外的所有協力廠商相依性。 FDD 包含的 *.dll* 檔案，可以使用 [dotnet 公用程式](../tools/dotnet.md)從命令列啟動。 例如，`dotnet app.dll` 執行名為 `app` 的應用程式。

- 自封式部署。 不同於 FDD，自封式部署 (SCD) 不仰賴任何存在於目標系統上的共用元件。 包括 .NET Core 程式庫和 .NET Core 執行階段的所有元件，都隨附於應用程式，並與其他 .NET Core 應用程式隔離。 SCD 包含可執行檔 (例如，Windows 平台上 `app` 應用程式的 *app.exe*)，這是重新命名的特定平台 .NET Core 主應用程式版本，以及實際的應用程式 *.dll* 檔案 (例如 *app.dll*)。

- 架構相依可執行檔。 產生可在目標平台上執行的可執行檔。 架構相依可執行檔 (FDE) 與 FDDs 類似，它是平台特定且不是自封式。 這些部署仍相依於共用系統面 .NET Core 版本。 與 SCD 不一樣，您的應用程式只包含您的程式碼與 .NET Core 程式庫外的任何第三方相依性。 FDE 會產生在目標平台上執行的可執行檔。

## <a name="framework-dependent-deployments-fdd"></a>與 Framework 相依的部署 (FDD)

針對 FDD，您只要部署您的應用程式與協力廠商相依性。 您的應用程式將會使用存在於目標系統上的 .NET Core 版本。 這是以 .NET Core 為目標是 .NET Core 與 ASP.NET Core 應用程式的預設部署模型。

### <a name="why-create-a-framework-dependent-deployment"></a>為何建立與 Framework 相依的部署？

部署 FDD 有許多優點︰

- 您不必事先定義 .NET Core 應用程式執行所在的目標作業系統。 由於不論作業系統為何，.NET Core 對可執行檔和程式庫都使用通用的 PE 檔案格式，所以 .NET Core 可以執行您的應用程式，不理會基礎作業系統。 如需 PE 檔格式的詳細資訊，請參閱 [.NET Assembly File Format](../../standard/assembly/file-format.md) (.NET 組件檔案格式)。

- 部署套件的大小很小。 您只需要部署您的應用程式及其相依性，不用部署 .NET Core。

- 除非被覆寫，否則 FDD 將會使用目標系統上安裝的最新維護執行階段。 這可讓您的應用程式使用最新的已修補 .NET Core 執行階段版本。 

- 多個應用程式使用相同的 .NET Core 安裝，這樣可減少主機系統的磁碟空間和記憶體使用量。

另外還有幾個缺點︰

- 只有主機系統安裝您的應用程式以其為目標的 .NET Core 版本[或更新版本](../versions/selection.md#framework-dependent-apps-roll-forward)，您的應用程式才能執行。

- .NET Core 執行階段和程式庫在未來的版本中可能有所變更，但不會通知您。 只有極其罕見的情況，才可能變更應用程式的行為。

## <a name="self-contained-deployments-scd"></a>自封式部署 (SCD)

針對自封式部署，您需要部署自己的應用程式和所有需要的協力廠商相依性，以及建置應用程式所用的 .NET Core 版本。 不過，建立 SCD 不包含各種平台的 [.NET Core 原生相依性](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)本身 (例如，macOS 上的 OpenSSL)，所以在執行應用程式前要先行安裝。 如需執行階段之版本繫結的詳細資訊，請參閱 [.NET Core 中的版本繫結](../versions/selection.md)上的文章。

從 NET Core 2.1 SDK (2.1.300 版) 開始，.NET Core 就支援*修補版本向前復原*。 當您建立自封式部署時，.NET Core 工具會自動包括您的應用程式以其為目標的最新 .NET Core 維護執行階段版本 （最新的服務執行時間包含安全性修補程式和其他錯誤修正）。服務執行時間不一定要存在於您的組建系統上;它會自動從 NuGet.org 下載。如需詳細資訊，包括如何退出宣告修補程式版本向前復原的指示，請參閱[獨立部署執行時間向前](runtime-patch-selection.md)復原。

FDD 和 SCD 使用不同的主機可執行檔，因此您可以使用自己的發行者簽章，為 SCD 簽署主機可執行檔。

### <a name="why-deploy-a-self-contained-deployment"></a>為什麼要部署自封式部署？

部署自封式部署有兩大優點︰

- 您可以獨家控制隨應用程式部署的 .NET Core 版本。 只有您可以提供 .NET Core 服務。

- 您可以保證目標系統能執行您的 .NET Core 應用程式，因為您提供的是它可以執行的 .NET Core 版本。

它也有一些缺點︰

- 因為 .NET Core 包含在您的部署套件中，所以您必須事先選取部署套件建置所在的目標平台。

- 您的部署套件的大小相當大，因為您必須包含 .NET Core 以及應用程式及其協力廠商相依性。

  從 .NET Core 2.0 開始，您就可以使用 .NET Core [*全球化不變模式*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)來減少 Linux 系統上的部署大小大約 28 MB。 一般而言，Linux 上的 .NET Core 依賴 [ICU 程式庫](http://icu-project.org)來提供全球化支援。 在不區分模式中，您的部署不包含程式庫，而且所有文化特性的行為[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)。

- 將多個自封式 .NET Core 應用程式部署到系統，會消耗大量的磁碟空間，因為每個應用程式都會重複 .NET Core 檔案。

## <a name="framework-dependent-executables-fde"></a>架構相依可執行檔 (FDE)

從 .NET Core 2.2 開始，您就可以將您的應用程式部署為 FDE，以及任何必要的第三方相依性。 您的應用程式將會使用安裝在目標系統上的 .NET Core 版本。

### <a name="why-deploy-a-framework-dependent-executable"></a>為何部署架構相依可執行檔？

部署 FDE有許多優點︰

- 部署套件的大小很小。 您只需要部署您的應用程式及其相依性，不用部署 .NET Core。

- 多個應用程式使用相同的 .NET Core 安裝，這樣可減少主機系統的磁碟空間和記憶體使用量。

- 您的應用程式可以透過呼叫已發行的可執行檔來執行，而不需要直接叫用 `dotnet` 公用程式。

另外還有幾個缺點︰

- 只有主機系統安裝您的應用程式以其為目標的 .NET Core 版本[或更新版本](../versions/selection.md#framework-dependent-apps-roll-forward)，您的應用程式才能執行。

- .NET Core 執行階段和程式庫在未來的版本中可能有所變更，但不會通知您。 只有極其罕見的情況，才可能變更應用程式的行為。

- 您必須為每個目標平台發行您的應用程式。

## <a name="step-by-step-examples"></a>逐步說明範例

如需使用 .NET Core CLI 部署 .NET Core 應用程式的逐步範例，請參閱[使用 .NET Core CLI 發佈 .Net core 應用程式](deploy-with-cli.md)。 如需使用 Visual Studio 部署 .NET Core 應用程式的逐步說明範例，請參閱[使用 Visual Studio 部署 .NET Core 應用程式](deploy-with-vs.md)。 

## <a name="see-also"></a>請參閱

- [使用 .NET Core CLI 發佈 .NET Core 應用程式](deploy-with-cli.md)
- [使用 Visual Studio 部署 .NET Core 應用程式](deploy-with-vs.md)
- [套件、中繼套件和架構](../packages.md)
- [.NET Core 執行階段識別項 (RID) 目錄](../rid-catalog.md)
