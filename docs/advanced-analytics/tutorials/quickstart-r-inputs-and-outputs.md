---
title: 入力と出力を R で SQL Server Machine Learning で使用するためのクイック スタート
description: SQL Server で R スクリプトのこのクイック スタートでは、入力と出力は、sp_execute_external_script のシステム ストアド プロシージャを構成する方法を説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 56d2eb65ca95dd4f153f3c7a6ebb00e926465687
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046862"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>クイック スタート:入力と SQL Server で R を使用する出力を処理します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイック スタートでは、入力を処理する方法について説明し、SQL Server Machine Learning Services での R または R Services を使用する場合に出力します。

SQL Server で R コードを実行する場合は、ストアド プロシージャで R スクリプトをラップする必要があります。 1 つは、作成したり、R スクリプトに渡すできます[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。 このシステム ストアド プロシージャを使用してデータを R に渡す、SQL Server のコンテキストで R ランタイムを開始するは、R ユーザー セッションを安全に、管理し、クライアントに結果を返します。

既定では、 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) 1 つの入力データセットが有効な SQL クエリの形式で指定する通常を受け入れます。 その他の種類の入力は、SQL 変数として渡すことができます。

ストアド プロシージャが、出力として 1 つの R データ フレームを返しますが、スカラー、および変数としてモデルを出力することもできます。 たとえば、二項変数としてトレーニング済みモデルを出力し、そのモデルをテーブルに書き込む、T-SQL INSERT ステートメントに渡すできます。 (バイナリ形式) でのプロットまたはスカラーを生成することもできます (日付と時刻をなど、個々 の値、経過時間、モデルのトレーニングなど)。

## <a name="prerequisites"></a>前提条件

前のクイック スタート[SQL server が存在することを確認する R](quickstart-r-verify.md)情報を提供し、このクイック スタートに必要な R 環境を設定するためにリンクします。

## <a name="create-the-source-data"></a>ソース データを作成する

次の T-SQL ステートメントを実行してテスト データの小さなテーブルを作成します。

```sql
CREATE TABLE RTestData (col1 INT NOT NULL)
INSERT INTO RTestData VALUES (1);
INSERT INTO RTestData VALUES (10);
INSERT INTO RTestData VALUES (100);
GO
```

テーブルが作成されたら、次のステートメントを使用してテーブルを照会します。
  
```sql
SELECT * FROM RTestData
```

**結果**

![RTestData テーブルの内容](./media/select-rtestdata.png)

## <a name="inputs-and-outputs"></a>[スクリプト変換エディター]

既定値を見てみましょう sp_execute_external_script の入力と出力の変数:`InputDataSet`と`OutputDataSet`します。

1. R スクリプトの入力としてテーブルからデータを取得できます。 次のステートメントを実行します。 テーブルからデータを取得、R ランタイムのラウンド トリップ、および列の名前で値を返します*NewColName*します。

    クエリによって返されるデータは、データ フレームとして SQL Database にデータを返す R ランタイムに渡されます。 WITH RESULT SETS 句では、SQL Database の返されたデータ テーブルのスキーマを定義します。

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **結果**

    ![テーブルからデータを返す R スクリプトからの出力](./media/r-output-rtestdata.png)

2. 入力または出力変数の名前を変更してみましょう。 上記のスクリプトは既定の入力を使用し、出力変数名は、 _InputDataSet_と_OutputDataSet_します。 関連付けられている入力データを定義する_InputDatSet_を使用する、 *@input_data_1*変数。

    このスクリプトでは、ストアド プロシージャの出力と入力変数の名前に変更されましたが*SQL_out*と*SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'R'
      , @script = N' SQL_out <- SQL_in;'
      , @input_data_1 = N'SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    R は大文字小文字が区別ことに注意してください。 ため、入力と出力の変数の大文字と小文字`@input_data_1_name`と`@output_data_1_name`で R コードで使用されていると一致する必要がある`@script`。 

    また、パラメーターの順序が重要です。 省略可能なパラメーター "*@input_data_1_name*" と "*@output_data_1_name*" を使用するためには、まず必須パラメーター "*@input_data_1*" と "*@output_data_1*" を指定する必要があります。

    パラメーターとして渡すことができるのは、1 つの入力データセットのみです。また、1 つのデータセットのみを返すことができます。 ただし、R コード内から他のデータセットを呼び出し、データセットに加えて他の型の出力を返すことができます。 また、OUTPUT キーワードを任意のパラメーターに追加して、その結果を受け取ることもできます。 

    `WITH RESULT SETS`ステートメントは、SQL Server で使用されるデータのスキーマを定義します。 R. から返す列ごとに SQL 互換のデータ型を提供する必要があります。スキーマ定義を使用して、新しい列名を提供するので、R データ フレームから列名を使用する必要はありません。

3. また、R スクリプトを使用して値を生成し、入力クエリ文字列のままにできます_@input_data_1_空白。

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N' mytextvariable <- c("hello", " ", "world");
            OutputDataSet <- as.data.frame(mytextvariable);'
        , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **結果**

    ![使用してクエリ結果@script入力として](./media/r-data-generated-output.png)

## <a name="next-steps"></a>次の手順

暗黙的な変換や表形式のデータで R と SQL の間の違いなど、R と SQL Server の間でデータを渡す場合に発生する可能性のある問題のいくつかを確認します。

> [!div class="nextstepaction"]
> [クイック スタート:データ型とオブジェクトを処理します。](quickstart-r-data-types-and-objects.md)