---
title: Visual Basic 語言逐步解說
description: Visual Basic 開發的常見案例逐步指示
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, walkthroughs
- examples [Visual Basic]
- Visual Basic code, walkthroughs
- walkthroughs [Visual Basic]
ms.assetid: e4e1f849-e1ce-4cf7-8483-d9b4c4887a8e
ms.openlocfilehash: f6a4c5b5376c5ee746bb0fadfeeac7ac9793e91f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040942"
---
# <a name="visual-basic-language-walkthroughs"></a>Visual Basic 語言逐步解說

逐步解說提供常見情節的逐步指示，使其成為開始學習產品或特定功能區域的最佳去處。

- [撰寫非同步程式](./programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 說明如何使用 [Async](language-reference/modifiers/async.md) 和 [Await](language-reference/operators/await-operator.md) 建立非同步解決方案。

- [宣告和引發事件](programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 說明如何在 Visual Basic 中宣告和引發事件。

- [處理事件](programming-guide/language-features/events/walkthrough-handling-events.md)  
 示範如何使用標準 `WithEvents` 關鍵字或新的 `AddHandler`/`RemoveHandler` 關鍵字來處理事件。

- [建立和實作介面](programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)  
 示範如何在 Visual Basic 中宣告和實作介面。

- [定義類別](programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 描述如何宣告類別及其欄位、屬性、方法和事件。

- [在 Visual Basic 中撰寫查詢](programming-guide/concepts/linq/walkthrough-writing-queries.md)  
 示範如何使用 Visual Basic 語言功能撰寫 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 查詢運算式。

- [在 Visual Basic 中實作 IEnumerable(Of T)](programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 示範如何建立實作 `IEnumerable(Of String)` 介面的類別和實作 `IEnumerator(Of String)` 介面的類別，以逐行讀取文字檔案。

- [呼叫 Windows API](programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 說明如何使用 `Declare` 陳述式並呼叫 Windows API。 包含如何使用屬性來控制 API 呼叫的封送處理相關資訊，以及如何以類別方法形式公開 API 呼叫的相關資訊。

- [使用 Visual Basic 建立 COM 物件](programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 示範如何使用和不使用 COM 類別範本，在 Visual Basic 中建立 COM 物件。

- [實作 COM 物件的繼承](programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 示範如何使用 Visual Basic 6.0 以建立包含類別的 COM 物件，並將它作為 Visual Basic 中的基底類別。

- [判斷 My.Application.Log 寫入資訊的位置](developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 說明預設的 `My.Application.Log` 設定，以及如何判斷應用程式的設定。

- [變更 My.Application.Log 寫入資訊的位置](developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 示範如何覆寫記錄事件資訊的預設 `My.Application.Log` 和 `My.Log` 設定，並使 `Log` 物件寫入至其他記錄檔接聽程式。

- [篩選 My.Application.Log 輸出](developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)  
 示範如何變更 `My.Application.Log` 物件的預設記錄檔篩選。

- [建立自訂的記錄檔接聽程式](developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 示範如何建立自訂記錄檔接聽程式，並將它設定為接聽 `My.Application.Log` 物件的輸出。

- [從 Managed 組件內嵌類型](../standard/assembly/embed-types-visual-studio.md)  
 描述如何建立內嵌類型的組件和用戶端程式。

- [驗證密碼確實複雜 (Visual Basic)](programming-guide/language-features/strings/walkthrough-validating-that-passwords-are-complex.md)  
 示範如何檢查強式密碼的特性，並以密碼未通過哪些檢查的資訊來更新字串參數。

- [在 Visual Basic 中為字串加密和解密](programming-guide/language-features/strings/walkthrough-encrypting-and-decrypting-strings.md)  
 示範如何使用 <xref:System.Security.Cryptography.DESCryptoServiceProvider> 類別來加密和解密字串。

- [在 Visual Basic 中管理檔案和資料夾](developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 示範如何使用 Visual Basic 函式來判斷檔案的相關資訊、搜尋檔案中的字串，以及寫入檔案。

- [使用 .NET Framework 方法管理檔案](developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 示範如何使用 .NET Framework 方法來判斷檔案的相關資訊、搜尋檔案中的字串，以及寫入檔案。

- [在 Visual Basic 中保存物件](programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 示範如何建立簡單的物件，並將其資料保存至檔案。

- [逐步解說：以使用時產生功能支援測試優先](/visualstudio/ide/walkthrough-test-first-support-with-the-generate-from-usage-feature)  
 示範如何執行測試優先開發；在這類開發中，您會先撰寫單元測試，再撰寫原始程式碼，以讓測試成功。
