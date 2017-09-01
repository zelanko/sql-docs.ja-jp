---
title: "更新 - リレーショナル データベース ドキュメント | Microsoft Docs"
description: "最近変更されたリレーショナル データベースに関するドキュメントで更新されたコンテンツのスニペットを示します。"
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
ms.date: 07/17/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 71203bfa7cb4dcd06cc14ad8e49e5bc1113f8605
ms.openlocfilehash: 519fbd2bc596112dbb1c662d76e4aeeb230ffc36
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>新規または最近の更新: リレーショナル データベース ドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最新の更新は、次の日付範囲と対象で報告されます。



- *更新日の範囲:* &nbsp; **2017 年 5 月 23 日**&nbsp;から &nbsp; **2017 年 7 月 17 日**
- *対象領域:* &nbsp; **リレーショナル データベース**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server 2016 の SQL Server インメモリ OLTP 内部](in-memory-oltp/sql-server-in-memory-oltp-internals-for-sql-server-2016.md)
2. [Microsoft SQL データベースでのアダプティブ クエリの処理](performance/adaptive-query-processing.md)
3. [Microsoft SQL プラットフォームでのプライバシーの強化と GDPR 要件への対応に関するガイド](security/microsoft-sql-and-the-gdpr-requirements.md)
4. [sys.pdw_replicated_table_cache_state (Transact-SQL)](system-catalog-views/sys-pdw-replicated-table-cache-state-transact-sql.md)
5. [sys.trusted_assemblies (Transact-SQL)](system-catalog-views/sys-trusted-assemblies-transact-sql.md)
6. [sys.dm_exec_query_parallel_workers (Transact-SQL)](system-dynamic-management-views/sys-dm-exec-query-parallel-workers-transact-sql.md)
7. [sys.sp_add_trusted_assembly (Transact-SQL)](system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)
8. [sys.sp_drop_trusted_assembly (Transact-SQL)](system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-altering-memory-optimized-tablesin-memory-oltpaltering-memory-optimized-tablesmd"></a>1.&nbsp; [メモリ最適化テーブルの変更](in-memory-oltp/altering-memory-optimized-tables.md)

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

### <a name="2-nbsp-table-and-row-size-in-memory-optimized-tablesin-memory-oltptable-and-row-size-in-memory-optimized-tablesmd"></a>2.&nbsp; [メモリ最適化テーブルのテーブルと行のサイズ](in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)

*更新日: 2017 年 6 月 22 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_1) | [次へ](#TitleNum_3))

<!-- Source markdown line 114.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 27ce0fa2e7bb464f9c3d6e32dd195de3b79abfcd 0a3cacd86024e2b734704ffd37e55ca0b17a0c94  (PR=2163  ,  Filename=table-and-row-size-in-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=fe6de2b16b9792a5399b1c014af72a2a5ee52377) -->



 
  
 行本文サイズ (row body size) の計算について、次の表で説明します。  
  
 行本文サイズには、計算されたサイズと実際のサイズという 2 種類の計算があります。  
  
-   [計算された行本文サイズ]\(computed row body size) で示される計算されたサイズは、8,060 バイトという行サイズの上限値を超えるかどうかを判断するために使用されます。  
  
-   [実際の行本文サイズ]\(actual row body size) で示される実際のサイズは、メモリ内およびチェックポイント ファイル内の行本文の実際の格納サイズです。  
  
 [計算された行本文サイズ]\(computed row body size) と [実際の行本文サイズ]\(actual row body size) はほぼ同じ方法で計算されます。 次の表の最後に説明されているとおり、唯一の違いは、(n)varchar(i) 列と varbinary(i) 列のサイズの計算です。 計算された行本体サイズでは、宣言されたサイズ *i* を列のサイズとして使用しますが、実際の行本体サイズではデータの実際のサイズを使用します。  
  
 [実際の行本文サイズ] = SUM([シャロー型のサイズ]) + 2 + 2 * [ディープ型の列の数] として指定した場合、行本文サイズの計算について、次の表で説明します。  
  
|セクション|サイズ|コメント|  
|-------------|----------|--------------|  
|シャロー型の列|SUM([シャロー型のサイズ])。 個々の型のサイズは次のとおりです (バイト単位)。<br /><br /> **Bit**: 1<br /><br /> **Tinyint**: 1<br /><br /> **Smallint**: 2<br /><br /> **Int**: 4<br /><br /> **Real**: 4<br /><br /> **Smalldatetime**: 4<br /><br /> **Smallmoney**: 4<br /><br /> **Bigint**: 8<br /><br /> **Datetime**: 8<br /><br /> **Datetime2**: 8<br /><br /> **Float**: 8<br /><br /> **Money**: 8<br /><br /> **Numeric** (精度 <=18): 8<br /><br /> **Time**: 8<br /><br /> **Numeric**(精度>18): 16<br /><br /> **Uniqueidentifier**: 16||  
|シャロー列の余白|有効な値は次のとおりです。<br /><br /> ディープ型の列が存在し、シャロー列の合計データ サイズが奇数になる場合は 1。<br /><br /> それ以外の場合は、0。|ディープ型は、(var)binary 型と (n)(var)char 型です。|  




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-post-migration-validation-and-optimization-guidepost-migration-validation-and-optimization-guidemd"></a>3.&nbsp; [移行後の検証および最適化ガイド](post-migration-validation-and-optimization-guide.md)

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

### <a name="4-nbsp-sysquerystoreplan-transact-sqlsystem-catalog-viewssys-query-store-plan-transact-sqlmd"></a>4. &nbsp; [sys.query_store_plan (Transact-SQL)](system-catalog-views/sys-query-store-plan-transact-sql.md)

*更新日: 2017 年 6 月 5 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_3))

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





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>類似した記事

このセクションでは、同じ GitHub.com リポジトリ [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (4 + 4): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (2 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (1 + 2): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (6 + 0): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (13 + 2): **SQL 用の Linux** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (1 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (1 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (8 + 4): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (2 + 2): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (1 + 0): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (1 + 0): **SQL 用のツール**に関するドキュメント](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


&nbsp;


