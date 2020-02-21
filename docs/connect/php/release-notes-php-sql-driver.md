---
title: Microsoft SQL Server 用 Drivers for PHP のリリース ノート | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: v-dapugl, kenvh
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5e279ba446e790a2262e5f0effe160632065dcba
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76941217"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Microsoft SQL Server 用 Drivers for PHP のリリース ノート

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このページでは、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] の各バージョンに追加された機能について説明します。  

<!--
Hello, We are standardizing the format of content inside our Release Notes (or What's New) articles.
Instead of bullets (or paragraphs), we have shifted to the 2-column format you see for H2 **What's New in Version 5.6**.
It is not necessary to reformat all the older H2 sections in this Release Notes file, but.....

Going forward, please be sure to use the 2-column format.

Also, all Release Notes .md file names now must begin with 'release-notes-*.md'.  And no filler words.
The 5.6 edition of this file is being renamed.....
FROM:  'release-notes-for-the-php-sql-driver.md'
TO  :  'release-notes-php-sql-driver.md'

For any questions, ask GeneMi or CraigG.
Thanks a lot.  2019-03-28  (DevO= 1467988)
-->

## <a name="whats-new-in-version-58"></a>バージョン 5.8 の新機能

| [新しい項目] | 詳細 |
| :------- | :------ |
| PHP 7.4 のサポートが追加されました。 | &nbsp; |
| PHP 7.1 のサポートを終了しました。 | &nbsp; |
| すべてのプラットフォーム上で Microsoft ODBC Driver 17.5 のサポートが追加されました。 | &nbsp; |
| Debian 10 および Red Hat 8 のサポートが追加されました。 | 両方とも、ODBC Driver 17.4 以降を必要とします。 |
| macOS Catalina、Alpine Linux 3.11<sup>1</sup>、および Ubuntu 19.10 のサポートが追加されました。 | すべて、ODBC Driver 17.5 以降を必要とします。 |
| SQL Server 2008 R2、macOS Sierra、Ubuntu 18.10、および Ubuntu 19.04 のサポートを終了しました。 | &nbsp; |
| SQL Server に接続するときの言語オプションがサポートされます。 | &nbsp; |
| PHP 7.2 で導入された PHP 拡張文字列型がサポートされます。 | &nbsp; |
| データ分類の秘密度メタデータの取得がサポートされます。 | SQL Server 2019 および ODBC Driver 17.4.2 以降が必要になります。 |
| セキュリティで保護されたエンクレーブが設定された Always Encrypted をサポートします。 | ODBC Driver 17.4 以降が必要になります。 |
| Linux および macOS でのロケール設定用の構成可能なオプションがサポートされます。 |
| フェッチ時にメタデータをキャッシュし、冗長な呼び出しを省略することで、パフォーマンスが向上しました。 | &nbsp; |
| &nbsp; | &nbsp; |

<sup>1</sup> Alpine Linux サポートは、バージョン 5.8 の試験段階です。

## <a name="whats-new-in-version-56"></a>バージョン 5.6 の新機能

| [新しい項目] | 詳細 |
| :------- | :------ |
| PHP 7.3 のサポート。 | &nbsp; |
| PHP 7.0 のサポートを終了しました。 | &nbsp; |
| すべてのプラットフォーム上で Microsoft ODBC Driver 17.3 がサポートされます。 | &nbsp; |
| macOS Mojave のサポート。 | ODBC Driver 17.3 以降が必要になります。 |
| Ubuntu 18.10 および Suse Linux 15 のサポート。 | 両方とも、ODBC Driver 17.3 以降を必要とします。 |
| Linux Ubuntu 17.10 および macOS El Capitan のサポートを終了しました。 | &nbsp; |
| Azure AD アクセス トークンのサポート。 | Linux および macOS では、ODBC Driver 17.2 以降および unixODBC 2.3.6 以降が必要になります。 |
| Azure リソース用のマネージド ID を使用した Azure AD による認証がサポートされます。 | ODBC Driver 17.3 以降が必要になります。 |
| 新しいフェッチ機能 | &bull; &nbsp; pdo_sqlsrv から datetime をオブジェクトとして返すための新しい PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE フラグ。<br/><br/>&bull; &nbsp; ReturnDatesAsStrings オプションを sqlsrv のステートメント レベルに追加します。<br/><br/>&bull; &nbsp; フェッチされた結果内で 10 進数を書式設定するための、両方のドライバー用の接続レベルおよびステートメント レベルでの新しいオプション。 |
| ユーザーがソースからビルドすることを選んだ場合に、ドライバーの静的コンパイルがサポートされます。 | &nbsp; |
| フェッチ時にメタデータをキャッシュし、Unicode 文字列の変換を高速化することで、パフォーマンスが向上しました。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>バージョン 5.3 の新機能

- すべてのプラットフォーム上で Microsoft ODBC Driver 17.2 がサポートされます
- macOS High Sierra のサポート (ODBC Driver 17 以降が必要になります)
- [SQL Server 用 PHP ドライバーと共に Always Encrypted を使用して](../../connect/php/using-always-encrypted-php-drivers.md)、サポート対象のすべての Windows、Linux、または macOS プラットフォーム上で Always Encrypted 機能を利用可能にする基本の CRUD 機能に対して、Always Encrypted 対応の Azure Key Vault がサポートされます
- Ubuntu 18.04 LTS がサポートされます (ODBC Driver 17.2 が必要になります)
- Linux または macOS での接続の回復性もサポートされます (ODBC Driver 17.2 が必要になります)

## <a name="whats-new-in-version-52"></a>バージョン 5.2 の新機能

- Windows 上では PHP 7.2.1 以降、他のプラットフォーム上では 7.2.0 以降がサポートされます
- Microsoft ODBC Driver 17 のサポート
  - すべてのプラットフォーム上でバージョン 17 が既定になりました
- Ubuntu 17.10、Debian 9、および Suse Enterprise Linux 12 のサポート
- Ubuntu 15.10 のサポートを終了しました
- Windows 上で CRUD 機能を利用した Always Encrypted がサポートされます。 詳しくは、「[SQL Server 用 PHP ドライバーと共に Always Encrypted を使用する](../../connect/php/using-always-encrypted-php-drivers.md)」をご覧ください
  - Windows 証明書ストアのサポート
  - Always Encrypted は、Microsoft ODBC Driver 17 以降のみでサポートされます
- Linux および macOS 上で UTF8 以外のロケールがサポートされます
  - Linux および macOS 上での UTF8 以外のロケールは、Microsoft ODBC Driver 17 以降のみでサポートされます
- Azure SQL Data Warehouse のサポート
- Azure SQL Managed Instance のサポート

## <a name="whats-new-in-version-43"></a>バージョン 4.3 の新機能

- PHP 7.1 のサポート
- macOS Sierra および macOS El Capitan のサポート
- Ubuntu 15.10 および Debian 8 のサポート
- Ubuntu 15.04 のサポートを終了しました
- 透過的なネットワーク IP の解決を利用した Always On 可用性グループがサポートされます。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。
- 制限付きの sql_variant データ型のサポートが追加されました。
- Windows での、アイドル状態の接続の回復性のサポート。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。
- Linux と macOS 向けの接続プールのサポート。 詳細については、[接続プール](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)に関するページを参照してください。
- ActiveDirectoryPassword および SqlPassword を利用した Azure Active Directory Authentication がサポートされます。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。

## <a name="whats-new-in-version-40"></a>バージョン 4.0 の新機能

- PHP 7.0 のサポート  
- 完全な 64 ビットのサポート
- Ubuntu 15.04、Ubuntu 16.04、および RedHat 7 のサポート

## <a name="whats-new-in-version-32"></a>バージョン 3.2 の新機能

- PHP 5.6 のサポート   
- 旧バージョンの PHP 5.5 および 5.4 最新の更新プログラムが含まれています   
- Microsoft SQL Server 用 ODBC Driver 11 が必要です  

## <a name="whats-new-in-version-31"></a>バージョン 3.1 の新機能

- PHP 5.5 のサポート  
- Microsoft SQL Server 用 ODBC Driver 11 が必要です。 以前のバージョンでは、SQL Native Client が必要でした。  

## <a name="whats-new-in-version-30"></a>バージョン 3.0 の新機能  

- PHP 5.4 のサポート  [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 3 では、PHP 5.2 はサポートされていません。  
- AttachDBFileName 接続オプションが追加されています。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
- [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] で追加された LocalDB のサポート。 詳細については、「[LocalDB のサポート](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)」を参照してください。
- AttachDBFileName 接続オプションが追加されています。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
- 高可用性のディザスター リカバリー機能のサポート。 詳細については、「[高可用性、障害復旧のサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)」をご覧ください。
- クライアント側のカーソル (結果セットのメモリ内キャッシュ) のサポート。 詳細については、「[カーソルの種類 &#40;SQLSRV ドライバー&#41;](../../connect/php/cursor-types-sqlsrv-driver.md)」および「[カーソルの種類 &#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)」を参照してください。
- PDO::ATTR_EMULATE_PREPARES 属性が追加されました。 詳細については、「[PDO::prepare](../../connect/php/pdo-prepare.md)」をご覧ください。  

## <a name="whats-new-in-version-20"></a>バージョン 2.0 の新機能

バージョン 2.0 では、PDO_SQLSRV ドライバーのサポートが追加されました。 詳細については、「 [PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)」を参照してください。  

## <a name="see-also"></a>参照

[Microsoft SQL Server 用 Drivers for PHP の概要](../../connect/php/overview-of-the-php-sql-driver.md)
