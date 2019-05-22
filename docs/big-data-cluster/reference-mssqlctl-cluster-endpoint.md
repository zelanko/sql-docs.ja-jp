---
title: mssqlctl クラスター エンドポイント参照
titleSuffix: SQL Server big data clusters
description: Mssqlctl クラスター エンドポイント コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 32c0506a3394ac6ac62745901f908ba1fb725ec2
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65995140"
---
# <a name="mssqlctl-cluster-endpoint"></a>mssqlctl クラスター エンドポイント

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**クラスター エンドポイント**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl クラスター エンドポイントの一覧](#mssqlctl-cluster-endpoint-list) | クラスターのエンドポイントを示しています。
## <a name="mssqlctl-cluster-endpoint-list"></a>mssqlctl クラスター エンドポイントの一覧
クラスターのエンドポイントを示しています。
```bash
mssqlctl cluster endpoint list [--endpoint-name -e] 
                               
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--endpoint-name -e`
クラスター エンドポイントの名前。
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

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。