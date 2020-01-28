---
title: HOW TO：註冊和設定服務 Moniker
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: fc0b2d00bcc8e3b14c491446f16297c1036b783b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747098"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>HOW TO：註冊和設定服務 Moniker

在具有具型別合約的 COM 應用程式中使用 Windows Communication Foundation （WCF）服務標記之前，您必須使用 COM 註冊必要的屬性化型別，並以必要的系結設定 COM 應用程式和名字標記配置.

## <a name="register-the-required-attributed-types-with-com"></a>向 COM 註冊必要的屬性化類型

1. 使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)工具，從 WCF 服務抓取中繼資料合約。 這會產生 WCF 用戶端元件和用戶端應用程式設定檔的原始程式碼。

2. 請確定組件中的型別已標示為 `ComVisible`。 若要這麼做，請將下列屬性新增至 Visual Studio 專案中的*AssemblyInfo.cs*檔案。

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. 將 managed WCF 用戶端編譯為強式名稱的元件。 這樣做將需要以密碼金鑰組 (Key Pairs) 進行簽署。 如需詳細資訊，請參閱[以強式名稱簽署組件](../../../standard/assembly/sign-strong-name.md)。

4. 使用組件註冊 (Regasm.exe) 工具並搭配 `-tlb` 選項，以使用 COM 註冊組件中的型別。

5. 使用全域組件快取 (Gacutil.exe) 工具，將組件新增至全域組件快取中。

    > [!NOTE]
    > 簽署組件並將該組件新增至全域組件快取都是選用性步驟，但這兩個步驟可以簡化在執行階段時，從正確的位置載入組件的程序。

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>使用必要的系結設定來設定 COM 應用程式和標記

- 在用戶端應用程式的設定檔中，將「配置」[中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)所產生的系結定義放在產生的用戶端應用程式設定檔中。 例如，若是名稱為 CallCenterClient.exe 的 Visual Basic 6.0 可執行檔，應該將組態放置在與可執行檔相同之目錄內的 CallCenterConfig.exe.config 檔案中。 用戶端應用程式現在就可使用 Moniker。 請注意，如果使用 WCF 所提供的其中一個標準系結類型，則不需要系結設定。

     接著會註冊下列型別。

    ```csharp
    using System.ServiceModel;

    [ServiceContract]
    public interface IMathService
    {
        [OperationContract]
        public int Add(int x, int y);
        [OperationContract]
        public int Subtract(int x, int y);
    }
    ```

     已使用 `wsHttpBinding` 繫結公開應用程式。 針對提供的型別和應用程式組態，將會使用下列範例 Moniker 字串。

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     或

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     在將參考新增至包含 `IMathService` 型別的組件之後，您就可以從 Visual Basic 6.0 應用程式中使用這些 Moniker 字串，如下列範例程式碼所示。

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     在此範例中，系結設定 `Binding1` 的定義會儲存在用戶端應用程式之適當命名的設定檔中，例如*vb6appname。*

    > [!NOTE]
    > 您可以在 C#、C++ 或其他 .NET 語言應用程式中使用類似的程式碼。

    > [!NOTE]
    > 如果標記的格式不正確或服務無法使用，則對 `GetObject` 的呼叫會傳回「不正確語法」錯誤。 如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。

     雖然本主題著重于從 Visual Basic 6.0 程式碼使用服務名字標記，但您可以使用其他語言的服務標記。 從 C++ 程式碼中使用 Moniker 時，應該以 "no_namespace named_guids raw_interfaces_only" 這個名稱匯入 Svcutil.exe 產生的組件，如下列程式碼所示。

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     這樣會修改匯入的介面定義，讓所有方法都會傳回 `HResult`。 其他傳回值都會轉換為 Out 參數。 整體的執行方法仍然相同。 這樣可讓您在 Proxy 上呼叫方法時，判斷發生例外狀況的原因。 不過這個功能只能用於 C++ 程式碼。

## <a name="see-also"></a>請參閱

- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
