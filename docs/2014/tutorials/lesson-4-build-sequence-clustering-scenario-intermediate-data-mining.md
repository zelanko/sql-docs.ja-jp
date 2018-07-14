---
title: 'レッスン 4: シーケンス クラスター シナリオ (中級者向けデータ マイニング チュートリアル) を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e594e44dd3c8af8ade94c549d8b489f31623553
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251204"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a>レッスン 4: シーケンス クラスター シナリオの作成 (中級者向けデータ マイニング チュートリアル)
  マーケティング部門は、[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]顧客の行動を把握したい、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] Web サイト。 同社は、顧客が製品を買い物かごに入れる順序に一定のパターンがあるのではないかと推測しています。 マーケティング部門は、顧客がどのような場合に関連商品を買い物かごに追加するかを把握するために、購入順序を分析しようとしています。 この情報を使用すると、Web サイトのフローを効率化し、別の製品も購入するように顧客を導くことができます。  
  
 このレッスンを完了すると、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用して顧客が次に買い物かごに入れる商品を予測するマイニング モデルを作成できます。 次に、2 つのバージョンのモデルを検証します。1 つは、顧客が買い物かごに商品を入れる順序のみを分析するモデルで、もう 1 つは、クラスタリングのための追加の顧客の人口統計を含むモデルです。 最後に、これらのモデルを使用して、顧客に商品を勧めるために使用できる予測を作成します。  
  
 作成した market basket マイニング構造を使用するのレッスンでは、タスクを完了する[レッスン 3: マーケット バスケット シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)します。 このレッスンの内容は次のとおりです。  
  
-   [シーケンス クラスター マイニング モデルの構造を作成する&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [シーケンス クラスター モデルの処理](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [シーケンス クラスター モデルの検証&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [関連するシーケンス クラスター モデルを作成する&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [シーケンス クラスター モデルで予測の作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [シーケンス クラスター マイニング モデルの構造を作成する&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>すべてのレッスン  
 [レッスン 1: 中級者向けデータ マイニング ソリューションの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [レッスン 2: 予測シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [レッスン 3: マーケット バスケット シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 レッスン 4: シーケンス クラスター シナリオ (中級者向けデータ マイニング チュートリアル)  
  
 [レッスン 5: ニューラル ネットワーク モデルとロジスティック回帰モデルの構築&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [基本的なデータ マイニング チュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [中級者向けデータ マイニング チュートリアル&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
