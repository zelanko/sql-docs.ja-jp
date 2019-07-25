---
title: Azdata を使用してアプリケーションをデプロイする
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグデータクラスター (プレビュー) で、Python または R スクリプトをアプリケーションとしてデプロイします。
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 06b76e7eb8eec8db1993ca558a1f57355457c4ad
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419486"
---
# <a name="how-to-deploy-an-app-on-sql-server-big-data-cluster-preview"></a>SQL Server ビッグデータクラスターにアプリをデプロイする方法 (プレビュー)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) 内でアプリケーションとして R および Python スクリプトをデプロイして管理する方法について説明します。

## <a name="whats-new-and-improved"></a>新機能と強化された機能

- クラスターとアプリを管理するための単一のコマンドラインユーティリティ。
- 仕様ファイルを細かく制御しながら、アプリのデプロイを簡略化します。
- 追加のアプリケーションの種類のホスティングのサポート-SSIS および MLeap (CTP 2.3 の新機能)
- アプリケーションの展開を管理するための[VS Code 拡張機能](app-deployment-extension.md)

アプリケーションは、コマンドラインユーティリティ`azdata`を使用して展開および管理されます。 この記事では、コマンドラインからアプリを展開する方法の例を示します。 でこれを使用する方法については Visual Studio Code [VS Code 拡張機能](app-deployment-extension.md)に関するページを参照してください。

サポートされているアプリの種類は次のとおりです。
- R と Python アプリ (関数、モデル、アプリ)
- MLeap サービス
- SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>必須コンポーネント

- [SQL Server 2019 ビッグデータクラスター](deployment-guidance.md)
- [azdata コマンドラインユーティリティ](deploy-install-azdata.md)

## <a name="capabilities"></a>Capabilities

SQL Server 2019 (プレビュー) では、アプリケーションの作成、削除、説明、初期化、一覧の実行、および更新を行うことができます。 次の表では、 **azdata**で使用できるアプリケーションの展開コマンドについて説明します。

|Command |説明 |
|:---|:---|
|`azdata login` | SQL Server ビッグデータクラスターへのサインイン |
|`azdata app create` | アプリケーションを作成します。 |
|`azdata app delete` | アプリケーションを削除します。 |
|`azdata app describe` | アプリケーションについて説明します。 |
|`azdata app init` | Kickstart 新しいアプリケーションスケルトン。 |
|`azdata app list` | アプリケーションを一覧表示します。 |
|`azdata app run` | アプリケーションを実行します。 |
|`azdata app update`| アプリケーションを更新します。 |

次の例のように`--help` 、パラメーターのヘルプを取得できます。

```bash
azdata app create --help
```

以下のセクションでは、これらのコマンドについて詳しく説明します。

## <a name="sign-in"></a>サインイン

アプリケーションをデプロイまたは操作する前に、まず、 `azdata login`コマンドを使用して SQL Server ビッグデータクラスターにサインインします。 `controller-svc-external`サービスの外部 IP アドレス (例: `https://ip-address:30080`) を、クラスターのユーザー名とパスワードと共に指定します。

```bash
azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
```

## <a name="aks"></a>AKS

AKS を使用している場合は、bash または cmd ウィンドウで次のコマンドを実行`mgmtproxy-svc-external`して、サービスの IP アドレスを取得するために、次のコマンドを実行する必要があります。


```bash
kubectl get svc mgmtproxy-svc-external -n <name of your big data cluster>
```

## <a name="kubeadm-or-minikube"></a>Kubeadm または Minikube

Kubeadm または Minikube を使用している場合は、次のコマンドを実行して、クラスターにログインするための IP アドレスを取得します。

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>アプリを作成する

アプリケーションを作成するには、 `azdata` `app create`コマンドを使用してを使用します。 これらのファイルは、アプリを作成するコンピューター上にローカルに配置されます。

ビッグデータクラスターで新しいアプリを作成するには、次の構文を使用します。

```bash
azdata app create --spec <directory containing spec file>
```

次のコマンドは、このコマンドの例を示しています。

```bash
azdata app create --spec ./addpy
```

これは、 `addpy`アプリケーションがフォルダーに格納されていることを前提としています。 このフォルダーには、と呼ばれる`spec.yaml`アプリケーションの仕様ファイルも含まれている必要があります。 `spec.yaml`ファイルの詳細について[は、「アプリケーションの配置」ページ](concept-application-deployment.md)を参照してください。

