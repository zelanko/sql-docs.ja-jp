---
title: "トレース結果のテーブルへの保存 (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "トレースの保存"
  - "トレース [SQL Server], 保存"
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# トレース結果のテーブルへの保存 (SQL Server Profiler)
  このトピックでは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して、トレース結果をデータベース テーブルに保存する方法について説明します。  
  
### トレース結果をテーブルに保存するには  
  
1.  **[ファイル]** メニューの **[新しいトレース]** をクリックし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  **[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、**[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。 この設定を無効にするには、**[ツール]** メニューの **[オプション]** をクリックし、**[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。  
  
2.  **[トレース名]** ボックスにトレースの名前を入力し、**[テーブルに保存]** チェック ボックスをオンにします。  
  
3.  **[サーバーへの接続]** ダイアログ ボックスで、トレース テーブルを格納する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続します。  
  
4.  **[キャプチャ先テーブル]** ダイアログ ボックスで、**[データベース]** ボックスの一覧からデータベースを選択します。  
  
5.  **[所有者]** ボックスの一覧で、トレースの所有者を選択します。  
  
6.  **[テーブル]** ボックスの一覧で、トレース結果用のテーブルの名前を入力または選択します。 クリックして **OK.**  
  
7.  **[トレースのプロパティ]** ダイアログ ボックスで、**[最大行数の設定 (1000 行単位)]** チェック ボックスをオンにして、保存する最大行数を指定します。  
  
## 参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  