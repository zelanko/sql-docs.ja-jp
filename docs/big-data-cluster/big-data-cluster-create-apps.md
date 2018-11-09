---
title: SQL Server のビッグ データ クラスター上のアプリをデプロイする方法 |Microsoft Docs
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) でアプリケーションとしては、Python または R スクリプトを展開します。
author: TheBharath
ms.author: bharaths
manager: craigg
ms.date: 11/07/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: dd24b4379f50a5b974e7a0a90412d1e13bf6db22
ms.sourcegitcommit: 87fec38a515a7c524b7c99f99bc6f4d338e09846
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2018
ms.locfileid: "51272560"
---
# <a name="how-to-deploy-an-app-on-sql-server-2019-big-data-cluster-preview"></a>SQL Server 2019 ビッグ データ クラスター (プレビュー) でアプリをデプロイする方法

この記事では、デプロイし、SQL Server 2019 ビッグ データ クラスター (プレビュー) 内でアプリケーションとして R と Python スクリプトを管理する方法について説明します。

R および Python アプリケーションがデプロイおよびで管理されている、 **mssqlctl pre**コマンド ライン ユーティリティ CTP 2.1 に含まれています。 この記事では、これらの R と Python スクリプトをコマンドラインからのアプリとして展開する方法の例を示します。

## <a name="prerequisites"></a>前提条件

構成されている SQL Server 2019 ビッグ データ クラスターが必要です。 詳細については、次を参照してください。[を Kubernetes クラスターのビッグ データ、SQL Server をデプロイする方法](deployment-guidance.md)します。 

## <a name="installation"></a>インストール

**Mssqlctl pre** Python および R のアプリケーション展開機能をプレビューするコマンド ライン ユーティリティが提供されます。 ユーティリティをインストールするのにには、次のコマンドを使用します。

```cmd
pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctlpre
```

## <a name="capabilities"></a>Capabilities

CTP 2.1 では作成することができますでは、リストを削除し、R または Python アプリケーションを実行します。 次の表は、アプリケーションの展開コマンドで使用できる**mssqlctl pre**します。

| コマンド | 説明 |
|---|---|
| `mssqlctl-pre login` | SQL Server のビッグ データ クラスターにログインします。 |
| `mssqlctl-pre app create` | アプリを作成します。 |
| `mssqlctl-pre app list` | デプロイ済みのアプリを一覧表示します。 |
| `mssqlctl-pre app delete` | アプリを削除します。 |
| `mssqlctl-pre app run` | 実行中のアプリを一覧表示します。 |

ヘルプを表示できる、`--help`次の例のようにパラメーター。

```bash
mssqlctl-pre app create --help
```

次に、これらのコマンドについて詳しく説明します。

## <a name="log-in"></a>ログイン

R および Python アプリケーションを構成する前にまずは、ログインを使用したクラスターのビッグ データ、SQL Server に、`mssqlctl-pre login`コマンド。 IP アドレス (外部) を指定、 `service-proxy-lb` (例: `https://ip-address:30777`) およびユーザー名とクラスターへのパスワード。

Bash または cmd ウィンドウでこのコマンドを実行してサービス プロキシ-lb サービスの IP アドレスを取得できます。
```bash 
kubectl get svc service-proxy-lb -n <name of your cluster>
```

```bash
mssqlctl-pre login -e https://<ip-address-of-service-proxy-lb> -u <user-name> -p <password>
```

## <a name="create-an-app"></a>アプリを作成します。

アプリケーションを作成するに Python または R のコード ファイルを渡します**mssqlctl pre**で、`app create`コマンド。 これらのファイルからアプリを作成しているコンピューターでローカルに存在します。

ビッグ データ クラスターで新しいアプリを作成するのにには、次の構文を使用します。

```bash
mssqlctl-pre app create -n <app_name> -v <version_number> -r <runtime> -i <path_to_code_init> -c <path_to_code> --inputs <input_params> --outputs <output_params> 
```

次のコマンドは、このコマンドの例を示しています。

```py
#add.py
def add(x,y):
        result = x+y
        return result;
result=add(x,y)
```
これには、として、ローカル ディレクトリに、上記のコード行を保存`add.py`し、次のコマンドを実行

```bash
mssqlctl-pre app create --name add-app --version v1 --runtime Python --code ./add.py  --inputs x=int,y=int --outputs result=int 
```

一覧のコマンドを使用して、アプリをデプロイするかどうかを確認できます。

```bash
mssqlctl-pre app list
```

デプロイが完了していない場合、「状態」表示「作成」が表示されます。 

```
[
  {
    "name": "add-app",
    "state": "Creating",
    "version": "v1"
  }
]
```

展開が成功した後は、"state"が表示されます「準備完了」状態に変更します。

```
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>アプリを登録します。

正常に作成されたすべてのアプリの一覧を表示することができます、`app list`コマンド。

次のコマンドでは、ビッグ データ クラスター内のすべての利用可能なアプリケーションが表示されます。

```bash
mssqlctl-pre app list
```

名前とバージョンを指定すると、その特定のアプリとその状態 (作成または準備完了) は一覧します。

```bash
mssqlctl-pre app list --name <app_name> --version <app_version>
```

次の例では、このコマンドを示しています。

```bash
mssqlctl-pre app list --name add-app --version v1
```

次の例のような出力が表示されます。

```
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>アプリを実行します。

アプリが"Ready"状態にある場合は、指定された入力パラメーターで実行することで使用できます。 アプリを実行するのにには、次の構文を使用します。

```bash
mssqlctl-pre app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

次のコマンドの例では、run コマンドを示しています。

```bash
mssqlctl-pre app run --name add-app --version v1 --inputs x=1,y=2
```

実行が成功した場合、アプリの作成時に指定すると、出力が表示されます。 以下に例を示します。

```
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

## <a name="delete-an-app"></a>アプリを削除します。

ビッグ データ クラスターからアプリを削除するには、次の構文を使用します。

```bash
mssqlctl-pre app delete --name add-app --version v1
```

## <a name="next-steps"></a>次の手順

その他のサンプルを確認することもできます。 [ https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster)します。 

ビッグ データの SQL Server クラスターの詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)します。
