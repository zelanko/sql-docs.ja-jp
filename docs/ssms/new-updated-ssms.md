---
title: 更新済み - SQL Server 用 SSMS のドキュメント | Microsoft Docs
description: Microsoft SQL Server の SQL Server Management Studio (SSMS) の最近変更されたドキュメントで更新されたコンテンツのスニペットを示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql
ms.component: ssms
ms.date: 02/03/2018
ms.openlocfilehash: 8f2ad52b9741a3220a8c5db0a60924a41cc62d27
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>新規または最近の更新: SQL Server の SQL Server Management Studio (SSMS)



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *"更新日の範囲:"* &nbsp; **2017 年 12 月 3 日**&nbsp;から&nbsp;**2018 年 2 月 3 日**
- *対象領域:* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [英語以外の言語バージョンの SQL Server Management Studio (SSMS) をインストールする](install-other-languages.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [SQL Server Management Studio (SSMS) のダウンロード](#TitleNum_1)
2. [SQL Server Management Studio - Changelog (SSMS)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-sql-server-management-studio-ssmsdownload-sql-server-management-studio-ssmsmd"></a>1.&nbsp; [SQL Server Management Studio (SSMS) のダウンロード](download-sql-server-management-studio-ssms.md)

*更新日: 2018 年 1 月 18 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([次へ](#TitleNum_2))

<!-- Source markdown line 83.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0e123e7bdf04f02fcd26ac31fa30ed5f31b19c7d 924246b55d3cad6a5d068da8a41f4be23dcfeb2b  (PR=4652  ,  Filename=download-sql-server-management-studio-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



SSMS 17.4 は SQL Server Management Studio の最新バージョンです。 SSMS の 17.x 世代は、SQL Server 2008 から SQL Server 2017 までのほぼすべての機能領域をサポートしています。 バージョン 17.x は、SQL Analysis Service PaaS もサポートしています。

バージョン 17.4 の内容:

脆弱性評価:
- データベースをスキャンして潜在的な脆弱性およびベスト プラクティスからの逸脱 (構成の不備、過剰なアクセス許可、公開された機密データなど) がないかを確認できるように新しい SQL 脆弱性評価サービスが追加されました。
- 評価の結果には、各々の問題を解決する実践的な手順が含まれ、カスタマイズした修復スクリプトが適宜提供されます。 評価レポートは環境ごとにカスタマイズし、特定の要件に合わせて調整することができます。 詳細については、「[SQL 脆弱性評価](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment)」を参照してください。

SMO:
- Azure 上で *HasMemoryOptimizedObjects* が例外をスローするという問題を修正しました。
- 新しい CATALOG_COLLATION 機能のサポートが追加されました。

Always On ダッシュボード:
- 可用性グループでの待機時間の分析の機能強化。
- 次の 2 つの新しいレポートが追加されました: *AlwaysOn\_Latency\_Primary* および *AlwaysOn\_Latency\_Secondary*

Showplan:
- 適切なドキュメントを指すようにリンクが更新されました。
- 実際に作成されたプランから直接、単一プラン分析を実行できます。
- 新しいアイコンのセット。
- GbApply や InnerApply などの "Apply 論理演算子" を認識するためのサポートが追加されました。

XE プロファイラー:
- XEvent プロファイラーに名前が変更になりました。
- 既定で、[停止] / [開始] メニュー コマンドによってセッションが停止/開始されるようになりました。
- キーボード ショートカットが有効になりました (たとえば、検索する場合は CTRL + F キー)。
- XEvent プロファイラー セッションの適切なイベントに database\_name アクションと client\_hostname アクションが追加されました。 変更を有効にするために、サーバー上で既存の QuickSessionStandard セッション インスタンスまたは QuickSessionTSQL セッション インスタンスを削除することが必要な場合があります - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>2.&nbsp; [SQL Server Management Studio - 変更ログ (SSMS)](sql-server-management-studio-changelog-ssms.md)

*更新日: 2018 年 1 月 29 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([前へ](#TitleNum_1))

<!-- Source markdown line 27.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5096fa8f1ae3f2e4bc040f43cb8810d96f2c69c eb641ac39386a26a76dc303f5bd55eb3f9f4c78d  (PR=0  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=ba4b1c2e5200f2f78786b710da18fd38fedde6c9) -->



**[SSMS 17.4](download-sql-server-management-studio-ssms.md)**

一般公開 | ビルド番号: 14.0.17213.0

**新機能**


**SSMS 全般**

脆弱性評価:
- データベースをスキャンして潜在的な脆弱性およびベスト プラクティスからの逸脱 (構成の不備、過剰なアクセス許可、公開された機密データなど) がないかを確認できるように新しい SQL 脆弱性評価サービスが追加されました。
- 評価の結果には、各々の問題を解決する実践的な手順が含まれ、カスタマイズした修復スクリプトが適宜提供されます。 評価レポートは環境ごとにカスタマイズし、特定の要件に合わせて調整することができます。 詳細については、「[SQL 脆弱性評価](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment)」を参照してください。

SMO:
- Azure 上で *HasMemoryOptimizedObjects* が例外をスローするという問題を修正しました。
- 新しい CATALOG_COLLATION 機能のサポートが追加されました。

Always On ダッシュボード:
- 可用性グループでの待機時間の分析の機能強化。
- 次の 2 つの新しいレポートが追加されました: *AlwaysOn\_Latency\_Primary* および *AlwaysOn\_Latency\_Secondary*

Showplan:
- 適切なドキュメントを指すようにリンクが更新されました。
- 実際に作成されたプランから直接、単一プラン分析を実行できます。
- 新しいアイコンのセット。
- GbApply や InnerApply などの "Apply 論理演算子" を認識するためのサポートが追加されました。

XE プロファイラー:
- XEvent プロファイラーに名前が変更になりました。
- 既定で、[停止] / [開始] メニュー コマンドによってセッションが停止/開始されるようになりました。
- キーボード ショートカットが有効になりました (たとえば、検索する場合は CTRL + F キー)。
- XEvent プロファイラー セッションの適切なイベントに database\_name アクションと client\_hostname アクションが追加されました。 変更を有効にするために、サーバー上で既存の QuickSessionStandard セッション インスタンスまたは QuickSessionTSQL セッション インスタンスを削除することが必要な場合があります - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)

コマンド ライン:
- 新しいコマンド ライン オプション ("-G") が追加されました。このオプションを指定すると、Active Directory 認証 ('統合' または 'パスワード' のいずれか) を使用してサーバー/データベースへの SSMS の自動接続を行うことができます。 詳細については、「[Ssms ユーティリティ](ssms-utility.md)」を参照してください。







## <a name="similar-articles-about-new-or-updated-articles"></a>新規記事または更新記事に関する類似記事

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ある*" 対象領域


- [新規 + 更新 (1 + 3):&nbsp;**SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (12 + 1): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (6 + 2):&nbsp;**Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (15 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (2 + 9):&nbsp;**SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (1 + 0):&nbsp;**SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (1 + 1):&nbsp;**SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (1 + 1):&nbsp;**Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (1 + 2):&nbsp;**SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2):&nbsp;**Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ない*" 対象領域


- [新規 + 更新 (0 + 0): **SQL の Data Migration Assistant (DMA)** に関するドキュメント](../dma/new-updated-dma.md)
- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../samples/new-updated-samples.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


