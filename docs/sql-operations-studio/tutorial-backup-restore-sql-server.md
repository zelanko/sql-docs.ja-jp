---
title: SQL 操作 Studio (プレビュー) を使用してデータベース バックアップおよび復元 |Microsoft ドキュメント
description: SQL 操作 Studio (プレビュー) を使用してデータベース バックアップおよび復元する方法をについてください。
ms.custom: tools|sos
ms.date: 11/15/2017
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
ms.openlocfilehash: 22a453caa9d29432381da6861a0f0c4e3e61d77e
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582454"
---
# <a name="backup-and-restore-using-includename-sosincludesname-sos-shortmd"></a>バックアップと復元を使用して [!INCLUDE[name-sos](../includes/name-sos-short.md)]

このチュートリアルでは、以下の操作を [!INCLUDE[name-sos](../includes/name-sos-short.md)] で行う方法を示しています:
> [!div class="checklist"]
> * データベースのバックアップ 
> * バックアップの状態を表示します。
> * バックアップを実行するためのスクリプトを生成します。
> * データベースを復元します。
> * 復元タスクの状態を表示します。

## <a name="prerequisites"></a>Prerequisites

このチュートリアルには、SQL Server が必要です。 *TutorialDB*です。 作成する、 *TutorialDB*データベースで、次のクイック スタートのいずれかを行います。

- [接続してクエリを使用して SQL サーバー [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)


## <a name="backup-a-database"></a>データベースのバックアップ

1. TutorialDB データベース ダッシュ ボードを開きます (開いて、**サーバー**サイドバー (**CTRL + G**)、展開**データベース**を右クリックして**TutorialDB**、選択と**管理**)。 

2. 開いている、**データベースのバックアップ**ダイアログ (をクリックして**バックアップ**上、**タスク**ウィジェット)。

   ![タスクのウィジェット](./media/tutorial-backup-restore-sql-server/tasks.png)

3. このチュートリアルは、既定のバックアップ オプションを使用して、クリックして**バックアップ**です。
   ![バックアップ ダイアログ](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

クリックした後**バックアップ**、 **Backup database**ダイアログは表示されなくなり、バックアップ プロセスを開始します。

## <a name="view-the-backup-status-and-view-the-backup-script"></a>バックアップの状態を表示し、バックアップ スクリプトの表示

1. 開く、**タスク履歴**サイド バーで時計のアイコンをクリックして、*操作バー*またはキーを押して**CTRL + T**です。

   ![タスクの履歴](./media/tutorial-backup-restore-sql-server/task-history.png)

2. 表示するには、バックアップ スクリプト エディター内を右クリックして**が成功したバックアップのデータベース**選択**スクリプト**です。

   ![バックアップ スクリプト](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>バックアップ ファイルからデータベースを復元します。


1. 開く、**サーバー**サイドバー (**CTRL + G**) をサーバーを右クリックし、**管理**です。 

2. 開いている、**データベースを復元**ダイアログ (をクリックして**復元**上、**タスク**ウィジェット)。

2. 選択**バックアップ ファイル**で、**から復元**フィールドです。 

3. 内の省略記号 (...) をクリックして、**バックアップ ファイルのパス**フィールド、および最新のバックアップ ファイルを選択して*TutorialDB*です。

3. 型**TutorialDB_Restored**で、**ターゲット データベース**フィールドに、**先**セクションに新しいデータベースをバックアップ ファイルを復元します。

   ![復元 (restore)](./media/tutorial-backup-restore-sql-server/restore.png)

4. をクリックして**復元**

5. 復元操作のステータスを表示するキーを押して**CTRL + T**を開くには、**タスク履歴**サイドバーです。

   ![復元 (restore)](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


このチュートリアルで学習した方法。
> [!div class="checklist"]
> * データベースのバックアップ 
> * バックアップの状態を表示します。
> * バックアップを実行するためのスクリプトを生成します。
> * データベースを復元します。
> * 復元タスクの状態を表示します。

