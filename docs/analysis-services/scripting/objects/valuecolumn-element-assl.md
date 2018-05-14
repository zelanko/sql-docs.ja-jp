---
title: ValueColumn 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2e9f7b8ed3b1c2a73c4d37d0f9b166ab49cbb91d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="valuecolumn-element-assl"></a>ValueColumn 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|データ型と長さ|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|既定値|変動 (「コメント」を参照)。|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 場合、 [NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)要素の**DimensionAttribute**が指定されている同じ**DataItem**値の既定値として使用されます、 **ValueColumn**要素。 場合、 **NameColumn**要素の**DimensionAttribute**が指定されていないと、 [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)のコレクション**DimensionAttribute**1 つを含む[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)要素のキー列と同じ文字列データ型を表す**DataItem**値の既定値として使用されます、 **ValueColumn**要素。  
  
 詳細については、 **DataItem**の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、 **DataItem**を入力しを参照してください[DataItem データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 親に対応する要素**NameColumn**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.DimensionAttribute>と<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>です。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
