---
description: IsTestCase (DMX)
title: IsTestCase (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 11795005d0a2a7cf97a515278a30a586ff640ef0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88352278"
---
# <a name="istestcase-dmx"></a>IsTestCase (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  指定されたデータマイニングモデルまたはマイニング構造のテストケースとしてケースが使用されるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsTestCase()  
```  
  
## <a name="result-type"></a>結果の種類  
 ケースがテストデータセットの一部である場合は **true** を返します。それ以外の場合は **false**。  
  
## <a name="remarks"></a>解説  
 データマイニングウィザードを使用してマイニング構造および関連マイニングモデルを作成する場合、既定では、ケースの30% がテストデータセットとして使用するために確保されます。 残りのケースは、データ マイニング モデルのトレーニングに使用されます。 同じテストデータセットは、その構造に基づくすべてのモデルで使用できます。 ただし、DMX を使用してマイニングモデルを作成する場合、既定では、すべてのデータがモデルのトレーニングに使用され、テストセットは作成されません。 テストデータセットの作成を有効にするには、WITH 予約句のパラメーターを設定する必要があります。  
  
 <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> プロパティと <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A> プロパティの値を表示すると、特定のマイニング構造にテスト セットが作成されたかどうかを確認できます。  
  
> [!NOTE]  
>  IsTrainingCase 関数または IsTestCase 関数を使用して特定のモデルのケースに関する詳細を返す場合は、モデルでドリルスルーを有効にする必要があります。 詳細については、「 [Enable Drillthrough for a Mining Model](https://docs.microsoft.com/analysis-services/data-mining/enable-drillthrough-for-a-mining-model)」(マイニング モデルのドリルスルーの有効化) を参照してください。  
  
 トレーニングデータセットの一部であるケースを返すには、関数 [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md)を使用します。  
  
## <a name="examples"></a>例  
 次の例では、 `Targeted Mailing` 「 [基本的なデータマイニングチュートリアル](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」で作成したマイニング構造を使用します。 このクエリでは、テストに使用される構造内のすべてのケースが返されます。  
  
```  
SELECT *  
FROM [Targeted Mailing].CASES  
WHERE IsTestCase()  
```  
  
 データマイニングで使用されるケースをクエリする方法の詳細については、「 [SELECT FROM &#60;model&#62;」を参照してください。DMX&#41;&#40;ケース ](../dmx/select-from-model-cases-dmx.md) は [&#60;構造&#62; から選択します。ケース](../dmx/select-from-structure-cases.md)。  
  
## <a name="see-also"></a>参照  
 [DMX&#41;&#40;関数 ](../dmx/functions-dmx.md)   
 [データマイニングクエリ](https://docs.microsoft.com/analysis-services/data-mining/data-mining-queries)   
 [トレーニング データ セットとテスト データ セット](https://docs.microsoft.com/analysis-services/data-mining/training-and-testing-data-sets)  
  
  
