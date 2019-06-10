---
title: チュートリアル:テーブル領域使用状況のサンプル insight ウィジェットを有効にします。
titleSuffix: Azure Data Studio
description: このチュートリアルでは、Azure Data Studio データベース ダッシュ ボードのテーブル領域使用状況のサンプル insight ウィジェットを有効にする方法について説明します。
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 9fb9fd0c1c498c330b92b71d00b2c9f33667056c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773661"
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>チュートリアル:テーブル領域使用状況分析ウィジェットを使用する例を有効にします。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

このチュートリアルでは、データベース内のすべてのテーブルの領域の使用状況についての概要ビューを提供すること、データベースのダッシュ ボード、洞察のウィジェットを有効にする方法について説明します。 このチュートリアルでは、中に確認する方法。

> [!div class="checklist"]
> * 組み込みの洞察のウィジェットの使用例を使用して、洞察のウィジェットですばやく切り替えるには
> * テーブルの使用領域の詳細を表示します。
> * データをフィルター処理し、分析グラフのラベルの詳細を表示

## <a name="prerequisites"></a>前提条件

このチュートリアルでは、SQL Server または Azure SQL Database に *TutorialDB* が必要です。 *TutorialDB* データベースを作成するには、次のクイック スタートのいずれかを行います。

- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して、SQL Server に接続し、クエリを実行する](quickstart-sql-server.md)
- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して、Azure SQL Database に接続し、クエリを実行する](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>マネジメント インサイトを有効にする[!INCLUDE[name-sos](../includes/name-sos-short.md)]のデータベースのダッシュ ボード
[!INCLUDE[name-sos](../includes/name-sos-short.md)] データベース内のテーブルで使用される領域を監視するための組み込みのサンプルのウィジェットがあり。

1. 開く*ユーザー設定*キーを押して**Ctrl + Shift + P**を開く、*コマンド パレット*します。
2. 型*設定*検索ボックスを選び**設定。ユーザー設定を開く**します。
2. 型*ダッシュ ボード*設定検索入力ボックス探し**dashboard.database.widgets**します。

3. カスタマイズする、 **dashboard.database.widgets**設定を編集する必要がある、 **dashboard.database.widgets**内のエントリ、**ユーザー設定**セクション (列に、右側にある)。 存在する場合ありません**dashboard.database.widgets**で、**ユーザー設定**セクションで、マウス、 **dashboard.database.widgets**テキスト列の既定の設定をクリックします鉛筆アイコンをクリックして、テキストの左側に表示される**設定にコピーする**します。 ポップアップがの場合は**設定を指定して置換**、クリックしてしないでください。 移動、**ユーザー設定**右に列を探し、 **dashboard.database.widgets**セクションと、次の手順に進みます。

4. **Dashboard.database.widgets**セクションで、以下を追加します。

   ```json
        {
            "name": "Space Used by Tables",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "table-space-db-insight": null
            }
        },
    ```
**Dashboard.database.widgets**セクションに次の図のようになります。

   ![検索の設定](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. キーを押して**Ctrl + S**設定を保存します。

6. 右クリックしてダッシュ ボードを開いているデータベース**TutorialDB**クリック**管理**します。

7. ビュー、*テーブル スペース*insight ウィジェットの次の図のようにします。 

   ![ウィジェット](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Insight グラフの操作

[!INCLUDE[name-sos](../includes/name-sos-short.md)]分析情報のグラフがフィルター処理とマウスのポイントの詳細を提供します。 次の手順を試すには。

1. をクリックし、切り替える、 *row_count*グラフの凡例をします。 [!INCLUDE[name-sos](../includes/name-sos-short.md)] 表示し、凡例は、オンまたはオフに切り替えると、データ系列を非表示にします。
    
2. グラフの上にマウス ポインターを移動します。 [!INCLUDE[name-sos](../includes/name-sos-short.md)] データ系列のラベルと次のスクリーン ショットに示すように、その値に関する情報が表示されます。

   ![グラフの切り替え、凡例](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>次の手順
このチュートリアルでは、以下の使用方法を学習しました:
> [!div class="checklist"]
> * 組み込み insight ウィジェットのサンプルを使用して、insight ウィジェットすばやく有効にします。
> * テーブルの使用領域の詳細を表示します。
> * データをフィルター処理し、分析グラフのラベルの詳細を表示

カスタム インサイト ウィジェットを構築する方法については、次のチュートリアルを行います。

> [!div class="nextstepaction"]
> [カスタム インサイト ウィジェットをビルド](tutorial-build-custom-insight-sql-server.md)します。
