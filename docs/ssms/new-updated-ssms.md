---
title: 更新済み - SQL Server 用 SSMS のドキュメント | Microsoft Docs
description: Microsoft SQL Server の SQL Server Management Studio (SSMS) の最近変更されたドキュメントで更新されたコンテンツのスニペットを示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: ssms
ms.date: 04/28/2018
ms.openlocfilehash: 1ce446219f71baca0f4cdedc835fca929b572a0f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>新規または最近の更新: SQL Server の SQL Server Management Studio (SSMS)



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- "*更新日の範囲:* " &nbsp; **2018 年 2 月 3 日** &nbsp;から&nbsp; **2018 年 4 月 28 日**
- *対象領域:* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [チュートリアル: SQL Server Management Studio を使用して SQL Server インスタンスに接続し、クエリを行う](tutorials/connect-query-sql-server.md)
2. [チュートリアル: SQL Server Management Studio でオブジェクトのスクリプトを作成する](tutorials/scripting-ssms.md)
3. [チュートリアル: SQL Server Management Studio のコンポーネントと構成](tutorials/ssms-configuration.md)
4. [チュートリアル: SSMS を使用するためのヒントとテクニック](tutorials/ssms-tricks.md)
5. [チュートリアル: SQL Server Management Studio 内でテンプレートを使用する](tutorials/templates-ssms.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [SQL Server Management Studio - Changelog (SSMS)](#TitleNum_1)
2. [SQL Server Management Studio (SSMS) のチュートリアル](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>1.&nbsp; [SQL Server Management Studio - 変更ログ (SSMS)](sql-server-management-studio-changelog-ssms.md)

*更新日: 2018 年 4 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次へ](#TitleNum_2))

<!-- Source markdown line 27.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 eb641ac39386a26a76dc303f5bd55eb3f9f4c78d f560f09b51ea30b255c10f7eb86857c3090881d9  (PR=5676  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**[SSMS 17.6]**


リリース番号: 17.6<br>
ビルド番号: 14.0.17230.0<br>
リリース日: 2018 年 3 月 20 日

**新機能**


**SSMS 全般**

SQL Database マネージ インスタンス:

- [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)のサポートが追加されました。 Azure SQL Database マネージ インスタンス (プレビュー) は Azure SQL Database の新しい種類であり、SQL Server オンプレミスとのほぼ 100% の互換性、セキュリティに関する一般的な問題に対応するネイティブな[仮想ネットワーク (VNet)](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) の実装、およびオンプレミスの SQL Server ユーザーに適した[ビジネス モデル](https://azure.microsoft.com/pricing/details/sql-database/)を提供します。
- 次のような一般的な管理シナリオをサポートします。
   - データベースの作成と変更。
   - データベースのバックアップと復元。
   - データ層アプリケーションのインポート、エクスポート、抽出、公開。
   - サーバー プロパティの表示と変更。
   - オブジェクト エクスプローラーの完全なサポート。
   - データベース オブジェクトのスクリプト作成。
   - SQL エージェント ジョブのサポート。
   - リンク サーバーのサポート。
- マネージ インスタンスの詳細については、[こちら](https://azure.microsoft.com/blog/migrate-your-databases-to-a-fully-managed-service-with-azure-sql-database-managed-instance/)を参照してください。

オブジェクト エクスプローラー:
- オブジェクト エクスプローラーからクエリ ウィンドウにドラッグ アンド ドロップするときに、名前を角かっこで囲むことを強制しない設定が追加されました。 (ユーザー提案 [32911933](https://feedback.azure.com/forums/908035-sql-server/suggestions/32911933) および [32671051](https://feedback.azure.com/forums/908035-sql-server/suggestions/32671051))

データ分類:
- 一般的な機能強化とバグの修正。

**Integration Services (IS)**

- [SQL Database マネージ インスタンス](docs/ssms/https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)にパッケージを展開するサポートが追加されました。



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-tutorials-for-sql-server-management-studio-ssmstutorialstutorial-sql-server-management-studiomd"></a>2.&nbsp; [SQL Server Management Studio (SSMS) のチュートリアル](tutorials/tutorial-sql-server-management-studio.md)

*更新日: 2018 年 4 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_1))

<!-- Source markdown line 49.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b272c75bab04912ebb706098cf6b6a6c80d9e2b8 d453ebc8251fb83ffcb1af58c9a08bb65b3e9fa2  (PR=5676  ,  Filename=tutorial-sql-server-management-studio.md  ,  Dirpath=docs\ssms\tutorials\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- チュートリアル: SSMS を使用した SQL Server に対する接続およびクエリ

    このチュートリアルでは、SQL Server インスタンスに接続する方法を学習します。 新しいデータベースを作成してクエリを実行するための基本的な Transact-SQL (T-SQL) コマンドについても学習します。

- チュートリアル: SSMS でオブジェクトのスクリプトを作成する

    このチュートリアルでは、データベースやクエリなどのさまざまなオブジェクトのスクリプトを SSMS で作成する方法を学習します。

- チュートリアル: SSMS でテンプレートを使用する

    このチュートリアルでは、SSMS で構築済みのテンプレートを使う方法を学習します。 テンプレートは、さまざまなデータベース管理タスクの Transact-SQL コード スニペットを格納する機能ですが、あまり知られていません。

- チュートリアル: SSMS を構成する

    このチュートリアルでは、環境レイアウトの変更など、SSMS 環境の構成の基本を学習します。 このチュートリアルでは、さまざまな SSMS コンポーネントについても説明します。


- チュートリアル: SSMS を使用するためのヒントとテクニック

    このチュートリアルでは、SSMS の使用に関するその他のヒントとテクニックを学習します。 チュートリアルは次のような内容です。
    - テキストのコメント化とコメント解除
    - テキストのインデント
    - オブジェクト エクスプローラーでのオブジェクトのフィルター
    - SQL Server エラー ログへのアクセス
    - インスタンスの名前の検索








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

