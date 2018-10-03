---
title: Azure Data Studio の機能を拡張 |Microsoft Docs
description: Azure Data Studio を拡張する方法について説明します
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b458234f0a166f3dc820cbfa58269bb90d7c33b2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "48039076"
---
# <a name="getting-started-with-includename-sosincludesname-sos-shortmd-extensibility"></a>概要[!INCLUDE[name-sos](../includes/name-sos-short.md)]機能拡張

[!INCLUDE[name-sos](../includes/name-sos.md)] ユーザー エクスペリエンスをカスタマイズし、これらのカスタマイズを全体のユーザー コミュニティを利用できるようにするいくつかの機能拡張メカニズムがあります。 コア[!INCLUDE[name-sos](../includes/name-sos.md)]プラットフォームの作成対象 Visual Studio Code、Visual Studio Code 拡張 Api のほとんどが使用できるようにします。 さらに、データの管理に固有のアクティビティの追加の機能拡張ポイントを用意されていますしました。

主要な拡張ポイントを次に示します。

- Visual Studio Code 拡張 Api
- Azure の Data Studio 拡張機能作成ツール
- 管理ダッシュ ボード タブのパネルの投稿
- アクションのエクスペリエンスを備えた insights
- Azure Data Studio 機能拡張 Api
- カスタム データ プロバイダーの Api

## <a name="visual-studio-code-extensibility-apis"></a>Visual Studio Code 拡張 Api

