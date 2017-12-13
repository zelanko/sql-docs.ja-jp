---
title: "MDSCHEMA_INPUT_DATASOURCES 行セット |Microsoft ドキュメント"
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
apiname: MDSCHEMA_INPUT_DATASOURCES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 64055e6a00de0229971812cf0979b838e15b8d03
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="mdschemainputdatasources-rowset"></a>MDSCHEMA_INPUT_DATASOURCES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]データベース内で定義されているデータ ソースをについて説明します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_INPUT_DATASOURCES**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||このデータ ソースが所属するカタログの名前。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||サポートされていません。|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**||データ ソース オブジェクトの名前。|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**||データ ソースの種類。 有効な値は次のとおりです。<br /><br /> **リレーショナル**<br /><br /> **Olap**|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**||データ ソースの作成日。|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**||データ ソースの最終変更日時。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||アクションについてのわかりやすい説明。|  
|**タイムアウト**|**DBTYPE_UI4**||データ ソースのタイムアウト。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_INPUT_DATASOURCES**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
