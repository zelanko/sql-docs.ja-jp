---
title: "SQL Server データ (SQL と R deep dive) クエリや変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/14/2017
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
ms.assetid: 8c7007a9-9a8f-4dcd-8068-40060d4f6444
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 901ae76597dd9a9ab1136a35442cc27b6ea63e61
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="query-and-modify-the-sql-server-data-sql-and-r-deep-dive"></a>クエリおよび SQL Server のデータ (SQL と R deep dive) の変更
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

これで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にデータを読み込んだので、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]で R 関数への引数として作成したデータ ソースを使用して、変数に関する基本情報を取得したり、概要やヒストグラムを生成したりできます。

このステップでクイック分析を実行し、データを強化するには、データ ソースを再利用します。

## <a name="query-the-data"></a>データのクエリ

最初に、列とそのデータ型の一覧を取得します。

1.  関数を使用して[rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf)し分析するデータ ソースを指定します。

    RevoScaleR のバージョンによって、使用することも[rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames)です。 
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **結果**
    
    *Var 1: custID, Type: integer*
    
    *Var 2: gender, Type: integer*
    
    *Var 3: state, Type: integer*
    
    *Var 4: cardholder, Type: integer*
    
    *Var 5: balance, Type: integer*
    
    *Var 6: numTrans, Type: integer*
    
    *Var 7: numIntlTrans, Type: integer*
    
    *Var 8: creditLine, Type: integer*
    
    *Var 9: fraudRisk, Type: integer*


## <a name="modify-metadata"></a>メタデータを変更します。

すべての変数は整数として格納されますが、一部の変数はカテゴリ データ (R で *要因変数* と呼ばれる) を表します。たとえば、 *state* 列には、50 の州およびコロンビア特別区の識別子として使用される数値が含まれています。  データをわかりやすくするために、この数値を州の略称の一覧で置き換えます。

このステップではの省略形を含む文字列のベクトルを作成し、元の整数識別子をこれらのカテゴリの値をマップします。 新しい変数を使用して、 *colInfo*的要因としてこの列を処理することを指定の引数。 データを分析したり、移動したときに、列が、要素として処理され、省略形が使用されます。

列を略称にマップしてから要因として使用すると、パフォーマンスも改善されます。 詳細については、次を参照してください。 [R とデータの最適化](..\r\r-and-data-optimization-r-services.md)です。

1. まず、次のように R 変数 *stateAbb*を作成し、この変数に追加する文字列のベクトルを定義します。
  
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
  
3. 最新のデータを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースを作成するには、以前と同様に **RxSqlServerData** を呼び出しますが、今回は *colInfo* 引数を追加します。
  
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
    
    *Var 1: custID, Type: integer*
    
    *Var 2: 2 つの要素レベルの性別: 男性女性*
    
    *Var 3: state   51 factor levels: AK AL AR AZ CA ...VT WA WI WV WY*
    
    *Var 4: カード会員 2 要素のレベル: プリンシパル セカンダリ*
    
    *Var 5: balance, Type: integer*
    
    *Var 6: numTrans, Type: integer*
    
    *Var 7: numIntlTrans, Type: integer*
    
    *Var 8: creditLine, Type: integer*
    
    *Var 9: fraudRisk, Type: integer*

これで、指定した 3 つの変数 (_性別_、 _州_、および _カード名義人_) は要素として扱われます。

## <a name="next-step"></a>次の手順

[計算コンテキストの定義と使用](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)

## <a name="previous-step"></a>前の手順

[RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
