---
title: "更新済み - SQL Server のドキュメント |Microsoft ドキュメント"
description: "更新されたコンテンツで最近変更したドキュメントについては、SQL Server 用のスニペットを表示します。"
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
ms.date: 06/30/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: f69a3301d46dcfffa811f11782c43791492a9c72
ms.contentlocale: ja-jp
ms.lasthandoff: 07/03/2017

---
<a id="new-and-recently-updated-sql-server-docs" class="xliff"></a>

# 新規または最近の更新: SQL Server のドキュメント



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新日の範囲:* &nbsp; **2017 年 5 月 17 日**&nbsp; から &nbsp;**2017 年 6 月 30 日**
- *サブジェクト領域:* &nbsp; **SQL Server**です。




&nbsp;

<a id="new-articles-created-recently" class="xliff"></a>

## 最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


*今回は新しい記事はありません。*



&nbsp;

<a id="updated-articles-with-excerpts" class="xliff"></a>

## 更新されたアーティクルの抜粋が

このセクションでは、大幅な更新が最近発生したアーティクルから収集された更新プログラムの抜粋を表示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

<a id="1-nbsp-customer-experience-improvement-program-for-sql-server-data-toolscustomer-experience-improvement-program-for-sql-server-data-toolsmd" class="xliff"></a>

### 1.&nbsp; [SQL Server Data Tools のカスタマー エクスペリエンス向上プログラム](customer-experience-improvement-program-for-sql-server-data-tools.md)

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

<a id="2-nbsp-editions-and-supported-features-of-sql-servereditions-and-components-of-sql-server-2016md" class="xliff"></a>

### 2.&nbsp; [エディションと SQL Server のサポートされる機能](editions-and-components-of-sql-server-2016.md)

*更新日: 2017 年 6 月 16 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_1) | [次へ](#TitleNum_3))

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




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

<a id="3-nbsp-sql-server-2017-release-notessql-server-2017-release-notesmd" class="xliff"></a>

### 3.&nbsp;[SQL Server 2017 年 1 リリース ノート](sql-server-2017-release-notes.md)

*更新日: 2017 年 5 月 17 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_2) | [次へ](#TitleNum_4))

<!-- Source markdown line 28.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 84e7a2a49f2893d49380db1ad75695d9a4fd59b2 27a145ad30c10fd667f926d2e092b88c0ba586c5  (PR=1737  ,  Filename=sql-server-2017-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=67c1c0f3a9da6cc5d050da5db8a493f5da934c2a) -->



**SQL Server 2017 CTP 2.1 (2017 年 5 月)**

**ドキュメント (CTP 2.1)**

- **問題およびユーザーへの影響:**のドキュメントを [です。[SsSQLv14_md--.. を含める/includes/sssqlv14-md.md)] は制限されてコンテンツに含まれ、[です。[SsSQL15_md--.. を含める/includes/sssql15-md.md)] ドキュメントのセット。  固有の記事の内容 [![SsSQLv14_md--.. を含める/includes/sssqlv14-md.md)] と共に記録されます**適用先**です。 
- **問題およびユーザーへの影響:**に対するオフライン コンテンツがありません [![SsSQLv14_md--.. を含める/includes/sssqlv14-md.md)] です。

**SQL Server Reporting Services (CTP 2.1)**


- **問題およびユーザーへの影響:** SQL Server Reporting Services と Power BI でレポート サーバーを同じコンピューターし、それらのいずれかのアンインストールの両方があれば、不要になったことができます、残りのレポート サーバーはレポート Server 構成マネージャーに接続します。
- **回避策**この問題を回避するには、サーバーのいずれかをアンインストールした後に、次の操作を行う必要があります。

    1. 管理者モードでコマンド プロンプトを起動します。
    2. 残りのレポート サーバーがインストールされているディレクトリに移動します。

        *Power BI のレポート サーバーの既定の場所: C:\Program files \microsoft Power BI のレポート サーバー*

        *SQL Server Reporting Services の既定の場所: C:\Program files \microsoft SQL Server Reporting Services*

    3. 次のフォルダーに移動し、します。 これになります*SSRS*または*PBIRS*残っている新機能によって異なります。
    4. WMI フォルダーに移動します。
    5. 次のコマンドを実行します。

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        表示する場合は、次のエラーを無視できます。

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

<a id="4-nbsp-what39s-new-in-sql-server-2017what-s-new-in-sql-server-2017md" class="xliff"></a>

### 4.&nbsp;[何 &#39; の SQL Server 2017](what-s-new-in-sql-server-2017.md)

*更新日: 2017 年 6 月 19 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_3))

