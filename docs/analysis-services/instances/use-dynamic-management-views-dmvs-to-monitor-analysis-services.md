---
title: Analysis Services での動的管理ビュー (Dmv) の使用 |Microsoft Docs
ms.date: 09/25/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 24dd1bce8d7433f55ba64eecb1e7a08396b9e548
ms.sourcegitcommit: 38076f423663bdbb42f325e3d0624264e05beda1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2018
ms.locfileid: "52984103"
---
# <a name="dynamic-management-views-dmvs"></a>動的管理ビュー (DMV) 

[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

Analysis Services 動的管理ビュー (DMV) は、モデル オブジェクト、サーバーの操作、およびサーバーの正常性に関する情報を返すクエリです。 SQL、に基づいて、クエリへのインターフェイスは、*スキーマ行セット*します。 スキーマ行セットは、Analysis Services オブジェクトとデータベース スキーマ、アクティブなセッション、接続、コマンド、サーバー上で実行されるジョブなどのサーバーの状態に関する情報を含む predescribed テーブルです。

DMV クエリは、XML/A Discover コマンドの実行の代わりとなる手段です。 ほとんどの管理者にとって DMV クエリを記述が簡単、構文は SQL に基づいているためです。 さらに、読み取りやコピーが容易な表形式で結果が返されます。 
  
ほとんどの DMV クエリを使用して、**選択**ステートメントと **$System**例については、xml/a スキーマ行セットを持つスキーマ。  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 DMV クエリは、クエリの実行時にサーバーとオブジェクトの状態に関する情報を返します。 リアルタイムで使用してトレース代わりに操作を監視します。 リアルタイムの詳細についてを参照、トレースを使用して監視[Analysis Services の監視を使用して SQL Server Profiler](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)します。  
  
## <a name="query-syntax"></a>クエリ構文

DMV のクエリ エンジンは、データ マイニング パーサーです。 DMV クエリ構文は、選択に基づいて&#40;DMX&#41;ステートメント。 DMV クエリ構文は SQL SELECT ステートメントに基づいていますが、SELECT ステートメントの完全な構文をサポートしていません。 特に、JOIN、GROUP BY、LIKE、CAST、CONVERT はサポートされていません。  
  
```  
SELECT [DISTINCT] [TOP <n>] <select list>  
FROM $System.<schemaRowset>  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
次の DISCOVER_CALC_DEPENDENCY の例では、クエリのパラメーターを提供するために WHERE 句を使用する方法について示しています。  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
WHERE OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
制限のあるスキーマ行セットには、クエリに SYSTEMRESTRICTSCHEMA 関数を含める必要があります。 次の例では、約 1103 互換性レベル表形式モデル CSDL メタデータを返します。 CATALOG_NAME では大文字と小文字が区別されることに注意してください。  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  

## <a name="examples-and-scenarios"></a>例とシナリオ

DMV クエリは、アクティブなセッションおよび接続に関する疑問に答えたり、特定の時刻に CPU またはメモリを最も消費しているオブジェクトを特定するために役立つ可能性があります。 以下に例を示します。
  
 `Select * from $System.discover_object_activity`  
このクエリは、サービスが前回起動されてからオブジェクト アクティビティについてレポートします。 
  
 `Select * from $System.discover_object_memory_usage`  
このクエリは、オブジェクトによるメモリ消費についてレポートします。  
  
 `Select * from $System.discover_sessions`  
このクエリは、セッションのユーザーや期間など、アクティブ セッションについてレポートします。  
  
 `Select * from $System.discover_locks`   
このクエリでは、特定の時点で使用されるロックのスナップショットを返します。  


## <a name="tools-and-permissions"></a>ツールと権限

MDX または DMX クエリをサポートする任意のクライアント アプリケーションを使用することができます。 ほとんどの場合、SQL Server Management Studio を使用することをお勧めします。 サーバー管理者のアクセス許可は、DMV クエリを実行するには、インスタンスが必要です。  
  
 **SQL Server Management Studio から DMV クエリを実行するには**

1. サーバーとクエリを実行するモデル オブジェクトに接続します。 
2. サーバーまたはデータベース オブジェクトを右クリックして >**新しいクエリ** > **MDX**します。
3. クエリを入力し、クリックして**Execute**、F5 キーを押します。
  
## <a name="schema-rowsets"></a>スキーマ行セット

すべてのスキーマ行セットに DMV インターフェイスがあるわけではありません。 DMV を使用してクエリを行うことができる、すべてのスキーマ行セットの一覧を返すには、次のクエリを実行します。  
 
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
DMV が指定された行セットは利用できない場合、サーバーには、エラーが返されます。`The <schemarowset> request type was not recognized by the server.` その他のすべてのエラーは、構文を使用して問題を示します。  

2 つの SQL Server Analysis Services プロトコルでは、スキーマ行セットがについて説明します。   

[[MS-SSAS-T]:SQL Server Analysis Services 表形式のプロトコル](https://msdn.microsoft.com/library/mt719260)-1200 以降の互換性レベル表形式モデルのスキーマ行セットについて説明します。

[MS-SSAS:SQL Server Analysis Services プロトコル](https://msdn.microsoft.com/library/ee320606)-多次元モデルと、互換性レベル 1100 と 1103 の表形式モデルのスキーマ行セットについて説明します。

### <a name="rowsets-described-in-the-ms-ssas-t-sql-server-analysis-services-tabular-protocol"></a>[MS SSAS--t] で説明されている行セット。SQL Server Analysis Services 表形式のプロトコル

|[行セット]  |説明  |
|---------|---------|
|[TMSCHEMA_ANNOTATIONS](https://msdn.microsoft.com/library/mt704370)|モデル内の注釈オブジェクトに関する情報を提供します。|
|[TMSCHEMA_ATTRIBUTE_HIERARCHIES](https://msdn.microsoft.com/library/mt704362)     |   列の AttributeHierarchy オブジェクトに関する情報を提供します。      |
|[TMSCHEMA_COLUMNS](https://msdn.microsoft.com/library/mt704373)    |  各テーブル内の列オブジェクトに関する情報を提供します。       |
|[TMSCHEMA_COLUMN_PERMISSIONS](https://msdn.microsoft.com/library/mt842440)|各テーブルのアクセス許可の ColumnPermission オブジェクトに関する情報を提供します。|
|[TMSCHEMA_CULTURES](https://msdn.microsoft.com/library/mt719125)|モデルのカルチャ オブジェクトについてを説明します。|
|[TMSCHEMA_DATA_SOURCES](https://msdn.microsoft.com/library/mt719191)   |   モデル内のデータ ソース オブジェクトに関する情報を提供します。      |
|[TMSCHEMA_DETAIL_ROWS_DEFINITIONS](https://msdn.microsoft.com/library/mt825017)|モデル内の DetailRowsDefinition オブジェクトに関する情報を提供します。|
|[TMSCHEMA_EXPRESSIONS](https://msdn.microsoft.com/library/mt825015)|モデル内の式オブジェクトに関する情報を提供します。|
|[TMSCHEMA_EXTENDED_PROPERTIES](https://msdn.microsoft.com/library/mt842451)|モデル内の ExtendedProperty オブジェクトに関する情報を提供します。|
|[TMSCHEMA_HIERARCHIES](https://msdn.microsoft.com/library/mt719136)    |    各テーブル内の階層オブジェクトに関する情報を提供します。     |
|[TMSCHEMA_KPIS](https://msdn.microsoft.com/library/mt719002)     |    モデルの KPI オブジェクトについてを説明します。     |
|[TMSCHEMA_LEVELS](https://msdn.microsoft.com/library/mt719038)     |   各階層のレベルのオブジェクトに関する情報を提供します。      |
|[TMSCHEMA_LINGUISTIC_METADATA](https://msdn.microsoft.com/library/mt719169)|特定のカルチャのモデル内のオブジェクトのシノニムについての情報を提供します。|
|[TMSCHEMA_MEASURES](https://msdn.microsoft.com/library/mt719218)     |    各テーブル内のメジャー オブジェクトに関する情報を提供します。     |
|[TMSCHEMA_MODEL](https://msdn.microsoft.com/library/mt719042)    |  データベースでは、モデル オブジェクトを指定します。       |
|[TMSCHEMA_OBJECT_TRANSLATIONS](https://msdn.microsoft.com/library/mt719119)|カルチャのさまざまなオブジェクトの翻訳についての情報を提供します。|
|[TMSCHEMA_PARTITIONS](https://msdn.microsoft.com/library/mt704375)     |     各テーブル内のパーティション オブジェクトに関する情報を提供します。    |
|[TMSCHEMA_PERSPECTIVE_COLUMNS](https://msdn.microsoft.com/library/mt719164)     |   各 PerspectiveTable オブジェクトに PerspectiveColumn オブジェクトに関する情報を提供します。      |
|[TMSCHEMA_PERSPECTIVE_HIERARCHIES](https://msdn.microsoft.com/library/mt719104)     |  各 PerspectiveTable オブジェクトに PerspectiveHierarchy オブジェクトに関する情報を提供します。       |
|[TMSCHEMA_PERSPECTIVE_MEASURES](https://msdn.microsoft.com/library/mt719135)     |    各 PerspectiveTable オブジェクトに PerspectiveMeasure オブジェクトに関する情報を提供します。     |
|[TMSCHEMA_PERSPECTIVE_TABLES](https://msdn.microsoft.com/library/mt719272)     |    パースペクティブ テーブル オブジェクトに関する情報を提供します。     |
|[TMSCHEMA_PERSPECTIVES](https://msdn.microsoft.com/library/mt704340)     |     モデルのパースペクティブ オブジェクトについてを説明します。    |
|[TMSCHEMA_RELATIONSHIPS](https://msdn.microsoft.com/library/mt704355)     |    モデルのリレーションシップ オブジェクトに関する情報を提供します。     |
|[TMSCHEMA_ROLE_MEMBERSHIPS](https://msdn.microsoft.com/library/mt704584)     |  RoleMembership オブジェクト内の各ロールに関する情報を提供します。      |
|[TMSCHEMA_ROLES](https://msdn.microsoft.com/library/mt719267)    |   モデル内のロール オブジェクトに関する情報を提供します。      |
|[TMSCHEMA_TABLE_PERMISSIONS](https://msdn.microsoft.com/library/mt704347)    |    TablePermission オブジェクト内の各ロールに関する情報を提供します。     |
|[TMSCHEMA_TABLES](https://msdn.microsoft.com/library/mt719250)     |   モデル内のテーブル オブジェクトについてを説明します。      |
|[TMSCHEMA_VARIATIONS](https://msdn.microsoft.com/library/mt825008)|各列内のバリエーション オブジェクトに関する情報を提供します。|

### <a name="rowsets-described-in-the-ms-ssas-sql-server-analysis-services-protocol"></a>[MS SSAS] で説明されている行セット。SQL Server Analysis Services のプロトコル

|[行セット]|説明|  
|------------|-----------------|  
|[DBSCHEMA_CATALOGS](https://msdn.microsoft.com/library/ee302115)|サーバーにアクセス可能なカタログをについて説明します。|  
|[DBSCHEMA_COLUMNS](https://msdn.microsoft.com/library/ee301789)|各メジャー、各キューブ ディメンションの属性、および列として公開される各スキーマ行セット列の行を返します。|  
|[DBSCHEMA_PROVIDER_TYPES](https://msdn.microsoft.com/library/ee301696)|サーバーでサポートされている (基本) データ型を識別します。|  
|[DBSCHEMA_TABLES](https://msdn.microsoft.com/library/ee320843)|ディメンション、メジャー グループ、またはテーブルとして公開されるスキーマ行セットを返します。|  
|[DISCOVER_CALC_DEPENDENCY](https://msdn.microsoft.com/library/hh770226)| 表形式データベースまたは表形式データベースに対して実行される DAX クエリで指定されたオブジェクトの計算依存関係についての情報を返します。 |  
|[DISCOVER_COMMAND_OBJECTS](https://msdn.microsoft.com/library/ee320662)|参照先のコマンドで使用中のオブジェクトに関するリソース使用状況とアクティビティ情報を提供します。|  
|[DISCOVER_COMMANDS](https://msdn.microsoft.com/library/ee320715)|サーバー上の開いている接続で現在実行中または最後に実行されたコマンドに関するリソース使用状況とアクティビティ情報を提供します。|  
|[DISCOVER_CONNECTIONS](https://msdn.microsoft.com/library/ee301889)|現在サーバー上で開いている接続について、リソースの使用状況とアクティビティに関する情報を提供します。|  
|[DISCOVER_CSDL_METADATA](https://msdn.microsoft.com/library/gg587670)|メモリ内のデータベースのデータベースのメタデータに関する情報を返します。|  
|[DISCOVER_DATASOURCES](https://msdn.microsoft.com/library/ee320285)|サーバーで使用できるデータ ソースの一覧を返します。|
|[DISCOVER_DB_CONNECTIONS](https://msdn.microsoft.com/library/ee320467)|サーバーからデータベースへの現在開いている接続に関するリソース使用量と利用状況の情報を提供します。|  
|[DISCOVER_DIMENSION_STAT](https://msdn.microsoft.com/library/ee320284)|指定したディメンションで統計を返します。|  
|[DISCOVER_ENUMERATORS](https://msdn.microsoft.com/library/ee302012)|特定のデータ ソースの XMLA プロバイダーによってサポートされている列挙子の名前、データ型、および列挙値の一覧を返します。|  
|[DISCOVER_INSTANCES](https://msdn.microsoft.com/library/ee320541)|サーバー上のインスタンスについて記述します。|  
|[DISCOVER_JOBS](https://msdn.microsoft.com/library/ee320363)|サーバーで実行されているアクティブなジョブに関する情報を提供します。 ジョブはコマンドの一部であり、コマンドに代わって特定のタスクを実行します。|  
|[DISCOVER_KEYWORDS &AMP;#40;XMLA&AMP;#41;](https://msdn.microsoft.com/library/ee301719)|XMLA サーバーによって予約されているキーワードに関する情報を返します。|  
|[DISCOVER_LITERALS](https://msdn.microsoft.com/library/ee301320)|サーバーでサポートされているリテラルに関する情報を返します。|  
|[DISCOVER_LOCATIONS](https://msdn.microsoft.com/library/ee302024)|バックアップ ファイルの内容に関する情報を返します。 |
|[DISCOVER_LOCKS](https://msdn.microsoft.com/library/ee320398)|サーバー上で現在保持されているロックに関する情報を提供します。|  
|[DISCOVER_MASTER_KEY](https://msdn.microsoft.com/library/ee301825)|サーバーのマスター暗号化キーを返します。|
|[DISCOVER_MEMORYGRANT](https://msdn.microsoft.com/library/ee320945)|サーバーで現在実行中のジョブによって確保されている内部メモリ クォータ付与の一覧を返します。|  
|[DISCOVER_MEMORYUSAGE](https://msdn.microsoft.com/library/ee320910)|サーバーによって割り当てられているさまざまなオブジェクトの DISCOVER_MEMORYUSAGE 統計を返します。|  
|[DISCOVER_OBJECT_ACTIVITY](https://msdn.microsoft.com/library/ee320661)|サービスが開始されてからのオブジェクトごとのリソース使用量に関する情報を提供します。|  
|[DISCOVER_OBJECT_MEMORY_USAGE](https://msdn.microsoft.com/library/ee320910)|サーバーによって割り当てられているさまざまなオブジェクトの DISCOVER_MEMORYUSAGE 統計を返します。|  
|[DISCOVER_PARTITION_DIMENSION_STAT](https://msdn.microsoft.com/library/ee320268)|パーティションに関連付けられているディメンションで統計を返します。|  
|[DISCOVER_PARTITION_STAT](https://msdn.microsoft.com/library/ee320483)|特定のパーティションの集計に関する統計を返します。|  
|[DISCOVER_PERFORMANCE_COUNTERS](https://msdn.microsoft.com/library/ee320809)|指定した 1 つ以上のパフォーマンス カウンターの値を返します。 |  
|[DISCOVER_PROPERTIES](https://msdn.microsoft.com/library/ee320589)|指定されたデータ ソースのサーバーでサポートされているプロパティに関する情報と値の一覧を返します。|  
|[DISCOVER_RING_BUFFERS](https://msdn.microsoft.com/library/mt719204)|サーバー上の現在の XEvent リング バッファーについての情報を返します。|
|[DISCOVER_SCHEMA_ROWSETS](https://msdn.microsoft.com/library/ee320478)|名前、制限、説明、およびすべての検出要求の他の情報を返します。|  
|[DISCOVER_SESSIONS](https://msdn.microsoft.com/library/ee301962)|サーバー上で現在開いているセッションに関するリソース使用量と利用状況の情報を提供します。|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](https://msdn.microsoft.com/library/ee320710)|インメモリ テーブルでのデータを格納するために使用される列セグメントに関する情報を返します。|  
|[DISCOVER_STORAGE_TABLE_COLUMNS](https://msdn.microsoft.com/library/ee302101)|メモリ内のテーブルの列を表すために使用する列についての情報が含まれています。|  
|[DISCOVER_STORAGE_TABLES](https://msdn.microsoft.com/library/ee302014)|サーバーに使用可能なメモリ内テーブルに関する統計情報を返します。|  
|[DISCOVER_TRACE_COLUMNS](https://msdn.microsoft.com/library/ee301342)||  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO](https://msdn.microsoft.com/library/ee301342)|DISCOVER_TRACE_COLUMNS スキーマ行セットが含まれています。|  
|[DISCOVER_TRACE_EVENT_CATEGORIES](https://msdn.microsoft.com/library/ee320442)|DISCOVER_TRACE_EVENT_CATEGORIES スキーマ行セットが含まれています。|  
|[DISCOVER_TRACES](https://msdn.microsoft.com/library/ee301643)|DISCOVER_TRACES スキーマ行セットが含まれています。|  
|[DISCOVER_TRANSACTIONS](https://msdn.microsoft.com/library/ee301363)|現在システムで保留中のトランザクションのセットを返します。|  
|[DISCOVER_XEVENT_TRACE_DEFINITION](https://msdn.microsoft.com/library/mt704568)|サーバーで現在アクティブな XEvent トレースに関する情報を提供します。|  
|[DISCOVER_XEVENT_PACKAGES](https://msdn.microsoft.com/library/mt704569)|サーバーで説明されている XEvent パッケージに関する情報を提供します。|
|[DISCOVER_XEVENT_OBJECTS](https://msdn.microsoft.com/library/mt704543)|サーバーで説明されている XEvent オブジェクトに関する情報を提供します。|
|[DISCOVER_XEVENT_OBJECT_COLUMNS](https://msdn.microsoft.com/library/mt719352)|サーバーで説明されている XEvent オブジェクトのスキーマに関する情報を提供します。|
|[DISCOVER_XEVENT_SESSIONS](https://msdn.microsoft.com/library/mt704397)|サーバー上の現在の XEvent セッションに関する情報を提供します。|
|[DISCOVER_XEVENT_SESSION_TARGETS](https://msdn.microsoft.com/library/mt704564)|サーバー上の現在の XEvent セッション ターゲットに関する情報を提供します。|
|[DISCOVER_XML_METADATA](https://msdn.microsoft.com/library/ee301560)|1 つの行と 1 つの列を含む行セットを返します。 |
|[DMSCHEMA_MINING_COLUMNS](https://msdn.microsoft.com/library/ee301664)|サーバーに展開されているすべての説明のデータ マイニング モデルの個々 の列について説明します。|  
|[DMSCHEMA_MINING_FUNCTIONS](https://msdn.microsoft.com/library/ee320415)|Analysis Services を実行しているサーバーで使用できるデータ マイニング アルゴリズムでサポートされているデータ マイニング関数について説明します。|  
|[DMSCHEMA_MINING_MODEL_CONTENT](https://msdn.microsoft.com/library/ee302124)|トレーニング済みのデータ マイニング モデルのコンテンツを参照するクライアント アプリケーションを有効にします。|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML](https://msdn.microsoft.com/library/ee320692)|マイニング モデルの XML 構造を返します。 XML 文字列の形式では、PMML 2.1 の標準に従います。|  
|[DMSCHEMA_MINING_MODEL_XML](https://msdn.microsoft.com/library/ee301916)|マイニング モデルの XML 構造を返します。 XML 文字列の形式では、PMML 2.1 の標準に従います。|  
|[DMSCHEMA_MINING_MODELS](https://msdn.microsoft.com/library/ee320603)|サーバー上に配置されているデータ マイニング モデルを列挙します。|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS](https://msdn.microsoft.com/library/ee320378)|サーバーにインストールされている各データ マイニング アルゴリズムの動作を構成するために使用できるパラメーターの一覧を提供します。|  
|[DMSCHEMA_MINING_SERVICES](https://msdn.microsoft.com/library/ee320487)|サーバーでサポートされている各データ マイニング アルゴリズムについてを説明します。|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS](https://msdn.microsoft.com/library/ee320277)|サーバー上に配置されているすべてのマイニング構造の各列について記述します。|  
|[DMSCHEMA_MINING_STRUCTURES](https://msdn.microsoft.com/library/ee320704)|現在のカタログ内のマイニング構造に関する情報を列挙します。|  
|[MDSCHEMA_ACTIONS](https://msdn.microsoft.com/library/ee320890)|クライアント アプリケーションで使用できることができるアクションをについて説明します。|
|[MDSCHEMA_CUBES](https://msdn.microsoft.com/library/ee301304)|データベース内のキューブの構造について記述します。 パースペクティブは、このスキーマにも返されます。|
|[MDSCHEMA_DIMENSIONS](https://msdn.microsoft.com/library/ee301366)|データベース内のディメンションについて説明します。|  
|[MDSCHEMA_FUNCTIONS](https://msdn.microsoft.com/library/mt719467)|DAX と MDX 言語で使用するために現在使用できる関数についての情報を返します。|
|[MDSCHEMA_HIERARCHIES](https://msdn.microsoft.com/library/ee320250)|特定のディメンション内の各階層について記述します。|  
|[MDSCHEMA_INPUT_DATASOURCES](https://msdn.microsoft.com/library/ee301386)|データベース内で説明されているデータ ソース オブジェクトをについて説明します。|  
|[MDSCHEMA_KPIS](https://msdn.microsoft.com/library/ee320406)|データベース内で Kpi をについて説明します。|  
|[MDSCHEMA_LEVELS](https://msdn.microsoft.com/library/ee320746)|特定の階層内の各レベルについて記述します。|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS](https://msdn.microsoft.com/library/ee320977)|メジャー グループのディメンションを列挙します。|  
|[MDSCHEMA_MEASUREGROUPS](https://msdn.microsoft.com/library/ee320601)|データベース内のメジャー グループについて記述します。|  
|[MDSCHEMA_MEASURES](https://msdn.microsoft.com/library/ee301871)|各メジャーをについて説明します。|  
|[MDSCHEMA_MEMBERS](https://msdn.microsoft.com/library/ee320960)|データベース内のメンバーについて記述します。|  
|[MDSCHEMA_PROPERTIES](https://msdn.microsoft.com/library/ee320393)|メンバーのプロパティおよびセルのプロパティについて説明します。|  
|[MDSCHEMA_SETS](https://msdn.microsoft.com/library/ee301356)|セッション スコープのセットを含む、データベースで現在説明されているすべてのセットについて説明します。|  

> [!NOTE]
> 記憶域の Dmv には、プロトコルで説明されているスキーマ行セットはありません。