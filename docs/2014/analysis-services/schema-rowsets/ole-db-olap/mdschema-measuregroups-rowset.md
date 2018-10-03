---
title: MDSCHEMA_MEASUREGROUPS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_MEASUREGROUPS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f889b66a9dcc72053c04adbd5e1949f6ebbf17dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060294"
---
# <a name="mdschemameasuregroups-rowset"></a>MDSCHEMA_MEASUREGROUPS 行セット
  データベース内のメジャー グループについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_MEASUREGROUPS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||このメジャー グループが所属するカタログの名前。 プロバイダーがカタログをサポートしない場合は `NULL` です。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||このメジャー グループが所属するキューブの名前。|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||メジャー グループの名前。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||メンバーに関する、人間が読める形式の説明。|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||メジャー グループが書き込み許可されているかどうかを示すブール値。<br /><br /> メジャー グループが書き込み許可されている場合は、`true` を返します。|  
|`MEASUREGROUP_CAPTION`|`DBTYPE_WSTR`||メジャー グループの表示キャプション。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_MEASUREGROUPS`行セットは、次の表の列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  
