---
title: "クロス検証の式 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd1ea582-29a1-4154-8de2-47bab3539b4d
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 041206471791fe8be8b06e407854f96fc021eedd
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="cross-validation-formulas"></a>クロス検証の式
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]クロス検証レポートを生成するときに含まれているマイニング モデル (モデルの作成に使用されたアルゴリズム) の種類、予測可能属性および予測可能な属性のデータ型に応じて、各モデルの精度のメジャー存在する場合は、値です。  
  
 このセクションでは、クロス検証レポートで使用されるメジャーを示し、計算の方法について説明します。  
  
 モデルの種類ごとの精度のメジャーについて詳しくは、「 [相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)」をご覧ください。  
  
## <a name="formulas-used-for-cross-validation-measures"></a>クロス検証のメジャーで使用される数式  
  
> [!NOTE]  
>  **重要:** これらの精度のメジャーは、対象の属性ごとに計算されます。 属性ごとに対象の値を指定または省略できます。 データ セット内のケースに対象の属性の値が含まれない場合、そのケースは、" *不足値*" と呼ばれる特殊な値が含まれるものと見なされます。 不足値のある行は、特定の対象の属性に対する精度のメジャーを計算するときにカウントされません。 スコアは属性ごとに個別に計算されるので、対象の属性に値があって他の属性に値がなくても、対象の属性のスコアには影響しません。  
  
|[メジャー]|適用対象|実装|  
|-------------|----------------|--------------------|  
|**真陽性**|不連続属性、値を指定|以下の条件を満たしているケースの数です。<br /><br /> 対象の値がケースに含まれている。<br /><br /> 対象の値がケースに含まれていることがモデルで予測された。|  
|**True Negative**|不連続属性、値を指定|以下の条件を満たしているケースの数です。<br /><br /> 対象の値がケースに含まれていない。<br /><br /> 対象の値がケースに含まれていないことがモデルで予測された。|  
|**偽陽性**|不連続属性、値を指定|以下の条件を満たしているケースの数です。<br /><br /> 実際の値が対象の値と等しい。<br /><br /> 対象の値がケースに含まれていることがモデルで予測された。|  
|**False Negative**|不連続属性、値を指定|以下の条件を満たしているケースの数です。<br /><br /> 実際の値が対象の値と等しくない。<br /><br /> 対象の値がケースに含まれていないことがモデルで予測された。|  
|**合格/不合格**|不連続属性、対象の指定なし|以下の条件を満たしているケースの数です。<br /><br /> 最も高い確率を持つ予測された状態が入力状態と同じであり、確率が **[状態のしきい値]**の値を超える場合は合格。<br /><br /> それ以外の場合は不合格。|  
|**リフト**|不連続属性。 対象の値を指定できますが、必須ではありません。|対象の属性の値が含まれるすべての行の平均対数確率値。ここで、各ケースの対数確率値は Log(ActualProbability/MarginalProbability) として計算されます。 平均を計算するため、対数尤度の合計が入力データセットの行数で割られます。対象の属性の不足値がある行は除外されます。<br /><br /> Lift には正または負の値を指定できます。 正の値は、ランダムな推測を上回る効果的なモデルであることを示します。|  
|**ログ スコア**|不連続属性。 対象の値を指定できますが、必須ではありません。|合計後に入力データセットの行数で割った、各ケースの実際の確率の対数。対象の属性の不足値がある行は除外されます。<br /><br /> 確率は小数で表されるので、ログ スコアは常に負の数値になります。 0 に近いほど、良いスコアになります。|  
|**Case likelihood**|クラスター|パーティション内のケースの数で割った、すべてのケースのクラスター可能性スコアの合計。対象の属性の不足値がある行は除外されます。|  
|**平均絶対誤差**|連続属性|パーティション内のケースの数で割った、パーティションのすべてのケースの絶対誤差の合計。|  
|**2 乗平均平方根誤差**|連続属性|パーティションの平均 2 乗誤差の平方根。|  
|**Root mean squared error**|不連続属性。 対象の値を指定できますが、必須ではありません。|パーティション内のケースの数で割った、確率スコアの補数の 2 乗の平均の平方根。対象の属性の不足値がある行は除外されます。|  
|**Root mean squared error**|不連続属性、対象の指定なし。|パーティション内のケースの数で割った、確率スコアの補数の 2 乗の平均の平方根。対象の属性の不足値があるケースは除外されます。|  
  
## <a name="see-also"></a>参照  
 [テストおよび検証 &#40;データ マイニング&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [相互検証 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)  
  
  
