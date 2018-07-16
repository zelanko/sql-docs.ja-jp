---
title: ValueColumn 要素 (ASSL) |Microsoft Docs
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
- ValueColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ValueColumn element
ms.assetid: 6c2d6822-8ecc-46df-9fa9-bb92ac716c36
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7279cb1f8f9bc5a7dc8c9e564081a227edc32f4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231902"
---
# <a name="valuecolumn-element-assl"></a>ValueColumn 要素 (ASSL)
  親要素の値を指定する列を識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <ValueColumn xsi:type="DataItem">...</ValueColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|既定値|変動 (「コメント」を参照)。|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 場合、 [NameColumn](namecolumn-element-assl.md)要素の`DimensionAttribute`が指定されている同じ`DataItem`値の既定値として使用する、`ValueColumn`要素。 場合、`NameColumn`要素の`DimensionAttribute`が指定されていないと、 [KeyColumns](../collections/keycolumns-element-assl.md)のコレクション`DimensionAttribute`が 1 つには含まれています[KeyColumn](keycolumn-element-assl.md)キー列、文字列を表す要素データ型は、同じ`DataItem`値の既定値として使用する、`ValueColumn`要素。  
  
 詳細については、`DataItem`の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、`DataItem`入力を参照してください[DataItem データ型&#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md)します。  
  
 親に対応する要素`NameColumn`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.DimensionAttribute>と<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
