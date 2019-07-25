---
title: azdata bdc プールの状態の参照
titleSuffix: SQL Server big data clusters
description: Azdata bdc プールの状態コマンドに関するリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d0a5925af4f16f2147988b2318880d9acec664c3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426132"
---
# <a name="azdata-bdc-pool-status"></a>azdata bdc プールの状態

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールの**bdc プールの状態**コマンドについて説明します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc プールの状態の表示](#azdata-bdc-pool-status-show) | プールの状態。
## <a name="azdata-bdc-pool-status-show"></a>azdata bdc プールの状態の表示
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
データプールの状態を取得します。
```bash
azdata bdc pool status show --kind data --name default
```
コンピューティングプールの状態を取得します。
```bash
azdata bdc pool status show --kind compute --name default
```
マスタープールの状態を取得します。
```bash
azdata bdc pool status show --kind master --name default
```
Spark プールの状態を取得します。
```bash
azdata bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--kind -k`
ビッグデータクラスタープールの種類。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--name -n`
ビッグデータクラスタープール名。
`default`
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

**Azdata**ツールをインストールする方法の詳細については、「 [Azdata をインストールして SQL Server 2019 ビッグデータクラスターを管理する](deploy-install-azdata.md)」を参照してください。
