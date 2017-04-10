---
title: "マージ パブリケーションの互換性レベルの設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compatibility [SQL Server], replication"
  - "backward compatibility [SQL Server], replication"
  - "パブリケーション [SQL Server レプリケーション]、下位互換性"
ms.assetid: db47ac73-948b-4d77-b272-bb3565135ea5
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# マージ パブリケーションの互換性レベルの設定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ パブリケーションの互換性レベルを設定する方法について説明します。 マージ レプリケーションでは、パブリケーションの互換性レベルを使用して、指定されたデータベースのパブリケーションで使用できる機能を決定します。  
  
 **このトピックの内容**  
  
-   **マージ パブリケーションのパブリケーション互換性レベルを設定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードの **[サブスクライバーの種類]** ページで互換性レベルを設定します。 このウィザードにアクセスする方法の詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md)します。 パブリケーション スナップショットの作成後、互換性レベルを上げることはできますが、下げることはできません。 互換性レベルを上げる、 **全般** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。 パブリケーションの互換性レベルを上げた場合、設定した互換性レベルよりも前のバージョンを実行しているサーバーでは、既存のサブスクリプションを同期できなくなります。  
  
> [!NOTE]  
>  互換性レベルはパブリケーションの他のプロパティ、および有効になるアーティクルのプロパティと密接に関連しているため、互換性レベルとその他のプロパティをこのダイアログ ボックスで同時に変更しないでください。 プロパティの変更後、パブリケーションのスナップショットを再生成する必要があります。  
  
#### パブリケーションの互換性レベルを設定するには  
  
-   パブリケーションの新規作成ウィザードの **[サブスクライバーの種類]** ページで、パブリケーションがサポートするサブスクライバーの種類を選択します。  
  
#### パブリケーションの互換性レベルを上げるには  
  
-    **全般** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** の選択] ダイアログ ボックスで、 **互換性レベル**します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 マージ パブリケーションの互換性レベルは、パブリケーションを作成したときにプログラムで設定するか、または後でプログラムから変更できます。 レプリケーション ストアド プロシージャを使用して、このパブリケーション プロパティを設定または変更できます。  
  
#### マージ パブリケーションのパブリケーション互換性レベルを設定するには  
  
1.  パブリッシャーで実行 [sp_addmergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), 、値を指定する **@publication_compatibility_level** 、パブリケーションの以前のバージョンの互換性を確保する [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
#### マージ パブリケーションのパブリケーション互換性レベルを変更するには  
  
1.  実行 [sp_changemergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), を指定して **publication_compatibility_level** の **@property** との適切なパブリケーション互換性レベル **@value**します。  
  
#### マージ パブリケーションのパブリケーション互換性レベルを確認するには  
  
1.  実行 [sp_helpmergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), 、目的のパブリケーションを指定します。  
  
2.  パブリケーションの互換性レベルを検索、 **backward_comp_level** 結果セット内の列です。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、マージ パブリケーションを作成して、パブリケーションの互換性レベルを設定します。  
  
```  
-- To avoid storing the login and password in the script file, the values   
-- are passed into SQLCMD as scripting variables. For information about   
-- how to use scripting variables on the command line and in SQL Server  
-- Management Studio, see the "Executing Replication Scripts" section in  
-- the topic "Programming Replication Using System Stored Procedures".  
  
--Add a new merge publication.  
DECLARE @publicationDB AS sysname;  
DECLARE @publication AS sysname;  
DECLARE @login AS sysname;  
DECLARE @password AS sysname;  
SET @publicationDB = N'AdventureWorks2012';   
SET @publication = N'AdvWorksSalesOrdersMerge'   
SET @login = $(Login);  
SET @password = $(Password);  
  
-- Create a new merge publication.   
USE [AdventureWorks2012]  
EXEC sp_addmergepublication   
@publication = @publication,   
-- Set the compatibility level to SQL Server 2014.  
@publication_compatibility_level = '120RTM';   
  
-- Create the snapshot job for the publication.  
EXEC sp_addpublication_snapshot   
@publication = @publication,  
@job_login = @login,  
@job_password = @password;  
GO  
```  
  
 次の例では、マージ パブリケーションのパブリケーション互換性レベルを変更します。  
  
> [!NOTE]  
>  パブリケーションで特定の互換性レベルを必要とする機能を使用していると、パブリケーションの互換性レベルの変更が許可されない場合があります。 詳細については、次を参照してください。 [レプリケーションの旧バージョンとの互換性](../../../relational-databases/replication/replication-backward-compatibility.md)します。  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
  
-- Change the publication compatibility level to   
-- SQL Server 2012.  
EXEC sp_changemergepublication   
@publication = @publication,   
@property = N'publication_compatibility_level',   
@value = N'110RTM';  
GO  
  
```  
  
 次の例では、マージ パブリケーションの現在のパブリケーション互換性レベルが返されます。  
  
```  
DECLARE @publication AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge' ;  
EXEC sp_helpmergepublication   
@publication = @publication;  
GO  
  
```  
  
## 参照  
 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)  
  
  