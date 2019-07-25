---
title: azdata notebook リファレンス
titleSuffix: SQL Server big data clusters
description: Azdata notebook コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b96c5e06ec51f53964a28cac86f385d6b42c1dc4
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426012"
---
# <a name="azdata-notebook"></a>azdata notebook

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールの**notebook**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata リファレンス](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata notebook ビュー](#azdata-notebook-view) | Notebook を表示します。  最初のセル実行エラー時に停止するオプションです。
[azdata notebook の実行](#azdata-notebook-run) | Notebook を実行します。  最初のエラーで実行が停止します。
## <a name="azdata-notebook-view"></a>azdata notebook ビュー
このコマンドは notebook ファイルを取得し、markdown、code、および output を color ターミナル形式に変換できます。
```bash
azdata notebook view --path -p 
                     [--continue-on-error -c]
```
### <a name="examples"></a>使用例
Notebook を表示します。  これにより、すべてのセルが表示されます。
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb'
```
Notebook を表示します。  これにより、出力にエラーのあるセルが検出されない限り、すべてのセルが表示されます。  その場合、出力は停止します。
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb' --stop-on-error
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
表示するノートブックのパス。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--continue-on-error -c`
ノートブックの出力で見つかったセルエラーを無視して、その他のセルを表示し続けます。  既定の動作では、エラー発生時に停止します。  停止すると、エラーが発生した最初のセルが見やすくなります。
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
## <a name="azdata-notebook-run"></a>azdata notebook の実行
このコマンドは、一時ディレクトリを作成し、作業ディレクトリとして指定されたノートブックを実行します。
```bash
azdata notebook run --path -p 
                    [--output-path]  
                    [--output-html]
```
### <a name="examples"></a>使用例
Notebook を実行します。
```bash
azdata notebook run --path '/home/me/notebooks/demo_notebook.ipynb'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--path -p`
実行するノートブックへのファイルパス。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--output-path`
Notebook の出力に使用するディレクトリパス。  出力データを含むノートブックと、ノートブックによって生成されるファイルは、このディレクトリに対して相対的に生成されます。
#### `--output-html`
省略可能なフラグ indicatingg 出力 notebook を HTML 形式にさらに変換するかどうかを指定します。  2番目の出力ファイルを作成します。
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

**Azdata**ツールをインストールする方法の詳細については、「 [Azdata をインストールして SQL Server 2019 ビッグデータクラスターを管理する](deploy-install-azdata.md)」を参照してください。
