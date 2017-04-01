---
title: "スキーマ変更のレプリケート | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replication [SQL Server], schema changes"
  - "スキーマ [SQL Server レプリケーション], 変更のレプリケート"
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# スキーマ変更のレプリケート
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、スキーマの変更をレプリケートする方法について説明します。  
  
 パブリッシュされたアーティクルに対し、次のようなスキーマ変更を行った場合、変更内容が既定で [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーに反映されます。  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **スキーマの変更をレプリケートするために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   ALTER TABLE … ALTER TABLE … DROP COLUMN ステートメントは、スキーマ変更のレプリケーションを無効にした場合でも、サブスクリプションに削除対象の列が含まれているすべてのサブスクライバーに必ずレプリケートされます。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションのスキーマ変更をレプリケートしないようにする場合は、スキーマの変更のレプリケーションを無効にする、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
#### スキーマ変更のレプリケーションを無効にするには  
  
1.   **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでの値を設定、 **スキーマ変更のレプリケート** プロパティを **False**します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     特定のスキーマ変更だけを反映させるには、スキーマを変更する前にプロパティを **[True]** に設定し、変更後に **[False]** に設定します。 逆に、ほとんどのスキーマ変更を反映するには、スキーマ変更前にプロパティを **[False]** に設定し、変更後に **[True]** に設定します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーションのストアド プロシージャを使用すると、これらのスキーマ変更をレプリケートするかどうかを指定できます。 どのストアド プロシージャを使用するかは、パブリケーションの種類によって異なります。  
  
#### スキーマ変更をレプリケートしないスナップショット パブリケーションまたはトランザクション パブリケーションを作成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addpublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), の値を指定する **0** の **@replicate_ddl**します。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
#### スキーマ変更をレプリケートしないマージ パブリケーションを作成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), の値を指定する **0** の **@replicate_ddl**します。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションでスキーマ変更のレプリケートを一時的に無効化するには  
  
1.  パブリケーションのスキーマ変更のレプリケーションが、実行 [sp_changepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), の値を指定する **replicate_ddl** の **@property** の **0** の **@value**します。  
  
2.  パブリッシュされたオブジェクトに対し、DDL コマンドを実行します。  
  
3.  (省略可能)実行することでスキーマ変更のレプリケートを再度有効に [sp_changepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), の値を指定する **replicate_ddl** の **@property** の **1** の **@value**します。  
  
#### マージ パブリケーションでスキーマ変更のレプリケートを一時的に無効化するには  
  
1.  パブリケーションのスキーマ変更のレプリケーションが、実行 [sp_changemergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), の値を指定する **replicate_ddl** の **@property** の **0** の **@value**します。  
  
2.  パブリッシュされたオブジェクトに対し、DDL コマンドを実行します。  
  
3.  (省略可能)実行することでスキーマ変更のレプリケートを再度有効に [sp_changemergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), の値を指定する **replicate_ddl** の **@property** の **1** の **@value**します。  
  
## 参照  
 [パブリケーション データベースでのスキーマの変更](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [パブリケーション データベースでのスキーマの変更](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  