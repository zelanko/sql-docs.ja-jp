---
title: "チュートリアル: SQL 操作 Studio (プレビュー) のテーブル領域使用状況のサンプル insight ウィジェットを有効にする |Microsoft ドキュメント"
description: "このチュートリアルでは、SQL 操作 Studio (プレビュー) の データベース ダッシュ ボードのテーブル領域使用状況のサンプル insight ウィジェットを有効にする方法について説明します。"
ms.custom: tools|sos
ms.date: 11/15/2017
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
ms.openlocfilehash: 7c51c7d1804baa490e665d316a08d911038c9f11
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>チュートリアル: 領域使用状況サンプル insight ウィジェットを使用してテーブルを有効にします。[!INCLUDE[name-sos](../includes/name-sos-short.md)]

このチュートリアルでは、データベース内のすべてのテーブルの領域の使用状況についての概要の概観を提供する、データベースのダッシュ ボードでの洞察ウィジェットを有効にする方法について説明します。 このチュートリアルで学習する方法。

> [!div class="checklist"]
> * 組み込みの洞察ウィジェットの例を使用して把握ウィジェットですばやく切り替えるには
> * テーブルの使用領域の詳細を表示します。
> * データをフィルター処理し、洞察グラフのラベルの詳細を表示

## <a name="prerequisites"></a>Prerequisites

このチュートリアルは、SQL Server または Azure SQL データベースが必要です。 *TutorialDB*です。 作成する、 *TutorialDB*データベースで、次のクイック スタートのいずれかを行います。

- [接続してクエリを使用して SQL サーバー[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [接続してクエリを使用して Azure SQL データベース[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>管理インサイトを有効に[!INCLUDE[name-sos](../includes/name-sos-short.md)]のデータベースのダッシュ ボード
[!INCLUDE[name-sos](../includes/name-sos-short.md)]データベース内のテーブルで使用される領域を監視する組み込みサンプル ウィジェットがします。

1. 開く**ユーザー設定**キーを押して**Ctrl + Shift + P**を開くには*コマンド パレット*、型*設定*クリックし、検索ボックスで**基本設定。 ユーザー設定 を開く**です。

   ![開いているユーザー設定 コマンド](./media/tutorial-table-space-sql-server/open-user-settings.png)

2. 型*ダッシュ ボード*設定検索入力ボックスと検索**dashboard.database.widgets**です。

   ![検索の設定](./media/tutorial-table-space-sql-server/search-settings.png)

3. カスタマイズする、 **dashboard.database.widgets**の左側にある鉛筆アイコンにマウスを設定する、 **dashboard.database.widgets**テキストをクリックして**編集** > **設定にコピーする**です。

4. 使用して[!INCLUDE[name-sos](../includes/name-sos-short.md)]の洞察の設定、IntelliSense の構成*名前*ウィジェットのタイトルの*gridItemConfig*ウィジェット サイズのおよび*ウィジェット*を選択して**テーブル スペース db insight**次のスクリーン ショットに示すようにドロップ ダウン リストから。

   ![情報の設定](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. キーを押して**Ctrl + S**設定を保存します。

6. 右クリックしてダッシュ ボードを開いているデータベース**TutorialDB**  をクリック**管理**です。

   ![ダッシュ ボードを開く](./media/tutorial-table-space-sql-server/insight-open-dashboard.png)

7. ビュー*テーブルで使用される領域*次のスクリーン ショットに示すようにします。 

   ![ウィジェット](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Insight グラフの操作

[!INCLUDE[name-sos](../includes/name-sos-short.md)]洞察のグラフがフィルター処理とマウスのポイントの詳細を提供します。 次の手順を試してください。

1. をクリックし、切り替える、 *row_count*グラフの凡例をします。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]表示し、凡例は、オンまたはオフに切り替えると、データ系列を非表示にします。
    
2. グラフ上には、マウス ポインターを置きます。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]詳細については、データ系列のラベルと次のスクリーン ショットに示すように、その値を示します。

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