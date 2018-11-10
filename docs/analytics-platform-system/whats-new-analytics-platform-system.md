---
title: 'Analytics Platform System: スケール アウト データ ウェアハウスの新機能新機能'
description: 新機能 Microsoft® Analytics Platform System、MPP SQL Server 並列データ ウェアハウスをホストするスケール アウト オンプレミス アプライアンスの新機能を参照してください。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f5c991130c59d1999cc68d27ffccc15138ffc34d
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269755"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Analytics Platform System、スケール アウトの MPP データ ウェアハウスの新機能新機能
新機能については最新のアプライアンスの更新プログラム Microsoft® Analytics Platform System (APS) を参照してください。 アクセス ポイントは、MPP SQL Server 並列データ ウェアハウスをホストするスケール アウト オンプレミス アプライアンスです。 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"
<a name="h2-aps-cu7.2"></a>
## <a name="aps-cu72"></a>APS CU7.2
リリース日 - 2018 の年 10 月

### <a name="support-for-tls-12"></a>TLS 1.2 のサポート
APS CU7.2 では、TLS 1.2 をサポートします。 クライアント マシン AP と AP にイントラ ノード通信できるようになりましたに設定する TLS1.2 経由でのみ通信します。 SSDT、SSIS、および TLS 1.2 経由でのみ通信するために設定されているクライアント コンピューターにインストールされている Dwloader などのツールは、TLS 1.2 を使用して AP に接続できます。 既定では、AP は旧バージョンとの互換性のため TLS (1.0、1.1、1.2) のすべてのバージョンをサポートします。 APS アプライアンスを設定する場合は、stictly に TLS 1.2 を使用して、レジストリ設定を変更することによって行うことができます。 

参照してください[AP で TLS1.2 を構成する](configure-tls12-aps.md)詳細についてはします。

