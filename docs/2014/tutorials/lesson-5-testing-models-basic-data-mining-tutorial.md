---
title: 'レッスン 5: モデルのテスト (基本的なデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9a7ddcf-2b01-485f-bbb5-62638b303bc6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 88a9d564b297d277d1566152cc11599bec912ddc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63185429"
---
# <a name="lesson-5-testing-models-basic-data-mining-tutorial"></a>レッスン 5: モデルのテスト (基本的なデータ マイニング チュートリアル)
  絞り込みメール配信シナリオのトレーニング セットを使用してモデルを処理したので、テスト セットに対してモデルをテストします。 検証は、データ マイニング プロセスにおける重要な手順です。 運用環境に配置する前に、実際のデータに対する絞り込みメール配信マイニング モデルの性能を把握しておくことが重要です。  
  
 テスト セット内のデータには自転車購入に関する既知の値が既に含まれているため、モデルの予測が正しいかどうかを簡単に判断できます。 最高のを実行するモデルは、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]マーケティング部門によって、対象となるメーリングキャンペーンの顧客を識別するために使用されます。  
  
 このレッスンでは、複数の手法を使用してモデルを検証します。  
  
1.  テストセットに対して予測を作成し、既知の結果に対するモデルの精度を確認します。 *リフトチャート*を使用して、その効果を測定します。  
  
     [リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
2.  フィルター選択されたデータ サブセットを対象にしてモデルをテストします。 同じリフト チャート内で複数のモデルを比較できます。  
  
     [フィルター選択されたモデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
 モデルの検証全般の詳細については、「[データマイニングの概念](../../2014/analysis-services/data-mining/data-mining-concepts.md)」を参照してください。  
  
## <a name="first-task-in-lesson"></a>このレッスンの最初の作業  
 [リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a>前のレッスン  
 [レッスン 4: 「基本的なデータマイニングチュートリアル」 &#40;対象を絞ったメーリングモデルの調査&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 6: 予測の作成と操作 &#40;基本的なデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [[リフトチャート] タブ &#40;マイニング精度チャートビュー&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)   
 [リフトチャート &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [データマイニング&#41;のテストと検証 &#40;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [[分類マトリックス] タブ &#40;マイニング精度チャートビュー&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md)   
 [分類マトリックス &#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)  
  
  
