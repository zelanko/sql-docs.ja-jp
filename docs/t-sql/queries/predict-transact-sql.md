---
title: "予測 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PREDICT
- PREDICT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PREDICT clause
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 529cb229b6658085d0f2122604a4ed638f66a84c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="predict-transact-sql"></a>予測 (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

予測値や保存されたモデルに基づいたスコアを生成します。  

## <a name="syntax"></a>構文

```
PREDICT  
(  
  MODEL = @model | model_literal,  
  DATA = object AS <table_alias>  
)  
WITH ( <result_set_definition> )  

<result_set_definition> ::=  
  {  
    { column_name  
      data_type  
      [ COLLATE collation_name ]  
      [ NULL | NOT NULL ]  
    }  
      [,...n ]  
  }  

MODEL = @model | model_literal  
```

### <a name="arguments"></a>引数

**model**

`MODEL`パラメーターを使用して、スコア付けまたは予測に使用するモデルを指定します。 モデルは、変数またはリテラル スカラー式として指定されます。

モデル オブジェクトは、R、Python または他のツールを使用して作成できます。

**データ**

データ パラメーターを使用してをスコア付けまたは予測に使用するデータを指定します。 データは、クエリでテーブル ソースの形式で指定されます。 テーブル ソースには、テーブル、テーブルの別名、CTE のエイリアス、ビュー、またはテーブル値関数を指定できます。

**パラメーター**

パラメーターのパラメーターは、スコア付けまたは予測に使用される省略可能なユーザー定義のパラメーターを指定する使用されます。

各パラメーターの名前は、モデルの種類に固有です。 RevoScaleR で rxPredict 関数では、パラメーター、たとえば、 _@computeResiduals ビット_ロジスティック回帰モデルのスコア付けに残差の計算をサポートするためにします。  パラメーター名とその値を渡す可能性があります、`PREDICT`関数。

> [注]このオプションは、SQL Server 2017 のプレリリース版ではサポートされていませんしの将来の互換性の目的でのみが含まれます。

**使用 ( \<result_set_definition >)**

によって返される出力のスキーマを指定すると、WITH 句が使用される、`PREDICT`関数。

によって返される列のほか、`PREDICT`関数自体は、データの一部であるすべての列がクエリで使用可能なを入力します。

### <a name="return-values"></a>戻り値

定義済みのスキーマがありません。SQL Server では、モデルの内容を検証しませんし、返される列の値を検証しません。  
- `PREDICT`関数が入力として列を使用して渡します  
- `PREDICT`関数では、新しい列の場合も生成されますが、列とそのデータ型の数は、予測に使用されたモデルの種類によって異なります。  

データに関連するすべてのエラー メッセージ、モデル、または列形式の関数から返される、基になる予測モデルに関連付けられています。  
- RevoScaleR、同等の関数は[rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict)  
- MicrosoftML、同等の関数は[rxPredict.mlModel](https://docs.microsoft.com/r-server/r-reference/microsoftml/rxpredict)  

内部構造を使用してモデルを表示することはできません`PREDICT`です。 モデル自体の内容を理解する場合は、モデル オブジェクトを読み込み、逆シリアル化、適切な R コードを使用して、モデルを解析してください。

## <a name="remarks"></a>解説

`PREDICT`関数は、Linux を含む、SQL Server のすべてのエディションでサポートされています。

R、Python、または言語を習得する別のコンピューターを使用するサーバーにインストールすることが必要はありません、`PREDICT`関数。 別の環境でモデルをトレーニングし、SQL Server テーブルで使用するために保存できます`PREDICT`、保存されたモデルが SQL Server の別のインスタンスから、モデルを呼び出したりします。

### <a name="supported-algorithms"></a>サポートされるアルゴリズム

モデルを使用する必要があります作成されている RevoScaleR パッケージからサポートされているアルゴリズムのいずれかを使用します。 現在サポートされているモデルの一覧は、次を参照してください。[リアルタイム スコアリング](../../advanced-analytics/real-time-scoring.md)です。

### <a name="permissions"></a>Permissions

アクセス許可は必要ありません`PREDICT`。 ただし、ユーザーのニーズ`EXECUTE`、データベースに対する権限と、入力として使用されるデータをクエリする権限です。 ユーザーも必要があります、テーブルからモデルを読み込むこと、モデルをテーブルに格納されている場合。

## <a name="examples"></a>使用例

次の例では、呼び出し元の構文`PREDICT`です。

### <a name="call-a-stored-model-and-use-it-for-prediction"></a>保存されたモデルを呼び出すし、予測に使用

この例では、[models_table] テーブルに格納されている既存のロジスティック回帰モデルを呼び出します。 最新トレーニング済みモデル取得、SELECT ステートメントを使用し、予測関数を二項モデルを渡します。 入力値を表す機能です。出力では、モデルによって割り当てられた分類を表します。

```sql
DECLARE @logit_model varbinary(max) = "SELECT TOP 1 @model from [models_table]";
DECLARE @input_qry = "SELECT ID, [Gender], [Income] from NewCustomers";

SELECT PREDICT [class]
FROM PREDICT( MODEL = @logit_model,  DATA = @input_qry
WITH (class string);
```

### <a name="using-predict-in-a-from-clause"></a>FROM 句での予測の使用

この例では参照、`PREDICT`で機能、`FROM`の句、`SELECT`ステートメント。

```sql
SELECT d.*, p.Score
FROM PREDICT(MODEL = @logit_model, 
  DATA = dbo.mytable AS d) WITH (Score float) AS p;
```

エイリアス**d**でテーブル ソースに指定された、_データ_dbo.mytable に属している列を参照するパラメーターを使用します。 エイリアス**p**向けに指定された、 **PREDICT** PREDICT 関数によって返される列を参照する関数を使用します。

### <a name="combining-predict-with-an-insert-statement"></a>INSERT ステートメントと予測の組み合わせ

入力データのスコアを生成し、テーブルに、予測された値を挿入すると予測のための一般的なユース ケースの 1 つです。 次の例では、呼び出し元のアプリケーションがテーブルに、予測される値を含む行を挿入するストアド プロシージャを使用することを前提としています。

```sql
CREATE PROCEDURE InsertLoanApplication
(@p1 varchar(100), @p2 varchar(200), @p3 money, @p4 int)
AS
BEGIN
  DECLARE @model varbinary(max) = (select model
  FROM scoring_model
  WHERE model_name = 'ScoringModelV1');
  WITH d as ( SELECT * FROM (values(@p1, @p2, @p3, @p4)) as t(c1, c2, c3, c4) )

  INSERT INTO loan_applications (c1, c2, c3, c4, score)
  SELECT d.c1, d.c2, d.c3, d.c4, p.score
  FROM PREDICT(MODEL = @model, DATA = d) WITH(score float) as p;
END;
```

プロシージャが、テーブル値パラメーターを使用して複数の行を受け取る場合に記述できますとおり。

```sql
CREATE PROCEDURE InsertLoanApplications (@new_applications dbo.loan_application_type)
AS
BEGIN
  DECLARE @model varbinary(max) = (SELECT model_bin FROM scoring_models WHERE model_name = 'ScoringModelV1');
  INSERT INTO loan_applications (c1, c2, c3, c4, score)
  SELECT d.c1, d.c2, d.c3, d.c4, p.score
  FROM PREDICT(MODEL = @model, DATA = @new_applications as d)
  WITH (score float) as p;
END;
```

### <a name="creating-an-r-model-and-generating-scores-using-optional-model-parameters"></a>R モデルを作成して、省略可能なモデル パラメーターを使用してスコアの生成

> [!NOTE]
> Release Candidate 1 では、パラメーターの引数の使用はサポートされていません。

この例が共分散マトリックスを取り付けて、ロジスティック回帰モデルを使って作成したこのなど RevoScaleR への呼び出しを前提としています。

```R
logitObj <- rxLogit(Kyphosis ~ Age + Start + Number, data = kyphosis, covCoef = TRUE)
```

SQL Server にバイナリ形式でモデルを格納する場合は、予測だけでなくエラーや信頼区間など、モデルの種類でサポートされている追加の情報を生成する予測関数を使用できます。

次のコードは、rxPredict に R から、同等の呼び出しを示しています。

```R
rxPredict(logitObj, data = new_kyphosis_data, computeStdErr = TRUE, interval = "confidence")
```

使用して、同等の呼び出し、`PREDICT`関数にも、スコアが用意されています (予測値)、エラー、および信頼区間。

```sql
SELECT d.Age, d.Start, d.Number, p.pred AS Kyphosis_Pred, p.stdErr, p.pred_lower, p.pred_higher
FROM PREDICT( MODEL = @logitObj,  DATA = new_kyphosis_data AS d,
  PARAMETERS = N'computeStdErr bit, interval varchar(30)',
  computeStdErr = 1, interval = 'confidence')
WITH (pred float, stdErr float, pred_lower float, pred_higher float) AS p;
```



