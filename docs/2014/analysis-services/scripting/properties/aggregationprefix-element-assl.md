---
title: AggregationPrefix 要素 (ASSL) |Microsoft ドキュメント
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
- AggregationPrefix Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationPrefix
helpviewer_keywords:
- AggregationPrefix element
ms.assetid: 1581e0df-ae8e-41ce-9c92-f0f7cac487f2
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 84f7b086e1cdc2516f0912a4580d0b3eb45132ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178316"
---
# <a name="aggregationprefix-element-assl"></a>AggregationPrefix 要素 (ASSL)
  関連する親要素全体にわたって集計名に使用する共通のプレフィックスを定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cube> <!-- or Database, MeasureGroup, Partition -->  
   ...  
   <AggregationPrefix>...</AggregationPrefix>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../objects/cube-element-assl.md)、[データベース](../objects/database-element-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)、[パーティション](../objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 集計プレフィックス集計名が生成[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、し、またリレーショナル OLAP (ROLAP) パーティションに格納された集計用のリレーショナル データベースでテーブル名を生成します。  
  
 完全に展開された集計名は、次の部分で構成されています。  
  
 *\<DatabasePrefix >\<CubePrefix >\<MeasureGroupPrefix >\<PartitionPrefix >\<AggregationID >*  
  
 集計名の最初の 4 つの部分が集計プレフィックスを構成しています。 最初の 4 つの部分はユーザーが指定します。  
  
-   *DatabasePrefix*の値を表す、`AggregationPrefix`要素に関連付けられた、`Database`要素。  
  
-   *CubePrefix*の値を表す、`AggregationPrefix`要素に関連付けられた、`Cube`要素。  
  
-   *MeasureGroupPrefix*の値を表す、`AggregationPrefix`要素に関連付けられた、`MeasureGroup`要素。  
  
-   *PartitionPrefix*の値を表す、`AggregationPrefix`要素に関連付けられた、`Partition`要素。  
  
 名前の 5 番目の部分*AggregationID*、システム定義の ID では、されユーザーがない、名前のこの部分を制御します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `AggregationPrefix` の親に対応する要素は、<xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.Database>、<xref:Microsoft.AnalysisServices.MeasureGroup>、および <xref:Microsoft.AnalysisServices.Partition> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  