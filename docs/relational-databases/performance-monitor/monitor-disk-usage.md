---
title: "ディスクの使用量の監視 | Microsoft Docs"
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
  - "データベース監視 [SQL Server], ディスク使用量"
  - "ディスク [SQL Server]"
  - "パフォーマンスの監視 [SQL Server], ディスク使用量"
  - "サーバー パフォーマンス [SQL Server], ディスク使用量"
  - "監視 [SQL Server], ディスク利用状況"
  - "過度なページング [SQL Server]"
  - "データベースのチューニング [SQL Server], ディスク使用量"
  - "I/O [SQL Server], 監視"
  - "ディスク [SQL Server], 利用状況の監視"
  - "ディスク利用状況の隔離 [SQL Server]"
  - "データベース パフォーマンス [SQL Server], ディスク使用量"
  - "サーバー パフォーマンスの監視 [SQL Server], ディスク使用量"
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# ディスクの使用量の監視
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、Microsoft Windows オペレーティング システムの入出力 (I/O) 呼び出しを使用して、ディスクに対する読み取りおよび書き込み操作を実行します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  では、ディスク I/O を実行する時期と方法が管理されます。ただし、基本的な I/O 操作は Windows オペレーティング システムで実行されます。 I/O サブシステムには、システム バス、ディスク コントローラー カード、ディスク、テープ ドライブ、CD-ROM ドライブなど、多数の I/O 装置が含まれます。 ディスク I/O は、頻繁にシステムのボトルネックの原因となります。  
  
 ディスク利用状況の監視には、次の 2 つの領域があります。  
  
-   ディスク I/O の監視と、過度なページングの検出  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で生成されるディスク利用状況の隔離  
  
 詳細については、「[ディスク使用量の監視](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)」を参照してください。  
  
  