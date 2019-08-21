---
title: azdata リファレンス
titleSuffix: SQL Server big data clusters
description: azdata コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 33cc3070647c58e6ae57c8bff3d587a76ae0a28d
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653098"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (プレビュー)](big-data-cluster-overview.md)用の**azdata**ツールのリファレンスを提供しています。 **Azdata**ツールをインストールする方法の詳細については、「[管理[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]する azdata をインストール](deploy-install-azdata.md)する」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
|[azdata app](reference-azdata-app.md) | アプリケーションを作成、削除、実行、および管理します。 |
|[azdata bdc](reference-azdata-bdc.md) | SQL Server ビッグ データ クラスターを選択、管理、および操作します。 |
|[azdata login](#azdata-login) | クラスターのコントローラー エンドポイントにログインします。
|[azdata logout](#azdata-logout) | クラスターからログアウトします。

## <a name="azdata-login"></a>azdata login
クラスターがデプロイされると、デプロイ中にコントローラーエンドポイントが一覧表示されます。これはログインに使用する必要があります。  コントローラーエンドポイントがわからない場合は、システム上のクラスターの kube config を/.kube/config の<user home>既定の場所に配置するか、KUBECONFIG env var (export KUBECONFIG = path/to/kube/config) を使用してログインすることができます。
```bash
azdata login [--cluster-name -n] 
             [--controller-username -u]  
             [--controller-endpoint -e]  
             [--accept-eula -a]
```
### <a name="examples"></a>使用例
対話形式でログインします。 引数として指定されていない場合は、クラスター名の入力が常に求められます。 システムに CONTROLLER_USERNAME、CONTROLLER_PASSWORD、および ACCEPT_EULA 環境変数を設定している場合、これらの入力は求められません。 システムに kube 構成がある場合、または構成のパスを指定するために KUBECONFIG 環境変数を使用している場合は、対話型エクスペリエンスでは、まず構成の使用が試行され、構成が失敗した場合にプロンプトが表示されます。
```bash
azdata login
```
ログイン (非対話形式)。 クラスター名、コントローラーのユーザー名、コントローラー エンドポイント、および使用許諾契約の同意を引数として設定してログインします。 環境変数 CONTROLLER_PASSWORD を設定する必要があります。  コントローラーエンドポイントを指定しない場合は、コンピューター上の kube config を/.kube/config の<user home>既定の場所に配置するか、KUBECONFIG env var (export KUBECONFIG = path/to/kube/config) を使用します。
```bash
azdata login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
マシン上で kube 構成を使用してログインし、CONTROLLER_USERNAME、CONTROLLER_PASSWORD、および ACCEPT_EULA の環境変数を設定してログインします。
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--cluster-name -n`
クラスター名。
#### `--controller-username -u`
アカウント ユーザー。 この引数を使用しない場合は、環境変数 CONTROLLER_USERNAME を設定できます。
#### `--controller-endpoint -e`
クラスター コントローラーのエンドポイント "https://host:port"。 この引数を使用しない場合は、マシンで kube 構成を使用できます。 構成が/.kube/config の既定の<user home>場所にあることを確認するか、KUBECONFIG env var を使用します。
#### `--accept-eula -a`
Do you accept the license terms? (ライセンス条項に同意しますか?) [yes/no]. ([はい/いいえ]。) この引数を使用しない場合は、環境変数 ACCEPT_EULA を 'yes' に設定できます。 
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細については[http://jmespath.org/](http://jmespath.org/]) 、「」を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。
## <a name="azdata-logout"></a>azdata logout
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
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細については[http://jmespath.org/](http://jmespath.org/]) 、「」を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。

## <a name="next-steps"></a>次の手順

**Azdata**ツールをインストールする方法の詳細については、「[管理[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]する azdata をインストール](deploy-install-azdata.md)する」を参照してください。
