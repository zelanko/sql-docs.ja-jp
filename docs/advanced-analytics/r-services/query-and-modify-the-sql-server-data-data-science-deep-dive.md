---
title: "SQL Server データに対するクエリおよび変更 (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
ms.assetid: 8c7007a9-9a8f-4dcd-8068-40060d4f6444
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# SQL Server データに対するクエリおよび変更 (データ サイエンスの詳細情報)
これで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にデータを読み込んだので、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で R 関数への引数として作成したデータ ソースを使用して、変数に関する基本情報を取得したり、概要やヒストグラムを生成したりできます。  
  
この手順では、データ ソースを再利用して、簡単な分析を実行し、データを強化します。  
  
## データのクエリ  
最初に、列とそのデータ型の一覧を取得します。  
  
1.  関数 *rxGetVarInfo* を使用し、分析するデータ ソースを指定します。  
  
    ```R  
    rxGetVarInfo(data = sqlFraudDS)   
    ```  
  
  
**[結果]**  
*Var 1: custID, Type: integer*  
*Var 2: gender, Type: integer*  
*Var 3: state, Type: integer*  
*Var 4: cardholder, Type: integer*  
*Var 5: balance, Type: integer*  
*Var 6: numTrans, Type: integer*  
*Var 7: numIntlTrans, Type: integer*  
*Var 8: creditLine, Type: integer*  
*Var 9: fraudRisk, Type: integer*  
  
## メタデータの変更  
すべての変数は整数として格納されますが、一部の変数はカテゴリ データ (R で*要因変数*と呼ばれる) を表します。たとえば、*state* 列には、50 の州およびコロンビア特別区の識別子として使用される数値が含まれています。  データをわかりやすくするために、この数値を州の略称の一覧で置き換えます。  
  
この手順では、略称を含む文字列ベクトルを用意し、そのカテゴリ値を元の整数の識別子にマップします。 この変数を用意したら、*colInfo* 引数で使用し、この列を要因として処理するように指定します。 以降、データの分析またはインポート時には、略称が使用され、列は要因として処理されるようになります。  
  
1.  まず、次のように R 変数 *stateAbb* を作成し、この変数に追加する文字列のベクトルを定義します。  
  
    ```R  
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",     
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",   
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",   
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",   
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")  
  
    ```  
  
2.  次に、*ccColInfo* という名前の列情報オブジェクトを作成します。このオブジェクトは、カテゴリ レベル (州の省略形) への既存の整数値のマッピングを指定します。  
  
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
  
3.  最新のデータを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースを作成するには、以前と同様に *RxSqlServerData* を呼び出しますが、今回は *colInfo* 引数を追加します。  
  
    ```R  
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,  
    table = sqlFraudTable, colInfo = ccColInfo,  
    rowsPerRead = sqlRowsPerRead)   
    ```  
  
    -   *table* パラメーターでは、先ほど作成したデータ ソースを含む変数 *sqlFraudTable* を渡します。    
    -   *colInfo* パラメーターでは、列のデータ型および要因レベルを含む変数 *ccColInfo* を渡します。
    -   列を略称にマップしてから要因として使用すると、パフォーマンスも改善されます。 詳細については、「[R とデータの最適化](https://msdn.microsoft.com/library/mt723575.aspx)」を参照してください。  
  
4.  以上の手順で、関数 *rxGetVarInfo* を使用して新しいデータ ソース内の変数を確認できるようになりました。  
  
    ```R  
    rxGetVarInfo(data = sqlFraudDS)   
    ```  
  
**[結果]**  
  
*Var 1: custID, Type: integer*  
*Var 2: gender       2 factor levels: Male Female*  
*Var 3: state       51 factor levels: AK AL AR AZ CA ...VT WA WI WV WY*  
*Var 4: cardholder       2 factor levels: Principal Secondary*  
*Var 5: balance, Type: integer*  
*Var 6: numTrans, Type: integer*  
*Var 7: numIntlTrans, Type: integer*  
*Var 8: creditLine, Type: integer*  
*Var 9: fraudRisk, Type: integer*  
  
これで、指定した 3 つの変数 (_性別_、_州_、および _カード名義人_) は要素として扱われます。  
  
## 次の手順  
[計算コンテキストの定義と使用 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/define-and-use-compute-contexts-data-science-deep-dive.md)  
  
## 前の手順  
[RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する](../../advanced-analytics/r-services/create-sql-server-data-objects-using-rxsqlserverdata.md)  
  
## 参照  
[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
