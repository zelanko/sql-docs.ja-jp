---
title: Microsoft SQL Server 用 Drivers for PHP のリリース ノート | Microsoft Docs
ms.custom: ''
ms.date: 02/12/2019
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
manager: jroth
ms.openlocfilehash: b17e45fee91b293524cca39037f15fac15cd881e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66797081"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Microsoft SQL Server 用 Drivers for PHP のリリース ノート

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このページでは、各バージョンで追加された内容、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]します。  

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

## <a name="whats-new-in-version-56"></a>バージョン 5.6 の新機能

| 新しい項目 | 詳細 |
| :------- | :------ |
| PHP 7.3 のサポート。 | &nbsp; |
| PHP 7.0 のドロップのサポート。 | &nbsp; |
| すべてのプラットフォームで Microsoft ODBC Driver 17.3 をサポートします。 | &nbsp; |
| MacOS Mojave をサポートします。 | 17.3 の ODBC ドライバーが必要以上。 |
| Ubuntu 18.10 および Suse Linux 15 をサポートします。 | どちらも ODBC ドライバー 17.3 以降。 |
| Linux Ubuntu 17.10 および El Capitan macOS のサポートを削除します。 | &nbsp; |
| Azure AD アクセス トークンをサポートします。 | Linux および macOS では、ODBC ドライバー 17.2 + と unixODBC 2.3.6+ が必要です。 |
| Azure リソースの管理対象 Id を使用する Azure AD での認証のサポート。 | ODBC ドライバー 17.3 以降が必要です。 |
| フェッチの新機能 | &bull; &nbsp; Datetime をオブジェクトとして返す pdo_sqlsrv 用の新しい PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE フラグです。<br/><br/>&bull; &nbsp; Sqlsrv のステートメント レベルを ReturnDatesAsStrings オプションを追加します。<br/><br/>&bull; &nbsp; フェッチされた結果の 10 進数の値を書式設定の両方のドライバーの接続とステートメント レベルでの新しいオプション。 |
| ユーザーがソースから構築する場合、ドライバーの静的なコンパイルをサポートします。 | &nbsp; |
| フェッチのメタデータをキャッシュし、Unicode 文字列の変換の高速化によってパフォーマンスが向上します。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>バージョン 5.3 の新機能

- すべてのプラットフォームでの Microsoft ODBC Driver 17.2 のサポート
- MacOS High Sierra のサポート (ODBC Driver 17 を必要以上)
- Azure Key Vault Always Encrypted の基本的な CRUD の機能のためこのような Always Encrypted 機能がすべて使用できるサポート Windows、Linux または macOS プラットフォーム[SQL Server 用 PHP ドライバーと共に Always Encrypted を使用](../../connect/php/using-always-encrypted-php-drivers.md)
- Ubuntu の 18.04 LTS (ODBC Driver 17.2 が必要) のサポートします。
- Linux または (ODBC Driver 17.2 が必要) も macOS での接続復元性のためのサポート

## <a name="whats-new-in-version-52"></a>バージョン 5.2 の新機能

- PHP 7.2.1 のサポートと、Windows と 7.2.0 アップおよび他のプラットフォームでアップ
- Microsoft ODBC Driver 17 のサポート
  - バージョン 17 は、すべてのプラットフォームで既定ではようになりました
- Ubuntu 17.10、Debian 9、および Suse Enterprise Linux 12 のサポート
- Ubuntu 15.10 のドロップのサポート
- Windows での CRUD 機能を持つ Always Encrypted をサポートします。 詳しくは、「[SQL Server 用 PHP ドライバーと共に Always Encrypted を使用する](../../connect/php/using-always-encrypted-php-drivers.md)」をご覧ください
  - Windows 証明書ストアのサポート
  - 以降では、Microsoft ODBC Driver 17 は常に暗号化がサポートのみ
- Linux と macOS での非 UTF8 ロケールのサポート
  - Microsoft ODBC Driver 17 以降、Linux と macOS での非 UTF8 ロケールはのみサポートされています
- Azure SQL Data Warehouse のサポート
- Azure SQL Managed Instance (延長されたプライベート プレビュー) のサポート

## <a name="whats-new-in-version-43"></a>バージョン 4.3 の新機能

- PHP 7.1 のサポート
- MacOS Sierra のサポートと macOS El Capitan
- Ubuntu 15.10、および Debian 8 のサポート
- Ubuntu 15.04 のドロップのサポート
- 透過的なネットワーク IP 解決を使用して Always On 可用性グループのサポート。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。
- 制限は sql_variant データ型のサポートが追加されました。
- Windows でアイドル状態の接続の回復性のサポート。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。
- 接続プールの Linux と macOS のサポート。 詳細については、[接続プール](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)に関するページを参照してください。
- ActiveDirectoryPassword SqlPassword と Azure Active Directory 認証のサポート。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。

## <a name="whats-new-in-version-40"></a>バージョン 4.0 の新機能

- PHP 7.0 のサポート  
- 完全な 64 ビット サポート
- Ubuntu 15.04、Ubuntu 16.04、および red Hat 7 のサポート

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
- [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] で追加された LocalDB のサポート。 詳細については、次を参照してください。 [LocalDB のサポート](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)します。
- AttachDBFileName 接続オプションが追加されています。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
- 高可用性のディザスター リカバリー機能のサポート。 詳細については、次を参照してください。[高可用性、ディザスター リカバリーのサポート](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)します。
- クライアント側のカーソル (結果セットのメモリ内キャッシュ) のサポート。 詳細については、「[カーソルの種類 &#40;SQLSRV ドライバー&#41;](../../connect/php/cursor-types-sqlsrv-driver.md)」および「[カーソルの種類 &#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)」を参照してください。
- PDO::ATTR_EMULATE_PREPARES 属性が追加されました。 詳細については、「[PDO::prepare](../../connect/php/pdo-prepare.md)」をご覧ください。  

## <a name="whats-new-in-version-20"></a>バージョン 2.0 の新機能

バージョン 2.0 では、PDO_SQLSRV ドライバーのサポートが追加されました。 詳細については、「 [PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)」を参照してください。  

## <a name="see-also"></a>参照

[Microsoft SQL Server 用 Drivers for PHP の概要](../../connect/php/overview-of-the-php-sql-driver.md)
