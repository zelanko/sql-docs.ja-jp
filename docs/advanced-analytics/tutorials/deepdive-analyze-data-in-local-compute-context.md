---
title: "ローカル コンピューティング コンテキストでデータを分析 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d8e6516b7d203180d5c2a605db1099b1dcbae708
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="analyze-data-in-local-compute-context-data-science-deep-dive"></a>ローカル コンピューティング コンテキスト (データ サイエンス Deep Dive) におけるデータを分析します。

サーバー コンテキストを使用して複雑な R コードを実行する高速ことも、場合によってだけ方が便利ですのうち、データを取得する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]およびプライベート ワークステーションに分析します。

このセクションでは、ローカル計算コンテキストに切り替えて戻す方法、およびコンテキスト間でデータを移動してパフォーマンスを最適化する方法を説明します。

## <a name="create-a-local-summary"></a>ローカル サマリーを作成する

1. すべての作業をローカルに行うように計算コンテキストを変更します。
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からデータを抽出するときは、1 回の読み取りで抽出する行数を増やすとパフォーマンスが向上することがよくあります。  そのためには、データ ソースで *rowsPerRead* パラメーターの値を大きくします。
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```
  
    これまでは、 *rowsPerRead* の値は 5000 に設定されていました。
  
3. 今度は、新しいデータ ソースに対して **rxSummary** を呼び出します。
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
    実際の結果は rxSummary のコンテキストで実行したときと同じにする必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター。  ただし、処理は速くなる場合と遅くなる場合があります。 データは分析のためのローカル コンピューターに転送されるので、処理速度はデータベースへの接続に左右されます。


## <a name="next--step"></a>次の手順

[SQL Server と XDF ファイル間でデータを移動します。](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)

## <a name="previous-step"></a>前の手順

[RxDataStep を使用して、チャンキング分析を実行します。](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)


