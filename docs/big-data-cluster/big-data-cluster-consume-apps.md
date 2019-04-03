---
title: ビッグ データ クラスター上のアプリケーションを使用します。
titleSuffix: SQL Server big data clusters
description: RESTful web サービス (プレビュー) を使用して SQL Server 2019 ビッグ データ クラスターでデプロイされたアプリケーションを使用します。
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: jroth
manager: craigg
ms.date: 03/18/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 4d299f364b4d67e1f31ce7c0e70d6ba062933f37
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860543"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>RESTful web サービスを使用して SQL Server のビッグ データ クラスターにデプロイされたアプリを使用します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、RESTful web サービス (プレビュー) を使用して SQL Server 2019 ビッグ データ クラスターにデプロイされたアプリを使用する方法について説明します。

## <a name="prerequisites"></a>前提条件

- [SQL Server 2019 ビッグ データ クラスター](deployment-guidance.md)
- [mssqlctl コマンド ライン ユーティリティ](deploy-install-mssqlctl.md)
- いずれかを使用してデプロイされたアプリ[ `mssqlctl` ](big-data-cluster-create-apps.md)または[アプリのデプロイの拡張機能](app-deployment-extension.md)

## <a name="capabilities"></a>Capabilities

SQL Server 2019 ビッグ データ クラスター (プレビュー) にアプリケーションを配置した後にアクセスし、RESTful web サービスを使用してアプリケーションを使用できます。 これには、他のアプリケーションやサービス (たとえば、モバイル アプリまたは web サイト) からそのアプリの統合が実現できます。 次の表は、アプリケーションの展開コマンドで使用できる**mssqlctl**アプリの RESTful web サービスに関する情報を取得します。

|コマンド |説明 |
|:---|:---|
|`mssqlctl app describe` | アプリケーションをについて説明します。 |

ヘルプを表示できる、`--help`次の例のようにパラメーター。

```bash
mssqlctl app describe --help
```

次のセクションでは、アプリケーションのエンドポイントを取得する方法とアプリケーションの統合、RESTful web サービスを操作する方法について説明します。

## <a name="retrieve-the-endpoint"></a>エンドポイントを取得します。

**Mssqlctl アプリについて説明する**コマンドは、クラスター内の終点を含むアプリに関する詳細情報を提供します。 これは通常使用して、アプリの開発者 swagger クライアントを使用して、rest ベースの方法で、アプリと対話する web サービスを使用してアプリをビルドします。

次のようなコマンドを実行して、アプリをについて説明します。

```bash
mssqlctl app describe --name addpy --version v1
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

IP アドレスに注意してください (`10.1.1.3`この例では) とポート番号 (`30777`) 出力します。

## <a name="generate-a-jwt-access-token"></a>JWT アクセス トークンを生成します。

展開しているアプリの RESTful web サービスにアクセスするためには、まず、JWT アクセス トークンを生成する必要があります。 次の URL をブラウザーで開きます: `https://[IP]:[PORT]/api/docs/swagger.json` IP アドレスとポートの実行中に取得したを使用して、`describe`上記のコマンド。 使用した同じ資格情報でログインする必要があります`mssqlctl login`します。

内容を貼り付けて、`swagger.json`に、 [Swagger Editor](https://editor.swagger.io)はどのような方法を理解します。

![API Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

通知、 `app` GET メソッドだけでなく`token`POST メソッドです。 POST 呼び出しを好みのツールを使用して、トークンを取得する必要があります apps の認証が JWT トークンを使用しているため、`token`メソッド。 これを実現する方法の例を次に示します[Postman](https://www.getpostman.com/):

![Postman のトークン](media/big-data-cluster-consume-apps/postman_token.png)

この要求の結果が、JWT を与える`access_token`、これは、アプリを実行する URL を呼び出す必要があります。

## <a name="execute-the-app-using-the-restful-web-service"></a>RESTful web サービスを使用して、アプリを実行します。

> [!NOTE]
> する場合は、URL を開くことができます、`swagger`実行したときに返された`mssqlctl app describe --name [appname] --version [version]`ブラウザーでいるようになります`https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`します。 使用した同じ資格情報でログインする必要があります`mssqlctl login`します。 内容、`swagger.json`に貼り付けること[Swagger Editor](https://editor.swagger.io)します。 Web サービスを公開すると表示されます、`run`メソッド。 ベース URL の上部に表示にも注意してください。

好みのツールを使用して呼び出すことができます、`run`メソッド (`https://[IP]:30778/api/app/[appname]/[version]/run`)、json として POST 要求の本文内のパラメーターに渡します。 この例では使用[Postman](https://www.getpostman.com/)します。 呼び出しを行う前に設定する必要があります、`Authorization`に`Bearer Token`以前に取得したトークンに貼り付けます。 これにより、要求ヘッダーが設定されます。 次のスクリーンショットを見てください。

![Postman のヘッダーを実行します。](media/big-data-cluster-consume-apps/postman_run_1.png)

次に、要求の本文にパラメーターを渡すを呼び出しているし、設定アプリに、`content-type`に`application/json`:

![Postman 本体を実行します。](media/big-data-cluster-consume-apps/postman_run_2.png)

要求を送信すると同じ、アプリを実行したときと同様の出力が表示されます`mssqlctl app run`:

![Postman の実行結果](media/big-data-cluster-consume-apps/postman_result.png)

Web サービスを使用してアプリは正常に呼び出すようになりました。 アプリケーションでは、この web サービスを統合する同じ手順を実行できます。

## <a name="next-steps"></a>次のステップ

その他のサンプルを確認することもできます。[アプリの展開サンプル](https://aka.ms/sql-app-deploy)します。

ビッグ データの SQL Server クラスターの詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)します。
