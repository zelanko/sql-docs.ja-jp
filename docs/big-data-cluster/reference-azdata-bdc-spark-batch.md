---
title: azdata bdc spark バッチリファレンス
titleSuffix: SQL Server big data clusters
description: Azdata bdc spark batch コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6e242b26f439b49dbf0b3cf5ab50ea46c273f45f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426162"
---
# <a name="azdata-bdc-spark-batch"></a>azdata bdc spark バッチ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールの**bdc spark batch**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata リファレンス](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc spark バッチ作成](#azdata-bdc-spark-batch-create) | 新しい Spark バッチを作成します。
[azdata bdc spark バッチ一覧](#azdata-bdc-spark-batch-list) | Spark 内のすべてのバッチを一覧表示します。
[azdata bdc spark バッチ情報](#azdata-bdc-spark-batch-info) | アクティブな Spark バッチに関する情報を取得します。
[azdata bdc spark バッチログ](#azdata-bdc-spark-batch-log) | Spark バッチの実行ログを取得します。
[azdata bdc spark バッチの状態](#azdata-bdc-spark-batch-state) | Spark バッチの実行状態を取得します。
[azdata bdc spark バッチの削除](#azdata-bdc-spark-batch-delete) | Spark バッチを削除します。
## <a name="azdata-bdc-spark-batch-create"></a>azdata bdc spark バッチ作成
これにより、指定されたコードを実行する新しい batch Spark ジョブが作成されます。
```bash
azdata bdc spark batch create --file -f 
                              [--class-name -c]  
                              [--arguments -a]  
                              [--jar-files -j]  
                              [--py-files -p]  
                              [--files]  
                              [--driver-memory]  
                              [--driver-cores]  
                              [--executor-memory]  
                              [--executor-cores]  
                              [--executor-count]  
                              [--archives]  
                              [--queue -q]  
                              [--name -n]  
                              [--config]
```
### <a name="examples"></a>使用例
新しい Spark バッチを作成します。
```bash
azdata spark batch create --code "2+2"
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--file -f`
実行するファイルのパス。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--class-name -c`
1つまたは複数の jar ファイルを渡すときに実行するクラスの名前。
#### `--arguments -a`
引数の一覧。  リストを渡すには、値をエンコードします。  例: ' ["entry1", "entry2"] '。
#### `--jar-files -j`
Jar ファイルパスの一覧。  リストを渡すには、値をエンコードします。  例: ' ["entry1", "entry2"] '。
#### `--py-files -p`
Python ファイルパスの一覧。  リストを渡すには、値をエンコードします。  例: ' ["entry1", "entry2"] '。
#### `--files`
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
#### `--archives`
アーカイブパスの一覧。  リストを渡すには、値をエンコードします。  例: ' ["entry1", "entry2"] '。
#### `--queue -q`
セッションを実行する Spark キューの名前。
#### `--name -n`
Spark セッションの名前。
#### `--config`
Spark 構成値を含む名前と値のペアの一覧。  JSON ディクショナリとしてエンコードされます。  例: ' {"name": "value", "name2": "value2"} '。
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
## <a name="azdata-bdc-spark-batch-list"></a>azdata bdc spark バッチ一覧
Spark 内のすべてのバッチを一覧表示します。
```bash
azdata bdc spark batch list 
```
### <a name="examples"></a>使用例
すべてのアクティブなバッチを一覧表示します。
```bash
azdata spark batch list
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
## <a name="azdata-bdc-spark-batch-info"></a>azdata bdc spark バッチ情報
これにより、指定された ID を持つ Spark バッチの情報が取得されます。  "Spark batch create" からバッチ id が返されます。
```bash
azdata bdc spark batch info --batch-id -i 
                            
```
### <a name="examples"></a>使用例
ID が0のバッチのバッチ情報を取得します。
```bash
azdata spark batch info --batch-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--batch-id -i`
Spark バッチ ID 番号。
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
## <a name="azdata-bdc-spark-batch-log"></a>azdata bdc spark バッチログ
これにより、指定された ID を持つ Spark バッチのバッチログエントリが取得されます。  "Spark batch create" からバッチ id が返されます。
```bash
azdata bdc spark batch log --batch-id -i 
                           
```
### <a name="examples"></a>使用例
ID が0のバッチのバッチログを取得します。
```bash
azdata spark batch log --batch-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--batch-id -i`
Spark バッチ ID 番号。
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
## <a name="azdata-bdc-spark-batch-state"></a>azdata bdc spark バッチの状態
これにより、指定された ID を持つ Spark バッチのバッチ状態が取得されます。  "Spark batch create" からバッチ id が返されます。
```bash
azdata bdc spark batch state --batch-id -i 
                             
```
### <a name="examples"></a>使用例
ID が0のバッチのバッチの状態を取得します。
```bash
azdata spark batch state --batch-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--batch-id -i`
Spark バッチ ID 番号。
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
## <a name="azdata-bdc-spark-batch-delete"></a>azdata bdc spark バッチの削除
これにより、Spark バッチが削除されます。 "Spark batch create" からバッチ id が返されます。
```bash
azdata bdc spark batch delete --batch-id -i 
                              
```
### <a name="examples"></a>使用例
バッチを削除します。
```bash
azdata spark batch delete --batch-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--batch-id -i`
Spark バッチ ID 番号。
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
