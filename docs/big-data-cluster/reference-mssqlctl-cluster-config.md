---
title: mssqlctl クラスター構成の参照
titleSuffix: SQL Server 2019 big data clusters
description: Mssqlctl クラスター コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 26e93151a1150bbbbd1798b38486ca5b01aaab1d
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527205"
---
# <a name="mssqlctl-cluster-config"></a>mssqlctl cluster config

次の記事への参照を提供する、**クラスターの構成**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a id="commands"></a> コマンド

|||
|---|---|
| [get](#get) | クラスターを取得します。 |

## <a id="get"></a> mssqlctl クラスター構成を取得します。

クラスターを取得します。

```
mssqlctl cluster config get
   --name
   --output-file
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--name -n** | クラスター名 kubernetes 名前空間に使用をします。 必須。 |
| **--output-file -f** | 結果を格納する出力ファイル。 必須。 |

## <a name="next-steps"></a>次のステップ

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。