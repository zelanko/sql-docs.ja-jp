---
title: ビッグデータクラスターでのアプリケーションの使用
titleSuffix: SQL Server big data clusters
description: RESTful web サービス (プレビュー) を使用して SQL Server 2019 ビッグデータクラスターにデプロイされたアプリケーションを使用します。
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a2135ef64fb17eba62eab75b81739eda047167ab
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419511"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>RESTful web サービスを使用して SQL Server ビッグデータクラスターにデプロイされたアプリを使用する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、RESTful web サービス (プレビュー) を使用して SQL Server 2019 ビッグデータクラスターにデプロイされたアプリを使用する方法について説明します。

## <a name="prerequisites"></a>必須コンポーネント

- [SQL Server 2019 ビッグデータクラスター](deployment-guidance.md)
- [mssqlctl コマンドラインユーティリティ](deploy-install-azdata.md)
- [Azdata](big-data-cluster-create-apps.md)または[アプリのデプロイ拡張機能](app-deployment-extension.md)を使用してデプロイされたアプリ

## <a name="capabilities"></a>Capabilities

SQL Server 2019 ビッグデータクラスター (プレビュー) にアプリケーションをデプロイした後、RESTful web サービスを使用してそのアプリケーションにアクセスして使用することができます。 これにより、そのアプリを他のアプリケーションやサービス (モバイルアプリや web サイトなど) と統合できるようになります。 次の表では、 **azdata**と共に使用して、アプリの RESTful web サービスに関する情報を取得するアプリケーションの展開コマンドについて説明します。

|Command |説明 |
|:---|:---|
|`azdata app describe` | アプリケーションについて説明します。 |

次の例のように`--help` 、パラメーターのヘルプを取得できます。

```bash
azdata app describe --help
```

以下のセクションでは、アプリケーションのエンドポイントを取得する方法と、アプリケーション統合のために RESTful web サービスを操作する方法について説明します。

## <a name="retrieve-the-endpoint"></a>エンドポイントを取得する

**Azdata app**の [説明] コマンドでは、クラスター内のエンドポイントを含む、アプリに関する詳細情報が提供されます。 これは通常、swagger クライアントを使用してアプリを構築し、web サービスを使用して RESTful 方式でアプリと対話するアプリ開発者によって使用されます。

次のようなコマンドを実行して、アプリを記述します。

```bash
azdata app describe --name addpy --version v1
```

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
    "app": "https://10.1.1.3:30777/api/app/addpy/v1",
    "swagger": "https://10.1.1.3:30777/api/app/addpy/v1/swagger.json"
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

出力の IP アドレス (`10.1.1.3`この例では) とポート番号 (`30777`) に注意してください。

## <a name="generate-a-jwt-access-token"></a>JWT アクセストークンを生成する

デプロイしたアプリの RESTful web サービスにアクセスするには、最初に JWT アクセストークンを生成する必要があります。 ブラウザーで次の URL を開きます`https://[IP]:[PORT]/api/docs/swagger.json` 。上の`describe`コマンドを実行して取得した IP アドレスとポートを使用します。 に使用したの`azdata login`と同じ資格情報でログインする必要があります。

の内容を`swagger.json` [Swagger エディター](https://editor.swagger.io)に貼り付けて、使用可能なメソッドを理解します。

![API の Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

GET メソッド`app` `token`と POST メソッドに注意してください。 アプリの認証では JWT トークンが使用されるため、 `token`メソッドへの POST 呼び出しを行うには、お気に入りのツールを使用してトークンを取得する必要があります。 [Postman](https://www.getpostman.com/)でこれを行う方法の例を次に示します。

![Postman トークン](media/big-data-cluster-consume-apps/postman_token.png)

この要求の結果により、JWT `access_token`が提供されます。これは、アプリを実行するために URL を呼び出す必要があります。

## <a name="execute-the-app-using-the-restful-web-service"></a>RESTful web サービスを使用してアプリを実行する

> [!NOTE]
> 必要に応じて、ブラウザーでを実行`swagger` `azdata app describe --name [appname] --version [version]`したときに返されたの URL を開くことができます。これ`https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`は、のようになります。 に使用したの`azdata login`と同じ資格情報でログインする必要があります。 の`swagger.json`内容を[Swagger エディター](https://editor.swagger.io)に貼り付けることができます。 Web サービスが`run`メソッドを公開していることがわかります。 また、上部に表示されているベース URL にも注意してください。

任意のツールを使用して`run`メソッド (`https://[IP]:30778/api/app/[appname]/[version]/run`) を呼び出し、POST 要求の本文のパラメーターを json として渡すことができます。 この例では、 [Postman](https://www.getpostman.com/)を使用します。 呼び出しを行う前に、 `Authorization`をに`Bearer Token`設定し、前の手順で取得したトークンを貼り付ける必要があります。 これにより、要求にヘッダーが設定されます。 次のスクリーンショットを見てください。

![Postman 実行ヘッダー](media/big-data-cluster-consume-apps/postman_run_1.png)

次に、要求本文で、呼び出しているアプリにパラメーターを渡し、 `content-type`をに`application/json`設定します。

![Postman 実行本文](media/big-data-cluster-consume-apps/postman_run_2.png)

要求を送信すると、を使用`azdata app run`してアプリを実行したときと同じ出力が得られます。

![Postman 実行結果](media/big-data-cluster-consume-apps/postman_result.png)

これで、web サービスを介してアプリが正常に呼び出されました。 同様の手順に従って、この web サービスをアプリケーションに統合することができます。

## <a name="next-steps"></a>次のステップ

[アプリのデプロイのサンプル](https://aka.ms/sql-app-deploy)で追加のサンプルを確認することもできます。

ビッグデータクラスター SQL Server の詳細については、「 [SQL Server 2019 ビッグデータクラスターとは](big-data-cluster-overview.md)」を参照してください。
