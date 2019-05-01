---
title: mssqlctl クラスターの構成セクションのリファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl クラスターの構成セクションのコマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d5a793e7d0fcaf782a09a4981491ef0a8d90ab5a
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63759139"
---
# <a name="mssqlctl-cluster-config-section"></a>mssqlctl クラスターの構成セクション

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**クラスターの構成セクション**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl クラスターの構成セクションを取得します。](#mssqlctl-cluster-config-section-get) | 構成ファイルからセクションを取得します。
[mssqlctl クラスターの構成セクションの設定](#mssqlctl-cluster-config-section-set) | 構成ファイルのセクションを設定します。
## <a name="mssqlctl-cluster-config-section-get"></a>mssqlctl クラスターの構成セクションを取得します。
指定された json パスに従って、選択した構成ファイルから、指定されたセクションを取得します。
```bash
mssqlctl cluster config section get --json-path -j 
                                    --config-file -f  
                                    [--target -t]
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--json-path -j`
構成ファイル、つまり key1.key2.key3 から目的の値のセクションに出ている json のキー パス。 Jsonpath クエリ言語を使用して https://github.com/h2non/jsonpath-ng、たとえば:-j ' $spec.pools [でしょうか。 (。@.spec.type "Master"= =)].エンドポイント
#### `--config-file -f`
クラスター構成ファイルのパス。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--target -t`
セクションのファイルに希望するファイルのパスに配置されます。
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
指定された json パスに従って、選択した構成ファイルで指定されたセクションを設定します。
```bash
mssqlctl cluster config section set --config-file -f 
                                    [--json-values -j]  
                                    [--patch-file -p]
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--config-file -f`
設定するには、構成のクラスター構成ファイルのパス
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--json-values -j`
値 json パスのキーと値のペアの一覧: key1.subkey1=value1,key2.subkey2=value2 します。 インライン化する json 値など: キー ='{「種類」:「クラスター、」"name":"test cluster"}' key=./values.json などのファイル パスを指定または
#### `--patch-file -p`
Jsonpatch ライブラリと jsonpath に基づく修正プログラムの json ファイルへのパス: https://github.com/stefankoegl/python-json-patch 、 https://github.com/h2non/jsonpath-ng -簡単な例: {「パッチ」: [{"op":"add"、"path":"metadata.name","value":"test"}、{"op":"add"、"path":"metadata.array","value": [1, 2, 3]}]}"Patch"、キーを含めるし、修正プログラムを作成する配列の値があるしてください。  そのため実行されます。 A more complex example: {"patch": [{"op": "replace", "path": "$.spec.pools[?(@.spec.type == 'Master')]..endpoints","value": {"name":「新しいエンドポイント」}}]}
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