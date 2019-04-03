---
title: mssqlctl アプリ テンプレート リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl アプリ テンプレート コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c67ed74750ac36d1a5c79503417414a9dd8ab6b5
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860103"
---
# <a name="mssqlctl-app-template"></a>mssqlctl アプリ テンプレート

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**アプリ テンプレート**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a id="commands"></a> コマンド

|||
|---|---|
| [一覧](#list) | サポートされているテンプレートをフェッチします。 |
| [プル (pull)](#pull) | サポートされているテンプレートをダウンロードします。 |

## <a id="list"></a> mssqlctl アプリ テンプレートの一覧

サポートされているテンプレートをフェッチします。

```
mssqlctl app template list
   --url
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--url -u** | 別のテンプレート リポジトリの場所を指定します。 既定値:https://github.com/Microsoft/sql-server-samples.gitします。 |

### <a name="examples"></a>使用例

既定のテンプレート リポジトリの場所のすべてのテンプレートをフェッチします。

```
mssqlctl app template list
```

別のリポジトリ場所のすべてのテンプレートをフェッチします。

```
mssqlctl app template list --url https://github.com/diffrent/templates.git
```

## <a id="pull"></a> mssqlctl アプリ テンプレートのプル

サポートされているテンプレートをダウンロードします。

```
mssqlctl app template pull
   --destination
   --name
   --url
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--destination -d** | アプリケーションのスケルトン テンプレートを配置する場所。  既定値:./テンプレート。 |
| **--name -n** | テンプレートの名前。 サポートされているテンプレートの名前を完全な一覧については、実行`mssqlctl app template list`します。 |
| **--url -u** | 別のテンプレート リポジトリの場所を指定します。 既定値:
https://github.com/Microsoft/sql-server-samples.git 。 |

### <a name="examples"></a>使用例

既定のテンプレート リポジトリの場所のすべてのテンプレートをダウンロードします。

```
mssqlctl app template pull
```

別のリポジトリ場所のすべてのテンプレートをダウンロードします。

```
mssqlctl app template list --url https://github.com/diffrent/templates.git
```

名前では、個々 のテンプレートをダウンロードします。

```
mssqlctl app template pull --name ssis
```

## <a name="next-steps"></a>次のステップ

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。