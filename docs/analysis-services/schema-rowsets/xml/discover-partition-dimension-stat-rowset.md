---
title: "DISCOVER_PARTITION_DIMENSION_STAT 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: bf4626b3-4d6b-4795-bb01-df335fb9c09a
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 42bbe583c494830308c021c1adc385ec48491007
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discoverpartitiondimensionstat-rowset"></a>DISCOVER_PARTITION_DIMENSION_STAT 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]パーティションに関連付けられているディメンションで統計を返します  
  
 **適用されます:**表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_PARTITION_DIMENSION_STAT**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Required|データベースの名前。<br /><br /> この列は制限リストに必要です。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Required|キューブまたはテーブル モデルの名前。<br /><br /> この列は制限リストに必要です。|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Required|メジャー グループの名前。<br /><br /> この列は制限リストに必要です。|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|Required|パーティションの名前。<br /><br /> この列は制限リストに必要です。|  
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
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
