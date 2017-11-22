---
title: "操作の入力と出力 (SQL のクイック スタートで R) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
- SQL
ms.assetid: 75480e5c-f37f-45b9-a176-67e08e9a9daf
caps.latest.revision: "7"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: cb651d6541bbba7be03b74265ffae5dccdbdf9c9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="working-with-inputs-and-outputs-r-in-sql-quickstart"></a>入力と出力 (R で SQL のクイック スタート) の使用

SQL Server で R コードを実行する場合は、システム ストアド プロシージャで R スクリプトをラップする必要があります[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。 このストアド プロシージャを使用して、SQL Server のコンテキストで、R ランタイムを起動します。このランタイムは、データを R に渡し、R ユーザー セッションを安全に管理し、結果をクライアントに返します。

## <a name="bkmk_SSMSBasics"></a>単純なテスト データを作成する

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

**[結果]**

|col1|
|------|
|*1*|
|"*10*"|
|"*100*"|

## <a name="get-the-same-data-using-r-script"></a>R スクリプトを使用して同じデータを取得する

テーブルが作成されたら、次のステートメントを実行します。

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N' OutputDataSet <- InputDataSet;'
    , @input_data_1 = N' SELECT *  FROM RTestData;'
    WITH RESULT SETS (([NewColName] int NOT NULL));
```

テーブルからデータを取得、R ランタイムを通じてラウンド トリップし、列の名前、値を返します*NewColName*です。

**[結果]**

![rsql_basictut_getsamedataR](media/rsql-basictut-getsamedatar.PNG)


**コメント**

+ Management Studio では、表形式の結果が **[値]** ペインで返されます。 R ランタイムから返されたメッセージは、**[メッセージ]** ペインに表示されます。
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

、エラーが発生したでした"オブジェクトの SQL\_で見つかりませんでした"しますか? これは R で大文字と小文字が区別されることが原因です。 例では、R スクリプトで変数 "*SQL_in*" と "*SQL_out*" を使用していますが、ストアド プロシージャへのパラメーターでは変数 "*SQL_In*" と "*SQL_Out*" を使用しています。

R は大文字小文字を区別するためです。 例では、R スクリプトで変数 "*SQL_in*" と "*SQL_out*" を使用していますが、ストアド プロシージャへのパラメーターでは変数 "*SQL_In*" と "*SQL_Out*" を使用しています。
修正を再試行してください**のみ**、 *SQL_In*変数と、ストアド プロシージャを再実行します。

取得するようになりました、**異なる**エラー。

```Error
EXECUTE statement failed because its WITH RESULT SETS clause specified 1 result set(s), but the statement only sent 0 result set(s) at run time.
```

紹介するこのエラーに新しい R コードをテストする際に多くの場合を期待できるためです。 R スクリプトは成功しましたが、SQL Server データを受信しないか、間違ったデータや予期しないデータを受信できないことを示します。

この場合、出力スキーマ (**WITH** で始まる行) は、整数データの 1 つの列を返す必要があると指定しますが、R では別の変数にデータが格納されるため SQL Server には何も返されず、そのためエラーになります。 このエラーを解決するには、2 つ目の変数名を修正します。

**これらの要件に注意してください。**

- 変数名は有効な SQL 識別子の規則に従っている必要があります。
- パラメーターの順序が重要です。 省略可能なパラメーター "*@input_data_1_name*" と "*@output_data_1_name*" を使用するためには、まず必須パラメーター "*@input_data_1*" と "*@output_data_1*" を指定する必要があります。
- パラメーターとして渡すことができるのは、1 つの入力データセットのみです。また、1 つのデータセットのみを返すことができます。 ただし、R コード内から他のデータセットを呼び出し、データセットに加えて他の型の出力を返すことができます。 また、OUTPUT キーワードを任意のパラメーターに追加して、その結果を受け取ることもできます。 このチュートリアルで後ほど簡単な例を示します。
- `WITH RESULT SETS` ステートメントは、SQL Server のためのデータのスキーマを定義します。 R から返す列ごとに SQL 互換のデータ型を提供する必要があります。スキーマ定義を使用して新しい列名を提供することもできます。R data.frame の列名を使用する必要はありません。 場合によっては、この句は省略可能です。これを省略して再試行してくださいし、何が起こるかを確認します。

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

**[結果]**

*Col1*
*こんにちは*
<code>   </code>"
*world*"

## <a name="next-lesson"></a>次のレッスン

R と SQL の間の暗黙的な変換や表形式データの違いなど、R と SQL Server の間でデータを渡す場合に発生する可能性のあるいくつかの問題を調べます。

[R および SQL のデータ型とデータ オブジェクト](../tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)
