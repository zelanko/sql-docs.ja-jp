---
title: "レッスン 3: R を使用したデータの変換 (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
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
ms.assetid: 0327e788-94cc-4a47-933b-7c5c027b9208
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# レッスン 3: R を使用したデータの変換 (データ サイエンスの詳細情報)
**RevoScaleR** パッケージは、分析のさまざまな段階でデータを変換するための複数の機能を提供します。  
  
-   **rxDataStep** を使用すると、データのサブセットを作成して変換できます。  
  
-   **rxImport** は、XDF ファイルまたはメモリ内のデータ フレームとの間でインポートされるデータの変換をサポートします。  
  
-   データ移動専用ではありませんが、**rxSummary**、**rxCube**、**rxLinMod**、**rxLogit** の各関数もすべてデータ変換をサポートします。  
  
このセクションでは、これらの関数を使用する方法を説明します。 最初は *rxDataStep* です。  
  
## rxDataStep を使用して変数を変換する  
*rxDataStep* 関数は一度に 1 つのチャンクのデータを処理し、1 つのデータ ソースからデータを読み取って別のデータ ソースに書き込みます。 変換する列や読み込む変換などを指定できます。  
  
この例を興味深いものにするため、別の R パッケージの関数を使用してデータを変換します。  **boot** パッケージは "推奨" パッケージの 1 つであり、**boot** は R のすべてのディストリビューションに含まれますが、起動時に自動的に読み込まれることはありません。 そのため、パッケージは、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで既に使用できるようになっています。  
  
**boot** パッケージからは、ロジットの逆数を計算する、*inv.logit* 関数を使用します。 つまり、*inv.logit* 関数はロジットを [0,1] のスケールで確率に変換します。  
  
> [!TIP]  
> このスケールの予測を取得するもう 1 つの方法としては、*rxPredict* の元の呼び出しで *type* パラメーターを **response** に設定します。  
  
1.  まず、テーブル *ccScoreOutput* 用のデータを保持するためのデータ ソースを作成します。  
  
    ```R  
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )  
  
    ```  
  
2.  テーブル ccScoreOutput2 のデータを保持するための別のデータ ソースを追加します。  
  
    ```R  
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )  
  
    ```  
  
    新しいテーブルでは、前の *ccScoreOutput* テーブルのすべての変数に加えて、新しく作成された変数を取得します。  
  
3.  計算コンテキストを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに設定します。  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
  
    ```  
  
4.  *rxSqlServerTableExists* 関数を使用して、出力テーブル *ccScoreOutput2* が既に存在するかどうかを確認します。存在する場合は、*rxSqlServerDropTable* 関数を使用してテーブルを削除します。  
  
    ```R    
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")  
  
    ```  
  
5.  *rxDataStep* 関数を呼び出して、一覧で目的の変換を指定します。  
  
    ```R  
    rxDataStep(inData = sqlOutScoreDS,   
        outFile = sqlOutScoreDS2,         
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),        
        transformPackages = "boot",   
        overwrite = TRUE)    
    ```  
  
    各列に適用される変換を定義するときは、変換の実行に必要な追加の R パッケージも指定できます。  実行できる変換の種類の詳細については、「[Transforming and Subsetting Data](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform)」 (データの変換およびサブセット化) を参照してください。
  
6.  *rxGetVarInfo* を呼び出して、新しいデータ セットの変数の概要を表示します。  
  
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
  
元のロジット スコアは保持されますが、新しい列の *ccFraudProb* が追加されており、ロジット スコアが 0 ～ 1 の値として表示されます。 

因子変数が文字データとしてテーブル *ccScoreOutput2* に書き込まれていることに注意してください。  以降の解析で因子として使用するには、*colInfo* パラメーターを使用してレベルを指定します。  

  
## 次の手順  
[rxImport を使用してメモリにデータを読み込む (データ サイエンス詳細情報)](../../advanced-analytics/r-services/load-data-into-memory-using-rximport-data-science-deep-dive.md)  
  
## 前の手順  
[レッスン 2: R スクリプトの作成と実行 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
  
  
