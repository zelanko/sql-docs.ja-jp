---
title: "sp_execute_external_script (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs: TSQL
helpviewer_keywords: sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d437e6e8d86aa648d9c6ef11a8ca04297cafbaf3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  外部の場所に引数として指定されたスクリプトを実行します。 スクリプトは、サポートされていると、登録済みの言語で記述する必要があります。 クエリ ツリーがによって制御されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と、ユーザーがクエリに任意の操作を実行できません。 実行する**sp_execute_external_script**、する必要がありますを使用してにまず外部スクリプトを有効にする、`sp_configure 'external scripts enabled', 1;`ステートメントです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_execute_external_script   
    @language = N'language,   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]   
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```  
  
## <a name="arguments"></a>引数  
 @language= N'*言語*'  
 スクリプト言語を示します。 *言語*は**sysname**です。  

 有効な値は `Python` または `R` です。 
  
 @script= N'*スクリプト*'  
 外部の言語のスクリプト リテラルまたは変数の入力として指定します。 *スクリプト*は**nvarchar (max)**です。  
  
 [ @input_data_1_name = N'*input_data_1_name*']  
 によって定義されたクエリを表すために使用する変数の名前を指定@input_data_1です。 外部のスクリプトで変数のデータ型は、言語に依存します。 R が発生した場合は、入力変数は、データ フレームです。 Python の場合は、入力が表形式でなければなりません。 *input_data_1_name*は**sysname**です。  
  
 既定値は、"InputDataSet"です。  
  
 [ @input_data_1 = N'*input_data_1*']  
 形式で外部のスクリプトで使用される入力データを指定します、[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。 *input_data_1*は**nvarchar (max)**です。  
  
 [ @output_data_1_name = N'*output_data_1_name*']  
 返されるデータを含む外部スクリプトで変数の名前を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアド プロシージャの呼び出しの完了時にします。 外部のスクリプトで変数のデータ型は、言語に依存します。 出力は、R の場合、データ フレームをする必要があります。 出力は、Python の場合、パンダ データ フレームをする必要があります。 *output_data_1_name*は**sysname**です。  
  
 既定値は、"OutputDataSet"です。  
  
 [ @parallel = 0 | 1 ]  
 R スクリプトの並列実行を有効に設定して、`@parallel`パラメーターを 1 です。 このパラメーターの既定は 0 (並列処理です)。  
  
 R スクリプトを使用して、RevoScaleR 関数を使用しないため、`@parallel`パラメーターは、スクリプトは普通並列化できると仮定した場合、大規模なデータセットの処理のパフォーマンスを向上できます。 たとえば、R を使用して`predict`関数は、新しい予測を生成するようにモデルを`@parallel = 1`クエリ エンジンへのヒントとして。 よると行を分散クエリを並列化できる場合、 **MAXDOP**設定します。  
  
 場合`@parallel = 1`し、出力は、クライアント マシンに直接ストリーミング中、`WITH RESULTS SETS`句は必須であり、出力スキーマを指定する必要があります。  
  
 RevoScaleR 関数を使用する R スクリプトには、並列処理は自動的に処理し、指定しないで`@parallel = 1`を**sp_execute_external_script**呼び出します。  
  
 [ @params = N' *@parameter_name data_type* [アウト |出力] [、.. .n]']  
 外部のスクリプトで使用される入力パラメーターの宣言の一覧。  
  
 [ @parameter1 = '*value1*' [アウト |出力] [、.. .n]  
 外部のスクリプトで使用される入力パラメーターの値の一覧。  


## <a name="remarks"></a>解説  
 **sp_execute_external_script** を使用して、R. などのサポートされている言語で記述されたスクリプトを実行します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] と共にインストールされるサーバーのコンポーネントと、ワークステーションのツールと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の高パフォーマンスの環境にデータ サイエンティストを接続する接続ライブラリのセットから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は構成されます。 R Services (In-database) をインストール中に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を R スクリプトの実行を有効に設定します。 詳細については、次を参照してください。 [SQL Server R Services &#40;データベースで"&"#41 です。 セットアップ](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)です。  
  
 外部リソース プールを構成することによって、外部スクリプトで使用したリソースを制御できます。 詳細については、「[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)」を参照してください。 ワークロードに関する情報は、リソース ガバナーのカタログ ビュー、DMV のカウンターから取得できます。 詳細については、次を参照してください。[リソース ガバナーのカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)、[リソース ガバナー関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)、および[SQL Server、外部のスクリプト オブジェクト](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)です。  

モニターの実行を使用してスクリプト[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)と[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)です。 

 既定は、このストアド プロシージャによって返される結果セットは、名前のない列と出力をされます。 スクリプト内で使用する列名は、スクリプト環境をローカルであり、出力される結果セットには反映されません。 結果セットの列を使用、`WITH RESULTS SET`の句[ `EXECUTE`](../../t-sql/language-elements/execute-transact-sql.md)です。
  
 結果セットを返すだけでなく、R スクリプトからスカラー値を返すことができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]出力パラメーターを使用します。 次の例は、出力パラメーターの使用方法を示しています。  
  
```  
DECLARE @model varbinary(max);  
EXEC sp_execute_external_script  
        @language = N'R'  
        , @script = N'  
    # build classification model to predict tipped or not  
    logitObj <- glm(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource, family = binomial(link=logit));  
  
    # First, serialize a model and put it into a database table  
    modelbin <- serialize(logitObj, NULL);  
    '  
        , @input_data_1 = N'  
SELECT tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance  
  FROM dbo.nyctaxi_sample TABLESAMPLE (1 PERCENT) REPEATABLE (98074)  
  CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d  
