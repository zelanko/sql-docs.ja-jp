---
title: OLE DB for OLAP スキーマ行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd2e29e03617ccc3929ca0845e2b703e406cbfb2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172972"
---
# <a name="ole-db-for-olap-schema-rowsets"></a>OLE DB for OLAP スキーマ行セット
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーでは、次の OLE DB for OLAP スキーマ行セットがサポートされています。  
  
> [!NOTE]  
>  特定のデータ ソース プロバイダーが行セットをサポートしているかどうかを確認するには、使用、`DISCOVER_ENUMERATIONS`を含む行セット、 [Discover](../../xmla/xml-elements-methods-discover.md)メソッド。  
  
 MSDN ライブラリで「OLAP スキーマ行セット」のトピックでは、検索することによりこれらの行セットに関する詳細情報を検索することもできます[Microsoft Web サイト](http://go.microsoft.com/fwlink/?LinkId=15426)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|スキーマ行セット<sup>1</sup>|説明|  
|-------------------------------|-----------------|  
|[DISCOVER_INSTANCES 行セット](discover-instances-rowset.md)|サーバー上のインスタンスについて記述します。|  
|[DISCOVER_KEYWORDS 行セット&#40;OLE DB for OLAP&#41;](discover-keywords-rowset-ole-db-for-olap.md)|プロバイダーの予約語の一覧を列挙します。|  
|[MDSCHEMA_ACTIONS 行セット](mdschema-actions-rowset.md)|クライアント アプリケーションで利用できるアクションについて記述します。|  
|[MDSCHEMA_CUBES 行セット](mdschema-cubes-rowset.md)|データベース内のキューブの構造について記述します。|  
|[MDSCHEMA_DIMENSIONS 行セット](mdschema-dimensions-rowset.md)|データベース内の共有ディメンションとプライベート ディメンションについて記述します。|  
|[MDSCHEMA_FUNCTIONS 行セット](mdschema-functions-rowset.md)|データベースに接続されているクライアント アプリケーションに使用できる関数をについて説明します。|  
|[MDSCHEMA_HIERARCHIES 行セット](mdschema-hierarchies-rowset.md)|特定のディメンションに含まれている各階層について記述します。|  
|[MDSCHEMA_INPUT_DATASOURCES 行セット](mdschema-input-datasources-rowset.md)|データベース内で定義されたデータ ソースについて記述します。|  
|[MDSCHEMA_KPIS 行セット](mdschema-kpis-rowset.md)|データベース内の主要業績評価指標 (KPI) について記述します。|  
|[MDSCHEMA_LEVELS 行セット](mdschema-levels-rowset.md)|特定の階層内の各レベルについて記述します。|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット](mdschema-measuregroup-dimensions-rowset.md)|メジャー グループのディメンションを列挙します。|  
|[MDSCHEMA_MEASUREGROUPS 行セット](mdschema-measuregroups-rowset.md)|データベース内のメジャー グループについて記述します。|  
|[MDSCHEMA_MEASURES 行セット](mdschema-measures-rowset.md)|キューブ内の各メジャーをについて説明します。|  
|[MDSCHEMA_MEMBERS 行セット](mdschema-members-rowset.md)|データベース内のメンバーについて記述します。|  
|[MDSCHEMA_PROPERTIES 行セット](mdschema-properties-rowset.md)|データベース内のメンバーのプロパティについて説明します。|  
|[MDSCHEMA_SETS 行セット](mdschema-sets-rowset.md)|データベースで現在定義されているセットについて記述します。セッション スコープのセットも含まれます。|  
  
 <sup>1</sup>の MSOLAP データ ソース プロバイダーで次のとおり、すべてのスキーマ行セットがサポートされている、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA プロバイダー。  
  
## <a name="see-also"></a>参照  
 [DISCOVER_ENUMERATORS 行セット](../xml/discover-enumerators-rowset.md)   
 [Analysis Services のスキーマ行セット](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
