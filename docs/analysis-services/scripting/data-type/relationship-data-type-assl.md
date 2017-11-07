---
title: "Relationship データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
ms.assetid: 73d7c48d-d8e0-4119-849d-b5f912d449e4
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: adf9322bebc1e1ed33af880fd435cddcde5293c1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="relationship-data-type-assl"></a>Relationship データ型 (ASSL)
  ディメンション内のリレーションシップを表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Relationship>  
   <ID>...</ID>  
   <Visible>...</Visible>  
   <FromRelationshipEnd>...</FromRelationshipEnd>  
   <ToRelationshipEnd>...</ToRelationshipEnd>  
</Relationship>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[ID](../../../analysis-services/scripting/properties/id-element-assl.md)、[表示](../../../analysis-services/scripting/properties/visible-element-assl.md)、 [FromRelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)、 [ToRelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)|  
|派生要素||  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Relationship>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

