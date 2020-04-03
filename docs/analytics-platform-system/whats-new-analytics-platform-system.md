---
title: 新機能
description: MPP SQL Server パラレル データ ウェアハウスをホストするオンプレミス のスケール アウト アプライアンスである Microsoft 分析プラットフォーム システムの新機能を参照してください。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: faf3bd1f487fb5c850759fdde3ddecd32bdd3b1f
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625541"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>スケールアウト MPP データ ウェアハウスの分析プラットフォーム システムの新機能
Microsoft 分析プラットフォーム システム (APS) の最新のアプライアンスの更新プログラムの新機能を参照してください。 APS は、MPP SQL Server パラレル データ ウェアハウスをホストするスケールアウトオンプレミス アプライアンスです。 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"
<a name="h2-aps-cu7.6"></a>
## <a name="aps-cu76"></a>APS CU7.6
リリース日 - 2020 年 4 月

### <a name="rename-column"></a>列名の変更
CU7.6 にアップグレードした後、ユーザーが作成したテーブルの列の名前を変更できます。 構文、例、制限事項、および詳細については、[名前の変更 (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/rename-transact-sql)を参照してください。

### <a name="alter-view"></a>ビューを変更する
お客様はビューを変更できるようになります。 詳細については、[ビューの変更 (トランザクション SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-view-transact-sql)を参照してください。

<a name="h2-aps-cu7.5"></a>
## <a name="aps-cu75"></a>APS CU7.5
リリース日 - 2019年9月

### <a name="alter-external-data-source"></a>外部データ ソースの変更
顧客は CU7.5 の更新プログラムを使用して外部データ ソース定義を変更することができます。 Hadoop name ノードの高可用性を持つお客様は、データ ソースを変更して、フェールオーバーが発生したときに引数を変更できるようになりました。 APS の場合、ロケーション、RESOURCE_MANAGER_LOCATION、および資格情報のみを変更できます。 詳細については、[外部データソースの変更](https://docs.microsoft.com/sql/t-sql/statements/alter-external-data-source-transact-sql?view=sql-server-2017)を参照してください。

### <a name="cdh-515-and-516-support-with-polybase"></a>ポリベースを使用した CDH 5.15 および 5.16 のサポート
CU7.5 アップデートを適用した APS 上の PolyBase は、Cloudera からの Hadoop ディストリビューションの CDH 5.15 および 5.16 バージョンをサポートするようになりました。 CDH 5.x バージョンにはオプション 6 を使用します。 

### <a name="try_convert-and-try_cast-support"></a>Try_ConvertとTry_Castサポート
CU7.5 APS は[、TRY_CAST](https://docs.microsoft.com/sql/t-sql/functions/try-cast-transact-sql?view=sql-server-2017)とTRY_CONVERTの tsql 関数[を](https://docs.microsoft.com/sql/t-sql/functions/try-convert-transact-sql?view=sql-server-2017)サポートするようになりました。 これらの関数はどちらも、変換が成功した場合に、指定したデータ型に変換された値を返します。それ以外の場合は、null を返します。

<a name="h2-aps-cu7.4"></a>
## <a name="aps-cu74"></a>APS CU7.4
リリース日 - 2019年5月

### <a name="loading-large-rows-with-dwloader"></a>dwloader を使用した大きな行のロード
APS CU7.4 以降では、新しい dwloader を使用して、32 KB (32,768 バイト) を超えるテーブルに行をロードできます。 新しい dwloader は、32768 から 33554432 (バイト単位) の整数値を受け取る -l スイッチをサポートし、32 KB を超える行をロードします。 このスイッチはクライアントとサーバーに多くのメモリを割り当て、負荷を遅くする可能性があるため、大きな行 (32 KB を超える) を読み込む場合にのみ、このオプションを使用してください。 新しい dwloader を[ダウンロード サイト](https://www.microsoft.com/download/details.aspx?id=57472)からダウンロードできます。  

### <a name="hdp-30-and-31-support-with-polybase"></a>ポリベースを使用した HDP 3.0 および 3.1 のサポート
APS 上のポリベースは、この更新プログラムで HDP 3.0 および 3.1 をサポートするようになりました。 HDP 3.x バージョンの場合はオプション 7 を使用します。 詳細については[、PolyBase 接続ページを](https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql)参照してください。

### <a name="utf16-file-support-with-polybase"></a>ポリベースでの UTF16 ファイルのサポート
PolyBase では、UTF16 (LE) エンコーディングで区切られたテキスト ファイルの読み取りがサポートされるようになりました。 設定の詳細については、「[外部ファイル形式の作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-file-format-transact-sql)」を参照してください。 

<a name="h2-aps-cu7.3"></a>
## <a name="aps-cu73"></a>APS CU7.3
リリース日 - 2018年12月

### <a name="common-subexpression-elimination"></a>共通部分式の削除
APS CU7.3 は、SQL クエリ オプティマイザで一般的な部分式を削除することで、クエリのパフォーマンスを向上させます。 この改善により、クエリは 2 つの方法で向上します。 最初の利点は、このような式を識別して除去することで、SQL コンパイル時間を短縮できることです。 2 つ目の重要な利点は、これらの冗長部分式のデータ移動操作が不要になるため、クエリの実行時間が速くなることです。 この機能の詳細については、[こちらをご覧ください](common-sub-expression-elimination.md)。

### <a name="aps-informatica-connector-for-informatica-1020-published"></a>APS インフォーマティカ コネクタ (10.2.0) が公開されました
Informatica バージョン 10.2.0 および 10.2.0 Hotfix 1 で動作する APS 用の新しいバージョンの Informatica コネクタをリリースしました。 新しいコネクタはダウンロード[サイト](https://www.microsoft.com/download/details.aspx?id=57472)からダウンロードできます。

#### <a name="supported-versions"></a>サポートされているバージョン

| APS バージョン | Informatica PowerCenter | ドライバー |
|:---|:---|:---|
| APS 2016 | 9.6.1 | SQL Server ネイティブ クライアント 11.x |
| APS 2016 以降 | 10.2.0, 10.2.0 修正プログラム 1 | SQL Server ネイティブ クライアント 11.x |

<a name="h2-aps-cu7.2"></a>
## <a name="aps-cu72"></a>APS CU7.2
リリース日 - 2018年10月

### <a name="support-for-tls-12"></a>TLS 1.2 のサポート
APS CU7.2 は TLS 1.2 をサポートしています。 クライアント マシンから APS および APS のノード内通信は、TLS1.2 経由でのみ通信するように設定できるようになりました。 TLS 1.2 経由でのみ通信するように設定されているクライアント マシンにインストールされている SSDT、SSIS、Dwloader などのツールは、TLS 1.2 を使用して APS に接続できるようになりました。 デフォルトでは、APS は下位互換性のためにすべての TLS (1.0、1.1、および 1.2) バージョンをサポートします。 TLS 1.2 を厳密に使用するように APS アプライアンスを設定する場合は、レジストリ設定を変更することで、これを行うことができます。 

詳細については[、APS での TLS1.2 の設定を](configure-tls12-aps.md)参照してください。

### <a name="hadoop-encryption-zone-support-for-polybase"></a>PolyBase の Hadoop 暗号化ゾーンのサポート
PolyBase は、Hadoop 暗号化ゾーンと通信できるようになりました。 [Hadoop セキュリティの設定](polybase-configure-hadoop-security.md#encryptionzone)で必要な APS 設定の変更を参照してください。

### <a name="insert-select-maxdop-options"></a>挿入 - maxdop オプションを選択
挿入選択操作で 1 より大きい maxdop 設定を選択できる[機能スイッチ](appliance-feature-switch.md)が追加されました。 maxdop の設定を 0、1、2、または 4 に設定できるようになりました。 既定値は 1 です。

> [!IMPORTANT]  
> maxdop を増やすと、操作が遅かったり、デッドロック エラーが発生したりする場合があります。 その場合は、設定を maxdop 1 に戻して、操作を再試行します。

### <a name="columnstore-index-health-dmv"></a>列ストア インデックスの正常性 DMV
dmv を使用して列ストア インデックスの正常性情報**dm_pdw_nodes_db_column_store_row_group_physical_stats**表示できます。 次のビューを使用して、断片化を判断し、列ストア インデックスを再構築または再編成するタイミングを決定します。

```sql
create view dbo.vCS_rg_physical_stats
as 
with cte
as
(
select   tb.[name]                    AS [logical_table_name]
,        rg.[row_group_id]            AS [row_group_id]
,        rg.[state]                   AS [state]
,        rg.[state_desc]              AS [state_desc]
,        rg.[total_rows]              AS [total_rows]
,        rg.[trim_reason_desc]        AS trim_reason_desc
,        mp.[physical_name]           AS physical_name
FROM    sys.[schemas] sm
JOIN    sys.[tables] tb               ON  sm.[schema_id]          = tb.[schema_id]                             
JOIN    sys.[pdw_table_mappings] mp   ON  tb.[object_id]          = mp.[object_id]
JOIN    sys.[pdw_nodes_tables] nt     ON  nt.[name]               = mp.[physical_name]
JOIN    sys.[dm_pdw_nodes_db_column_store_row_group_physical_stats] rg      ON  rg.[object_id]     = nt.[object_id]
                                                                            AND rg.[pdw_node_id]   = nt.[pdw_node_id]
                                        AND rg.[pdw_node_id]    = nt.[pdw_node_id]                                          
)
select *
from cte;
```

### <a name="polybase-date-range-increase-for-orc-and-parquet-files"></a>ORC ファイルと寄木ファイルの PolyBase の日付範囲の増加
PolyBase を使用して日付データ型の読み取り、インポート、エクスポートを行う場合、ORC ファイルタイプと Parquet ファイルタイプでは、1970-01-01 より前の日付と 2038-01-20 以降の日付がサポートされるようになりました。

### <a name="ssis-destination-adapter-for-sql-server-2017-as-target"></a>ターゲットとして SQL Server 2017 の SSIS 変換先アダプター
SQL Server 2017 を展開ターゲットとしてサポートする新しい APS SSIS デスティネーション アダプタは[、ダウンロード サイト](https://www.microsoft.com/download/details.aspx?id=57472)からダウンロードできます。

<a name="h2-aps-cu7.1"></a>
## <a name="aps-cu71"></a>APS CU7.1
リリース日 - 2018年7月

### <a name="dbcc-commands-do-not-consume-concurrency-slots-behavior-change"></a>DBCC コマンドは同時実行スロットを消費しません (動作の変更)
APS は[、DBCC DROPCLEANBUFFERS](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql)などの T-SQL [DBCC コマンド](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-transact-sql)のサブセットをサポートしています。 以前は、これらのコマンドは[コンカレンシー スロット](https://docs.microsoft.com/sql/analytics-platform-system/workload-management?view=aps-pdw-2016-au7#concurrency-slots)を消費したので、実行できるユーザー負荷/クエリの数が減少しました。 コマンド`DBCC`は、ユーザー同時実行スロットを使用しないローカル キューで実行され、クエリの全体的な実行パフォーマンスが向上します。

### <a name="replaces-some-metadata-calls-with-catalog-objects"></a>一部のメタデータ呼び出しをカタログ オブジェクトに置き換えます。
SMO を使用する代わりにメタデータ呼び出しにカタログ オブジェクトを使用すると、APS のパフォーマンスが向上しています。 CU7.1 以降では、これらのメタデータ呼び出しの一部がデフォルトでカタログ オブジェクトを使用するようになりました。 メタデータ クエリを使用している顧客が問題に遭遇した場合、この動作は[機能スイッチ](appliance-feature-switch.md)によって無効にすることができます。

### <a name="bug-fixes"></a>バグの修正
APS CU7.1 を使用して SQL Server 2016 SP2 CU2 にアップグレードしました。 アップグレードにより、以下に説明するいくつかの問題が修正されます。

| タイトル | 説明 |
|:---|:---|
| **タプルの引き渡しのデッドロックの可能性** |このアップグレードにより、分散トランザクションおよびタプルの引き渡しバックグラウンド スレッドでデッドロックが発生する可能性が長く修正されます。 CU7.1 をインストールした後、TF634 を使用して SQL Server のスタートアップ パラメータまたはグローバル トレース フラグとしてタプル ムーバーを停止したお客様は、安全に削除できます。 | 
| **特定のラグ/リード クエリが失敗する** |エラーになる可能性のある入れ子になったラグ/リード関数を持つ CCI テーブルに対するクエリが、このアップグレードで修正されるようになりました。 | 


<a name="h2-aps-au7"></a>
## <a name="aps-au7"></a>APS AU7
リリース日 - 2018年5月

APS 2016 は AU7 にアップグレードするための前提条件です。 APS AU7 の新機能を次に示します。

### <a name="auto-create-and-auto-update-statistics"></a>統計の自動作成と自動更新
APS AU7 は、デフォルトで統計を自動的に作成および更新します。 統計の設定を更新するには、管理者は[Configuration Manager](appliance-configuration.md#CMTasks)の新しい機能スイッチ メニュー項目を使用できます。 [機能スイッチ](appliance-feature-switch.md)は、統計の自動作成、自動更新、および非同期更新の動作を制御します。 また[、ALTER DATABASE (パラレル データ ウェアハウス)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)ステートメントを使用して、統計の設定を更新することもできます。

### <a name="t-sql"></a>T-SQL
選択@varがサポートされるようになりました。 詳細については、「[ローカル変数の選択](/sql/t-sql/language-elements/select-local-variable-transact-sql)」を参照してください。 

クエリ ヒントのハッシュと ORDER GROUP がサポートされるようになりました。 詳細については、ヒント[(Transact-SQL) - クエリを参照してください。](/sql/t-sql/queries/hints-transact-sql-query)

### <a name="feature-switch"></a>機能スイッチ
APS AU7 では[、構成マネージャ](launch-the-configuration-manager.md)で機能スイッチが導入されています。 管理者が変更できる構成可能なオプションが、現在は有効なオプションと DmsProcessStopMessageTimeout 秒です。

### <a name="known-issues"></a>既知の問題
APS AU7ソフトウェアでは、*投機的実行サイドチャネル攻撃*として記述された問題を修正するインテル BIOS アップデートが提供されます。 この攻撃は、スペクターとメルトダウンの*脆弱性と*呼ばれるものを悪用することを目的としています。 APS と一緒にパッケージ化されますが、BIOS アップデートは手動でインストールされ、APS AU7 ソフトウェアのインストールの一部としてインストールされるわけではありません。

マイクロソフトは、更新された BIOS をインストールするようすべてのお客様にアドバイスします。 マイクロソフトでは、さまざまな環境でのさまざまな SQL ワークロードに対するカーネル仮想アドレス シャドウ (KVAS)、カーネル ページ テーブル間接 (KPTI) および間接分岐予測軽減 (IBP) の影響を測定しました。 測定値によって、一部のワークロードで大幅な劣化が見つかりました。 結果に基づいて、BIOS 更新を有効にした場合のパフォーマンスへの影響をテストしてから、運用環境に展開することを推奨します。 SQL Server のガイダンスについては[、ここを参照してください](https://support.microsoft.com/help/4073225/guidance-protect-sql-server-against-spectre-meltdown)。

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"
<a name="h2-aps-au6"></a>
## <a name="aps-2016"></a>APS 2016
このセクションでは、APS 2016-AU6 の新機能について説明しました。

### <a name="sql-server-2016"></a>SQL Server 2016

APS AU6 は、最新の SQL Server 2016 リリースで実行され、既定のデータベース互換性レベル 130 を使用します。 SQL Server 2016 では、次のような新機能のサポートが可能になります。

- クラスター化列ストア インデックスのセカンダリ インデックス。
- ポリベースの Kerberos。

### <a name="t-sql"></a>T-SQL
APS AU6 では、これらの T-SQL 互換性の向上がサポートされています。  これらの追加言語要素を使用すると、SQL Server やその他のデータ ソースから簡単に移行できます。 

- [列レベルの SQL 照合順序][]が、Windows 照合順序に加えてサポートされるようになりました。
- [クラスター化列ストア インデックスの非クラスター化インデックスは、クラスター][]化列ストア インデックス内の特定の値を検索するクエリのパフォーマンスを向上させます。 
- [選択。。。に][] 
- [sp_spaceused() は][]、テーブルまたはデータベースで使用または予約されているディスク領域を表示します。
- [ワイド テーブル][]のサポートは、SQL Server 2016 と同じです。 行サイズに対する以前の上限である 32 K は存在しません。 

**データ型**

- [VARCHAR(最大)][] [、NVARCHAR(最大)][]および[VARBINARY (最大) 。][] これらの LOB データ型の最大サイズは 2 GB です。 これらのオブジェクトをロードするには[、 bcp ユーティリティ][]を使用します。 PolyBase および dwloader は、現在これらのデータ型をサポートしていません。 
- [SYSNAME][]
- [Uniqueidentifier][]
- [数値][]および 10 進データ・タイプ。

**ウィンドウ関数**

- SELECT ステートメントのオーバー句の[行または範囲][]。
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

**セキュリティ機能**

- [チェックサム()][]と[BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

**その他の機能**

- [ニューイド()][]
- [Rand()][]

### <a name="polybasehadoop-enhancements"></a>ポリベース/ハドオップの機能強化

- ホートンワークスHDP 2.4およびHDP 2.5との互換性
- データベース スコープの資格情報による Kerberos のサポート
- Azure ストレージ BLOB を使用した資格情報のサポート

### <a name="install-and-upgrade-enhancements"></a>インストールとアップグレードの機能強化

**エンタープライズ アーキテクチャの更新**既存のアプライアンスを APS AU6 にアップグレードすると、最新のファームウェアおよびドライバの更新がインストールされます。 

HPEまたはDELLの新しいアプライアンスには、最新のアップデートと以下のアップデートが含まれています。

- 最新世代プロセッササポート (ブロードウェル)
- DDR4 DIMM へのアップデート
- DIMM スループットの向上

**統合**

- 完全修飾ドメイン名 (FQDN) のサポートにより、アプライアンスに対するドメインの信頼を設定できます。 
- FQDN を使用するには、アップグレード中に完全アップグレードとオプトインを行う必要があります。 

**ダウンタイムの削減**APS AU6 のインストールまたはアップグレードは、以前のリリースよりも高速で、ダウンタイムが少なくて済みます。 ダウンタイムを減らすには、インストールまたはアップグレード: 

 - 2016 年 6 月までのすべての更新プログラムを含むイメージを使用して、WSUS の更新プログラムを適用する方法を合理化します。
 - ドライバとファームウェアの更新プログラムでセキュリティ更新プログラムを適用します。
 - 最新の修正プログラムとアプライアンス検証ユーティリティ(PAV)をアプライアンスに配置して、ダウンロードする必要なくインストールできるようにします。

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[列レベルの SQL 照合順序]: ~/relational-databases/collations/collation-and-unicode-support.md

[クラスター化列ストア インデックスの非クラスター化インデックス]:/sql/t-sql/statements/create-index-transact-sql
[ヴァルチャー(最大)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[バールチャー(最大)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY(最大)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[選択。。。に]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[ワイドテーブル]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[bcp ユーティリティ]:/sql/tools/bcp-utility
[Uniqueidentifier]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[数値]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[行または範囲]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[チェックサム()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[ニューイド()]:/sql/t-sql/functions/newid-transact-sql
[Rand()]:/sql/t-sql/functions/rand-transact-sql


  

  


