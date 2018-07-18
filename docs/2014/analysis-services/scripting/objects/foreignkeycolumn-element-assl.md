---
title: ForeignKeyColumn 要素 (ASSL) |Microsoft Docs
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
- ForeignKeyColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ForeignKeyColumn
helpviewer_keywords:
- ForeignKeyColumn element
ms.assetid: 6c00dcc6-8d5b-4293-8b72-c7a22e298c8d
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 824589905f1acf1834e971b8a049005ef1465c26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207882"
---
# <a name="foreignkeycolumn-element-assl"></a>ForeignKeyColumn 要素 (ASSL)
  リレーショナル データ ソースの親テーブルへの結合を識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ForeignKeyColumns>  
   <ForeignKeyColumn xsi:type="DataItem">...</ForeignKeyColumn>  
</ForeignKeyColumns>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ForeignKeyColumns](../collections/columns-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 詳細については、`DataItem`の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、`DataItem`入力を参照してください[DataItem データ型&#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `ForeignKeyColumns` コレクションの親に対応する要素は、<xref:Microsoft.AnalysisServices.TableMiningStructureColumn> です。  
  
## <a name="see-also"></a>参照  
 [TableMiningStructureColumn データ型&#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [MiningStructureColumn データ型&#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [MiningStructure 要素&#40;ASSL&#41;](miningstructure-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
