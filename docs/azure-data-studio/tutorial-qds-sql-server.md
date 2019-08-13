---
title: チュートリアル:5 つの最低速クエリのサンプル ウィジェットを有効にする
titleSuffix: Azure Data Studio
description: このチュートリアルでは、データベース ダッシュボードで 5 つの最低速クエリ サンプル ウィジェットを有効にする方法について説明します。
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 5c94d2cf8b80ad7724cc1f710dc67d3f4a13c59e
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959067"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>チュートリアル:データベース ダッシュボードに *5 つの最低速クエリ* サンプル ウィジェットを追加する

このチュートリアルでは、[!INCLUDE[name-sos](../includes/name-sos-short.md)] に組み込まれているサンプル ウィジェットの 1 つを*データベース ダッシュボード*に追加することでデータベースの 5 つの最低速クエリを表示するプロセスについて説明します。 低速クエリの詳細を表示する方法と [!INCLUDE[name-sos](../includes/name-sos-short.md)] の機能を利用してプランにクエリを実行する方法についても説明します。 このチュートリアルでは、次の方法を学習します。

> [!div class="checklist"]
> * データベースでクエリ ストアを有効にする
> * 事前に構築された分析情報ウィジェットをデータベース ダッシュボードに追加する
> * データベースの最低速クエリに関する詳細を表示する
> * 低速クエリのクエリ実行プランを表示する

[!INCLUDE[name-sos](../includes/name-sos-short.md)] には、面倒な設定なしですぐに使える分析情報ウィジェットがいくつか含まれています。 このチュートリアルでは、*query-data-store-db-insight* ウィジェットを追加する方法を紹介しますが、手順は基本的にどのウィジェットを追加する場合でも同じです。

## <a name="prerequisites"></a>Prerequisites

このチュートリアルには、SQL Server か Azure SQL Database *TutorialDB* が必要です。 *TutorialDB* データベースを作成するには、次のクイックスタートのいずれかを実行します。

- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して SQL Server に接続し、クエリを実行する](quickstart-sql-server.md)
- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して Azure SQL Database に接続し、クエリを実行する](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>データベースのクエリ ストアをオンにする

この例のウィジェットでは、*クエリ ストア*を有効にする必要があります。

1. ( **[サーバー]** サイドバーで) **TutorialDB** データベースを右クリックし、 **[新しいクエリ]** を選択します。
2. クエリ エディターに次の Transact-SQL (T-SQL) ステートメントを貼り付けて、 **[実行]** をクリックします。

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-the-slow-queries-widget-to-your-database-dashboard"></a>低速クエリ ウィジェットをデータベース ダッシュボードに追加する

*低速クエリ ウィジェット*をダッシュボードに追加するには、 *[ユーザー設定]* ファイルの *dashboard.database.widgets* 設定を編集します。

1. **Ctrl + Shift + P** を押して *[ユーザー設定]* を開き、 *[コマンド パレット]* を開きます。
2. 検索ボックスに「*settings*」と入力し、 **[ユーザー設定:ユーザー設定を開く]** を選択します。

   ![[ユーザー設定を開く] コマンド](./media/tutorial-qds-sql-server/open-user-settings.png)

2. [設定の検索] ボックスに「*dashboard*」と入力し、**dashboard.database.widgets** を見つけます。

   ![検索設定](./media/tutorial-qds-sql-server/search-settings.png)

3. **dashboard.database.widgets** 設定をカスタマイズするには、 **[ユーザー設定]** セクション (右側の列) にある **dashboard.database.widgets** を編集する必要があります。 **[ユーザー設定]** セクションに **dashboard.database.widgets** がない場合、[デフォルト設定] 列の **dashboard.database.widgets** テキストにカーソルを合わせ、テキストの左に表示された鉛筆アイコンをクリックし、 **[設定にコピー]** をクリックします。 ポップアップに **[設定を置換]** と表示された場合、それをクリックしないでください。 右にある **[ユーザー設定]** 列に移動し、**dashboard.database.widgets** セクションを見つけ、次の手順に進みます。

4. **dashboard.database.widgets** セクションに次を追加します。

   ```json
        {
            "name": "slow queries widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "query-data-store-db-insight": null
            }
        },
    ```

1. 新しいウィジェットを追加するのが初めての場合、**dashboard.database.widgets** セクションは次のようになるはずです。

   ```json
   "dashboard.database.widgets": [
       {
           "name": "slow queries widget",
           "gridItemConfig": {
               "sizex": 2,
               "sizey": 1
           },
           "widget": {
               "query-data-store-db-insight": null
           }
       },
       {
           "name": "Tasks",
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 1
           },
           "widget": {
               "tasks-widget": {}
           }
       },
       {
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 2
           },
           "widget": {
               "explorer-widget": {}
           }
       }
   ]
   ```

1. **Ctrl + S** を押し、変更後の **[ユーザー設定]** を保存します。

6. **[サーバー]** サイドバーの **[TutorialDB]** に移動して *[データベース ダッシュボード]* を開き、右クリックして **[管理]** を選択します。

   ![ダッシュボードを開く](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. 分析情報ウィジェットがダッシュボードに表示されます。 

   ![QDS ウィジェット](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>詳細は、分析情報詳細を参照してください。

1. 分析情報ウィジェットの追加情報を表示するには、右上にある省略記号 ( **...** ) をクリックし、 **[詳細の表示]** を選択します。
2. 項目の詳細を表示するには、 **[グラフ データ]** 一覧で任意の項目を選択します。

   ![分析情報詳細ダイアログ](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. **[項目の詳細]** で **query_sql_txt** の右にあるセルを右クリックし、 **[セルのコピー]** をクリックします。

4. **[分析情報]** ウィンドウを閉じます。

## <a name="view-the-query-plan"></a>クエリ プランを表示する 

1. **Ctrl + N** を押し、新しいクエリ エディターを開きます。

2. 前の手順からのクエリ テキストをエディターに貼り付けます。

3. **[説明]** をクリックします。

   ![分析情報 QDS 説明](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. クエリの実行プランを表示します。

   ![プラン表示 (showplan)](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>クエリ プランを保存して開く 

1. 分析情報詳細ダイアログを開きます。
2. いずれかのクエリ項目を選択します。
2. **query_plan** 値を右クリックし、 **[セルのコピー]** を選択します。

   ![分析情報 QDS プラン](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. **Ctrl + N** を押し、新しいエディターを開きます。

4. コピーしたプランをエディターに貼り付けます。

5. **Ctrl + S** を押してファイルを保存し、ファイルの拡張子を *.sqlplan* に変更します。 *.sqlplan* はファイルの拡張子ドロップダウンに表示されません。直接入力してください。 このチュートリアルでは、ファイルに *slowquery.sqlplan* という名前を付けます。

6. クエリ プランが [!INCLUDE[name-sos](../includes/name-sos-short.md)] のクエリ プラン ビューアーで開きます。

   ![分析情報 QDS プラン](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>次の手順
このチュートリアルでは、次の方法を学習しました。
> [!div class="checklist"]
> * データベースでクエリ ストアを有効にする
> * 分析情報ウィジェットをデータベース ダッシュボードに追加する
> * データベースの最低速クエリに関する詳細を表示する
> * 低速クエリのクエリ実行プランを表示する


**テーブル領域使用**のサンプル分析情報を有効にする方法については、次のチュートリアルを完了してください。

> [!div class="nextstepaction"]
> [テーブル領域のサンプル分析情報ウィジェットを有効にする](tutorial-table-space-sql-server.md)
