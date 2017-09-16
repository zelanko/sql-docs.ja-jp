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
ms.date: 07/17/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 8cd44c8b384019418a2a913e5f8d13d82120eac2
ms.openlocfilehash: d61aed44a16e78107c36ed4f7b1be387043b6746
ms.contentlocale: ja-jp
ms.lasthandoff: 08/29/2017

---
# <a name="new-and-recently-updated-sql-server-docs"></a>新規および最近の更新: SQL Server のドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 5 月 23 日**&nbsp;から &nbsp; **2017 年 7 月 17 日**
- *対象領域:* &nbsp; **SQL Server**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [エディションと SQL Server 2017 のサポートされる機能](editions-and-components-of-sql-server-2017.md)
2. [フィードバックを Microsoft に送信する SQL Server の構成](sql-server-customer-feedback.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-customer-experience-improvement-program-for-sql-server-data-toolscustomer-experience-improvement-program-for-sql-server-data-toolsmd"></a>1.&nbsp; [SQL Server Data Tools のカスタマー エクスペリエンス向上プログラム](customer-experience-improvement-program-for-sql-server-data-tools.md)

*更新日: 2017 年 6 月 14 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([次へ](#TitleNum_2))

<!-- Source markdown line 25.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e35a35aaa3c8ee8a4419b6318ebff9db027aa73d 16a623cf0ab4c9e6d7a17f4617804432c863ac86  (PR=2038  ,  Filename=customer-experience-improvement-program-for-sql-server-data-tools.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=be884b2d1b316506592f939167c5be91ddc2a9f6) -->



 カスタマー エクスペリエンス向上プログラムは、Microsoft が時間の経過と共に製品を向上させるために記述されたプログラムです。 このプログラムは、コンピューターで実行しているユーザーのタスクを中断することなく、コンピューターのハードウェアおよびユーザーによる製品の利用状況を収集します。 収集される情報は、Microsoft がどの機能を改善するかを特定するために役立ちます。 このドキュメントでは、Visual Studio 2017、Visual Studio 2015 および Visual Studio 2013 で SQL Server Data Tools (SSDT) の CEIP を有効または無効にする方法について説明します。  

**Visual Studio 2017 の CEIP と SQL Server Data Tools の選択および制御  **

 Visual Studio 2017 の SSDT は、SQL Server 2017 に付属するデータ モデリング ツールです。 Visual Studio 2017 に組み込まれている CEIP オプションが使用されます。 Visual Studio 2017 の CEIP を通じてフィードバックを送信する方法の詳細は、[Visual Studio のヘルプ ドキュメント](https://www.visualstudio.com/en-us/docs/work/connect/give-feedback)で確認できます。  
  
 プレビュー版の SQL Server 2017 では、CEIP が既定で有効になっています。 次の手順で、無効にし、再度有効に戻すことができます。  
  
 **Visual Studio の場合 (全言語がインストールされた Visual Studio 2017 に適用されます)**  
  
 既に Visual Studio が含まれているコンピューターに SSDT セットアップを実行する場合は、SQL Server および Business Intelligence プロジェクト テンプレートのみが追加されます。 このシナリオでは、Visual Studio で提供されるカスタマー フィードバックのオプションを使用して CEIP を有効または無効にできます。  
  
1.  Visual Studio を起動します。  
  
2.  [ヘルプ] メニューから、 **[フィードバックの送信]** > **[設定]**を選択します。  
  
3.  CEIP をオフにするには、 **[いいえ、協力しません]**をクリックし、 **[OK]**をクリックします。  
  
     CEIP をオンにするには、 **[はい、協力します]**をクリックし、 **[OK]**をクリックします。  
  

  
 **レジストリ ベースのポリシーまたはグループ ポリシーを使用する**  




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-editions-and-supported-features-of-sql-server-2016editions-and-components-of-sql-server-2016md"></a>2.&nbsp;[SQL Server 2016 の各エディションとサポートされている機能](editions-and-components-of-sql-server-2016.md)

*更新日: 2017 年 6 月 16 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_1))

<!-- Source markdown line 113.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 471ad35ebf1898470033d43c7bd43cbac5ddfece 7814e4d7428907161a9a2567280fb9fe20d5f273  (PR=2064  ,  Filename=editions-and-components-of-sql-server-2016.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=727d9ccd8cd1e40d89cfe74291edae92988b407c) -->



**Developer Edition と Evaluation Edition**   
Developer Edition と Evaluation Edition でサポートされている機能については、下の表に記載されている SQL Server Enterprise Edition の機能をご覧ください。
[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 の Developer Edition に追加された機能の一覧については、[SQL Server 2016 SP1 の各エディション](https://aka.ms/uw6cw4)に関するページをご覧ください。  

Developer Edition は引き続き [SQL Server Distributed Replay--../tools/distributed-replay/sql-server-distributed-replay.md) のクライアントを 1 つだけサポートします。 
  
**<a name="Cross-BoxScaleLimits"></a> 規模の制限 **

  
|機能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssDEnoversion--../includes/ssdenoversion-md.md)]<sup>1</sup>|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限| 
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssASnoversion--../includes/ssasnoversion-md.md)] または [!INCLUDE[ssRSnoversion--../includes/ssrsnoversion-md.md)]|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|  
|[!INCLUDE[ssDEnoversion--../includes/ssdenoversion-md.md)] のインスタンスごとのバッファー プールの最大メモリ|オペレーティング システムの最大容量|128 GB|64 GB|1410 MB|1410 MB|
|[!INCLUDE[ssDEnoversion--../includes/ssdenoversion-md.md)] のインスタンスごとの列ストア セグメント キャッシュの最大メモリ|メモリ制限なし| 32 GB<sup>2</sup>| 16 GB<sup>2</sup>| 352 MB<sup>2</sup>| 352 MB<sup>2</sup>|  
|[!INCLUDE[ssDEnoversion--../includes/ssdenoversion-md.md)] のデータベースごとのメモリ最適化データ サイズ最大値|メモリ制限なし| 32 GB<sup>2</sup>| 16 GB<sup>2</sup>| 352 MB<sup>2</sup>| 352 MB<sup>2</sup>|  





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>類似した記事

このセクションでは、同じ GitHub.com リポジトリ [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (4 + 4): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (2 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (1 + 2): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (6 + 0): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (13 + 2): **SQL 用の Linux** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (1 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (1 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (8 + 4): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (2 + 2): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (1 + 0): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (1 + 0): **SQL 用のツール**に関するドキュメント](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


&nbsp;


