---
title: システム要件 (ODBC Driver for SQL Server)
description: ここでは、Linux オペレーティング システムおよび macOS オペレーティング システムでの ODBC Driver for SQL Server のシステム要件について説明します。
ms.custom: ''
ms.date: 03/18/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01a5dd44d111fd72d76db244c8135d3bdde00ec8
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2020
ms.locfileid: "86391757"
---
# <a name="system-requirements-linux-and-macos"></a>システム要件 (Linux および macOS)

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

このトピックでは、Linux および macOS の [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を使用する要件について説明します。

## <a name="sql-version-compatibility"></a>SQL バージョンの互換性

Linux および macOS ドライバーの SQL バージョンの互換性は、[Windows ドライバーの SQL バージョンの互換性](../windows/system-requirements-installation-and-driver-files.md#sql-version-compatibility)と同じです。

## <a name="operating-system-support"></a>オペレーティング システムのサポート

Linux ドライバーおよび macOS ドライバーのバージョン 17、13.1、13 は、次のオペレーティング システムの x64 アーキテクチャでサポートされています。

|サポートされるオペレーティング システム     |17.5|17.4|17.3|17.2|17.1|17.0|13.1|13|
|-------------------------------|----|----|----|----|----|----|----|--|
|Apple OS X 10.11 (El Capitan)  | |Y|Y|Y|Y|Y|Y|Y|
|Apple macOS 10.12 (Sierra)     | |Y|Y|Y|Y|Y|Y|Y|
|Apple macOS 10.13 (High Sierra)|Y|Y|Y|Y|Y|Y|Y|Y|
|Apple macOS 10.14 (Mojave)     |Y|Y|Y| | | | | |
|Apple macOS 10.15 (Catalina)   |Y| | | | | | | |
|Alpine Linux 3.11              |Y| | | | | | | |
|Debian Linux 8                 | |Y|Y|Y|Y|Y|Y|Y|
|Debian Linux 9                 |Y|Y|Y|Y|Y|Y|Y|Y|
|Debian Linux 10                |Y|Y| | | | | | |
|Oracle Linux 8                 |Y| | | | | | | |
|RedHat Enterprise Linux 6      |Y|Y|Y|Y|Y|Y|Y|Y|
|RedHat Enterprise Linux 7      |Y|Y|Y|Y|Y|Y|Y|Y|
|RedHat Enterprise Linux 8      |Y|Y| | | | | | |
|SUSE Linux Enterprise Server 11<sup>1</sup>|Y|Y|Y|Y|Y|Y|Y|Y|
|SUSE Linux Enterprise Server 12|Y|Y|Y|Y|Y|Y|Y|Y|
|SUSE Linux Enterprise Server 15|Y|Y|Y| | | | | |
|Ubuntu Linux 14.04             | |Y|Y|Y|Y|Y|Y|Y|
|Ubuntu Linux 16.04             |Y|Y|Y|Y|Y|Y|Y|Y|
|Ubuntu Linux 18.04             |Y|Y|Y|Y| | | | |
|Ubuntu Linux 19.10             |Y| | | | | | | |

<sup>1</sup> ODBC Driver 17 では、SUSE Linux Enterprise Server 11 SP4 のみがサポートされています

Linux と macOS 上の [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13、13.1、17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストール パッケージでは、[ODBC ドライバーをインストールする (Linux)](installing-the-microsoft-odbc-driver-for-sql-server.md) および [ODBC ドライバーをインストールする (macOS)](install-microsoft-odbc-driver-sql-server-macos.md) の手順に従って、ディストリビューションのパッケージ管理システムを使用してドライバーをインストールすると、ドライバーの依存関係が自動的に解決されます。

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Microsoft SQL Server 用 ODBC Driver 11  
  
* 64 ビット UnixODBC 2.3.0 Driver Manager (64 ビット SQLLEN/SQLULEN 向けの設計)。 これよりも新しいバージョンの 64 ビット UnixODBC Driver Manager は、Linux 上の ODBC ドライバーではサポートされません。 詳細については、「 [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) 」をご覧ください。  
  
* **Red Hat Enterprise Linux 5 (64 ビット)** 用 ODBC ドライバーの場合、次のパッケージが必要です。また、[SQL Server 用 Microsoft ODBC Driver 11 - Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321) のページでダウンロードできます。  
  * `glibc`  
  * `libgcc`  
  * `libstdc++`  
  * `e2fsprogs-libs`  
  * `krb5-libs`  
  * `openssl`  
  
* **Red Hat Enterprise Linux 6 (64 ビット)** 用 ODBC ドライバーの場合、次のパッケージが必要です。また、[SQL Server 用 Microsoft ODBC Driver 11 - Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321) のページでダウンロードできます。  
  * `glibc`  
  * `libgcc`  
  * `libstdc++`  
  * `libuuid`  
  * `krb5-libs`  
  * `openssl`  
  
* **SUSE Linux Enterprise 11 サービス パック 2 (64 ビット)** 用 ODBC ドライバーの場合、次のパッケージが必要です。また、[SQL Server 用 Microsoft ODBC Driver 11 (Preview) - SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916) のページでダウンロードできます。  
  * `glibc`  
  * `libstdc++46`  
  * `libgcc46`  
  * `libuuid1`  
  * `krb5`  
  * `libopenssl0_9_8`  
  
## <a name="see-also"></a>参照

[ドライバー マネージャーのインストール](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)  
[このバージョンのドライバーの既知の問題](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  
[リリース ノート](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)  
