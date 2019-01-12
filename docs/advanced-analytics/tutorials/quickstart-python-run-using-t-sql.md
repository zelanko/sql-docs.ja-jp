---
title: "\"Hello World\"の基本的な Python 用のクイック スタート コードの T-SQL と SQL Server Machine Learning での実行"
description: SQL Server での Python スクリプトのクイック スタートです。 Hello world の演習では、sp_execute_external_script のシステム ストアド プロシージャを使用して Python スクリプトを呼び出すことの基礎について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/11/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 0061e96168f16d8a92ed47578c32a3b16bf57306
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241813"
---
# <a name="quickstart-hello-world-python-script-in-sql-server"></a>クイック スタート:SQL Server での Python スクリプトの"hello world" 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイック スタートでを"Hello World"Python を実行して、主要な概念スクリプト inT SQL の概要を説明する、 **sp_execute_external_script**システム ストアド プロシージャ。 

## <a name="prerequisites"></a>前提条件

前のクイック スタート[SQL server が存在することを確認する Python](quickstart-python-verify.md)情報を提供し、このクイック スタートに必要な Python 環境を設定するためにリンクします。

## <a name="basic-python-interaction"></a>基本的な Python の対話

SQL Server での Python コードを実行する 2 つの方法はあります。

+ Python スクリプトを追加する、システム ストアド プロシージャの引数として[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。

+ [Python クライアントをリモート](../python/setup-python-client-tools-sql.md)、SQL Server に接続し、計算コンテキストとして SQL Server を使用してコードを実行します。 これは、必要があります[revoscalepy](../python/ref-py-revoscalepy.md)します。

次の演習は最初の対話モデルに重点を置いて: Python コードをストアド プロシージャに渡す方法です。

1. SQL Server と Python 間のデータの前後の渡す方法を確認する簡単なコードを実行します。

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

2. Python と SQL Server が互いに通信を正しく設定するすべてのものがあると仮定すると、正しい結果が計算される、および Python`print`関数に結果を返す、**メッセージ**windows。

    **結果**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```

    取得中に**stdout**メッセージは、コードをテストするときに便利ですより多くの場合する必要があるアプリケーションで使用したり、テーブルに書き込むように表形式で結果を返します。

ここでは、これらのルールに注意してください。

+ 内のすべて、`@script`引数は有効な Python コードである必要があります。 
+ コードは、インデント、変数名、およびなどに関するすべての Python ルールに従う必要があります。 エラーが発生したときに、ホワイト スペースと大文字小文字の区別を確認します。
+ Python では、プログラミング言語間で、最も柔軟性が高いの 1 つ単一引用符と二重引用符に関してほぼ同義です。 ただし、T-SQL では、特定の情報のみに対して単一引用符を使用し、`@script`引数では、単一引用符を使用して、Unicode 文字列としての Python コードを囲みます。 そのため、Python コードを確認し、いくつかの単一引用符を二重引用符に変更する必要があります。
+ 既定で読み込まれていないすべてのライブラリを使用している場合は、読み込みに、スクリプトの先頭に import ステートメントを使用する必要があります。 SQL Server では、いくつかの製品に固有のライブラリを追加します。 詳細については、次を参照してください。 [Python ライブラリ](../python/python-libraries-and-data-types.md)します。
+ ライブラリがインストールされていない停止および」の説明に従って、SQL Server の外部での Python パッケージをインストールします。[SQL Server に新しい Python パッケージをインストールする](../python/install-additional-python-packages-on-sql-server.md)

## <a name="run-a-hello-world-script"></a>Hello World スクリプトを実行します。

次の演習では、別の単純な Python スクリプトを実行します。

```sql
EXEC sp_execute_external_script
@language =N'Python',
@script=N'OutputDataSet = InputDataSet',
@input_data_1 =N'SELECT 1 AS hello'
WITH RESULT SETS (([Hello World] int));
GO
```

このストアド プロシージャへの入力は次のとおりです。

+ *@language* パラメーターは、この場合は、Python を呼び出す言語拡張機能を定義します。
+ *@script* パラメーターは、Python のランタイムに渡されるコマンドを定義します。 Unicode テキストとして、この引数で、Python スクリプト全体を囲む必要があります。 **nvarchar** 型の変数にテキストを追加して、その変数を呼び出すこともできます。
+ *@input_data_1* データ フレームとして SQL Server へデータを返す Python ランタイムに渡される、クエリによってデータが返されます。
+ 句の結果セット列名として"Hello World"を追加する、SQL Server の返されたデータ テーブルのスキーマを定義します**int**データ型。

**結果**

| ハローワールド |
|-------------|
| 1 |

## <a name="next-steps"></a>次の手順

これで、複数の単純な Python スクリプトを実行すると、入力と出力の構成について詳しく見てを実行します。

> [!div class="nextstepaction"]
> [クイック スタート:入力と出力を処理します。](quickstart-python-run-using-t-sql.md)
