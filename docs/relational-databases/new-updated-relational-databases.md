---
title: "更新済み - リレーショナル データベースのドキュメント |Microsoft ドキュメント"
description: "最近変更したドキュメントについては、リレーショナル データベースの更新されたコンテンツのスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 06/30/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 19b664245f45ad45a4c7d1eba249858030fad718
ms.contentlocale: ja-jp
ms.lasthandoff: 07/03/2017

---
<a id="new-and-recently-updated-relational-databases-docs" class="xliff"></a>

# 新規または最近の更新: リレーショナル データベース ドキュメント



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新日の範囲:* &nbsp; **2017 年 5 月 17 日**&nbsp; から &nbsp;**2017 年 6 月 30 日**
- *サブジェクト領域:* &nbsp; **リレーショナル データベース**です。




&nbsp;

<a id="new-articles-created-recently" class="xliff"></a>

## 最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server 2016 の SQL Server インメモリ OLTP 内部](in-memory-oltp/sql-server-in-memory-oltp-internals-for-sql-server-2016.md)
2. [Microsoft SQL データベースでのアダプティブ クエリの処理](performance/adaptive-query-processing.md)
3. [Microsoft SQL プラットフォームでのプライバシーの強化と GDPR 要件への対応に関するガイド](security/microsoft-sql-and-the-gdpr-requirements.md)
4. [sys.dm_db_log_stats (Transact-SQL)](system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)
5. [sys.dm_exec_query_parallel_workers (Transact-SQL)](system-dynamic-management-views/sys-dm-exec-query-parallel-workers-transact-sql.md)



&nbsp;

<a id="updated-articles-with-excerpts" class="xliff"></a>

## 更新されたアーティクルの抜粋が

このセクションでは、大幅な更新が最近発生したアーティクルから収集された更新プログラムの抜粋を表示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

<a id="1-nbsp-altering-memory-optimized-tablesin-memory-oltpaltering-memory-optimized-tablesmd" class="xliff"></a>

### 1.&nbsp; [メモリ最適化テーブルの変更](in-memory-oltp/altering-memory-optimized-tables.md)

