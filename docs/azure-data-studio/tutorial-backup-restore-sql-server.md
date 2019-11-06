---
title: データベースをバックアップし、復元する
titleSuffix: Azure Data Studio
description: Azure Data Studio を使用してデータベースをバックアップし、復元する方法について説明します。
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 77679106577cd8f8374f932d8ddd22644beb63d8
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959107"
---
# <a name="backup-and-restore-databases-using-includename-sosincludesname-sos-shortmd"></a>[!INCLUDE[name-sos](../includes/name-sos-short.md)] を使用してデータベースをバックアップし、復元する

このチュートリアルでは、次の目的で [!INCLUDE[name-sos](../includes/name-sos-short.md)] を使用する方法について学習します。
> [!div class="checklist"]
> * データベースをバックアップする 
> * バックアップ状態を表示する
> * バックアップを実行するために使用するスクリプトを生成する
> * データベースを復元する
> * 復元タスクの状態を表示する

## <a name="prerequisites"></a>Prerequisites

このチュートリアルには、SQL Server *TutorialDB* が必要です。 *TutorialDB* データベースを作成するには、次のクイックスタートのいずれかを実行します。

- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して SQL Server に接続し、クエリを実行する](quickstart-sql-server.md)

このチュートリアルでは、SQL Server データベースに接続する必要があります。 Azure SQL Database には自動バックアップがあるため、Azure Data Studio では Azure SQL Database のバックアップと復元が実行されません。 詳細は、[自動 SQL Database バックアップ](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups)に関するページを参照してください。

## <a name="backup-a-database"></a>データベースをバックアップする

1. TutorialDB データベースダッシュボードを開きます ( **[サーバー]** サイドバーを開き (**Ctrl + G**)、 **[データベース]** を展開し、 **[TutorialDB]** を右クリック、 **[管理]** を選択します)。

2. **[データベースのバックアップ]** ダイアログを開きます ( **[タスク]** ウィジェットで **[バックアップ]** をクリックします)。

   ![タスク ウィジェット](./media/tutorial-backup-restore-sql-server/tasks.png)

3. このチュートリアルでは、既定のバックアップ オプションが使用されています。そのため、 **[バックアップ]** をクリックします。
   ![バックアップ ダイアログ](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

**[バックアップ]** をクリックすると、 **[データベースのバックアップ]** ダイアログボックスが消え、バックアップ プロセスが開始されます。

## <a name="view-the-backup-status-and-view-the-backup-script"></a>バックアップの状態を表示し、バックアップ スクリプトを表示する

1. *[アクション]* バーの時計アイコンをクリックするか、**Ctrl + T** キーを押し、 **[タスクの履歴]** サイドバーを開きます。

   ![タスクの履歴](./media/tutorial-backup-restore-sql-server/task-history.png)

2. エディターでバックアップ スクリプトを表示するには、 **[Backup Database succeeded]\(データベース バックアップに成功しました\)** を右クリックし、 **[スクリプト]** を選択します。

   ![バックアップ スクリプト](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>データベースをバックアップ ファイルから復元する


1. **[サーバー]** サイドバーを開き (**Ctrl + G**)、サーバーを右クリックし、 **[管理]** を選択します。 

2. **[データベースの復元]** ダイアログを開きます ( **[タスク]** ウィジェットで **[復元]** をクリックします)。

2. **[復元元]** フィールドで **[バックアップ ファイル]** を選択します。 

3. **[バックアップ ファイル パス]** フィールドの省略記号 (...) をクリックし、*TutorialDB* の最新バックアップ ファイルを選択します。

3. **[Destination]\(復元先\)** セクションの **[Target database]\(復元先データベース\)** フィールドに「**TutorialDB_Restored**」と入力すると、バックアップ ファイルが新しいデータベースに復元されます。

   ![復元 (restore)](./media/tutorial-backup-restore-sql-server/restore.png)

4. **[復元]** をクリックします。

5. 復元操作の状態を表示するには、**Ctrl + T** キーを押して **[タスク履歴]** サイドバーを開きます。

   ![復元 (restore)](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


このチュートリアルでは、次の方法を学習しました。
> [!div class="checklist"]
> * データベースをバックアップする 
> * バックアップ状態を表示する
> * バックアップを実行するために使用するスクリプトを生成する
> * データベースを復元する
> * 復元タスクの状態を表示する

