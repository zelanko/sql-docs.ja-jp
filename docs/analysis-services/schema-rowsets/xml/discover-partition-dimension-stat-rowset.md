---
title: DISCOVER_PARTITION_DIMENSION_STAT Rowset | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe43b694b8fdeb4128ae1ad2aa9dc137d2bc9d42
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="discoverpartitiondimensionstat-rowset"></a>DISCOVER_PARTITION_DIMENSION_STAT 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  パーティションに関連付けられているディメンションについての統計を返します。  
  
 **適用されます:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_PARTITION_DIMENSION_STAT**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|必須|データベースの名前。<br /><br /> この列は制限リストに必要です。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|必須|キューブまたはテーブル モデルの名前。<br /><br /> この列は制限リストに必要です。|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|必須|メジャー グループの名前。<br /><br /> この列は制限リストに必要です。|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|必須|パーティションの名前。<br /><br /> この列は制限リストに必要です。|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||ディメンションの名前。<br /><br /> この列は制限リストに必要です。|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||ディメンションの属性の名前。|  
|**ATTRIBUTE_INDEXED**|**DBTYPE_BOOL**||true の場合、属性にインデックスが設定されていることを示します。それ以外の場合は false です。|  
|**ATTRIBUTE_COUNT_MIN**|**DBTYPE_I8**||属性の最小数。|  
|**ATTRIBUTE_COUNT_MAX**|**DBTYPE_I8**||属性の最大数。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd8e-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
