---
title: 多次元モデルのキューブ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: adb21e802d437f7cd1e2d805f90c4525d6f9e8ef
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103959"
---
# <a name="cubes-in-multidimensional-models"></a>多次元モデルのキューブ
  キューブは、分析目的の情報を含む多次元構造です。キューブの主な構成要素はディメンションとメジャーです。 ディメンションでは、スライスおよびダイス化に使用するキューブの構造が定義され、メジャーによってエンド ユーザーが必要とする集計された数値が用意されます。 論理構造としてキューブを使用すると、クライアント アプリケーションでは、キューブ内のセルに含まれているかのようにメジャーの値を取得できます。セルは、考えられるすべての集約値に対して定義されます。 キューブのセルは、ディメンションのメンバーの交差領域によって定義され、その交差領域のメジャーの集計値を含みます。  
  
## <a name="benefits-of-using-cubes"></a>キューブを使用する利点  
 キューブでは、分析用のすべての関連データが格納されている単一の場所が提供されます。  
  
## <a name="components-of-cubes"></a>キューブのコンポーネント  
 キューブは次の要素から構成されます。  
  
|要素|説明|  
|-------------|-----------------|  
|ディメンション|[多次元モデル内のディメンション](dimensions-in-multidimensional-models.md)|  
|メジャーおよびメジャー グループ|[多次元モデル内のメジャーおよびメジャー グループを作成します。](create-measures-and-measure-groups-in-multidimensional-models.md)|  
|[メジャー グループ]|[多次元モデル内のパーティション](partitions-in-multidimensional-models.md)|  
|パースペクティブ|[多次元モデルのパースペクティブ](perspectives-in-multidimensional-models.md)|  
|階層|[ユーザー定義階層を作成します。](user-defined-hierarchies-create.md)|  
|アクション|[多次元モデルのアクション](actions-in-multidimensional-models.md)|  
|主要業績評価指標 (KPI)|[主要業績評価指標&#40;Kpi&#41;多次元モデル](key-performance-indicators-kpis-in-multidimensional-models.md)|  
|[新しい名前付きセット]|[多次元モデルの計算](calculations-in-multidimensional-models.md)|  
|翻訳|[多次元モデルの翻訳](translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|トピック|説明|  
|-----------|-----------------|  
|[キューブ ウィザードを使用したキューブの作成](create-a-cube-using-the-cube-wizard.md)|キューブ ウィザードを使用して、キューブ、ディメンション、ディメンション属性、ユーザー定義階層を定義する方法を説明します。|  
|[多次元モデル内のメジャーおよびメジャー グループを作成します。](create-measures-and-measure-groups-in-multidimensional-models.md)|メジャー グループを定義する方法について説明します。|  
|[多次元モデルの計算](calculations-in-multidimensional-models.md)|MDX スクリプトで計算を定義して構成する方法を説明します。|  
|[多次元モデルのアクション](actions-in-multidimensional-models.md)|アクションを定義して構成する方法を説明します。|  
|[多次元モデルのパースペクティブ](perspectives-in-multidimensional-models.md)|パースペクティブを定義して構成する方法を説明します。|  
|[ストアド プロシージャの定義](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|ストアド プロシージャを操作する方法について説明します。|  
  
  
