---
title: XML for Analysis スキーマ行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- rowsets [Analysis Services], XML for Analysis
- XML for Analysis, schema rowsets
- schema rowsets [Analysis Services], XML for Analysis
- schema rowsets [XML for Analysis]
ms.assetid: 36e3ecfd-fcc3-415a-9c43-f59921d2468a
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c8125b3543e6f3c088ad8b7ae7dd5952d52df26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159273"
---
# <a name="xml-for-analysis-schema-rowsets"></a>XML for Analysis スキーマ行セット
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーには、サーバーの状態、アクティビティ、およびオブジェクトに関するメタデータを返すスキーマ行セットが含まれています。 構造と特性が変化する Analysis Services モデルに接続するクライアント アプリケーションを開発する場合は、メタデータを取得する必要があります。  
  
 スキーマ行セットは、サーバーの監視と問題のトラブルシューティングに役立つ、内部プロセスおよび操作の内部情報も提供します。 アドホック管理タスクをより適切にサポートするには、ほとんどのスキーマ行セットに対して動的管理ビュー (DMV) クエリを実行できます。 DMV クエリが返す判読可能なテーブル形式の結果は、[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] で表示できます。  
  
 次の表では、各 XMLA スキーマ行セットについて説明し、表形式のデータ モデルに固有の情報を返すかどうかを示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|行セット<sup>1</sup>|説明|  
