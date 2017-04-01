---
title: "SQL Server:SQL Errors オブジェクト | Microsoft Docs"
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
  - "SQL Errors オブジェクト"
  - "SQLServer:SQL Errors"
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# SQL Server:SQL Errors オブジェクト
  Microsoft **の** SQLServer:SQL Errors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトには、 **SQL Errors**を監視するカウンターが用意されています。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** のカウンターについて説明します。  
  
|SQL Server SQL Errors のカウンター|説明|  
|------------------------------------|-----------------|  
|**Errors/sec**|1 秒あたりのエラー数|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|アイテム|定義|  
|----------|----------------|  
|**_Total**|すべてのエラーに関する情報。|  
|**DB Offline Errors**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で現在のデータベースがオフラインになる原因となる重大なエラーを追跡します。|  
|**Info Errors**|問題を起こしているわけではない、ユーザーに情報提供を行っているエラーメッセージの情報。|  
|**Kill Connection Errors**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在の接続を強制的に切断する原因となる重大なエラーを追跡します。|  
|**User Errors**|ユーザー エラーに関する情報。|  
  
## 参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  