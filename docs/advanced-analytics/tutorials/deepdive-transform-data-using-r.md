---
title: "R を使用するデータを変換 |Microsoft ドキュメント"
ms.custom: SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 0327e788-94cc-4a47-933b-7c5c027b9208
caps.latest.revision: "19"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ebc10cd4169f48956ab6b9a770b46c1c11cad6f3
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="transform-data-using-r"></a>R を使用するデータを変換します。

**RevoScaleR** パッケージは、分析のさまざまな段階でデータを変換するための複数の機能を提供します。

- **rxDataStep** を使用すると、データのサブセットを作成して変換できます。

- **rxImport** は、XDF ファイルまたはメモリ内のデータ フレームとの間でインポートされるデータの変換をサポートします。

- データ移動専用ではありませんが、 **rxSummary**、 **rxCube**、 **rxLinMod**、 **rxLogit** の各関数もすべてデータ変換をサポートします。

このセクションでは、これらの関数を使用する方法を説明します。 RxDataStep から始めましょう。

## <a name="use-rxdatastep-to-transform-variables"></a>rxDataStep を使用して変数を変換する

RxDataStep 関数は、一度に 1 つのデータ ソースからの読み取りと書き込み別に 1 つのデータ チャンクを処理します。 変換する列や読み込む変換などを指定できます。

この例を興味深いものにするため、別の R パッケージの関数を使用してデータを変換します。  **boot** パッケージは "推奨" パッケージの 1 つであり、**boot** は R のすべてのディストリビューションに含まれますが、起動時に自動的に読み込まれることはありません。 そのため、パッケージは、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで既に使用できるようになっています。

**ブート**パッケージ、関数を使用する`inv.logit`をクライアントの逆関数を計算します。 つまり、 `inv.logit` 関数はロジットを [0,1] のスケールで確率に変換します。

> [!TIP] 
> このスケールの予測を取得するもう 1 つの方法を設定すること、*型*パラメーターを**応答**rxPredict 元の呼び出しで。

1. まず、テーブル *ccScoreOutput*用のデータを保持するためのデータ ソースを作成します。
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. テーブル ccScoreOutput2 のデータを保持するための別のデータ ソースを追加します。
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    新しいテーブルでは、前の *ccScoreOutput* テーブルのすべての変数に加えて、新しく作成された変数を取得します。
  
3. 計算コンテキストを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに設定します。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. 関数 rxSqlServerTableExists を使用して確認するかどうか、出力テーブル*ccScoreOutput2*既に; が存在して、場合は、関数 rxSqlServerDropTable を使用してテーブルを削除します。
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")
    ```
  
5. RxDataStep 関数を呼び出すし、一覧で目的の変換を指定します。
  
    ```R
    rxDataStep(inData = sqlOutScoreDS,
        outFile = sqlOutScoreDS2,
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),
        transformPackages = "boot",
        overwrite = TRUE)
    ```

    各列に適用される変換を定義するときは、変換の実行に必要な追加の R パッケージも指定できます。  実行できる変換の種類の詳細については、「  [Transforming and Subsetting Data](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform)」 (データの変換およびサブセット化) を参照してください。
  
6. 新しいデータ セット内で変数の概要を表示する rxGetVarInfo を呼び出します。
  
    ```R
    rxGetVarInfo(sqlOutScoreDS2)
    ```

    **[結果]**
    
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

因子変数が文字データとしてテーブル *ccScoreOutput2* に書き込まれていることに注意してください。  以降の解析で因子として使用するには、 *colInfo* パラメーターを使用してレベルを指定します。

## <a name="next-step"></a>次の手順

[RxImport を使用しているメモリにデータを読み込む](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)

## <a name="previous-step"></a>前の手順

[作成し、R スクリプトを実行します。](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
