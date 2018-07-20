---
title: 入力と出力 (SQL Server Machine Learning) の R で使用するためのクイック スタート |Microsoft Docs
description: SQL Server で R スクリプトのこのクイック スタートでは、入力と出力は、sp_execute_external_script のシステム ストアド プロシージャを構成する方法を説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b41a8c30cd0ecbe040819478c0cadece1b9eb704
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086584"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>クイック スタート: 入力と SQL Server で R を使用する出力を処理します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server で R コードを実行する場合は、ストアド プロシージャで R スクリプトをラップする必要があります。 1 つは、作成したり、R スクリプトに渡すできます[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。 このシステム ストアド プロシージャを使用してデータを R に渡す、SQL Server のコンテキストで R ランタイムを開始するは、R ユーザー セッションを安全に、管理し、クライアントに結果を返します。

## <a name="prerequisites"></a>前提条件

前のクイック スタート[の Hello World R と SQL を](rtsql-using-r-code-in-transact-sql-quickstart.md)情報を提供し、このクイック スタートに必要な R 環境を設定するためにリンクします。

<a name="bkmk_SSMSBasics"></a>

## <a name="create-some-simple-test-data"></a>単純なテスト データを作成する

次の T-SQL ステートメントを実行してテスト データの小さなテーブルを作成します。

```sql
CREATE TABLE RTestData ([col1] int not null) ON [PRIMARY]
INSERT INTO RTestData   VALUES (1);
INSERT INTO RTestData   VALUES (10);
INSERT INTO RTestData   VALUES (100) ;
GO
```

テーブルが作成されたら、次のステートメントを使用してテーブルを照会します。
  
```sql
SELECT * FROM RTestData
```

**結果**

![RTestData テーブルの内容](media/quickstart-r-working-input-outputs-results-1.png)


## <a name="get-the-same-data-using-r-script"></a>R スクリプトを使用して同じデータを取得する

テーブルが作成されたら、次のステートメントを実行します。

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N' OutputDataSet <- InputDataSet;'
    , @input_data_1 = N' SELECT *  FROM RTestData;'
    WITH RESULT SETS (([NewColName] int NOT NULL));
```

テーブルからデータを取得、R ランタイムのラウンド トリップ、および列の名前、値を返します*NewColName*します。

**結果**

![rsql_basictut_getsamedataR](media/rsql-basictut-getsamedatar.PNG)


**コメント**

+ "*@language*" パラメーターでは、呼び出す言語拡張機能 (この例では R) を定義します。
+ "*@script*" パラメーターでは、R ランタイムに渡すコマンドを定義します。 Unicode テキストとして、この引数で R スクリプト全体を囲む必要があります。 **nvarchar** 型の変数にテキストを追加して、その変数を呼び出すこともできます。
+ クエリによって返されるデータは R ランタイムに渡され、そこからデータがデータ フレームとして SQL Server に返されます。
+ WITH RESULT SETS 句では、SQL Server の返されたデータ テーブルのスキーマを定義します。

## <a name="change-input-or-output-variables"></a>入力または出力変数を変更する

前の例では、入力と出力の既定の変数名である "_InputDataSet_" と "_OutputDataSet_" を使用しました。 "_InputDatSet_" に関連付けられている入力データを定義するには、"*@input_data_1*" 変数を使用します。

この例では、ストアド プロシージャの出力と入力の変数名がそれぞれ "*SQLOut*" と "*SQLIn*" に変更されています。

```sql
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N' SQL_out <- SQL_in;'
  , @input_data_1 = N' SELECT 12 as Col;'
  , @input_data_1_name  = N'SQL_In'
  , @output_data_1_name =  N'SQL_Out'
  WITH RESULT SETS (([NewColName] int NOT NULL));
```

エラーが発生しました"オブジェクトの SQL\_で見つかりませんでした"でしょうか。 これは R で大文字と小文字が区別されることが原因です。 例では、R スクリプトで変数 "*SQL_in*" と "*SQL_out*" を使用していますが、ストアド プロシージャへのパラメーターでは変数 "*SQL_In*" と "*SQL_Out*" を使用しています。

修正を試す**のみ**、 *SQL_In*変数を*@script*ストアド プロシージャを再実行します。

取得するので、**異なる**エラー。

```Error
EXECUTE statement failed because its WITH RESULT SETS clause specified 1 result set(s), but the statement only sent 0 result set(s) at run time.
```

紹介するこのエラーのために新しい R コードをテストするときに多くの場合を参照してください。 R スクリプトの実行が正常が、SQL Server のデータを受信しないまたは問題または予期しないデータを受信したことを意味します。

この場合、出力スキーマ (**WITH** で始まる行) は、整数データの 1 つの列を返す必要があると指定しますが、R では別の変数にデータが格納されるため SQL Server には何も返されず、そのためエラーになります。 エラーを解決するには、2 つ目の変数名を修正します。

**これらの要件に注意してください。**

- 変数名は有効な SQL 識別子の規則に従っている必要があります。
- パラメーターの順序が重要です。 省略可能なパラメーター "*@input_data_1_name*" と "*@output_data_1_name*" を使用するためには、まず必須パラメーター "*@input_data_1*" と "*@output_data_1*" を指定する必要があります。
- パラメーターとして渡すことができるのは、1 つの入力データセットのみです。また、1 つのデータセットのみを返すことができます。 ただし、R コード内から他のデータセットを呼び出し、データセットに加えて他の型の出力を返すことができます。 また、OUTPUT キーワードを任意のパラメーターに追加して、その結果を受け取ることもできます。 このチュートリアルで後ほど簡単な例を示します。
- `WITH RESULT SETS` ステートメントは、SQL Server のためのデータのスキーマを定義します。 R から返す列ごとに SQL 互換のデータ型を提供する必要があります。スキーマ定義を使用して新しい列名を提供することもできます。R data.frame の列名を使用する必要はありません。 場合によっては、この句は省略可能です。省略することをお試しくださいし、動作を確認します。

## <a name="generate-results-using-r"></a>R を使用して結果を生成する

R スクリプトだけを使用して値を生成し、"_@input_data_1_" の入力クエリ文字列は空白のままにすることもできます。 または、有効な SQL SELECT ステートメントをプレースホルダーとして使用し、SQL の結果は R スクリプトで使用しません。

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
   , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
   , @input_data_1 = N' SELECT 1 as Temp1'
   WITH RESULT SETS (([Col1] char(20) NOT NULL));
```

**結果**

![使用してクエリ結果@script入力として](media/quickstart-r-working-input-outputs-results-3.png)

## <a name="next-steps"></a>次のステップ

暗黙的な変換や表形式のデータで R と SQL の間の違いなど、R と SQL Server の間でデータを渡す場合に発生する可能性のある問題のいくつかを確認します。

> [!div class="nextstepaction"]
> [クイック スタート: データ型とオブジェクトを処理します。](../tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)