'  
        , @input_data_1_name = N'featureDataSource'  
        , @params = N'@modelbin varbinary(max) OUTPUT'  
        , @modelbin = @model OUTPUT;  
```  


## <a name="streaming-execution-for-r-script"></a>R スクリプトの実行 (ストリーミング)  
 指定して R スクリプトの実行のストリーミングがサポートされている`@r_rowsPerRead int parameter`で`@params`コレクション。  ストリーミングではメモリに収まらないデータを操作する R スクリプト。 たとえばを使用してスコア付け十億行がある場合は、予測関数、新しい`@r_rowsPerRead`パラメーターは、一度に 1 つのストリームに、実行の分割を使用することができます。 このパラメーターは、R のプロセスに送信される行の数を制御するため、同時に読み取られる行の数を制限するも使用できます。 これに場合、たとえば、大規模なモデルのトレーニング中は、サーバー パフォーマンスの問題を軽減するために役立ちます。 このパラメーターは、R スクリプトの出力が読み取りまたは行のセット全体を見るに依存しない場合にのみ使用されることに注意してください。  
  
 両方の`@r_rowsPerRead`ストリーミング用のパラメーターと`@parallel`引数にヒントを考慮する必要があります。 ヒントを適用するには、並列処理を含む SQL クエリ プランを生成する場合があります。 これが可能でない場合、並列処理を有効にすることはできません。  
  
> [!NOTE]  
>  ストリーミングおよび並列処理は、Enterprise Edition でのみサポートされます。 、エラーが発生せず、Standard Edition で、クエリでパラメーターを含めることができますが、パラメーターなし効果や R のスクリプトを 1 つのプロセスで実行します。  
  
## <a name="restrictions"></a>制限  
 **データ型:**入力クエリまたはのパラメーターで使用すると、次のデータ型はサポートされていません`sp_execute_external_script`プロシージャ、およびサポートされていない型エラーの戻り値。  
  
 この問題を回避するには、**キャスト**列または値でサポートされている型[!INCLUDE[tsql](../../includes/tsql-md.md)]R. に送信します  
  
-   **カーソル (cursor)**  
  
-   **timestamp**  
  
-   **datetime2**、 **datetimeoffset**、**時間**  
  
-   **sql_variant**  
  
-   **テキスト**、**イメージ**  
  
-   **xml**  
  
-   **hierarchyid**、 **geometry**、 **geography**  
  
-   CLR ユーザー定義型  
  
 **datetime**入力内の値は、R 側 R. のためには、このことが必要では値の許容範囲に収まらないの値に"na"に変換されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]R 言語ではサポートされているより値の範囲が広いを許可します。  
  
 浮動小数点数の値 (例では、+、Inf、-inf、NaN) でサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合でも、両方の言語は、IEEE 754 を使用します。 現在の動作は、値を送信するだけ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]直接と結果の sqlclient に[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]エラーをスローします。 これらの値に変換**NULL**です。  
  
 任意の R 結果セットにマップすることはできません、[!INCLUDE[tsql](../../includes/tsql-md.md)]データ型は、NULL として出力します。  
  
## <a name="permissions"></a>Permissions  
 必要があります**EXECUTE ANY EXTERNAL SCRIPT**データベース権限です。  
  
## <a name="examples"></a>使用例  
 このセクションには、このストアド プロシージャを使用してを使用して R スクリプトを実行する方法の例が含まれています。[!INCLUDE[tsql](../../includes/tsql-md.md)]です。  
  
### <a name="a-return-a-data-set-from-r-to-sql-server"></a>A. R からには、SQL Server のデータ セットを返す  
 次の例を使用するストアド プロシージャを作成する**sp_execute_external_script** R から、虹彩データセットを返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
```  
DROP PROC IF EXISTS get_iris_dataset;  
go  
CREATE PROC get_iris_dataset  
AS  
BEGIN  
 EXEC   sp_execute_external_script  
       @language = N'R'  
     , @script = N'iris_data <- iris;'  
     , @input_data_1 = N''  
     , @output_data_1_name = N'iris_data'  
     WITH RESULT SETS (("Sepal.Length" float not null,   
           "Sepal.Width" float not null,  
        "Petal.Length" float not null,   
        "Petal.Width" float not null, "Species" varchar(100)));  
END;  
go  
```  
  
### <a name="b-generate-a-model-based-on-data-from-sql-server"></a>B. SQL Server からのデータに基づくモデルを生成します。  
 次の例を使用するストアド プロシージャを作成する**sp_execute_external_script**を虹彩のモデルを生成し、モデルを返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!NOTE]  
>  この例では、e1071 パッケージをインストールする必要があります。 詳細については、次を参照してください。 [SQL Server に追加の R パッケージのインストール](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)です。  
  
```  
DROP PROC IF EXISTS generate_iris_model;  
go  
  
CREATE PROC generate_iris_model  
AS  
BEGIN  
 EXEC sp_execute_external_script  
      @language = N'R'  
     , @script = N'  
          library(e1071);  
          irismodel <-naiveBayes(iris_data[,1:4], iris_data[,5]);  
          trained_model <- data.frame(payload = as.raw(serialize(irismodel, connection=NULL)));  
'  
     , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from iris_data'  
     , @input_data_1_name = N'iris_data'  
     , @output_data_1_name = N'trained_model'  
    WITH RESULT SETS ((model varbinary(max)));  
END;  
go  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Python ライブラリとデータ型](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [R ライブラリと R データ型](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [SQL Server R サービス](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [SQL Server R Services の既知の問題](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [外部ライブラリ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare と #40 です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [SQL Server のExternal Scripts オブジェクト](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
  
