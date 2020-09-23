---
title: azdata sql リファレンス
titleSuffix: SQL Server big data clusters
description: azdata sql コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9965c6805cb8e12e6a5a2990a43bb7bf7c937fe1
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733702"
---
# <a name="azdata-sql"></a>azdata sql

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

以下の記事では、`azdata` ツールの `sql` コマンドに関するリファレンスを提供します。 `azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください。

## <a name="commands"></a>コマンド
| command | 説明 |
| --- | --- |
[azdata sql shell](#azdata-sql-shell) | SQL Database CLI により、ユーザーは T-SQL を使用して SQL Server を操作できます。
[azdata sql query](#azdata-sql-query) | クエリ コマンドを使用すると、T-SQL クエリを実行できます。
## <a name="azdata-sql-shell"></a>azdata sql shell
SQL Database CLI により、ユーザーは T-SQL を使用して SQL Server を操作できます。
```bash
azdata sql shell 
```
### <a name="examples"></a>例
対話型エクスペリエンスを開始するコマンド ラインの例。
```bash
azdata sql shell
```
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。
## <a name="azdata-sql-query"></a>azdata sql query
クエリ コマンドを使用すると、T-SQL クエリを実行できます。
```bash
azdata sql query --database -d 
                 -q
```
### <a name="examples"></a>例
テーブル名の一覧を選択します。  データベースの既定値は master です。
```bash
azdata sql query "SELECT name FROM SYS.TABLES"
```
### <a name="required-parameters"></a>必須のパラメーター
#### `--database -d`
クエリを実行するデータベース。  既定値は master です。
#### `-q`
実行する SQL クエリ。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。

## <a name="next-steps"></a>次のステップ

`azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください。 `azdata` ツールのインストール方法の詳細については、[SQL Server 2019 ビッグ データ クラスターを管理する azdata のインストール](../install/deploy-install-azdata.md)に関するページを参照してください。