*更新日: 2017 年 6 月 23 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([次へ](#TitleNum_2))

<!-- Source markdown line 82.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 8359700b5db24838f1bb273526794c2865bbbe11 41d77cf0bbcf53a1b64d6524a24e5736c5a073da  (PR=2171  ,  Filename=altering-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7) -->



**メモリ最適化テーブルの ALTER TABLE のログ記録**

メモリ最適化テーブルでは、ほとんどの ALTER TABLE シナリオが並列に実行され、トランザクション ログへの書き込みが最適化されるようになりました。 最適化は、メタデータの変更のみをトランザクション ログに記録することによって実現されます。 ただし、次の ALTER TABLE 操作ではシングル スレッドが実行され、ログ最適化は行われません。

この場合のシングル スレッド操作は、変更されたテーブルの内容全体をトランザクション ログに記録します。 シングル スレッド操作の一覧を以下に示します。

- nvarchar(max)、varchar(max)、varbinary(max) などのラージ オブジェクト (LOB) 型を使用するために列を変更または追加します。

- COLUMNSTORE インデックスを追加または削除します。

- [行外列--../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md)に影響するほぼあらゆる操作。

    - 行内の列を行外に移動します。

    - 行外の列を行内に移動します。

    - 新しい行外の列を作成します。

    - *例外:* 既存の行外列が長くなった場合は、最適化された方法でログに記録されます。 
  




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

<a id="2-nbsp-table-and-row-size-in-memory-optimized-tablesin-memory-oltptable-and-row-size-in-memory-optimized-tablesmd" class="xliff"></a>

### 2.&nbsp; [メモリ最適化テーブルのテーブルと行のサイズ](in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)

*更新日: 2017 年 6 月 22 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_1) | [次へ](#TitleNum_3))

<!-- Source markdown line 114.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 27ce0fa2e7bb464f9c3d6e32dd195de3b79abfcd 0a3cacd86024e2b734704ffd37e55ca0b17a0c94  (PR=2163  ,  Filename=table-and-row-size-in-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=fe6de2b16b9792a5399b1c014af72a2a5ee52377) -->



 
  
 行本文サイズ (row body size) の計算について、次の表で説明します。  
  
 行本文サイズには、計算されたサイズと実際のサイズという 2 種類の計算があります。  
  
-   [計算された行本文サイズ] (computed row body size) で示される計算されたサイズは、8,060 バイトという行サイズの上限値を超えるかどうかを判断するために使用されます。  
  
-   [実際の行本文サイズ] (actual row body size) で示される実際のサイズは、メモリ内およびチェックポイント ファイル内の行本文の実際の格納サイズです。  
  
 [計算された行本文サイズ] (computed row body size) と [実際の行本文サイズ] (actual row body size) はほぼ同じ方法で計算されます。 次の表の最後に説明されているとおり、唯一の違いは、(n)varchar(i) 列と varbinary(i) 列のサイズの計算です。 計算された行本体サイズでは、宣言されたサイズ *i* を列のサイズとして使用しますが、実際の行本体サイズではデータの実際のサイズを使用します。  
  
 [実際の行本文サイズ] = SUM([シャロー型のサイズ]) + 2 + 2 * [ディープ型の列の数] として指定した場合、行本文サイズの計算について、次の表で説明します。  
  
|セクション|サイズ|コメント|  
|-------------|----------|--------------|  
|シャロー型の列|SUM([シャロー型のサイズ])。 個々の型のサイズは次のとおりです (バイト単位)。<br /><br /> **Bit**: 1<br /><br /> **Tinyint**: 1<br /><br /> **Smallint**: 2<br /><br /> **Int**: 4<br /><br /> **Real**: 4<br /><br /> **Smalldatetime**: 4<br /><br /> **Smallmoney**: 4<br /><br /> **Bigint**: 8<br /><br /> **Datetime**: 8<br /><br /> **Datetime2**: 8<br /><br /> **Float**: 8<br /><br /> **Money**: 8<br /><br /> **Numeric** (精度 <=18): 8<br /><br /> **Time**: 8<br /><br /> **Numeric**(精度>18): 16<br /><br /> **Uniqueidentifier**: 16||  
|シャロー列の余白|有効な値は次のとおりです。<br /><br /> ディープ型の列が存在し、シャロー列の合計データ サイズが奇数になる場合は 1。<br /><br /> それ以外の場合は、0。|ディープ型は、(var)binary 型と (n)(var)char 型です。|  




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

<a id="3-nbsp-post-migration-validation-and-optimization-guidepost-migration-validation-and-optimization-guidemd" class="xliff"></a>

### 3.&nbsp; [移行後の検証および最適化ガイド](post-migration-validation-and-optimization-guide.md)

*更新日: 2017 年 6 月 21 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_2) | [次へ](#TitleNum_4))

<!-- Source markdown line 27.  ms.author= "harinid".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 faa2e3dd8be3aeb475bf8c7f71617ebf17969892 f2760dfecda10baeb121929b72a4d8164e81185b  (PR=2126  ,  Filename=post-migration-validation-and-optimization-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=dcbeda6b8372b358b6497f78d6139cad91c8097c) -->



[!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] プラットフォームへの移行後に発生する一般的なパフォーマンス シナリオと、その解決方法を以下に示します。 [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] から [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] への移行 (古いバージョンから新しいバージョン) に固有のシナリオや、外部のプラットフォーム (Oracle、DB2、MySQL、Sybase など) から [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] への移行に固有のシナリオが含まれています。

**<a name="CEUpgrade"></a> CE バージョンでの変更によるクエリ パフォーマンス低下**


**適用対象:** [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] から [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] への移行。

古いバージョンの [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] から [!INCLUDE[ssSQL14--../includes/sssql14-md.md)] 以降に移行する場合、および[データベース互換性レベル--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)を最新のレベルにアップグレードする場合、ワークロードのパフォーマンスが低下するリスクにさらされる場合があります。

これは、[!INCLUDE[ssSQL14--../includes/sssql14-md.md)] 以降、すべてのクエリ オプティマイザーの変更が最新の[データベース互換性レベル--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)と連携しているため、プランの変更は、アップグレードの時点ではなく、ユーザーが `COMPATIBILITY_LEVEL` のデータベース オプションを最新のものに変更した時点で発生するためです。 この機能とクエリ ストアの組み合わせによって、アップグレード プロセス中のクエリのパフォーマンスを高いレベルで制御できます。 

[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] で導入されたクエリ オプティマイザーの変更の詳細については、「[Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator](http://msdn.microsoft.com/library/dn673537.aspx)」(SQL Server 2014 の基数推定を使用したクエリ プランの最適化) を参照してください。




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

<a id="4-nbsp-sysquerystoreplan-transact-sqlsystem-catalog-viewssys-query-store-plan-transact-sqlmd" class="xliff"></a>

### 4. &nbsp; [sys.query_store_plan (Transact-SQL)](system-catalog-views/sys-query-store-plan-transact-sql.md)

*更新日: 2017 年 6 月 5 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_3) | [次へ](#TitleNum_5))

<!-- Source markdown line 58.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1b77e34309ba7033578b3c82ed83c8c2fbc93e24 ce4ade9ab906c35cb87068a1fb91c4e1d7549aac  (PR=1940  ,  Filename=sys-query-store-plan-transact-sql.md  ,  Dirpath=docs\relational-databases\system-catalog-views\  ,  MergeCommitSha40=1d363db8e8bd0e1460cdea3c3a7add68e48714c9) -->



**プランの適用の制限事項**

クエリ ストアには、クエリ オプティマイザーに特定の実行プランを使用させるためのメカニズムがあります。 ただし、適用の適用を妨げる可能性のある制限がいくつかあります。 

第 1 に、プランに次の構造が含まれる場合です。
* INSERT BULK ステートメント
* INSERT BULK ステートメント
* 外部テーブルの参照
* 分散クエリまたはフルテキスト操作
* グローバル クエリの使用 
* カーソル
* 無効なスター結合の指定 

第 2 に、プランが依存しているオブジェクトが使用できなくなった場合です。
* データベース (プランの基になっているデータベースが存在しなくなった場合)
* インデックス (存在しない場合、または無効になった場合)

最後に、プラン自体に問題がある場合です。
* クエリに対して有効ではない
* クエリ オプティマイザーが許可されている操作の数を超えた
* プランの XML の形式が正しくない




&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

<a id="5-nbsp-manage-retention-of-historical-data-in-system-versioned-temporal-tablestablesmanage-retention-of-historical-data-in-system-versioned-temporal-tablesmd" class="xliff"></a>

### 5.&nbsp;[システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)

*Updated: 2017-05-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_4))

<!-- Source markdown line 425.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ee69beb6a46913934d4a322f5d95343cc86f2ec4 94da98fec4ab16636a4581c16eb4456e2d1ff66b  (PR=1777  ,  Filename=manage-retention-of-historical-data-in-system-versioned-temporal-tables.md  ,  Dirpath=docs\relational-databases\tables\  ,  MergeCommitSha40=5bd0e1d3955d898824d285d28979089e2de6f322) -->



**テンポラル履歴保有期間ポリシーのアプローチを使用します。**

> **注:**テンポラル履歴保有期間ポリシーを使用する方法は [!INCLUDE [sqldbesa--../../includes/sqldbesa-md.md)]、SQL Server 2017 年 1 CTP 1.3 から開始します。  

テンポラル履歴の保有期間を指定できます、個々 のテーブル レベルで構成されている、ポリシーを柔軟なエージングを作成できます。 テンポラルの保有期間を適用することは簡単: 1 つだけのパラメーター テーブルの作成時またはスキーマの変更時に設定する必要があります。

保有ポリシーを定義した後、Azure SQL データベースは対象データの自動クリーンアップの履歴行があるかどうかを定期的に確認を開始します。 一致する行の id および履歴テーブルからそれらの削除のスケジュール設定し、システムによって実行されるバック グラウンド タスクの透過的に行われます。 Age 状態、履歴テーブルの行は、SYSTEM_TIME 期間の終了を表す列に基づいてがチェックされます。 たとえば、保有期間は 6 か月間に設定は、クリーンアップの対象となるテーブルの行は、次の条件を満たしています。
```
ValidTo < DATEADD (MONTH, -6, SYSUTCDATETIME())
```
前の例では、ValidTo 列は、SYSTEM_TIME 期間の終了に対応していることと見なされます。
**保有ポリシーを構成する方法は?**

テンポラル テーブルの保有ポリシーを構成する前にまず、データベース レベルでテンポラル履歴保有期間が有効になっているかどうか。
```
SELECT is_temporal_history_retention_enabled, name
FROM sys.databases
```
データベースのフラグ**is_temporal_history_retention_enabled**既定では、ON に設定されているが、ユーザーが ALTER DATABASE ステートメントを使用して変更できます。 ポイントイン タイム復元操作後に OFF に自動的に設定されます。 データベースの一時的な履歴保有期間のクリーンアップを有効にするには、次のステートメントを実行します。





&nbsp;

<a name="compactupdatedlist"/>

<a id="compact-list-of-articles-updated-recently" class="xliff"></a>

## 最近更新されたアーティクルの圧縮のリスト

この圧縮リストは、前のセクションに記載されているすべての更新されたアーティクルへのリンクを提供します。

1. [メモリ最適化テーブルの変更](#TitleNum_1)
2. [メモリ最適化テーブルのテーブルと行のサイズ](#TitleNum_2)
3. [移行後の検証および最適化ガイド](#TitleNum_3)
4. [sys.query_store_plan (Transact-SQL)](#TitleNum_4)
5. [システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](#TitleNum_5)




<a name="sisters2"/>

&nbsp;

<a id="sister-articles" class="xliff"></a>

## 関連記事

このセクションでは、同じ GitHub.com リポジトリ [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

<!--  20170630-1150  -->

<a id="subject-areas-which-do-have-new-or-recently-updated-articles" class="xliff"></a>

#### 新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (12 + 2): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (1 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 2): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (3 + 0): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (1 + 2): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (2 + 8): **SQL 用の Linux** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (1 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (5 + 5): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (2 + 0): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 4): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (1 + 0): **SQL 用のツール**に関するドキュメント](../tools/new-updated-tools.md)


<a id="subject-areas-which-have-no-new-or-recently-updated-articles" class="xliff"></a>

#### 新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


&nbsp;


