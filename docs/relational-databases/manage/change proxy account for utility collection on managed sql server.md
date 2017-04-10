---
title: "SQL Server のマネージ インスタンスにおけるユーティリティ コレクション セットのプロキシ アカウントの変更 (SQL Server ユーティリティ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# SQL Server のマネージ インスタンスにおけるユーティリティ コレクション セットのプロキシ アカウントの変更 (SQL Server ユーティリティ)
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のマネージ インスタンスでユーティリティ コレクション セットのプロキシ アカウントを変更する方法について説明します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### SQL Server のマネージ インスタンスにおけるユーティリティ コレクション セットのプロキシ アカウントを変更するには  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから削除します。  
  
    -   SSMS の**ユーティリティ エクスプローラー**で**[マネージ インスタンス]** ノードをクリックします。  
  
    -   **ユーティリティ エクスプローラー**のリスト ビューで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前を右クリックし、**[マネージ インスタンスの削除]** をクリックします。 詳細については、「[SQL Server ユーティリティからの SQL Server のインスタンスの削除](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md)」を参照してください。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに再度登録します。  
  
    -   SSMS の**ユーティリティ エクスプローラー**で、**[マネージ インスタンス]** ノードを右クリックし、**[マネージ インスタンスの追加]** をクリックします。  
  
    -   新しいプロキシ アカウントを指定して、画面の指示に従ってウィザードを完了します。  
  
## 参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [SQL Server ユーティリティのトラブルシューティング](../Topic/Troubleshoot%20the%20SQL%20Server%20Utility.md)  
  
  