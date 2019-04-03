---
title: mssqlctl リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b050638ee0ca600c5df0ecdbe5616b801f41e7a8
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860354"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **mssqlctl**用のツール[SQL Server 2019 ビッグ データ クラスター (プレビュー)](big-data-cluster-overview.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。

## <a id="commands"></a> コマンド

|||
|---|---|
| [app](reference-mssqlctl-app.md) | 作成、削除、実行、およびアプリケーションを管理します。 |
| [クラスター](reference-mssqlctl-cluster.md) | 選択、管理、およびクラスターを操作します。 |
| [ログイン](#login) | クラスターにログインします。 |
| [ログアウト](#logout) | クラスターからログアウトします。 |
| [ストレージ](reference-mssqlctl-storage.md) | クラスター記憶域を管理します。 |

## <a id="login"></a> mssqlctl login

クラスターにログインします。

```
mssqlctl login
   --endpoint
   --password
   --username
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
|**--endpoint -e**| クラスターのホストとポート (ex)`http://host:port"`します。 |
|**-パスワードに p**| パスワードの資格情報。 |
|**--username -u**| アカウントのユーザー。 |

### <a name="examples"></a>使用例

対話形式でログインします。

```
mssqlctl login
```

ユーザー名とパスワードでログインします。

```
mssqlctl login -u johndoe@contoso.com -p VerySecret
```

ユーザー名、パスワード、およびクラスター エンドポイントを使用してログインします。

```
mssqlctl login -u johndoe@contoso.com -p VerySecret --endpoint https://host.com:12800
```

## <a id="logout"></a> mssqlctl logout

クラスターからログアウトします。

```
mssqlctl logout
   --username
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--username -u** | アカウントのユーザー、ない場合、現在アクティブなアカウントをログアウトします。 |

### <a name="examples"></a>使用例

このユーザーをログアウトします。

```
mssqlctl logout --username admin
```

## <a name="next-steps"></a>次のステップ

インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。