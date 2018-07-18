---
title: Microsoft Drivers for PHP for SQL Server のサポート マトリックス |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: David-Engel
ms.author: v-daveng
manager: ''
ms.openlocfilehash: 9aae3c88e1460304cf4b2bea7dbc529f31393bde
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307921"
---
# <a name="microsoft-php-drivers-for-sql-server-support-matrix"></a>SQL Server のサポート マトリックス用の Microsoft PHP ドライバー
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

  このページには、SQL Server 用 Microsoft PHP ドライバーのサポート表とサポート ライフ サイクル ポリシーが含まれています。

## <a name="microsoft-php-drivers-support-lifecycle-matrix-and-policy"></a>Microsoft PHP ドライバーのサポート ライフ サイクルの表とポリシー
 マイクロソフト サポート ライフサイクル (MSL) ポリシーでは、マイクロソフト製品のサポート ライフサイクルを理解しやすくする、予測可能な情報を提供しています。 PHP のドライバー バージョン 3.x、4.x および 5.x 5 年間のドライバーのリリース日からメイン ストリーム サポートします。 メイン ストリーム サポートがで定義された、[マイクロソフト サポート ライフ サイクルの web サイト](https://support.microsoft.com/lifecycle)です。

 Microsoft PHP ドライバーの拡張およびカスタムのサポート オプションが利用できません。

 次の Microsoft PHP Driver は、指定されたサポートの終了日までサポートされます。

|ドライバー名|ドライバー パッケージのバージョン|メイン ストリーム サポートの終了|
|-|-|-|
|SQL Server 用 Microsoft PHP ドライバー 5.2|5.2|2023 年 2 月 9日|
|SQL Server 用 Microsoft PHP ドライバー 4.3|4.3|2022 年 7 月 6日|
|SQL Server 用 Microsoft PHP ドライバー 4.0|4.0|2021 年 7 月 11日|
|SQL Server 用 Microsoft PHP ドライバー 3.2|3.2|2020 年 3 月 9日に|
|SQL Server 用 Microsoft PHP ドライバー 3.1|3.1|2019 年 12 月 12日|

 次の Microsoft PHP ドライバーがサポートされていません。

|ドライバー名|ドライバー パッケージのバージョン|メイン ストリーム サポートの終了|
|-|-|-|
|SQL Server 用 Microsoft PHP ドライバー 3.0|3.0|2017 年 3 月 6 日|
|SQL Server 用 Microsoft PHP ドライバー 2.0|2.0|、2015 年 8 月 10日|
|SQL Server 用 Microsoft PHP ドライバー 1.0|1.0|2014 年 4 月 28 日|

## <a name="sql-server-version-certified-compatibility"></a>SQL Server のバージョンの互換性を認定
 次のマトリックスには、テスト済みで対応するドライバーのバージョンと互換性のあるとして認定されている SQL Server のバージョンが一覧表示します。 ドライバーの以前のバージョンとの下位互換性を維持するために努めていますが、最新サポートされているドライバーのみをテストして、SQL Server がリリースされると、新しいバージョンの SQL Server に認定します。

|ドライバーのバージョンの SQL Server 用 PHP&#8594;<br />&#8595;SQL Server のバージョン|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|Azure SQL のマネージ インスタンス<br/> (拡張プライベート プレビューで)|Y|Y| | | | | |
|Azure SQL データ ウェアハウス|Y|Y| | | | | |
|SQL Server 2017   |Y|Y| | | | | |
|SQL Server 2016   |Y|Y|Y| | | | |
|SQL Server 2014   |Y|Y|Y|Y|Y| | |
|SQL Server 2012   |Y|Y|Y|Y|Y|Y| |
|SQL Server 2008 R2|Y|Y|Y|Y|Y|Y|Y|
|SQL Server 2008:   | | |Y|Y|Y|Y|Y|

## <a name="php-version-support"></a>PHP のバージョンのサポート
 Microsoft PHP ドライバーのバージョンでは、次のバージョンの PHP がサポートされています。

|ドライバーのバージョンの SQL Server 用 PHP&#8594;<br />&#8595;PHP バージョン|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|7.2|Windows 上の 7.2.1+<br/>他のプラットフォームで 7.2.0+| | | | | | |
|7.1|7.1.0+ |7.1.0+ |       |        |        |        |        |
|7.0|7.0.0+ |7.0.0+ |7.0.0+ |        |        |        |        |
|5.6|       |       |       |5.6.4+  |        |        |        |
|5.5|       |       |       |5.5.16+ |5.5.16+ |        |        |
|5.4|       |       |       |5.4.32  |5.4.32  |5.4.32  |        |
|5.3|       |       |       |        |        |5.3.0   |5.3.0   |
|5.2|       |       |       |        |        |        |5.2.4<br />5.2.13|

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム
 Microsoft PHP ドライバーのバージョンでは、次の Windows オペレーティング システムのバージョンがサポートされています。

|ドライバーのバージョンの SQL Server 用 PHP&#8594;<br />&#8595;オペレーティング システム|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
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

 Microsoft PHP ドライバーの一覧表示されたバージョンとは、次の Linux と Mac のオペレーティング システムのバージョン (64 ビットのみ) がサポートされています。

|ドライバーのバージョンの SQL Server 用 PHP&#8594;<br />&#8595;オペレーティング システム|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|3.0<br />&nbsp;|2.0<br />&nbsp;|
|---|---|---|---|---|---|---|---|
|Ubuntu 17.10 (64 ビット)               |Y  |   |   |   |   |   |   |
|Ubuntu 16.04 (64 ビット)               |Y  |Y  |Y  |   |   |   |   |
|Ubuntu 15.10 (64 ビット)               |   |Y  |   |   |   |   |   |
|Ubuntu 15.04 (64 ビット)               |   |   |Y  |   |   |   |   |
|Debian 9 (64 ビット)                   |Y  |   |   |   |   |   |   |
|Debian 8 (64 ビット)                   |Y  |Y  |   |   |   |   |   |
|Red Hat Enterprise Linux 7 (64 ビット) |Y  |Y  |Y  |   |   |   |   |
|Suse Enterprise Linux (64 ビット) の 12   |Y  |   |   |   |   |   |   |
|macOS Sierra (64 ビット)               |Y  |Y  |   |   |   |   |   |
|macOS 許可されて (64 ビット)           |Y  |Y  |   |   |   |   |   |

## <a name="see-also"></a>参照  
[リリース ノート](../../connect/php/release-notes-for-the-php-sql-driver.md)

[サポート リソース](../../connect/php/support-resources-for-the-php-sql-driver.md)

[システム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)
