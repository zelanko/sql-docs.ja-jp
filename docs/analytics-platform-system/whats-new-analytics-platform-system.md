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
ms.openlocfilehash: b4059d9460eec5cd69e6e8b4a2f2ac95af5b3d0e
ms.sourcegitcommit: 2e038db99abef013673ea6b3535b5d9d1285c5ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2018
ms.locfileid: "39400645"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Analytics Platform System、スケール アウトの MPP データ ウェアハウスの新機能新機能
新機能については最新のアプライアンスの更新プログラム Microsoft® Analytics Platform System (APS) を参照してください。 アクセス ポイントは、MPP SQL Server 並列データ ウェアハウスをホストするスケール アウト オンプレミス アプライアンスです。 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"

## <a name="aps-au7"></a>APS AU7
APS 2016 を AU7 にアップグレードしてください。 次に、AP AU7 の新機能。

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

- [Varchar (max)][]、 [NVARCHAR(MAX)][]と[varbinary (max)][]します。 これらの LOB データ型では、2 GB の最大サイズがあります。 オブジェクトによって使用されるこれらの読み込みに[bcp ユーティリティ][]します。 Polybase と dwloader は、これらのデータ型を現在サポートされません。 
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


  

  


