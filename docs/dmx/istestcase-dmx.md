---
title: "IsTestCase (DMX) |Microsoft ドキュメント"
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
- IsTestCase
dev_langs:
- DMX
helpviewer_keywords:
- IsTestCase function
ms.assetid: 7ff4b895-9bb4-4e26-ab1b-c9049cfc2291
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0880841c201e9f25eb4685d0e6368abbb5bca885
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="istestcase-dmx"></a>IsTestCase (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ケースが、指定されたデータ マイニング モデルまたはマイニング構造のテスト ケースとして使用されるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsTestCase()  
```  
  
## <a name="result-type"></a>結果の種類  
 返します**true**ケースがテスト データ セットの一部である場合それ以外の場合**false**です。  
  
## <a name="remarks"></a>解説  
 データ マイニング ウィザードを使用してマイニング構造および関連マイニング モデルを作成する場合、既定では全ケースの 30% がテスト データセットの使用のために確保されます。 残りのケースは、データ マイニング モデルのトレーニングに使用されます。 その構造に基づくすべてのモデルで同じテスト データセットを使用できます。 ただし、DMX を使用してマイニング モデルを作成する場合は、既定ですべてのデータがモデルのトレーニングに使用され、テスト セットは作成されません。 テスト データ セットの作成を有効にするには、WITH HOLDOUT 句のパラメーターを設定する必要があります。  
  
 <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> プロパティと <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A> プロパティの値を表示すると、特定のマイニング構造にテスト セットが作成されたかどうかを確認できます。  
  
> [!NOTE]  
>  IsTrainingCase または IsTestCase 関数を使用して、特定のモデルでケースに関する詳細を返す場合、モデルでドリルスルーを有効にする必要があります。 詳細については、「 [Enable Drillthrough for a Mining Model](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)」(マイニング モデルのドリルスルーの有効化) を参照してください。  
  
 トレーニング データ セットの一部であるケースを返すには、関数を使用[IsTrainingCase & # #40; DMX &#41;](../dmx/istrainingcase-dmx.md)です。  
  
## <a name="examples"></a>使用例  
 次の例では、`Targeted Mailing`で作成されるマイニング構造、[基本的なデータ マイニング チュートリアル」](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)です。 このクエリでは、テストに使用される構造内のすべてのケースが返されます。  
  
```  
SELECT *  
FROM [Targeted Mailing].CASES  
WHERE IsTestCase()  
```  
  
 データ マイニングで使用されるケースをクエリする方法の詳細については、次を参照してください。 [SELECT FROM &#60; モデル &#62;。場合 (&) #40";"DMX"&"#41;](../dmx/select-from-model-cases-dmx.md)と[SELECT FROM &#60; 構造 &#62;。ケース](../dmx/select-from-structure-cases.md)です。  
  
## <a name="see-also"></a>参照  
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [データ マイニング クエリ](../analysis-services/data-mining/data-mining-queries.md)   
 [トレーニング セットとテスト データ セット](../analysis-services/data-mining/training-and-testing-data-sets.md)  
  
  

