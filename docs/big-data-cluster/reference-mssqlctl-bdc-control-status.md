---
title: mssqlctl bdc コントロールの状態の参照
titleSuffix: SQL Server big data clusters
description: Mssqlctl bdc コントロールの状態コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 714ed2152dfff071193a7c33ed29e5fcb9ec8f17
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394394"
---
# <a name="mssqlctl-bdc-control-status"></a>mssqlctl bdc コントロールの状態

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供します、 **bdc コントロール状態**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl bdc コントロールの状態の表示](#mssqlctl-bdc-control-status-show) | コントロールの状態です。
## <a name="mssqlctl-bdc-control-status-show"></a>mssqlctl bdc コントロールの状態の表示
コントロールの状態です。
```bash
mssqlctl bdc control status show 
```
### <a name="examples"></a>使用例
コントロールの状態を取得します。
```bash
mssqlctl bdc control status show
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