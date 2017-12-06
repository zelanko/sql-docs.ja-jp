---
title: "SQL Server のドキュメントをサンプリングします更新済み - |。Microsoft ドキュメント"
description: "最近変更したドキュメントについては、Microsoft SQL Server のサンプルの更新されたコンテンツのスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.component: samples
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.author: genemi
ms.workload: sample
ms.openlocfilehash: 363cb5dde93c628317a977082fe8697af890d51c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="new-and-recently-updated-sample-for-sql-server"></a>新規または最近更新された: SQL Server のサンプル



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-09-28** &nbsp;対&nbsp; **2017 年-12-02**
- *サブジェクト領域:* &nbsp; **SQL Server のサンプル**です。




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

1. [WideWorldImporters データベース カタログ](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-wideworldimporters-database-catalogworld-wide-importersdatabase-catalog-oltpmd"></a>1.&nbsp;[WideWorldImporters データベース カタログ](world-wide-importers/database-catalog-oltp.md)

*最終更新日: 2017 年-11-20* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 136.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c055d0483699f06b8766ac2c999101934c14c55c 6975d5a3d1ade7b0ce34bd165bc0e9ef49299ba2  (PR=4032  ,  Filename=database-catalog-oltp.md  ,  Dirpath=docs\sample\world-wide-importers\  ,  MergeCommitSha40=7f8aebc72e7d0c8cff3990865c9f1316996a67d5) -->



可能な限り、データベースは、一般的にたずねますまとめて結合の複雑さを最小限に抑える同じスキーマにテーブルを collocates です。

データベース スキーマがされましたコードによって生成されたメタデータ内のテーブルの別のデータベース WWI_Preparation 系列に基づきます。 これにより、WideWorldImporters は非常に高度なデザインの整合性、名前付け一貫性、および完全を期すためにします。 スキーマの生成方法の詳細については、ソース コードを参照してください: [wide world-インポーター/第一次世界大戦-データベースのスクリプト](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

**テーブルのデザイン**


- すべてのテーブルには、結合わかりやすくするための主キーを 1 つの列があります。
- すべてのスキーマ、テーブル、列、インデックス、および check 制約がある拡張オブジェクトまたは列の目的を識別するために使用できるプロパティの説明。 メモリ最適化テーブルは、拡張プロパティを現在サポートしていないために、この例外となるはします。
- 同じ左側コンポーネントを含む別の非クラスター化インデックスがある場合を除き、すべての外部キーが自動的にインデックスします。
- テーブルに自動番号付けは、シーケンスに基づいています。 これらのシーケンスは、リンク サーバーと ID 列よりも同様の環境全体で作業しやすくします。 メモリ最適化テーブルは、SQL Server 2016 でサポートしないために、ID 列を使用します。
- これらのテーブルの 1 つのシーケンス (TransactionID) を使用: CustomerTransactions、SupplierTransactions、および StockItemTransactions です。 これは、一連のテーブルが 1 つのシーケンスを持つ方法を示します。
- 一部の列では、適切な既定値があります。

**セキュリティのスキーマ**


セキュリティ、WideWorldImporters を外部アプリケーション データのスキーマに直接アクセスをすることはできません。 でのアクセスを特定するのには、WideWorldImporters は、データを保持しませんが、ビュー、ストアド プロシージャが含まれているセキュリティ アクセス スキーマを使用します。 外部アプリケーションでは、セキュリティ スキーマを使用して、表示が許可されているデータを取得します。  これにより、ユーザーのみで実行できますビューおよびストアド プロシージャ、セキュリティで保護されたアクセス スキーマ







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新しい + 更新 (3 + 14): **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (1 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新しい + 更新 (87 + 0): **sql 分析プラットフォーム システム**docs](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新しい + 更新 (5 + 4): **SQL への接続**docs](../connect/new-updated-connect.md)
- [新しい + 更新 (0 + 1): **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (2 + 2): **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (10 + 9): **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (2 + 4):**リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (4 + 2): **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (0 + 1): **SQL 用のサンプル**docs](../sample/new-updated-sample.md)
- [新しい + 更新 (21 + 0): **SQL 操作 Studio** docs](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新しい + 更新 (5 + 1): **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新しい + 更新 (1 + 0): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新しい + 更新 (0 + 2): **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新しい + 更新 (0 0 以降):**データ移行アシスタント (DMA) sql** docs](../dma/new-updated-dma.md)
- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


