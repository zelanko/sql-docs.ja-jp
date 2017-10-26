---
title: "PHP SQL ドライバーのリリース ノート |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2c63079bda91844995540aade94bac397be6b94c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="release-notes-for-the-php-sql-driver"></a>PHP SQL ドライバーのリリース ノート
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、各バージョンで追加された新機能について説明します、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]です。  

## <a name="whats-new-in-version-43"></a>バージョン 4.3 の新機能

- PHP 7.1 のサポート
- Mac OS Sierra と許可されて Mac OS のサポート
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
- [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]で追加された LocalDB のサポート。 詳細については、「 [PHP Driver for SQL Server Support for LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)」を参照してください。
- AttachDBFileName 接続オプションが追加されています。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
- 高可用性のディザスター リカバリー機能のサポート。 詳細については、「 [PHP Driver for SQL Server Support for High Availability, Disaster Recovery](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)」(高可用性、障害復旧の PHP Driver for SQL Server のサポート) を参照してください。
- クライアント側のカーソル (結果セットのメモリ内キャッシュ) のサポート。 詳細については、次を参照してください。[カーソルの種類 & #40 です。SQLSRV ドライバー &#41;](../../connect/php/cursor-types-sqlsrv-driver.md)と[カーソルの種類 & #40 です。PDO_SQLSRV ドライバー &#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- PDO::ATTR_EMULATE_PREPARES 属性が追加されました。 詳細については、次を参照してください。 [pdo::prepare](../../connect/php/pdo-prepare.md)です。  
  
## <a name="whats-new-in-version-20"></a>バージョン 2.0 の新機能  
バージョン 2.0 では、PDO_SQLSRV ドライバーのサポートが追加されました。 詳細については、「 [PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Microsoft Drivers for PHP for SQL Server の概要](../../connect/php/overview-of-the-php-sql-driver.md)
  

