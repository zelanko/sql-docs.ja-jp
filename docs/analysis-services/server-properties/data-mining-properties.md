---
title: データ マイニング プロパティ |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f3b63036a1279280a57886ea69feffaa19c29078
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="data-mining-properties"></a>データ マイニング プロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
  
