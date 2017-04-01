---
title: "手動によるサブスクリプションの初期化 | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "manual subscription initialization [SQL Server replication]"
  - "subscriptions [SQL Server replication], initializing"
  - "サブスクリプションの初期化 [SQL Server レプリケーション], スナップショットなし"
ms.assetid: 27a1bc38-e498-4fff-8082-04b52aa4b22c
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# 手動によるサブスクリプションの初期化
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、サブスクリプションを手動で初期化する方法について説明します。 サブスクリプションを初期化する場合、一般には、初期スナップショットが使用されます。ただし、スキーマおよび初期データがサブスクライバー側に既に存在していれば、パブリケーションのサブスクリプションをスナップショットを使用せずに初期化できます。  
  

##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   データとスキーマをサブスクライバーにコピーしてからサブスクリプションが手動で初期化されるまでの間に、トランザクション レプリケーションを使ってパブリッシュされたデータベース上で処理が実行されると、この処理による変更がサブスクライバーにレプリケートされない場合があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 スキーマ (通常はデータも含まれます) をサブスクリプション データベースにコピーすることによって、パブリケーションに対するサブスクリプションを手動で初期化します。 スキーマとデータは、パブリケーション データベースと一致している必要があります。 その後、サブスクリプションの新規作成ウィザードの **[サブスクリプションの初期化]** ページで、サブスクリプションにスキーマとデータが必要ないことを指定します。 このウィザードにアクセスする方法の詳細については、次を参照してください。 [、スナップショット トランザクション サブスクリプションなしの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md) と [プル サブスクリプションを作成する](../../relational-databases/replication/create-a-pull-subscription.md)です。  
  
 初めてサブスクリプションを同期させたときに、レプリケーションに必要なオブジェクトとメタデータがサブスクリプション データベースにコピーされます。  
  
#### パブリケーションに対するサブスクリプションを手動で初期化するには  
  
1.  スキーマとデータがサブスクリプション データベースにコピーされていることを確認します。  
  
2.  サブスクリプションの新規作成ウィザードの **[サブスクリプションの初期化]** ページで、 **[初期化]** チェック ボックスをオフにします。 この操作を、レプリケーション オブジェクトとメタデータのみをコピーする必要がある各サブスクリプションに対して行います。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 サブスクリプションは、レプリケーションのストアド プロシージャを使用して手動で初期化できます。  
  
#### トランザクション パブリケーションのプル サブスクリプションを手動で初期化するには  
  
1.  スキーマとデータがサブスクリプション データベースに存在することを確認します。 詳細については、次を参照してください。 [、スナップショット トランザクション サブスクリプションなしの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)します。 指定 **@publication**, 、**@subscriber**, の公開データを格納するサブスクライバー データベースの名前 **@destination_db**, の値 **プル** の **@subscription_type**, の値との **レプリケーションのサポートのみ** の **@sync_type**します。 詳しくは、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」をご覧ください。  
  
3.  サブスクライバーで、[sp_addpullsubscription](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md) を実行します。 サブスクリプションを更新するには、次を参照してください。 [トランザクション パブリケーションに対する更新可能なサブスクリプションを作成する](https://technet.microsoft.com/library/ms152769(v=sql.130).aspx)です。  
  
4.  サブスクライバーで、[sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) を実行します。 詳しくは、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」をご覧ください。  
  
5.  ディストリビューション エージェントを起動して、パブリッシャーからレプリケーション オブジェクトを転送し、最新の変更をダウンロードします。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」をご覧ください。  
  
#### トランザクション パブリケーションのプッシュ サブスクリプションを手動で初期化するには  
  
1.  スキーマとデータがサブスクリプション データベースに存在することを確認します。 詳細については、次を参照してください。 [、スナップショット トランザクション サブスクリプションなしの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)します。 パブリッシュされたデータを格納するサブスクライバー データベースの名前を指定 **@destination_db**, の値 **プッシュ** の **@subscription_type**, の値との **レプリケーションのサポートのみ** の **@sync_type**します。 サブスクリプションを更新するには、次を参照してください。 [トランザクション パブリケーションに対する更新可能なサブスクリプションを作成する](https://technet.microsoft.com/library/ms152769(v=sql.130).aspx)です。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)します。 詳しくは、「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」をご覧ください。  
  
4.  ディストリビューション エージェントを起動して、パブリッシャーからレプリケーション オブジェクトを転送し、最新の変更をダウンロードします。 詳しくは、「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」をご覧ください。  
  
#### マージ パブリケーションのプル サブスクリプションを手動で初期化するには  
  
1.  スキーマとデータがサブスクリプション データベースに存在することを確認します。 これは、サブスクライバーでパブリケーション データベースのバックアップを復元することによって行います。  
  
2.  パブリッシャーで実行 [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)します。 指定 **@publication**, 、**@subscriber**, 、**@subscriber_db**, の値との **プル** の **@subscription_type**します。 これにより、プル サブスクリプションが登録されます。  
  
3.  サブスクライバー、パブリッシュされたデータを含むデータベースで、次のように実行します。 [sp_addmergepullsubscription](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)します。 値を指定して **none** の **@sync_type**します。  
  
4.  サブスクライバーで、次のように実行します。 [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)します。 詳しくは、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」をご覧ください。  
  
5.  マージ エージェントを起動して、パブリッシャーからレプリケーション オブジェクトを転送し、最新の変更をダウンロードします。 詳しくは、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」をご覧ください。  
  
#### マージ パブリケーションのプッシュ サブスクリプションを手動で初期化するには  
  
1.  スキーマとデータがサブスクリプション データベースに存在することを確認します。 これは、サブスクライバーでパブリケーション データベースのバックアップを復元することによって行います。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)します。 公開データを格納するサブスクライバー データベースの名前を指定 **@subscriber_db**, の値 **プッシュ** の **@subscription_type**, の値との **none** の **@sync_type**します。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)します。 詳しくは、「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」をご覧ください。  
  
4.  マージ エージェントを起動して、パブリッシャーからレプリケーション オブジェクトを転送し、最新の変更をダウンロードします。 詳しくは、「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」をご覧ください。  
  
## 参照  
 [スナップショットを使用しないトランザクション サブスクリプションを初期化します。](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)   
 [レプリケートされたデータベースのバックアップと復元](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  