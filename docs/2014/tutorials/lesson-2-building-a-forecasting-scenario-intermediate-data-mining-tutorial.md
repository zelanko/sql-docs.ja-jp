---
title: 'レッスン 2: 予測シナリオの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ee814dc0891e70dfeccf2b96383d1d7b5c324aa8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62931530"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a>レッスン 2: 予測シナリオの作成 (中級者向けデータ マイニング チュートリアル)
  [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]のセールス アナリストであるあなたは、翌年の製品売上を予測するよう依頼されました。 具体的には、さまざまな地域および製品ラインの売上予測を比較する必要があります。 さらに、各製品の売上が一年を通じてどのように変化するかも調べなければなりません。  
  
 依頼された情報を得るため、このレッスンでは、同社の売上データを月別に集計します。また、これらの販売成績をヨーロッパ、北米、太平洋の 3 つの地域別に集計します。  
  
 このレッスンのタスクを完了すると、次の情報を取得できるようになります。  
  
-   各種の自転車の売上の時系列における変化。  
  
-   3 つの地域での売上パターンに違いがあるかどうか。  
  
-   売上高が最も多い時期を予測できるか。  
  
 レッスンは、2 つに分けて行うことができます。  
  
-   第 1 部では、タイム シリーズ モデルを作成および使用する方法の基本について説明します。  
  
-   第 2 部では、すべての地域に基づいた汎用的なタイム シリーズ モデルを作成する方法を、順をおって説明します。 *クロス予測*にこの一般的なモデルを使用できます。  
  
 このレッスンのタスクを完了するには、「レッスン 1: 中級者向け[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データ[マイニングソリューションの作成 &#40;中間データマイニングチュートリアル&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)」で作成したデータソースを使用します。  
  
> [!WARNING]  
>  [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] サンプル データベース内の日付は、このリリース用に更新されています。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]の以前のバージョンを使用する場合は、ここでの手順に従ってモデルを構築することはできますが、異なる結果が表示される場合があります。  
  
 **簡単な予測モデルの作成**  
  
-   [予測のためのデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [中間データマイニングチュートリアル &#40;予測構造とモデルの作成&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [中間データマイニングチュートリアル &#40;予測構造の変更&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [予測モデルのカスタマイズと処理 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [予測モデル &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [タイムシリーズ予測の作成 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 **クロス予測のための一般的な予測モデルの作成**  
  
-   [高度な時系列予測 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [更新されたデータを使用した時系列予測 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [交換データ &#40;中間データマイニングチュートリアル&#41;を使用した時系列予測](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [予測モデルの予測の比較 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [予測のためのデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [タイムシリーズモデルの要件について &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>すべてのレッスン  
 [レッスン 1: 中級者向けデータマイニングソリューションの作成 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 レッスン 2: 予測シナリオ (中級者向けデータ マイニング チュートリアル)  
  
 [レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Microsoft Time Series アルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