このアプリサンプルアプリをデプロイするには、という名前`addpy`のディレクトリに次のファイルを作成します。

- `add.py`。 次の Python コードをこのファイルにコピーします。
   ```py
   #add.py
   def add(x,y):
        result = x+y
        return result
    result=add(x,y)
   ```
- `spec.yaml`。 次のコードをこのファイルにコピーします。
   ```yaml
   #spec.yaml
   name: add-app #name of your python script
   version: v1  #version of the app
   runtime: Python #the language this app uses (R or Python)
   src: ./add.py #full path to the location of the app
   entrypoint: add #the function that will be called upon execution
   replicas: 1  #number of replicas needed
   poolsize: 1  #the pool size that you need your app to scale
   inputs:  #input parameters that the app expects and the type
     x: int
     y: int
   output: #output parameter the app expects and the type
     result: int
   ```

次に、次のコマンドを実行します。

```bash
azdata app create --spec ./addpy
```

List コマンドを使用してアプリが展開されているかどうかを確認できます。

```bash
azdata app list
```

デプロイが完了していない場合は、 `state`次`WaitingforCreate`の例のように表示されます。

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

デプロイが正常に完了すると、 `state` `Ready`状態が変更されていることがわかります。

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>アプリを一覧表示する

コマンドを使用して、 `app list`正常に作成されたすべてのアプリを一覧表示できます。

次のコマンドは、ビッグデータクラスターで使用可能なすべてのアプリケーションを一覧表示します。

```bash
azdata app list
```

名前とバージョンを指定すると、その特定のアプリとその状態 (作成中または準備完了) が一覧表示されます。

```bash
azdata app list --name <app_name> --version <app_version>
```

このコマンドの例を次に示します。

```bash
azdata app list --name add-app --version v1
```

次の例のような出力が表示されます。

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>アプリを実行する

アプリが`Ready`状態の場合は、指定された入力パラメーターを使用して実行することで、アプリを使用できます。 アプリを実行するには、次の構文を使用します。

```bash
azdata app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

次のコマンド例では、run コマンドを示します。

```bash
azdata app run --name add-app --version v1 --inputs x=1,y=2
```

実行が成功した場合は、アプリの作成時に指定した出力が表示されます。 以下に例を示します。

```json
{
  "changedFiles": [],
  "consoleOutput": "",
  "errorMessage": "",
  "outputFiles": {},
  "outputParameters": {
    "result": 3
  },
  "success": true
}
```

## <a name="create-an-app-skeleton"></a>アプリスケルトンを作成する

Init コマンドは、アプリのデプロイに必要な関連するアーティファクトを含むスキャフォールディングを提供します。 次の例では、次のコマンドを実行して hello を作成します。

```bash
azdata app init --name hello --version v1 --template python
```

これにより、hello という名前のフォルダーが作成されます。  ディレクトリに`cd`入り、フォルダー内の生成されたファイルを調べることができます。 spec は、名前、バージョン、ソースコードなどのアプリを定義します。 仕様を編集して、名前、バージョン、入力、および出力を変更することができます。

フォルダーに表示される init コマンドからの出力例を次に示します。

```
hello.py
README.md
run-spec.yaml
spec.yaml

```

## <a name="describe-an-app"></a>アプリの説明

[説明] コマンドは、クラスター内のエンドポイントを含む、アプリに関する詳細情報を提供します。 これは通常、swagger クライアントを使用してアプリを構築し、web サービスを使用して RESTful 方式でアプリと対話するアプリ開発者によって使用されます。 詳細については、「[ビッグデータクラスターでのアプリケーションの使用](big-data-cluster-consume-apps.md)」を参照してください。

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30777/api/app/add-app/v1",
    "swagger": "https://10.1.1.3:30777/api/app/add-app/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

## <a name="delete-an-app"></a>アプリを削除する

ビッグデータクラスターからアプリを削除するには、次の構文を使用します。

```bash
azdata app delete --name add-app --version v1
```

## <a name="next-steps"></a>次のステップ

詳細については、「[ビッグデータクラスターでアプリケーションを使用](big-data-cluster-consume-apps.md)する」で、SQL Server ビッグデータクラスターにデプロイされているアプリを独自のアプリケーションに統合する方法について説明します。 [アプリのデプロイのサンプル](https://aka.ms/sql-app-deploy)で追加のサンプルを確認することもできます。

ビッグデータクラスター SQL Server の詳細については、「 [SQL Server 2019 ビッグデータクラスターとは](big-data-cluster-overview.md)」を参照してください。
