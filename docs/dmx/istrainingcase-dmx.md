---
title: IsTrainingCase (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c42ecb976884573e313c06adc4241e202e123df
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62503572"
---
# <a name="istrainingcase-dmx"></a>IsTrainingCase (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ケースが、指定されたデータ マイニング モデルまたはマイニング構造のトレーニング ケースとして使用されるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsTrainingCase()  
```  
  
## <a name="result-type"></a>結果の種類  
 返します**true**場合は、トレーニング データ セットの一部である場合は、それ以外の場合**false**。  
  
## <a name="remarks"></a>コメント  
 データ マイニング ウィザードを使用してマイニング構造および関連マイニング モデルを作成する場合、既定では全ケースの 30% がテスト データセットの使用のために確保されます。 指定したデータ ソース内の残りのケースはモデルのトレーニングに使用されます。 ただし、データ マイニング拡張機能 (DMX) を使用してマイニング モデルを作成する場合は、既定ですべてのデータがモデルのトレーニングに使用され、テスト セットは作成されません。 テスト データセットの作成を有効にするには、WITH HOLDOUT 句のパラメーターを設定する必要があります。  
  
 <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> プロパティと <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A> プロパティの値を表示すると、特定のデータ マイニング構造のデータがテスト セットとトレーニング セットにパーティション分割されているかどうかを確認できます。  
  
> [!NOTE]  
>  モデルのケースに関する詳細を返す、IsTrainingCase または IsTestCase 関数を使用する場合、モデルでドリルスルーを有効にする必要があります。 詳細については、「 [Enable Drillthrough for a Mining Model](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)」(マイニング モデルのドリルスルーの有効化) を参照してください。  
  
 テスト データ セットの一部であるケースを返す関数を使用して[IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md)します。  
  
## <a name="examples"></a>使用例  
 次の例は、クラスタ リングのデータ マイニング モデルで対象の絞り込みメール配信シナリオから、 [Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)します。 クエリでは、マイニング モデルのトレーニングで使用されたケースのみが返されます。 さらに、トレーニング ケースは 40 歳未満の顧客だけに制限されます。  
  
```  
SELECT *  
FROM [TM Clustering].CASES  
WHERE IsTrainingCase()  
AND [Age] <40  
```  
  
 他のデータ マイニングで使用されるケースをクエリする方法の例では、次を参照してください。 [SELECT FROM&#60;モデル&#62;します。ケース&#40;DMX&#41; ](../dmx/select-from-model-cases-dmx.md)と[SELECT FROM&#60;構造&#62;します。ケース](../dmx/select-from-structure-cases.md)します。  
  
## <a name="see-also"></a>参照  
 [トレーニング セットとテスト データ セット](../analysis-services/data-mining/training-and-testing-data-sets.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [データ マイニング クエリ](../analysis-services/data-mining/data-mining-queries.md)  
  
  
