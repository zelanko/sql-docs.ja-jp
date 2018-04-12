---
title: 'チュートリアル: SQL Operations Studio (preview) のテーブル領域使用状況のサンプル insight ウィジェットを有効にする |Microsoft ドキュメント'
description: このチュートリアルでは、SQL Operations Studio (preview) の データベース ダッシュ ボードのテーブル領域使用状況のサンプル insight ウィジェットを有効にする方法について説明します。
ms.custom: tools|sos
ms.date: 03/19/2018
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
ms.openlocfilehash: 09a1ebe6fda1baf546923887f28b51d416a80b59
ms.sourcegitcommit: 6bd21109abedf64445bdb3478eea5aaa7553fa46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2018
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>チュートリアル: 領域使用状況サンプル insight ウィジェットを使用してテーブルを有効にします。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

このチュートリアルでは、データベース内のすべてのテーブルの領域の使用状況についての概要の概観を提供する、データベースのダッシュ ボードでの洞察ウィジェットを有効にする方法について説明します。 このチュートリアルで学習する方法。

> [!div class="checklist"]
> * 組み込みの洞察ウィジェットの例を使用して把握ウィジェットですばやく切り替えるには
> * テーブルの使用領域の詳細を表示します。
> * データをフィルター処理し、洞察グラフのラベルの詳細を表示

## <a name="prerequisites"></a>前提条件

このチュートリアルは、SQL Server または Azure SQL データベースが必要です。 *TutorialDB*です。 作成する、 *TutorialDB*データベースで、次のクイック スタートのいずれかを行います。

- [接続してクエリを使用して SQL サーバー [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [接続してクエリを使用して Azure SQL データベース [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>管理インサイトを有効に[!INCLUDE[name-sos](../includes/name-sos-short.md)]のデータベースのダッシュ ボード
[!INCLUDE[name-sos](../includes/name-sos-short.md)] データベース内のテーブルで使用される領域を監視する組み込みサンプル ウィジェットがします。

1. 開く*ユーザー設定*キーを押して**Ctrl + Shift + P**を開くには、*コマンド パレット*です。
2. 型*設定*クリックし、[検索] ボックスで**設定: ユーザー設定を開く**です。
2. 型*ダッシュ ボード*設定検索入力ボックスと検索**dashboard.database.widgets**です。

3. カスタマイズする、 **dashboard.database.widgets**設定を編集する必要があります、 **dashboard.database.widgets**内のエントリ、**ユーザー設定**セクション (内の列、右側にある)。 ある場合ありません**dashboard.database.widgets**で、**ユーザー設定**セクションで、ポインターを合わせる、 **dashboard.database.widgets**のテキスト列の既定の設定 をクリックします鉛筆アイコンをクリックして、テキストの左側に表示される**設定にコピーする**です。 ポップアップとされている場合**設定で置き換える**、クリックしてしないでください。 移動して、**ユーザー設定**右側の列を検索し、 **dashboard.database.widgets**セクションと、次の手順に進みます。

4. **Dashboard.database.widgets**セクションで、次の追加。

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
**Dashboard.database.widgets**セクションに次の画像のようになります。

   ![検索の設定](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. キーを押して**Ctrl + S**設定を保存します。

6. 右クリックしてダッシュ ボードを開いているデータベース**TutorialDB**  をクリック**管理**です。

7. ビュー、*テーブル スペース*insight ウィジェット、次の図に示すように。 

   ![ウィジェット](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Insight グラフの操作

[!INCLUDE[name-sos](../includes/name-sos-short.md)]洞察のグラフがフィルター処理とマウスのポイントの詳細を提供します。 次の手順を試してください。

1. をクリックし、切り替える、 *row_count*グラフの凡例をします。 [!INCLUDE[name-sos](../includes/name-sos-short.md)] 表示し、凡例は、オンまたはオフに切り替えると、データ系列を非表示にします。
    
2. グラフ上には、マウス ポインターを置きます。 [!INCLUDE[name-sos](../includes/name-sos-short.md)] 詳細については、データ系列のラベルと次のスクリーン ショットに示すように、その値を示します。

   ![グラフの表示/非表示、および凡例](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>次の手順
このチュートリアルで学習した方法。
> [!div class="checklist"]
> * すばやく組み込み insight ウィジェット サンプルを使用して把握ウィジェットをオンにします。
> * テーブルの使用領域の詳細を表示します。
> * データをフィルター処理し、洞察グラフのラベルの詳細を表示

カスタム インサイト ウィジェットを構築する方法については、するには、次のチュートリアルを行います。

> [!div class="nextstepaction"]
> [カスタム インサイト ウィジェットを構築](tutorial-build-custom-insight-sql-server.md)です。