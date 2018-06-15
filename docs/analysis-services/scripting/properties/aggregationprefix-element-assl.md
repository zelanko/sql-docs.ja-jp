---
title: AggregationPrefix 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b23721728f8e196c47ab326024a6f514631c3b6f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031495"
---
# <a name="aggregationprefix-element-assl"></a>AggregationPrefix 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 集計プレフィックス集計名が生成[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、し、またリレーショナル OLAP (ROLAP) パーティションに格納された集計用のリレーショナル データベースでテーブル名を生成します。  
  
 完全に展開された集計名は、次の部分で構成されています。  
  
 *\<DatabasePrefix >\<CubePrefix >\<MeasureGroupPrefix >\<PartitionPrefix >\<AggregationID >*  
  
 集計名の最初の 4 つの部分が集計プレフィックスを構成しています。 最初の 4 つの部分はユーザーが指定します。  
  
-   *DatabasePrefix*の値を表す、 **AggregationPrefix**要素に関連付けられた、**データベース**要素。  
  
-   *CubePrefix*の値を表す、 **AggregationPrefix**要素に関連付けられた、**キューブ**要素。  
  
-   *MeasureGroupPrefix*の値を表す、 **AggregationPrefix**要素に関連付けられた、 **MeasureGroup**要素。  
  
-   *PartitionPrefix*の値を表す、 **AggregationPrefix**要素に関連付けられた、**パーティション**要素。  
  
 名前の 5 番目の部分*AggregationID*、システム定義の ID では、されユーザーがない、名前のこの部分を制御します。  
  
 親に対応する要素**AggregationPrefix**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Cube>、 <xref:Microsoft.AnalysisServices.Database>、 <xref:Microsoft.AnalysisServices.MeasureGroup>、および<xref:Microsoft.AnalysisServices.Partition>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
