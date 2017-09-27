---
title: "システムの要件 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: 75c8c9daea3f26dc694ae66597649f399a986456
ms.contentlocale: ja-jp
ms.lasthandoff: 09/22/2017

---
# <a name="system-requirements"></a>システム要件
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

このトピックの内容を使用するための要件を一覧表示、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Linux や macOS にします。

## <a name="microsoft-odbc-driver-13-and-131-for-sql-server"></a>Microsoft ODBC Driver 13 および 13.1 for SQL Server

Linux および macOS のドライバーは、次のオペレーティング システムの 64 ビット バージョンでのみ使用できます。

- Apple macOS 10.12 (Sierra)
- Apple OS X 10.11 (許可されて)
- Debian Linux 8
- Red Hat Enterprise Linux 6
- Red Hat Enterprise Linux 7
- SuSE Linux Enterprise Server 11
- SuSE Linux Enterprise Server 12
- Ubuntu Linux 14.04
- Ubuntu Linux 15.10
- Ubuntu Linux 16.04
- Ubuntu Linux 16.10

インストール パッケージ化、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 およびの 13.1 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Linux と macOS 」の説明に従って、配布のパッケージ管理システムを使用してインストールされているときに自動的に、ドライバーの依存関係を解決する[ドライバーをインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)です。

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Microsoft SQL Server 用 ODBC Driver 11  
  
-   64 ビット UnixODBC 2.3.0 Driver Manager (64 ビット SQLLEN/SQLULEN 向けの設計)。 これよりも新しいバージョンの 64 ビット UnixODBC Driver Manager は、Linux 上の ODBC ドライバーではサポートされません。 詳細については、「 [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) 」をご覧ください。  
  
-   ODBC ドライバー用**Red Hat Enterprise Linux 5 (64 ビット)** 、次のパッケージが必要であり、ここでダウンロードできます: [Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   glibc  
    -   libgcc  
    -   libstdc++  
    -   e2fsprogs-libs  
    -   krb5-libs  
    -   openssl  
  
-   ODBC ドライバー用**Red Hat Enterprise Linux 6 (64 ビット)** 、次のパッケージが必要であり、ここでダウンロードできます: [Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](http://go.microsoft.com/fwlink/?LinkId=267321)  
    -   glibc  
    -   libgcc  
    -   libstdc++  
    -   libuuid  
    -   krb5-libs  
    -   openssl  
  
-   ODBC ドライバー用**SUSE Linux Enterprise 11 Service Pack 2 (64 ビット)** 、次のパッケージが必要であり、ここでダウンロードできます: [for SQL Server - SUSE Linux の Microsoft ODBC Driver 11 プレビュー](http://go.microsoft.com/fwlink/?LinkId=264916)  
    -   glibc  
    -   libstdc++46  
    -   libgcc46  
    -   libuuid1  
    -   krb5  
    -   libopenssl0_9_8  
  
## <a name="see-also"></a>参照
[ドライバー マネージャーのインストール](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[このバージョンのドライバーの既知の問題](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)  

