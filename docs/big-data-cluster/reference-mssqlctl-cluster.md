---
title: mssqlctl クラスターの参照
titleSuffix: SQL Server big data clusters
description: Mssqlctl クラスター コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e4e54ac3c7206ad8a6592c8cfe0b45d9ea4b8fd8
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860473"
---
# <a name="mssqlctl-cluster"></a>mssqlctl クラスター

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**クラスター**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a id="commands"></a> コマンド

|||
|---|---|
| [create](#create) | クラスターを作成します。 |
| [delete](#delete) | クラスターを削除します。 |
| [config](reference-mssqlctl-cluster-config.md) | クラスターの構成コマンド。 |
| [debug](reference-mssqlctl-cluster-debug.md) | コマンドをデバッグします。 |

## <a id="create"></a> mssqlctl クラスターを作成します。

クラスターを作成します。

```
mssqlctl cluster create
   --name
   --accept-eula
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--name -n** | クラスター名 kubernetes 名前空間に使用をします。 |
| **--accept-eula -e** | ライセンス条項に同意しますか。 \[はい/いいえ\]します。  使用できる値: いいえ、はい。 必須。 |

## <a id="delete"></a> mssqlctl cluster delete

クラスターを削除します。

```
mssqlctl cluster delete
   --name
   [--force]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--name -n** | クラスター名 kubernetes 名前空間に使用をします。 必須。 |
| **--f を強制** | 強制削除クラスター。 |

## <a name="next-steps"></a>次のステップ

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。