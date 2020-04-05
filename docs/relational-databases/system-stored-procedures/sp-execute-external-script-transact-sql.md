---
title: sp_execute_external_script (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning
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
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 8800df26e505f1fffe25e6f65218481e7a8158f0
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80663011"
---
# <a name="sp_execute_external_script-transact-sql"></a>sp_execute_external_script (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
**sp_execute_external_script**ストアド プロシージャは、プロシージャの入力引数として提供されるスクリプトを実行し、[機械学習サービス](../../machine-learning/index.yml)および[言語拡張機能](../../language-extensions/language-extensions-overview.md)と共に使用されます。 

機械学習サービスの場合[、Python](../../machine-learning/concepts/extension-python.md)と[R](../../machine-learning/concepts/extension-r.md)はサポートされている言語です。 言語拡張機能の場合、Java はサポートされますが、[外部言語の作成](../../t-sql/statements/create-external-language-transact-sql.md)で定義する必要があります。

**sp_execute_external_script**を実行するには、まず機械学習サービスまたは言語拡張機能をインストールする必要があります。 詳細については、「 WINDOWS および Linux[に SQL Server の機械学習サービス (Python および R) をインストール](../../machine-learning/install/sql-machine-learning-services-windows-install.md)する 」または「Windows および[Linux](../../linux/sql-server-linux-setup-machine-learning.md)[に SQL Server 言語拡張機能をインストール](../../language-extensions/install/install-sql-server-language-extensions-on-windows.md)する 」を参照してください。 [Linux](../../linux/sql-server-linux-setup-language-extensions.md)
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
**sp_execute_external_script**ストアド プロシージャは、プロシージャへの入力引数として提供されるスクリプトを実行し、SQL Server 2017 の[機械学習サービス](../../machine-learning/index.yml)で使用されます。 

機械学習サービスの場合[、Python](../../machine-learning/concepts/extension-python.md)と[R](../../machine-learning/concepts/extension-r.md)はサポートされている言語です。 

**sp_execute_external_script**を実行するには、まず機械学習サービスをインストールする必要があります。 詳細については、「 [WINDOWS に SQL Server の機械学習サービス (Python および R) をインストールする 」](../../machine-learning/install/sql-machine-learning-services-windows-install.md)を参照してください。
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
**sp_execute_external_script**ストアド プロシージャは、プロシージャへの入力引数として提供されるスクリプトを実行し、SQL Server 2016 の[R サービス](../../machine-learning/r/sql-server-r-services.md)で使用されます。

R サービスの場合[、R](../../machine-learning/concepts/extension-r.md)はサポートされている言語です。

**sp_execute_external_script**を実行するには、まず R サービスをインストールする必要があります。 詳細については、「 [WINDOWS に SQL Server の機械学習サービス (Python および R) をインストールする 」](../../machine-learning/install/sql-r-services-windows-install.md)を参照してください。
::: moniker-end

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="syntax"></a>構文

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]  
    [ , @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]    
    [ , @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]  
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
## <a name="syntax-for-2017-and-earlier"></a>2017 年以前の構文

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
::: moniker-end

## <a name="arguments"></a>引数
 言語 = N'*言語*' ** \@**  
::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
 スクリプト言語を示します。 *言語*は**sysname です**。 有効な値は**R** **、Python、** および[CREATE 外部言語](../../t-sql/statements/create-external-language-transact-sql.md)で定義された言語 (Java など) です。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
 スクリプト言語を示します。 *言語*は**sysname です**。 SQL Server 2017 では、有効な値は**R**と**Python**です。
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
 スクリプト言語を示します。 *言語*は**sysname です**。 SQL Server 2016 では、有効な値は**R**のみです。
::: moniker-end

 script = N'*スクリプト*' リテラルまたは変数入力として指定された外部言語スクリプト。 ** \@** *スクリプト*は**nvarchar(最大) です**。  

