---
title: "レッスン 5: ディメンションとメジャー グループ間のリレーションシップを定義する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 31aeb271-47a1-433b-a8a5-120bcb4584d7
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 5b3637cc09617b51663ac2bc65dea13c764981c2
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="lesson-5-defining-relationships-between-dimensions-and-measure-groups"></a>レッスン 5 : ディメンションおよびメジャー グループ間のリレーションシップの定義
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

このチュートリアルの前のレッスンでは、キューブに追加したデータベース ディメンションを、1 つ以上のキューブ ディメンションの基準として使用できることを学習しました。 このレッスンでは、キューブ ディメンションとメジャー グループの間に各種のリレーションシップを定義し、これらのリレーションシップのプロパティを指定します。  
  
詳細については、「 [ディメンション リレーションシップ](../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」を参照してください。  
  
> [!NOTE]  
> このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。 途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。 このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](http://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。  
  
このレッスンの内容は次のとおりです。  
  
[参照リレーションシップの定義](../analysis-services/lesson-5-1-defining-a-referenced-relationship.md)  
この実習では、主キーと外部キーのリレーションシップを介して直接リンクしているディメンションを使用し、ディメンションとファクト テーブルを間接的にリンクする方法を学習します。  
  
[ファクト リレーションシップの定義](../analysis-services/lesson-5-2-defining-a-fact-relationship.md)  
ここでは、ファクト テーブルのデータに基づいてディメンションを定義する方法を学習します。また、ディメンション リレーションシップをファクト リレーションシップとして定義する方法を学習します。  
  
[多対多リレーションシップを定義します。](../analysis-services/lesson-5-3-defining-a-many-to-many-relationship.md)  
ここでは、ディメンション テーブルとファクト テーブルの間に存在する多対多リレーションシップの定義を使用し、ファクトを複数のディメンション メンバーに関連付ける方法を学習します。  
  
[メジャー グループ内のディメンションの粒度を定義します。](../analysis-services/lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)  
ここでは、特定のメジャー グループに対し、ディメンションの粒度を定義する方法を学習します。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 6: 計算の定義](../analysis-services/lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a>参照  
[Analysis Services のチュートリアル シナリオ](../analysis-services/analysis-services-tutorial-scenario.md)  
[多次元モデリング &#40;です。Adventure Works チュートリアル &#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[ディメンションのリレーションシップ](../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
  
