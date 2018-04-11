---
title: 更新済み - SQL Server のドキュメント | Microsoft Docs
description: 最近変更された SQL Server に関するドキュメントで更新されたコンテンツのスニペットを示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: sql-server
ms.date: 02/03/2018
ms.openlocfilehash: bcbf9a579fce8d27eaa53471190dbe850774c146
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2018
---
# <a name="new-and-recently-updated-sql-server-docs"></a>新規および最近の更新: SQL Server のドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *"更新日の範囲:"* &nbsp; **2017 年 12 月 3 日**&nbsp;から&nbsp;**2018 年 2 月 3 日**
- *対象領域:* &nbsp; **SQL Server**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [Windows Server 2008/2008 R2/2012 クラスターで実行されている SQL Server インスタンスのアップグレード](failover-clusters/windows/upgrade-sql-server-failover-cluster-instance-2008-2012.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [SQL Server のオフライン ヘルプとヘルプ ビューアー](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-offline-help-and-help-viewersql-server-help-installationmd"></a>1.&nbsp; [SQL Server のオフライン ヘルプとヘルプ ビューアー](sql-server-help-installation.md)

*更新日: 2017 年 12 月 19 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 67.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ea491fdc173a54fb4cdb3dfa2e26bd206d1cc45d 22444427a48064b76088d19d1ffae0a885bfe2a7  (PR=4338  ,  Filename=sql-server-help-installation.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=f2fde1c324466530f92006561a9a29decb711e1b) -->



   ヘルプ ビューアーが開き、[コンテンツの管理] タブが表示されます。

2. 最新のヘルプ コンテンツ パッケージをインストールするには、[インストール元] の **[オンライン]** を選択します。

   ![HelpViewer2_ManageContent_OnlineSource](../sql-server/media/sql-server-help-installation/helpviewer2-managecontent-onlinesource.png)

   >[!NOTE]
   > ディスクからインストールするには (SQL Server 2014 ヘルプ)、[インストール元] で **[ディスク]** を選択し、ディスクの場所を指定します。

   [コンテンツの管理] タブの [ローカル ストア パス] に、ローカル コンピューター上でのコンテンツのインストール先が表示されます。 場所を変更する場合は、**[移動]** をクリックし、**[宛先]** フィールドに異なるフォルダー パスを入力し、**[OK]** をクリックします。
   [ローカル ストア パス] を変更した後、ヘルプのインストールに失敗した場合は、ヘルプ ビューアーを閉じてから再度開き、[ローカル ストア パス] に新しい場所が表示されていることを確認し、インストールを再試行します。

3. インストールする各コンテンツ パッケージ (ドキュメント) の横にある **[追加]** をクリックします。
   SQL Server ヘルプ コンテンツをすべてインストールするには、SQL Server で 13 のドキュメント全部を追加します。

4. 右下の **[更新]** をクリックします。
   左側に表示されているヘルプの目次に、追加のドキュメントが自動的に反映されます。

   ![HelpViewer2_ManageContent_AddContent](../sql-server/media/sql-server-help-installation/helpviewer2-managecontent-addcontent.png)

> [!NOTE]
> SQL Server の目次にあるすべての最上位ノード タイトルが、対応するダウンロード可能なヘルプ ドキュメントの名前と厳密に一致するとは限りません。 目次のタイトルは、次のようにドキュメント名にマップされています。

| コンテンツ ウィンドウ | SQL Server のドキュメント |
|-----|-----|
|Analysis Services 言語のリファレンス | Analysis Services (MDX) 言語のリファレンス|
|Data Analysis Expressions (DAX) リファレンス | Data Analysis Expressions (DAX) リファレンス|
|データ マイニング拡張機能 (DMX) リファレンス | データ マイニング拡張機能 (DMX) リファレンス|
|SQL Server の開発者ガイド | SQL Server 開発者用リファレンス|
|SQL Server Management Studio のダウンロード | [SQL Server Management Studio]|







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


