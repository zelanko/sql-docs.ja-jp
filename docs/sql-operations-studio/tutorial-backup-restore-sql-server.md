---
title: SQL Operations Studio (プレビュー) を使用したバックアップの取得と復元 |Microsoft ドキュメント
description: SQL Operations Studio (プレビュー) を使用してデータベースのバックアップおよび復元方法を学習します
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
ms.openlocfilehash: df4eca076f18ce5b75a36d05c8ee26965d6a3bae
ms.sourcegitcommit: b3bb41424249de198f22d9c6d40df4996f083aa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2018
---
# <a name="backup-and-restore-using-includename-sosincludesname-sos-shortmd"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] を使用したバックアップの取得と復元

このチュートリアルでは、次の [!INCLUDE[name-sos](../includes/name-sos-short.md)] の使用方法を学習します:
> [!div class="checklist"]
> * データベースのバックアップ 
> * バックアップ状態の表示
> * バックアップを実行するためのスクリプトの生成
> * データベースの復元
> * 復元タスクの状態の表示

## <a name="prerequisites"></a>Prerequisites

このチュートリアルでは、SQL Server *TutorialDB* が必要です。 *TutorialDB* データベースを作成するには、次のクイック スタートのいずれかを完了してください。

- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して SQL サーバーに接続し、クエリを問い合わせる](quickstart-sql-server.md)


## <a name="backup-a-database"></a>データベースのバックアップ

1. TutorialDB の データベース ダッシュ ボードを開きます (**サーバー** サイドバー (**CTRL + G**) を開き、**データベース** を展開、**TutorialDB** を右クリックして、**管理** を選択します)。

2. **データベースのバックアップ** ダイアログを開きます (**タスク**ウィジェットにある **バックアップ** をクリックします)。

   ![タスクのウィジェット](./media/tutorial-backup-restore-sql-server/tasks.png)

3. このチュートリアルでは、既定のバックアップ オプションを使用します。**バックアップ** をクリックします。
   ![バックアップ ダイアログ](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

**バックアップ** をクリックした後、 **データベースのバックアップ** ダイアログが閉じられ、バックアップ プロセスを開始します。

## <a name="view-the-backup-status-and-view-the-backup-script"></a>バックアップ状態の表示とバックアップ スクリプトの表示

1. *操作バー* の時計のアイコンをクリックするか、または **CTRL + T** を押して、**タスク履歴** サイド バーを開きます。

   ![タスクの履歴](./media/tutorial-backup-restore-sql-server/task-history.png)

2. バックアップ スクリプトをエディターに表示するには、**成功したデータベースのバックアップ** を右クリックして **スクリプト** を選択します。

   ![バックアップ スクリプト](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>バックアップ ファイルからデータベースを復元


1. **サーバー** サイドバー (**CTRL + G**) を開き、対象のサーバーを右クリックし、**管理** を選択します。

2. **データベースを復元** ダイアログを開きます (**タスク**ウィジェットの **復元** をクリックします)。

3. **Restore from** フィールドで **バックアップ ファイル** を選択します。

4. **バックアップ ファイルのパス** フィールドの省略記号(...)をクリックして、*TutorialDB* の最新のバックアップ ファイルを選択します。

5. バックアップ ファイルから新しいデータベースを復元するために、 **Destination** セクションの **ターゲット データベース** フィールドに **TutorialDB_Restored** と入力します。

   ![復元 (restore)](./media/tutorial-backup-restore-sql-server/restore.png)

6. **復元** をクリックします。

7. 復元操作の状態を表示するには、**CTRL + T** を押して **タスク履歴** サイドバーを開きます。

   ![復元 (restore)](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


このチュートリアルでは、以下の使用方法を学習しました:
> [!div class="checklist"]
> * データベースのバックアップ 
> * バックアップ状態の表示
> * バックアップを実行するためのスクリプトの生成
> * データベースの復元
> * 復元タスクの状態の表示

