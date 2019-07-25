---
title: azdata bdc の構成リファレンス
titleSuffix: SQL Server big data clusters
description: Azdata bdc コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ed777391af3695da69e04c0e2693cff912c76771
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426292"
---
# <a name="azdata-bdc-config"></a>azdata bdc の構成

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールでの**bdc の構成**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc の構成の初期化](#azdata-bdc-config-init) | クラスター作成で使用できるビッグデータクラスター構成プロファイルを初期化します。
[azdata bdc の構成リスト](#azdata-bdc-config-list) | 使用可能な構成プロファイルの選択肢を一覧表示します。
[azdata bdc の構成の表示](#azdata-bdc-config-show) | BDC の現在の構成、または指定したローカルファイルの構成 (カスタム/クラスター. json など) を表示します。
[azdata bdc の構成の追加](#azdata-bdc-config-add) | 構成ファイルに json パスの値を追加します。
[azdata bdc の構成の削除](#azdata-bdc-config-remove) | 構成ファイル内の json パスの値を削除します。
[azdata bdc の構成の置換](#azdata-bdc-config-replace) | 構成ファイル内の json パスの値を置き換えます。
[azdata bdc 構成パッチ](#azdata-bdc-config-patch) | Json 修正プログラムファイルに基づいて構成ファイルを修正します。
## <a name="azdata-bdc-config-init"></a>azdata bdc の構成の初期化
クラスター作成で使用できるビッグデータクラスター構成プロファイルを初期化します。 構成プロファイルの特定のソースは、3つの選択肢の引数で指定できます。
```bash
azdata bdc config init [--target -t] 
                       [--source -s]  
                       [--force -f]  
                       [--accept-eula -a]
```
### <a name="examples"></a>使用例
ガイド付き BDC の構成の初期エクスペリエンス-必要な値の入力を求めるメッセージが表示されます。
```bash
azdata bdc config init
```
引数を使用した BDC 構成の初期化では、aks の構成プロファイルが作成されます。
```bash
azdata bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--target -t`
Config プロファイルを配置する場所のファイルパス。既定値は cwd に設定されています。
#### `--source -s`
Config profile source: ['aks-dev-test', 'kubeadm-dev-test', 'minikube-dev-test']
#### `--force -f`
ターゲットファイルを強制的に上書きします。
#### `--accept-eula -a`
ライセンス条項に同意しますか? [はい/いいえ]。 この引数を使用しない場合は、環境変数 ACCEPT_EULA を "yes" に設定します。 この製品のライセンス条項に https://aka.ms/azdata-eula ついては、「」を参照してください。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-config-list"></a>azdata bdc の構成リスト
使用可能な構成プロファイルの選択肢を一覧表示します`bdc config init`
```bash
azdata bdc config list [--config-profile -c] 
                       [--type -t]  
                       [--accept-eula -a]
```
### <a name="examples"></a>使用例
使用可能なすべての構成プロファイルの名前が表示されます。
```bash
azdata bdc config list
```
特定の構成プロファイルの json を表示します。
```bash
azdata bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--config-profile -c`
既定の構成プロファイル: [' aks ', ' kubeadm ', ' minikube '] \ (開発-テスト ')
#### `--type -t`
表示する構成の種類を選択します。
`cluster`
#### `--accept-eula -a`
ライセンス条項に同意しますか? [はい/いいえ]。 この引数を使用しない場合は、環境変数 ACCEPT_EULA を "yes" に設定します。 この製品のライセンス条項に https://aka.ms/azdata-eula ついては、「」を参照してください。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-config-show"></a>azdata bdc の構成の表示
BDC の現在の構成、または指定したローカルファイルの構成 (カスタム/クラスター. json など) を表示します。 また、セクションのみを取得する場合は、json パスでコマンドを実行します。  出力先ファイルを指定することもできます。  ターゲットファイルが指定されていない場合は、ターミナルにのみ出力されます。
```bash
azdata bdc config show [--config-file -c] 
                       [--target -t]  
                       [--json-path -j]  
                       [--force -f]
```
### <a name="examples"></a>使用例
コンソールに BDC 構成を表示する
```bash
azdata bdc config show
```
ローカル構成ファイルで、単純な json キーパスの最後に値を取得します。
```bash
azdata bdc config show --config-file custom-config/cluster.json --json-path 'metadata.name' --target section.json
```
ローカル構成ファイルで、条件を指定した json キーパスの最後にある値を取得します。
```bash
azdata bdc config show --config-file custom-config/cluster.json  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--config-file -c`
現在ログインしているクラスターの構成 (カスタム/クラスター) を必要としない場合は、ビッグデータクラスターの構成ファイルのパス
#### `--target -t`
結果を格納する出力ファイル。 既定値: stdout に送信されます。
#### `--json-path -j`
構成から必要なセクションまたは値につながる json キーのパス (つまり、key1... key3)。 Jsonpath クエリ言語 https://jsonpath.com/ を使用します。例:-j ' $. spec. プール [? (@.spec.type = = "Master")]..
#### `--force -f`
ターゲットファイルを強制的に上書きします。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-config-add"></a>azdata bdc の構成の追加
構成ファイルの json パスに値を追加します。  Bash では、以下のすべての例が提供されています。  別のコマンドラインを使用する場合は、適切に escapequotations する必要があることに注意してください。  または、修正プログラムファイルの機能を使用することもできます。
```bash
azdata bdc config add --config-file -c 
                      --json-values -j
```
### <a name="examples"></a>使用例
例 1-コントロールプレーンストレージを追加します。
```bash
azdata bdc config add --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--config-file -c`
設定する構成のビッグデータクラスター構成ファイルのパス、つまりカスタム/クラスター。 json
#### `--json-values -j`
値への json パスのキーと値のペアのリスト: subkey1 = value1, key2. subkey2 = value2。 次のようなインライン json 値を指定することができます: key = ' {"kind": "cluster", "name": "test-cluster"} ' またはファイルパスを指定します (キー =./値/jsonなど)。 Add は条件をサポートしていません。  パスの http://jsonpatch.com/ 表示方法の例については、「」を参照してください。  配列にアクセスする場合は、インデックスを指定する必要があります。たとえば、key. 0 = value のように指定します。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-config-remove"></a>azdata bdc の構成の削除
構成ファイルの json パスにある値を削除します。  Bash では、以下のすべての例が提供されています。  別のコマンドラインを使用する場合は、適切に escapequotations する必要があることに注意してください。  または、修正プログラムファイルの機能を使用することもできます。
```bash
azdata bdc config remove --config-file -c 
                         --json-path -j
```
### <a name="examples"></a>使用例
例 1-コントロールプレーンのストレージを削除します。
```bash
azdata bdc config remove --config-file custom/control.json --json-path '.spec.storage'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--config-file -c`
設定する構成のビッグデータクラスター構成ファイルのパス、つまりカスタム/クラスター。 json
#### `--json-path -j`
削除する値 (subkey1、subkey2 など) を示す、jsonpatch ライブラリに基づく json パスの一覧です (例:)。 削除は条件をサポートしていません。 パスの http://jsonpatch.com/ 表示方法の例については、「」を参照してください。  配列にアクセスする場合は、インデックスを指定する必要があります。たとえば、key. 0 = value のように指定します。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-config-replace"></a>azdata bdc の構成の置換
構成ファイルの json パスの値を置き換えます。  Bash では、以下のすべての例が提供されています。  別のコマンドラインを使用する場合は、適切に escapequotations する必要があることに注意してください。  または、修正プログラムファイルの機能を使用することもできます。
```bash
azdata bdc config replace --config-file -c 
                          --json-values -j
```
### <a name="examples"></a>使用例
例 1-1 つのエンドポイント (コントローラーエンドポイント) のポートを交換します。
```bash
azdata bdc config replace --config-file custom/control.json --json-values '$.spec.endpoints[?(@.name=="Controller")].port=30080'
```
例 2-コントロールプレーンのストレージを置き換えます。
```bash
azdata bdc config replace --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
例 3-レプリカ (記憶域プール) を含むプール記憶域を置き換えます。
```bash
azdata bdc config replace --config-file custom/cluster.json --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--config-file -c`
設定する構成のビッグデータクラスター構成ファイルのパス、つまりカスタム/クラスター。 json
#### `--json-values -j`
値への json パスのキーと値のペアのリスト: subkey1 = value1, key2. subkey2 = value2。 次のようなインライン json 値を指定することができます: key = ' {"kind": "cluster", "name": "test-cluster"} ' またはファイルパスを指定します (キー =./値/jsonなど)。 置換は、jsonpath ライブラリを介して条件をサポートします。  これを使用するには、$ でパスを開始します。 これにより、-j $. key1. key2 のような条件 (@.key3= = ' 値 '] key4 = 値。 次の例が表示されます。 詳細については、以下を参照してください。 https://jsonpath.com/
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-config-patch"></a>azdata bdc 構成パッチ
指定された修正プログラムファイルに従って、構成ファイルを修正します。 パスを http://jsonpatch.com/ 構成する方法の詳細については、「」を参照してください。 置換操作では、jsonpath ライブラリ https://jsonpath.com/ によりパスで条件を使用できます。 すべての patch json ファイルは、対応する op (add、replace、remove)、path、value を含むパッチの配列を含む "patch" のキーで始まる必要があります。 "Remove" 操作には、値を指定する必要はありません。パスだけです。 次の例を参照してください。
```bash
azdata bdc config patch --config-file -c 
                        --patch-file -p
```
### <a name="examples"></a>使用例
例 1-1 つのエンドポイント (コントローラーエンドポイント) のポートを修正プログラムファイルに置き換えます。
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
例 2-コントロールプレーンの記憶域を修正プログラムファイルに置き換えます。
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":".spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
例 3-レプリカ (記憶域プール) を含むプール記憶域を修正プログラムファイルに置き換えます。
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--config-file -c`
設定する構成のビッグデータクラスター構成ファイルのパス、つまりカスタム/クラスター。 json
#### `--patch-file -p`
Jsonpatch ライブラリに基づく patch json ファイルへのパス: http://jsonpatch.com/ 。 修正プログラムの json ファイルは、"patch" というキーを使用して開始する必要があります。このキーの値は、実行しようとしているパッチ操作の配列です。 パッチ操作のパスでは、ほとんどの操作に対して key1 などのドット表記を使用できます。 置換操作を実行し、条件を必要とする配列の値を置き換える場合は、パスを $ で始まる jsonpath 表記法を使用してください。 このようにすると、$. key1. key2 [? (@.key3= = ' 値 '] key4。 次の例を参照してください。 条件の詳細については、「 https://jsonpath.com/ 」を参照してください。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。

## <a name="next-steps"></a>次の手順

その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。 **Azdata**ツールをインストールする方法の詳細については、「 [Azdata をインストールして SQL Server 2019 ビッグデータクラスターを管理する](deploy-install-azdata.md)」を参照してください。