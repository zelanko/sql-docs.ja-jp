---
title: 'Analytics Platform System: スケール アウト データ ウェアハウスの新機能'
description: Microsoft® Analytics Platform System、MPP SQL Server 並列データ ウェアハウスをホストするスケール アウト、内部設置型アプライアンスの新機能を参照してください。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c2408e84e7ff81f54ad00a98f85cd8dce7b04131
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Analytics Platform System、スケール アウト MPP データ ウェアハウスの新機能
最新のアプライアンス更新プログラム Microsoft® Analytics Platform System (APS) の新機能を参照してください。 AP は、MPP SQL Server 並列データ ウェアハウスをホストするスケール アウト、内部設置型アプライアンスです。 


## <a name="aps-au7"></a>APS AU7
APS2016 は AU7 へのアップグレードの前提条件です。 APS AU7 の新機能を次に示します。

### <a name="auto-create-and-auto-update-statistics"></a>自動作成] および [統計の自動更新
APS AU7 は、作成し、既定では、自動的に統計を更新します。 統計情報の設定を更新するには、管理者がの新しい機能のスイッチのメニュー項目を使用できます、 [Configuration Manager](appliance-configuration.md#CMTasks)です。 [機能スイッチ](appliance-feature-switch.md)られた、自動更新、および統計の非同期更新の動作を制御します。 統計情報の設定を更新することも、 [ALTER DATABASE (並列データ ウェアハウス)](/sql/t-sql/statements/alter-database-parallel-data-warehouse)ステートメントです。

### <a name="t-sql"></a>T-SQL
選択@varがサポートされています。 詳細については、[ローカル変数の選択] を参照してください (/sql/t-sql/language-elements/select-local-variable-transact-sql) 

ハッシュと ORDER GROUP クエリ ヒントはサポートされています。 詳細については、[Hints(Transact-SQL) - クエリ] を参照してください (/sql/t-sql/クエリ/ヒント-transact-sql クエリ)

### <a name="feature-switch"></a>機能スイッチ
APS AU7 で機能スイッチが導入されています[Configuration Manager](launch-the-configuration-manager.md)です。 AutoStatsEnabled と DmsProcessStopMessageTimeoutInSeconds が管理者によって変更できる構成可能なオプションではようになりました。

### <a name="known-issues"></a>既知の問題
APS AU7 ソフトウェアはパッケージ化と (別名「サイド チャネル攻撃を予測の実行」を修正する Intel BIOS 更新プログラムを提供します。 Spectre およびメルトダウンの脆弱性) です。 パッケージにまとめ、BIOS 更新プログラムを手動でインストールし、AP AU7 ソフトウェアの一部ではないをインストールします。 Microsoft では、BIOS の更新をインストールするすべてのお客様が示されます。 Microsoft がさまざまな環境でさまざまな SQL ワークロードでのカーネル仮想アドレス シャドウ (KVAS)、カーネル ページ テーブルの間接参照 (KPTI) および間接のブランチ予測の軽減 (IBP) の影響を測定し、いくつかが大幅に低下を検出ワークロード。 実稼働環境で展開する前に、BIOS の更新プログラムを有効化のパフォーマンスに与える影響をテストすることをお勧めします。 これらの機能を有効化のパフォーマンスに与える影響が既存のアプリケーションに対して高すぎる場合は、信頼されていないコードを実行してから、AP アプライアンスを分離するが、アプリケーションがより緩和であるかどうかを検討することができます。 SQL Server のガイダンスを参照してください[ここ](https://support.microsoft.com/en-us/help/4073225/guidance-protect-sql-server-against-spectre-meltdown)です。

## <a name="aps-2016"></a>APS 2016
APS 2016 の新機能を次に示します。

### <a name="sql-server-2016"></a>SQL Server 2016

APS 2016 では、最新の SQL Server 2016 リリースで実行し、既定のデータベース互換性レベル 130 を使用します。  SQL Server 2016 では、PolyBase のクラスター化列ストア インデックスと Kerberos のセカンダリ インデックスなどの新機能の一部をサポートすることです。 


### <a name="t-sql"></a>T-SQL
APS 2016 では、それらの改良の T-SQL の互換性をサポートします。  これらの追加の言語要素容易にできるように SQL Server およびその他のデータ ソースからの移行します。 

- [列レベルの SQL 照合順序][]に加えて Windows 照合順序がサポートされています。
- [クラスター化列ストア インデックスの非クラスター化インデックス][]クラスター化列ストア インデックスに特定の値を検索するクエリのパフォーマンスが向上します。 
- [SELECT...INTO][] 
- [sp_spaceused()][]ディスク領域が使用されるか、テーブルまたはデータベースで予約されていますが表示されます。
- [幅の広いテーブル][]サポートは SQL Server 2016 と同じです。 行サイズの 32 K の以前の制限は存在しません。 

**データ型**

- [Varchar (max)][]、 [NVARCHAR(MAX)][]と[varbinary (max)][]です。 これらの LOB データ型では、2 GB の最大サイズがあります。 オブジェクトによって使用されるこれらの読み込みに[bcp ユーティリティ][]です。 Polybase と dwloader は、これらのデータ型を現在サポートされません。 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [NUMERIC][]および DECIMAL データ型。

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

- Hortonworks HDP 2.4 と HDP 2.5 との互換性
- データベース スコープ資格情報を使用して Kerberos をサポートします。
- Azure ストレージ Blob の資格情報のサポート

### <a name="install-and-upgrade-enhancements"></a>インストールとアップグレードの機能強化

**エンタープライズ アーキテクチャの更新プログラム**最新のファームウェアとドライバーの更新プログラム、セキュリティ修正プログラムを含む、既存のアプライアンスを APS 2016 にアップグレードがインストールされます。 

HPE または DELL から新しいアプライアンスに、最新の更新プログラムが含まれていますとします。

- 最新世代プロセッサのサポート (Broadwell)
- DDR4 Dimm への更新
- DIMM スループットの向上

**統合**

- 完全修飾ドメイン名 (FQDN) をサポートできるようになりますアプライアンスにドメインの信頼関係をセットアップします。 
- FQDN を使用するのには、完全なアップグレードを行うと、アップグレード中にオプトインする必要があります。 

**ダウンタイムの短縮**APS 2016 へのアップグレードのインストールまたは高速で、以前のリリースよりも少ないダウンタイムが必要です。 ダウンタイムをインストールまたはアップグレードを減らします。 

 - 2016 年 6 月経由のすべての更新プログラムを含むイメージを使用して WSUS 更新プログラムを適用する効率化
 - ドライバーおよびファームウェアの更新とセキュリティ更新プログラムを適用します。
 - ダウンロードする必要はありませんでをインストールする準備ができるように、アプライアンス上で最新の修正プログラムとアプライアンス検証ユーティリティ (PAV) を配置します。


<!--MSDN references-->
[database compatibility level 130]:/sql/t-sql/statements/alter-database-transact-sql-compatibility-level
[列レベルの SQL 照合順序]:/sql/relational-databases/collations/collation-and-unicode-support
[クラスター化列ストア インデックスの非クラスター化インデックス]:/sql/t-sql/statements/create-index-transact-sql
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


  

  


