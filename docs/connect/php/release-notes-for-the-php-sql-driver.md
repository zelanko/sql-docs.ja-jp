---
title: リリース ノート Microsoft Drivers for PHP for SQL Server |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6fc3b3b4e815aaa5dba9d49e90ce7e2a4774c2a9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Microsoft Drivers for PHP for SQL Server のリリース ノート
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このページは、の各バージョンで追加された新機能について説明します、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]です。  

## <a name="whats-new-in-version-52"></a>バージョン 5.2 の新機能

- PHP 7.2.1 のサポートとウィンドウ、および 7.2.0 はアップおよび他のプラットフォームでアップ
- Microsoft ODBC Driver 17 のサポート
  - バージョン 17 が既定のすべてのプラットフォームで
- Ubuntu 17.10、Debian 9、および Suse Enterprise Linux 12 のサポート
- Ubuntu 15.10 のドロップのサポート
- Windows 上で機能を CRUD で Always Encrypted のサポート。 詳細については、次を参照してください[SQL Server 用 PHP ドライバーで Always Encrypted を使用する。](../../connect/php/using-always-encrypted-php-drivers.md)
  - Windows 証明書ストアのサポート
  - 以降では、Microsoft ODBC Driver 17 は常に暗号化がサポートのみ
- Linux および macOS 上の非 UTF8 ロケールのサポート
  - Linux および macOS 上の非 UTF8 ロケールは、Microsoft ODBC Driver 17 以降のみサポートします。
- Azure SQL Data Warehouse のサポート
- Azure SQL のマネージ インスタンス (拡張プライベート プレビュー) のサポート


## <a name="whats-new-in-version-43"></a>バージョン 4.3 の新機能

- PHP 7.1 のサポート
- MacOS Sierra のサポートや macOS 許可されて
- 15.10、および 8 Debian、Ubuntu のサポート
- Ubuntu 15.04 のドロップのサポート
- 透過的なネットワーク IP 解決を使用して Always On 可用性グループのサポート。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。
- 制限と sql_variant データ型のサポートを追加します。
- ウィンドウでアイドル接続の回復をサポートします。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。
- 接続プールの Linux および macOS 用のサポート。 詳細については、次を参照してください。[接続プーリング](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)です。
- ActiveDirectoryPassword と SqlPassword による Azure Active Directory 認証をサポートします。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。

## <a name="whats-new-in-version-40"></a>バージョン 4.0 の新機能

- PHP 7.0 のサポート  
- 完全な 64 ビット サポート
- Ubuntu 15.04、Ubuntu 16.04、Red Hat 7 のサポート

## <a name="whats-new-in-version-32"></a>バージョン 3.2 の新機能

- PHP 5.6 のサポート   
- 旧バージョンの PHP 5.5 および 5.4 最新の更新プログラムが含まれています   
- Microsoft ODBC Driver 11 for SQL Server が必要です。  

## <a name="whats-new-in-version-31"></a>バージョン 3.1 の新機能

- PHP 5.5 のサポート  
- Microsoft ODBC Driver 11 for SQL Server が必要です。 以前のバージョンでは、SQL Native Client が必要でした。  

## <a name="whats-new-in-version-30"></a>バージョン 3.0 の新機能  

- PHP 5.4 のサポート  [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 3 では、PHP 5.2 はサポートされていません。  
- AttachDBFileName 接続オプションが追加されています。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
- [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]で追加された LocalDB のサポート。 詳細については、次を参照してください。 [LocalDB のサポート](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)です。
- AttachDBFileName 接続オプションが追加されています。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
- 高可用性のディザスター リカバリー機能のサポート。 詳細については、次を参照してください。 [High Availability, Disaster Recovery のサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)です。
- クライアント側のカーソル (結果セットのメモリ内キャッシュ) のサポート。 詳細については、次を参照してください。[カーソルの種類&#40;SQLSRV ドライバー&#41; ](../../connect/php/cursor-types-sqlsrv-driver.md)と[カーソルの種類&#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)です。
- PDO::ATTR_EMULATE_PREPARES 属性が追加されました。 詳細については、次を参照してください。 [pdo::prepare](../../connect/php/pdo-prepare.md)です。  

## <a name="whats-new-in-version-20"></a>バージョン 2.0 の新機能  
バージョン 2.0 では、PDO_SQLSRV ドライバーのサポートが追加されました。 詳細については、「 [PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)」を参照してください。  

## <a name="see-also"></a>参照  
[Microsoft Drivers for PHP for SQL Server の概要](../../connect/php/overview-of-the-php-sql-driver.md)
