---
title: CaptionColumn 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CaptionColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CaptionColumn
helpviewer_keywords:
- CaptionColumn element
ms.assetid: bdb1b9b8-b5d5-4d91-81c7-8de8635bbb83
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c60ac92841ce35e7b4c00c80da4be4eeed6bd96
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273348"
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
|データ型と長さ|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeTranslation](../data-type/translation-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 詳細については、`DataItem`の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、`DataItem`入力を参照してください[DataItem データ型&#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md)します。  
  
 親に対応する要素`CaptionColumn`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AttributeTranslation>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
