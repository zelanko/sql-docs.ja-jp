---
title: azdata リファレンス
titleSuffix: SQL Server big data clusters
description: Azdata コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8136c85f8c32e08423f3d199a021d4f60353b39
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425992"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 [SQL Server 2019 ビッグデータクラスター (プレビュー)](big-data-cluster-overview.md)用の**azdata**ツールのリファレンスを提供します。 **Azdata**ツールをインストールする方法の詳細については、「 [Azdata をインストールして SQL Server 2019 ビッグデータクラスターを管理する](deploy-install-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
|[azdata アプリ](reference-azdata-app.md) | アプリケーションを作成、削除、実行、および管理します。 |
|[azdata bdc](reference-azdata-bdc.md) | SQL Server ビッグデータクラスターの選択、管理、および操作を行います。 |
|[azdata notebook](reference-azdata-notebook.md) | ターミナルからノートブックを表示、実行、管理するためのコマンドです。 |
[azdata ログイン](#azdata-login) | クラスターのコントローラーエンドポイントにログインします。
[azdata ログアウト](#azdata-logout) | クラスターからログアウトします。
|[azdata sql](reference-azdata-sql.md) | SQL DB CLI を使用すると、ユーザーは T-sql を使用して SQL Server を操作できます。 |
## <a name="azdata-login"></a>azdata ログイン
クラスターがデプロイされると、デプロイ中にコントローラーエンドポイントが一覧表示されます。これはログインに使用する必要があります。  コントローラーのエンドポイントがわからない場合は、システム上のクラスターの kube config を/.kube/config の<user home>既定の場所に置くか、KUBECONFIG env var (export KUBECONFIG = path/to/kube/config) を使用してログインすることができます。
```bash
azdata login [--cluster-name -n] 
             [--controller-username -u]  
             [--controller-endpoint -e]  
             [--accept-eula -a]
```
### <a name="examples"></a>使用例
対話形式でログインします。 引数として指定されていない場合、クラスター名には常にが表示されます。 システムに CONTROLLER_USERNAME、CONTROLLER_PASSWORD、および ACCEPT_EULA env 変数が設定されている場合、これらの変数はの入力を求められません。 システムに kube config がある場合、または構成へのパスを指定するために KUBECONFIG env var を使用している場合は、対話型エクスペリエンスによって、まず config の使用が試行され、構成が失敗した場合にプロンプトが表示されます。
```bash
azdata login
```
ログイン (非対話形式)。 クラスター名、コントローラーのユーザー名、コントローラーエンドポイント、および使用許諾契約の同意を引数として設定してログインします。 環境変数 CONTROLLER_PASSWORD を設定する必要があります。  コントローラーエンドポイントを指定しない場合は、コンピューター上の kube 構成を/.kube/config の<user home>既定の場所に設定するか、KUBECONFIG env var (export KUBECONFIG = path/to/kube/config) を使用してください。
```bash
azdata login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
コンピューターで kube config を使用してログインし、CONTROLLER_USERNAME、CONTROLLER_PASSWORD、および ACCEPT_EULA の env var set を使用してログインします。
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--cluster-name -n`
クラスター名。
#### `--controller-username -u`
アカウントユーザー。 この引数を使用しない場合は、環境変数 CONTROLLER_USERNAME を設定できます。
#### `--controller-endpoint -e`
クラスターコントローラーのエンド https://host:port ポイント ""。 この引数を使用しない場合は、コンピューターで kube config を使用することができます。 構成が/.kube/config の既定の<user home>場所にあることを確認するか、KUBECONFIG env var を使用してください。
#### `--accept-eula -a`
ライセンス条項に同意しますか? [はい/いいえ]。 この引数を使用しない場合は、環境変数 ACCEPT_EULA を "yes" に設定します。 この製品のライセンス条項に https://aka.ms/azdata-eula ついては、「」を参照してください。
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
## <a name="azdata-logout"></a>azdata ログアウト
クラスターからログアウトします。
```bash
azdata logout 
```
### <a name="examples"></a>使用例
このユーザーをログアウトします。
```bash
azdata logout
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

**Azdata**ツールをインストールする方法の詳細については、「 [Azdata をインストールして SQL Server 2019 ビッグデータクラスターを管理する](deploy-install-azdata.md)」を参照してください。