<!-- Source markdown line 31.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 41ed3624662404aa63ade007d1ea987fe72a3ab5 921f698ae101f7e6b53d268621b868e1a7e7ada7  (PR=2075  ,  Filename=what-s-new-in-sql-server-2017.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=aa08b5e7de9bb317fd781a98ee5d829431b92df6) -->



**SQL Server 2017 CTP 2.1 (2017 年 5 月) の新機能**

* * SQL Server データベース エンジン * *

- 新しい DMF [sys.dm_db_log_stats--../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)、概要レベルの属性とトランザクション ログ ファイルに関する情報を公開するが導入されましたトランザクション ログの正常性を監視するために便利です。  
- この CTP には、バグ修正とパフォーマンスの向上、データベース エンジンが含まれています。
- 2017 年の詳細な一覧については以前の CTP リリースの CTP の機能強化は、[SQL Server 2017 (データベース エンジン)--新規は '..' を参照してください。/database-engine/configure-windows/what-s-new-in-sql-server-2017-database-engine.md)。

**SQL Server Reporting Services (SSRS)**

- SQL Server Reporting Services では、CTP 2.1 の時点での SQL Server のセットアップでインストールできるように不要になったです。
- コメントは、レポートに使用できるようになりました。 コメントでは、レポート内に何がパースペクティブを追加し、組織内の他のユーザーと共同作業を行うことができます。 コメントに、添付ファイルを含めることもできます。
- さらに詳細な SSRS の新機能の詳細の以前のリリースから、新しい情報、新機能 [Reporting Services--.. を参照してください。/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)。 
- Power BI のレポート サーバーについては、次を参照してください。 [Power BI のレポート サーバーの概要](https://powerbi.microsoft.com/documentation/reportserver-get-started/)です。

**SQL Server コンピューターのサービスの学習**

- この CTP では、Machine Learning のサービスの新機能はありません。
- さらに詳細な Machine Learning のサービスの新機能以前の Ctp からの詳細を含む、新しい情報、[新規の SQL Server マシン ラーニング サービス--は '..' を参照してください。/advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)。  

**SQL Server Analysis Services (SSAS)**

- この CTP に新しい SSAS 機能はありません。  
- 機能強化とバグ修正を行いました。 このリリースの詳細については、[新規で SQL Server 2017 Analysis Services - は '..' を参照してください。/analysis-services/what-s-new-in-sql-server-analysis-services-2017.md)。  





&nbsp;

<a name="compactupdatedlist"/>

<a id="compact-list-of-articles-updated-recently" class="xliff"></a>

## 最近更新されたアーティクルの圧縮のリスト

この圧縮リストは、前のセクションに記載されているすべての更新されたアーティクルへのリンクを提供します。

1. [SQL Server Data Tools のカスタマー エクスペリエンス向上プログラム](#TitleNum_1)
2. [エディションと SQL Server のサポートされる機能](#TitleNum_2)
3. [SQL Server 2017 年 1 リリース ノートします。](#TitleNum_3)
4. [どのような &#39; の SQL Server 2017](#TitleNum_4)




<a name="sisters2"/>

&nbsp;

<a id="sister-articles" class="xliff"></a>

## 関連記事

このセクションでは、同じ GitHub.com リポジトリ [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

<!--  20170630-1150  -->

<a id="subject-areas-which-do-have-new-or-recently-updated-articles" class="xliff"></a>

#### 新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (12 + 2): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (1 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 2): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (3 + 0): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (1 + 2): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (2 + 8): **SQL 用の Linux** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (1 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (5 + 5): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (2 + 0): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 4): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (1 + 0): **SQL 用のツール**に関するドキュメント](../tools/new-updated-tools.md)


<a id="subject-areas-which-have-no-new-or-recently-updated-articles" class="xliff"></a>

#### 新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


&nbsp;


