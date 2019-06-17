---
title: mssqlctl クラスターの構成セクションのリファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl クラスターの構成セクションのコマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e0c4f543f349d166962e65ea91338595d25308ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800960"
---
# <a name="mssqlctl-cluster-config-section"></a>mssqlctl クラスターの構成セクション

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**クラスターの構成セクション**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl クラスターの構成セクションの表示](#mssqlctl-cluster-config-section-show) | 構成ファイルからセクションを取得します。
[mssqlctl クラスターの構成セクションの設定](#mssqlctl-cluster-config-section-set) | 構成ファイルのセクションを設定します。
## <a name="mssqlctl-cluster-config-section-show"></a>mssqlctl cluster config section show
指定された json パスに従って、選択した構成ファイルから、指定されたセクションを取得します。
```bash
mssqlctl cluster config section show --json-path -j 
                                     --config-file -c  
                                     [--target -t]  
                                     [--force -f]
```
### <a name="examples"></a>使用例
単純な json のキーのパスの最後に値を取得します。
```bash
mssqlctl cluster config section show --config-file custom-config.json --json-path 'metadata.name' --target section.json
```
条件文で json のキーのパスの最後に値を取得します
```bash
mssqlctl cluster config section show --config-file custom-config.json  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--json-path -j`
構成ファイル、つまり key1.key2.key3 から目的の値のセクションに出ている json のキー パス。 Jsonpath クエリ言語を使用して https://github.com/h2non/jsonpath-ng 、たとえば:-j ' $spec.pools [でしょうか。 (。@.spec.type "Master"= =)].エンドポイント
#### `--config-file -c`
クラスター構成ファイルのパス。
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
## <a name="mssqlctl-cluster-config-section-set"></a>mssqlctl クラスターの構成セクションの設定
指定された json パスに従って、選択した構成ファイルで指定されたセクションを設定します。  Bash では、すべて examplesbelow 与えられます。  別のコマンドラインを使用する場合は、必要になる escapequotations を適切を了承ください。  または、修正プログラム ファイルの機能を使用することがあります。
```bash
mssqlctl cluster config section set --config-file -c 
                                    [--json-values -j]  
                                    [--patch-file -p]
```
### <a name="examples"></a>使用例
1 (インライン) の例には、1 つのエンドポイント (コント ローラー エンドポイント) のポートを設定します。
```bash
mssqlctl cluster config section set --config-file custom-config.json --json-values '$.spec.controlPlane.spec.endpoints[?(@.name=="Controller")].port=30080'
```
1 (patch) の例には、修正プログラム ファイルを 1 つのエンドポイント (コント ローラー エンドポイント) のポートを設定します。
```bash
mssqlctl cluster config section set --config-file custom-config.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.controlPlane.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
例 2 (インライン) のセットの制御プレーン格納します。
```bash
mssqlctl cluster config section set --config-file custom-config.json --json-values 'spec.controlPlane.spec.storage=spec.controlPlane.spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
例 2 (patch) の修正プログラム ファイルとコントロール プレーンの記憶域をセットします。
```bash
mssqlctl cluster config section set --config-file custom-config.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"spec.controlPlane.spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
3(inline) - ex、(記憶域プール) のレプリカを含むプール ストレージを設定します。
```bash
mssqlctl cluster config section set --config-file custom-config.json --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
例 3 (patch) で、修正プログラム ファイルのレプリカ (記憶域プール) を含むプール ストレージを設定します。
```bash
mssqlctl cluster config section set --config-file custom-config.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--config-file -c`
設定するには、構成のクラスター構成ファイルのパス
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

## <a name="next-steps"></a>次のステップ

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。