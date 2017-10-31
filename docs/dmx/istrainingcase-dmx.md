---
title: "IsTrainingCase (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsTrainingCase
dev_langs:
- DMX
helpviewer_keywords:
- IsTrainingCase function
ms.assetid: 63eab315-e743-470d-9c4c-edfc3f4058a3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ed062df083d4c11c635f9241eac38b4ec4406a32
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="istrainingcase-dmx"></a>IsTrainingCase (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ケースが、指定されたデータ マイニング モデルまたはマイニング構造のトレーニング ケースとして使用されるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsTrainingCase()  
```  
  
## <a name="result-type"></a>結果の種類  
 返します**true**ケースがトレーニング データ セットの一部である場合それ以外の場合**false**です。  
  
## <a name="remarks"></a>解説  
 データ マイニング ウィザードを使用してマイニング構造および関連マイニング モデルを作成する場合、既定では全ケースの 30% がテスト データセットの使用のために確保されます。 指定したデータ ソース内の残りのケースはモデルのトレーニングに使用されます。 ただし、データ マイニング拡張機能 (DMX) を使用してマイニング モデルを作成する場合は、既定ですべてのデータがモデルのトレーニングに使用され、テスト セットは作成されません。 テスト データセットの作成を有効にするには、WITH HOLDOUT 句のパラメーターを設定する必要があります。  
  
 <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> プロパティと <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A> プロパティの値を表示すると、特定のデータ マイニング構造のデータがテスト セットとトレーニング セットにパーティション分割されているかどうかを確認できます。  
  
> [!NOTE]  
>  モデルのケースに関する詳細を返す、IsTrainingCase または IsTestCase 関数を使用する場合、モデルでドリルスルーを有効にする必要があります。 詳細については、「 [Enable Drillthrough for a Mining Model](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)」(マイニング モデルのドリルスルーの有効化) を参照してください。  
  
 テスト データ セットの一部であるケースを返すには、関数を使用[IsTestCase & # #40; DMX &#41;](../dmx/istestcase-dmx.md)です。  
  
## <a name="examples"></a>使用例  
 次の例は、クラスタ リングのデータ マイニング モデルの絞り込みメール配信シナリオから、[基本的なデータ マイニング チュートリアル」](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)です。 クエリでは、マイニング モデルのトレーニングで使用されたケースのみが返されます。 さらに、トレーニング ケースは 40 歳未満の顧客だけに制限されます。  
  
```  
SELECT *  
FROM [TM Clustering].CASES  
WHERE IsTrainingCase()  
AND [Age] <40  
```  
  
 その他のデータ マイニングで使用されるケースをクエリする方法の例については、次を参照してください。 [SELECT FROM &#60; モデル &#62;。場合 &#40;DMX"&"#41;](../dmx/select-from-model-cases-dmx.md)と[SELECT FROM &#60; 構造 &#62;。ケース](../dmx/select-from-structure-cases.md)です。  
  
## <a name="see-also"></a>参照  
 [トレーニング セットとテスト データ セット](../analysis-services/data-mining/training-and-testing-data-sets.md)   
 [関数 &#40;DMX"&"#41;](../dmx/functions-dmx.md)   
 [データ マイニング クエリ](../analysis-services/data-mining/data-mining-queries.md)  
  
  

