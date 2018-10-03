---
title: MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_MEASUREGROUP_DIMENSIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUP_DIMENSIONS rowset
ms.assetid: c731c06a-7382-4e50-ba0e-d8cee3ab4f28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: be9e28aefd3170f8db73f21ae5f3f021be61c34c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062677"
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット
  メジャー グループのディメンションを列挙します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_MEASUREGROUP_DIMENSIONS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||このメジャー グループが所属するカタログの名前。 プロバイダーがカタログをサポートしない場合は `NULL` です。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||このメジャー グループが所属するキューブの名前。|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||メジャー グループの名前。|  
|`MEASUREGROUP_CARDINALITY`|`DBTYPE_WSTR`||メジャー グループ内のメジャーが 1 つのディメンション メンバーに対して持つことができるインスタンスの数。 有効な値は次のとおりです。<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||ディメンションの一意の名前。|  
|`DIMENSION_CARDINALITY`|`DBTYPE_WSTR`||ディメンション メンバーがメジャー グループの 1 つのメジャー インスタンスに対して持つことができるインスタンスの数。<br /><br /> 有効な値は次のとおりです。<br /><br /> -   `ONE`<br />-   `MANY`|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||ディメンションの階層が表示されるかどうかを示すブール値。<br /><br /> ディメンションの階層が 1 つ以上表示される場合は `TRUE` を返し、それ以外の場合は `FALSE` を返します。|  
|`DIMENSION_IS_FACT_DIMENSION`|`DBTYPE_BOOL`||ディメンションがファクト ディメンションであるかどうかを示すブール値。<br /><br /> ディメンションがファクト ディメンションである場合は `TRUE` を返し、それ以外の場合は `FALSE` を返します。|  
|`DIMENSION_PATH`|`DBTYPE_HCHAPTER`||参照ディメンションのディメンションの一覧。|  
|`DIMENSION_GRANULARITY`|`DBTYPE_WSTR`||粒度階層の一意の名前。|  
  
 行セットは、`CATALOG_NAME`、`SCHEMA_NAME`、`CUBE_NAME`、`MEASUREGROUP_NAME`、`DIMENSION_UNIQUE_NAME` を基準にした並べ替えをサポートしています。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_MEASUREGROUP_DIMENSIONS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|任意。|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`DIMENSION_VISIBILITY`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 の表示<br />-2 の非表示<br />-既定の制限は、1 の値です。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  
