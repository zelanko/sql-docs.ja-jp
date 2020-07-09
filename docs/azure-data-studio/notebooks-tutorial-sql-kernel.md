---
title: Azure Data Studio の Notebooks と SQL Kernel
description: このチュートリアルでは、SQL Server ノートブックを作成し、実行する方法を紹介します。
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray, alayu
ms.topic: tutorial
ms.prod: azure-data-studio
ms.technology: ''
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 64e5bcfa188707e784d33a6504b120c4ce0ea553
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85735316"
---
# <a name="create-and-run-a-sql-server-notebook"></a>SQL Server ノートブックを作成して実行する

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

このチュートリアルでは、SQL Server を使用し、Azure Data Studio でノートブックを作成し、実行する方法について説明します。

## <a name="prerequisites"></a>前提条件

- [Azure Data Studio をインストールしていること](download-azure-data-studio.md)
- SQL Server をインストールしていること
  - [Windows](../database-engine/install-windows/install-sql-server.md)
  - [Linux](../linux/sql-server-linux-setup.md)

## <a name="new-notebook"></a>新しいノートブック

次の手順では、Azure Data Studio でノートブック ファイルを作成する方法を示しています。

1. Azure Data Studio で SQL Server に接続します。

2. **[サーバー]** ウィンドウの **[接続]** の下で選択します。 次に **[新しいノートブック]** を選択します。

   ![ノートブックを開く](media/notebook-tutorial/azure-data-studio-open-notebook.png)

3. **[カーネル]** とターゲット コンテキスト ( **[アタッチ先]** ) が設定されるまで待ちます。 **[カーネル]** が **[SQL]** に設定されていることを確認し、SQL Server の **[アタッチ先]** を設定します (今回はその "*localhost*" です)。

   ![[カーネル] と [アタッチ先] を設定する](media/notebook-tutorial/set-kernel-and-attach-to.png)

## <a name="run-a-notebook-cell"></a>ノートブック セルを実行する

セルの左側にある [再生] ボタンを押して、各ノートブック セルを実行することができます。 セルの実行が完了した後、結果がノートブックに表示されます。

### <a name="code"></a>コード

ツールバーの **[+Code]** コマンドを選択して、新しいコード セルを追加します。

![ノートブック ツール バー](media/notebooks-guidance/notebook-toolbar.png)

この例では、新しいデータベースを作成します。

```sql
USE master
GO

   -- Drop the database if it already exists
IF  EXISTS (
        SELECT name
        FROM sys.databases
        WHERE name = N'TestNotebookDB'
   )
DROP DATABASE TestNotebookDB
GO

-- Create the database
CREATE DATABASE TestNotebookDB
GO
```

   ![ノートブック セルを実行する](media/notebook-tutorial/run-notebook-cell.png)

結果を返すスクリプトを実行した場合、その結果を別の形式で保存できます。

- CSV として保存
- Excel として保存
- JSON として保存
- XML として保存

今回、[PI](../t-sql/functions/pi-transact-sql.md) の結果を返します。

```sql
SELECT PI() AS PI;
GO
```

![ノートブック セルを実行する](media/notebook-tutorial/run-notebook-cell-2.png)

### <a name="text"></a>Text

ツールバーの **[+Text]** コマンドを選択して、新しいテキスト セルを追加します。

![ノートブック ツール バー](media/notebooks-guidance/notebook-toolbar.png)

セルは編集モードに変わり、「markdown」と入力すると、プレビューが同時に表示されます。

![Markdown セル](media/notebooks-guidance/notebook-markdown-cell.png)

テキスト セルの外側を選択すると、markdown テキストが表示されます。

![Markdown テキスト](media/notebooks-guidance/notebook-markdown-preview.png)

## <a name="next-steps"></a>次のステップ

ノートブックについてさらに学習します:

- [SQL Server でノートブックを使用する方法](notebooks-guidance.md)

- [Azure Data Studio でノートブックを管理する方法](notebooks-manage-sql-server.md)

- [Spark を使用したサンプル ノートブックの実行](../big-data-cluster/notebooks-tutorial-spark.md)