---
title: "SQL Server エラー ログの表示 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 20a301e257244b66e1c149c7cf8cf1f2489eb489
ms.openlocfilehash: a8c1290e33ad567520c813a1f365830644f545c7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/29/2017

---
# <a name="view-the-sql-server-error-log-sql-server-management-studio"></a>SQL Server エラー ログの表示 (SQL Server Management Studio)

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログには、トラブルシューティングに必要なユーザー定義のイベントや特定のシステム イベントが含まれています。 

## <a name="how-to-view-the-logs"></a>ログを表示する方法

1.  SSMS で **[オブジェクト エクスプローラー]** を選択します。 オブジェクト エクスプローラーを**開く**キーボード ショートカットは **F8** です。 または、上部メニューで **[表示]**、**[オブジェクト エクスプローラー]** の順にクリックします。
    
    ![Object_explorer](../../relational-databases/performance/media/object-explorer.png) 

2.  **[オブジェクト エクスプローラー]**で、SQL Server のインスタンスに接続して、そのインスタンスを展開します。
  
3.  **[管理]** セクションを探して開きます (表示するアクセス許可が必要です)。

4.  **[SQL Server ログ]** を右クリックし、**[表示]** を選択して、**[SQL Server ログの表示]** を選択します。

    ![View_SQLServer_Log_SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5.  ログ ファイル ビューアーでログの一覧が表示されます (1 分ほどかかる場合があります)。
  
6. [MSSQLTips.com](https://www.mssqltips.com/) の「 [Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/)」 (SQL Server エラー ログ ファイルの場所を探す) をご覧ください。 役に立つ情報があります。


