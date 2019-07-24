---
title: azdata bdc デバッグリファレンス
titleSuffix: SQL Server big data clusters
description: Azdata bdc デバッグコマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 38c327287273ae6596326d88d9e0d67c8e014d47
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426232"
---
# <a name="azdata-bdc-debug"></a>azdata bdc デバッグ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールでの**bdc デバッグ**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc デバッグコピー-ログ](#azdata-bdc-debug-copy-logs) | ログをコピーします。
[azdata bdc デバッグダンプ](#azdata-bdc-debug-dump) | ログダンプをトリガーします。
## <a name="azdata-bdc-debug-copy-logs"></a>azdata bdc デバッグコピー-ログ
ビッグデータクラスターからデバッグログをコピーします-kube config はシステムに必要です。
```bash
azdata bdc debug copy-logs --namespace -n 
                           [--container -c]  
                           [--target-folder -d]  
                           [--pod -p]  
                           [--timeout -t]
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--namespace -n`
ビッグデータクラスター名。 kubernetes 名前空間に使用されます。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--container -c`
類似した名前のコンテナーのログをコピーします (省略可能)。既定では、すべてのコンテナーのログがコピーされます。 を複数回指定することはできません。 複数回指定した場合、最後の1つが使用されます。
#### `--target-folder -d`
ログをコピーするターゲットフォルダーのパス。 省略可能。既定では、結果がローカルフォルダーに作成されます。  を複数回指定することはできません。 複数回指定した場合、最後の1つが使用されます。
#### `--pod -p`
類似した名前のポッドのログをコピーします。 省略可能。既定では、すべてのポッドのログがコピーされます。 を複数回指定することはできません。 複数回指定した場合、最後の1つが使用されます。
#### `--timeout -t`
コマンドの完了を待機する秒数。 既定値は0で、無制限です。
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
## <a name="azdata-bdc-debug-dump"></a>azdata bdc デバッグダンプ
システムでは、ログ出力のトリガーと kube config からのコピーが必要です。
```bash
azdata bdc debug dump --namespace -n 
                      --container -c  
                      [--target-folder -d]
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--namespace -n`
ビッグデータクラスター名。 kubernetes 名前空間に使用されます。
#### `--container -c`
類似した名前のコンテナーのログをコピーします (省略可能)。既定では、すべてのコンテナーのログがコピーされます。 を複数回指定することはできません。 複数回指定した場合、最後の1つが使用されます。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--target-folder -d`
ログをコピーするターゲットフォルダーのパス。 省略可能。既定では、結果がローカルフォルダーに作成されます。  を複数回指定することはできません。 複数回指定した場合、最後の1つが使用されます。`./output/dump`
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
