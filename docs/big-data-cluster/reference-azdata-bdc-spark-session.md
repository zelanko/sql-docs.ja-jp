---
title: azdata bdc spark セッションリファレンス
titleSuffix: SQL Server big data clusters
description: Azdata bdc spark session コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 20b7ac3dcf72482e80278ce0f0df922026232a6d
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426102"
---
# <a name="azdata-bdc-spark-session"></a>azdata bdc spark セッション

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

次の記事では、 **azdata**ツールでの**bdc spark session**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata リファレンス](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc spark セッションの作成](#azdata-bdc-spark-session-create) | 新しい Spark セッションを作成します。
[azdata bdc spark セッションリスト](#azdata-bdc-spark-session-list) | Spark 内のすべてのアクティブなセッションを一覧表示します。
[azdata bdc spark セッション情報](#azdata-bdc-spark-session-info) | アクティブな Spark セッションに関する情報を取得します。
[azdata bdc spark セッションログ](#azdata-bdc-spark-session-log) | アクティブな Spark セッションの実行ログを取得します。
[azdata bdc spark セッション状態](#azdata-bdc-spark-session-state) | アクティブな Spark セッションの実行状態を取得します。
[azdata bdc spark セッションの削除](#azdata-bdc-spark-session-delete) | Spark セッションを削除します。
## <a name="azdata-bdc-spark-session-create"></a>azdata bdc spark セッションの作成
これにより、新しい対話型の Spark セッションが作成されます。 呼び出し元は、Spark セッションの種類を指定する必要があります。 このセッションは azdata execution の有効期間を超えているため、' spark session delete ' で削除する必要があります
```bash
azdata bdc spark session create [--session-kind -k] 
                                [--jar-files -j]  
                                [--py-files -p]  
                                [--files -f]  
                                [--driver-memory]  
                                [--driver-cores]  
                                [--executor-memory]  
                                [--executor-cores]  
                                [--executor-count]  
                                [--archives -a]  
                                [--queue -q]  
                                [--name -n]  
                                [--config -c]  
                                [--timeout-seconds -t]
```
### <a name="examples"></a>使用例
セッションを作成します。
```bash
azdata spark session create --session-kind pyspark
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--session-kind -k`
作成するセッションの種類の名前。  Spark、pyspark、sparkr、または sql のいずれか。
#### `--jar-files -j`
Jar ファイルパスの一覧。  リストを渡すには、値をエンコードします。  例: ' ["entry1", "entry2"] '。
#### `--py-files -p`
Python ファイルパスの一覧。  リストを渡すには、値をエンコードします。  例: ' ["entry1", "entry2"] '。
#### `--files -f`
ファイルパスの一覧。  リストを渡すには、値をエンコードします。  例: ' ["entry1", "entry2"] '。
#### `--driver-memory`
ドライバーに割り当てるメモリの量。  単位を値の一部として指定します。  例512M または2G。
#### `--driver-cores`
ドライバーに割り当てる CPU コアの量。
#### `--executor-memory`
実行プログラムに割り当てるメモリの量。  単位を値の一部として指定します。  例512M または2G。
#### `--executor-cores`
実行プログラムに割り当てる CPU コアの量。
#### `--executor-count`
実行する実行プログラムのインスタンスの数。
#### `--archives -a`
アーカイブパスの一覧。  リストを渡すには、値をエンコードします。  例: ' ["entry1", "entry2"] '。
#### `--queue -q`
セッションを実行する Spark キューの名前。
#### `--name -n`
Spark セッションの名前。
#### `--config -c`
Spark 構成値を含む名前と値のペアの一覧。  JSON ディクショナリとしてエンコードされます。  例: ' {"name": "value", "name2": "value2"} '。
#### `--timeout-seconds -t`
セッションのアイドルタイムアウト (秒)。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-spark-session-list"></a>azdata bdc spark セッションリスト
Spark 内のすべてのアクティブなセッションを一覧表示します。
```bash
azdata bdc spark session list 
```
### <a name="examples"></a>使用例
すべてのアクティブなセッションを一覧表示します。
```bash
azdata spark session list
```
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-spark-session-info"></a>azdata bdc spark セッション情報
これにより、指定された ID を持つアクティブな Spark セッションのセッション情報が取得されます。  ' Spark session create ' からセッション id が返されます。
```bash
azdata bdc spark session info --session-id -i 
                              
```
### <a name="examples"></a>使用例
ID が0のセッションのセッション情報を取得します。
```bash
azdata spark session info --session-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--session-id -i`
Spark セッション ID 番号。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-spark-session-log"></a>azdata bdc spark セッションログ
これは、指定された ID を持つアクティブな Spark セッションのセッションログエントリを取得します。  ' Spark session create ' からセッション id が返されます。
```bash
azdata bdc spark session log --session-id -i 
                             
```
### <a name="examples"></a>使用例
ID が0のセッションのセッションログを取得します。
```bash
azdata spark session log --session-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--session-id -i`
Spark セッション ID 番号。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-spark-session-state"></a>azdata bdc spark セッション状態
これにより、指定された ID を持つアクティブな Spark セッションのセッション状態が取得されます。  ' Spark session create ' からセッション id が返されます。
```bash
azdata bdc spark session state --session-id -i 
                               
```
### <a name="examples"></a>使用例
ID が0のセッションのセッション状態を取得します。
```bash
azdata spark session state --session-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--session-id -i`
Spark セッション ID 番号。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-spark-session-delete"></a>azdata bdc spark セッションの削除
これにより、対話型の Spark セッションが削除されます。 ' Spark session create ' からセッション id が返されます。
```bash
azdata bdc spark session delete --session-id -i 
                                
```
### <a name="examples"></a>使用例
セッションを削除します。
```bash
azdata spark session delete --session-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--session-id -i`
Spark セッション ID 番号。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。

## <a name="next-steps"></a>次の手順

その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。 **Azdata**ツールをインストールする方法の詳細については、「 [Azdata をインストールして SQL Server 2019 ビッグデータクラスターを管理する](deploy-install-azdata.md)」を参照してください。
