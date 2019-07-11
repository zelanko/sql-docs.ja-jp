---
title: mssqlctl sql リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl sql コマンドに関する参照記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 844ea94e9df18132fd0729745ff154783b578fc1
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728509"
---
# <a name="mssqlctl-sql"></a>mssqlctl sql

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **sql**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl sql シェル](#mssqlctl-sql-shell) | SQL DB の CLI には、T-SQL を使用して SQL Server との対話をユーザーができます。
[mssqlctl sql クエリ](#mssqlctl-sql-query) | クエリ コマンドでは、T-SQL クエリの実行が許可されます。
## <a name="mssqlctl-sql-shell"></a>mssqlctl sql シェル
SQL DB の CLI には、T-SQL を使用して SQL Server との対話をユーザーができます。
```bash
mssqlctl sql shell 
```
### <a name="examples"></a>使用例
コマンドラインの例を対話型エクスペリエンスを開始します。
```bash
mssqlctl sql shell
```
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-sql-query"></a>mssqlctl sql クエリ
クエリ コマンドでは、T-SQL クエリの実行が許可されます。
```bash
mssqlctl sql query --database -d 
                   -q
```
### <a name="examples"></a>使用例
テーブル名のリストを選択します。  マスターへのデータベースの既定値です。
```bash
mssqlctl sql query 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--database -d`
クエリを実行するデータベースです。  既定値は master です。
#### `-q`
実行する T-SQL クエリ。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。

## <a name="next-steps"></a>次の手順

インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。