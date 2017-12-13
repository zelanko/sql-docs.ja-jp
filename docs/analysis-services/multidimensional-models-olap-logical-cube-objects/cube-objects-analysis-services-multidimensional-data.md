---
title: "キューブ オブジェクト (Analysis Services - 多次元データ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords: cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e44d2108dece395dcc32c1fcc7626e0e738d883f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Cube オブジェクト (Analysis Services - 多次元データ)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
    
## <a name="introducing-cube-objects"></a>Cube オブジェクトの導入  
 簡単な <xref:Microsoft.AnalysisServices.Cube> オブジェクトは、基本情報、ディメンション、およびメジャー グループで構成されます。 基本情報には、キューブの名前、キューブの既定のメジャー、データ ソース、ストレージ モードなどが含まれます。  
  
 Dimensions コレクションには、データベースのディメンション コレクションのキューブで使用される、実際のディメンションのセットが含まれています。 すべてのディメンションは、キューブ内で参照される前に、データベースのディメンション コレクション内で定義されている必要があります。 プライベート ディメンションでは使用できない[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。  
  
 メジャー グループは、キューブ内のメジャーのセットです。 メジャー グループは、共通のデータ ソース ビューと共通のディメンション セットを持つ、メジャーのコレクションです。 メジャー グループは、メジャーの処理単位です。メジャー グループは個別に処理されてから参照できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|||  
|-|-|  
|トピック||  
|[アクション &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[集計と集計デザイン](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)||  
|[計算](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)||  
|[キューブ セル &#40;です。Analysis Services - 多次元データ &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-cells-analysis-services-multidimensional-data.md)||  
|[キューブ プロパティ - 多次元モデルのプログラミング](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-properties-multidimensional-model-programming.md)||  
|[キューブのストレージと #40 です。Analysis Services - 多次元データ &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)||  
|[キューブの翻訳](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)||  
|[ディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)||  
|[多次元モデルの主要業績評価指標 &#40;KPI&#41;](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[メジャーおよびメジャー グループ](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)||  
|[パーティション (Analysis Services - 多次元データ)](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)||  
|[パースペクティブ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)||  
  
  
