---
title: mssqlctl リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ebd3b63d641c77dae1afbff21264ec4fe34df4d0
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775505"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **mssqlctl**用のツール[SQL Server 2019 ビッグ データ クラスター (プレビュー)](big-data-cluster-overview.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
|[mssqlctl アプリ](reference-mssqlctl-app.md) | 作成、削除、実行、およびアプリケーションを管理します。 |
|[mssqlctl クラスター](reference-mssqlctl-cluster.md) | 選択、管理、およびクラスターを操作します。 |
[mssqlctl login](#mssqlctl-login) | クラスターにログインします。
[mssqlctl logout](#mssqlctl-logout) | クラスターからログアウトします。
|[mssqlctl ストレージ](reference-mssqlctl-storage.md) | クラスター記憶域を管理します。 |
## <a name="mssqlctl-login"></a>mssqlctl login
クラスターにログインします。
```bash
mssqlctl login [--username -u] 
               [--password -p]  
               [--endpoint -e]
```
### <a name="examples"></a>使用例
対話形式でログインします。
```bash
mssqlctl login
```
ユーザー名とパスワードでログインします。
```bash
mssqlctl login -u johndoe@contoso.com -p VerySecret
```
ユーザー名、パスワード、およびクラスター エンドポイントを使用してログインします。
```bash
mssqlctl login -u johndoe@contoso.com -p VerySecret --endpoint https://host.com:12800
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--username -u`
アカウントのユーザー。
#### `--password -p`
パスワードの資格情報。
#### `--endpoint -e`
クラスターのホストとポート (ex)"http://host:port"。
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
## <a name="mssqlctl-logout"></a>mssqlctl logout
クラスターからログアウトします。
```bash
mssqlctl logout 
```
### <a name="examples"></a>使用例
このユーザーをログアウトします。
```bash
mssqlctl logout
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

## <a name="next-steps"></a>次のステップ

インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。