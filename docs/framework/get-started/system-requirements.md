---
title: .NET Framework 系統需求
description: 了解安裝 .NET Framework 4.5 及更新版本的硬體、作業系統和軟體需求。
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
ms.openlocfilehash: f2c22f13f74698b8cbd1474b331d65dcedfa4889
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114555"
---
# <a name="net-framework-system-requirements"></a>.NET Framework 系統需求

本主題中的表格提供下列 .NET Framework 版本的硬體、作業系統和軟體需求：

- .NET Framework 4.5 及其小數點發行版本 (4.5.1 和 4.5.2)。
- .NET Framework 4.6 及其小數點發行版本 (4.6.1 和 4.6.2)。
- .NET Framework 4.7 及其小數點發行版本 (4.7.1 和 4.7.2)。
- .NET Framework 4.8

如需有關 .NET Framework 4.5 之前之 .NET Framework 版本的資訊，請參閱 [.NET Framework 版本和相依性](../migration-guide/versions-and-dependencies.md)。

您用以開發 .NET Framework 應用程式的開發環境，則會有另一組不同的需求。

[!INCLUDE[net-framework-4-versions](../../../includes/net-framework-4x-versions.md)]

如需下載資訊和連結，請參閱[安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)。

如需 .NET Framework 版本支援週期的資訊，請參閱 [Microsoft 支援週期](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO)。

## <a name="hardware-requirements"></a>硬體需求

|                          |        |
| ------------------------ | ------ |
| **處理器**            | 1 GHz  |
| **RAM**                  | 512 MB |
| **磁碟空間 (最小)** |        |
| 32 位元                   | 4.5 GB |
| 64 位元                   | 4.5 GB |

## <a name="installation-requirements"></a>安裝需求

必須有系統管理員權限才能安裝 .NET Framework。 如果您在要安裝 .NET Framework 的電腦上沒有系統管理員權限，請連絡您的網路系統管理員。

## <a name="supported-client-operating-systems"></a>支援的用戶端作業系統

| 作業系統 | 支援的版本 | 與作業系統一起預先安裝 | 可個別安裝 |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows 10 2019 年 5 月更新 | 32 位元和 64 位元 | .NET Framework 4.8 | -- |
| Windows 10 2018 年 10 月更新 | 32 位元和 64 位元 | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows 10 2018 4 月更新 | 32 位元和 64 位元 | .NET Framework 4.7.2 |.NET Framework 4.8|
| Windows 10 Fall Creators Update | 32 位元和 64 位元 | .NET Framework 4.7.1 | .NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows 10 Creators Update | 32 位元和 64 位元 | .NET Framework 4.7 | .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows 10 年度更新 | 32 位元和 64 位元 | .NET Framework 4.6.2 |.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8  |
| Windows 10 11 月更新 | 32 位元和 64 位元 | .NET Framework 4.6.1 | .NET Framework 4.6.2 |
| Windows 10 | 32 位元和 64 位元 | .NET Framework 4.6 | .NET Framework 4.6.1 <br/><br/> .NET Framework 4.6.2 |
| [!INCLUDE[win81](../../../includes/win81-md.md)] | 32 位元、64 位元和 ARM | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| [!INCLUDE[win8](../../../includes/win8-md.md)] | 32 位元、64 位元和 ARM | .NET Framework 4.5 | .NET Framework 4.5.1<br /><br />.NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1 |
| Windows 7 SP1|32 位元和 64 位元 | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Vista SP2|32 位元和 64 位元 | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |
| Windows XP |32 位元和 64 位元 | -- | .NET Framework 4 |

 **注意：**

- 在 Windows 7 系統中，.NET Framework 需要 Windows 7 SP1。 若您使用 Windows 7 而尚未安裝 Service Pack 1，就必須先加以安裝，之後才能安裝 .NET Framework。

- Windows 預先安裝環境 (Windows PE) 支援 .NET Framework 4.5。 並非所有的功能在 Windows PE 上都支援。

- .NET Framework 4 也支援 IA64 平台。

- 對於所有平台，建議您升級至 [Windows Update 網站](https://go.microsoft.com/fwlink/?LinkId=168461)上提供的最新 Windows Service Pack 和安裝重要更新，確保有最佳相容性與安全性。

- 在 64 位元作業系統上，.NET Framework 同時支援 WOW64 (在 64 位元電腦上進行 32 位元處理) 和原生 64 位元處理。

## <a name="supported-server-operating-systems"></a>支援的伺服器作業系統

| 作業系統 | 支援的版本 | 與作業系統一起預先安裝 | 可個別安裝 |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows Server 2019 | 64 位元 | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server，版本 1809 | 64 位元 | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server，版本 1803 | 64 位元 | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server，版本 1709 | 64 位元 | .NET Framework 4.7.1 | .NET Framework 4.7.2|
| Windows Server 2016 | 64 位元 | .NET Framework 4.6.2 | .NET Framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2012 R2 | 64 位元 | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2012 (64 位元版本) | 64 位元| .NET Framework 4.5 | .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2008 R2 SP1|64 位元 | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2008 SP2|32 位元和 64 位元 | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |

 **注意：**

- [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] 包含 .NET Framework 4.5，因此您不需要另外安裝。 同樣地，[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] 也包含 .NET Framework 4.5.1。

- Windows Server 2008 R2 SP1 (含) 更新版本的伺服器核心角色，對於 .NET Framework 的支援有限。 請參閱[伺服器核心 .NET 功能](https://docs.microsoft.com/previous-versions//dd745015(v=vs.85))，以取得不受支援的 API 清單。

- Itanium 型系統的 Windows Server 2008 R2 不支援.NET Framework。

- 在 Windows Server 2008 SP2 上，伺服器核心角色不支援 .NET Framework。

- 對於所有平台，建議您升級至 [Windows Update 網站](https://go.microsoft.com/fwlink/?LinkId=168461)上提供的最新 Windows Service Pack 和重要更新，確保有最佳相容性與安全性。 某些作業系統上可能需要安裝最新的 Windows Service Pack。

- 在 64 位元作業系統上，.NET Framework 同時支援 WOW64 (在 64 位元電腦上進行 32 位元處理) 和原生 64 位元處理。

## <a name="see-also"></a>請參閱

- [安裝指南](../install/index.md)
- [使用者入門](index.md)
- [疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](../install/troubleshoot-blocked-installations-and-uninstallations.md)
