---
title: "Usage 要素 (MiningModelColumn) (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
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
- Usage Element (MiningModelColumn)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: 435a857e-37a9-434e-9de1-354f1ff2993f
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eb454a49ae0035cedca3a8ef322f5f9d13c7625e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="usage-element-miningmodelcolumn-assl"></a>Usage 要素 (MiningModelColumn) (ASSL)
  について説明する方法の親に関連付けられた列[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)を使用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <Usage>...</Usage>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*[キー]*|列はキー列です。|  
|*入力*|列は入力列です。|  
|*Predict*|列は予測列です。|  
|*PredictOnly*|列は予測列のみです。|  
|*なし*|列はモデルによって使用されません。<br /><br /> **\*\*警告\* \*** 使用状況の値が「なし」の場合は、Analysis Services 送信しません任意の値をサーバーに既定以外の場合はそのため、使用法 属性は、要求/応答に含まれていません。|  
  
 許可される値に対応する列挙**使用状況**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningModelColumnUsages>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

