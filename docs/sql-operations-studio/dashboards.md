---
title: "Insights と SQL 操作 Studio (プレビュー) での一般的なタスクを簡単にアクセス |Microsoft ドキュメント"
description: "SQL 操作 Studio (プレビュー) で洞察に富んだウィジェットを表示する方法について説明します。"
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b501b653920d2a8ff7e3e8ed4656c8154b344f6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="dashboards-in-includename-sosincludesname-sos-shortmd"></a>ダッシュ ボード[!INCLUDE[name-sos](../includes/name-sos-short.md)]

ダッシュ ボード、右クリックし、サーバーまたはデータベースを表示および選択**管理**です。

![サンプルのダッシュ ボード](media/dashboards/sample-dashboard.png)

**サーバーのプロパティ**バージョン、エディション、コンピューター名、およびオペレーティング システムのバージョンを含む、サーバーのプロパティが含まれています。

**タスク**コモンズ タスク復元し、新しいクエリなどにはが含まれています。

**データベース検索**テーブルを含む、サーバーに格納されている既存のデータベースを簡単に検索します。

**バックアップの状態**既存のデータベースのバックアップの状態を簡単に検索します。

## <a name="configuring-insight-widgets"></a>Insight ウィジェットを構成します。
ダッシュ ボードを設定するためのチュートリアルに従うことを強くお勧め[ここ](tutorial-build-custom-insight-sql-server.md)です。

加えて、チェック アウトすることを確認して、 [insight ウィジェットの構成の操作方法に関する]()です。

このチュートリアルの後に読み取られた後に、このチュートリアルで説明されていない特定のウィジェットについてを説明します。

## <a name="insight-detail"></a>情報の詳細
Insight 詳細フライアウトは、関連するインサイト ウィジェットのより詳細な情報を提供します。 
- Insight ウィジェットでは、カウント、線、グラフなどの概要、概要ビューをレンダリングします。 
- Insight 詳細フライアウトは、ウィジェットで、高度な洞察の各項目のデータのより深い洞察を一覧表示する、「にドリル ダウン」の詳細を提供します。 
  - 詳細フライアウト内容は、メインのウィジェットのクエリを別の SQL クエリで定義されます。 

クエリについては、情報の詳細、一連の要件はありませんが、レイアウトは標準です。
- ビューの上半分は、常に 2 列「概要」ビューです。 JSON の構成の"value"と「ラベル」プロパティで使用する列が定義されています。
- 概要テーブル内の行をクリックすると、下部にあるフライアウトの半分はリストの完全なセットの該当する行の列情報です。

### <a name="insight-detail-configuration-in-packagejson"></a>Package.json の洞察詳細構成

サンプル Insight 詳細フライアウトの構成
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
|詳細情報|json オブジェクト|||必須のプロパティの構造内で洞察詳細定義を定義||
|queryFile|string|||package.json の場所への相対ファイル名と洞察詳細 sql クエリ ファイル パス||
|ラベル●らべる○|json オブジェクト|||概要リスト ビューの各行アイテムを定義する必須のプロパティ|将来的に 'summaryList' のように変更するには、このプロパティの名前|
|アイコン●あいこん○|string|||各概要リスト ビュー項目のリーダーをアイコンの名前を指定します。|サポートされているアイコンのリストを (tbd) が文書化します。|
|column|string|||概要リスト ビューで、クエリの結果セットから最初の列の名前を示す|将来的に、このプロパティの名前はよりわかりやすい名前に変更されます。|
|value|string|||クエリの結果セットから集計のリスト ビューで 2 番目の列の名前を指定します。 この列の値が条件を確認し、各集計のリスト ビュー項目の色のドットの色を設定します。|後でこのプロパティの名前より直感的なものに変わります。|
|condition|json オブジェクト|||列の値の条件のチェックを定義し、各集計のリスト ビューの項目の色を決定||
|if|string|常に、equals、notEquals、greaterThan、lessThan、greaterThanOrEqauls lessThanOrEquals||条件のチェック演算子|後で、プロパティ名が、演算子が変わります。|
|equals|string|||条件値の確認|後でこのプロパティ名が、'value' が変わります。|

## <a name="insight-actions"></a>Insight アクション
Insight ウィジェットと洞察の詳細については、問題を軽減または管理する行動計画を思い出すことができます。 たとえば、DBCC CHECKDB を実行すると考えるエラー ログを読み取る、またはデータベースは復旧待ち状態のときに、データベースを復元は。 またはを実行するアクションのいずれかであることができます。

使用して[!INCLUDE[name-sos](../includes/name-sos-short.md)]の洞察アクション構成では、復元、または sql スクリプトを使用して定義されているアクションは、独自の表示などの組み込みのアクションをマップすることができます。

> Sql スクリプトを使用してカスタムの動作の構成は、開発とことはまだはプライベート プレビューではビルドに使用できません。

## <a name="sample-insight-action-definition"></a>サンプル Insight アクションの定義

```"actions"{}```insight アクションを定義します。 アクションをなど、特定のスコープを定義できる```"server"```、```"database"```などと[!INCLUDE[name-sos](../includes/name-sos-short.md)]アクションに現在の接続コンテキスト情報を渡します。 

WideWorldImporters データベースの復元アクションが起動した場合に、```"database": "${Database}"```を渡すことを示します定義```Database```が復元アクションをクエリの結果の列の値。 データベースの復元アクションを開始します。 ```"types"```json 配列は、配列に複数のアクションを指定できます。 コンテキスト メニューを基本的になる情報の詳細 ダイアログでそのユーザーをクリックして、操作を実行します。 

> [!INCLUDE[name-sos](../includes/name-sos-short.md)]「のバックアップ」、「復元中」、「新しいクエリ」および「新しいデータベース」のアクションの種類として、プレビュー 0.17.1 が有効にします。

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
