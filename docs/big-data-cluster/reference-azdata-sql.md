---
title: azdata sql リファレンス
titleSuffix: SQL Server big data clusters
description: Azdata sql コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 90512592901fcf83e4697b5eefc80a6df7aeb032
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426022"
---
# <a name="azdata-sql"></a>azdata sql

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールの**sql**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata sql シェル](#azdata-sql-shell) | SQL DB CLI を使用すると、ユーザーは T-sql を使用して SQL Server を操作できます。
[azdata sql クエリ](#azdata-sql-query) | クエリコマンドを使用すると、T-sql クエリを実行できます。
## <a name="azdata-sql-shell"></a>azdata sql シェル
SQL DB CLI を使用すると、ユーザーは T-sql を使用して SQL Server を操作できます。
```bash
azdata sql shell 
```
### <a name="examples"></a>使用例
対話型エクスペリエンスを開始するコマンドラインの例。
```bash
azdata sql shell
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
## <a name="azdata-sql-query"></a>azdata sql クエリ
クエリコマンドを使用すると、T-sql クエリを実行できます。
```bash
azdata sql query --database -d 
                 -q
```
### <a name="examples"></a>使用例
テーブル名の一覧を選択します。  データベースの既定値は master です。
```bash
azdata sql query 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--database -d`
クエリを実行するデータベースです。  既定値は master です。
#### `-q`
実行する t-sql クエリ。
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
