---
title: 'レッスン 5: ディメンションとメジャー グループ間のリレーションシップを定義する |Microsoft Docs'
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a78e3eed7baebee02e0fb7da97f25d9fdbb400b5
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403764"
---
# <a name="lesson-5-defining-relationships-between-dimensions-and-measure-groups"></a>レッスン 5: ディメンションおよびメジャー グループ間のリレーションシップの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

このチュートリアルの前のレッスンでは、キューブに追加したデータベース ディメンションを、1 つ以上のキューブ ディメンションの基準として使用できることを学習しました。 このレッスンでは、キューブ ディメンションとメジャー グループの間に各種のリレーションシップを定義し、これらのリレーションシップのプロパティを指定します。  
  
詳細については、「 [ディメンション リレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」を参照してください。  
  
> [!NOTE]  
> このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。 途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。 このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](http://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。  
  
このレッスンの内容は次のとおりです。  
  
[参照リレーションシップの定義](lesson-5-1-defining-a-referenced-relationship.md)  
このタスクでは、プライマリ キーと外部キー リレーションシップを介して直接リンクされているディメンションを介して間接的にファクト テーブルにディメンションをリンクするについて説明します。  
  
[ファクト リレーションシップの定義](lesson-5-2-defining-a-fact-relationship.md)  
ここでは、ファクト テーブルのデータに基づいてディメンションを定義する方法を学習します。また、ディメンション リレーションシップをファクト リレーションシップとして定義する方法を学習します。  
  
[多対多関係の定義](lesson-5-3-defining-a-many-to-many-relationship.md)  
ここでは、ディメンション テーブルとファクト テーブルの間に存在する多対多リレーションシップの定義を使用し、ファクトを複数のディメンション メンバーに関連付ける方法を学習します。  
  
[メジャー グループでのディメンション粒度の定義](lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)  
ここでは、特定のメジャー グループに対し、ディメンションの粒度を定義する方法を学習します。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 6:計算の定義](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a>参照  
[Analysis Services のチュートリアル シナリオ](analysis-services-tutorial-scenario.md)  
[ディメンション リレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
  
