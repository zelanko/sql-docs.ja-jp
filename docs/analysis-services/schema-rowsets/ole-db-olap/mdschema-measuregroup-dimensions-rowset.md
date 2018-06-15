---
title: MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 817507a53e327c6fdb16f73d3b0eb0fb5c264f24
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032923"
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  メジャー グループのディメンションを列挙します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_MEASUREGROUP_DIMENSIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||このメジャー グループが所属するカタログの名前。 **NULL**プロバイダーがカタログをサポートしていない場合。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||サポートされていません。|  
|**CUBE_NAME**|**DBTYPE_WSTR**||このメジャー グループが所属するキューブの名前。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||メジャー グループの名前。|  
|**MEASUREGROUP_CARDINALITY**|**DBTYPE_WSTR**||メジャー グループ内のメジャーが 1 つのディメンション メンバーに対して持つことができるインスタンスの数。 有効な値は次のとおりです。<br /><br /> **1 つ**<br /><br /> **多く**|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**||ディメンションの一意の名前。|  
|**DIMENSION_CARDINALITY**|**DBTYPE_WSTR**||ディメンション メンバーがメジャー グループの 1 つのメジャー インスタンスに対して持つことができるインスタンスの数。 有効な値は次のとおりです。<br /><br /> **1 つ**<br /><br /> **多く**|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**||ディメンションの階層が表示されるかどうかを示すブール値。<br /><br /> 返します**TRUE**ディメンション内の 1 つまたは複数の階層が表示されている、それ以外の場合は**FALSE**です。|  
|**DIMENSION_IS_FACT_DIMENSION**|**DBTYPE_BOOL**||ディメンションがファクト ディメンションであるかどうかを示すブール値。<br /><br /> 返します**TRUE**ディメンションはファクト ディメンションである場合は、それ以外の場合、 **FALSE**です。|  
|**DIMENSION_PATH**|**DBTYPE_HCHAPTER**||参照ディメンションのディメンションの一覧。|  
|**DIMENSION_GRANULARITY**|**DBTYPE_WSTR**||粒度階層の一意の名前。|  
  
 行セットでの並べ替えをサポートしている**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**、 **MEASUREGROUP_NAME**、 **DIMENSION_UNIQUE_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_MEASUREGROUP_DIMENSIONS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DIMENSION_VISIBILITY**|**DBTYPE_UI2**|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> 1 表示<br /><br /> 2 not 表示<br /><br /> 既定の制限の値は 1 です。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
