---
title: "更新 - データベース エンジン ドキュメント | Microsoft Docs"
description: "最近変更されたデータベース エンジンに関するドキュメントで更新されたコンテンツのスニペットを示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: barbkess
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: database-engine
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: ce80496cdf82c2bc2df2447ed043216e6c78ad7e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-database-engine-docs"></a>新規ドキュメントと最近更新されたドキュメント: データベース エンジン ドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 7 月 18 日**&nbsp;から&nbsp;**2017 年 9 月 11 日**
- *件名:* &nbsp; **データベース エンジン**




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server のインストール](install-windows/installation-for-sql-server.md)
2. [SQL Server 2017 のサポートされているバージョンとエディションのアップグレード](install-windows/supported-version-and-edition-upgrades-2017.md)
3. [SQL Server データベース エンジン](sql-server-database-engine-overview.md)
4. [データベース エンジンの新機能 - SQL Server 2016](whats-new-in-sql-server-2016.md)
5. [データベース エンジンの新機能 - SQL Server 2017](whats-new-in-sql-server-2017.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [セカンダリ レプリカの自動シード処理](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-automatic-seeding-for-secondary-replicasavailability-groupswindowsautomatic-seeding-secondary-replicasmd"></a>1.&nbsp; [セカンダリ レプリカの自動シード処理](availability-groups/windows/automatic-seeding-secondary-replicas.md)

*更新日: 2017 年 8 月 21 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 55.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0b7b6a23f38bfe5959ccd170527a9bbdb308dc4b dc51fdf69649ed6cae03584cff7bc900d5b72149  (PR=2896  ,  Filename=automatic-seeding-secondary-replicas.md  ,  Dirpath=docs\database-engine\availability-groups\windows\  ,  MergeCommitSha40=80642503480add90fc75573338760ab86139694c) -->



SQL Server 2016 以前では、自動シード処理でデータベースが作成されるフォルダーが既に存在しており、プライマリ レプリカのパスと同じである必要があります。

SQL Server 2017 では、可用性グループに参加するすべてのレプリカで同じデータとログ ファイルのパスを使用することをお勧めしますが、必要に応じて別のパスを使用することもできます。 たとえば、クロス プラットフォーム可用性グループの場合、SQL Server のあるインスタンスは Windows 上に、SQL Server の別インスタンスは Linux 上に展開することができます。 プラットフォームによって、既定のパスは異なります。 SQL Server 2017 は、既定のパスが異なる SQL Server のインスタンス上にある可用性グループ レプリカをサポートしています。

次の表は、自動シード処理に対応できるサポート対象のデータ ディスク レイアウトの例をまとめたものです。

|[プライマリ インスタンス]</br>既定のデータ パス|セカンダリ インスタンス</br>既定のデータ パス|[プライマリ インスタンス]</br>ソース ファイルの場所|セカンダリ インスタンス</br> ターゲット ファイルの場所
|:------|:------|:------|:------
|c:\\data\\ |/var/opt/mssql/data/ |c:\\data\\ |/var/opt/mssql/data/|
|c:\\data\\ |/var/opt/mssql/data/ |c:\\data\\group1\\ |/var/opt/mssql/data/group1/|
|c:\\data\\ |d:\\data\\ |c:\\data\\ |d:\\data\\
|c:\\data\\ |d:\\data\\ |c:\\data\\group1\\ |d:\\data\\group1\

プライマリおよびセカンダリのレプリカ データベースの場所がインスタンスの既定のパスではないシナリオは、この変更の影響を受けません。 セカンダリ レプリカ ファイルのパスをプライマリ レプリカ ファイルのパスと合わせるという要件は同じままです。

|[プライマリ インスタンス]</br>既定のデータ パス|セカンダリ インスタンス</br>既定のデータ パス|[プライマリ インスタンス]</br>ファイルの場所|セカンダリ インスタンス</br> ファイルの場所
|:------|:------|:------|:------
|c:\\data\\ |c:\\data\\ |d:\\group1\\ |d:\\group1\\
|c:\\data\\ |c:\\data\\ |d:\\data\\ |d:\\data\\
|c:\\data\\ |c:\\data\\ |d:\\data\\group1\\ |d:\\data\\group1\\

プライマリ レプリカとセカンダリ レプリカで既定のパスと既定以外のパスを混合していると、SQL Server 2017 は以前のリリースと異なる動作になります。 次の表は、SQL Server 2017 の動作の一覧です。







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (3 + 12): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (5 + 0): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (5 + 1): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (19 + 82): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (1 + 8): **SQL 用の Linux** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (12 + 1): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (0 + 1): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (7 + 1): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (1 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 2): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (1 + 4): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (4 + 1): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (0 + 1): **SQL 用のツール**に関するドキュメント](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)



