---
title: MDSCHEMA_INPUT_DATASOURCES 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 329f3081e3e16b3603c5ddd299ccafc0a98f6a9a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028303"
---
# <a name="mdschemainputdatasources-rowset"></a>MDSCHEMA_INPUT_DATASOURCES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  データベース内で定義されたデータ ソースについて記述します。  
  
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
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