`[ @input_data_1 =  N'input_data_1' ]`外部スクリプトで使用される入力データを[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリの形式で指定します。 *input_data_1*のデータ型は**nvarchar(max) です**。

`[ @input_data_1_name = N'input_data_1_name' ]`で定義されたクエリを表すために使用する変数の名前を@input_data_1指定します。 外部スクリプト内の変数のデータ型は言語によって異なります。 R の場合、入力変数はデータ フレームです。 Python の場合、入力は表形式でなければなりません。 *input_data_1_name*は**sysname**です。  既定値は *、入力データセットです*。  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
`[ @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]`パーティション単位のモデルを構築するために使用されます。 結果セットの順序付けに使用する列の名前を、例えば製品名で指定します。 外部スクリプト内の変数のデータ型は言語によって異なります。 R の場合、入力変数はデータ フレームです。 Python の場合、入力は表形式でなければなりません。

`[ @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]`パーティション単位のモデルを構築するために使用されます。 地理的な地域や日付など、データのセグメント化に使用する列の名前を指定します。 外部スクリプト内の変数のデータ型は言語によって異なります。 R の場合、入力変数はデータ フレームです。 Python の場合、入力は表形式でなければなりません。 
::: moniker-end

`[ @output_data_1_name =  N'output_data_1_name' ]`ストアド プロシージャ呼び出しの完了[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時に返されるデータを含む外部スクリプト内の変数の名前を指定します。 外部スクリプト内の変数のデータ型は言語によって異なります。 R の場合、出力はデータ フレームである必要があります。 Python の場合、出力はパンダのデータ フレームである必要があります。 *output_data_1_name*は**sysname**です。  既定値は*出力データセット です*。  

`[ @parallel = 0 | 1 ]`パラメータを 1 に設定して、R スクリプトの並列実行を`@parallel`有効にします。 このパラメーターのデフォルトは 0 (並列処理なし) です。 出力`@parallel = 1`がクライアント マシンに直接ストリーミングされる場合は、`WITH RESULT SETS`句が必要であり、出力スキーマを指定する必要があります。  

 + RevoScaleR 関数を使用しない R スクリプトの場合`@parallel`、スクリプトが簡単に並列化できると仮定すると、このパラメーターを使用すると、大きなデータセットを処理する場合に役立ちます。 たとえば、R`predict`関数をモデルと共に使用して新しい予測を生成する`@parallel = 1`場合、クエリ エンジンへのヒントとして設定します。 クエリを並列化できる場合 **、MAXDOP**設定に従って行が分散されます。  
  
 + RevoScaleR 関数を使用する R スクリプトの場合、並列処理は自動的に`@parallel = 1`処理され **、sp_execute_external_script**呼び出しに指定しないでください。  
  
`[ @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ]`外部スクリプトで使用される入力パラメーター宣言のリスト。  
  
`[ @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]`外部スクリプトで使用される入力パラメータの値のリスト。  

## <a name="remarks"></a>解説

> [!IMPORTANT]
> クエリ ツリーはによって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]制御され、ユーザーはクエリに対して任意の操作を実行できません。 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
sp_execute_external_script**を**使用して、サポートされている言語で記述されたスクリプトを実行します。 サポートされている言語は、機械学習サービスで使用される**Python**と**R、** および言語拡張機能で使用される[外部言語の作成](../../t-sql/statements/create-external-language-transact-sql.md)(Java など) で定義された言語です。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
sp_execute_external_script**を**使用して、サポートされている言語で記述されたスクリプトを実行します。 サポートされている言語は、SQL Server 2017 の機械学習サービスの**Python**と**R**です。
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
sp_execute_external_script**を**使用して、サポートされている言語で記述されたスクリプトを実行します。 サポートされる**言語は**、SQL Server 2016 R サービスの R のみです。
::: moniker-end

既定では、このストアド プロシージャによって返される結果セットは、名前のない列を持つ出力になります。 スクリプト内で使用される列名はスクリプト環境に対してローカルであり、出力される結果セットには反映されません。 結果セット列に名前を付ける`WITH RESULT SET`には、[`EXECUTE`](../../t-sql/language-elements/execute-transact-sql.md)の句を使用します。

結果セットを返すだけでなく、OUTPUT パラメーターを使用してスカラー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]値を返すことができます。 
  
