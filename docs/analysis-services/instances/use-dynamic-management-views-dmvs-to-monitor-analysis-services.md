---
title: "Analysis Services の監視を動的管理ビュー (Dmv) を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22b82b2d-867f-4ebf-9288-79d1cdd62f18
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 6969869d6f4a7c10303838d2e3e696ae577fe180
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="use-dynamic-management-views-dmvs-to-monitor-analysis-services"></a>動的管理ビュー (DMV) を使用した Analysis Services の監視
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Analysis Services 動的管理ビュー (DMV) は、ローカル サーバーの操作やサーバーの正常性に関する情報を公開するクエリ構造です。 クエリ構造は、Analysis Services インスタンスのメタデータと監視情報を返すためのスキーマ行セットへのインターフェイスです。  
  
 ほとんどの DMV クエリでは、XML/A スキーマ行セットと合わせて **SELECT** ステートメントと **$System** スキーマを使用します。  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 DMV クエリは、クエリが実行された時点でのサーバーの状態に関する情報を返します。 リアルタイムでの操作を監視するには、代わりにトレースを使用します。 詳細については、「 [SQL Server Profiler を使用した Analysis Services の監視](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)」を参照してください。  
  
 このトピックのセクションは次のとおりです。  
  
 [DMV クエリを使用する利点](#bkmk_ben)  
  
 [例とシナリオ](#bkmk_ex)  
  
 [クエリ構文](#bkmk_syn)  
  
 [ツールと権限](#bkmk_tools)  
  
 [DMV リファレンス](#bkmk_ref)  
  
##  <a name="bkmk_ben"></a> DMV クエリを使用する利点  
 DMV クエリは、他の手段では取得できない操作とリソース消費に関する情報を返します。  
  
 DMV クエリは、XML/A Discover コマンドの実行の代わりとなる手段です。 クエリの構文は SQL に基づいているため、多くの管理者にとって DMV クエリを記述するのはより簡単です。 また、結果セットは、読み取りやコピーが容易な表形式で返されます。  
  
##  <a name="bkmk_ex"></a> 例とシナリオ  
 DMV クエリは、アクティブなセッションおよび接続に関する疑問に答えたり、特定の時刻に CPU またはメモリを最も消費しているオブジェクトを特定するために役立つ可能性があります。 このセクションでは、DMV クエリが最もよく使用されるシナリオの例を示します。 DMV クエリを使用してサーバー インスタンスを監視する方法の詳細については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](http://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409) 」を参照してください。  
  
 `Select * from $System.discover_object_activity` /** このクエリは、サービスの前回の開始以降のオブジェクト アクティビティについてレポートします。 この DMV に基づくクエリの例については、「 [New System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322)」を参照してください。  
  
 `Select * from $System.discover_object_memory_usage` /** このクエリは、オブジェクトによるメモリ消費についてレポートします。  
  
 `Select * from $System.discover_sessions` /** このクエリは、セッションのユーザーや期間など、アクティブ セッションについてレポートします。  
  
 `Select * from $System.discover_locks` /** このクエリは、特定の時点で使用されるロックのスナップショットを返します。  
  
##  <a name="bkmk_syn"></a> クエリ構文  
 DMV のクエリ エンジンは、データ マイニング パーサーです。 DMV クエリ構文は、[SELECT (DMX)](../../dmx/select-dmx.md) ステートメントに基づきます。  
  
 DMV クエリ構文は SQL SELECT ステートメントに基づいていますが、SELECT ステートメントの完全な構文をサポートしていません。 特に、JOIN、GROUP BY、LIKE、CAST、CONVERT はサポートされていません。  
  
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
  
 または、制限のあるスキーマ行セットについては、クエリに SYSTEMRESTRICTSCHEMA 関数を含める必要があります。 次の例は、表形式モードのサーバーで実行されている表形式モデルに関する CSDL メタデータを返します。 CATALOG_NAME では大文字と小文字が区別されることに注意してください。  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  
  
##  <a name="bkmk_tools"></a> ツールと権限  
 DMV のクエリを行うには、Analysis Services インスタンスに対するシステム管理者権限が必要です。  
  
 SQL Server Management Studio、Reporting Services レポート、または PerformancePoint ダッシュボードなど、MDX または DMX クエリをサポートするクライアント アプリケーションを使用できます。  
  
 Management Studio から DMV クエリを実行するには、クエリを行うインスタンスに接続し、 **[新しいクエリ]**をクリックします。 MDX または DMX クエリ ウィンドウからクエリを実行することができます。  
  
##  <a name="bkmk_ref"></a> DMV リファレンス  
 すべてのスキーマ行セットに DMV インターフェイスがあるわけではありません。 DMV を使用してクエリを行うことができる、すべてのスキーマ行セットの一覧を返すには、次のクエリを実行します。  
  
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
> [!NOTE]  
>  サーバーが、次のエラーを返す DMV が指定された行セットは利用できない場合は、:"、 \<schemarowset > 要求の種類は、サーバーで認識されませんでした"。 他のすべてのエラーは、構文の問題を示します。  
  
|[行セット]|Description|  
|------------|-----------------|  
|[DBSCHEMA_CATALOGS 行セット](../../analysis-services/schema-rowsets/ole-db/dbschema-catalogs-rowset.md)|現在の接続の Analysis Services データベースの一覧を返します。|  
|[DBSCHEMA_COLUMNS 行セット](../../analysis-services/schema-rowsets/ole-db/dbschema-columns-rowset.md)|現在のデータベース内のすべての列の一覧を返します。 DMV クエリを作成するために、この一覧を使用できます。|  
|[DBSCHEMA_PROVIDER_TYPES 行セット](../../analysis-services/schema-rowsets/ole-db/dbschema-provider-types-rowset.md)|OLE DB データ プロバイダーでサポートされる基本データ型に関するプロパティを返します。|  
|[DBSCHEMA_TABLES 行セット](../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md)|現在のデータベース内のすべてのテーブルの一覧を返します。 DMV クエリを作成するために、この一覧を使用できます。|  
|[DISCOVER_CALC_DEPENDENCY 行セット](../../analysis-services/schema-rowsets/xml/discover-calc-dependency-rowset.md)|他の列およびテーブルとの依存関係があるモデルで使用されている列およびテーブルの一覧を返します。|  
|[DISCOVER_COMMAND_OBJECTS 行セット](../../analysis-services/schema-rowsets/xml/discover-command-objects-rowset.md)|参照先のコマンドによって使用されているオブジェクトに関するリソース使用量と利用状況の情報を提供します。|  
|[DISCOVER_COMMANDS 行セット](../../analysis-services/schema-rowsets/xml/discover-commands-rowset.md)|現在実行されているコマンドのリソース使用状況とアクティビティ情報を提供します。|  
|[DISCOVER_CONNECTIONS 行セット](../../analysis-services/schema-rowsets/xml/discover-connections-rowset.md)|Analysis Services に対して開いている接続について、リソースの使用状況とアクティビティに関する情報を提供します。|  
|[DISCOVER_CSDL_METADATA 行セット](../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md)|テーブル モデルに関する情報を返します。<br /><br /> SYSTEMRESTRICTSCHEMA と追加のパラメーターが必要です。|  
|[DISCOVER_DB_CONNECTIONS 行セット](../../analysis-services/schema-rowsets/xml/discover-db-connections-rowset.md)|たとえば処理中またはインポート中に、Analysis Services から外部データ ソースに対して開いている接続について、リソースの使用状況とアクティビティに関する情報を提供します。|  
|[DISCOVER_DIMENSION_STAT 行セット](../../analysis-services/schema-rowsets/xml/discover-dimension-stat-rowset.md)|モデルの種類により、テーブルのディメンションまたは列の属性を返します。|  
|[DISCOVER_ENUMERATORS 行セット](../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)|特定のデータ ソースについてサポートされている列挙子に関するメタデータを返します。|  
|[DISCOVER_INSTANCES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)|指定したインスタンスに関する情報を返します。<br /><br /> SYSTEMRESTRICTSCHEMA と追加のパラメーターが必要です。|  
|[DISCOVER_JOBS 行セット](../../analysis-services/schema-rowsets/xml/discover-jobs-rowset.md)|現在のジョブに関する情報を返します。|  
|[DISCOVER_KEYWORDS 行セット (XMLA)](../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)|予約されているキーワードの一覧を返します。|  
|[DISCOVER_LITERALS 行セット](../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)|XMLA によってサポートされているデータ型や値など、リテラルの一覧を返します。|  
|[DISCOVER_LOCKS 行セット](../../analysis-services/schema-rowsets/xml/discover-locks-rowset.md)|特定の時点で使用されているロックのスナップショットを返します。|  
|[DISCOVER_MEMORYGRANT 行セット](../../analysis-services/schema-rowsets/xml/discover-memorygrant-rowset.md)|スタートアップ時に Analysis Services によって割り当てられたメモリに関する情報を返します。|  
|[DISCOVER_MEMORYUSAGE 行セット](../../analysis-services/schema-rowsets/xml/discover-memoryusage-rowset.md)|特定のオブジェクトによるメモリ使用量を示しています。|  
|[DISCOVER_OBJECT_ACTIVITY 行セット](../../analysis-services/schema-rowsets/xml/discover-object-activity-rowset.md)|サービスの前回の開始以降のオブジェクト アクティビティについてレポートします。|  
|[DISCOVER_OBJECT_MEMORY_USAGE 行セット](../../analysis-services/schema-rowsets/xml/discover-object-memory-usage-rowset.md)|オブジェクトによるメモリ消費についてレポートします。|  
|[DISCOVER_PARTITION_DIMENSION_STAT 行セット](../../analysis-services/schema-rowsets/xml/discover-partition-dimension-stat-rowset.md)|ディメンションの属性に関する情報を提供します。<br /><br /> SYSTEMRESTRICTSCHEMA と追加のパラメーターが必要です。|  
|[DISCOVER_PARTITION_STAT 行セット](../../analysis-services/schema-rowsets/xml/discover-partition-stat-rowset.md)|ディメンション、テーブル、またはメジャー グループのパーティションに関する情報を提供します。<br /><br /> SYSTEMRESTRICTSCHEMA と追加のパラメーターが必要です。|  
|[DISCOVER_PERFORMANCE_COUNTERS 行セット](../../analysis-services/schema-rowsets/xml/discover-performance-counters-rowset.md)|パフォーマンス カウンターで使用される列を示します。<br /><br /> SYSTEMRESTRICTSCHEMA と追加のパラメーターが必要です。|  
|[DISCOVER_PROPERTIES 行セット](../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)|指定されたデータ ソースの XMLA によってサポートされるプロパティに関する情報を返します。|  
|[DISCOVER_SCHEMA_ROWSETS 行セット](../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)|XMLA によってサポートされているすべての列挙値について、名前、制限、説明、その他の情報を返します。|  
|[DISCOVER_SESSIONS 行セット](../../analysis-services/schema-rowsets/xml/discover-sessions-rowset.md)|セッションのユーザーや期間など、アクティブ セッションについてレポートします。|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS 行セット](../../analysis-services/schema-rowsets/xml/discover-storage-table-column-segments-rowset.md)|テーブル モードまたは SharePoint モードで動作している Analysis Services データベースに関して、使用されているストレージ テーブルについての列およびセグメント レベルの情報を提供します。|  
|[DISCOVER_STORAGE_TABLE_COLUMNS 行セット](../../analysis-services/schema-rowsets/xml/discover-storage-table-columns-rowset.md)|クライアントは、テーブル モードまたは SharePoint モードで動作している Analysis Services データベースによって使用されるストレージ テーブルに対する列の割り当てを確認できます。|  
|[DISCOVER_STORAGE_TABLES 行セット](../../analysis-services/schema-rowsets/xml/discover-storage-tables-rowset.md)|テーブル モデル データベース内のモデルを格納するためのテーブルに関する情報を返します。|  
|[DISCOVER_TRACE_COLUMNS 行セット](../../analysis-services/schema-rowsets/xml/discover-trace-columns-rowset.md)|トレースに表示される列の XML 記述を返します。|  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO 行セット](../../analysis-services/schema-rowsets/xml/discover-trace-definition-providerinfo-rowset.md)|プロバイダーの名前とバージョン情報を返します。|  
|[DISCOVER_TRACE_EVENT_CATEGORIES 行セット](../../analysis-services/schema-rowsets/xml/discover-trace-event-categories-rowset.md)|使用できるカテゴリの一覧を返します。|  
|[DISCOVER_TRACES 行セット](../../analysis-services/schema-rowsets/xml/discover-traces-rowset.md)|現在の接続でアクティブに実行しているトレースの一覧を返します。|  
|[DISCOVER_TRANSACTIONS 行セット](../../analysis-services/schema-rowsets/xml/discover-transactions-rowset.md)|現在の接続でアクティブに実行しているトランザクションの一覧を返します。|  
|[DISCOVER_XEVENT_TRACE_DEFINITION 行セット](http://msdn.microsoft.com/library/e1ce2d2d-f994-4318-801a-ee0385aecd84)|現在の接続でアクティブに実行している XEvent トレースの一覧を返します。|  
|[DMSCHEMA_MINING_COLUMNS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|現在の接続で利用可能な、すべてのマイニング モデルの個々の列を一覧表示します。|  
|[DMSCHEMA_MINING_FUNCTIONS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)|サーバー上のデータ マイニング アルゴリズムによってサポートされる関数の一覧を返します。|  
|[DMSCHEMA_MINING_MODEL_CONTENT 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|現在のモデルを説明する列で構成される行セットを返します。|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)|PMML 形式で現在のモデルを説明する列で構成される行セットを返します。|  
|[DMSCHEMA_MINING_MODEL_XML 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)|PMML 形式で現在のモデルを説明する列で構成される行セットを返します。|  
|[DMSCHEMA_MINING_MODELS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|現在のデータベース内のマイニング モデルの一覧を返します。|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|サーバー上のアルゴリズムのパラメーターの一覧を返します。|  
|[DMSCHEMA_MINING_SERVICES 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|サーバー上で使用可能なデータ マイニング アルゴリズムの一覧を返します。|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|現在の接続で使用できるすべてのマイニング モデルのすべての列の一覧を返します。|  
|[DMSCHEMA_MINING_STRUCTURES 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|現在の接続で利用可能なマイニング構造を一覧表示します。|  
|[MDSCHEMA_CUBES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|現在のデータベースで定義されるキューブに関する情報を返します。|  
|[MDSCHEMA_DIMENSIONS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|現在のデータベースで定義されるディメンションに関する情報を返します。|  
|[MDSCHEMA_FUNCTIONS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)|データベースに接続されているクライアント アプリケーションで利用できる関数の一覧を返します。|  
|[MDSCHEMA_HIERARCHIES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|現在のデータベースで定義される階層に関する情報を返します。|  
|[MDSCHEMA_INPUT_DATASOURCES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)|現在のデータベースで定義されるデータ ソース オブジェクトに関する情報を返します。|  
|[MDSCHEMA_KPIS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|現在のデータベースで定義される KPI に関する情報を返します。|  
|[MDSCHEMA_LEVELS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|現在のデータベースで定義される階層内のレベルに関する情報を返します。|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)|メジャー グループのディメンションを一覧表示します。|  
|[MDSCHEMA_MEASUREGROUPS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)|現在の接続にあるメジャー グループの一覧を返します。|  
|[MDSCHEMA_MEASURES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|現在の接続にあるメジャーの一覧を返します。|  
|[MDSCHEMA_MEMBERS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|現在の接続にあるすべてのメンバーの一覧を返し、データベース、キューブ、およびディメンションごとに一覧表示します。|  
|[MDSCHEMA_PROPERTIES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|プロパティの型、データ型、その他のメタデータと共に、各プロパティの完全修飾名を返します。|  
|[MDSCHEMA_SETS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|現在の接続で定義されるセットの一覧を表示します。|  
  
## <a name="see-also"></a>参照  
 [SQL Server 2008 R2 Analysis Services 操作ガイド](http://go.microsoft.com/fwlink/?LinkID=225539&clcid=0x409)   
 [New System.Discover_Object_Activity](http://go.microsoft.com/fwlink/?linkid=221322)   
 [制限された行セットと Dmv の新しい SYSTEMRESTRICTEDSCHEMA 関数](http://go.microsoft.com/fwlink/?LinkId=231885)  
  
  
