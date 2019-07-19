---
title: データベースをバックアップおよび復元
titleSuffix: Azure Data Studio
description: Azure Data Studio を使用してデータベース バックアップおよび復元する方法について説明します
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 77679106577cd8f8374f932d8ddd22644beb63d8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959107"
---
# <a name="backup-and-restore-databases-using-includename-sosincludesname-sos-shortmd"></a>バックアップと復元を使用するデータベース [!INCLUDE[name-sos](../includes/name-sos-short.md)]

このチュートリアルでは、次の [!INCLUDE[name-sos](../includes/name-sos-short.md)] の使用方法を学習します:
> [!div class="checklist"]
> * データベースのバックアップ 
> * バックアップ状態の表示
> * バックアップを実行するためのスクリプトの生成
> * データベースの復元
> * 復元タスクの状態の表示

## <a name="prerequisites"></a>Prerequisites

のチュートリアルでは、SQL Server *TutorialDB* が必要です。 *TutorialDB*データベースを作成するには、次のクイック スタートのいずれかを完了してください。

- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して、SQL Server に接続し、クエリを実行する](quickstart-sql-server.md)

このチュートリアルでは、SQL Server データベースに接続する必要があります。 Azure SQL Database は、Azure Data Studio から Azure SQL Database のバックアップを実行して復元しないように自動バックアップ、います。 詳細については、次を参照してください。 [SQL Database 自動バックアップについての詳細情報](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups)します。

## <a name="backup-a-database"></a>データベースのバックアップ

1. TutorialDB の データベース ダッシュ ボードを開きます (**サーバー**サイドバー (**CTRL + G**) を開き、**データベース** を展開、**TutorialDB** を右クリックして、**管理** を選択します)。

2. **データベースのバックアップ** ダイアログを開きます (**タスク**ウィジェットにある **バックアップ** をクリックします)。

   ![タスクのウィジェット](./media/tutorial-backup-restore-sql-server/tasks.png)

3. このチュートリアルでは、既定のバックアップ オプションを使用します。**バックアップ** をクリックします。
   ![バックアップ ダイアログ](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

**バックアップ** をクリックした後、 **データベースのバックアップ** ダイアログが閉じられ、バックアップ プロセスを開始します。

## <a name="view-the-backup-status-and-view-the-backup-script"></a>バックアップ状態の表示とバックアップ スクリプトの表示

1. **操作バー**の時計のアイコンをクリックするか、または **CTRL + T** を押して、*タスク履歴* サイド バーを開きます。

   ![タスクの履歴](./media/tutorial-backup-restore-sql-server/task-history.png)

2. バックアップ スクリプトをエディターに表示するには、**成功したデータベースのバックアップ** を右クリックして **スクリプト** を選択します。

   ![バックアップ スクリプト](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>バックアップ ファイルからデータベースを復元


1. **サーバー** サイドバー (**CTRL + G**) を開き、対象のサーバーを右クリックし、**管理** を選択します。 

2. **データベースを復元** ダイアログを開きます (**タスク**ウィジェットの **復元** をクリックします)。

2. **Restore from** フィールドで **バックアップ ファイル** を選択します。 

3. **バックアップ ファイルのパス** フィールドの省略記号(...)をクリックして、*TutorialDB* の最新のバックアップ ファイルを選択します。

3. バックアップ ファイルから新しいデータベースを復元するために、 **Destination** セクションの **ターゲット データベース** フィールドに **TutorialDB_Restored** と入力します。

   ![復元 (restore)](./media/tutorial-backup-restore-sql-server/restore.png)

4. **復元** をクリックします。

5. 復元操作の状態を表示するには、**CTRL + T** を押して **タスク履歴** サイドバーを開きます。

   ![復元 (restore)](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


このチュートリアルでは、以下の使用方法を学習しました:
> [!div class="checklist"]
> * データベースのバックアップ 
> * バックアップ状態の表示
> * バックアップを実行するためのスクリプトの生成
> * データベースの復元
> * 復元タスクの状態の表示