|------------------------|-----------------|  
|[DISCOVER_CALC_DEPENDENCY 行セット](discover-calc-dependency-rowset.md)|テーブル、列、メジャー、および計算列の式の依存関係に関する情報を返します。<br /><br /> Analysis Services インスタンスに配置されたテーブル モデル、および SharePoint 環境で実行する Excel ブック内の PowerPivot モデルに適用されます。|  
|[DISCOVER_CONNECTIONS 行セット](discover-connections-rowset.md)|現在サーバー上で開いている接続について、リソースの使用状況とアクティビティに関する情報を提供します。|  
|[DISCOVER_COMMAND_OBJECTS 行セット](discover-command-objects-rowset.md)|参照先のコマンドで使用中のオブジェクトに関するリソース使用状況とアクティビティ情報を提供します。|  
|[DISCOVER_COMMANDS 行セット](discover-commands-rowset.md)|現在サーバー上で開いている接続について、実行中のコマンド、または最後に実行したコマンドのリソース使用状況とアクティビティに関する情報を提供します。|  
|[DISCOVER_CSDL_METADATA 行セット](discover-csdl-metadata-rowset.md)|テーブル モデルまたは PowerPivot モデルを利用し、レポートの一部としてソース データを提示できるクライアントにデータ ソースの XML 定義を返します。<br /><br /> Analysis Services インスタンスに配置されたテーブル モデル、および SharePoint 環境で実行する Excel ブック内の PowerPivot モデルに適用されます。|  
|[DISCOVER_DATASOURCES 行セット](discover-datasources-rowset.md)|サーバーまたは Web サービスで使用できる XMLA プロバイダー データ ソースの一覧を返します。|  
|[DISCOVER_DB_CONNECTIONS 行セット](discover-db-connections-rowset.md)|サーバーからデータベースへの現在開いている接続に関するリソース使用量と利用状況の情報を提供します。|  
|[DISCOVER_DIMENSION_STAT 行セット](discover-dimension-stat-rowset.md)|指定したディメンションで統計を返します。|  
|[DISCOVER_ENUMERATORS 行セット](discover-enumerators-rowset.md)|特定のデータ ソースの XMLA プロバイダーによってサポートされている列挙子の名前、データ型、および列挙値の一覧を返します。|  
|[DISCOVER_JOBS 行セット](discover-jobs-rowset.md)|サーバーで実行されているアクティブなジョブに関する情報を提供します。|  
|[DISCOVER_KEYWORDS 行セット&#40;XMLA&#41;](discover-keywords-rowset-xmla.md)|XMLA プロバイダーによって予約されているキーワードに関する情報を返します。|  
|[DISCOVER_LITERALS 行セット](discover-literals-rowset.md)|XMLA プロバイダーによってサポートされているデータ型や値などを含むリテラルに関する情報を返します。|  
|[DISCOVER_LOCATIONS 行セット](discover-locations-rowset.md)|バックアップ ファイルの内容に関する情報を返します。|  
|[DISCOVER_LOCKS 行セット](discover-locks-rowset.md)|サーバー上で現在保持されているロックに関する情報を提供します。|  
|[DISCOVER_MEMORYGRANT 行セット](discover-memorygrant-rowset.md)|サーバーで現在実行中のジョブによって確保されている内部メモリ クォータ付与の一覧を返します。|  
|[DISCOVER_MEMORYUSAGE 行セット](discover-memoryusage-rowset.md)|サーバーによって割り当てられているさまざまなオブジェクトのメモリ使用量の統計を返します。|  
|[DISCOVER_OBJECT_ACTIVITY 行セット](discover-object-activity-rowset.md)|サービスが開始されてからのオブジェクトごとのリソース使用量に関する情報を提供します。|  
|[DISCOVER_OBJECT_MEMORY_USAGE 行セット](discover-object-memory-usage-rowset.md)|オブジェクトによって使用されたメモリ リソースに関する情報を提供します。|  
|[DISCOVER_PARTITION_DIMENSION_STAT 行セット](discover-partition-dimension-stat-rowset.md)|パーティションに関連付けられているディメンションで統計を返します。|  
|[DISCOVER_PARTITION_STAT 行セット](discover-partition-stat-rowset.md)|特定のパーティションの集計に関する統計を返します。|  
|[DISCOVER_PERFORMANCE_COUNTERS 行セット](discover-performance-counters-rowset.md)|指定した 1 つ以上のパフォーマンス カウンターの値を返します。|  
|[DISCOVER_PROPERTIES 行セット](discover-properties-rowset.md)|指定されたデータ ソースの XMLA プロバイダーによってサポートされている標準プロパティとプロバイダー固有のプロパティに関する情報および値の一覧を返します。|  
|[DISCOVER_SCHEMA_ROWSETS 行セット](discover-schema-rowsets-rowset.md)|すべての列挙値と、XMLA プロバイダーによってサポートされている追加のプロバイダー固有の列挙値について、名前、制限、説明、その他の情報を返します。|  
|[DISCOVER_SESSIONS 行セット](discover-sessions-rowset.md)|サーバー上で現在開いているセッションに関するリソース使用量と利用状況の情報を提供します。|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS 行セット](discover-storage-table-column-segments-rowset.md)|表形式または PowerPivot のデータベースによって使用されているストレージ テーブルについての列およびセグメント レベルの情報を提供します。<br /><br /> Analysis Services インスタンスに配置されたテーブル モデル、および SharePoint 環境で実行する Excel ブック内の PowerPivot モデルに適用されます。|  
|[DISCOVER_STORAGE_TABLE_COLUMNS 行セット](discover-storage-table-columns-rowset.md)|表形式または PowerPivot のデータベースによって使用されるストレージ テーブルに対する列の割り当てを確認できます。<br /><br /> Analysis Services インスタンスに配置されたテーブル モデル、および SharePoint 環境で実行する Excel ブック内の PowerPivot モデルに適用されます。|  
|[DISCOVER_STORAGE_TABLES 行セット](discover-storage-tables-rowset.md)|モデルで使用されているテーブルに関する情報を返します。<br /><br /> Analysis Services インスタンスに配置されたテーブル モデル、および SharePoint 環境で実行する Excel ブック内の PowerPivot モデルに適用されます。|  
|[DISCOVER_TRACE_COLUMNS 行セット](discover-trace-columns-rowset.md)|トレース プロバイダーによって提供されるトレース列を記述します。|  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO 行セット](discover-trace-definition-providerinfo-rowset.md)|トレース プロバイダーの名前や説明など、トレース プロバイダーについての基本的な情報を返します。|  
|[DISCOVER_TRACE_EVENT_CATEGORIES 行セット](discover-trace-event-categories-rowset.md)|トレース プロバイダーによって提供されるイベント カテゴリを記述します。|  
|[DISCOVER_TRACES 行セット](discover-traces-rowset.md)|サーバーで実行しているトレースに関する情報を返します。|  
|[DISCOVER_TRANSACTIONS 行セット](discover-transactions-rowset.md)|現在システムで保留中のトランザクションのセットを返します。|  
|[DISCOVER_XML_METADATA 行セット](discover-xml-metadata-rowset.md)|要求されたオブジェクトについて記述する XML ドキュメントを返します。|  
  
 <sup>1</sup>の MSOLAP データ ソース プロバイダーで次のとおり、すべてのスキーマ行セットがサポートされている、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA プロバイダー。  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [動的管理ビューを使用して&#40;Dmv&#41;サービス モニターは分析するには](../../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)   
 [分析データ ソースからのメタデータの取得](../../multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
