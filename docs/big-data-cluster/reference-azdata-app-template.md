---
title: azdata アプリテンプレートリファレンス
titleSuffix: SQL Server big data clusters
description: Azdata app テンプレートコマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3b257a2bacc56a7907ab0d25f492ed0ebd605543
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426332"
---
# <a name="azdata-app-template"></a>azdata アプリテンプレート

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールでの**アプリテンプレート**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata アプリテンプレートの一覧](#azdata-app-template-list) | サポートされているテンプレートを取得します。
[azdata アプリテンプレートのプル](#azdata-app-template-pull) | サポートされているテンプレートをダウンロードします。
## <a name="azdata-app-template-list"></a>azdata アプリテンプレートの一覧
指定された [URL] github リポジトリでサポートされているテンプレートを取得します。
```bash
azdata app template list [--url -u] 
                         
```
### <a name="examples"></a>使用例
既定のテンプレートリポジトリの場所にあるすべてのテンプレートを取得します。
```bash
azdata app template list
```
別のリポジトリの場所にあるすべてのテンプレートをフェッチします。
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--url -u`
別のテンプレートリポジトリの場所を指定してください。 標準 https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="azdata-app-template-pull"></a>azdata アプリテンプレートのプル
指定された [URL] github リポジトリで、サポートされているテンプレートをダウンロードします。
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         [--destination -d]
```
### <a name="examples"></a>使用例
テンプレートリポジトリの既定の場所にあるすべてのテンプレートをダウンロードします。
```bash
azdata app template pull
```
別のリポジトリの場所にあるすべてのテンプレートをダウンロードします。
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
個々のテンプレートを名前でダウンロードします。
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--name -n`
テンプレート名。 サポートされているテンプレート namesrun の完全な一覧については、`azdata app template list`
#### `--url -u`
別のテンプレートリポジトリの場所を指定してください。 標準 https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
アプリケーションスケルトンテンプレートを配置する場所。
`./templates`
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
