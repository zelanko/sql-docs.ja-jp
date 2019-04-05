---
title: T-SQL - SQL Server Machine Learning の"Hello World"基本的な R コード実行のクイック スタート
description: SQL Server で R スクリプトのクイック スタートです。 Hello world の演習では、sp_execute_external_script のシステム ストアド プロシージャを使用して R スクリプトを呼び出すことの基礎について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 1ec9580a533e51b7e99ea0ac34c1d322a27da452
ms.sourcegitcommit: 3cfedfeba377560d460ca3e42af1e18824988c07
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2019
ms.locfileid: "59042281"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>クイック スタート: SQL Server で R スクリプトの"hello world" 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイック スタートでを"Hello World"R を実行して、主要な概念スクリプト inT SQL の概要を学習します、 **sp_execute_external_script**システム ストアド プロシージャ。 

## <a name="prerequisites"></a>前提条件

前のクイック スタート[SQL server が存在することを確認する R](quickstart-r-verify.md)情報を提供し、このクイック スタートに必要な R 環境を設定するためにリンクします。

## <a name="basic-r-interaction"></a>基本的な R の対話

SQL Database での R コードを実行する 2 つの方法はあります。

+ R スクリプトをシステム ストアド プロシージャの引数として追加[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)します。
+ [リモート R client](https://docs.microsoft.com/sql/advanced-analytics/r/set-up-a-data-science-client)SQL database に接続し、計算コンテキストとして SQL Database を使用してコードを実行します。

次の演習は最初の対話モデルに重点を置いて: ストアド プロシージャに R コードを渡す方法です。

1. SQL database での R スクリプトの実行方法を表示する単純なスクリプトを実行します。

    ```sql
    EXECUTE sp_execute_external_script
    @language = N'R',
    @script = N'
    a <- 1
    b <- 2
    c <- a/b
    d <- a*b
    print(c(c, d))'
    '
    ```

2. すべての正しい結果正しくセットアップがある場合が計算され、R と`print`関数に結果を返す、**メッセージ**ウィンドウ。

    **[結果]**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    取得中に**stdout**メッセージは、コードをテストするときに有用ですより多くの場合する必要があるアプリケーションで使用したり、テーブルに書き込むように表形式で結果を返します。 参照してください[クイック スタート。ハンドルは、入力し、出力の SQL Server で R を使用して](rtsql-working-with-inputs-and-outputs.md)詳細についてはします。

内のすべての記憶、`@script`引数は有効な R コードである必要があります。

## <a name="run-a-hello-world-script"></a>Hello World スクリプトを実行します。

次の演習では、別の単純な R スクリプトを実行します。

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'OutputDataSet<-InputDataSet',
  @input_data_1 =N'SELECT 1 AS hello'
  WITH RESULT SETS (([Hello World] int));
GO
```

このストアド プロシージャへの入力は次のとおりです。

+ *@language* パラメーターは、ここでは、R. を呼び出す言語拡張機能を定義します。
+ *@script* パラメーターは、R ランタイムに渡されるコマンドを定義します。 Unicode テキストとして、この引数で R スクリプト全体を囲む必要があります。 **nvarchar** 型の変数にテキストを追加して、その変数を呼び出すこともできます。
+ *@input_data_1* データ フレームとして SQL Server へデータを返す R ランタイムに渡される、クエリによってデータが返されます。
+ 句の結果セット列名として"Hello World"を追加する、SQL Server の返されたデータ テーブルのスキーマを定義します**int**データ型。

**[結果]**

| ハローワールド |
|-------------|
| 1 |

## <a name="next-steps"></a>次のステップ

これで、複数の単純な R スクリプトを実行すると、入力と出力の構成について詳しく見てを実行します。

> [!div class="nextstepaction"]
> [クイック スタート: 入力と出力の処理](quickstart-r-inputs-and-outputs.md)
