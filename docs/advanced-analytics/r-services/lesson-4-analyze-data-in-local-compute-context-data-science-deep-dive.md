---
title: "レッスン 4: ローカル計算コンテキストでデータを分析する (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: ""
ms.date: "10/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# レッスン 4: ローカル計算コンテキストでデータを分析する (データ サイエンスの詳細情報)
通常はサーバー コンテキストを使用して複雑な R コードを実行する方がはるかに高速ですが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータを取り出してプライベート ワークステーションで分析する方が便利な場合があります。  
  
このセクションでは、ローカル計算コンテキストに切り替えて戻す方法、およびコンテキスト間でデータを移動してパフォーマンスを最適化する方法を説明します。  
  
## ローカル サマリーを作成する  
  
1.  すべての作業をローカルに行うように計算コンテキストを変更します。  
  
    ```R  
    rxSetComputeContext ("local")    
    ```  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータを抽出するときは、1 回の読み取りで抽出する行数を増やすとパフォーマンスが向上することがよくあります。  そのためには、データ ソースで *rowsPerRead* パラメーターの値を大きくします。  
  
    ```R  
    sqlServerDS1 <- RxSqlServerData(  
       connectionString = sqlConnString,        
       table = sqlFraudTable,   
       colInfo = ccColInfo,   
       rowsPerRead = 10000)  
    ```  
  
    これまでは、*rowsPerRead* の値は 5000 に設定されていました。  
  
3.  今度は、新しいデータ ソースに対して *rxSummary* を呼び出します。  
  
    ```R  
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)    
    ```  
  
    実際の結果は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターのコンテキストで *rxSummary* を実行した場合と同じになるはずです。  ただし、処理は速くなる場合と遅くなる場合があります。 データは分析のためのローカル コンピューターに転送されるので、処理速度はデータベースへの接続に左右されます。  
  

## 次の手順  
[SQL Server と XDF ファイルの間でデータを移動させる (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/move-data-between-sql-server-and-xdf-file-data-science-deep-dive.md)  
  
## 前の手順  
[rxDataStep を使用してチャンク分析を実行する (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/perform-chunking-analysis-using-rxdatastep-data-science-deep-dive.md)  
  
  
  
