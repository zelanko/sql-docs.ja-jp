---
title: チュートリアル:カスタム インサイト ウィジェットをビルドします。
titleSuffix: Azure Data Studio
description: このチュートリアルでは、カスタムの洞察のウィジェットをビルドして Azure Data Studio でのデータベースとサーバーのダッシュ ボードに追加する方法について説明します。
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 4a2aee7f7ca9c61306e0241ff77a87c1c7dae112
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089731"
---
# <a name="tutorial-build-a-custom-insight-widget"></a>チュートリアル:カスタム インサイト ウィジェットをビルドします。

このチュートリアルでは、独自の分析クエリを使用して、カスタムの洞察のウィジェットを構築する方法を示します。

このチュートリアルの中に確認する方法。
> [!div class="checklist"]
> * 独自のクエリを実行し、グラフで表示
> * カスタム インサイト ウィジェット グラフからを構築します。
> * サーバーまたはデータベースのダッシュ ボードにグラフを追加します。
> * 詳細、カスタム インサイト ウィジェットを追加します。

## <a name="prerequisites"></a>Prerequisites

このチュートリアルでは、SQL Server または Azure SQL Database に *TutorialDB* が必要です。 *TutorialDB* データベースを作成するには、次のクイック スタートのいずれかを行います。

- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して、SQL Server に接続し、クエリを実行する](quickstart-sql-server.md)
- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して、Azure SQL Database に接続し、クエリを実行する](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>独自のクエリを実行し、結果をグラフ ビューで表示
この手順では、現在アクティブなセッションを照会する sql スクリプトを実行します。

1. 新しいエディターを開くには、キーを押して**Ctrl + N**します。 

2. 接続コンテキストを変更する**TutorialDB**します。

3. クエリ エディターには、次のクエリを貼り付けます。

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. エディターでクエリを保存、 \*.sql ファイル。 このチュートリアルでは、スクリプトとして保存*activeSession.sql*します。

5. クエリを実行するキーを押して**F5**します。

6. クエリの結果が表示されたら、クリックして**グラフとして表示**、 をクリックし、**グラフ ビューアー**  タブ。

7. 変更**グラフの種類**に**カウント**します。 これらの設定は、カウントのグラフを表示します。

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>データベース ダッシュ ボードにカスタム インサイトを追加します。

1. Insight ウィジェットの構成を開くには、*グラフ ビューアー* で **作成洞察** をクリックします:

   ![構成](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. インサイトの構成 (JSON データ) をコピーします。 

3. キーを押して**Ctrl + コンマ**を開く*ユーザー設定*します。

4. 型*ダッシュ ボード*で*検索設定*します。

5. クリックして**編集**の*dashboard.database.widgets*します。

   ![ダッシュ ボードの設定](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. インサイトの構成 JSON を貼り付けますに*dashboard.database.widgets*します。 ダッシュ ボードの設定が、次のようにデータベースします。

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

7. 保存、*ユーザー設定*ファイルを探して開きます、 *TutorialDB*データベースのダッシュ ボードは、アクティブなセッションのウィジェットを参照してください。

   ![activesession insight](./media/tutorial-build-custom-insight-sql-server/insight-activesession-dashboard.png)

## <a name="add-details-to-custom-insight"></a>詳細カスタム インサイトを追加します。

1. 新しいエディターを開くには、キーを押して**Ctrl + N**します。

2. 接続コンテキストを変更する**TutorialDB**します。

3. クエリ エディターには、次のクエリを貼り付けます。

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. エディターでクエリを保存、 \*.sql ファイル。 このチュートリアルでは、スクリプトとして保存*activeSessionDetail.sql*します。

5. キーを押して**Ctrl + コンマ**を開く*ユーザー設定*します。

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

7. 保存、*ユーザー設定*ファイルを探して開きます、 *TutorialDB*データベース ダッシュ ボード。 次に省略記号 (...) ボタンをクリックして*マイ ウィジェット*詳細を表示します。

    ![activesession insight](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>次の手順
このチュートリアルでは、以下の使用方法を学習しました:
> [!div class="checklist"]
> * 独自のクエリを実行し、グラフで表示
> * カスタム インサイト ウィジェット グラフからを構築します。
> * サーバーまたはデータベースのダッシュ ボードにグラフを追加します。
> * 詳細、カスタム インサイト ウィジェットを追加します。

バックアップおよびデータベースを復元する方法については、するには、次のチュートリアルを行います。

> [!div class="nextstepaction"]
> [バックアップおよびデータベースを復元](tutorial-backup-restore-sql-server.md)します。
