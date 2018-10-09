---
title: Microsoft Drivers for PHP for SQL Server のサポート マトリックス |Microsoft Docs
ms.custom: ''
ms.date: 07/20/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
manager: ''
ms.openlocfilehash: 82a8576365889d02381e3b18b622fd541b5b9235
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728700"
---
# <a name="microsoft-php-drivers-for-sql-server-support-matrix"></a>Microsoft PHP Drivers for SQL Server のサポート マトリックス
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

  このページには、Microsoft SQL Server 用 PHP Driver のサポート表とサポート ライフサイクル ポリシーがあります。

## <a name="microsoft-php-drivers-support-lifecycle-matrix-and-policy"></a>Microsoft PHP ドライバーのサポート ライフ サイクルの表とポリシー
 マイクロソフト サポート ライフサイクル (MSL) ポリシーでは、マイクロソフト製品のサポート ライフサイクルを理解しやすくする、予測可能な情報を提供しています。 JDBC ドライバーのバージョン 3.0、4.x、6.x、7.x には、ドライバーのリリース日から 5 年間のメインストリーム サポートが含まれています。 メインストリーム サポートについては、[マイクロソフト サポート ライフサイクルの Web サイト](https://support.microsoft.com/lifecycle)で定義されています。

 延長サポートとカスタム サポートのオプションは、Microsoft PHP Driver では使用できません。

 次の Microsoft PHP Driver は、表示されているサポートの終了日までサポートされます。

|ドライバー名|ドライバー パッケージのバージョン|メイン ストリーム サポートの終了|
|-|-|-|
|SQL Server 用 Microsoft PHP ドライバー 5.3|5.3|2023 年 7 月 20日|
|SQL Server 用 Microsoft PHP ドライバー 5.2|5.2|2023 年 2 月 9日|
|SQL Server 用 Microsoft PHP ドライバー 4.3|4.3|2022 年 7 月 6 日|
|SQL Server 用 Microsoft PHP ドライバー 4.0|4.0|2021 年 7 月 11 日|
|Microsoft PHP Drivers 3.2 for SQL Server|3.2|2020 年 3 月 9日に|
|Microsoft PHP Drivers 3.1 for SQL Server|3.1|2019 年 12 月 12日|

 次の Microsoft PHP ドライバーはサポートされなくなりました。

|ドライバー名|ドライバー パッケージのバージョン|メイン ストリーム サポートの終了|
|-|-|-|
|Microsoft PHP Drivers 3.0 for SQL Server|3.0|2017 年 3 月 6 日|
|Microsoft PHP Drivers 2.0 for SQL Server|2.0|2015 年 8 月 10 日|
|SQL Server 用 Microsoft PHP ドライバー 1.0|1.0|2014 年 4 月 28 日|

## <a name="sql-server-version-certified-compatibility"></a>SQL Server のバージョンの互換性を認定
 次の表は、テストして、対応するバージョンのドライバーと互換性のあるものとして認定されている SQL Server のバージョンを一覧表示します。 以前のバージョンのドライバーとの下位互換性を維持するために努力しますが、最新サポートされているドライバーのみをテストして、SQL Server がリリースされると、新しい SQL Server のバージョンを認定します。

|SQL Server ドライバーのバージョンの PHP&#8594;<br />&#8595; SQL Server のバージョン|5.3 および 5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|Azure SQL Managed Instance<br/> (延長プライベート プレビュー)|Y|Y| | | | | |
|Azure SQL データ ウェアハウス|Y|Y| | | | | |
|SQL Server 2017   |Y|Y| | | | | |
|SQL Server 2016   |Y|Y|Y| | | | |
|SQL Server 2014   |Y|Y|Y|Y|Y| | |
|SQL Server 2012   |Y|Y|Y|Y|Y|Y| |
|SQL Server 2008 R2|Y|Y|Y|Y|Y|Y|Y|
|SQL Server 2008:   | | |Y|Y|Y|Y|Y|

## <a name="php-version-support"></a>PHP バージョンのサポート
 Microsoft PHP ドライバーの一覧表示されているバージョンでは、次のバージョンの PHP がサポートされています。

|SQL Server ドライバーのバージョンの PHP&#8594;<br />&#8595; PHP バージョン|5.3 および 5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|7.2|Windows で 7.2.1+<br/>他のプラットフォームで 7.2.0+| | | | | | |
|7.1|7.1.0+ |7.1.0+ |       |        |        |        |        |
|7.0|7.0.0+ |7.0.0+ |7.0.0+ |        |        |        |        |
|5.6|       |       |       |5.6.4+  |        |        |        |
|5.5|       |       |       |5.5.16+ |5.5.16+ |        |        |
|5.4|       |       |       |5.4.32  |5.4.32  |5.4.32  |        |
|5.3|       |       |       |        |        |5.3.0   |5.3.0   |
|5.2|       |       |       |        |        |        |5.2.4<br />5.2.13|

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム
 Microsoft PHP ドライバーの一覧表示されているバージョンでは、次の Windows オペレーティング システムのバージョンがサポートされています。

|SQL Server ドライバーのバージョンの PHP&#8594;<br />&#8595; オペレーティング システム|5.3 および 5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|Windows Server 2016                 |Y  |Y  |   |   |   |   |   |
|Windows Server 2012 R2              |Y  |Y  |Y  |Y  |Y  |   |   |
|Windows Server 2012                 |Y  |Y  |Y  |Y  |Y  |   |   |
|Windows Server 2008 R2 SP1          |   |   |Y  |Y  |Y  |Y  |   |
|Windows Server 2008 R2              |   |   |   |   |   |   |Y  |
|Windows Server 2008 SP2             |   |   |Y  |Y  |Y  |Y  |   |
|Windows Server 2008                 |   |   |   |   |   |   |Y  |
|Windows Server 2003 SP1             |   |   |   |   |   |   |Y  |
|Windows 10                          |Y  |Y  |Y  |   |   |   |   |
|Windows 8.1                         |Y  |Y  |Y  |Y  |Y  |   |   |
|Windows 8                           |   |Y  |Y  |Y  |Y  |   |   |
|Windows 7 SP1                       |   |   |Y  |Y  |Y  |Y  |   |
|Windows Vista SP2                   |   |   |Y  |Y  |Y  |Y  |Y  |
|Windows XP SP3                      |   |   |   |   |   |   |Y  |

 Microsoft PHP ドライバーの一覧表示されているバージョンでは、次の Linux と Mac のオペレーティング システムのバージョン (64 ビットのみ) がサポートされています。

|SQL Server ドライバーのバージョンの PHP&#8594;<br />&#8595; オペレーティング システム|5.3<br />&nbsp;|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|--|---|---|---|---|---|---|---|---|
|Ubuntu 18.04 (64 ビット)               |Y  |   |   |   |   |   |   |   |
|Ubuntu 17.10 (64 ビット)               |Y  |Y  |   |   |   |   |   |   |
|Ubuntu 16.04 (64 ビット)               |Y  |Y  |Y  |Y  |   |   |   |   |
|Ubuntu 15.10 (64 ビット)               |   |   |Y  |   |   |   |   |   |
|Ubuntu 15.04 (64 ビット)               |   |   |   |Y  |   |   |   |   |
|Debian 9 (64 ビット)                   |Y  |Y  |   |   |   |   |   |   |
|Debian 8 (64 ビット)                   |Y  |Y  |Y  |   |   |   |   |   |
|Red Hat Enterprise Linux 7 (64 ビット) |Y  |Y  |Y  |Y  |   |   |   |   |
|Suse Enterprise Linux (64 ビット) の 12   |Y  |Y  |   |   |   |   |   |   |
|macOS High Sierra (64 ビット)          |Y  |   |   |   |   |   |   |   |
|macOS Sierra (64 ビット)               |Y  |Y  |Y  |   |   |   |   |   |
|macOS El Capitan (64 ビット)           |Y  |Y  |Y  |   |   |   |   |   |

## <a name="see-also"></a>参照  
[リリース ノート](../../connect/php/release-notes-for-the-php-sql-driver.md)

[サポート リソース](../../connect/php/support-resources-for-the-php-sql-driver.md)

[システム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)
