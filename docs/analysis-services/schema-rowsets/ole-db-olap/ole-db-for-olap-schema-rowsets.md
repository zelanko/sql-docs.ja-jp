---
title: "OLE DB for OLAP スキーマ行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 75bdb07bd24f44fd42cf257a1e365c101329060f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="ole-db-for-olap-schema-rowsets"></a>OLE DB for OLAP スキーマ行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーは、OLAP スキーマ行セットを次の OLE DB をサポートしています。  
  
> [!NOTE]  
>  特定のデータ ソース プロバイダーが行セットをサポートしているかどうかを確認するには、使用、 **DISCOVER_ENUMERATIONS**を含む行セット、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドです。  
  
 MSDN ライブラリで、トピック、「OLAP スキーマ行セット"を検索することでこれらの行セットに関する詳細情報を見つけることができますも[Microsoft Web サイト](http://go.microsoft.com/fwlink/?LinkId=15426)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|スキーマ行セット<sup>1</sup>|Description|  
|-------------------------------|-----------------|  
|[DISCOVER_INSTANCES 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)|サーバー上のインスタンスについて記述します。|  
|[DISCOVER_KEYWORDS 行セット (&) #40 です。 OLE DB for OLAP &#41;](../../../analysis-services/schema-rowsets/ole-db-olap/discover-keywords-rowset-ole-db-for-olap.md)|プロバイダーの予約語の一覧を列挙します。|  
|[MDSCHEMA_ACTIONS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)|クライアント アプリケーションで利用できるアクションについて記述します。|  
|[MDSCHEMA_CUBES 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|データベース内のキューブの構造について記述します。|  
|[MDSCHEMA_DIMENSIONS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|データベース内の共有ディメンションとプライベート ディメンションについて記述します。|  
|[MDSCHEMA_FUNCTIONS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)|データベースに接続されているクライアント アプリケーションに使用できる関数をについて説明します。|  
|[MDSCHEMA_HIERARCHIES 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|特定のディメンションに含まれている各階層について記述します。|  
|[MDSCHEMA_INPUT_DATASOURCES 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)|データベース内で定義されたデータ ソースについて記述します。|  
|[MDSCHEMA_KPIS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|データベース内の主要業績評価指標 (KPI) について記述します。|  
|[MDSCHEMA_LEVELS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|特定の階層内の各レベルについて記述します。|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)|メジャー グループのディメンションを列挙します。|  
|[MDSCHEMA_MEASUREGROUPS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)|データベース内のメジャー グループについて記述します。|  
|[MDSCHEMA_MEASURES 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|キューブ内の各メジャーをについて説明します。|  
|[MDSCHEMA_MEMBERS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|データベース内のメンバーについて記述します。|  
|[MDSCHEMA_PROPERTIES 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|データベース内のメンバーのプロパティについて説明します。|  
|[MDSCHEMA_SETS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|データベースで現在定義されているセットについて記述します。セッション スコープのセットも含まれます。|  
  
 <sup>1</sup>の MSOLAP データ ソース プロバイダーによっては、ここに表示されているすべてのスキーマ行セットがサポートされている、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA プロバイダー。  
  
## <a name="see-also"></a>参照  
 [DISCOVER_ENUMERATORS 行セット](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)   
 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
