---
title: "Persistence 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Persistence Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Persistence
helpviewer_keywords:
- Persistence element
ms.assetid: dafe3df2-4795-48ea-bebe-33c1a3bf18b6
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fd24f62070693d74949bd9ff328c87f66567929f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="persistence-element-assl"></a>Persistence 要素 (ASSL)
  調べ、バインドされているソース データのどの部分は動的で指定された頻度を使用して更新プログラムの確認は、 [RefreshPolicy](../../../analysis-services/scripting/properties/refreshpolicy-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Persistence>...</Persistence>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*NotPersisted*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)、 [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*NotPersisted*|基になるメタデータ、メンバー、データがすべて動的です。|  
|*メタデータ*|基になるメタデータは静的ですが、メンバーとデータは動的です。|  
|*すべて*|基になるメタデータ、メンバー、データはすべて静的です。|  
  
 許可される値に対応する列挙**永続化**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.PersistenceType>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

