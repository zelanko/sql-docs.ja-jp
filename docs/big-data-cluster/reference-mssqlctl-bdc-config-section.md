---
title: mssqlctl bdc config section reference
titleSuffix: SQL Server big data clusters
description: Mssqlctl bdc 構成セクションのコマンドに関する参照記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3ca96ddbbf64b04e8ccd8854a8338fe6e118debb
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728695"
---
# <a name="mssqlctl-bdc-config-section"></a>mssqlctl bdc config section

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **bdc 構成セクション**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl bdc config section show](#mssqlctl-bdc-config-section-show) | 構成プロファイルからのセクションを取得します。
[mssqlctl bdc config section set](#mssqlctl-bdc-config-section-set) | 構成プロファイルのセクションを設定します。
## <a name="mssqlctl-bdc-config-section-show"></a>mssqlctl bdc config section show
指定された json パスに従って、選択した構成プロファイルから、指定されたセクションを取得します。
```bash
mssqlctl bdc config section show --json-path -j 
                                 --config-profile -c  
                                 [--target -t]  
                                 [--force -f]
```
### <a name="examples"></a>使用例
単純な json のキーのパスの最後に値を取得します。
```bash
mssqlctl bdc config section show --config-profile custom-config --json-path 'metadata.name' --target section.json
```
条件文で json のキーのパスの最後に値を取得します
```bash
mssqlctl bdc config section show --config-profile custom-config  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--json-path -j`
構成プロファイルの cluster.json ファイル、つまり key1.key2.key3 から目的の値のセクションに出ている json のキー パス。 Jsonpath クエリ言語を使用して https://github.com/h2non/jsonpath-ng 、たとえば:-j ' $spec.pools [でしょうか。 (。@.spec.type "Master"= =)].エンドポイント
#### `--config-profile -c`
BDC 構成プロファイルのパス。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--target -t`
セクションのファイルに希望するファイルのパスに配置されます。 既定値: は stdout に送られます。
#### `--force -f`
ターゲット ファイルの上書きを強制します。
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
## <a name="mssqlctl-bdc-config-section-set"></a>mssqlctl bdc config section set
指定された json パスに従って、選択した構成プロファイルで指定されたセクションを設定します。  Bash では、すべて examplesbelow 与えられます。  別のコマンドラインを使用する場合は、必要になる escapequotations を適切を了承ください。  または、修正プログラム ファイルの機能を使用することがあります。
```bash
mssqlctl bdc config section set --config-profile -c 
                                [--json-values -j]  
                                [--patch-file -p]
```
### <a name="examples"></a>使用例
1 (インライン) の例には、1 つのエンドポイント (コント ローラー エンドポイント) のポートを設定します。
```bash
mssqlctl bdc config section set --config-profile custom-config --json-values '$.spec.controlPlane.spec.endpoints[?(@.name=="Controller")].port=30080'
```
1 (patch) の例には、修正プログラム ファイルを 1 つのエンドポイント (コント ローラー エンドポイント) のポートを設定します。
```bash
mssqlctl bdc config section set --config-profile custom-config --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.controlPlane.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
例 2 (インライン) のセットの制御プレーン格納します。
```bash
mssqlctl bdc config section set --config-profile custom-config --json-values 'spec.controlPlane.spec.storage=spec.controlPlane.spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
例 2 (patch) の修正プログラム ファイルとコントロール プレーンの記憶域をセットします。
```bash
mssqlctl bdc config section set --config-profile custom-config --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"spec.controlPlane.spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
3(inline) - ex、(記憶域プール) のレプリカを含むプール ストレージを設定します。
```bash
mssqlctl bdc config section set --config-profile custom-config --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
例 3 (patch) で、修正プログラム ファイルのレプリカ (記憶域プール) を含むプール ストレージを設定します。
```bash
mssqlctl bdc config section set --config-profile custom-config --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--config-profile -c`
設定するには、構成の BDC 構成プロファイルのパス
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--json-values -j`
値 json パスのキーと値のペアの一覧: key1.subkey1=value1,key2.subkey2=value2 します。 インライン化する json 値など: キー ='{「種類」:「クラスター、」"name":"test cluster"}' または key=./values.json などのファイル パスを指定します。 条件文を必要とする値を設定する場合は、$ でパスを開始することで、jsonpath 表記を使用してください。 これができるように、$-j などの条件付きの操作を行います key1.key2 [でしょうか。 (。@.key3'someValue' = =] .key4 = 値。 次の例を参照してください可能性があります。 追加のヘルプを参照してください。 https://jsonpath.com/
#### `--patch-file -p`
Jsonpatch ライブラリに基づく修正プログラムの json ファイルへのパス: http://jsonpatch.com/ します。 "Patch"、値が patch 操作をする場合の配列と呼ばれるキーを使用して、修正プログラムの json ファイルを開始する必要があります。 Patch 操作のパス、key1.key2 ほとんどの操作など、ドット表記を使用することがあります。 置換の操作を実行するには、条件文を必要となる配列の値を置換する場合は、$ でパスを開始することで、jsonpath 表記を使用してください。 これができるように、$ などの条件付きの操作を行います key1.key2 [でしょうか。 (。@.key3'someValue' = =] .key4 します。 次の例を参照してください。 追加のヘルプを参照してください: https://jsonpath.com/ します。
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