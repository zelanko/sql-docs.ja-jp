---
title: SkippedLevelsColumn 要素 (ASSL) |Microsoft Docs
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
- SkippedLevelsColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SkippedLevelsColumn
helpviewer_keywords:
- SkippedLevelsColumn element
ms.assetid: 6b00a288-99c1-4735-9e6b-cd13ed4fa346
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c04dea8c63d71483de9a8194a15bc4e4d7be5b88
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196032"
---
# <a name="skippedlevelscolumn-element-assl"></a>SkippedLevelsColumn 要素 (ASSL)
    
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
|データ型と長さ|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `SkippedLevelsColumn`要素は親属性にのみ適用されます (つまり、他の値、[使用状況](../properties/usage-element-dimensionattribute-assl.md)の要素、`DimensionAttribute`に親が設定されている*親*)。 `SkippedLevelsColumn` 要素には、各メンバーとその親メンバーの間でスキップされたレベルの数を格納する親属性の列または属性があります。 これにより、親属性に基づく親子階層ではメンバー間でレベルをスキップできます。 この列または属性の値は、負でない整数である必要があります。値が負の場合、処理エラーが発生します。 `SkippedLevelsColumn` 要素が指定されていない場合や、要素に値が含まれていない場合、現在のメンバーにはその親メンバーより 1 つ下のレベルがあります。  
  
 詳細については、`DataItem`の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、`DataItem`テーブルを参照してください[DataItem データ型&#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md)します。  
  
 親に対応する要素`SkippedLevelsColumn`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [Attributes 要素&#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [ディメンション要素&#40;ASSL&#41;](dimension-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
