---
title: "Reporting Services の REST Api を使用して開発 |Microsoft ドキュメント"
ms.description: The REST API provides programmatic access to the objects in a SQL Server 2017 Reporting Services report server catalog.
ms.date: 10/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 7c2c34047ac316045387b036cf10ee149175580a
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="develop-with-the-rest-apis-for-reporting-services"></a>Reporting Services の REST Api を使用した開発します。

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

Microsoft SQL Server 2017 Reporting Services では、Representational State Transfer (REST) Api をサポートします。 REST Api は、サービスを提供する HTTP 操作 (メソッド) のセットをサポートするエンドポイントを作成、取得、更新、またはレポート サーバー内のリソースへのアクセスを削除します。

REST API は、SQL Server 2017 Reporting Services レポート サーバー カタログ内のオブジェクトにプログラムでアクセスを提供します。 オブジェクトには、フォルダー、レポート、Kpi、データ ソース、データセット、更新プラン、サブスクリプション、および詳細があります。 REST API を使用する、たとえば、フォルダー階層内を移動、フォルダーの内容を検出したり、レポート定義をダウンロードできます。 ことができますも作成、更新、およびオブジェクトを削除します。 オブジェクトを操作の例は、レポートのアップロード、更新計画を実行、フォルダーを削除およびなどです。

## <a name="components-of-a-rest-api-requestresponse"></a>REST API の要求/応答のコンポーネント

REST API 要求/応答の組み合わせは、5 つのコンポーネントに分けることができます。

* **要求の URI**から構成される:`{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`です。 要求 URI は、要求メッセージ ヘッダーに含まれていますが、おを呼び出すことこことは別にほとんどの言語やフレームワークを必要とすると、要求メッセージから個別に渡すためです。

    * URI スキーム: 要求を送信するために使用するプロトコルを指定します。 たとえば、`http`または`https`です。
    * URI ホスト: ドメイン名またはサービスの REST エンドポイントがホストされているなどのサーバーの IP アドレスを指定`myserver.contoso.com`です。
    * リソースのパス: リソースまたはリソースのコレクションは、それらのリソースの選択範囲を決定するとき、サービスによって使用される複数のセグメントを含めることがありますを指定します。 例: `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` CatalogItem の指定したプロパティを取得するために使用できます。
    * クエリ文字列 (省略可能)。 API バージョンまたはリソースの選択条件など、追加の単純なパラメーターを提供します。

* HTTP 要求メッセージのヘッダー フィールド:

    * 必要な[HTTP メソッド](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)とも呼ばれる、操作 (動詞)、サービスに要求している操作の種類を通知します。 Reporting Services REST Api をサポートして DELETE、GET、HEAD、PUT、POST と、メソッドの修正プログラムを適用します。
    * 省略可能な追加のヘッダー フィールド、指定した URI および HTTP メソッドで必要とします。

* 省略可能な HTTP**要求メッセージの本文**URI および HTTP 操作をサポートするためのフィールドです。 たとえば、POST 操作には、複雑なパラメーターとして渡された MIME でエンコードされたオブジェクトが含まれています。 POST または PUT 操作では、本文の MIME エンコードの種類を指定する必要があります、`Content-type`要求ヘッダーにもします。 一部のサービスなどの特定の MIME タイプを使用する必要があります`application/json`です。

* HTTP**応答メッセージ ヘッダー**フィールド。

    * [HTTP ステータス コード](http://www.w3.org/Protocols/HTTP/HTRESP.html)4 xx または 5 xx のエラー コードを 2 xx 成功コードの範囲、します。 また、サービスで定義されたステータス コード可能性があります返される、API のドキュメントに記載されています。
    * 省略可能な追加のヘッダー フィールドなど、要求の応答をサポートするために、`Content-type`応答ヘッダー。

* 省略可能な HTTP**応答メッセージの本文**フィールド。

    * 応答の MIME でエンコードされたオブジェクトは、データを返す GET メソッドからの応答など、HTTP 応答の本文で返されます。 通常、これらのオブジェクトが返されますなどの JSON または XML を構造化された形式でによって示される、`Content-type`応答ヘッダー。

## <a name="api-documentation"></a>API のドキュメント

最新の API ドキュメントの最新の REST API を呼び出します。 (ルール サブタイプ)、REST API は、OpenAPI 仕様に基づいて構築されて swagger specification) ドキュメントが[SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0)です。 API の文書化、を超えて SwaggerHub 選択肢: JavaScript、TypeScript、c#、Java、Python、Ruby、および複数の言語でクライアント ライブラリの生成に役立ちます。

## <a name="testing-api-calls"></a>テストの API 呼び出し

HTTP 要求/応答メッセージをテストするためのツールは[Fiddler](http://www.telerik.com/fiddler)です。 Fiddler は、デバッグの HTTP 要求を診断しやすく、REST 要求を遮断するプロキシ無料の web/応答メッセージ。

## <a name="next-steps"></a>次の手順

上で利用可能な Api を確認[SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0)です。

使用可能なサンプル[GitHub](https://github.com/Microsoft/Reporting-Services)です。 このサンプルには、TypeScript、対応、および PowerShell の使用例と共に webpack 上に構築された HTML5 アプリケーションが含まれています。

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
