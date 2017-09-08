---
title: "データ マイニング プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ClusterCount property
- AllowedProvidersInOpenRowset property
- MinimumSeriesValue property
- ScoreMethod property
- MinimumImportance property
- ModellingCardinality property
- BrentTolerance property
- ComplexityPenalty property
- MaximumItemsetCount property
- MinimumSupport property
- AllowSessionMiningModels property
- HoldoutPercentage property
- ClusterCountPrior property
- MaximumSequenceStates property
- OptimizedPredictionCount property
- data mining [Analysis Services], properties
- MaximumStates property
- MaximumContinuousInputAttributes property
- MaximumOutputAttributes property
- AllowAdHocOpenRowsetQueries property
- Enabled property
- HistoricModelGap property
- SampleSize property
- MaximumInputAttributes property
- PeriodicityHint property
- MissingValueSubstitution property
- SplitMethod property
- ForceRegressor property
- MaximumBucketsForContinuousSplit property
- MaxConcurrentPredictionQueries property
- MinimumItemsetSize property
- AcyclicGraph property
- HoldoutMethod property
- StoppingTolerance property
- properties [data mining]
- AutoDetectPeriodicity property
- HoldoutTolerance property
- MinimumLeafCases property
- HoldoutSeed property
- MinimumClusterCases property
- ClusterCountDeviation property
- MinimumDependencyProbability property
- ClusteringMethod property
- MaximumItemsetSize property
- HiddenNodeRatio property
- MaximumSeriesValue property
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9d8dfbc8391518ff1375cf47102d4cb607992338
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="data-mining-properties"></a>データ マイニング プロパティ
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、次の表に示すデータ マイニング サーバー プロパティがサポートされています。 その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードのみ  
  
## <a name="non-specific-category"></a>不特定カテゴリ  
 **AllowSessionMiningModels**  
 セッション マイニング モデルを作成できるかどうかを示すブール型プロパティです。  
  
 このプロパティの既定値は False であり、セッション マイニング モデルを作成できないことを示します。  
  
 **AllowAdHocOpenRowsetQueries**  
 開かれた行セットのアドホック クエリを許可するかどうかを示すブール型プロパティです。  
  
 このプロパティの既定値は False であり、開かれた行セットのクエリがセッション中に許可されないことを示します。  
  
 **AllowedProvidersInOpenRowset**  
 開かれた行セットで許可されるプロバイダーを識別する文字列プロパティです。コンマまたはセミコロンで区切られたプロバイダー ProgID の一覧または [All] で構成されます。  
  
 **MaxConcurrentPredictionQueries**  
 同時予測クエリの最大数を定義する、符号付き 32 ビット整数のプロパティです。  
  
## <a name="algorithms-category"></a>アルゴリズム カテゴリ  
 **Microsoft_Association_Rules\ Enabled**  
 Microsoft_Association_Rules アルゴリズムが有効かどうかを示すブール型プロパティです。  
  
 **Microsoft_Clustering\ Enabled**  
 Microsoft_Clustering algorithm アルゴリズムが有効かどうかを示すブール型プロパティです。  
  
 **Microsoft_Decision_Trees\ Enabled**  
 Microsoft_DecisionTrees アルゴリズムが有効かどうかを示すブール型プロパティです。  
  
 **Microsoft_Naive_Bayes\ Enabled**  
 Microsoft_Naive_Bayes アルゴリズムが有効かどうかを示すブール型プロパティです。  
  
 **Microsoft_Neural_Network\ Enabled**  
 Microsoft_Neural_Network アルゴリズムが有効かどうかを示すブール型プロパティです。  
  
 **Microsoft_Sequence_Clustering\ Enabled**  
 Microsoft_Sequence_Clustering アルゴリズムが有効かどうかを示すブール型プロパティです。  
  
 **Microsoft_Time_Series\ Enabled**  
 Microsoft_Time_Series アルゴリズムが有効かどうかを示すブール型プロパティです。  
  
 **Microsoft_Linear_Regression\ Enabled**  
 Microsoft_Linear_Regression アルゴリズムが有効かどうかを示すブール型プロパティです。  
  
 **Microsoft_Logistic_Regression\ Enabled**  
 Microsoft_Logistic_Regression アルゴリズムが有効かどうかを示すブール型プロパティです。  
  
> [!NOTE]  
>  サーバー上で使用可能なデータ マイニング サービスを定義するプロパティ以外に、特定のアルゴリズムの動作を定義するデータ マイニング プロパティが存在します。 データ マイニング モデルをサーバー レベルでなく、個々に作成する場合は、これらのプロパティを構成します。 詳しくは、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [物理アーキテクチャ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/physical-architecture-analysis-services-data-mining.md)   
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
