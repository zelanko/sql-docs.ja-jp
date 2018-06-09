---
title: データ マイニング拡張機能 (DMX) 関数リファレンス |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9f0851d3ec373161c9277013fc746ebda5b91f89
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842535"
---
# <a name="data-mining-extensions-dmx-function-reference"></a>データ マイニング拡張機能 (DMX) 関数リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、データ マイニング拡張機能 (DMX) 言語のいくつかの関数をサポートしています。 関数によって、予測クエリの結果が拡張され、予測の詳細を説明する情報が含まれるようになります。 また、関数により、予測結果が返される方法をよりコントロールできるようにもなります。 次の表に、DMX の関数の使用方法を理解するのに役立つリソースへのリンクを示します。  
  
|機能|説明|  
|--------------|-----------------|  
|[一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)|すべての種類のモデルで使用できる関数の一覧を示し、特定の種類のマイニング モデルに対してクエリを実行する方法に関する詳細情報へのリンクを提供します。|  
|[構造と DMX 予測クエリの使用](../dmx/structure-and-usage-of-dmx-prediction-queries.md)|DMX を使用して予測クエリを作成する方法の概要について説明します。|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|順位付け式に基づいてデータを昇順に並べ替え、最下位行から指定数を含むテーブルを返します。|  
  
 次の表は、DMX がサポートする関数の一覧を示しています。  
  
|機能|説明|  
|--------------|-----------------|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|順位付け式に基づいてデータを昇順に並べ替え、末尾から指定された行数を含むテーブルを返します。|  
|[BottomPercent &#40;DMX&#41;](../dmx/bottompercent-dmx.md)|順位付け式に基づいてデータを昇順に並べ替え、最下位行から指定されたパーセント式を満たすまでの最小行数を含むテーブルを返します。|  
|[BottomSum &#40;DMX&#41;](../dmx/bottomsum-dmx.md)|順位付け式に基づいてデータを昇順に並べ替え、最下位行から指定された合計式を満たすまでの最小行数を含むテーブルを返します。|  
|[クラスター &#40;DMX&#41;](../dmx/cluster-dmx.md)|入力ケースを含んでいる可能性が最も高いクラスターを返します。|  
|[ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)|入力ケースがクラスターに所属する確率を返します。|  
|[存在する&#40;DMX&#41;](../dmx/exists-dmx.md)|指定した SELECT ステートメントから返された結果セットに少なくとも 1 行が含まれる場合は true を返します。|  
|[IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)|現在のノードが、指定したノードからの降順であるかどうかを示します。|  
|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)|指定したノードがそのケースを含むかどうかを示します。|  
|[IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)|ケースがテスト ケースのセットに属しているかどうかを示します。|  
|[IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md)|ケースがトレーニング ケースのセットに属しているかどうかを示します。|  
|[Lag &#40;DMX&#41;](../dmx/lag-dmx.md)|現在のケースの日付とデータ内の最後の日付とのタイム スライスを返します。|  
|[予測&#40;DMX&#41;](../dmx/predict-dmx.md)|指定した列上で予測を行います。|  
|[PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)|指定した予測可能列の調整済みの確率を返します。|  
|[PredictAssociation &#40;DMX&#41;](../dmx/predictassociation-dmx.md)|列内の結合メンバーシップを予測します。|  
|[PredictCaseLikelihood &#40;DMX&#41;](../dmx/predictcaselikelihood-dmx.md)|入力ケースが既存のモデル内に収まる確率値を返します。 この関数は、クラスター モデルでのみ使用できます。|  
|[PredictHistogram &#40;DMX&#41;](../dmx/predicthistogram-dmx.md)|指定した列に対するヒストグラムを表すテーブルを返します。|  
|[PredictNodeId &#40;DMX&#41;](../dmx/predictnodeid-dmx.md)|選択したケースの NodeID を返します。|  
|[PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)|指定した列の確率を返します。|  
|[PredictSequence &#40;DMX&#41;](../dmx/predictsequence-dmx.md)|シーケンス内の次の値を予測します。|  
|[PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)|指定した列に対する標準偏差値を取得します。|  
|[PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)|列のサポート値を返します。|  
|[PredictTimeSeries &#40;DMX&#41;](../dmx/predicttimeseries-dmx.md)|時系列に対する将来の値を予測します。|  
|[PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)|指定した列の変位値を返します。|  
|[RangeMax &#40;DMX&#41;](../dmx/rangemax-dmx.md)|指定した DISCRETIZED 型の列に対して検出される予測バケットの上限値を返します。|  
|[RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)|指定した DISCRETIZED 型の列に対して検出される予測バケットの中間値を返します。|  
|[RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)|指定した DISCRETIZED 型の列に対して検出される予測バケットの下限値を返します。|  
|[StructureColumn &#40;DMX&#41;](../dmx/structurecolumn-dmx.md)|指定したテーブルのマイニング構造列の値を返します。|  
|[TopCount &#40;DMX&#41;](../dmx/topcount-dmx.md)|指定された最上位行数を含むテーブルを、順位付け式に基づいて降順で返します。|  
|[TopPercent &#40;DMX&#41;](../dmx/toppercent-dmx.md)|順位付け式に基づいてデータを降順に並べ替え、最上位行から指定されたパーセント式を満たすまでの最小行数を含むテーブルを返します。|  
|[TopSum &#40;DMX&#41;](../dmx/topsum-dmx.md)|順位付け式に基づいてデータを降順に並べ替え、最上位行から指定された合計式を満たすまでの最小行数を含むテーブルを返します。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
