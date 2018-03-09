---
title: "(SQL と R deep dive) のローカル コンピューティング コンテキストでデータを分析 |Microsoft ドキュメント"
ms.date: 12/18/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- R
ms.assetid: 787bb526-4a13-40fa-9343-75d3bf5ba6a2
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 0cfdc4df8709d2aeb186681d3268c48b746ab858
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="analyze-data-in-local-compute-context-sql-and-r-deep-dive"></a>(SQL と R deep dive) のローカル コンピューティング コンテキストでのデータを分析します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

このセクションでは、ローカル コンピューティング コンテキストに戻すと、パフォーマンスを最適化するためにコンテキスト間でデータを移動する方法を学習します。

I は、サーバー コンテキストを使用して複雑な R コードを実行する高速になりますが、場合によってはのうち、データを取得する方が便利[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]およびローカルのワークステーションで分析します。

## <a name="create-a-local-summary"></a>ローカルの概要を作成します。

1. すべての作業をローカルに行うように計算コンテキストを変更します。
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からデータを抽出するときは、1 回の読み取りで抽出する行数を増やすとパフォーマンスが向上することがよくあります。  そのためには、データ ソースで *rowsPerRead* パラメーターの値を大きくします。 これまでは、 *rowsPerRead* の値は 5000 に設定されていました。
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. 呼び出す**rxSummary**新しいデータ ソースにします。
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
    実際の結果は、 **コンピューターのコンテキストで** rxSummary [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行した場合と同じになるはずです。  ただし、処理は速くなる場合と遅くなる場合があります。 データは分析のためのローカル コンピューターに転送されるので、処理速度はデータベースへの接続に左右されます。

## <a name="next-step"></a>次の手順

[SQL Server と XDF ファイル間でデータを移動します。](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)

## <a name="previous-step"></a>前の手順

[rxDataStep を使用したチャンク分析の実行](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
