---
title: "チュートリアル: 5 つを有効にする速度が遅かったクエリ サンプル ウィジェット - SQL 操作 Studio (プレビュー) |Microsoft ドキュメント"
description: "このチュートリアルは、5 つ最も低速なクエリのサンプル ダッシュ ボードのウィジェット、データベースを有効にする方法を示します。"
ms.custom: tools|sos
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fc30051dff2bef07ac3e7d06aa98d92d4e05e79e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>チュートリアル: 追加、 *5 速度が遅かったクエリ*データベース ダッシュ ボードにウィジェットをサンプル

このチュートリアルは、のいずれかの追加の手順を示します[!INCLUDE[name-sos](../includes/name-sos-short.md)]の組み込みサンプルするウィジェットを*データベース ダッシュ ボード*をすぐに、データベースの 5 つの最も低速なクエリを表示します。 低速のクエリの詳細を表示する方法についても説明し、クエリ プランを使用して[!INCLUDE[name-sos](../includes/name-sos-short.md)]の機能です。 このチュートリアルで学習する方法。

> [!div class="checklist"]
> * データベースでクエリ ストアを有効にします。
> * データベース ダッシュ ボードに構築済みの洞察のウィジェットを追加します。
> * データベースの速度が遅かったクエリに関する詳細を表示
> * 低速のクエリのクエリ実行プランを表示します。

[!INCLUDE[name-sos](../includes/name-sos-short.md)]いくつか把握ウィジェットのすぐに含まれています。 このチュートリアルは、追加する方法を示します、*クエリのデータのストアの db の洞察を得る*ウィジェットが、手順は基本的に同じ任意のウィジェットを追加するためです。

## <a name="prerequisites"></a>Prerequisites

このチュートリアルは、SQL Server または Azure SQL データベースが必要です。 *TutorialDB*です。 作成する、 *TutorialDB*データベースで、次のクイック スタートのいずれかを行います。

- [接続してクエリを使用して SQL サーバー[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [接続してクエリを使用して Azure SQL データベース[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>データベースに対してクエリ ストアを有効に

この例では、ウィジェットが必要です*クエリのストア*データベースに対して次実行のための TRANSACT-SQL (T-SQL) ステートメントを有効にします。

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-an-insight-widget-to-your-database-dashboard"></a>データベース ダッシュ ボードに insight ウィジェットを追加します。

Insight ウィジェットをダッシュ ボードに追加するには、編集、 *dashboard.database.widgets*での設定、*ユーザー設定*ファイル。

1. 開く*ユーザー設定*キーを押して**Ctrl + Shift + P**を開くには、*コマンド パレット*です。
2. 型*設定*検索ボックスに、使用可能な設定ファイルから を選択**設定: ユーザー設定を開く**です。

   ![開いているユーザー設定 コマンド](./media/tutorial-qds-sql-server/open-user-settings.png)

2. 型*ダッシュ ボード*設定の検索ボックスに検索し、 **dashboard.database.widgets**です。

   ![検索の設定](./media/tutorial-qds-sql-server/search-settings.png)

3. カスタマイズする、 **dashboard.database.widgets**の左側にある鉛筆アイコンにマウスを設定する、 **dashboard.database.widgets**テキストをクリックして**編集** > **設定にコピーする**です。

4. 設定をコピーした後**dashboard.database.widgets**、キーを押して、角かっこの後に、行の末尾にカーソルを置きます**Enter**次のように、中かっこを追加し、(右中かっこ自動的に表示されます)。

   ```json
   "dashboard.database.widgets": [
   {}
   ```
5. 中かっこにカーソルを合わせ、キーを押して**Ctrl + Space**選択と**名前**です。 
6. ウィジェットの設定が完了したら、次のように表示されます。

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
        }
    ...
    ```

5. キーを押して**Ctrl + S** 、変更を保存する**ユーザー設定**です。

6. 開く、*データベース ダッシュ ボード*に移動して**TutorialDB**で、*サーバー*サイド バーを右クリックし、**管理**です。

   ![ダッシュ ボードを開く](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Insight ウィジェットをダッシュ ボードを表示します。 

   ![QDS ウィジェット](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>詳細については理解詳細の表示

1. Insight ウィジェットの追加情報を表示するには、省略記号ボタンをクリックして (**.**) クリックし、右上にある**詳細の表示**です。
2. 項目の詳細を表示するには、任意のアイテムを選択**グラフ データ** ボックスの一覧です。

   ![情報の詳細 ダイアログ](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. 右クリック**query_sql_txt**で**項目の詳細** をクリック**コピー セル**です。

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

5. キーを押して**Ctrl + S**ファイルを保存するファイル拡張子を変更して*.sqlplan*です。 このチュートリアルでは、ファイルに名前*slowquery.sqlplan*です。

6. クエリ プランを開きます[!INCLUDE[name-sos](../includes/name-sos-short.md)]のクエリ プランのビューアー。

   ![Insights QDS プラン](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>次の手順
このチュートリアルで学習した方法。
> [!div class="checklist"]
> * データベースでクエリ ストアを有効にします。
> * データベース ダッシュ ボードへ insight ウィジェットを追加します。
> * データベースの速度が遅かったクエリに関する詳細を表示
> * 低速のクエリのクエリ実行プランを表示します。


有効にする方法については、**領域の使用状況の表に**インサイトをサンプルを次のチュートリアルを完了します。

> [!div class="nextstepaction"]
> [テーブル領域サンプル insight ウィジェットを有効にします。](tutorial-table-space-sql-server.md)