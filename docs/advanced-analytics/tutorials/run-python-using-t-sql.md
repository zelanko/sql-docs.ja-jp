---
title: "T-SQL を使用して Python を実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- Python
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: ea8010bb51e02e9676653bb0dc2f12cbfe02761a
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="run-python-using-t-sql"></a>T-SQL を使用して実行の Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この例は、ストアド プロシージャを使用して、SQL Server で単純な Python スクリプトを実行する方法を示しています[sp_execute_external_script。](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

## <a name="step-1-create-the-test-data-table"></a>手順 1. テスト データ テーブルを作成します。

最初に、ソース データへの週の曜日名のマッピング時に使用する、追加のデータを作成します。 テーブルの作成に次の T-SQL ステートメントを実行します。

```SQL
CREATE TABLE PythonTest (
    [DayOfWeek] varchar(10) NOT NULL,
    [Amount] float NOT NULL
    )
GO

INSERT INTO PythonTest VALUES
('Sunday', 10.0),
('Monday', 11.1),
('Tuesday', 12.2),
('Wednesday', 13.3),
('Thursday', 14.4),
('Friday', 15.5),
('Saturday', 16.6),
('Friday', 17.7),
('Monday', 18.8),
('Sunday', 19.9)
GO
```

## <a name="step-2-run-the-hello-world-script"></a>手順 2. "Hello World"のスクリプトを実行します。

次のコード Python 実行可能ファイル、入力のデータを渡しますを読み込んで、入力データの各行の曜日単位のインデックスを表す数で、テーブルの曜日名を更新します。

パラメーターのメモ *@RowsPerRead*です。 このパラメーターは、SQL Server から Python ランタイムに渡される行の数を指定します。

呼ばれる、Python データ分析ライブラリ**パンダ**の SQL Server にデータを渡すことが必要、および既定では、Machine Learning のサービスは含まれています。

```sql
DECLARE @ParamINT INT = 1234567
DECLARE @ParamCharN VARCHAR(6) = 'INPUT '

print '------------------------------------------------------------------------'
print 'Output parameters (before):'
print FORMATMESSAGE('ParamINT=%d', @ParamINT)
print FORMATMESSAGE('ParamCharN=%s', @ParamCharN)

print 'Dataset (before):'
SELECT * FROM PythonTest

print '------------------------------------------------------------------------'
print 'Dataset (after):'
DECLARE @RowsPerRead INT = 5

execute sp_execute_external_script 
@language = N'Python',
@script = N'
import sys
import os
print("*******************************")
print(sys.version)
print("Hello World")
print(os.getcwd())
print("*******************************")
if ParamINT == 1234567:
       ParamINT = 1
else:
       ParamINT += 1

ParamCharN="OUTPUT"
OutputDataSet = InputDataSet

global daysMap

daysMap = {
       "Monday" : 1,
       "Tuesday" : 2,
       "Wednesday" : 3,
       "Thursday" : 4,
       "Friday" : 5,
       "Saturday" : 6,
       "Sunday" : 7
       }

OutputDataSet["DayOfWeek"] = pandas.Series([daysMap[i] for i in OutputDataSet["DayOfWeek"]], index = OutputDataSet.index, dtype = "int32")
', 
@input_data_1 = N'SELECT * FROM PythonTest', 
@params = N'@r_rowsPerRead INT, @ParamINT INT OUTPUT, @ParamCharN CHAR(6) OUTPUT',
@r_rowsPerRead = @RowsPerRead,
@paramINT = @ParamINT OUTPUT,
@paramCharN = @ParamCharN OUTPUT
with result sets (("DayOfWeek" int null, "Amount" float null))

print 'Output parameters (after):'
print FORMATMESSAGE('ParamINT=%d', @ParamINT)
print FORMATMESSAGE('ParamCharN=%s', @ParamCharN)
GO
```

> [!TIP]
> このストアド プロシージャのパラメーターがこのクイック スタートで詳しく説明されている: [t-sql を使用して R コード](rtsql-using-r-code-in-transact-sql-quickstart.md)です。

## <a name="step-3-view-the-results"></a>手順 3. 結果を表示します。

ストアド プロシージャは、元のデータを取得し、Python スクリプトを適用で変更されたデータを返します、**結果**の Management Studio またはその他の SQL クエリ ツール ウィンドウです。


|DayOfWeek (変更前) に、| Amount|DayOfWeek (変更後) |
|-----|-----|-----|
|日曜日|10|7|
|月曜日|11.1|1|
|火曜日|12.2|2|
|水曜日|13.3|3|
|木曜日|14.4|4|
|金曜日|15.5|5|
|土曜日|16.6|6|
|金曜日|17.7|5|
|月曜日|18.8|1|
|日曜日|19.9|7|

内のメッセージとして返されるステータス メッセージ、または Python コンソールに返されるエラー、**クエリ**ウィンドウです。 次に表示される出力の抜粋を示します。

*サンプルの結果*

```
Output parameters (before):
ParamINT=1234567
ParamCharN=INPUT 
Dataset (before):

(10 rows affected)

Dataset (after):
STDOUT message(s) from external script: 
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy

3.5.2 |Anaconda 4.2.0 (64-bit)| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
Hello World
C:\PROGRA~1\MICROS~2\MSSQL1~1.MSS\MSSQL\EXTENS~1\MSSQLSERVER01\7A70B3FB-FBA2-4C52-96D6-8634DB843229

3.5.2 |Anaconda 4.2.0 (64-bit)| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
Hello World
C:\PROGRA~1\MICROS~2\MSSQL1~1.MSS\MSSQL\EXTENS~1\MSSQLSERVER01\7A70B3FB-FBA2-4C52-96D6-8634DB843229

(10 rows affected)
Output parameters (after):
ParamINT=2
ParamCharN=OUTPUT
```

+ **メッセージ**出力には、スクリプトの実行に使用する作業ディレクトリが含まれています。 この例では MSSQLSERVER01 はジョブを管理する SQL Server によって割り当てられたワーカー アカウントを参照します。 

    GUID は、データとスクリプトの成果物を保管するスクリプトの実行中に作成された一時フォルダーの名前です。 これらの一時フォルダーは、SQL Server がセキュリティで保護されクリーンアップされます Windows ジョブ オブジェクトでスクリプトが終了した後です。

+ メッセージ"Hello World"が含まれたセクションでは、2 回を出力します。 これは、値の *@RowsPerRead*  5 に設定しは、テーブルの 10 行では Python を 2 つの呼び出しがテーブル内のすべての行を処理に必要なため、します。

    実行では、運用、各バッチで渡す必要がある行の最大数を決定する値が異なる試してみることをお勧めします。 最適な数の行のデータに依存するは、データセット内の列の番号の両方と渡されたデータの種類によって影響をします。

## <a name="resources"></a>リソース

これらの他の Python サンプルと高度なヒントと、エンド ツー エンドのデモ用のチュートリアルを参照してください。

+ [Python revoscalepy を使用してモデルを作成するには](use-python-revoscalepy-to-create-model.md)
+ [SQL 開発者のためのデータベースでの Python](sqldev-in-database-python-for-sql-developers.md)
+ [Python および SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

## <a name="troubleshooting"></a>トラブルシューティング

ストアド プロシージャを見つけられない場合`sp_execute_external_script`、おそらくが終了していない外部スクリプトの実行をサポートするためにインスタンスを構成することを意味します。 SQL Server 2017 セットアップを実行し、機械学習の言語としての Python を選択すると、後にする必要があります明示的に有効にする機能を使用して、 `sp_configure`、インスタンスを再起動します。 詳細については、「 [Python セットアップの Machine Learning サービス](../python/setup-python-machine-learning-services.md)です。