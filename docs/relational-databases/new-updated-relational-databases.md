---
title: "更新 - リレーショナル データベース ドキュメント | Microsoft Docs"
description: "最近変更されたリレーショナル データベースに関するドキュメントで更新されたコンテンツのスニペットを示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.openlocfilehash: 1fbc7affa833eb34b6e13e28b229d47ac0b05a5c
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>新規または最近の更新: リレーショナル データベース ドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 9 月 28 日**&nbsp;から &nbsp; **2017 年 12 月 2 日**
- *対象領域:* &nbsp; **リレーショナル データベース**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SSMS XEvent プロファイラーの使用](extended-events/use-the-ssms-xe-profiler.md)
2. [SQL のフラット ファイルのインポート ウィザード](import-export/import-flat-file-wizard.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [tempdb データベース](#TitleNum_1)
2. [メモリ管理アーキテクチャ ガイド](#TitleNum_2)
3. [統計](#TitleNum_3)
4. [sp_server_diagnostics (Transact-SQL)](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-tempdb-databasedatabasestempdb-databasemd"></a>1. &nbsp; [tempdb データベース](databases/tempdb-database.md)

*更新日: 2017 年 11 月 20 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([次へ](#TitleNum_2))

<!-- Source markdown line 121.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5c8bb5f9c40625aaf955295e5b5d03e4257e6c6b 337555ea28f4c3fdd6b78f1bfb4d62607a6bf92d  (PR=4039  ,  Filename=tempdb-database.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=ef1fa818beea435f58986af3379853dc28f5efd8) -->



**tempdb のパフォーマンスの最適化**

 tempdb データベースのサイズと物理的な配置場所は、システムのパフォーマンスに影響を与えることがあります。 たとえば、tempdb に定義されているサイズが小さすぎると、..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] のインスタンスを再起動するたびに、tempdb のサイズがワークロードのサポートに必要なサイズまで自動的に拡張されるので、システムの処理負荷の一部が占有されます。

 可能な場合は、[データベースのファイルの瞬時初期化--../../relational-databases/databases/database-instant-file-initialization.md)を使用して、データ ファイル拡張操作のパフォーマンスを向上します。

 すべての tempdb ファイルに対する領域をあらかじめ割り当てるには、環境における一般的なワークロードに十分に対応できる大きさの値にファイル サイズを設定します。 これにより、パフォーマンスに影響を与える可能性がある tempdb の過度に頻繁な拡張が回避されます。 tempdb データベースは自動拡張が行われるように設定する必要がありますが、これは想定外の例外に対してディスク領域を増加するために使用する必要があります。

 各[ファイル グループ--../../relational-databases/databases/database-files-and-filegroups.md#filegroups)内でデータ ファイルのサイズを等しくする必要があります。これは、..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] がより多くの空き領域を持つファイル内の割り当てを優先する比例配分アルゴリズムを使用しているためです。 サイズの等しい複数のデータ ファイルに tempdb を分割すると、tempdb を使用する操作において効率の高い並列処理を実現できます。

 tempdb データベース ファイルの拡張単位が小さすぎることのないように、ファイル拡張の増分値を妥当なサイズに設定します。 tempdb に書き込まれたデータ量と比較してファイルの拡張単位が小さすぎると、tempdb を頻繁に拡張する必要が生じる場合があります。 このことは、パフォーマンスに影響します。

 現在の tempdb のサイズと拡張パラメーターを確認するには、次のクエリを使用します。
```sql
 SELECT name AS FileName,
    size*1.0/128 AS FileSizeinMB,
    CASE max_size
        WHEN 0 THEN 'Autogrowth is off.'
        WHEN -1 THEN 'Autogrowth is on.'
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-memory-management-architecture-guidememory-management-architecture-guidemd"></a>2.&nbsp; [メモリ管理アーキテクチャ ガイド](memory-management-architecture-guide.md)

*更新日: 2017 年 11 月 28 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_1) | [次へ](#TitleNum_3))

<!-- Source markdown line 75.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 dd47431ca47eab16af40e41adaeeaf3fc5fb7461 445f013af3bdad65dd3eaf837db7f744b43e8f97  (PR=4113  ,  Filename=memory-management-architecture-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=28cccac53767db70763e5e705b8cc59a83c77317) -->



以前のバージョンの SQL Server (..!NCLUDE-NotShown--ssVersion2005--../includes/ssversion2005-md.md)]、..!NCLUDE-NotShown--ssKatmai--../includes/ssKatmai-md.md)]、..!NCLUDE-NotShown--ssKilimanjaro--../includes/ssKilimanjaro-md.md)]) では、5 つの異なるメカニズムを利用してメモリが割り当てられていました。
-  **SPA (Single-page Allocator/単一ページ アロケータ)**。..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)] プロセスで 8 KB 以下のメモリ割り当てのみ含む。 構成オプションの *max server memory (MB)* と *min server memory (MB)* によって、SPA が利用する物理メモリの上限が決められていました。 同時にバッファー プールが SPA のメカニズムであり、これが単一ページ割り当てを最も多く利用していました。
-  **MPA (Multi-Page Allocator/複数ページ アロケータ)**。8KB より多くを要求するメモリ割り当て用。
-  **CLR アロケータ**。CLR 初期化中に作成される SQL CLR ヒープとそのグローバル割り当てを含む。
-  ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)] プロセスの**[スレッド スタック--../relational-databases/memory-management-architecture-guide.md#stacksizes)**のメモリ割り当て。
-  **DWA (Direct Windows allocations/直接 Windows 割り当て)**。Windows に直接行われるメモリ割り当て要求。 モジュールによって行われ、..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)] プロセスに読み込まれる、Windows のヒープ使用量と直接仮想割り当てが含まれます。 このようなメモリ割り当ての例としては、たとえば、拡張ストアド プロシージャ DLL からの割り当て、オートメーション プロシージャ (sp_OA 呼び出し) で作成されたオブジェクト、リンク サーバー プロバイダーからの割り当てがあります。

..!NCLUDE-NotShown--ssSQL11--../includes/sssql11-md.md)] 以降、SPA、MPA、CLR 割り当てがすべて統合され、**"あらゆるサイズの"** ページ アロケータになります。これは、構成オプションの *max server memory (MB)* と *min server memory (MB)* によって制御されるメモリ上限に含まれます。 この変更によって、..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)] メモリ マネージャーを通過するすべてのメモリ要件において、より正確にサイズを調整できるようになりました。



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-statisticsstatisticsstatisticsmd"></a>3.&nbsp; [統計](statistics/statistics.md)

*更新日: 2017 年 11 月 27 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_2) | [次へ](#TitleNum_4))

<!-- Source markdown line 48.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1dbe3bd6fdfcd27cf4a597cac5a4a09821b51ba7 971cfccf75fbc8842a0ef020a2bc93992c5f4ad9  (PR=4087  ,  Filename=statistics.md  ,  Dirpath=docs\relational-databases\statistics\  ,  MergeCommitSha40=9fbe5403e902eb996bab0b1285cdade281c1cb16) -->



> [!NOTE]
> ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] のヒストグラムは、静的オブジェクトのキー列セットの 1 列または最初の列用にのみ構築されています。

ヒストグラムを作成するには、クエリ オプティマイザーで列値を並べ替え、個別の列値ごとに一致する値の数を計算し、列値を最大 200 の連続したヒストグラム区間に集計します。 各ヒストグラム手順には、上限の列値までの列値の範囲が含まれます。 この範囲には、境界値の間 (境界値自体は除く) のすべての有効な列値が含まれます。 格納される最小の列値は、最初のヒストグラム区間の上限境界値になります。

詳しく説明すると、次の 3 つの手順で、..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] は列値の並べ替えられたセットから**ヒストグラム**を作成します。

- **ヒストグラムの初期化**: 最初の手順で、並べ替えられたセットの先頭から始まる値のシーケンスが処理され、*range_high_key*、*equal_rows*、*range_rows*、*distinct_range_rows* の最大 200 個の値が収集されます (この手順の間、*range_rows* と *distinct_range_rows* は常にゼロです)。 最初の手順は、すべての入力が使用されたとき、または 200 個の値が見つかったときに終了します。
- **バケットのマージを使用したスキャン**: 2 つ目の手順では、統計キーの先頭の列から追加された各値が並び順で処理されます。連続する各値は最後の範囲に追加されるか、末尾に新しい範囲が作成されます (これは、入力値が並べ替えられているため可能です。)。 新しい範囲が作成されると、既存の隣接する範囲の 1 組が 1 つの範囲に折りたたまれます。 情報の損失を最小限に抑えるために、この範囲の組が選択されます。 この方法では、*区間幅を最大にする*アルゴリズムを使用して境界値の差を最大にし、ヒストグラムの区間の数を最小限に抑えます。 範囲を折りたたんだ後の手順の数は、この手順全体で 200 個のままです。



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-spserverdiagnostics-transact-sqlsystem-stored-proceduressp-server-diagnostics-transact-sqlmd"></a>4. &nbsp; [sp_server_diagnostics (Transact-SQL)](system-stored-procedures/sp-server-diagnostics-transact-sql.md)

*更新日: 2017 年 11 月 21 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_3))

<!-- Source markdown line 157.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d0d97efbb0b16638d0120af9ac5e66ec3bcfa391 b98735ec26a091f8c8c58ca1790243be7942e038  (PR=4052  ,  Filename=sp-server-diagnostics-transact-sql.md  ,  Dirpath=docs\relational-databases\system-stored-procedures\  ,  MergeCommitSha40=45e4efb7aa828578fe9eb7743a1a3526da719555) -->



次のクエリ例では、テーブルから出力の概要を読み取ります。
```sql
SELECT create_time,
       component_name,
       state_desc
FROM SpServerDiagnosticsResult;
```

次のクエリ例では、テーブルの各コンポーネントから詳細な出力の一部を読み取ります。
```sql
-- system
select data.value('(/system/@systemCpuUtilization)[1]','bigint') as 'System_CPU',
   data.value('(/system/@sqlCpuUtilization)[1]','bigint') as 'SQL_CPU',
   data.value('(/system/@nonYieldingTasksReported)[1]','bigint') as 'NonYielding_Tasks',
   data.value('(/system/@pageFaults)[1]','bigint') as 'Page_Faults',
   data.value('(/system/@latchWarnings)[1]','bigint') as 'Latch_Warnings',
   data.value('(/system/@BadPagesDetected)[1]','bigint') as 'BadPages_Detected',
   data.value('(/system/@BadPagesFixed)[1]','bigint') as 'BadPages_Fixed'
from SpServerDiagnosticsResult
where component_name like 'system'
go

-- Resource Monitor
select data.value('(./Record/ResourceMonitor/Notification)[1]', 'VARCHAR(max)') AS [Notification],
    data.value('(/resource/memoryReport/entry[@description=''Working Set'']/@value)[1]', 'bigint')/1024 AS [SQL_Mem_in_use_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Paging File'']/@value)[1]', 'bigint')/1024 AS [Avail_Pagefile_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Physical Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_Physical_Mem_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Virtual Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_VAS_MB],
    data.value('(/resource/@lastNotification)[1]','varchar(100)') as 'LastNotification',
    data.value('(/resource/@outOfMemoryExceptions)[1]','bigint') as 'OOM_Exceptions'
from SpServerDiagnosticsResult
where component_name like 'resource'
go

-- Nonpreemptive waits
```







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (3 + 14): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (1 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (87 + 0): **SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (5 + 4): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 1): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (2 + 2): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (10 + 9): **Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (2 + 4): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (4 + 2): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 1): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (21 + 0): **SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (5 + 1): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (1 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の Data Migration Assistant (DMA)** に関するドキュメント](../dma/new-updated-dma.md)
- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


