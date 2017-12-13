---
title: "AggregationPrefix 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AggregationPrefix Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AggregationPrefix
helpviewer_keywords: AggregationPrefix element
ms.assetid: 1581e0df-ae8e-41ce-9c92-f0f7cac487f2
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3a5681f6defdd1c18702d0e00300c9c6309825a2
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="aggregationprefix-element-assl"></a>AggregationPrefix 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]関連付けられている親要素全体にわたって集計名に使用する共通のプレフィックスを定義します。  
  
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
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
