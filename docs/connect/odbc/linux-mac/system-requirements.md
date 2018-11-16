---
title: システム要件 (ODBC Driver for SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18016780c53575b0416d9a0aa7a8f4499c41de51
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603712"
---
# <a name="system-requirements"></a>システム要件
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

このトピックでは、Linux および macOS の [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を使用する要件について説明します。


## <a name="microsoft-odbc-driver-13-131-and-17-for-sql-server"></a>Microsoft ODBC Driver 13、13.1、17 for SQL Server

Linux と macOS のドライバーは、次のオペレーティング システムの 64 ビット バージョンでのみ使用できます。

|オペレーティング システム|サポートされているドライバーのバージョン|
|------------------------------------|--------------------------------|
|Apple OS X 10.11 (El Capitan)|13、13.1、17|
|Apple macOS 10.12 (Sierra)|13、13.1、17|
|Apple macOS 10.13 (High Sierra)|17| 
|Debian Linux 8|13、13.1、17|
|Debian Linux 9|17|
|RedHat Enterprise Linux 6|13、13.1、17|
|RedHat Enterprise Linux 7|13、13.1、17|
|SuSE Linux Enterprise Server 11|13、13.1、17 <br /><br /> **注:** のみ ODBC Driver 17 に SuSE Linux Enterprise Server 11 SP4 がサポートしています|
|SuSE Linux Enterprise Server 12|13、13.1、17|
|Ubuntu Linux 14.04|13、13.1、17|
|Ubuntu Linux 15.10|13、13.1|
|Ubuntu Linux 16.04|13、13.1、17|
|Ubuntu Linux 16.10|13、13.1|
|Ubuntu Linux 17.10|17|

パッケージのインストール、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13、13.1、17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Linux と macOS で、ドライバーの依存関係」の説明に従って、お使いのディストリビューションのパッケージ管理システムを使用してインストールされているときに自動的に解決します。[ドライバーをインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)します。

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Microsoft SQL Server 用 ODBC Driver 11  
  
-   64 ビット UnixODBC 2.3.0 Driver Manager (64 ビット SQLLEN/SQLULEN 向けの設計)。 これよりも新しいバージョンの 64 ビット UnixODBC Driver Manager は、Linux 上の ODBC ドライバーではサポートされません。 詳細については、「 [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) 」をご覧ください。  
  
-   **Red Hat Enterprise Linux 5 (64 ビット)** 用 ODBC ドライバーの場合、次のパッケージが必要です。また、[SQL Server 用 Microsoft ODBC Driver 11 - Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321) のページでダウンロードできます。  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `e2fsprogs-libs`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   **Red Hat Enterprise Linux 6 (64 ビット)** 用 ODBC ドライバーの場合、次のパッケージが必要です。また、[SQL Server 用 Microsoft ODBC Driver 11 - Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321) のページでダウンロードできます。  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `libuuid`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   **SUSE Linux Enterprise 11 サービス パック 2 (64 ビット)** 用 ODBC ドライバーの場合、次のパッケージが必要です。また、[SQL Server 用 Microsoft ODBC Driver 11 (Preview) - SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916) のページでダウンロードできます。  
    -   `glibc`  
    -   `libstdc++46`  
    -   `libgcc46`  
    -   `libuuid1`  
    -   `krb5`  
    -   `libopenssl0_9_8`  
  
## <a name="see-also"></a>参照
[ドライバー マネージャーのインストール](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[このバージョンのドライバーの既知の問題](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)  
