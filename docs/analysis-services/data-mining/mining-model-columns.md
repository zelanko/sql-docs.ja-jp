---
title: マイニング モデル列 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a55d6c68fa721d45dcafff96b831dcba7950bc17
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="mining-model-columns"></a>マイニング モデル列
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング モデルは、マイニング構造によって表されるデータにマイニング モデル アルゴリズムを適用します。 マイニング構造と同様に、マイニング モデルには列が含まれています。 マイニング モデルはマイニング構造内に含まれ、マイニング構造によって定義されるプロパティのすべての値を継承します。 マイニング モデルは、マイニング構造に含まれているすべての列またはその一部を使用することができます。  
  
 マイニング モデル列には、使用法とモデリング フラグという 2 つの追加情報を定義できます。  
  
-   **使用法** は、モデルで列がどのように使用されるかを定義するプロパティです。 列は、入力列、キー列、または予測可能列として使用できます。  
  
-   **モデリング フラグ** では、アルゴリズムがより正確なモデルを作成できるように、ケース テーブルに定義されているデータに関する追加情報をアルゴリズムに提供します。 モデリング フラグは、データ マイニング拡張機能 (DMX) 言語を使用してプログラムで定義するか、または **の** データ マイニング デザイナー [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で定義できます。  
  
 次に、マイニング モデル列で定義できるモデリング フラグを示します。  
  
 **MODEL_EXISTENCE_ONLY**  
 属性の存在が属性列の値よりも重要であることを示します。 たとえば、特定の顧客に関連付けられている発注品目の一覧が含まれたケース テーブルについて考えてみます。 テーブル データには、各発注品目の製品タイプ、ID、およびコストが含まれています。 モデリングには、顧客が特定の発注品目を購入したという事実の方が、発注品目そのもののコストよりも重要な場合があります。 この場合は、コスト列を **MODEL_EXISTENCE_ONLY**として設定します。  
  
 **REGRESSOR**  
 アルゴリズムが、指定した列を回帰アルゴリズムの回帰式に使用できることを示します。 このフラグは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリーと [!INCLUDE[msCoName](../../includes/msconame-md.md)] タイム シリーズ アルゴリズムでサポートされています。  
  
 使用法プロパティの設定と、DMX を使用したプログラムによるモデリング フラグの定義について詳しくは、「[CREATE MINING MODEL &#40;DMX&#41;](../../dmx/create-mining-model-dmx.md)」をご覧ください。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] での使用法プロパティの設定およびモデリング フラグの定義について詳しくは、「[データ マイニング オブジェクトの移動](../../analysis-services/data-mining/moving-data-mining-objects.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [マイニング構造と #40 です。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [マイニング モデルのプロパティの変更](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)   
 [マイニング モデルから列を除外します。](../../analysis-services/data-mining/exclude-a-column-from-a-mining-model.md)   
 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
