---
title: "MDSCHEMA_MEASUREGROUPS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDSCHEMA_MEASUREGROUPS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d39a7ce85ec5c4781d69d5a0bcd2fb468dd701bc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemameasuregroups-rowset"></a>MDSCHEMA_MEASUREGROUPS 行セット
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
  
  

