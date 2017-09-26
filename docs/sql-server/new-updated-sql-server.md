---
title: "更新済み - SQL Server のドキュメント | Microsoft Docs"
description: "最近変更された SQL Server に関するドキュメントで更新されたコンテンツのスニペットを示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 7f1c64e11e1bec44a558cec10c3d1f90f4951dfd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="new-and-recently-updated-sql-server-docs"></a>新規および最近の更新: SQL Server のドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 7 月 18 日**&nbsp;から &nbsp; **2017 年 9 月 11 日**
- *対象領域:* &nbsp; **SQL Server**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server 2008 R2 SP2 リリース ノート](sql-server-2008-r2-sp2-release-notes.md)
2. [SQL Server 2012 リリース ノート](sql-server-2012-release-notes.md)
3. [SQL Server 2012 SP1 リリース ノート](sql-server-2012-sp1-release-notes.md)
4. [SQL Server 2012 SP2 のリリース ノートします。](sql-server-2012-sp2-release-notes.md)
5. [SQL Server 2012 SP3 リリース ノート](sql-server-2012-sp3-release-notes.md)
6. [SQL Server 2014 リリース ノート](sql-server-2014-release-notes.md)
7. [SQL Server のヘルプ ビューアーとオフライン コンテンツ](sql-server-help-installation.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [SQL Server 2016 の新機能](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-whats-new-in-sql-server-2016what-s-new-in-sql-server-2016md"></a>1.&nbsp;[SQL Server 2016 の新機能](what-s-new-in-sql-server-2016.md)

*更新日: 2017 年 9 月 8 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 34.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e5bc0c05f120289f09a535400a4d521e4113ae55 0607d0a9af1c9a8dd9d3d7b0606895ff23bbffdc  (PR=0  ,  Filename=what-s-new-in-sql-server-2016.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=b97cc9723d563b19c85661f5ad7049a96fc904ff) -->



- **無料の** [**SQL Server 2016 Developer edition**](https://www.microsoft.com/en-us/cloud-platform/sql-server-editions-developers) をダウンロードしてください。
- 最新バージョンの [SQL Server Management Studio (SSMS)](/sql-docs/docs/ssms/download-sql-server-management-studio-ssms) をダウンロードします。
- Azure アカウントをすでにお持ちですか? [SQL Server 2016 がインストール済みの仮想マシン](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)をすぐにご利用いただけます。

**QL Server 2016 データベース エンジン**

- SQL Server のインストールおよびセットアップ時に、**複数の tempDB** データベース ファイルを構成できます。
- 新しい**クエリ ストア**は、データベース内に、クエリ テキスト、実行プラン、およびパフォーマンス指標を格納するため、パフォーマンス問題の監視およびトラブルシューティングが容易になります。 ダッシュボードには、どのクエリが最も多くの時間、メモリまたは CPU リソースを消費しているのかが表示されます。
- **テンポラル テーブル**は、すべてのデータ変更とその発生日時を記録する履歴テーブルです。
- SQL Server に新しく組み込まれた **JSON サポート**は、JSON のインポート、エクスポート、解析および格納をサポートします。
- 新しい **PolyBase** クエリ エンジンは、Hadoop または Azure Blob Storage 内の外部データと SQL Server を統合します。 クエリの実行だけでなく、データをインポートおよびエクスポートすることができます。
- 新しい **Stretch Database** 機能を使用すれば、ローカル SQL Server データベースからクラウドの Azure SQL Database へ、動的かつ安全に、データをアーカイブすることができます。 SQL Server は、リンクされたデータベースのローカルとリモートの両方のデータに自動的にクエリを実行します。
- **インメモリ OLTP:**
    - 現在は、FOREIGN KEY、UNIQUE、CHECK などの制約、ネイティブ コンパイルされたストアド プロシージャの OR、NOT、SELECT DISTINCT、OUTER JOIN、および SELECT のサブクエリをサポートしています。
    - 最大テーブル 2 TB をサポートしています (256 GB 以上)。
    - 並べ替えと Always On 可用性グループのサポートに対する列ストア インデックスの機能強化があります。
- 新しいセキュリティ機能
    - **Always Encrypted:** 有効にすると、暗号化キーを持つアプリケーションのみが、SQL Server 2016 データベースの暗号化された機微なデータにアクセスにできます。 キーが SQL Server に渡されることはありません。







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



