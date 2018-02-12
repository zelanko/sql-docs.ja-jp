---
title: "R (SQL と R deep dive) を使用するデータを変換 |Microsoft ドキュメント"
ms.date: 12/24/2017
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
ms.assetid: 0327e788-94cc-4a47-933b-7c5c027b9208
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: d3dbda505155cb8da1f192b2dc36a6889938ccde
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="transform-data-using-r-sql-and-r-deep-dive"></a>R (SQL と R deep dive) を使用するデータを変換します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

**RevoScaleR** パッケージは、分析のさまざまな段階でデータを変換するための複数の機能を提供します。

- **rxDataStep** を使用すると、データのサブセットを作成して変換できます。

- **rxImport** は、XDF ファイルまたはメモリ内のデータ フレームとの間でインポートされるデータの変換をサポートします。

- データ移動専用ではありませんが、 **rxSummary**、 **rxCube**、 **rxLinMod**、 **rxLogit** の各関数もすべてデータ変換をサポートします。

このセクションでは、これらの関数を使用する方法を学習します。 始めましょう[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep)です。

## <a name="use-rxdatastep-to-transform-variables"></a>RxDataStep を使用して変数を変換するには

**rxDataStep** 関数は一度に 1 つのチャンクのデータを処理し、1 つのデータ ソースからデータを読み取って別のデータ ソースに書き込みます。 変換する列や読み込む変換などを指定できます。

この例を興味深いにするためには、データを変換するのに別の R パッケージから関数を使用してみましょう。  **boot** パッケージは "推奨" パッケージの 1 つであり、 **boot** は R のすべてのディストリビューションに含まれますが、起動時に自動的に読み込まれることはありません。 そのため、パッケージは、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで既に使用できるようになっています。

**ブート**パッケージ、関数を使用して`inv.logit`をクライアントの逆関数を計算します。 つまり、 `inv.logit` 関数はロジットを [0,1] のスケールで確率に変換します。

> [!TIP] 
> このスケールの予測を取得するもう 1 つの方法を設定すること、*型*パラメーターを**応答**rxPredict 元の呼び出しで。

1. テーブルに送信されるデータを保持するデータ ソースを作成して開始`ccScoreOutput`です。
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. テーブルのデータを保持するために別のデータ ソースを追加`ccScoreOutput2`です。
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    新しいテーブルで、前のすべての変数を格納`ccScoreOutput`テーブルと新しく作成された変数です。
  
3. 計算コンテキストを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに設定します。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. 関数を使用して**rxSqlServerTableExists**を確認するかどうか、出力テーブル`ccScoreOutput2`既に; が存在する場合は、機能を使用**rxSqlServerDropTable**テーブルを削除します。
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")
    ```
  
5. **rxDataStep** 関数を呼び出して、一覧で目的の変換を指定します。
  
    ```R
    rxDataStep(inData = sqlOutScoreDS,
        outFile = sqlOutScoreDS2,
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),
        transformPackages = "boot",
        overwrite = TRUE)
    ```

    各列に適用される変換を定義するときは、変換の実行に必要な追加の R パッケージも指定できます。  実行できる変換の種類の詳細については、次を参照してください。 [RevoScaleR を使用してデータを変換およびサブセット方法](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform)です。
  
6. **rxGetVarInfo** を呼び出して、新しいデータ セットの変数の概要を表示します。
  
    ```R
    rxGetVarInfo(sqlOutScoreDS2)
    ```

    **結果**
    
    *Var 1: ccFraudLogitScore, Type: numeric*
    
    *Var 2: state, Type: character*
    
    *Var 3: gender, Type: character*
    
    *Var 4: cardholder, Type: character*
    
    *Var 5: balance, Type: integer*
    
    *Var 6: numTrans, Type: integer*
    
    *Var 7: numIntlTrans, Type: integer*
    
    *Var 8: creditLine, Type: integer*
    
    *Var 9: ccFraudProb, Type: numeric*

元のロジット スコアは保持されますが、新しい列の *ccFraudProb*が追加されており、ロジット スコアが 0 ～ 1 の値として表示されます。

要素変数は、テーブルに書き込まれていることを確認`ccScoreOutput2`文字データとして。 以降の解析で因子として使用するには、 *colInfo* パラメーターを使用してレベルを指定します。

## <a name="next-step"></a>次の手順

[rxImport を使用してメモリにデータを読み込む](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)

## <a name="previous-step"></a>前の手順

[R スクリプトの作成と実行](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
