---
title: azdata bdc endpoint リファレンス
titleSuffix: SQL Server big data clusters
description: azdata bdc endpoint コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 71f52b8312518cf669751d50dcc857c3d892bd98
ms.sourcegitcommit: db1b6153f0bc2d221ba1ce15543ecc83e1045453
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2020
ms.locfileid: "82588078"
---
# <a name="azdata-bdc-endpoint"></a>azdata bdc endpoint

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

以下の記事では、`azdata` ツールの `bdc endpoint` コマンドに関するリファレンスを提供します。 `azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc endpoint list](#azdata-bdc-endpoint-list) | ビッグ データ クラスターのエンドポイントを一覧表示します。
## <a name="azdata-bdc-endpoint-list"></a>azdata bdc endpoint list
ビッグ データ クラスターのエンドポイントを一覧表示します。

```bash
azdata bdc endpoint list [--endpoint-name -e] 
```

### <a name="optional-parameters"></a>省略可能なパラメーター

#### `--endpoint-name -e`

ビッグ データ クラスターのエンドポイント名。

### <a name="global-arguments"></a>グローバル引数

#### `--debug`

すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。

#### `--help -h`

このヘルプ メッセージを表示して終了します。

#### `--output -o`

出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。

#### `--query -q`

JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org/) を参照してください。

#### `--verbose`

ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。

## <a name="next-steps"></a>次のステップ

`azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください。 `azdata` ツールのインストール方法の詳細については、[SQL Server 2019 ビッグ データ クラスターを管理する azdata のインストール](deploy-install-azdata.md)に関するページを参照してください。
