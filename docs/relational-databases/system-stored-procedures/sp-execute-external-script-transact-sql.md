---
title: sp_execute_external_script (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/22/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5660860a3a03a268b0903a0222753f1ea9bc5382
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263108"
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  外部の場所に引数として指定されたスクリプトを実行します。 スクリプトは、サポートされていると、登録済みの言語で記述する必要があります。 実行する**sp_execute_external_script**、ステートメントを使用して外部スクリプトを有効にする必要があります最初`sp_configure 'external scripts enabled', 1;`です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]   
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```

## <a name="arguments"></a>引数
 @language = N'*言語*'  
 スクリプト言語を示します。 *言語*は**sysname**です。  

 有効な値は `Python` または `R` です。 
  
 @script = N'*スクリプト*'  
 外部の言語のスクリプト リテラルまたは変数の入力として指定します。 *スクリプト*は**nvarchar (max)** です。  
  
 [ @input_data_1_name = N'*input_data_1_name*']  
 によって定義されたクエリを表すために使用する変数の名前を指定@input_data_1です。 外部のスクリプトで変数のデータ型は、言語に依存します。 R が発生した場合は、入力変数は、データ フレームです。 Python の場合は、入力が表形式でなければなりません。 *input_data_1_name*は**sysname**です。  
  
 既定値は`InputDataSet`します。  
  
 [ @input_data_1 = N'*input_data_1*']  
 形式で外部のスクリプトで使用される入力データを指定します、[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。 データ型*input_data_1*は**nvarchar (max)** です。
  
 [ @output_data_1_name =  N'*output_data_1_name*' ]  
 返されるデータを含む外部スクリプトで変数の名前を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアド プロシージャの呼び出しの完了時にします。 外部のスクリプトで変数のデータ型は、言語に依存します。 R、出力は、データ フレームをする必要があります。 Python、出力はパンダ データ フレームをする必要があります。 *output_data_1_name*は**sysname**です。  
  
 既定値は、"OutputDataSet"です。  
  
 [ @parallel = 0 | 1] の設定で R スクリプトの並列実行を有効にする、`@parallel`パラメーターを 1 です。 このパラメーターの既定は 0 (並列処理です)。  
  
 R スクリプトを使用して、RevoScaleR 関数を使用しないため、`@parallel`パラメーターは、スクリプトは普通並列化できると仮定した場合、大規模なデータセットの処理のパフォーマンスを向上できます。 たとえば、R を使用して`predict`関数は、新しい予測を生成するようにモデルを`@parallel = 1`クエリ エンジンへのヒントとして。 よると行を分散クエリを並列化できる場合、 **MAXDOP**設定します。  
  
 場合`@parallel = 1`し、出力は、クライアント マシンに直接ストリーミング中、`WITH RESULTS SETS`句は必須であり、出力スキーマを指定する必要があります。  
  
 RevoScaleR 関数を使用する R スクリプトには、並列処理は自動的に処理し、指定しないで`@parallel = 1`を**sp_execute_external_script**呼び出します。  
  
 [ @params = N' *@parameter_name data_type* [アウト |出力] [、.. .n]']  
 外部のスクリプトで使用される入力パラメーターの宣言の一覧。  
  
 [ @parameter1 = '*value1*'  [ OUT | OUTPUT ] [ ,...n ] ]  
 外部のスクリプトで使用される入力パラメーターの値の一覧。  

## <a name="remarks"></a>解説

使用して**sp_execute_external_script**サポートされている言語で記述されたスクリプトを実行します。 現時点では、サポートされる言語は、SQL Server 2016 および Python R と SQL Server 2017 の R はします。 

> [!IMPORTANT]
> クエリ ツリーがによって制御されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と、ユーザーがクエリに任意の操作を実行できません。 

既定は、このストアド プロシージャによって返される結果セットは、名前のない列と出力をされます。 スクリプト内で使用する列名は、スクリプト環境をローカルであり、出力される結果セットには反映されません。 結果セットの列を使用、`WITH RESULTS SET`の句[ `EXECUTE`](../../t-sql/language-elements/execute-transact-sql.md)です。
  
 結果セットを返すだけでなく、スカラー値を返すことができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]出力パラメーターを使用しています。 次の例は、スクリプトへの入力として使用されたシリアル化された R モデルを返す出力パラメーターの使用方法を示しています。  

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]と共にインストールされるサーバー コンポーネントから成ります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、およびワークステーションのツールとの高パフォーマンスの環境にデータ サイエンティストを接続する接続ライブラリのセット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 機械学習中にコンポーネントをインストールする必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を外部スクリプトの実行を有効に設定します。 詳細については、次を参照してください。 [SQL Server マシン ラーニング Services セットアップ](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)です。  
  
外部リソース プールを構成することによって、外部スクリプトで使用したリソースを制御できます。 詳細については、「[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)」を参照してください。 ワークロードに関する情報は、リソース ガバナーのカタログ ビュー、DMV のカウンターから取得できます。 詳細については、次を参照してください[リソース ガバナーのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)、[リソース ガバナー関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)、および。[SQL Server、外部のスクリプト オブジェクト](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)です。  

モニターの実行を使用してスクリプト[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)と[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)です。 

## <a name="streaming-execution-for-r-and-python-scripts"></a>R と Python スクリプトの実行 (ストリーミング)  

ストリーミングでは、R または Python スクリプト メモリに収まりきらない場合、詳細データを操作します。 ストリーミング中に渡される行の数を制御するには、パラメーターには、整数値を指定`@r_rowsPerRead`で、`@params`コレクション。  たとえば、非常に全体のデータを使用するモデルをトレーニングは、データの 1 つのチャンク内のすべての行を送信できることを確認するより少ない行を読み取る値を調整するでした。 このパラメーターを使用して、読み取りし、サーバー パフォーマンスの問題を軽減するために同時に処理される行の数を管理することもできます。 
  
両方の`@r_rowsPerRead`ストリーミング用のパラメーターと`@parallel`引数にヒントを考慮する必要があります。 ヒントを適用するには、並列処理を含む SQL クエリ プランを生成する場合があります。 これが可能でない場合、並列処理を有効にすることはできません。  
  
> [!NOTE]  
>  ストリーミングおよび並列処理は、Enterprise Edition でのみサポートされます。 、エラーが発生せず、Standard Edition で、クエリでパラメーターを含めることができますが、パラメーターなし効果や R のスクリプトを 1 つのプロセスで実行します。  
  
## <a name="restrictions"></a>制限  


### <a name="data-types"></a>データ型

入力クエリまたはのパラメーターで使用すると、次のデータ型はサポートされていません`sp_execute_external_script`プロシージャ、およびサポートされていない型エラーの戻り値。  

この問題を回避するには、**キャスト**列または値でサポートされている型[!INCLUDE[tsql](../../includes/tsql-md.md)]外部のスクリプトを送信する前にします。  
  
-   **カーソル (cursor)**  
  
-   **timestamp**  
  
-   **datetime2**、 **datetimeoffset**、**時間**  
  
-   **sql_variant**  
  
-   **テキスト**、**イメージ**  
  
-   **xml**  
  
-   **hierarchyid**、 **geometry**、 **geography**  
  
-   CLR ユーザー定義型

一般に、いずれかの結果セットにマップすることはできません、[!INCLUDE[tsql](../../includes/tsql-md.md)]データ型は、NULL として出力します。  

### <a name="restrictions-specific-to-r"></a>R に固有の制限事項

入力が含まれる場合**datetime** R では値の許容範囲に収まらないの値、値に変換**NA**です。 これが必要な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]R 言語ではサポートされているより値の範囲が広いを許可します。

値を float (たとえば、 `+Inf`、 `-Inf`、 `NaN`) でサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合でも、両方の言語は、IEEE 754 を使用します。 現在の動作は、値を送信するだけ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]直接の結果として、SQL クライアントに[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]はエラーをスローします。 したがって、これらの値が変換を**NULL**です。

## <a name="permissions"></a>権限

必要があります**EXECUTE ANY EXTERNAL SCRIPT**データベース権限です。  

## <a name="examples"></a>使用例

このセクションには、このストアド プロシージャを使用してを使用して R または Python スクリプトを実行する方法の例が含まれています。[!INCLUDE[tsql](../../includes/tsql-md.md)]です。

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. SQL Server に R データ セットを返す  

次の例を使用するストアド プロシージャを作成する**sp_execute_external_script**を R に含まれている Iris データセットを返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  

```sql
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
GO
```

### <a name="b-generate-an-r-model-based-on-data-from-sql-server"></a>B. SQL Server からデータに基づく R モデルを生成します。  

次の例を使用するストアド プロシージャを作成する**sp_execute_external_script**を虹彩のモデルを生成し、モデルを返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  

> [!NOTE]
>  この例では、e1071 パッケージの事前インストールが必要です。 詳細については、次を参照してください。 [SQL Server に追加の R パッケージをインストール](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)です。

```sql
DROP PROC IF EXISTS generate_iris_model;
GO
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
GO
```

Python を使って似たモデルを生成するには、言語識別子を `@language=N'R'` から `@language = N'Python'` に変更し、`@script` 引数を必要に応じて修正します。 そうしないと、すべてのパラメーターが R と同じように機能します。

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>C. Python モデルを作成し、そこからスコアを生成します。

この例では、\_execute\_external\_script を使って簡単な Python モデルでスコアを生成する方法を示します。 

```sql
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

-- Input query to generate the customer data
DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders'

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

# Get data from input query
customer_data = my_input_data

# Define the model
n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Python コードで使われている列見出しは、SQL Server への出力ではありません。そのため、WITH RESULTS ステートメントを使って、SQL で使う列名とデータ型を指定します。

スコアリングには、ネイティブな [PREDICT](../../t-sql/queries/predict-transact-sql.md) 関数を使うこともできます。通常、これは Python や R のランタイムを呼び出さないので高速です。

## <a name="see-also"></a>参照

 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Python ライブラリとデータ型](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [R ライブラリと R データ型](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [SQL Server R サービス](../../advanced-analytics/r/sql-server-r-services.md)   
 [SQL Server コンピューターのサービスの学習の既知の問題](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)   
 [外部ライブラリの作成&#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [SQL Server のExternal Scripts オブジェクト](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
