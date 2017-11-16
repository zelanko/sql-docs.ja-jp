---
title: "クロス検証レポート内のメジャー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- root mean square error [data mining]
- cross-validation [data mining]
- mean absolute error [data mining]
- log score [data mining]
- likelihood [data mining]
ms.assetid: a07b1665-7f72-4266-82a4-43a91ae2571d
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f046ddaa3152318bfb3fe01d055bf213fdfdec41
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="measures-in-the-cross-validation-report"></a>相互検証レポートのメジャー
  相互検証では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はマイニング構造のデータを複数のセクションにパーティション分割し、構造および関連マイニング モデルのテストを反復的に実行します。 この分析に基づき、構造および各モデルの標準の精度のメジャーを出力します。  
  
 レポートでは、データ内のフォールドの数や各フォールド内のデータの量に関するいくつかの基本情報に加えて、データの分布を示す一連の一般的な基準が表示されます。 それぞれのセクションに対する一般的な基準を比較することで、構造またはモデルの信頼性を評価できます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、マイニング モデルの一連の詳細メジャーも表示されます。 これらのメジャーは、分析するモデルの種類や、不連続であるか連続であるかなど属性の型によって異なります。  
  
 ここでは、 **[相互検証]** レポートに含まれるメジャーおよびその意味の一覧を示します。 各メジャーの計算方法の詳細については、「 [クロス検証の式](../../analysis-services/data-mining/cross-validation-formulas.md)」を参照してください。  
  
## <a name="list-of-measures-in-the-cross-validation-report"></a>相互検証レポートのメジャーの一覧  
 次の表は、相互検証レポートに表示されるメジャーの一覧を示します。 メジャーは、表の左の列に表示されている *テストの種類*でグループ化されています。 右の列には、レポートに表示されるメジャーの名前、および意味に関する簡単な説明を示します。  
  
|テストの種類|基準と説明|  
|---------------|-------------------------------|  
|クラスター|クラスタリング モデルに適用されるメジャー|  
||**Case likelihood**:<br />                      通常、ケースが特定のクラスターに属する確率を示します。 相互検証の場合、スコアが集計された後、ケースの数で割られます。スコアは、ケースの平均確率となります。|  
|分類|分類モデルに適用されるメジャー|  
||**True Positive**/**True Negative**/**False Positive**/**False Negative**:<br /><br /> 予測された状態が対象の状態と一致し、指定されたしきい値より予測確率が大きい、パーティション内の行または値の数。<br /><br /> 対象の属性の不足値のあるケースは除外されます。すべての値のカウントが加算されるわけではありません。|  
||**Pass/Fail**:<br />                      予測された状態が対象の状態と一致し、予測確率の値が 0 を超えるパーティション内の行または値の数。|  
|Likelihood|Likelihood メジャーは複数の種類のモデルに適用されます。|  
||**Lift**:<br />                      実際の予測確率対テスト ケースの周辺確率の比です。 対象の属性の不足値があるケースは除外されます。<br /><br /> 通常、モデルが使用されるときに対象の結果の確率がどれだけ向上するかを示します。|  
||**Root Mean Square Error**:<br />                      パーティション内のケースの数で割った、すべてのパーティション ケースの平均誤差の平方根です。対象の属性の不足値がある行は除外されます。<br /><br /> RMSE は、予測モデルの一般的な推定機能です。 スコアは各ケースの残差を平均し、モデル誤差の 1 つのインジケーターを生成します。|  
||**Log score**:<br />                      合計後に入力データセットの行数で割った、各ケースの実際の確率の対数です。対象の属性の不足値がある行は除外されます。<br /><br /> 確率は小数で表されるので、ログ スコアは常に負の数値になります。 0 に近い数値ほど、良いスコアになります。 生のスコアが非常に不規則な分布またはゆがんだ分布を持つのに対し、ログ スコアは割合に似ています。|  
|Estimation|連続する数値属性を予測する推定モデルのみに適用されるメジャー。|  
||**Root Mean Square Error**:<br />                      予測値を実際の値と比較するときの平均誤差。<br /><br /> RMSE は、予測モデルの一般的な推定機能です。 スコアは各ケースの残差を平均し、モデル誤差の 1 つのインジケーターを生成します。|  
||**Mean Absolute Error**:<br />                      予測値対実際の値の平均誤差です。誤差の絶対合計の平均として計算されます。<br /><br /> 平均絶対誤差は、予測全体が実際の値にどの程度近いかを判断するときに便利です。 小さいスコアは、予測が正確だったことを意味します。|  
||**Log Score**:<br />                      合計後に入力データセットの行数で割った、各ケースの実際の確率の対数です。対象の属性の不足値がある行は除外されます。<br /><br /> 確率は小数で表されるので、ログ スコアは常に負の数値になります。 0 に近い数値ほど、良いスコアになります。 生のスコアが非常に不規則な分布またはゆがんだ分布を持つのに対し、ログ スコアは割合に似ています。|  
|集計|各パーティションの結果における分散を示します。|  
||**Mean**:<br />                      特定のメジャーに関するパーティション値の平均です。|  
||**Standard Deviation**:<br />                      モデル内のすべてのパーティションを対象とした、特定メジャーの平均値に基づく偏差の平均。<br /><br /> 相互検証の場合、このスコアの値が高いことは、フォールドの間の変動が大きいことを意味します。|  
  
## <a name="see-also"></a>参照  
 [テストおよび検証 (データ マイニング)](../../analysis-services/data-mining/testing-and-validation-data-mining.md)  
  
  

