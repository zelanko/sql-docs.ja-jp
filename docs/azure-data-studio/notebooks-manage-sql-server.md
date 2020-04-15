---
title: SQL Server ノートブックの管理
description: Azure Data Studio でノートブックを管理する方法について学習します。 これには、ノートブックを開く、ノートブックの保存、ビッグ データ クラスター接続の変更などが含まれます。
author: markingmyname
ms.author: maghan
ms.reviewer: achatter, alayu, mikeray
ms.metadata: seo-lt-2019
ms.topic: conceptual
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 9b071a9d1b9e770e1443e5df539208baa4399a30
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531595"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Azure Data Studio でノートブックを管理する方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server を使用して Azure Data Studio でノートブック ファイルを開いて保存する方法について示します。 また、SQL Server への接続を変更する方法も示します。

## <a name="open-a-notebook"></a>ノートブックを開く

**[ノートブックを開く]** ダイアログを開くには、いくつかの方法があります。 [ファイル] メニュー、ダッシュボード、コマンド パレットを使用できます。 次のセクションでは、各メソッドについて説明します。

### <a name="file-menu"></a>[ファイル] メニュー

[ファイル] メニューで **[ファイルを開く]** を選択します (Windows の場合は Ctrl + O キー、Mac の場合は Cmd + O キー)。

![[ファイルを開く] を選択して [ファイルを開く] ダイアログを開く](./media/notebooks-manage-sql-server/open-file-1.png)

### <a name="dashboard"></a>ダッシュボード

ダッシュボードで **[ノートブックを開く]** をクリックして、[ファイルを開く] ダイアログを開きます。

![ダッシュボードで [ノートブックを開く] を選択して [ファイルを開く] ダイアログを開く](./media/notebooks-manage-sql-server/open-file-2.png) 

### <a name="command-palette"></a>コマンド パレット

コマンド パレットから「**File: Open**」コマンドを使用します (Windows の場合は Ctrl + Shift + P キー、Mac の場合は Cmd + Shift + P キーと入力)。

![コマンド パレットに「File: Open」と入力し、[ファイルを開く] ダイアログを開く](./media/notebooks-manage-sql-server/open-file-3.png)

## <a name="save-a-notebook"></a>ノートブックを保存する

現在、ノートブックを保存する方法は 1 つあります。 ノートブックのツール バーから **[保存]** を選択します。

![ノートブックのツール バーの [保存] を選択してファイルを保存する](./media/notebooks-manage-sql-server/save-file-1.png)

> [!NOTE]
> 現在、次のメソッドではノートブックへの変更は保存されません。
>
> - [ファイル] メニューの **[ファイルの保存]** 、 **[名前を付けて保存]** 、 **[すべてのファイルを保存]** コマンド。
> - コマンド パレットに入力した「**File: Save**」コマンド。

## <a name="change-the-connection"></a>接続の変更

ノートブックの接続を変更するには:

1. ノートブック ツール バーから **[アタッチ先]** メニューを選択し、 **[接続の変更]** を選択します。

   ![ノートブックのツール バーから [アタッチ先] メニューをクリックする](./media/notebooks-manage-sql-server/select-attach-to-1.png)

2. これで最近使用した接続サーバーを選択するか、新しい接続の詳細を入力して接続できます。

   ![[アタッチ先] メニューからサーバーを選択する](./media/notebooks-manage-sql-server/select-attach-to-2.png)

## <a name="next-steps"></a>次のステップ

Azure Data Studio のノードブックの詳細については、「[SQL Server 2019 でノートブックを使用する方法](notebooks-guidance.md)」を参照してください。
