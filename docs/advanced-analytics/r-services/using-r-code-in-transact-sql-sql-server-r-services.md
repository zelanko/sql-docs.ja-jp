---
title: "SQL Server での R コードの使用 (SQL Server R Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/10/2017"
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
ms.assetid: 4e6fe30d-a105-4d5b-bc05-5e5204753847
caps.latest.revision: 36
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 28
---
# SQL Server での R コードの使用 (SQL Server R Services)
このチュートリアルでは、SQL Server R Services の R で使用できる簡単な構文例を紹介します。    
    
    
このチュートリアルは、SQL Server R Services を初めて使用する方で、T-SQL ストアド プロシージャで R スクリプトを定義する方法、入力としてデータを使用する方法、出力を定義する方法の基礎を理解したい場合にお勧めです。    
    
**前提条件:** SQL Server R Services で R コードを実行するには、R Services が既にインストールされている SQL Server のインスタンスに接続する必要があります。     
    
## パート 1 - 基本的な操作  

以降のセクションでは、パラメーターを追加してストアド プロシージャを拡張する方法と、入力と出力を構成する方法について説明します。   
  
### 1.1. R が SQL Server で動作するかどうかを確認する  

このクエリでは、システム ストアド プロシージャ [sp_execute_external_script](https://msdn.microsoft.com/library/mt604368.aspx) を使用し、SQL Server のコンテキストで R を呼び出します。 この例では、R への入力として SQL クエリを渡し、R はデータ フレームを SQL Server に返します。     
    
1. Windows の [スタート] メニューから、[Microsoft SQL Server Management Studio] を見つけます。     
2. 見つからない場合は、「[SQL Server Management Studio (SSMS) のダウンロード](https://msdn.microsoft.com/library/mt238290.aspx)」を参照し、インストールできます。    
3. **[サーバーに接続]** ダイアログ ボックスで、SQL Server R Services を有効にしたサーバーまたはインスタンスの名前を入力します。 これらの例では、新しいデータベースの作成、SELECT ステートメントの実行、テーブルの表示の権限があるアカウントを必ず使用してログインしてください。  すべてが動作していることを確認するには、新しい **[クエリ]** ウィンドウを開き、このステートメントに貼り付けます。    
    
    ```sql   
    exec sp_execute_external_script  
      @language =N'R',    
      @script=N'OutputDataSet<-InputDataSet',      
      @input_data_1 =N'select 1 as hello'    
      with result sets (([hello] int not null));    
    go    
    ```   
       
       
  
### <a name="bkmk_SSMSBasics"></a>1.2. 単純なテスト データを作成する  
    
複雑なデータ サイエンス ソリューションを開発する前に、SQL Server と R の違いを理解することが重要です。    
  
1. 次の T-SQL ステートメントを実行してデータの一時テーブルを作成します。     
   
    ```sql    
    CREATE TABLE #MyData ([Col1] int not null) ON [PRIMARY]    
    INSERT INTO #MyData   VALUES (1);    
    INSERT INTO #MyData   Values (10);    
    INSERT INTO #MyData   Values (100) ;    
    GO    
    ```    
5. テーブルが作成されたら、次のステートメントを使用してテーブルを照会します。  
    ```sql  
    SELECT * from #MyData  
    ```  

**[結果]**  
  
|Col1 |   
|----|   
|1|   
|10|   
|100|   
  
    
### 1.3. R スクリプトを使用してテスト データを取得する    
  
テーブルが作成されたら、次のステートメントを実行します。  
  
  ```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' OutputDataSet <- InputDataSet;'    
    , @input_data_1 = N' SELECT *  FROM #MyData;'    
    WITH RESULT SETS (([NewColName] int NOT NULL));
  ```    
    
新しい列名で同じ値が返されます。  
  
**注**    
- *@language* パラメーターでは、呼び出す言語拡張機能 (この例では R) を定義します。    
- *@script* パラメーターでは、Unicode テキストとして R ランタイムに渡すコマンドを定義します。 型 **nvarchar** の変数にテキストを追加して、その変数を呼び出すこともできます。    
- 行 `N'OutputDataSet <- InputDataSet;'` は、既定の変数名 **InputDataSet** に含まれている入力データを R に渡し、その後の操作なしで結果に戻ります。 R では大文字と小文字が区別されるため、入力と出力の変数名について、大文字と小文字を含め正確に指定する必要があります。不正確な場合、エラーが発生します。    
   
    
別の入力変数または出力変数を指定するには、*@input_data_1_name* パラメーターを使用し、有効な SQL 識別子を入力します。 たとえば、この例では出力と入力の変数名がそれぞれ *SQLOut* と *SQLIn* に変更されています。    
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' SQLOut <- SQLIn;'    
    , @input_data_1 = N' SELECT 12 as Col;'    
    , @input_data_1_name  = N'SQLIn'    
    , @output_data_1_name =  N'SQLOut'    
    WITH RESULT SETS (([NewColName] int NOT NULL));    
```    
    
**注**    
- 省略可能なパラメーターの *@input_data_1_name* と *@output_data_1_name* を使用するには、必須のパラメーター *@input_data_1* と *@output_data_1* を先に指定する必要があります。    
- SQL と R は同じデータ型をサポートしていないため、SQL Server から R、またはその逆方向にデータを送信する場合、型変換が頻繁に実行されます。 詳細については、「[R データ型の処理](../../advanced-analytics/r-services/working-with-r-data-types.md)」を参照してください。    
- パラメーターとして渡すことができるのは、1 つの入力データセットのみです。また、1 つのデータセットのみを返すことができます。 ただし、R コード内から他のデータセットを呼び出し、データセットに加えて他の型の出力を返すことができます。 また、OUTPUT キーワードを任意のパラメーターに追加して、その結果を受け取ることもできます。      
- 返されたデータセットのスキーマ (R data.frame) は、`WITH RESULT SETS` ステートメントで定義されます。 これを省略するとどうなるかを見てみましょう。    
- 表形式の結果が **[値]** ペインで返されます。 R ランタイムから返されたメッセージは、**[メッセージ]** に表示されます。     
  
### 1.4. R を使用して結果を生成する    
    
R スクリプトだけを使用して値を生成し、_@input_data_1_ の入力クエリ文字列は空白のままにすることもできます。 または、有効な SQL SELECT ステートメントをプレースホルダーとして使用して、SQL の結果を R スクリプトで使用しないこともできます。    
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' mytextvariable <- c("hello", " ", "world");    
                         OutputDataSet <- as.data.frame(mytextvariable);'    
    , @input_data_1 = N' SELECT 1 as Temp1'    
    WITH RESULT SETS (([col] char(20) NOT NULL));    
```    
    
**[結果]**    
    
    
 |*col* |    
 |-----|    
 |*hello*|    
 |     |    
 |*world*|    
    

上に示した Hello World の例の別のバージョンも試してみましょう。     
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' OutputDataSet<- data.frame(c("hello"), " ", c("world"));'    
    , @input_data_1 = N'  '    
    WITH RESULT SETS (([col1] varchar(20) , [col2] char(1), [col3] varchar(20) ));    
```    
    
    
**[結果]**    
    
    
 |*col1* | *col2* | *col3*|    
 |-------|-------|-------    
 |*hello*|  |*world*|    
    
どちらのステートメントも、3 つの値のベクトルを作成しますが、2 番目の例では 3 つの列に単一の行を返し、最初の例では単一の列に 3 つの行を返しています。 なぜでしょうか。
    
R には、ベクトル、マトリックス、配列、一覧という値の列を操作する方法が多数用意されているためです。 これらの操作は、強力で柔軟ですが、SQL 開発者の期待に必ずしも添うものではありません。  一部の R 関数は一覧およびマトリックスに対して暗黙的なデータ オブジェクトの変換を実行します。

> [!TIP] 
> 
> 必ず結果を検証し、R コードから返されるデータの列数と、結果のデータ型を確認してください。    
>     
> R コードで使用されるのが、マトリックスか、ベクトルか、またはそれ以外のデータ構造かに関わらず、R スクリプトからストアド プロシージャに出力される結果は必ず **data.frame** になることを覚えておいてください。      
  
  
## パート 2 - データ変換とその他の問題  
  
ここでは、SQL Server で R コードを実行する場合に注意すべき問題についての概要を説明します。  
  
+ データ型: キャストと変換のオプションだけでなく、暗黙的な変換についても理解します。  
+ 表形式の結果セット: R でデータの列と行を変更する方法を予測します。    
  
### 2.1 データ型の暗黙的な強制変換  
    
R と SQL Server は同じデータ型を使用しないので、R とデータベース間でデータを移行するときの制限事項について注意する必要があります。 次の例では、いくつかの一般的な問題について説明します。   
    
    
1. 次のステートメントを実行して、R を使用したマトリックス乗算を実行します。このスクリプトでは、3 つの値の単一の列が 1 列のマトリックスに変換されます。  次に、R は 2 つ目の変数 `y` を暗黙的に 1 列のマトリックスに変換し、2 つの引数が一致するようにします。  
    
    ```sql    
    execute sp_execute_external_script    
      @language = N'R'    
      , @script = N'    
        x <- as.matrix(InputDataSet);    
        y <- array(12:15);    
      OutputDataSet <- as.data.frame(x %*% y);'    
     , @input_data_1 = N' SELECT [Col1]  from #MyData;'    
      WITH RESULT SETS (([Col1] int, [Col2] int, [Col3] int, Col4 int));    
    ```    
**[結果]**

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|12|13|14|15|
|120|130|140|150|
|1200|1300|1400|1500|
 
  
      
2. 類似する次のスクリプトを実行し、配列の長さが変わると何が起こるかを確認します。 
   
    ```sql    
    execute sp_execute_external_script    
      @language = N'R'    
      , @script = N'    
        x <- as.matrix(InputDataSet);    
        y <- array(12:14);    
      OutputDataSet <- as.data.frame(y %*% x);'    
      , @input_data_1 = N' SELECT [Col1]  from #MyData;'    
      WITH RESULT SETS (([Col1] int ));    
    ```    

**[結果]**    
    
|Col1|
|---|    
|1542|    
  
  今回、R は、結果として 1 つの値を返します。 この結果は、2 つの引数が同じ長さのベクトルなので有効です。そのため、R は内部製品をマトリックスとして返します。    
    
   
  
### 2.2 異なる長さの列の結合または乗算    
    
  
次のスクリプトは、データベース開発者の期待に添わない可能性がある、R のいくつかの動作を示しています。   
  
このスクリプトでは、長さが 6 の新しい数値配列を定義し、R 変数 `df1` に格納します。 数値配列は、3 つの値を含む #MyData テーブルの整数と組み合わされ、新しいデータ フレーム `df2` が作成されます。   
    
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N'    
               df1 <- as.data.frame( array(1:6) );    
               df2 <- as.data.frame( c( InputDataSet , df1 ));    
               OutputDataSet <- df2'    
    , @input_data_1 = N' SELECT [Col1]  from #MyData;'    
    WITH RESULT SETS (( [Col2] int not null, [Col3] int not null ));    
```    
    
**[結果]**    
    
|*Col2*|*Col3*|    
|----|----|    
|1|1|    
|10|2|    
|100|3|    
|1|4|    
|10|5|    
|100|6|    
    
R には、表形式の出力を作成する関数が多数ありますが、R データベース オブジェクトによっては、値に対してまったく異なる操作を実行できます。 この [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャには、入力と出力の両方を data.frame として渡す必要があるため、データ フレームの行列の変換に頻繁に関数を使用することになります。    
    
使用されている R データ オブジェクトについて疑問がある場合は、R `str()` 関数または識別関数 (`is.matrix`、`is.vector` など) のいずれかを追加して、結果を確認し、実際のスキーマと値の型を取得します。    
  
  
詳細については、Hadley Wickham が書いた [R データ構造](http://adv-r.had.co.nz/Data-structures.html)に関する記事を参照してください。    
    
### 2.3 データ型の識別とスキーマの検証   
R コードから返される正確な列数と、各列のデータ型を把握することは重要です。     
    
  
R スクリプトで関数 `str()` を使用して、情報メッセージとして R オブジェクトのデータ スキーマを返すことができます。 

たとえば、次のステートメントは、#MyData テーブルのスキーマを返します。    
        
```sql    
    execute sp_execute_external_script    
      @language = N'R'    
    , @script = N' str(InputDataSet);'    
    , @input_data_1 = N' SELECT *  FROM #MyData;'    
      WITH RESULT SETS undefined;    
```    
    
    
**[結果]**    
    
*STDOUT message (s) from external script:*    
*'data.frame': 3 obs. of 1 variable:*    
*STDOUT message (s) from external script:*    
*$ Col1: int 1   10   100*    
    
  
  
### 2.4 キャスト列または変換列   
  
SQL Server から R にデータを送信するときに、適切にデータが処理されるように、データ型をキャストまたは変換することはよくあります。    
  
R コードに対する入力して SQL クエリを使用する場合、複数のデータ変換が実行されます。    
- SQL Server は、Launchpad サービスで管理される R プロセスにクエリのデータをプッシュし、内部表現に変換します。    
- R ランタイムはデータを data.frame 変数に読み込み、データに対する操作を実行します。    
- データベース エンジンは、Management Studio や他の SQL Server データ型を使用するクライアントにデータを返します。  
    
1. AdventureWorksDW データ ウェアハウスに対して次のクエリを実行します。 この入力データ クエリで、予測を作成するときに使用する売上データのテーブルを定義します。   
  
    ```sql    
    execute sp_execute_external_script    
       @language = N'R'    
      , @script = N' str(InputDataSet);'    
      , @input_data_1 = N'
           SELECT ReportingDate    
         , CAST(ModelRegion as varchar(50)) as ProductSeries    
         , Amount    
           FROM [AdventureworksDW2016CTP3].[dbo].[vTimeSeries]     
           WHERE [ModelRegion] = ''M200 Europe''    
           ORDER BY ReportingDate ASC ;'    
        WITH RESULT SETS undefined;    
    ```    
  
2. `str` 関数の結果を見て、R が入力データをどのように処理したかを確認します。
      
**[結果]**    
    
  *STDOUT message(s) from external script: 'data.frame':    37 obs. of  3 variables:*    
  *STDOUT message(s) from external script: $ ReportingDate: POSIXct, format: "2010-12-24 23:00:00" "2010-12-24 23:00:00"*    
  *STDOUT message(s) from external script: $ ProductSeries: Factor w/ 1 levels "M200 Europe",..: 1 1 1 1 1 1 1 1 1 1 ...*    
  *STDOUT message(s) from external script: $ Amount       : num  3400 16925 20350 16950 16950*    
    
    
**注**    
    
- 一部の SQL Server のデータ型は R でサポートされていません。そのため、エラーを防ぐために、個別に列を指定し、一部の列をキャストすることをお勧めします。    
- WHERE 句に predicate という文字列を含める場合、単一引用符で囲む必要があります。    
- datetime 列は R データ型 **POSIXct** として返されました。    
- 列 [ProductSeries] は **factor** として (正しく) 識別されました。    
     
  
### 2.5 複数の入力を使用する   
1 つのパラメーターで渡すことができるのは、1 つの入力データセットのみです。 ただし、内部の R コードから、RODBC を使用して他のデータセットを呼び出すことはできます。     
  
たとえば、次のサンプルでは、SELECT ステートメントでデータを指定して、RODBC パッケージに対する呼び出しを実行しています。    
    
```sql    
    @script = N' 
       <other R code here>;    
       library(RODBC);    
       connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");        dbhandle <- odbcDriverConnect(connStr)    
       OutputDataSet <- sqlQuery(dbhandle, "SELECT * from <table_name>");    
       <more R code combining the data>'    
```

参照や要因の一覧などの小さいデータセットを取得する場合は RODBC を使用し、モデルのトレーニングで使用するような大きなデータセットを SQL Server から取得する場合は@input_data パラメーターを使用することをお勧めします。 


### 2.6 複数の出力を生成する

SQL Server 2016 では、ストアド プロシージャ sp_execute_external_script からの R の出力は、1 つの data.frame またはデータセットに制限されています (この制限は、将来的に削除される可能性があります)。   
ただし、データセットに加え、他の型の出力を返すことはできます。 たとえば、入力として 1 つのデータセットを使用し、出力として統計情報のテーブルに加え、オブジェクトとしてトレーニングされたモデルを返すモデルをトレーニングすることができます。    
    
さらに、`OUTPUT` キーワードを任意の入力パラメーターに追加して、その結果を受け取ることもできます。   
    
### 2.7 並列処理    
    
大規模なデータセットと、並列クエリ計画を生成するような SQL クエリを操作する場合、*@parallel* パラメーターを 1 に設定することで、R スクリプトを並列実行することができます。 並列処理は、大量の結果セットをスコアリングする場合に特に便利です。 この方法を使用する場合、WITH RESULT SETS を使用して事前に出力結果スキーマを指定する必要があります。    
    
ただし、すべての行を使用するモデルをトレーニングする必要がある場合、このパラメーターは何の影響もありません。そのため、**ScaleR** パッケージを使用することをお勧めします。 これらのパッケージは処理を自動的に分散することができます。sp_execute_external_script の呼び出しで *@parallel =1* を指定する必要はありません。    
    
      
  
## パート 3 - ストアド プロシージャで R 関数をラップする  
  
R は、T-SQL で再現すると複雑なコードが必要になる、高度な統計関数を多数実行することができます。  ただし、R Services では次のようなタスクをサポートする R ユーティリティ スクリプトをストアド プロシージャで実行できます。   
    
- R の数学関数と統計関数を SQL Server データに適用する    
    
- R コードを使用するテーブル値関数またはスカラー関数を作成する    
     

 通常、こうした R 関数の呼び出しは、パラメーターに渡しやすくするため、ストアド プロシージャでカプセル化されます。 このプロセスを説明するため、同じ関数が R コード、sp_execute_external_script に対するアドホックのストアド プロシージャ呼び出し、R 関数のパラメーター化で使用できるストアド プロシージャで提供されています。
 
      
### 3.1. ランダムな数値を生成する  
  
次のステートメントは、`stats` パッケージの R 関数の 1 つを使用します。このパッケージは R Services のインストール時に既定で読み込まれます。 次の `rnorm` 関数で、正規分布で平均値が 100 のランダムな数値が 20 個生成されます。    

処理を行う R コードを次に示します。

```r
as.data.frame(rnorm(20, mean = 100));
```

このステートメントは、T-SQL から関数を呼び出し、SQL Server に結果を出力します。  
   
```sql    
EXEC sp_execute_external_script    
      @language = N'R'    
    , @script = N' 
         OutputDataSet <- as.data.frame(rnorm(20, mean = 100));'    
    , @input_data_1 = N'   ;'    
      WITH RESULT SETS (([Density] float NOT NULL));    
```    

次に、パラメーターに渡しやすくするため、このストアド プロシージャを別のストアド プロシージャにラップします。 _@params_ 引数にそれぞれの入力パラメーターを定義し、各パラメーターを名前ごとに対応する R パラメーターにラップする必要があります。

```sql
CREATE PROCEDURE MyRNorm (@mynorm int, @mymean int)
AS
    EXEC sp_execute_external_script    
      @language = N'R'    
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynorm, mymean));'    
    , @input_data_1 = N'   ;' 
    , @params = N' @mynorm int, @mymean int'  
    , @mynorm = @mynorm
    , @mymean = @mymean
    WITH RESULT SETS (([Density] float NOT NULL));    
```

新しいストアド プロシージャを呼び出して、値を渡します。

```sql
exec MyRNorm @mynorm = 20,@mymean = 100
```  
    
### 3.2 R ユーティリティ関数のその他の使用  
  
この例では、R ユーティリティ パッケージの 1 つを呼び出し、`memory.limit()` 関数を使用して、現在の環境のメモリを取得します。 `utils` パッケージは既定でインストールされますが、読み込まれません。    
    
```sql    
execute sp_execute_external_script    
      @language = N'R'    
    , @script = N'    
        library(utils);    
        mymemory <- memory.limit();    
        OutputDataSet <- as.data.frame(mymemory);'    
    , @input_data_1 = N' ;'    
     WITH RESULT SETS (([Col1] int not null));    
```    

次の例では、R の .Machine 関数を使用して現在のコンピューターでサポートされる整数の最大長を取得し、コンソールに出力しています。

```R
localmax <- .Machine$integer.max;
localmax;
```

```sql
execute sp_execute_external_script
  @language = N'R'
  , @script = N'
      localmax <- .Machine$integer.max;
      OutputDataSet <- as.data.frame(localmax);'
  , @input_data_1 = N'select [Col1]  from #MyData;'
  WITH RESULT SETS (([MaxIntValue] int not null));
```     
    
ただし、常に R での処理が適しているわけではありません。 データ サイエンティストが R で従来から実行している一部の処理では、SQL Server のセットベースの処理の方がはるかに効率的な場合もあります。R 関数と T-SQL のカスタム関数のパフォーマンスを比較した例は、「[Data Science End-to-End solution](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)」(データ サイエンスのエンドツーエンド ソリューション) を参照してください。 

特定の操作を実行する際に、R、T-SQL、または他のツールのいずれを使用するかを判断する場合は、ケースバイケースで評価することをお勧めします。    
    
    
    
### その他のリソース    
    
[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md): このチュートリアルでは、一般的なデータ サイエンス タスクを実地体験できます    
[データ サイエンスの詳細ソリューション](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md): このチュートリアルでは、SQL アプローチと R アプローチのバランスをとった開発プロセスと展開プロセスについて説明します       
[SQL Developer の高度な分析](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md): SQL Developer の完全なモデル操作分析について説明します     
    
    
    
    
