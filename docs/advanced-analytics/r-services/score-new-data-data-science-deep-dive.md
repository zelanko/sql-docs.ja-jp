---
title: "新しいデータのスコア付け (データ サイエンスの詳細情報) | Microsoft Docs"
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
ms.assetid: 87056467-f67f-4d72-a83c-ac052736d85d
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# 新しいデータのスコア付け (データ サイエンスの詳細情報)
予測に利用できるモデルが与えられたので、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからそれにデータを入力し、いくつかの予測を生成します。  
  
## 新しいデータのスコア付け  
ロジスティック回帰モデル *logitObj* を使用して、同じ独立した変数を入力として使用する別のデータセットのスコアを作成します。  
  
> [!NOTE]  
> 手順の一部には、DDL 管理者特権が必要です。  
  
1.  以前にセットアップしたデータ ソースの *sqlScoreDS* を更新して、必要な列情報を追加します。  
  
    ```R  
    sqlScoreDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        table = sqlScoreTable,   
        colInfo = ccColInfo,   
        rowsPerRead = sqlRowsPerRead)    
    ```  
  
2.  結果が失われないように、新しいデータ ソース オブジェクトを作成します。このオブジェクトは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに新しいテーブルを作成する際に使用します。  
  
    ```R    
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",   
        connectionString = sqlConnString,   
        rowsPerRead = sqlRowsPerRead )    
    ```  
     この時点では、テーブルは作成されていません。 これはデータのコンテナーを定義するためだけのステートメントです。
     
3.  現在のコンピューティング コンテキストを確認し、必要に応じてコンピューティング コンテキストをサーバーに設定します。  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
  
4.  結果を生成する予測関数を実行する前に、既存の出力テーブルの存在を確認する必要があります。 出力テーブルが存在しない場合、新しいテーブルを記述するとき、エラーが表示されます。  
  
    この処理を実行するには、入力としてテーブル名を渡して、関数 *rxSqlServerTableExists* と *rxSqlServerDropTable* を呼び出します。  
  
    ```R  
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")   
    ```  
  
    -   関数 *rxSqlServerTableExists* は ODBC ドライバーに対してクエリを実行し、テーブルが存在する場合は TRUE、それ以外の場合は FALSE を返します。    
    -   関数 *rxSqlServerDropTable* は DDL を実行し、テーブルが正常にドロップされた場合は TRUE、それ以外の場合は FALSE を返します。   
  
5.  これで、*rxPredict* 関数を使用してスコアを作成し、データ ソース *sqlScoreDS* に定義した新しいテーブルに保存する準備が整いました。  
  
    ```R  
    rxPredict(modelObject = logitObj,   
        data = sqlScoreDS,        
        outData = sqlServerOutDS,     
        predVarNames = "ccFraudLogitScore",   
          type = "link",      
        writeModelVars = TRUE,        
        overwrite = TRUE)    
    ```  
  
    *rxPredict* 関数も、リモート計算コンテキストでの実行をサポートする関数です。 *rxLinMod*、*rxLogit*、または *rxGlm* を使用して作成したモデルからスコアを作成する場合に *rxPredict* 関数を使用できます。  
  
    -   ここで *writeModelVars* パラメーターは **TRUE** に設定されます。 これは見積もりに使用された変数が新しいテーブルに追加されることを意味します。  
  
    -   *predVarNames* パラメーターにより、結果が保存される変数が指定されます。 ここで、*ccFraudLogitScore* という新しい変数を渡します。  
  
    -   *rxPredict* の *type* パラメーターで、予測の計算方法を定義します。 キーワード **response** を指定し、応答変数のスケールに基づいてスコアを生成するか、キーワード **link** を使用し、基礎となるリンク関数に基づいてスコアを生成します。リンク関数に基づく場合、予測はロジスティック スケールになります。  

6. 少し時間をおいて Management Studio でテーブルの一覧を更新すると、新しいテーブルとそのデータを確認することができます。

7. その他の変数を出力の予測に追加するには、*extraVarsToWrite* 引数を使用します。  たとえば、次のコードの変数 *custID* は、スコアリング データ テーブルから予測の出力テーブルに追加されています。  
  
    ```R   
    rxPredict(modelObject = logitObj,    
            data = sqlScoreDS,        
            outData = sqlServerOutDS,     
            predVarNames = "ccFraudLogitScore",   
              type = "link",      
            writeModelVars = TRUE,        
            extraVarsToWrite = "custID",      
            overwrite = TRUE)    
    ```  
  
## ヒストグラムでスコアを表示する  
新しいテーブルが作成されたら、10,000 件の予測スコアのヒストグラムを計算し、表示します。 下限と上限を指定すると (データベースから取得し、作業中のデータに追加する)、計算が速くなります。  
  
1.  新しいデータ ソース *sqlMinMax* を作成します。データベースに対してクエリを実行し、下限と上限を取得するデータ ソースです。  
  
    ```R  
    sqlMinMax <- RxSqlServerData(  
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",   
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),   
        connectionString = sqlConnString)    
    ```  
     この例を見ると、*RxSqlServerData* データ ソース オブジェクトを使用して SQL クエリ、関数、またはストアド プロシージャに基づいて任意のデータセットを定義し、それを R コードで使用するのが簡単だということがわかります。 この変数には実際の値は格納されず、データ ソースの定義のみが格納されます。*rxImport* など関数で使用する場合にのみ、このクエリを実行して値を生成します。  
      
2.  *rxImport* 関数を呼び出して、計算コンテキスト全体で共有できるデータ フレームに値を置きます。  
  
    ```R  
    minMaxVals <- rxImport(sqlMinMax)   
    minMaxVals <- as.vector(unlist(minMaxVals))  
  
    ```  
     **[結果]**
 
     *> minMaxVals*
     
     *[1] -23.970256   9.786345*
  
3.  これで最大値と最小値が利用可能になりました。最大値と最小値を利用し、スコア データ ソースを作成します。  
  
    ```R  
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",    
        connectionString = sqlConnString,   
        rowsPerRead = sqlRowsPerRead,   
            colInfo = list(ccFraudLogitScore = list(   
                low = floor(minMaxVals[1]),    
                        high = ceiling(minMaxVals[2]) ) ) )  
  
    ```  

  
4.  最後に、スコア データ ソース オブジェクトを使用してスコアリング データを取得し、ヒストグラムを計算して表示します。 必要に応じて、計算コンテキストを設定するコードを追加してください。  
  
    ```R  
    # rxSetComputeContext(sqlCompute)   
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)  
  
    ```  
  
    **[結果]**  
  
    ![complex histogram created by R](../../advanced-analytics/r-services/media/rsql-sue-complex-histogram.png "complex histogram created by R")  
  
## 次の手順  
[レッスン 3: R を使用したデータの変換 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/lesson-3-transform-data-using-r-data-science-deep-dive.md)  
  
## 前の手順  
[モデルの作成 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/create-models-data-science-deep-dive.md)  
  
## 参照  
[データ サイエンスの詳細: 概要 (SQL Server R Services)](http://msdn.microsoft.com/library/mt637368(SQL.130).aspx)  
  
  
  
