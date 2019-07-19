---
title: クエリおよび RevoScaleR - SQL Server Machine Learning を使用してデータを SQL Server の変更
description: クエリおよび SQL Server で R 言語を使用してデータを変更する方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 35583815be7c89707efcf9bb31488cd80e3836e8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962189"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>クエリおよび SQL Server のデータ (SQL Server と RevoScaleR チュートリアル) を変更します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

データが読み込まれる前のレッスンで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 この手順で検証し、データを使用して変更**RevoScaleR**:

> [!div class="checklist"]
> * 変数に関する基本情報を返す
> * 生データからのカテゴリ データを作成します。

カテゴリのデータまたは*要因変数*は、探索的データの視覚化に役立ちます。 その操作は、次のようにどのような変数のデータを理解するのにヒストグラムへの入力として使用できます。

## <a name="query-for-columns-and-types"></a>列と型のクエリ

R スクリプトを実行するのに R IDE または RGui.exe を使用します。 

最初に、列とそのデータ型の一覧を取得します。 関数を使用する[rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf)し分析するデータ ソースを指定します。 バージョンによって**RevoScaleR**、使用することも[rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames)します。 
  
```R
rxGetVarInfo(data = sqlFraudDS)
```

**結果**

```R
Var 1: custID, Type: integer
Var 2: gender, Type: integer
Var 3: state, Type: integer
Var 4: cardholder, Type: integer
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: fraudRisk, Type: integer
```

## <a name="create-categorical-data"></a>カテゴリ データを作成します。

すべての変数は、整数として格納されますが、いくつかの変数と呼ばれるカテゴリのデータを表す*要因変数*r.たとえば、列*状態*50 の州およびコロンビア、識別子として使用する番号が含まれています。 データをわかりやすくするために、この数値を州の略称の一覧で置き換えます。

この手順で、省略形を含む文字列ベクトルを作成し、元の整数識別子をこれらのカテゴリ値をマップします。 新しい変数を使用して、 *colInfo*この列が係数として処理することを指定するための引数。 データを分析したり、移動したときに、省略形が使用され、列が係数として処理されます。

列を略称にマップしてから要因として使用すると、パフォーマンスも改善されます。 詳細については、次を参照してください。 [R とデータの最適化](../r/r-and-data-optimization-r-services.md)します。

1. R 変数を作成して開始*stateAbb*、し、次のように、追加する文字列のベクトルを定義します。
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. 次に、 *ccColInfo*という名前の列情報オブジェクトを作成します。このオブジェクトは、カテゴリ レベル (州の省略形) への既存の整数値のマッピングを指定します。
  
    このステートメントは、性別およびカード名義人の要因変数も作成します。
  
    ```R
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"),
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51),
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )
    ```
  
3. 作成する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]呼び出し、更新されたデータを使用するデータ ソース、 **RxSqlServerData**以前と同様に機能しますが、追加、 *colInfo*引数。
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - *table* パラメーターでは、先ほど作成したデータ ソースを含む変数 *sqlFraudTable*を渡します。
    - *colInfo* パラメーターでは、列のデータ型および要因レベルを含む変数 *ccColInfo* を渡します。

4.  以上の手順で、関数 **rxGetVarInfo** を使用して新しいデータ ソース内の変数を確認できるようになりました。
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **結果**
    
    ```R
    Var 1: custID, Type: integer
    Var 2: gender  2 factor levels: Male Female
    Var 3: state   51 factor levels: AK AL AR AZ CA ... VT WA WI WV WY
    Var 4: cardholder  2 factor levels: Principal Secondary
    Var 5: balance, Type: integer
    Var 6: numTrans, Type: integer
    Var 7: numIntlTrans, Type: integer
    Var 8: creditLine, Type: integer
    Var 9: fraudRisk, Type: integer
    ```

これで、指定した 3 つの変数 (*性別*、 *州*、および *カード名義人*) は要素として扱われます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [計算コンテキストの定義と使用](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)