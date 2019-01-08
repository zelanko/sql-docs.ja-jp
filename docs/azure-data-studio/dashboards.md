---
title: Insights および一般的なタスクを簡単にアクセスします。
titleSuffix: Azure Data Studio
description: Azure Data Studio でデータベースのダッシュ ボード ウィジェットを表示する方法について説明します。
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: faaa59e8607f707bb43f31638880f771ae7ae6ab
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030486"
---
# <a name="dashboards-in-includename-sosincludesname-sos-shortmd"></a>ダッシュ ボード [!INCLUDE[name-sos](../includes/name-sos-short.md)]

ダッシュ ボード、右クリックして、サーバーまたはデータベースを表示および選択**管理**します。

![サンプルのダッシュ ボード](media/dashboards/sample-dashboard.png)

**サーバーのプロパティ**バージョン、エディション、コンピューター名、および OS のバージョンを含む、サーバーのプロパティが含まれています。

**タスク**commons タスク復元と新しいクエリなどが含まれています。

**データベース検索**テーブルを含む、サーバーに格納されている既存のデータベースを簡単に確認します。

**バックアップの状態**既存のデータベースのバックアップの状態を簡単に確認します。

## <a name="configuring-insight-widgets"></a>洞察のウィジェットを構成します。
ダッシュ ボードを設定するためのチュートリアルに従うことを強くお勧め[ここ](tutorial-build-custom-insight-sql-server.md)します。

さらに、必ずチェック アウト、[洞察のウィジェットの構成の操作方法に関する]()します。

このチュートリアルでは、次に読み取られた後に、このチュートリアルで取り上げられていない特定のウィジェットについて説明します。

## <a name="insight-detail"></a>インサイトの詳細
インサイトの詳細のポップアップは、関連する洞察のウィジェットのより詳細な情報を提供します。 
- 洞察のウィジェットでは、カウント、行、グラフなどの概要概要ビューを表示します。 
- インサイトの詳細のフライアウトは、高レベルの洞察のウィジェットに表示された各項目のより深いデータ洞察を一覧表示する、「ドリル」の詳細を説明します。 
  - 詳細のポップアップの内容は、メインのウィジェットのクエリを別の SQL クエリで定義されます。

インサイトの詳細クエリでは、セットの要件はありませんが、レイアウトは標準。
- ビューの上半分は、常に、2 列の"summary"ビューです。 JSON 構成のプロパティ"label"と"value"プロパティで使用する列が定義されています。
- 概要テーブル内の行をクリックすると、下部にある、フライアウトの半分はリストの完全なセットの該当する行の列情報。

### <a name="insight-detail-configuration-in-packagejson"></a>Package.json でインサイトの詳細構成

インサイトの詳細のフライアウトのサンプル構成
```json
"details": {
    "queryFile": "./relative_path_to_sqlfile_from_package_json_file.sql",
    "label": {
        "icon": "database",
        "column": "first_column_name_for_summary_list_view",
        "state": [
            {
                "condition": {
                    "if": "equals",
                    "equals": "0"
                },
                "color": "red"
            },
            {
                "condition": {
                    "if": "equals",
                    "equals": "1"
                },
                "color": "orange"
            },
            {
                "condition": {
                    "if": "equals",
                    "equals": "2"
                },
                "color": "green"
            }
        ]
    },
    "value": "second_column_and_condition_check_value_column_for_summary_list_view",
```
|property|型|value|既定値|description|comment|
|:---|:---|:---|:---|:---|:---|
|詳細情報|json オブジェクト|||その構造内で洞察の詳細の定義を定義する必須のプロパティ||
|queryFile|string|||insight 詳細 sql クエリ ファイルのパスとファイル名 package.json の位置を基準||
|ラベル●らべる○|json オブジェクト|||概要のリスト ビューでの各品目を定義する必須のプロパティ|将来的に 'summaryList' のように変更するには、このプロパティの名前|
|アイコン●あいこん○|string|||各概要リスト ビュー項目に表示されるアイコンの名前を指定します。|サポートされているアイコンの (tbd) の一覧が文書化します。|
|column|string|||クエリの結果セットから概要リスト ビューで最初の列の名前を示す|後で、このプロパティの名前はより直感的な名前に変更されます。|
|value|string|||クエリの結果セットから概要リスト ビューで 2 番目の列の名前を指定します。 この列の値の使用条件を確認し、各概要リスト ビュー項目の色のドットの色を設定するには|後でこのプロパティの名前より直感的なものに変わります。|
|condition|json オブジェクト|||列の値の条件のチェックを定義し、各集計のリスト ビュー項目の色を決定します。||
|if|string|常に、equals、notEquals、greaterThan、lessThan、greaterThanOrEquals lessThanOrEquals||条件のチェック演算子|後で、プロパティ名が、演算子に変わります。|
|equals|string|||条件チェックの値|後でこのプロパティ名が、'value' に変わります。|

## <a name="insight-actions"></a>Insight アクション
洞察のウィジェットと洞察の詳細、または管理する、問題を軽減するアクション プランの簡単に取得できます。 たとえば、DBCC CHECKDB を実行すると考えることをエラー ログを読み取り、データベースが復旧待ち状態であるときに、データベースを復元またはします。 またはを実行するアクションのいずれかのことができます。

使用して[!INCLUDE[name-sos](../includes/name-sos-short.md)]の Insight アクション構成では、復元、または sql スクリプトを使用して定義されている独自のアクションの表示などの組み込みのアクションをマップすることができます。

> Sql スクリプトを使用して、カスタム アクションの構成は、開発中と、それはまだプライベート プレビュー ビルドでは利用できません。

## <a name="sample-insight-action-definition"></a>サンプル Insight アクションの定義

```"actions"{}``` insight アクションを定義します。 アクションをなど、特定のスコープを定義できます```"server"```、```"database"```などと[!INCLUDE[name-sos](../includes/name-sos-short.md)]アクションに現在の接続コンテキスト情報を渡します。

WideWorldImporters データベースの復元アクションが起動されたときに、```"database": "${Database}"```を渡すことを示します定義```Database```復元操作にクエリの結果の列の値。 データベースの復元操作を開始します。 ```"types"``` json 配列であり、配列に複数のアクションを表示できます。 コンテキスト メニューが基本的にそのユーザーをクリックして、操作を実行する分析情報の詳細 ダイアログでします。 

> [!INCLUDE[name-sos](../includes/name-sos-short.md)] 「バックアップ」、"restore"「新しいクエリ」および"新しい"データベース アクションの種類として、プレビュー 0.17.1 が有効にします。

```json
"details": {
    "queryFile": "./sql/database_state_detail.sql",
    "label": {...},
    "value": "state",
    "actions": {
        "database": "${Database}",
        "types": ["restore"]
    }
}
```
