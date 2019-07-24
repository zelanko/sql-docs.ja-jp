---
title: azdata bdc の状態リファレンス
titleSuffix: SQL Server big data clusters
description: Azdata bdc のステータスコマンドに関するリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 15fec084fc6ff5d7b3e62ec0b775047aa9bc59db
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426052"
---
# <a name="azdata-bdc-status"></a>azdata bdc の状態

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールの**bdc ステータス**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc の状態の表示](#azdata-bdc-status-show) | ビッグデータクラスターの状態が表示されます。
## <a name="azdata-bdc-status-show"></a>azdata bdc の状態の表示
ビッグデータクラスターの状態が表示されます。
```bash
azdata bdc status show 
```
### <a name="examples"></a>使用例
ユーザーがログインしている BDC の状態。
```bash
azdata bdc status show
```
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
