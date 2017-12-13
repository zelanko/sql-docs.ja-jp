---
title: "多次元モデルのキューブ |Microsoft ドキュメント"
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
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 2bec0055791056d71879f9d2d4be2dbda26c5b7b
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="cubes-in-multidimensional-models"></a>多次元モデルのキューブ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]キューブは、分析の目的で情報を含む多次元構造体キューブの主な構成要素とは、ディメンションとメジャーです。 ディメンションでは、スライスおよびダイス化に使用するキューブの構造が定義され、メジャーによってエンド ユーザーが必要とする集計された数値が用意されます。 論理構造としてキューブを使用すると、クライアント アプリケーションでは、キューブ内のセルに含まれているかのようにメジャーの値を取得できます。セルは、考えられるすべての集約値に対して定義されます。 キューブのセルは、ディメンションのメンバーの交差領域によって定義され、その交差領域のメジャーの集計値を含みます。  
  
## <a name="benefits-of-using-cubes"></a>キューブを使用する利点  
 キューブでは、分析用のすべての関連データが格納されている単一の場所が提供されます。  
  
## <a name="components-of-cubes"></a>キューブのコンポーネント  
 キューブは次の要素から構成されます。  
  
|要素|Description|  
|-------------|-----------------|  
|ディメンション|[多次元モデル内のディメンション](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)|  
|メジャーおよびメジャー グループ|[多次元モデル内のメジャーおよびメジャー グループの作成](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|  
|パーティション|[多次元モデル内のパーティション](../../analysis-services/multidimensional-models/partitions-in-multidimensional-models.md)|  
|パースペクティブ|[多次元モデルのパースペクティブ](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|  
|階層|[ユーザー定義階層の作成](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)|  
|アクション|[多次元モデルのアクション](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|  
|主要業績評価指標 (KPI)|[多次元モデルの主要業績評価指標 &#40;KPI&#41;](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)|  
|計算|[多次元モデルの計算](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|  
|翻訳|[多次元モデルの翻訳 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>関連タスク  
  
|トピック|Description|  
|-----------|-----------------|  
|[キューブ ウィザードを使用したキューブの作成](../../analysis-services/multidimensional-models/create-a-cube-using-the-cube-wizard.md)|キューブ ウィザードを使用して、キューブ、ディメンション、ディメンション属性、ユーザー定義階層を定義する方法を説明します。|  
|[多次元モデル内のメジャーおよびメジャー グループの作成](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|メジャー グループを定義する方法について説明します。|  
|[多次元モデルの計算](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|MDX スクリプトで計算を定義して構成する方法を説明します。|  
|[多次元モデルのアクション](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|アクションを定義して構成する方法を説明します。|  
|[多次元モデルのパースペクティブ](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|パースペクティブを定義して構成する方法を説明します。|  
|[ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|ストアド プロシージャを操作する方法について説明します。|  
  
  
