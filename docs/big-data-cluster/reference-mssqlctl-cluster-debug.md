---
title: mssqlctl クラスター デバッグ リファレンス
titleSuffix: SQL Server 2019 big data clusters
description: Mssqlctl クラスター コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9312e972dfcb439f4ef19a4e72d8d66454622096
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527235"
---
# <a name="mssqlctl-cluster-debug"></a>mssqlctl cluster debug

次の記事への参照を提供する、**クラスター デバッグ**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a id="commands"></a> コマンド

|||
|---|---|
| [copy-logs](#copy-logs) | ログをコピーします。 |
| [ダンプ](#dump) | トリガー ログのダンプします。 |

## <a id="copy-logs"></a> クラスターのデバッグのコピー ログ

ログをコピーします。

```
mssqlctl cluster debug copy-logs
   --namespace
   [--container]
   [--pod]
   [--target-folder]
   [--timeout]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--namespace -n** | クラスター名 kubernetes 名前空間に使用をします。 必須。 |
| **--container -c** | ログのコピーのような名前のコンテナーでは、省略可能、既定ではコピーのすべてのコンテナーのログ。 複数回を指定できません。 複数回指定すると場合は、最後 1 つが使用されます。 |
| **--pod -p** | 類似した名前のポッドのログをコピーします。 すべてのポッドの既定のコピー ログが省略可能です。 複数回を指定できません。 複数回指定すると場合は、最後 1 つが使用されます。 |
| **--target-folder -d** | ログをコピーする対象のフォルダー パス。 省略可能で、既定では、ローカル フォルダーのまま、結果を作成します。  複数回を指定できません。 複数回指定すると場合は、最後 1 つが使用されます。 |
| **--timeout-t** | コマンドが完了するまで待機する秒数。 既定値は、0 では制限されません。 |

## <a id="dump"></a> クラスター デバッグ ダンプ

トリガー ログのダンプします。

```
mssqlctl cluster debug dump
   [--container]
   [--namespace]
   --target-folder
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--container -c** | ログのコピーのような名前のコンテナーでは、省略可能、既定ではコピーのすべてのコンテナーのログ。 複数回を指定できません。 複数回指定すると場合は、最後 1 つが使用されます。  使用できる値: mssql コント ローラー。 |
| **--namespace -n** | クラスター名 kubernetes 名前空間に使用をします。 必須。 |
| **--target-folder -d** | ログをコピーする対象のフォルダー パス。 省略可能で、既定では、ローカル フォルダーのまま、結果を作成します。  複数回を指定できません。 複数回指定すると場合は、最後 1 つが使用されます。  既定値:`./output/dump`します。 必須。 |

## <a name="next-steps"></a>次のステップ

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。