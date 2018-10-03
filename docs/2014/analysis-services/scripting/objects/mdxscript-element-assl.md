---
title: MdxScript 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MdxScript Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MdxScript
helpviewer_keywords:
- MdxScript element
ms.assetid: 0c59a550-dc95-4d50-948a-bb99348bdd86
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1e138b4112a96bc6cdd5e08af0dbd0941a422d8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106532"
---
# <a name="mdxscript-element-assl"></a>MdxScript 要素 (ASSL)
  関連付けられている多次元式 (MDX) スクリプトに関する情報を格納する[キューブ](cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MdxScripts>  
   <MdxScript>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Annotations>...</Annotations>  
      <Commands>...</Commands>  
      <DefaultScript>...</DefaultScript>  
      <CalculationProperties>...</CalculationProperties>  
   </MdxScript>  
</MdxScripts>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MdxScripts](../collections/mdxscripts-element-assl.md)|  
|子要素|[注釈](../collections/annotations-element-assl.md)、 [CalculationProperties](../collections/calculationproperties-element-assl.md)、[コマンド](../collections/commands-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、 [DefaultScript](../properties/defaultscript-element-assl.md)、 [説明](../properties/description-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、[名](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 スクリプトの `DefaultScript` 要素は、既定により `True` に設定されます。 特定のスクリプトで `DefaultScript` を `True` に設定すると、他のすべてのスクリプトで `DefaultScript` が `False` に設定されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MdxScript>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
