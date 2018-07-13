---
title: 'レッスン 5: ニューラル ネットワーク モデルとロジスティック回帰モデル (中級者向けデータ マイニング チュートリアル) の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- data mining [Analysis Services], tutorials
- neural networks
- tutorials [Data Mining]
- neural network model [Analysis Services]
ms.assetid: 42c3701a-1fd2-44ff-b7de-377345bbbd6b
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93946e13e9836aef4cd10bc39ec964e7f8c0d531
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222342"
---
# <a name="lesson-5-building-neural-network-and-logistic-regression-models-intermediate-data-mining-tutorial"></a>レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 (中級者向けデータ マイニング チュートリアル)
  
  
 オペレーション部門[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)]は、コール センターで顧客満足度を向上させるために、プロジェクトに関与しています。 この部門では、コール センターを管理すると共にコール センターの有効性に関する基準をレポートするためにベンダーを雇っています。ここであなたは、ベンダーから提供されたいくつかの予備データの分析を求められました。 彼らは、興味深い発見があるかどうかを知りたがっています。 彼らは特に、人員の配置上の問題を示唆するデータや、顧客満足の改善に役立つと思われるデータに関する情報を求めています。  
  
 データセットは小さなもので、コール センターでのオペレーションの 30 日分しかカバーしていません。 このデータは、シフトごとの未経験のオペレーターと経験を積んだオペレーターの人数、問い合わせの電話の件数、注文の件数と解決する必要がある案件の件数、および顧客からの電話に対する平均応答時間を追跡しています。 さらに、顧客の不満を表す 1 つの指標である *電話放棄呼率*に基づくサービス品質基準も含まれています。  
  
 データが何を示すかについての事前予測情報がないので、ご自身はニューラル ネットワーク モデルを使用して有効な相関関係を探すことに決めました。 ニューラル ネットワーク モデルは、多くの入力と出力の間の複雑な関係を分析できるため、データ探索によく使用されます。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このレッスンでは、データに含まれる傾向を理解するために、ニューラル ネットワーク アルゴリズムを使用して、ご自身とオペレーション チームが使用できるモデルを作成します。 このレッスンの一部として、次の質問に回答してください。  
  
-   顧客満足に影響する要因には何がありますか。  
  
-   コール センターのサービス品質を向上させるにはどのような方法がありますか。  
  
 結果に基づいて、予測に使用できるロジスティック回帰モデルを作成します。 予測は、コール センターのオペレーションの計画に役立てるためにオペレーション チームによって使用されます。  
  
 このレッスンの内容は次のとおりです。  
  
-   [コール センター データ用のビューをソース データを追加する&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
-   [ニューラル ネットワーク構造およびモデルの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [コール センター モデルの検証&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
-   [コール センター構造へのロジスティック回帰モデルの追加&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
-   [コール センター モデルの予測の作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [コール センター データ用のビューをソース データを追加する&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>すべてのレッスン  
 [レッスン 1: 中級者向けデータ マイニング ソリューションの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [レッスン 2: 予測シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [レッスン 3: マーケット バスケット シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [レッスン 4: シーケンス クラスター シナリオの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 レッスン 5: ニューラル ネットワークとロジスティック回帰のシナリオ (中級者向けデータ マイニング チュートリアル)  
  
## <a name="see-also"></a>参照  
 [基本的なデータ マイニング チュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [中級者向けデータ マイニング チュートリアル&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
