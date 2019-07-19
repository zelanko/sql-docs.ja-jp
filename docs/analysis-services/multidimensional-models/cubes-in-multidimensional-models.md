---
title: 多次元モデルのキューブ |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5962889f38043e675b70558e7561bfc3f63b39ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209056"
---
# <a name="cubes-in-multidimensional-models"></a>多次元モデルのキューブ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブは、分析目的の情報を含む多次元構造です。キューブの主な構成要素はディメンションとメジャーです。 ディメンションでは、スライスおよびダイス化に使用するキューブの構造が定義され、メジャーによってエンド ユーザーが必要とする集計された数値が用意されます。 論理構造としてキューブを使用すると、クライアント アプリケーションでは、キューブ内のセルに含まれているかのようにメジャーの値を取得できます。セルは、考えられるすべての集約値に対して定義されます。 キューブのセルは、ディメンションのメンバーの交差領域によって定義され、その交差領域のメジャーの集計値を含みます。  
  
## <a name="benefits-of-using-cubes"></a>キューブを使用する利点  
 キューブでは、分析用のすべての関連データが格納されている単一の場所が提供されます。  
  
## <a name="components-of-cubes"></a>キューブのコンポーネント  
 キューブは次の要素から構成されます。  
  
|要素|説明|  
|-------------|-----------------|  
|ディメンション|[多次元モデル内のディメンション](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)|  
|メジャーおよびメジャー グループ|[多次元モデル内のメジャーおよびメジャー グループの作成](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|  
|[メジャー グループ]|[多次元モデル内のパーティション](../../analysis-services/multidimensional-models/partitions-in-multidimensional-models.md)|  
|パースペクティブ|[多次元モデルのパースペクティブ](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|  
|階層|[ユーザー定義階層の作成](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)|  
|Actions|[「多次元モデルのアクション」](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|  
|主要業績評価指標 (KPI)|[多次元モデルの主要業績評価指標 &#40;KPI&#41;](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)|  
|[新しい名前付きセット]|[多次元モデルの計算](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|  
|翻訳|[多次元モデルの翻訳 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|トピック|説明|  
|-----------|-----------------|  
|[キューブ ウィザードを使用したキューブの作成](../../analysis-services/multidimensional-models/create-a-cube-using-the-cube-wizard.md)|キューブ ウィザードを使用して、キューブ、ディメンション、ディメンション属性、ユーザー定義階層を定義する方法を説明します。|  
|[多次元モデル内のメジャーおよびメジャー グループの作成](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|メジャー グループを定義する方法について説明します。|  
|[多次元モデルの計算](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|MDX スクリプトで計算を定義して構成する方法を説明します。|  
|[「多次元モデルのアクション」](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|アクションを定義して構成する方法を説明します。|  
|[多次元モデルのパースペクティブ](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|パースペクティブを定義して構成する方法を説明します。|  
|[ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|ストアド プロシージャを操作する方法について説明します。|  
  
  
