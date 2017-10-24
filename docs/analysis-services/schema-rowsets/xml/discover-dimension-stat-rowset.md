---
title: "DISCOVER_DIMENSION_STAT 行セット |Microsoft ドキュメント"
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
applies_to:
- SQL Server 2016 Preview
ms.assetid: 639f8cd7-3b43-40d5-8b84-552daf60d484
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8646303bf73732a1a9f62c94879840e9e9866865
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="discoverdimensionstat-rowset"></a>DISCOVER_DIMENSION_STAT 行セット
  ディメンションに関する情報を提供します。これには、ディメンションを含むデータベースの名前、ディメンション名、その属性、および各属性のメンバーの数が含まれます。 テーブル モデルでは、これはテーブルの列および各列の値の数に相当します。  
  
 **適用されます:**表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_DIMENSION_STAT**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|必須|ディメンションを含むデータベースの名前。<br /><br /> この列は制限リストに必要です。|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|必須|ディメンションの名前。<br /><br /> この列は制限リストに必要です。|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||ディメンションの属性の名前。|  
|**ATTRIBUTE_COUNT**|**DBTYPE_I8**||指定された属性の値の数。 テーブル モデルでは、値は常にテーブル内の行数と同じです。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd90-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

