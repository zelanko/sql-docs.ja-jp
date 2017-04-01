---
title: "トレースの一時停止 (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "トレースの一時停止"
  - "一時的なトレースの停止"
  - "トレース [SQL Server], 一時停止"
  - "トレースの停止"
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# トレースの一時停止 (SQL Server Profiler)
  トレースを一時停止すると、トレースを再開するまで、それ以上のイベント データはキャプチャされません。  
  
 トレースを一時停止すると、トレースを再開するまで、それ以上のイベント データはキャプチャされません。 トレースを再開すると、トレース操作が再開されます。 キャプチャを再開しても、それ以前にキャプチャしたデータが失われることはありません。 トレースを再開すると、その時点から、データのキャプチャが再開されます。 トレースを一時停止している間は、名前、イベント、列、およびフィルターを変更することができます。 ただし、トレース データの送信先またはサーバー接続は変更できません。  
  
### トレースを一時停止するには  
  
1.  実行中のトレースを含んでいるウィンドウを選択します。  
  
2.  **[ファイル]** メニューの **[トレースの一時停止]** をクリックします。  
  
## 参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  