---
title: "ForeignKeyColumn 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- ForeignKeyColumn Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ForeignKeyColumn
helpviewer_keywords:
- ForeignKeyColumn element
ms.assetid: 6c00dcc6-8d5b-4293-8b72-c7a22e298c8d
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cc3000d1bdab66434e4cc8134567da46f87f0544
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
|データ型と長さ|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ForeignKeyColumns](../../../analysis-services/scripting/collections/foreignkeycolumns-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 詳細については、 **DataItem**の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、 **DataItem**を入力しを参照してください[DataItem データ型と #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 親に対応する要素、 **ForeignKeyColumns**分析管理オブジェクト (AMO) オブジェクト モデルのコレクションが<xref:Microsoft.AnalysisServices.TableMiningStructureColumn>です。  
  
## <a name="see-also"></a>参照  
 [TableMiningStructureColumn データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)   
 [MiningStructureColumn データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)   
 [MiningStructure 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

