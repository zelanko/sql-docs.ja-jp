---
title: 'チュートリアル: SQL Operations Studio (preview) でカスタム インサイト ウィジェットの構築 |Microsoft ドキュメント'
description: このチュートリアルでは、カスタム インサイト ウィジェットを構築し、SQL Operations Studio (preview) でのデータベースとサーバーのダッシュ ボードに追加する方法を示します。
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 344cf021a4a0abc13fc8c531875c604095c8c0d1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-build-a-custom-insight-widget"></a>チュートリアル: カスタム インサイト ウィジェットを構築します。

このチュートリアルでは、独自の洞察クエリを使用してカスタム インサイト ウィジェットを構築する方法について説明します。

このチュートリアルで学習する方法。
> [!div class="checklist"]
> * 独自のクエリを実行し、グラフの表示
> * グラフからカスタム インサイト ウィジェットをビルドします。
> * サーバーまたはデータベースのダッシュ ボードにグラフを追加します。
> * 詳細、カスタム インサイト ウィジェットを追加します。

## <a name="prerequisites"></a>Prerequisites

このチュートリアルは、SQL Server または Azure SQL データベースが必要です。 *TutorialDB*です。 作成する、 *TutorialDB*データベースで、次のクイック スタートのいずれかを行います。

- [接続してクエリを使用して SQL サーバー[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [接続してクエリを使用して Azure SQL データベース[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>独自のクエリを実行し、結果をグラフ ビューで表示
このステップでは、現在アクティブなセッションを照会する sql スクリプトを実行します。

1. 新しいエディターを開くには、キーを押して**Ctrl + N**です。 

2. 接続コンテキストを変更する**TutorialDB**です。

3. 次のクエリをクエリ エディターに貼り付けます。

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. エディターでクエリを保存、 \*.sql ファイル。 このチュートリアルでは、としてスクリプトを保存する*activeSession.sql*です。

5. クエリを実行するキーを押して**f5 キーを押して**です。

6. クエリの結果が表示されたら、クリックして**ビューをグラフとして**、をクリックして、**グラフ ビューアー**タブです。

7. 変更**グラフの種類**に**カウント**です。 これらの設定は、カウントのグラフを表示します。

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>データベース ダッシュ ボードにカスタム インサイトを追加します。

1. Insight ウィジェットの構成を開くをクリックして**作成洞察**で*グラフ ビューアー*:

   ![構成](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. インサイトの構成 (JSON データ) をコピーします。 

3. キーを押して**Ctrl + コンマ**を開くには*ユーザー設定*です。

4. 型*ダッシュ ボード*で*検索設定*です。

5. をクリックして**編集**の*dashboard.database.widgets*です。

   ![ダッシュ ボードの設定](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. インサイト構成 JSON を貼り付けるに*dashboard.database.widgets*です。 データベース ダッシュ ボードは、次のようの外観を設定:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
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
            }
        }
    ]
   ```

7. 保存、*ユーザー設定*ファイルから開き、 *TutorialDB*データベースのダッシュ ボードは、アクティブなセッション ウィジェットを参照してください。

   ![activesession insight](./media/tutorial-build-custom-insight-sql-server/insight-activesession-dashboard.png)

## <a name="add-details-to-custom-insight"></a>カスタムの洞察に詳細を追加します。

1. 新しいエディターを開くには、キーを押して**Ctrl + N**です。

2. 接続コンテキストを変更する**TutorialDB**です。

3. 次のクエリをクエリ エディターに貼り付けます。

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. エディターでクエリを保存、 \*.sql ファイル。 このチュートリアルでは、としてスクリプトを保存する*activeSessionDetail.sql*です。

5. キーを押して**Ctrl + コンマ**を開くには*ユーザー設定*です。

6. 既存の編集*dashboard.database.widgets*設定ファイル内のノード。

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql",
                    "details": {
                        "queryFile": "{your file folder}/activeSessionDetail.sql",
                        "label": "SID",
                        "value": "Login Name"
                    }
                }
            }
        }
    ]
   ```

7. 保存、*ユーザー設定*ファイルから開き、 *TutorialDB*データベース ダッシュ ボード。 次に、省略記号 (...) ボタンをクリックして*マイ ウィジェット*詳細を表示します。

    ![activesession insight](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>次の手順
このチュートリアルで学習した方法。
> [!div class="checklist"]
> * 独自のクエリを実行し、グラフの表示
> * グラフからカスタム インサイト ウィジェットをビルドします。
> * サーバーまたはデータベースのダッシュ ボードにグラフを追加します。
> * 詳細、カスタム インサイト ウィジェットを追加します。

バックアップおよびデータベースを復元する方法については、するには、次のチュートリアルを行います。

> [!div class="nextstepaction"]
> [バックアップおよびデータベースを復元](tutorial-backup-restore-sql-server.md)です。