コア[!INCLUDE[name-sos](../includes/name-sos.md)]プラットフォームが Visual Studio Code に基づいて構築されていますが、Visual Studio Code 拡張機能 Api に関する詳細が記載、[拡張機能作成](https://code.visualstudio.com/docs/extensions/overview)と[拡張機能 API](https://code.visualstudio.com/docs/extensionAPI/overview)Visual Studio Code の web サイトに関するドキュメントです。

## <a name="manage-dashboard-tab-panel-contributions"></a>管理ダッシュ ボード タブのパネルの投稿

詳細については、次を参照してください。[貢献ポイント](#contribution-points)と[コンテキスト変数](#context-variables)します。

## <a name="azure-data-studio-extensibility-apis"></a>Azure Data Studio 機能拡張 Api

詳細については、次を参照してください。[拡張性 Api](extensibility-apis.md)します。


## <a name="contribution-points"></a>貢献ポイント

このセクションでは、package.json の拡張機能マニフェストで定義されているさまざまなコントリビューション ポイントについて説明します。

IntelliSense は azuredatastudio 内でサポートされています。

## <a name="contributes-dashboard"></a>ダッシュ ボードを貢献します。

タブ、コンテナー、ダッシュ ボードに insight ウィジェットを投稿します。

![ダッシュボード](media/extensibility/dashboard-page.png)

`dashboard.tabs`

Dashboard.tabs では、タブ セクションでは、ダッシュ ボード ページ内で作成します。 オブジェクトまたはオブジェクトの配列が期待しています。  

```json
"dashboard.tabs": [
{
    "id": "test-tab1",
    "title": "Test 1",
    "description": "The test 1 displays a list of widgets.",
    "when": "connectionProvider == 'MSSQL' && !mssql:iscloud",
    "alwaysShow": true,
    "container": {
        …
    }
}
]
```

`dashboard.containers`

代わりに、(dashboard.tab) 内のダッシュ ボードのコンテナーのインラインを指定します。 Dashboard.containers を使用してコンテナーを登録することができます。 オブジェクトまたはオブジェクトの配列を受け入れます。

```json
"dashboard.containers": [
{
    "id": "innerTab1",
    "container": {
        …
    }
},
{
    "id": "innerTab2",
    "container": {
       …
    }
}
]
```

登録済みコンテナーを参照するには、コンテナーの id を指定します。

```json
"dashboard.tabs": [
{
    ...
    "container": {
        "innerTab1": {             
        }
    }
}
]

```

`dashboard.insights`

Dashboard.insights を使用してインサイトを登録することができます。 これはのような[チュートリアル: カスタム インサイト ウィジェットをビルド](https://docs.microsoft.com/en-us/sql/sql-operations-studio/tutorial-build-custom-insight-sql-server)

```json
"dashboard.insights": {
"id": "my-widget"
"type": {
    "count": {
        "dataDirection": "vertical",
        "dataType": "number",
        "legendPosition": "none",
           "labelFirstColumn": false,
        "columnsAsLabels": false
       }
   },
   "queryFile": "{your file folder}/activeSession.sql"
}
```


### <a name="dashboard-container-types"></a>ダッシュ ボードの種類のコンテナー

現在はサポートされているコンテナーの 4 種類があります。

1. `widgets-container`

    ![ウィジェットのコンテナー](media/extensibility/widgets-container.png)

    コンテナーに表示されるウィジェットの一覧。 フロー レイアウトになります。 ウィジェットの一覧を受け入れます。

    ```json
    "container": {
        "widgets-container": [
        {
            "widget": {
                "query-data-store-db-insight": {
                }
            }
        },
        {
            "widget": {
                "explorer-widget": {
                }
            }
        }
      ]
    }
    ```

2. `webview-container`

    ![webview コンテナー](media/extensibility/webview-container.png)

    全体のコンテナーでは、web ビューが表示されます。 Webview id タブの ID が同じにする必要があります。

    ```json
    "container": {
        "webview-container": null
    }
    ```

3. `grid-container`

   ![グリッド コンテナー](media/extensibility/grid-container.png)

   ウィジェットまたはグリッド レイアウトで表示される web 表示の一覧

    ```json
    "container": {
        "grid-container": [
        {
            "name": "widget 1",
            "widget": {
                "explorer-widget": {
                }
            },
            "row":0,
            "col":0
        },
        {
            "name": "widget 2",
            "widget": {
                "tasks-widget": {
                    "backup", 
                    "restore",
                    "configureDashboard",
                    "newQuery"
                }
            },
            "row":0,
            "col":1
        },
        {
            "name": "Webview 1",
            "webview": {
                "id": "google"
            },
            "row":1,
            "col":0,
            "colspan":2
        },
        {
            "name": "widget 3",
            "widget": {
                "explorer-widget": {}
            },
            "row":0,
            "col":3,
            "rowspan":2
        },
    ]
    ```

4.  `nav-section`

    ![nav セクション](media/extensibility/nav-section.png)

    コンテナー内のナビゲーション セクションが表示されます。

    ```json
    "container": {
        "nav-section": [
            {
                "id": "innerTab1",
                "title": "inner-tab1",
                "icon": {
                    "light": "./icons/tab1Icon.svg",
                    "dark": "./icons/tab1Icon_dark.svg"
                }
                "container": {
                    …
                }
            },
            {
                "id": "innerTab2",
                "title": "inner-tab2",
                "icon": {
                    "light": "./icons/tab2Icon.svg",
                    "dark": "./icons/tab2Icon_dark.svg"
                }
                "container": {
                    …
                }
            }
        ]
    }
    ```



## <a name="context-variables"></a>コンテキスト変数

Visual Studio Code とその後に Azure Data Studio でのコンテキストについては、次を参照してください。 [Extensibility](https://code.visualstudio.com/docs/extensionAPI/extension-points#_example)します。

Azure データ studio では、拡張機能の使用可能なデータベース接続に関する特定のコンテキストがあります。

### <a name="dashboard"></a>ダッシュボード

ダッシュ ボードで、次のコンテキスト変数を提供します。

|コンテキスト変数| description|
|:---|:---|
|`connectionProvider` | 現在の接続のプロバイダーの識別子の文字列。 例: `connectionProvider == 'MSSQL'`。|
|`serverName`|現在の接続のサーバー名の文字列。 例: `serverName == 'localhost'`。|
|`databaseName` | 現在の接続のデータベース名の文字列。 例: `databaseName == 'master'`。|
|`connection` | 現在の接続 (IConnectionProfile) の完全な接続プロファイル オブジェクト|
|`dashboardContext` | ダッシュ ボードのページのコンテキストの文字列は現在のです。 'Database' または 'server'。 例: `dashboardContext == 'database'`|
