---
title: SkippedLevelsColumn 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 64f50b81486e1d9b14e395fdec4f86bec32645cc
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="skippedlevelscolumn-element-assl"></a>SkippedLevelsColumn 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
    
> [!NOTE]  
>  この機能は、このバージョンの Microsoft SQL Server では除外されています。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
 各メンバーとその親の間でスキップされた (空の) レベルの数を格納する列の詳細を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <SkippedLevelsColumn xsi:type="DataItem">...</SkippedLevelsColumn>  
   ...  
</DimensionAttribute>  
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
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **SkippedLevelsColumn**要素は親属性にのみ適用されます (つまり、他の値、[使用状況](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)の要素、 **DimensionAttribute**親の設定*親*)。 **SkippedLevelsColumn**要素には、列または各メンバーとその親メンバーの間でスキップされたレベルの数を格納する親属性の属性が含まれています。 これにより、親属性に基づく親子階層ではメンバー間でレベルをスキップできます。 この列または属性の値は、負でない整数である必要があります。値が負の場合、処理エラーが発生します。 場合、 **SkippedLevelsColumn**要素が指定されていない値が含まれていない、現在のメンバーでは、親メンバーより 1 レベルの深さ。  
  
 詳細については、 **DataItem**の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、 **DataItem**表を参照してください[DataItem データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)です。  
  
 親に対応する要素**SkippedLevelsColumn**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [要素の属性&#40;ASSL&#41;](../../../analysis-services/scripting/collections/attributes-element-assl.md)   
 [Dimension 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
