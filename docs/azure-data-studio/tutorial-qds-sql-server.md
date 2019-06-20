---
title: チュートリアル:5 つの最も低速なクエリ サンプルのウィジェットを有効にします。
titleSuffix: Azure Data Studio
description: このチュートリアルでは、データベースのダッシュ ボードで最も低速なクエリ サンプルの 5 つウィジェットを有効にする方法について説明します。
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 10795ae2e1836e018e103a51cb7bea718ec9299f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66797933"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>チュートリアル:追加、 *5 つの最も低速なクエリ*データベース ダッシュ ボードにサンプルのウィジェット

このチュートリアルは、[!INCLUDE[name-sos](../includes/name-sos-short.md)] の組み込みサンプルウィジェットの 1 つを *データベース ダッシュ ボード* に追加して 5 つの低速なクエリを表示する手順を示します。 ここでは、低速なクエリの詳細と [!INCLUDE[name-sos](../includes/name-sos-short.md)] を使用したクエリ プランを表示する方法についても学ぶことができます。 このチュートリアルでは、中に確認する方法。

> [!div class="checklist"]
> * データベースでクエリ ストアを有効にします。
> * データベース ダッシュ ボードに構築済みのインサイトウィジェットを追加します。
> * データベースの遅延クエリに関する詳細を表示します。
> * 遅延クエリに対するのクエリ実行プランを表示します。

[!INCLUDE[name-sos](../includes/name-sos-short.md)] いくつかインサイト ウィジェット-、-インボックスが含まれています。 このチュートリアルで追加する方法、*クエリ-データのストアの db-insight*ウィジェットでは、手順は基本的に同じ任意のウィジェットを追加するためです。

## <a name="prerequisites"></a>前提条件

このチュートリアルでは、SQL Server または Azure SQL Database に *TutorialDB* が必要です。 *TutorialDB* データベースを作成するには、次のクイック スタートのいずれかを行います。

- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して、SQL Server に接続し、クエリを実行する](quickstart-sql-server.md)
- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して、Azure SQL Database に接続し、クエリを実行する](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>データベースのクエリ ストアで有効にします。

この例では、ウィジェットが必要です*クエリ ストア*を有効にします。

1. 右クリックして、 **TutorialDB**データベース (で、**サーバー**サイドバー) を選択して**新しいクエリ**します。
2. クエリ エディターで、次の TRANSACT-SQL (T-SQL) ステートメントを貼り付けて、をクリックして**実行**:

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-the-slow-queries-widget-to-your-database-dashboard"></a>データベース ダッシュ ボードに速度の遅いクエリ ウィジェットを追加します。

追加する、*速度の遅いクエリ ウィジェット*ダッシュ ボードには、編集、 *dashboard.database.widgets*で設定、*ユーザー設定*ファイル。

1. 開く*ユーザー設定*キーを押して**Ctrl + Shift + P**を開く、*コマンド パレット*します。
2. 型*設定*検索ボックスを選び**設定。ユーザー設定を開く**します。

   ![開いているユーザー設定 コマンド](./media/tutorial-qds-sql-server/open-user-settings.png)

2. 型*ダッシュ ボード*設定の検索ボックス**dashboard.database.widgets**します。

   ![検索の設定](./media/tutorial-qds-sql-server/search-settings.png)

3. カスタマイズする、 **dashboard.database.widgets**設定を編集する必要がある、 **dashboard.database.widgets**内のエントリ、**ユーザー設定**セクション (列に、右側にある)。 存在する場合ありません**dashboard.database.widgets**で、**ユーザー設定**セクションで、マウス、 **dashboard.database.widgets**テキスト列の既定の設定をクリックします鉛筆アイコンをクリックして、テキストの左側に表示される**設定にコピーする**します。 ポップアップがの場合は**設定を指定して置換**、クリックしてしないでください。 移動、**ユーザー設定**右に列を探し、 **dashboard.database.widgets**セクションと、次の手順に進みます。

4. **Dashboard.database.widgets**セクションで、以下を追加します。

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

1. これは、最初に、新しいウィジェットを追加する場合、 **dashboard.database.widgets**セクションに次のようになります。

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

1. キーを押して**Ctrl + S** 、変更を保存する**ユーザー設定**します。

6. 開く、*データベース ダッシュ ボード*に移動して**TutorialDB**で、**サーバー**サイド バーを右クリックし、**管理**します。

   ![ダッシュ ボードを開く](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. 洞察のウィジェットをダッシュ ボードが表示されます。 

   ![QDS ウィジェット](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>詳細については把握詳細の表示

1. 洞察のウィジェットの追加情報を表示する、省略記号ボタンをクリックします ( **...** ) クリックし、右上にある**詳細の表示**します。
2. 項目の詳細を表示するには、任意の項目を選択します。**グラフ データ**一覧。

   ![インサイトの詳細 ダイアログ](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. 右側にあるセルを右クリックして**query_sql_txt**で**項目の詳細**クリック**コピー セル**。

4. 閉じる、 **Insights**ウィンドウ。

## <a name="view-the-query-plan"></a>クエリ プランを表示します。 

1. キーを押して、新しいクエリ エディターを開く**Ctrl + N**します。

2. 前の手順からクエリ テキストをエディターに貼り付けます。

3. クリックして**説明**します。

   ![Insight QDS について説明します](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. クエリの実行プランを表示するには。

   ![プラン表示 (showplan)](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>保存およびクエリ プランを開く 

1. インサイトの詳細 ダイアログを開きます。
2. クエリ項目のいずれかを選択します。
2. 右クリックして**query_plan**値し、選択**コピー セル**

   ![Insights QDS プラン](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. キーを押して**Ctrl + N**新しいエディターを開きます。

4. コピー元の計画をエディターに貼り付けます。

5. キーを押して**Ctrl + S**ファイルを保存するファイル拡張子を変更して *.sqlplan*します。 *.sqlplan*見当たらない場合はファイル拡張子のドロップダウン リストに、ただで入力します。 このチュートリアルでは、ファイルに名前*slowquery.sqlplan*します。

6. クエリ プランを開きます[!INCLUDE[name-sos](../includes/name-sos-short.md)]のクエリ プランのビューアー。

   ![Insights QDS プラン](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>次の手順
このチュートリアルでは、以下の使用方法を学習しました:
> [!div class="checklist"]
> * データベースでクエリ ストアを有効にします。
> * データベース ダッシュ ボードに insight ウィジェットを追加します。
> * データベースの遅延クエリに関する詳細を表示します。
> * 遅延クエリに対するのクエリ実行プランを表示します。


有効にする方法については、**テーブル領域使用状況**インサイトをサンプルを次のチュートリアルを完了します。

> [!div class="nextstepaction"]
> [テーブル領域サンプル洞察のウィジェットを有効にします。](tutorial-table-space-sql-server.md)
