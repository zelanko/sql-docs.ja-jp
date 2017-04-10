---
title: "SQL Server インスタンス上のデータベースの一覧表示 | Microsoft Docs"
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
  - "現在のデータベース"
  - "現在サーバー上に存在するデータベース [SQL Server]"
  - "データベース一覧 [SQL Server]"
  - "データベース一覧の表示"
  - "データベース一覧の確認"
  - "データベース [SQL Server], 表示"
  - "サーバー [SQL Server], に一覧表示されているデータベース"
  - "データベースの一覧表示"
ms.assetid: 7ee7a789-db36-4be9-8a0e-0362a1e152dd
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# SQL Server インスタンス上のデータベースの一覧表示
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]インスタンス上のデータベースの一覧を表示する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用して SQL Server インスタンス上のデータベースの一覧を表示するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> 権限  
 **sys.databases** の呼び出し元がデータベースの所有者ではなく、データベースが **master** でも **tempdb** でもない場合、対応する行を表示するには、少なくとも **master** データベースで、ALTER ANY DATABASE または VIEW ANY DATABASE のサーバーレベルの権限、あるいは、CREATE DATABASE の権限が必要です。 呼び出し元が接続しているデータベースは常に **sys.databases**で確認できます。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### SQL Server インスタンス上のデータベースの一覧を表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  インスタンス上のすべてのデータベースの一覧を表示するには、 **[データベース]**を展開します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### SQL Server インスタンス上のデータベースの一覧を表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに存在するデータベースの一覧を返します。 この一覧には、データベースの名前、ID、および作成日が含まれます。  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT name, database_id, create_date  
FROM sys.databases ;  
GO  
  
```  
  
## 参照  
 [データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  