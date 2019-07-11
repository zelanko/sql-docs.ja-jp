---
title: mssqlctl bdc status reference
titleSuffix: SQL Server big data clusters
description: Mssqlctl bdc 状態コマンドに関する参照記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2f1b7f7c635b621c1c85953e63acc8f80bb52b01
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728557"
---
# <a name="mssqlctl-bdc-status"></a>mssqlctl bdc status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **bdc 状態**コマンドを**mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl bdc 状態の表示](#mssqlctl-bdc-status-show) | ビッグ データ クラスターの状態が表示されます。
## <a name="mssqlctl-bdc-status-show"></a>mssqlctl bdc status show
ビッグ データ クラスターの状態が表示されます。
```bash
mssqlctl bdc status show 
```
### <a name="examples"></a>使用例
ユーザーがログインしている BDC 状態です。
```bash
mssqlctl bdc status show
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

## <a name="next-steps"></a>次の手順

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。