---
title: mssqlctl リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: dd9248c059cb4179bca7953e8a7d5bf721892fb8
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993320"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **mssqlctl**用のツール[SQL Server 2019 ビッグ データ クラスター (プレビュー)](big-data-cluster-overview.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
|[mssqlctl アプリ](reference-mssqlctl-app.md) | 作成、削除、実行、およびアプリケーションを管理します。 |
|[mssqlctl クラスター](reference-mssqlctl-cluster.md) | 選択、管理、およびクラスターを操作します。 |
[mssqlctl login](#mssqlctl-login) | クラスターのコント ローラーのエンドポイントにログインします。
[mssqlctl logout](#mssqlctl-logout) | クラスターからログアウトします。
## <a name="mssqlctl-login"></a>mssqlctl login
使用する必要があります、展開中にコント ローラー エンドポイントが一覧表示、クラスターを展開するときにログインします。  コント ローラー エンドポイントがわからない場合、システムの既定の場所で、クラスターの kube 構成することでログイン<user home>/.kube/config または、KUBECONFIG 環境変数を使用して、つまり KUBECONFIG=path/to/.kube/config をエクスポートします。
```bash
mssqlctl login [--cluster-name -n] 
               [--controller-username -u]  
               [--controller-endpoint -e]  
               [--accept-eula -a]
```
### <a name="examples"></a>使用例
対話形式でログインします。 クラスター名は常の入力を求めいないされる引数として指定されました。 システムに設定 CONTROLLER_USERNAME、CONTROLLER_PASSWORD、および ACCEPT_EULA 環境変数があれば、これらが求められないのです。 システム上、kube 構成を保持するか、またはには、構成パスを指定して、KUBECONFIG 環境変数を使用している場合、対話型エクスペリエンスは最初に、構成を使用して、メッセージが表示されますが、構成が失敗した場合に試します。
```bash
mssqlctl login
```
(非対話形式) にログインします。 クラスター名、コント ローラーのユーザー名、コント ローラーのエンドポイント、および EULA 同意の引数として設定を使用してログインします。 環境変数 CONTROLLER_PASSWORD を設定する必要があります。  コント ローラーのエンドポイントを指定しない場合の既定の場所のコンピューターに kube 構成があるください<user home>/.kube/config または、KUBECONFIG 環境変数を使用して、つまり KUBECONFIG=path/to/.kube/config をエクスポートします。
```bash
mssqlctl login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
マシン、および設定 CONTROLLER_USERNAME、CONTROLLER_PASSWORD、および ACCEPT_EULA 環境変数の kube 構成でログインします。
```bash
mssqlctl login -n ClusterName
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--cluster-name -n`
クラスターの名前。
#### `--controller-username -u`
アカウントのユーザー。 この引数を使用しない場合は、CONTROLLER_USERNAME 環境変数を設定することがあります。
#### `--controller-endpoint -e`
クラスター エンドポイントのコント ローラー"https://host:port"。 この引数を使用しない場合は、コンピューターに kube 構成を使用することがあります。 既定の場所に、構成が配置されているか確認してください<user home>/.kube/config または KUBECONFIG env var 関数の使用
#### `--accept-eula -a`
ライセンス条項に同意しますか。 [はい/いいえ] です。 この引数を使用しない場合は、'yes' に ACCEPT_EULA 環境変数を設定することがあります。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-logout"></a>mssqlctl logout
クラスターからログアウトします。
```bash
mssqlctl logout 
```
### <a name="examples"></a>使用例
このユーザーをログアウトします。
```bash
mssqlctl logout
```
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。

## <a name="next-steps"></a>次のステップ

インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。