### <a name="hadoop-encryption-zone-support-for-polybase"></a>PolyBase の Hadoop 暗号化ゾーンをサポートします。
PolyBase は Hadoop 暗号化ゾーンを通信できるようになりました。 必要なアクセス ポイントの構成の変更を参照してください。 [Hadoop セキュリティの構成](polybase-configure-hadoop-security.md#encryptionzone)します。

### <a name="insert-select-maxdop-options"></a>Insert Select maxdop オプション
追加されました、[機能スイッチ](appliance-feature-switch.md)insert select 操作の 1 より大きい maxdop 設定を選択することができます。 0、1、2、または 4 に、maxdop 設定を設定できます。 既定値は 1 です。

> [!IMPORTANT]  
> 低速操作やデッドロック エラーでは、maxdop の増加は発生可能性がある場合があります。 発生する場合は、maxdop 1 に設定を変更、操作を再試行してください。

### <a name="columnstore-index-health-dmv"></a>列ストア インデックスの状態を DMV
列ストア インデックスの正常性を使用して情報を表示する**dm_pdw_nodes_db_column_store_row_group_physical_stats** dmv。 次のビューを使用して、断片化を確認し、再構築または列ストア インデックスを再構成するタイミングを決定します。

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

### <a name="polybase-date-range-increase-for-orc-and-parquet-files"></a>PolyBase ORC、Parquet ファイルの日付範囲を増やす
読み取り、インポート、現在、PolyBase を使用して日付データ型をエクスポート、ORC、Parquet ファイルの種類の日付 2038-01-20 の前後に 1970-01-01 をサポートしています。

### <a name="ssis-destination-adapter-for-sql-server-2017-as-target"></a>ターゲットとして SQL Server 2017 の SSIS 変換先アダプター
配置ターゲットをからダウンロードできるように SQL Server 2017 をサポートする新しい AP SSIS 変換先アダプター[ダウンロード サイト](https://www.microsoft.com/en-us/download/details.aspx?id=57472)します。

<a name="h2-aps-cu7.1"></a>
## <a name="aps-cu71"></a>APS CU7.1
リリース日 - 2018 年 7 月

### <a name="dbcc-commands-do-not-consume-concurrency-slots-behavior-change"></a>DBCC コマンドは、同時実行スロット (動作の変更) を使用しません。
AP、T-SQL のサブセットをサポートする[DBCC コマンド](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-transact-sql)など[DBCC DROPCLEANBUFFERS](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql)します。 以前は、これらのコマンドを消費する、[の同時実行スロット](https://docs.microsoft.com/sql/analytics-platform-system/workload-management?view=aps-pdw-2016-au7#concurrency-slots)実行することがユーザーの読み込み/クエリの数を減らします。 `DBCC`を全体的なクエリ実行のパフォーマンスを向上させるユーザー同時実行スロットを使用しないローカル キューにあるコマンドが実行されますようになりました。

### <a name="replaces-some-metadata-calls-with-catalog-objects"></a>カタログ オブジェクト メタデータの一部の呼び出しで置き換えます
SMO を使用する代わりにメタデータの呼び出しのカタログ オブジェクトを使用して、パフォーマンスの向上が AP で説明しました。 CU7.1 から開始するこれらのメタデータの呼び出しのようになりましたオブジェクトを使用してカタログ既定で。 この動作がによってオフに[機能スイッチ](appliance-feature-switch.md)メタデータ クエリを使用しているお客様に問題が発生する場合。

### <a name="bug-fixes"></a>バグの修正
APS CU7.1 で SQL Server 2016 SP2 CU2 にアップグレードします。 アップグレードでは、以下に示すいくつかの問題を修正します。

| [タイトル] | 説明 |
|:---|:---|
| **組ムーバー デッドロックの可能性** |アップグレードでは、分散トランザクション、およびタプル ムーバー バック グラウンド スレッドでデッドロックの長年にわたる可能性を修正します。 CU7.1 をインストールすると、TF634 SQL Server スタートアップ パラメーターまたはグローバル トレース フラグとして組ムーバーを停止するために使用するお客様に安全に削除できます。 | 
| **特定の遅延/リード クエリが失敗しました。** |このアップグレードでは、入れ子になった lag/リード関数はエラーを使用した CCI テーブルで特定のクエリは固定されます。 | 


<a name="h2-aps-au7"></a>
## <a name="aps-au7"></a>APS AU7
リリース日 - 2018 年 5 月

APS 2016 を AU7 にアップグレードしてください。 以下は、AP AU7 の新機能です。

### <a name="auto-create-and-auto-update-statistics"></a>自動作成] および [統計の自動更新
APS AU7 は作成し、既定では、自動的に統計を更新します。 統計情報の設定を更新するには、管理者がの新しい機能のスイッチのメニュー項目を使用できます、 [Configuration Manager](appliance-configuration.md#CMTasks)します。 [機能スイッチ](appliance-feature-switch.md)られた、自動更新、および統計の非同期更新の動作を制御します。 統計情報の設定を更新することも、 [ALTER DATABASE (並列データ ウェアハウス)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)ステートメント。

### <a name="t-sql"></a>T-SQL
選択@varがサポートされています。 詳細については、[ローカル変数を選択します] を参照してください (/sql/t-sql/language-elements/select-local-variable-transact-sql) 

ハッシュと ORDER GROUP クエリ ヒントはサポートされています。 詳細については、[Hints(Transact-SQL) - クエリ] を参照してください (/sql/t-sql/クエリ/ヒント-transact-sql クエリ)

### <a name="feature-switch"></a>機能スイッチ
APS AU7 で機能スイッチが導入されています[Configuration Manager](launch-the-configuration-manager.md)します。 AutoStatsEnabled と DmsProcessStopMessageTimeoutInSeconds が管理者によって変更できる構成可能なオプションではようになりました。

### <a name="known-issues"></a>既知の問題
として記載されている問題を修正する Intel BIOS の更新プログラムを提供、AP AU7 ソフトウェアと*予測実行のサイド チャネル攻撃*します。 攻撃と呼ばれるものを悪用することを目指します*Spectre や Meltdown の脆弱性*します。 BIOS の更新プログラムが手動でインストールが、AP と共にパッケージ化、および APS AU7 ソフトウェアのインストールの一部ではなく。

Microsoft では、BIOS の更新をインストールするすべての顧客が表示されます。 Microsoft には、さまざまな環境でさまざまな SQL ワークロードに対するカーネル仮想アドレス シャドウ (KVAS)、カーネル ページ テーブルの間接参照 (KPTI) および間接のブランチ予測の軽減策 (IBP) の効果が測定されます。 測定値には、一部のワークロードで大幅に低下が検出されました。 推奨事項の結果に基づいての運用環境で展開する前に、BIOS の更新プログラムを有効にすると、パフォーマンスに与える影響をテストすることは。 SQL Server のガイダンスを参照してください。[ここ](https://support.microsoft.com/en-us/help/4073225/guidance-protect-sql-server-against-spectre-meltdown)します。

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"
<a name="h2-aps-au6"></a>
## <a name="aps-2016"></a>APS 2016
このセクションでは、APS 2016 AU6 の新機能について説明します。

### <a name="sql-server-2016"></a>SQL Server 2016

APS AU6 では、最新の SQL Server 2016 リリースでは実行され、既定のデータベース互換性レベル 130 を使用します。 SQL Server 2016 などの新機能のサポートが有効にします。

- クラスター化列ストア インデックスのセカンダリ インデックス。
- Polybase Kerberos。

### <a name="t-sql"></a>T-SQL
APS AU6 では、これらの T-SQL での互換性の改善をサポートします。  これらの追加の言語要素を簡単に SQL Server と他のデータ ソースから移行します。 

- [列レベルの SQL 照合順序][]Windows 照合順序だけでなく、サポートされています。
- [クラスター化列ストア インデックスに非クラスター化インデックス][]クラスター化列ストア インデックスで特定の値を検索するクエリのパフォーマンスが向上します。 
- [SELECT...INTO][] 
- [sp_spaceused()][]ディスク領域が、テーブルまたはデータベース内で予約されたまたは使用が表示されます。
- [幅の広いテーブル][]サポートは、SQL Server 2016 の場合と同じです。 行のサイズの 32 K の以前の上限が存在しません。 

**データ型**

- [Varchar (max)][]、 [NVARCHAR(MAX)][]と[varbinary (max)][]します。 これらの LOB データ型では、2 GB の最大サイズがあります。 オブジェクトによって使用されるこれらの読み込みに[bcp ユーティリティ][]します。 PolyBase と dwloader は、これらのデータ型を現在サポートされません。 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [NUMERIC][]と 10 進データ型。

**ウィンドウ関数**

- [ROWS または RANGE][] SELECT ステートメントの OVER 句でします。
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

**セキュリティ関数**

- [CHECKSUM()][]と[BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

**追加の関数**

- [NEWID()][]
- [RAND()][]

### <a name="polybasehadoop-enhancements"></a>PolyBase/Hadoop の機能強化

- Hortonworks HDP 2.4 および HDP 2.5 との互換性
- データベース スコープ資格情報を使用して Kerberos をサポートします。
- Azure Storage Blob を使用した資格情報のサポート

### <a name="install-and-upgrade-enhancements"></a>インストールとアップグレードの機能強化

**エンタープライズ アーキテクチャの更新プログラム**最新のファームウェアとドライバーの更新プログラム、セキュリティ修正プログラムを含むインストール AP AU6 に、既存のアプライアンスをアップグレードします。 

HPE または DELL から新しいアプライアンスには、最新の更新プログラムが含まれていますと。

- 最新世代のプロセッサ サポート (Broadwell)
- DDR4 Dimm に更新
- DIMM スループットの向上

**統合**

- 完全修飾ドメイン名 (FQDN) のサポートにより、アプライアンスにドメインの信頼関係をセットアップすることにします。 
- FQDN を使用するには、完全なアップグレードを行うと、アップグレード中にオプトインする必要があります。 

**ダウンタイムを短縮**AP AU6 へのアップグレードのインストールまたは高速で、以前のリリースよりも少ないダウンタイムが必要です。 ダウンタイム、インストールまたはアップグレードを減らします。 

 - 2016 年 6 月からすべての更新プログラムを含むイメージを使用して WSUS 更新プログラムの適用を効率化
 - ドライバーとファームウェアの更新プログラムがセキュリティ更新プログラムを適用します。
 - ダウンロードする必要なくインストールする準備ができたために、アプライアンス上で最新の修正プログラムとアプライアンス検証ユーティリティ (PAV) を配置します。

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[列レベルの SQL 照合順序]: ~/relational-databases/collations/collation-and-unicode-support.md

[クラスター化列ストア インデックスに非クラスター化インデックス]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR (MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR(MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY (MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[SELECT...INTO]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[幅の広いテーブル]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[bcp ユーティリティ]:/sql/tools/bcp-utility
[UNIQUEIDENTIFIER]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[NUMERIC]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[ROWS または RANGE]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[CHECKSUM()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[NEWID()]:/sql/t-sql/functions/newid-transact-sql
[RAND()]:/sql/t-sql/functions/rand-transact-sql


  

  


