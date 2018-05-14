---
title: MDSCHEMA_DIMENSIONS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e1e509ad466a0d173fe67a8fd1f3ac5190647eb7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="mdschemadimensions-rowset"></a>MDSCHEMA_DIMENSIONS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  データベース内の共有ディメンションとプライベート ディメンションについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_DIMENSIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|データベースの名前。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|サポートされていません。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|キューブの名前。|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|ディメンションの名前。 ディメンションが複数のキューブまたはメジャー グループの一部である場合は、ディメンション、メジャー グループ、およびキューブの一意の組み合わせごとに 1 つの行が存在します。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|ディメンションの一意の名前。|  
|**DIMENSION_GUID**|**DBTYPE_GUID 型**|サポートされていません。|  
|**DIMENSION_CAPTION**|**DBTYPE_WSTR**|ディメンションのキャプション。 ユーザー インターフェイスやレポートなどでディメンションの名前をユーザーに対して表示する場合に使用します。|  
|**DIMENSION_ORDINAL**|**DBTYPE_UI4**|キューブ内のディメンションの位置。|  
|**DIMENSION_TYPE**|**DBTYPE_I2**|ディメンションの種類。 有効な値は次のとおりです。<br /><br /> **MD_DIMTYPE_UNKNOWN** (**0**)<br /><br /> **MD_DIMTYPE_TIME** (**1**)<br /><br /> **MD_DIMTYPE_MEASURE** (**2**)<br /><br /> **MD_DIMTYPE_OTHER** (**3**)<br /><br /> **MD_DIMTYPE_QUANTITATIVE** (**5**)<br /><br /> **MD_DIMTYPE_ACCOUNTS** (**6**)<br /><br /> **MD_DIMTYPE_CUSTOMERS** (**7**)<br /><br /> **MD_DIMTYPE_PRODUCTS** (**8**)<br /><br /> **MD_DIMTYPE_SCENARIO** (**9**)<br /><br /> **MD_DIMTYPE_UTILIY** (**10**)<br /><br /> **MD_DIMTYPE_CURRENCY** (**11**)<br /><br /> **MD_DIMTYPE_RATES** (**12**)<br /><br /> **MD_DIMTYPE_CHANNEL** (**13**)<br /><br /> **MD_DIMTYPE_PROMOTION** (**14**)<br /><br /> **MD_DIMTYPE_ORGANIZATION** (**15**)<br /><br /> **MD_DIMTYPE_BILL_OF_MATERIALS** (**16**)<br /><br /> **MD_DIMTYPE_GEOGRAPHY** (**17**)|  
|**DIMENSION_CARDINALITY**|**DBTYPE_UI4**|キー属性内のメンバーの数。|  
|**DEFAULT_HIERARCHY**|**DBTYPE_WSTR**|ディメンションの階層。 これは旧バージョンとの互換性のために保持されています。|  
|**DESCRIPTION**|**DBTYPE_WSTR**|ディメンションについてのわかりやすい説明。|  
|**IS_VIRTUAL**|**DBTYPE_BOOL**|常に**FALSE**です。|  
|**IS_READWRITE**|**DBTYPE_BOOL**|ディメンションが書き込み許可されているかどうかを示すブール値。<br /><br /> **TRUE**ディメンションが書き込み可能な場合です。|  
|**DIMENSION_UNIQUE_SETTINGS**|**DBTYPE_I4**|ディメンションに一意の名前を持つメンバーのみが含まれている場合に、一意な値を含んでいる列を示すビットマップ。 このビットマップの Msmd.h では、次のビット値定数が定義されています。<br /><br /> **MDDIMENSIONS_MEMBER_KEY_UNIQUE**|  
|**DIMENSION_MASTER_UNIQUE_NAME**|**DBTYPE_WSTR**|常に**NULL**です。|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**|常に**TRUE**です。<br /><br /> メモ: ディメンションは表示されませんしない限り、ディメンション内の 1 つまたは複数の階層が表示されます。|  
  
 行セットが並べ替えられて**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**、 **DIMENSION_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_DIMENSIONS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 キューブ<br /><br /> 2 ディメンション|  
|**DIMENSION_VISIBILITY**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 表示<br /><br /> 2 not 表示|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
