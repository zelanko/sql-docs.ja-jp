---
title: azdata bdc spark ステートメントリファレンス
titleSuffix: SQL Server big data clusters
description: Azdata bdc spark ステートメントコマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 778980ac6b93e7db79d59182fbd18ab4cfdb8b75
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426092"
---
# <a name="azdata-bdc-spark-statement"></a>azdata bdc spark ステートメント

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

次の記事では、 **azdata**ツールでの**bdc spark ステートメント**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata リファレンス](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc spark ステートメントの一覧](#azdata-bdc-spark-statement-list) | 指定された Spark セッション内のすべてのステートメントを一覧表示します。
[azdata bdc spark ステートメントの作成](#azdata-bdc-spark-statement-create) | 指定されたセッションで、新しい Spark ステートメントを作成します。
[azdata bdc spark ステートメントの情報](#azdata-bdc-spark-statement-info) | 指定された Spark セッションで、要求されたステートメントに関する情報を取得します。
[azdata bdc spark ステートメントのキャンセル](#azdata-bdc-spark-statement-cancel) | 指定された Spark セッション内のステートメントをキャンセルします。
## <a name="azdata-bdc-spark-statement-list"></a>azdata bdc spark ステートメントの一覧
指定された Spark セッション内のすべてのステートメントを一覧表示します。
```bash
azdata bdc spark statement list --session-id -i 
                                
```
### <a name="examples"></a>使用例
すべてのセッションステートメントを一覧表示します。
```bash
azdata spark statement list --session-id 0
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
## <a name="azdata-bdc-spark-statement-create"></a>azdata bdc spark ステートメントの作成
これにより、指定されたセッションで新しいステートメントが作成され、実行されます。  実行が簡単な場合、結果には実行からの出力が含まれます。  それ以外の場合、ステートメントの完了後に "spark session info" を使用して結果を取得できます。
```bash
azdata bdc spark statement create --session-id -i 
                                  --code -c
```
### <a name="examples"></a>使用例
ステートメントを実行します。
```bash
azdata spark statement create --session-id 0 --code "2+2"
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--session-id -i`
Spark セッション ID 番号。
#### `--code -c`
ステートメントの一部として実行するコードを含む文字列。
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
## <a name="azdata-bdc-spark-statement-info"></a>azdata bdc spark ステートメントの情報
ステートメントが完了すると、実行状態と実行結果が取得されます。 ' Spark statement create ' からステートメント id が返されます。
```bash
azdata bdc spark statement info --session-id -i 
                                --statement-id -s
```
### <a name="examples"></a>使用例
ID が0、ステートメント ID が0のセッションのステートメント情報を取得します。
```bash
azdata spark statement info --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--session-id -i`
Spark セッション ID 番号。
#### `--statement-id -s`
指定されたセッション ID 内の Spark ステートメント ID 番号。
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
## <a name="azdata-bdc-spark-statement-cancel"></a>azdata bdc spark ステートメントのキャンセル
これにより、指定された Spark セッション内のステートメントが取り消されます。 ' Spark statement create ' からステートメント id が返されます。
```bash
azdata bdc spark statement cancel --session-id -i 
                                  --statement-id -s
```
### <a name="examples"></a>使用例
ステートメントをキャンセルします。
```bash
azdata spark statement cancel --session-id 0 --statement-id 0
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--session-id -i`
Spark セッション ID 番号。
#### `--statement-id -s`
指定されたセッション ID 内の Spark ステートメント ID 番号。
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
