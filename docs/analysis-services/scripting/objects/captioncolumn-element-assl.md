---
title: "CaptionColumn 要素 (ASSL) |Microsoft ドキュメント"
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
apiname:
- CaptionColumn Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CaptionColumn
helpviewer_keywords:
- CaptionColumn element
ms.assetid: bdb1b9b8-b5d5-4d91-81c7-8de8635bbb83
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f7e270368ae02f5e5b14564df2a0b3bd089bb085
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="captioncolumn-element-assl"></a>CaptionColumn 要素 (ASSL)
  属性のキャプションを指定する列を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeTranslation>  
   ...  
   <CaptionColumn xsi:type="DataItem">...</CaptionColumn>  
   ...  
</AttributeTranslation>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 詳細については、 **DataItem**の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、 **DataItem**を入力しを参照してください[DataItem データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 親に対応する要素**CaptionColumn**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AttributeTranslation>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
