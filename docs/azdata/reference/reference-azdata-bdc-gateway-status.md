---
title: azdata bdc gateway status リファレンス
titleSuffix: SQL Server big data clusters
description: azdata bdc gateway status コマンドに関するリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2e9443c7c984b6ebea23a733c96478760107da09
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733785"
---
# <a name="azdata-bdc-gateway-status"></a>azdata bdc gateway status

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

以下の記事では、`azdata` ツールの `sql` コマンドに関するリファレンスを提供します。 `azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください。

## <a name="commands"></a>コマンド
| command | 説明 |
| --- | --- |
[azdata bdc gateway status show](#azdata-bdc-gateway-status-show) | ゲートウェイ サービスの状態。
## <a name="azdata-bdc-gateway-status-show"></a>azdata bdc gateway status show
ゲートウェイ サービスの状態。
```bash
azdata bdc gateway status show [--resource -r] 
                               [--all -a]
```
### <a name="examples"></a>例
ゲートウェイ サービスの状態を取得します。
```bash
azdata bdc gateway status show
```
ゲートウェイ サービスとすべてのインスタンスの状態を取得します。
```bash
azdata bdc gateway status show --all
```
ゲートウェイ サービス内のゲートウェイ リソースの状態を取得します。
```bash
azdata bdc gateway status show --resource gateway
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--resource -r`
このサービス内のこのリソースを取得します。
#### `--all -a`
サービス内の各リソースのすべてのインスタンスを表示します。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。

## <a name="next-steps"></a>次のステップ

`azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください。 `azdata` ツールのインストール方法の詳細については、[SQL Server 2019 ビッグ データ クラスターを管理する azdata のインストール](../install/deploy-install-azdata.md)に関するページを参照してください。
