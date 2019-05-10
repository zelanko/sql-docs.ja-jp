---
title: mssqlctl クラスター デバッグ リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl クラスター デバッグ コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5099a9ac611602e0c4c8d7f0103421e34b7fa8a2
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774861"
---
# <a name="mssqlctl-cluster-debug"></a>mssqlctl クラスターのデバッグ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**クラスター デバッグ**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl cluster debug copy-logs](#mssqlctl-cluster-debug-copy-logs) | ログをコピーします。
[mssqlctl クラスター デバッグ ダンプ](#mssqlctl-cluster-debug-dump) | トリガー ログのダンプします。
## <a name="mssqlctl-cluster-debug-copy-logs"></a>mssqlctl cluster debug copy-logs
クラスターから、デバッグ ログをコピーします。
```bash
mssqlctl cluster debug copy-logs --namespace -n 
                                 [--container -c]  
                                 [--target-folder -d]  
                                 [--pod -p]  
                                 [--timeout -t]
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--namespace -n`
クラスター名 kubernetes 名前空間に使用をします。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--container -c`
ログのコピーのような名前のコンテナーでは、省略可能、既定ではコピーのすべてのコンテナーのログ。 複数回を指定できません。 複数回指定すると場合、前回使用します。
#### `--target-folder -d`
ログをコピーする対象のフォルダー パス。 省略可能で、既定では、ローカル フォルダーのまま、結果を作成します。  複数回を指定できません。 複数回指定すると場合、前回使用します。
#### `--pod -p`
類似した名前のポッドのログをコピーします。 すべてのポッドの既定のコピー ログが省略可能です。 複数回を指定できません。 複数回指定すると場合、前回使用します。
#### `--timeout -t`
コマンドが完了するまで待機する秒数。 既定値は 0 は無制限を
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
## <a name="mssqlctl-cluster-debug-dump"></a>mssqlctl cluster debug dump
ログのダンプをトリガーし、コンテナーからコピーします。
```bash
mssqlctl cluster debug dump --namespace -n 
                            --container -c  
                            [--target-folder -d]
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--namespace -n`
クラスター名 kubernetes 名前空間に使用をします。
#### `--container -c`
ログのコピーのような名前のコンテナーでは、省略可能、既定ではコピーのすべてのコンテナーのログ。 複数回を指定できません。 複数回指定すると場合、前回使用します。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--target-folder -d`
ログをコピーする対象のフォルダー パス。 省略可能で、既定では、ローカル フォルダーのまま、結果を作成します。  複数回を指定できません。 複数回指定すると場合、前回使用します。 `./output/dump`
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