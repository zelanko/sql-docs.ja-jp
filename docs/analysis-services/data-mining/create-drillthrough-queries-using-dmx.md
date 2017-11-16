---
title: "DMX を使用したドリルスルー クエリを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 93a6893146a2367719ad7b4bed23a76b7d43e589
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-drillthrough-queries-using-dmx"></a>DMX を使用したドリルスルー クエリの作成
  ドリルスルーをサポートするすべてのモデルでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または DMX をサポートするその他のクライアントで DMX クエリを作成することで、ケース データと構造データを取得できます。  
  
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
  
  

