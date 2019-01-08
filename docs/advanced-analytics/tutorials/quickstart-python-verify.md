---
title: Python を検証するためのクイック スタートは、SQL Server に存在します
description: Python と Machine Learning サービスが SQL server が存在するかを確認するためのクイック スタートです。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7a2e9bf58839832ba29b103d2e862a845090a9f1
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046917"
---
# <a name="quickstart-verify-python-exists-in-sql-server"></a>クイック スタート:Python は、SQL Server に存在することを確認します。 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server には、常駐の SQL Server データでのデータ科学分析用の Python 言語サポートが含まれています。 スクリプトの実行は、次の方法のいずれかを使用して、ストアド プロシージャです。

+ 組み込み[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)ストアド プロシージャでの Python スクリプトを入力パラメーターとして渡します。
+ Python スクリプトをラップする[カスタム ストアド プロシージャ](sqldev-in-database-r-for-sql-developers.md)作成します。

このクイック スタートで、ことを確認は[SQL Server 2017 Machine Learning Services](../what-is-sql-server-machine-learning.md)をインストールして構成します。

## <a name="prerequisites"></a>前提条件

この演習で SQL Server のインスタンスへのアクセスを必要と[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)をインストールします。

SQL Server インスタンスは、Azure の仮想マシンまたはオンプレミスにできます。 注意する必要がありますので、既定で外部のスクリプト機能は無効にされる[外部スクリプトを有効に](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature)ことを確認します**SQL Server スタート パッド サービス**が実行されているは、開始する前にします。

SQL クエリを実行するためのツールも必要です。 任意のデータベース管理を使用して Python スクリプトを実行したり、ツール、SQL Server インスタンスに接続し、T-SQL クエリまたはストアド プロシージャを実行する限りのクエリを実行できます。 このクイック スタートを使用して[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)します。

## <a name="verify-python-exists"></a>Python の存在を確認します。

確認できます (は、SQL Server インスタンスと Python のバージョンがインストールされている有効その Machine Learning サービスです。 次の手順に従います。

1. SQL Server Management Studio を開き、SQL Server インスタンスに接続します。

2. 次のコードを実行します。 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import sys
    print(sys.version)';
    GO
    ```

3. Python`print`にバージョンを返します、**メッセージ**ウィンドウ。 次の例の出力で確認できます SQL Server がここで Python バージョン 3.5.2 インストールであります。

    **結果**

    ```text
    STDOUT message(s) from external script: 
    3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
    ```

エラーが発生する場合のさまざまなインスタンスと Python が通信できるようにすることがあります。

最初に、インストールの問題を排除します。 インストール後の構成は、外部コード ライブラリの使用を有効にする必要があります。 参照してください[SQL Server 2017 の Machine Learning サービスをインストール](../install/sql-machine-learning-services-windows-install.md)します。 同様に、スタート パッド サービスが実行されていることを確認します。

Windows ユーザー グループを追加することも必要があります。`SQLRUserGroup`スタート パッドで Python と SQL Server 間の通信を提供できることを確認する、インスタンス上のログインとして。 (同じグループが両方の R の使用し、Python コードの実行)。詳細については、次を参照してください。[暗黙の認証を有効](../security/add-sqlrusergroup-to-database.md)します。

さらに、無効になっているネットワーク プロトコルを有効にまたは SQL Server が外部クライアントと通信できるようにファイアウォールを開く必要があります。 詳細については、次を参照してください。[セットアップのトラブルシューティング](../common-issues-external-script-execution.md)します。

## <a name="call-revoscalepy-functions"></a>Revoscalepy 関数を呼び出す

確認する**revoscalepy**を含むスクリプトの例を実行する使用可能な[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary)統計概要データを生成します。 次のスクリプトでは、revoscalepy に含まれている組み込みのサンプルからサンプル .xdf データ ファイルを取得する方法を示します。 RxOptions 関数は、提供、 **sampleDataDir**サンプル ファイルの場所を返すパラメーターです。

Rx_summary 型のオブジェクトを返すため`class revoscalepy.functions.RxSummary.RxSummaryResults`、複数の要素が含まれています、pandas を使用して表形式でデータ フレームだけを抽出することができます。

```sql
EXEC sp_execute_external_script @language = N'Python', 
@script = N'
import os
from pandas import DataFrame
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions

sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay + DayOfWeek", ds)
print(summary)
dfsummary = summary.summary_data_frame
OutputDataSet = dfsummary
'
WITH RESULT SETS  ((ColName nvarchar(25) , ColMean float, ColStdDev  float, ColMin  float,   ColMax  float, Col_ValidObs  float, Col_MissingObs int))
```

## <a name="list-python-packages"></a>Python パッケージを一覧表示します。

Microsoft は、多くの SQL Server インスタンスで Machine Learning サービスと共にプレインストール Python パッケージを提供します。 バージョンを含め、パッケージがインストールされている Python の一覧を表示するには、次の手順に従います。

1. SQL Server インスタンスでは、以下のスクリプトを実行します。

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import pip
    for i in pip.get_installed_distributions():
        print(i)';
    GO
    ```

2. 出力は`pip.get_installed_distributions()`python として返されると`STDOUT`メッセージ。

    **結果**

    ```text
    STDOUT message(s) from external script: 
    xlwt 1.2.0
    XlsxWriter 0.9.6
    xlrd 1.0.0
    win-unicode-console 0.5
    widgetsnbextension 2.0.0
    wheel 0.29.0
    Werkzeug 0.12.1
    wcwidth 0.1.7
    unicodecsv 0.14.1
    traitlets 4.3.2
    tornado 4.4.2
    toolz 0.8.2
    testpath 0.3
    tables 3.2.2
    sympy 1.0
    statsmodels 0.8.0
    sqlparse 0.1.19
    SQLAlchemy 1.1.9
    snowballstemmer 1.2.1
    six 1.10.0
    simplegeneric 0.8.1
    seaborn 0.7.1
    scipy 0.19.0
    scikit-learn 0.18.1
    ...
    ```

## <a name="next-steps"></a>次の手順

これで、インスタンスは、Python を使用する準備が確認した後、基本的な Python の対話について詳しく見てを実行します。

> [!div class="nextstepaction"]
> [クイック スタート:SQL Server での Python スクリプトの"hello world" ](quickstart-python-run-using-t-sql.md)
