---
title: "SQL Server エラー ログの表示 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "07/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ログの表示"
  - "ログの確認"
  - "エラー [SQL Server], ログ"
  - "ログ [SQL Server], SQL Server エラー ログ"
  - "ログ [SQL Server], 表示"
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: 14
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 14
---
# SQL Server エラー ログの表示 (SQL Server Management Studio)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログには、トラブルシューティングに必要なユーザー定義のイベントや特定のシステム イベントが含まれています。 
  

  ## ログを表示する方法
1.  SSMS で **[オブジェクト エクスプローラー]** を選択します。

>オブジェクト エクスプローラーを**開く**キーボード ショートカットは **F8** です。 または、上部メニューで [表示]、[オブジェクト エクスプローラー] の順にクリックします。![Object_explorer](../../relational-databases/performance/media/object-explorer.png) 


2.  **[オブジェクト エクスプローラー]** で、SQL Server のインスタンスに接続して、そのインスタンスを展開します。
  
3.  **[管理]** セクションを探して開きます (表示するアクセス許可が必要です)。

4.  **[SQL Server ログ]** を右クリックし、[表示] を選択して、**[SQL Server ログの表示]** を選択します。
 ![View_SQLServer_Log_SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5.  ログ ファイル ビューアーでログの一覧が表示されます (1 分ほどかかる場合があります)。
  
6. [MSSQLTips.com](https://www.mssqltips.com/) の「[Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/)」 (SQL Server エラー ログ ファイルの場所を探す) をご覧ください。 役に立つ情報があります。
  
  