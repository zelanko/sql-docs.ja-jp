---
title: "DMX を使用したドリルスルー クエリの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 5
---
# DMX を使用したドリルスルー クエリの作成
  ドリルスルーをサポートするすべてのモデルでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または DMX をサポートするその他のクライアントで DMX クエリを作成することで、ケース データと構造データを取得できます。  
  
> [!WARNING]  
>  データを表示するには、ドリルスルーが有効になっており、必要な権限がある必要があります。  
  
## ドリルスルー オプションの指定  
 モデル ケースと構造ケースを取得する場合の一般的な構文は、次のとおりです。  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 DMX クエリを使用してケース データを返す方法については、「[SELECT FROM &#60;model&#62;.CASES (DMX)](../Topic/SELECT%20FROM%20%3Cmodel%3E.CASES%20\(DMX\).md)」と「[SELECT FROM &#60;structure&#62;.CASES](../Topic/SELECT%20FROM%20%3Cstructure%3E.CASES.md)」を参照してください。  
  
## 使用例  
 次に示す DMX クエリでは、タイム シリーズ モデルから特定の製品シリーズのケース データが返されます。 このクエリでは、 **Amount**列も返されます。この列はモデルでは使用されていませんが、マイニング構造では使用可能です。  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 この例では、別名を使用して構造列の名前が変更されています。 構造列に別名を割り当てないと、'Expression' という名前で列が返されます。 これはすべての名前のない列に対する既定の動作です。  
  
## 参照  
 [ドリルスルー クエリ (データ マイニング)](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [マイニング構造でのドリルスルー](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  