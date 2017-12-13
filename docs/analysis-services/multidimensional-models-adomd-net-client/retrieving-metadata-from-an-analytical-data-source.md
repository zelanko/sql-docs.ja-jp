---
title: "分析データ ソースからメタデータを取得する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- metadata [ADOMD.NET]
- retrieving metadata
ms.assetid: 00043ebd-7164-4ceb-b945-6e44378ea00a
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2c432c699cd0a924b0624d98b0e7f97323718f3c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="retrieving-metadata-from-an-analytical-data-source"></a>分析データ ソースからのメタデータの取得
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]メタデータは、分析データを取得して操作するアプリケーションに重要です。 リレーショナル データ ソースからデータを取得する場合、データセットが入れ子になっていても、それらのデータの次元を予測することができます。 通常、リレーショナル データベースから取得する結果セットは 2 次元またはスカラー構造です。 一方、分析データ ソースから取得したデータは次元がさまざまであり、多層構造になっている場合もあります。  
  
 分析データ ソースからメタデータを取得する際の複雑さに対応するため、ADOMD.NET には次の 2 つのメタデータ取得形式が用意されています。  
  
 **オブジェクト モデル**  
 ADOMD.NET オブジェクト モデルは、一般に、スキーマ行セットよりも使い方が簡単です。 ほとんどの場合、オブジェクト モデルを使用すれば、さまざまなデータベース オブジェクトのメタデータにアクセスできます。 ADOMD.NET では、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> を通してオブジェクト モデルが公開されます。  
  
 詳細については: [ADOMD.NET オブジェクト モデルの操作](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-adomd-net-object-model.md)  
  
 **スキーマ行セット**  
 少し難しくなりますが、メタデータを取得するための完全なアプローチとして、スキーマ行セットを使用する方法があります。 スキーマ行セットは、データベース内の特定の種類のすべてのオブジェクトの記述をカプセル化した、OLE DB 行セットです。 分析データ ソースのスキーマの情報には、そのデータ ソースで使用できるデータベースやカタログ、データベース内のキューブ モデルとマイニング モデル、データ ソースのキューブに割り当てられているロールなどが含まれています。 使用して、このメタデータを取得できる、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>いずれかに渡して、メソッド、 **GUID**または XML for Analysis (XMLA) の名前。  
  
 詳細については: [Working with Schema Rowsets in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)  
  
 これらのメタデータ取得方法では、それぞれ異なる種類のメタデータにアクセスします。 次の表は、それぞれの方法で使用できるメタデータと、そのメタデータにアクセスするためのメソッドを示しています。  
  
|GUID (スキーマ行セットで使用)|XMLA 名 (スキーマ行セットで使用)|ADOMD.NET オブジェクト モデル|  
|-------------------------------------|------------------------------------------|----------------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Actions>|[MDSCHEMA_ACTIONS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Catalogs>|[DBSCHEMA_CATALOGS 行セット](../../analysis-services/schema-rowsets/ole-db/dbschema-catalogs-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Columns>|[DBSCHEMA_COLUMNS 行セット](../../analysis-services/schema-rowsets/ole-db/dbschema-columns-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Connections>|**DISCOVER_CONNECTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Cubes>|[MDSCHEMA_CUBES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|AdomdConnection.Cubes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DataSources>|[DISCOVER_DATASOURCES 行セット](../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DBConnections>|**DISCOVER_DB_CONNECTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Dimensions>|[MDSCHEMA_DIMENSIONS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|AdomdConnection.Cubes[].Dimensions|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DimensionStat>|**DISCOVER_DIMENSION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Enumerators>|[DISCOVER_ENUMERATORS 行セット](../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Functions>|[MDSCHEMA_FUNCTIONS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Hierarchies>|[MDSCHEMA_HIERARCHIES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.InputDataSources>|[MDSCHEMA_INPUT_DATASOURCES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Instances>|[DISCOVER_INSTANCES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Jobs>|**DISCOVER_JOBS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Keywords>|[DISCOVER_KEYWORDS 行セット (&) #40 です。 OLE DB for OLAP &#41;](../../analysis-services/schema-rowsets/ole-db-olap/discover-keywords-rowset-ole-db-for-olap.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Kpis>|[MDSCHEMA_KPIS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|AdomdConnection.Cubes[].KPIs|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Levels>|[MDSCHEMA_LEVELS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies[].Levels|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Literals>|[DISCOVER_LITERALS 行セット](../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locations>|**DISCOVER_LOCATIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locks>|**DISCOVER_LOCKS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MasterKey>|**DISCOVER_MASTER_KEY**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroupDimensions>|[MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroups>|[MDSCHEMA_MEASUREGROUPS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Measures>|[MDSCHEMA_MEASURES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|AdomdConnection.Cubes[].Measures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemberProperties>|[MDSCHEMA_PROPERTIES 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|ほとんどの主要な ADOMD.NET オブジェクトで使用できる PropertyCollection。|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Members>|[MDSCHEMA_MEMBERS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies[].Levels[].GetMembers()|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryGrant>|**DISCOVER_MEMORYGRANT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryUsage>|**DISCOVER_MEMORYUSAGE**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningColumns>|[DMSCHEMA_MINING_COLUMNS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|AdomdConnection.MiningModels[].MiningModelColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningFunctions>|[DMSCHEMA_MINING_FUNCTIONS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContent>|[DMSCHEMA_MINING_MODEL_CONTENT 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|AdomdConnection.MiningModels[].MiningContentNodes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContentPmml>|[DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModels>|[DMSCHEMA_MINING_MODELS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|AdomdConnection.MiningModels|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelXml>|[DMSCHEMA_MINING_MODEL_XML 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServiceParameters>|[DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|AdomdConnection.MiningServices[].MiningServiceParameters|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServices>|[DMSCHEMA_MINING_SERVICES 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|AdomdConnection.MiningServices|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructureColumns>|[DMSCHEMA_MINING_STRUCTURE_COLUMNS 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|AdomdConnection.MiningStructures[].MiningStructureColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructures>|[DMSCHEMA_MINING_STRUCTURES 行セット](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|AdomdConnection.MiningStructures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionDimensionStat>|**DISCOVER_PARTITION_DIMENSION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionStat>|**DISCOVER_PARTITION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PerformanceCounters>|**DISCOVER_PERFORMANCE_COUNTERS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.ProviderTypes>|[DBSCHEMA_PROVIDER_TYPES 行セット](../../analysis-services/schema-rowsets/ole-db/dbschema-provider-types-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.SchemaRowsets>|[DISCOVER_SCHEMA_ROWSETS 行セット](../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sessions>|**DISCOVER_SESSIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sets>|[MDSCHEMA_SETS 行セット](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|AdomdConnection.Cubes[].NamedSets|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Tables>|[DBSCHEMA_TABLES 行セット](../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TablesInfo>|**DBSCHEMA_TABLES_INFO**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceColumns>|**DISCOVER_TRACE_COLUMNS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceDefinitionProviderInfo>|**DISCOVER_TRACE_DEFINITION_PROVIDERINFO**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceEventCategories>|**DISCOVER_TRACE_EVENT_CATEGORIES**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Traces>|**DISCOVER_TRACES**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Transactions>|**DISCOVER_TRANSACTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlaProperties>|[DISCOVER_PROPERTIES 行セット](../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlMetadata>|[DISCOVER_XML_METADATA 行セット](../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md)||  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [ADOMD.NET クライアント プログラミング](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Analysis Services のスキーマ行セット](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
