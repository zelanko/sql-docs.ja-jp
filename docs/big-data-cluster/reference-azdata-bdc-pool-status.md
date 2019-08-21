---
title: azdata bdc pool status リファレンス
titleSuffix: SQL Server big data clusters
description: azdata bdc pool status コマンドに関するリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: eafc72c6d86d38eabd26b735a9d5dab967e2e6be
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653483"
---
# <a name="azdata-bdc-pool-status"></a>azdata bdc pool status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

以下の記事では、**azdata** ツールでの **bdc pool status** コマンドのリファレンスを提供します。 他の **azdata** コマンドの詳細については、[azdata リファレンス](reference-azdata.md)に関するページを参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc pool status show](#azdata-bdc-pool-status-show) | プールの状態。
## <a name="azdata-bdc-pool-status-show"></a>azdata bdc pool status show
プールの状態。
```bash
azdata bdc pool status show --kind -k 
                            [--name -n]
```
### <a name="examples"></a>使用例
記憶域プールの状態を取得します。
```bash
azdata bdc pool status show --kind storage --name default
```
データ プールの状態を取得します。
```bash
azdata bdc pool status show --kind data --name default
```
コンピューティング プールの状態を取得します。
```bash
azdata bdc pool status show --kind compute --name default
```
マスター プールの状態を取得します。
```bash
azdata bdc pool status show --kind master --name default
```
Spark プールの状態を取得します。
```bash
azdata bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--kind -k`
ビッグ データ クラスター プールの種類。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--name -n`
ビッグ データ クラスター プール名。
`default`
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org/]) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。

## <a name="next-steps"></a>次の手順

**Azdata**ツールをインストールする方法の詳細については、「[管理[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]する azdata をインストール](deploy-install-azdata.md)する」を参照してください。