外部リソースプールを構成することで、外部スクリプトで使用されるリソースを制御できます。 詳細については、「[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)」を参照してください。 ワークロードに関する情報は、リソース ガバナー カタログ ビュー、DMV の、およびカウンタから取得できます。 詳細については、「 [Transact-SQL&#41;&#40;リソース ガバナー カタログ ビュー ](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)」、[リソース ガバナー関連の動的管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)、および SQL Server [、外部スクリプト オブジェクト](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)を参照してください。  

### <a name="monitor-script-execution"></a>スクリプトの実行を監視する

[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)と[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)を使用してスクリプトの実行を監視します。 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
### <a name="parameters-for-partition-modeling"></a>パーティション モデリングのパラメータ

パーティション・データのモデル化を可能にする追加のパラメーターを 2 つ設定できます。 年齢、性別、地域、日付、時刻の繰り返し値を含む列は、パーティション化されたデータセットに適した例です。
 
2 つのパラメーターは**input_data_1_partition_by_columns**と**input_data_1_order_by_columns**で、2 番目のパラメーターを使用して結果セットを並べ替えます。 パラメータは、外部スクリプトが`sp_execute_external_script`各パーティションに対して 1 回実行される場合に、入力として渡されます。 詳細と例については、「[チュートリアル: パーティションベースのモデルを作成](https://docs.microsoft.com/sql/machine-learning/tutorials/r-tutorial-create-models-per-partition)する」を参照してください。

スクリプトは、 を指定して並列実行`@parallel=1`できます。 入力クエリを並列化できる場合は、引数の一`@parallel=1`部として を に`sp_execute_external_script`設定する必要があります。 既定では、クエリ オプティマイザ`@parallel=1`は 256 行を超えるテーブルで動作しますが、これを明示的に処理する場合は、このスクリプトにこのパラメータがデモとして含まれます。

> [!Tip]
> トレーニング ワークロードの場合、Microsoft-rx 以外のアルゴリズムを使用している場合でも、任意のトレーニング スクリプトで `@parallel` を使用できます。 通常、SQL Server のトレーニング シナリオで並列処理が提供されるのは、RevoScaleR アルゴリズム (rx プレフィックスが付いたもの) だけです。 しかし、SQL Server vNext の新しいパラメータを使用すると、その機能を使用して特別に設計されていない関数を呼び出すスクリプトを並列化できます。
::: moniker-end

### <a name="streaming-execution-for-python-and-r-scripts"></a>Python スクリプトと R スクリプトのストリーミング実行  

ストリーミングを使用すると、Python スクリプトまたは R スクリプトは、メモリに収まらないデータを処理できます。 ストリーミング中に渡される行数を制御するには、`@r_rowsPerRead`コレクション内でパラメーターの整数値を指定します。 `@params`  たとえば、非常に幅の広いデータを使用するモデルをトレーニングする場合、値を調整して読み取る行数を減らして、すべての行を 1 つのデータのチャンクで送信できるようにします。 また、サーバーのパフォーマンスの問題を軽減するために、このパラメーターを使用して、一度に読み取りおよび処理される行数を管理することもできます。 
  
ストリーミングの`@r_rowsPerRead`パラメータと引数の両方を`@parallel`ヒントと考える必要があります。 ヒントを適用するには、並列処理を含む SQL クエリ プランを生成できる必要があります。 これが不可能な場合、並列処理を有効にすることはできません。  
  
> [!NOTE]  
> ストリーミングと並列処理は、エンタープライズ エディションでのみサポートされます。 エラーを発生させることなく、Standard Edition のクエリにパラメーターを含めることができますが、パラメーターは無効であり、R スクリプトは 1 つのプロセスで実行されます。  
  
## <a name="restrictions"></a>制限  

### <a name="data-types"></a>データ型

次のデータ型は、sp_execute_external_script**の入力**クエリまたはプロシージャのパラメーターで使用されている場合はサポートされず、サポートされていない型エラーを返します。  

回避策として、外部**CAST**スクリプトに送信する[!INCLUDE[tsql](../../includes/tsql-md.md)]前に、サポートされている型にカラムまたは値をキャストします。  
  
-   **カーソル**  
  
-   **タイムスタンプ**  
  
-   **日時 2**,**日時オフセット**,**時刻**  
  
-   **Sql_variant**  
  
-   **テキスト**,**イメージ**  
  
-   **xml**  
  
-   **階層 ,****ジオメトリ ,****地理**  
  
-   CLR ユーザー定義型

一般に、[!INCLUDE[tsql](../../includes/tsql-md.md)]データ型にマップできない結果セットは NULL として出力されます。  

### <a name="restrictions-specific-to-r"></a>R に固有の制限事項

R の許容範囲に適合しない**日時**値が入力に含まれている場合、値は**NA**に変換されます。 これは、R[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]言語でサポートされている値の範囲よりも大きな範囲を許可するため、必要です。

両方の言語で IEEE `+Inf` `-Inf`754`NaN`が使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]されている場合でも、浮動小数値 ( など ) はサポートされていません。 現在の動作は値を直接[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に送信するだけです。その結果、SQL クライアントは[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]エラーをスローします。 したがって、これらの値は**NULL**に変換されます。

## <a name="permissions"></a>アクセス許可

**任意の外部スクリプト**データベースの実行権限が必要です。  

## <a name="examples"></a>例

この節では、このストアド プロシージャを使用して R または Python スクリプト[!INCLUDE[tsql](../../includes/tsql-md.md)]を実行する方法の例を示します。

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. SQL サーバに R データ セットを返す  

次の例では **、sp_execute_external_script**を使用して、R に含まれる Iris データセット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を返すストアド プロシージャを作成します。  

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

### <a name="b-generate-an-r-model-based-on-data-from-sql-server"></a>B. SQL Server からのデータに基づいて R モデルを生成します。  

次の例では **、sp_execute_external_script**を使用して虹彩モデルを生成し、モデルを に返[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]すストアド プロシージャを作成します。  

> [!NOTE]
>  この例では、e1071 パッケージの事前インストールが必要です。 詳細については、「 [SQL Server に追加の R パッケージをインストールする](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md)」を参照してください。

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

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>C. Python モデルを作成し、それからスコアを生成する

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

Python コードで使用される列見出しは SQL Server に出力されません。したがって、WITH RESULT ステートメントを使用して、SQL で使用する列名とデータ・タイプを指定します。

スコアリングには、ネイティブな [PREDICT](../../t-sql/queries/predict-transact-sql.md) 関数を使うこともできます。通常、これは Python や R のランタイムを呼び出さないので高速です。

## <a name="see-also"></a>関連項目

+ [SQL Server Machine Learning サービス](../../machine-learning/index.yml)
+ [SQL Server 言語拡張機能](../../language-extensions/language-extensions-overview.md): 
+ [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
+ [Python ライブラリとデータ型](../../machine-learning/python/python-libraries-and-data-types.md)  
+ [R ライブラリと R データ型](../../machine-learning/r/r-libraries-and-data-types.md)  
+ [SQL サーバー R サービス](../../machine-learning/r/sql-server-r-services.md)   
+ [SQL Server の機械学習サービスの既知の問題](../../machine-learning/known-issues-for-sql-server-machine-learning-services.md)   
+ [Transact-SQL&#41;&#40;外部ライブラリを作成する](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [sp_prepare&#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
+ [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
+ [external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
+ [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
+ [SQL Server のExternal Scripts オブジェクト](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
+ [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
