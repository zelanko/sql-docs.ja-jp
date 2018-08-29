---
title: sp_execute_external_script (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 07/14/2018
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 5e866f5a9856fe1308bc5233432e053b18d207f7
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118320"
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (TRANSACT-SQL)

[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  外部の場所に引数として指定されたスクリプトを実行します。 サポートされていると、登録済みの言語 (R または Python) では、スクリプトを記述する必要があります。 実行する**sp_execute_external_script**、ステートメントを使用して外部スクリプトを有効にする必要があります最初`sp_configure 'external scripts enabled', 1;`します。  
  
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
 \@言語 = N'*言語*'  
 スクリプト言語を示します。 *言語*は**sysname**します。  

 有効な値は `Python` または `R` です。 
  
 \@スクリプト = N'*スクリプト*'  
 外部の言語のスクリプト リテラルまたは変数の入力として指定します。 *スクリプト*は**nvarchar (max)** します。  
  
 [ \@input_data_1_name = N'*input_data_1_name*']  
 によって定義されたクエリを表すために使用する変数の名前を示す\@input_data_1 します。 外部のスクリプトで変数のデータ型は、言語に依存します。 R が発生した場合は、入力変数は、データ フレームです。 Python の場合は、入力を表形式でなければなりません。 *input_data_1_name*は**sysname**します。  
  
 既定値は`InputDataSet`します。  
  
 [ \@input_data_1 = N'*input_data_1*']  
 形式で外部のスクリプトで使用する入力データを指定します、[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。 データ型*input_data_1*は**nvarchar (max)** します。
  
 [ \@output_data_1_name = N'*output_data_1_name*']  
 返されるデータを含む外部スクリプトで変数の名前を指定します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアド プロシージャの呼び出しの完了時にします。 外部のスクリプトで変数のデータ型は、言語に依存します。 R、出力は、データ フレームである必要があります。 Python、出力は、pandas データ フレームである必要があります。 *output_data_1_name*は**sysname**します。  
  
 既定値は、"OutputDataSet"です。  
  
 [\@並列 0 を = | 1]

 R スクリプトの並列実行を有効に設定して、`@parallel`パラメーターを 1 にします。 このパラメーターに既定では 0 (並列処理です)。  
  
 R スクリプトを使用して、RevoScaleR 関数を使用して、`@parallel`パラメーターをスクリプトが普通に並列化と仮定すると、大規模なデータセットを処理するために役立つことができます。 たとえば、R を使用して`predict`に新しい予測を生成して設定するには、モデルで関数を`@parallel = 1`クエリ エンジンへのヒントとして。 に従って行が分散クエリを並列に処理できる場合、 **MAXDOP**設定します。  
  
 場合`@parallel = 1`出力が、クライアント コンピューターに直接ストリーミングされていると、`WITH RESULTS SETS`句は必須であり、出力スキーマを指定する必要があります。  
  
 RevoScaleR 関数を使用する R スクリプトでは、並列処理は自動的に処理され、指定しないでください`@parallel = 1`を**sp_execute_external_script**呼び出します。  
  
 [ \@params = N'*\@parameter_name data_type* [OUT |出力] [、.. .n]']  
 外部のスクリプトで使用される入力パラメーターの宣言の一覧。  
  
 [ \@parameter1 = '*value1*' [OUT |出力] [、.. .n]  

 外部のスクリプトで使用される入力パラメーターの値の一覧。  

## <a name="remarks"></a>コメント

使用**sp_execute_external_script**サポートされている言語で記述されたスクリプトを実行します。 現在、サポートされている言語は、SQL Server 2016、および Python 用の R と SQL Server 2017 の R は。 

> [!IMPORTANT]
> クエリ ツリーがによって制御される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と、ユーザーは、クエリに任意の操作を実行できません。 

既定では、このストアド プロシージャによって返される結果セットは、名前のない列と出力が。 スクリプト内で使用する列名は、スクリプト環境をローカルであり、出力される結果セットには反映されません。 結果セット列名を使用して、`WITH RESULTS SET`の句[ `EXECUTE`](../../t-sql/language-elements/execute-transact-sql.md)します。
  
 結果セットを返すことに加えてをスカラー値を返すことができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]出力パラメーターを使用しています。 次の例は、スクリプトへの入力として使用されたシリアル化された R モデルを返す出力パラメーターの使用を示しています。  

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]と共にインストールされるサーバー コンポーネントで構成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、一連のワークステーションのツールとの高パフォーマンスの環境にデータ サイエンティストを接続する接続ライブラリと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 機械学習中にコンポーネントをインストールする必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を外部スクリプトの実行を有効に設定します。 詳細については、次を参照してください。[を設定する SQL Server Machine Learning Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)します。  
  
外部リソース プールを構成することで、外部スクリプトで使用されるリソースを制御できます。 詳細については、「[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)」を参照してください。 ワークロードに関する情報は、リソース ガバナーのカタログ ビュー、DMV のカウンターから取得できます。 詳細については、次を参照してください[リソース ガバナーのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)、[リソース ガバナー関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)、および。[SQL Server の External Scripts オブジェクト](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)します。  

監視スクリプトの実行を使用して[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)と[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)します。 

## <a name="streaming-execution-for-r-and-python-scripts"></a>R と Python スクリプトの実行 (ストリーミング)  

ストリーミングには、メモリ内に収まるよりも多くのデータを使用する R または Python スクリプトが使用できます。 ストリーミング中に渡される行の数を制御するには、パラメーターには、整数値を指定`@r_rowsPerRead`で、`@params`コレクション。  たとえば、非常に大きなデータを使用するモデルをトレーニングする場合は、データの 1 つのチャンクですべての行を送信できることを確認するが少ない行を読み取る値を調整できます。 読み取りし、サーバー パフォーマンスの問題を軽減するために、一度に処理されている行の数を管理するのにこのパラメーターを使用することも可能性があります。 
  
両方の`@r_rowsPerRead`ストリーミング用のパラメーターと`@parallel`引数にヒントを検討する必要があります。 ヒントを適用するには、並列処理を含む SQL クエリ プランを生成できない場合があります。 それができない場合、並列処理を有効にすることはできません。  
  
> [!NOTE]  
>  ストリーミングと並列処理は、Enterprise Edition でのみサポートされます。 エラーを生成することがなく、Standard Edition で、クエリ内でパラメーターを含めることができますが、効果と 1 つのプロセスで実行される R スクリプトのパラメーターがあるありません。  
  
## <a name="restrictions"></a>制限  


### <a name="data-types"></a>データ型

入力クエリまたはのパラメーターで使用すると、次のデータ型はサポートされていません**sp_execute_external_script**プロシージャ、およびサポートされていない型エラーを返します。  

この問題を回避するには、**キャスト**列または値でサポートされている型[!INCLUDE[tsql](../../includes/tsql-md.md)]外部スクリプトを送信する前にします。  
  
-   **カーソル (cursor)**  
  
-   **timestamp**  
  
-   **datetime2**、 **datetimeoffset**、**時間**  
  
-   **sql_variant**  
  
-   **テキスト**、**イメージ**  
  
-   **xml**  
  
-   **hierarchyid**、 **geometry**、 **geography**  
  
-   CLR ユーザー定義型

一般に、いずれかの結果セットにマップすることはできませんが、[!INCLUDE[tsql](../../includes/tsql-md.md)]データ型である NULL として出力します。  

### <a name="restrictions-specific-to-r"></a>R に固有の制限

入力が含まれている場合**datetime** r 値の許容範囲に収まらないの値、値に変換されます**NA**します。 これは、必要なため[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は R 言語でサポートされているより値の範囲が広いを許可します。

値を float (たとえば、 `+Inf`、 `-Inf`、 `NaN`) でサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でも、両方の言語が IEEE 754 を使用します。 現在の動作は、値を送信するだけ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]その結果、SQL client には直接[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]エラーをスローします。 そのため、これらの値に変換されます**NULL**します。

## <a name="permissions"></a>アクセス許可

必要があります**EXECUTE ANY EXTERNAL SCRIPT**データベース権限。  

## <a name="examples"></a>使用例

このセクションには、このストアド プロシージャを使用してを使用して、R または Python スクリプトを実行する方法の例が含まれています。[!INCLUDE[tsql](../../includes/tsql-md.md)]します。

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. SQL Server に R のデータ セットを返す  

次の例を使用するストアド プロシージャを作成する**sp_execute_external_script**を R に含まれている Iris データセットを返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  

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

次の例を使用するストアド プロシージャを作成する**sp_execute_external_script**を虹彩のモデルを生成し、モデルを返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  

> [!NOTE]
>  この例では、e1071 パッケージの事前インストールが必要です。 詳細については、次を参照してください。 [SQL Server に追加の R パッケージをインストール](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)します。

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

## <a name="see-also"></a>関連項目

 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Python ライブラリとデータ型](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [R ライブラリと R データ型](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [SQL Server R サービス](../../advanced-analytics/r/sql-server-r-services.md)   
 [SQL Server Machine Learning サービスの既知の問題](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)   
 [外部ライブラリを作成する&#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [SQL Server のExternal Scripts オブジェクト](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
