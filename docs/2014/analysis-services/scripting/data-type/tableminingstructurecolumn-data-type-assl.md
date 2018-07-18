---
title: TableMiningStructureColumn データ型 (ASSL) |Microsoft Docs
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
- TableMiningStructureColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableMiningStructureColumn
helpviewer_keywords:
- TableMiningStructureColumn data type
ms.assetid: 350358b0-f2fc-43c3-957d-884c59fa879e
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e03fec81f796ccf87f19df9b2e43fe29b0e318e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319402"
---
# <a name="tableminingstructurecolumn-data-type-assl"></a>TableMiningStructureColumn データ型 (ASSL)
  表す派生データ型を定義、 [MiningStructureColumn](miningstructurecolumn-data-type-assl.md)に関連付けられているスカラー値ではなく、入れ子になったテーブルを含む要素、 [ScalarMiningStructureColumn](scalarminingstructurecolumn-data-type-assl.md)要素スカラー値を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TableMiningStructureColumn>  
   <!-- The following elements extend MiningStructureColumn -->  
   <ForeignKeyColumn>..</ForeignKeyColumn>  
   <SourceMeasureGroup>..</SourceMeasureGroup>  
   <Columns>..</Columns>  
   <Translations>..</Translations>  
</TableMiningStructureColumn>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[MiningStructureColumn](miningstructurecolumn-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[列](../collections/columns-element-assl.md)、 [ForeignKeyColumn](../objects/column-element-assl.md)、 [SourceMeasureGroup](../objects/group-element-assl.md)、[翻訳](../collections/translations-element-assl.md)|  
|派生要素|[列](../objects/column-element-assl.md)([列](../collections/columns-element-assl.md)のコレクション[MiningStructure](../objects/miningstructure-element-assl.md))|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.TableMiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
