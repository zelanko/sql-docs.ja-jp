---
title: "DMX を使用したドリルスルー クエリを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3b9487131e474dd00a25390a53cb5f3f11d07d2c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="create-drillthrough-queries-using-dmx"></a>DMX を使用したドリルスルー クエリの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]ドリルスルーをサポートするすべてのモデルを取得できますケース データと構造データで DMX クエリを作成することで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または DMX をサポートするその他のクライアントです。  
  
> [!WARNING]  
>  データを表示するには、ドリルスルーが有効になっており、必要な権限がある必要があります。  
  
## <a name="specifying-drillthrough-options"></a>ドリルスルー オプションの指定  
 モデル ケースと構造ケースを取得する場合の一般的な構文は、次のとおりです。  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 DMX クエリを使用してケース データを返す方法については、「[SELECT FROM &#60;model&#62;.CASES (DMX)](../../dmx/select-from-model-cases-dmx.md)」と「[SELECT FROM &#60;structure&#62;.CASES](../../dmx/select-from-structure-cases.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次に示す DMX クエリでは、タイム シリーズ モデルから特定の製品シリーズのケース データが返されます。 このクエリでは、 **Amount**列も返されます。この列はモデルでは使用されていませんが、マイニング構造では使用可能です。  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 この例では、別名を使用して構造列の名前が変更されています。 構造列に別名を割り当てないと、'Expression' という名前で列が返されます。 これはすべての名前のない列に対する既定の動作です。  
  
## <a name="see-also"></a>参照  
 [ドリルスルー クエリ (データ マイニング)](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [マイニング構造でのドリルスルー](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  
