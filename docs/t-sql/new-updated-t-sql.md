---
title: 更新済み - T-SQL ドキュメント | Microsoft Docs
description: 最近変更された Transact-SQL に関するドキュメントで更新されたコンテンツのスニペットを示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: t-sql
ms.date: 04/28/2018
ms.openlocfilehash: b1bc891bf7edc4cd82c38c8d647c279828190298
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32725624"
---
# <a name="new-and-recently-updated-transact-sql-docs"></a>新規および最近の更新: Transact-SQL ドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- "*更新日の範囲:* " &nbsp; **2018 年 2 月 3 日** &nbsp;から&nbsp; **2018 年 4 月 28 日**
- *対象分野:* &nbsp; **T-SQL**.




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


***今回は新しい記事はありません。***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](#TitleNum_1)
2. [RESTORE ステートメント (Transact-SQL)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-alter-database-scoped-configuration-transact-sqlstatementsalter-database-scoped-configuration-transact-sqlmd"></a>1.&nbsp; [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](statements/alter-database-scoped-configuration-transact-sql.md)

*更新日: 2018 年 4 月 13 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次へ](#TitleNum_2))

<!-- Source markdown line 150.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f6833910b664d0059a9073589807b195052325b3 bf969f123b22e6ebc650380a6905156f26ed6ca6  (PR=0  ,  Filename=alter-database-scoped-configuration-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



XTP_PROCEDURE_EXECUTION_STATISTICS  **=** { ON | **OFF** }

**適用対象**: *{Included-Content-Goes-Here}*

現在のデータベース内のすべてのネイティブ コンパイル T-SQL モジュールに対し、モジュール レベルで実行統計コレクションを有効また無効にします。 既定値は OFF です。 実行統計は [sys.dm_exec_procedure_stats] に反映されます。

このオプションが ON の場合、または統計コレクションが [sp_xtp_control_proc_exec_stats] によって有効化されている場合は、ネイティブ コンパイル T-SQL モジュールのモジュール レベルの実行統計が収集されます。

XTP_QUERY_EXECUTION_STATISTICS  **=** { ON | **OFF** }

**適用対象**: *{Included-Content-Goes-Here}*

現在のデータベース内のすべてのネイティブ コンパイル T-SQL モジュールに対し、ステートメント レベルで実行統計コレクションを有効また無効にします。 既定値は OFF です。 実行統計は、[sys.dm_exec_query_stats] および[クエリ ストア]に反映されます。

このオプションが ON の場合、または統計コレクションが [sp_xtp_control_query_exec_stats] によって有効化されている場合は、ネイティブ コンパイル T-SQL モジュールのステートメント レベルの実行統計が収集されます。

ネイティブ コンパイル T-SQL モジュールのパフォーマンスの監視の詳細については、「[ネイティブ コンパイル ストアド プロシージャのパフォーマンスの監視]」を参照してください。



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-restore-statements-transact-sqlstatementsrestore-statements-transact-sqlmd"></a>2.&nbsp; [RESTORE ステートメント (Transact-SQL)](statements/restore-statements-transact-sql.md)

*更新日: 2018 年 4 月 13 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_1))

<!-- Source markdown line 339.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2902efb58bb964d3e9a0660956690d37f0397c00 36186a7cffd26ffa54a83e383ffd752dbc568a4d  (PR=0  ,  Filename=restore-statements-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**全般的な解説 - SQL Database マネージ インスタンス**


非同期復元では、クライアント接続が切断された場合でも復元は続行されます。 接続が切断された場合は、[sys.dm_operation_status] ビューで復元操作の状態 (と CREATE および DROP DATABASE) を確認できます。

次のデータベース オプションが設定または上書きされます。後で変更することはできません。

- NEW_BROKER (.bak ファイルでブローカーが有効になっていない場合)
- NEW_BROKER (.bak ファイルでブローカーが有効になっていない場合)
- AUTO_CLOSE=OFF (.bak ファイル内のデータベースに AUTO_CLOSE=ON がある場合)
- RECOVERY FULL (.bak ファイル内のデータベースに SIMPLE または BULK_LOGGED 回復モードがある場合)
- メモリ最適化ファイルグループがソース .bak ファイルにない場合は、追加され、XTP と呼ばれます。 既存のメモリ最適化ファイルグループはすべて XTP に名前変更されます
- SINGLE_USER および RESTRICTED_USER オプションは、MULTI_USER に変換されます

**制限事項 - SQL Database マネージ インスタンス**

これらの制限が適用されます。

- 複数のバックアップ セットを含む .BAK ファイルは復元できません。
- 複数のログ ファイルを含む .BAK ファイルは復元できません。
- .bak に FILESTREAM データが含まれている場合、復元は失敗します。
- アクティブなインメモリ オブジェクトを持つデータベースが含まれているバックアップは、現在復元することができません。
- 任意の時点でインメモリ オブジェクトが存在していたデータベースが含まれているバックアップは、現在復元することができません。
- 読み取り専用モードのデータベースが含まれているバックアップは、現在復元することができません。 この制限は間もなく解除される予定です。

詳細については、[マネージ インスタンス]に関するトピックを参照してください。







## <a name="similar-articles-about-new-or-updated-articles"></a>新規記事または更新記事に関する類似記事

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ある*" 対象領域

- [新規 + 更新 (11 + 6): &nbsp; &nbsp;**SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (18 + 0): &nbsp; &nbsp;**SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (218 + 14):**SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (14 + 0): &nbsp; &nbsp;**SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (3 + 2): &nbsp; &nbsp; **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (3 + 3): &nbsp; &nbsp; **Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (7 + 10): &nbsp; &nbsp;**SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (0 + 2): &nbsp; &nbsp; **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (1 + 3): &nbsp; &nbsp; **SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (2 + 3): &nbsp; &nbsp; **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (1 + 1): &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (5 + 2): &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2): &nbsp; &nbsp; **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (1 + 1): &nbsp; &nbsp; **Tools for SQL** に関するドキュメント](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ない*" 対象領域

- [新規 + 更新 (0 + 0): **SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../samples/new-updated-samples.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)

