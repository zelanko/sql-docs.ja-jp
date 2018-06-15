---
title: 'チュートリアル: データベース ダッシュ ボードに *5 つの遅いクエリ* のサンプルウィジェットを追加する - SQL Operations Studio (プレビュー) |Microsoft ドキュメント'
description: このチュートリアルは、5 つ最も低速なクエリのサンプル ダッシュ ボードのウィジェット、データベースを有効にする方法を示します。
ms.custom: tools|sos
ms.date: 03/15/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cef672411019a0c4402663597382eba426c2562b
ms.sourcegitcommit: b3bb41424249de198f22d9c6d40df4996f083aa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2018
ms.locfileid: "34306451"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>チュートリアル: データベース ダッシュ ボードに *5 つの遅いクエリ* のサンプルウィジェットを追加する

このチュートリアルは、[!INCLUDE[name-sos](../includes/name-sos-short.md)] の組み込みサンプルウィジェットの 1 つを *データベース ダッシュ ボード* に追加して 5 つの低速なクエリを表示する手順を示します。 ここでは、低速なクエリの詳細と [!INCLUDE[name-sos](../includes/name-sos-short.md)] を使用したクエリ プランを表示する方法についても学ぶことができます。 このチュートリアルで学習する方法。

> [!div class="checklist"]
> * データベースでクエリ ストアを有効にします。
> * データベース ダッシュ ボードに構築済みのインサイトウィジェットを追加します。
> * データベースの遅延クエリに関する詳細を表示します。
> * 遅延クエリに対するのクエリ実行プランを表示します。

[!INCLUDE[name-sos](../includes/name-sos-short.md)] いくつか把握ウィジェットのすぐに含まれています。 このチュートリアルは、追加する方法を示します、*クエリのデータのストアの db の洞察を得る*ウィジェットが、手順は基本的に同じ任意のウィジェットを追加するためです。

## <a name="prerequisites"></a>前提条件

このチュートリアルは、SQL Server または Azure SQL データベースが必要です。 *TutorialDB*です。 作成する、 *TutorialDB*データベースで、次のクイック スタートのいずれかを行います。

- [接続してクエリを使用して SQL サーバー [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [接続してクエリを使用して Azure SQL データベース [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>データベースに対してクエリ ストアを有効に

この例では、ウィジェットが必要です*クエリのストア*を有効にします。

1. 右クリックして、 **TutorialDB**データベース (で、**サーバー**サイド バー) を選択して**新しいクエリ**です。
2. クエリ エディターで、次の TRANSACT-SQL (T-SQL) ステートメントを貼り付け、をクリックして**実行**:

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-the-slow-queries-widget-to-your-database-dashboard"></a>データベース ダッシュ ボードに速度の遅いクエリ ウィジェットを追加します。

追加する、*速度の遅いクエリ ウィジェット*ダッシュ ボードを編集、 *dashboard.database.widgets*での設定、*ユーザー設定*ファイル。

1. 開く*ユーザー設定*キーを押して**Ctrl + Shift + P**を開くには、*コマンド パレット*です。
2. 型*設定*クリックし、[検索] ボックスで**設定: ユーザー設定を開く**です。

   ![開いているユーザー設定 コマンド](./media/tutorial-qds-sql-server/open-user-settings.png)

2. 型*ダッシュ ボード*設定の検索ボックスに検索し、 **dashboard.database.widgets**です。

   ![検索の設定](./media/tutorial-qds-sql-server/search-settings.png)

3. カスタマイズする、 **dashboard.database.widgets**設定を編集する必要があります、 **dashboard.database.widgets**内のエントリ、**ユーザー設定**セクション (内の列、右側にある)。 ある場合ありません**dashboard.database.widgets**で、**ユーザー設定**セクションで、ポインターを合わせる、 **dashboard.database.widgets**のテキスト列の既定の設定 をクリックします鉛筆アイコンをクリックして、テキストの左側に表示される**設定にコピーする**です。 ポップアップとされている場合**設定で置き換える**、クリックしてしないでください。 移動して、**ユーザー設定**右側の列を検索し、 **dashboard.database.widgets**セクションと、次の手順に進みます。

4. **Dashboard.database.widgets**セクションで、次の追加。

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

1. これは、初めて新しいウィジェットを追加する場合、 **dashboard.database.widgets**セクションに次のようになります。

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

1. キーを押して**Ctrl + S** 、変更を保存する**ユーザー設定**です。

6. 開く、*データベース ダッシュ ボード*に移動して**TutorialDB**で、**サーバー**サイド バーを右クリックし、**管理**です。

   ![ダッシュ ボードを開く](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Insight ウィジェットをダッシュ ボードを表示します。 

   ![QDS ウィジェット](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>詳細については理解詳細の表示

1. Insight ウィジェットの追加情報を表示するには、省略記号ボタンをクリックして (**.**) クリックし、右上にある**詳細の表示**です。
2. 項目の詳細を表示するには、任意のアイテムを選択**グラフ データ** ボックスの一覧です。

   ![情報の詳細 ダイアログ](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. 右側にあるセルを右クリックして**query_sql_txt**で**項目の詳細** をクリック**コピー セル**です。

4. 閉じる、 **Insights**ウィンドウです。

## <a name="view-the-query-plan"></a>クエリ プランを表示します。 

1. キーを押して新しいクエリ エディターを開く**Ctrl + N**です。

2. 上記の手順からクエリ テキストをエディターに貼り付けます。

3. をクリックして**説明**です。

   ![Insight QDS の説明](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. クエリの実行プランを表示します。

   ![プラン表示 (showplan)](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>保存して、クエリ プランを開く 

1. 情報の詳細 ダイアログを開きます。
2. クエリ項目のいずれかを選択します。
2. 右クリック**query_plan**値および選択**コピー セル**

   ![Insights QDS プラン](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. キーを押して**Ctrl + N**新しいエディターを開きます。

4. コピー元の計画をエディターに貼り付けます。

5. キーを押して**Ctrl + S**ファイルを保存するファイル拡張子を変更して *.sqlplan*です。 *.sqlplan*されていません、ファイル拡張子のドロップダウン リストに表示される、ためだけに入力します。 このチュートリアルでは、ファイルに名前*slowquery.sqlplan*です。

6. クエリ プランを開きます[!INCLUDE[name-sos](../includes/name-sos-short.md)]のクエリ プランのビューアー。

   ![Insights QDS プラン](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>次の手順
このチュートリアルで学習した方法。
> [!div class="checklist"]
> * データベースでクエリ ストアを有効にします。
> * データベース ダッシュ ボードへ insight ウィジェットを追加します。
> * データベースの遅延クエリに関する詳細を表示します。
> * 遅延クエリに対するのクエリ実行プランを表示します。


有効にする方法については、**領域の使用状況の表に**インサイトをサンプルを次のチュートリアルを完了します。

> [!div class="nextstepaction"]
> [テーブル領域サンプル insight ウィジェットを有効にします。](tutorial-table-space-sql-server.md)