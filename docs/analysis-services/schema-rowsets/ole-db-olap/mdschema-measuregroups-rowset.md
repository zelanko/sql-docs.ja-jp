---
title: MDSCHEMA_MEASUREGROUPS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df2bfe8aecc32c8f046d18fff4e72cd15409fdc8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029043"
---
# <a name="mdschemameasuregroups-rowset"></a>MDSCHEMA_MEASUREGROUPS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  データベース内のメジャー グループについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_MEASUREGROUPS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||このメジャー グループが所属するカタログの名前。 **NULL**プロバイダーがカタログをサポートしていない場合。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||サポートされていません。|  
|**CUBE_NAME**|**DBTYPE_WSTR**||このメジャー グループが所属するキューブの名前。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||メジャー グループの名前。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||メンバーに関する、人間が読める形式の説明。|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**||メジャー グループが書き込み許可されているかどうかを示すブール値。<br /><br /> 返します**true**メジャー グループが書き込み可能な場合です。|  
|**MEASUREGROUP_CAPTION**|**DBTYPE_WSTR**||メジャー グループの表示キャプション。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_MEASUREGROUPS**行セットは、次の表の列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
