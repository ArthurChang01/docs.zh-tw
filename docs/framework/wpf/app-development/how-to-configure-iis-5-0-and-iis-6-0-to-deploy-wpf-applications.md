---
title: 如何：設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
ms.openlocfilehash: d557ac6cd380edcbc93b5315f6356697817274bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740414"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>如何：設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式

您可以從大部分的 Web 服務器部署 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式，只要它們已設定適當的多用途網際網路郵件延伸（MIME）類型即可。 根據預設，Microsoft Internet Information Services （IIS）7.0 是使用這些 MIME 類型來設定，但 Microsoft Internet Information Services （IIS）5.0 和 Microsoft Internet Information Services （IIS）6.0 則不是。

本主題說明如何設定 Microsoft Internet Information Services （IIS）5.0 和 Microsoft Internet Information Services （IIS）6.0 以部署 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。

> [!NOTE]
> 您可以檢查登錄中的*UserAgent*字串，以判斷系統是否已安裝 .NET Framework。 如需詳細資訊和檢查*UserAgent*字串以判斷系統上是否已安裝 .NET Framework 的腳本，請參閱偵測[是否已安裝 .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)。

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>調整內容到期設定

您應該將內容到期設定調整為 1 分鐘。 下列程式概述如何使用 IIS 來執行這項操作。

1. 按一下 [開始] 功能表，指向 [系統管理工具]，然後按一下 [Internet Information Services (IIS) 管理員]。 您也可以從命令列使用 "%SystemRoot%\system32\inetsrv\iis.msc" 來啟動此應用程式。

2. 展開 IIS 樹狀結構，直到您找到 [**預設的網站**] 節點。

3. 以滑鼠右鍵按一下 [預設的網站]，然後從操作功能表選取 [屬性]。

4. 選取 [HTTP 標頭] 索引標籤，然後按一下 [啟用內容到期日]。

5. 設定內容於 1 分鐘後過期。

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>註冊 MIME 類型和副檔名

您必須註冊數個 MIME 類型和副檔名，才能讓用戶端系統上的瀏覽器載入正確的處理常式。 您需要新增下列類型：

|副檔名|MIME 類型|
|---------------|---------------|
|.manifest|application/manifest|
|.xaml|application/xaml+xml|
|.application|application/x-ms-application|
|.xbap|application/x-ms-xbap|
|.deploy|application/octet-stream|
|.xps|application/vnd.ms-xpsdocument|

> [!NOTE]
> 您不需要在用戶端系統上註冊 MIME 類型或副檔名。 當您安裝 Microsoft .NET Framework 時，它們會自動註冊。

下列 Microsoft Visual Basic Scripting Edition （VBScript）範例會自動將必要的 MIME 類型新增至 IIS。 若要使用指令碼，請將程式碼複製到伺服器上的 .vbs 檔案。 然後，從命令列執行檔案，或在 Microsoft Windows Explorer 中按兩下該檔案，以執行腳本。

```vb
' This script adds the necessary Windows Presentation Foundation MIME types
' to an IIS Server.
' To use this script, just double-click or execute it from a command line.
' Running this script multiple times results in multiple entries in the IIS MimeMap.

Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec
Const ADS_PROPERTY_UPDATE = 2

' Set the MIME types to be added
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _
    "application/xaml+xml", ".application", "application/x-ms-application", _
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _
    ".xps", "application/vnd.ms-xpsdocument")

' Get the MimeMap object
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")

' Call AddMimeType for every pair of extension/MIME type
For counter = 0 to UBound(MimeTypesToAddArray) Step 2
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)
Next

' Create a Shell object
Set WshShell = CreateObject("WScript.Shell")

' Stop and Start the IIS Service
Set oExec = WshShell.Exec("net stop w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = WshShell.Exec("net start w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = Nothing

' Report status to user
WScript.Echo "Windows Presentation Foundation MIME types have been registered."

' AddMimeType Sub
Sub AddMimeType (Ext, MType)

    ' Get the mappings from the MimeMap property.
    MimeMapArray = MimeMapObj.GetEx("MimeMap")

    ' Add a new mapping.
    i = UBound(MimeMapArray) + 1
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> 多次執行此腳本會在 Microsoft Internet Information Services （IIS）5.0 或 Microsoft Internet Information Services （IIS）6.0 元資料庫中建立多個 MIME 對應專案。

執行此腳本之後，您可能不會看到來自 Microsoft Internet Information Services （IIS）5.0 或 Microsoft Internet Information Services （IIS） 6.0 Microsoft Management Console （MMC）的其他 MIME 類型。 不過，這些 MIME 類型已新增至 Microsoft Internet Information Services （IIS）5.0 或 Microsoft Internet Information Services （IIS）6.0 元資料庫。 下列腳本會顯示 Microsoft Internet Information Services （IIS）5.0 或 Microsoft Internet Information Services （IIS）6.0 元資料庫中的所有 MIME 類型。

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

請將指令碼儲存為 `.vbs` 檔案 (例如 `DiscoverIISMimeTypes.vbs`)，然後從命令提示字元使用下列命令來執行：

```console
cscript DiscoverIISMimeTypes.vbs
```
