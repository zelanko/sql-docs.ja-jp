---
title: "DisplayFlag 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DisplayFlag Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DisplayFlag
helpviewer_keywords: DisplayFlag element
ms.assetid: a6750477-0763-46da-9add-1f4448146a6b
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f4b9875aaf9c7554c9d65f8fdc83ba02a5a3ed98
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="displayflag-element-assl"></a>DisplayFlag 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]ユーザー インターフェイス コンポーネントを関連付けられているに表示するかどうかを示す読み取り専用のヒントを含む[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ServerProperty>  
   ...  
   <DisplayFlag>...</DisplayFlag>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**DisplayFlag**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ServerProperty>します。  
  
## <a name="see-also"></a>参照  
 [ServerProperties 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)   
 [Server 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
