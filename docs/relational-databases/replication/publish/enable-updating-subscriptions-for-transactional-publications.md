---
title: "トランザクション パブリケーションの更新可能なサブスクリプションの有効化 | Microsoft Docs"
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
  - "transactional replication, updatable subscriptions"
  - "updatable subscriptions, enabling"
  - "サブスクリプション [SQL Server レプリケーション], 更新可能"
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# トランザクション パブリケーションの更新可能なサブスクリプションの有効化
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、トランザクション パブリケーションに対するサブスクリプションの更新を有効にする方法について説明します。  
  
> **注: ** [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  

##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードの **[パブリケーションの種類]** ページで、トランザクション パブリケーションの更新サブスクリプションを有効にします。  
  
 更新サブスクリプションを使用するには、サブスクリプションの新規作成ウィザードでオプションも構成する必要があります。  
  
#### 更新サブスクリプションを有効にするには  
  
1.  パブリケーションの新規作成ウィザードの **[パブリケーションの種類]** ページで、 **[更新可能なサブスクリプションを含むトランザクション パブリケーション]**を選択します。  
  
2.  **[エージェント セキュリティ]** ページで、スナップショット エージェントおよびログ リーダー エージェントの他に、キュー リーダー エージェントのセキュリティ設定を指定します。 キュー リーダー エージェントが実行されるアカウントに必要な権限の詳細については、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
    > **注:** 即時更新サブスクリプションのみを使用する場合でも、キュー リーダー エージェントが構成されています。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーション ストアド プロシージャを使用してプログラムからトランザクション パブリケーションを作成するときに、即時更新サブスクリプションまたはキュー更新サブスクリプションを有効にできます。  
  
#### 即時更新サブスクリプションをサポートするパブリケーションを作成するには  
  
1.  必要に応じて、パブリケーション データベース用のログ リーダー エージェント ジョブを作成します。  
  
    -   パブリケーション データベース用のログ リーダー エージェント ジョブが既に存在する場合、手順 2. に進みます。  
  
    -   パブリッシュされたデータベースに対するログ リーダー エージェント ジョブが存在するかどうかが不明な場合は実行 [sp_helplogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 結果セットが空の場合、ログ リーダー エージェント ジョブを作成する必要があります。  
  
    -   パブリッシャーで実行 [sp_addlogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)します。 指定の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] のエージェントを実行する Windows 資格情報 **@job_name** と **@password**します。 値を指定する場合は、パブリッシャーに接続するときに、エージェントは SQL Server 認証を使用もする必要があります **0** の **@publisher_security_mode** と [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。  
  
2.  実行 [sp_addpublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), の値を指定する **true** パラメーター **@allow_sync_tran**します。  
  
3.  パブリッシャーで実行 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。 手順 2 で使用するパブリケーションの名前を指定 **@publication** とスナップショット エージェントを実行する Windows 資格情報 **@job_name** と **@password**します。 値を指定する場合は、パブリッシャーに接続するときに、エージェントは SQL Server 認証を使用もする必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。  
  
4.  パブリケーションにアーティクルを追加します。 詳細については、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」を参照してください。  
  
5.  サブスクライバーで、このパブリケーションに対する更新サブスクリプションを作成します。   
  
#### キュー更新サブスクリプションをサポートするパブリケーションを作成するには  
  
1.  必要に応じて、パブリケーション データベース用のログ リーダー エージェント ジョブを作成します。  
  
    -   パブリケーション データベース用のログ リーダー エージェント ジョブが既に存在する場合、手順 2. に進みます。  
  
    -   パブリッシュされたデータベースに対するログ リーダー エージェント ジョブが存在するかどうかが不明な場合は実行 [sp_helplogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 結果セットが空の場合、ログ リーダー エージェント ジョブを作成する必要があります。  
  
    -   パブリッシャーで実行 [sp_addlogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)します。 エージェントを実行する Windows 資格情報を指定 **@job_name** と **@password**します。 値を指定する場合は、パブリッシャーに接続するときに、エージェントは SQL Server 認証を使用もする必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。  
  
2.  必要に応じて、ディストリビューター用のキュー リーダー エージェント ジョブを作成します。  
  
    -   ディストリビューション データベース用のキュー リーダー エージェント ジョブが既に存在する場合、手順 3. に進みます。  
  
    -   キュー リーダー エージェント ジョブがディストリビューション データベースに存在するかどうかが不明な場合は実行 [sp_helpqreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md) ディストリビューター側でディストリビューション データベースです。 結果セットが空の場合、キュー リーダー エージェント ジョブを作成する必要があります。  
  
    -   ディストリビューターで実行 [sp_addqreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)します。 エージェントを実行する Windows 資格情報を指定 **@job_name** と **@password**します。 これらの資格情報は、キュー リーダー エージェントがパブリッシャーとサブスクライバーに接続するときに使用されます。 詳しくは、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
3.  実行 [sp_addpublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), の値を指定する **true** パラメーターの **@allow_queued_tran** の **pub wins**, 、**sub reinit**, 、または **sub wins** の **@conflict_policy**します。  
  
4.  パブリッシャーで実行 [sp_addpublication_snapshot (TRANSACT-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。 手順 3 で使用されるパブリケーションの名前を指定 **@publication** とスナップショット エージェントを実行する Windows 資格情報 **@snapshot_job_name** と **@password**します。 値を指定する場合は、パブリッシャーに接続するときに、エージェントは SQL Server 認証を使用もする必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。  
  
5.  パブリケーションにアーティクルを追加します。 詳細については、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」を参照してください。  
  
6.  サブスクライバーで、このパブリケーションに対する更新サブスクリプションを作成します。  
  
#### キュー更新サブスクリプションが可能なパブリケーションの競合ポリシーを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)します。 値を指定して **conflict_policy** の **@property** との競合ポリシー モード **pub wins**, 、**sub reinit**, 、または **sub wins** の **@value**します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、即時更新プル サブスクリプションとキュー更新プル サブスクリプションの両方がサポートされるパブリケーションを作成します。  
  
 [!code-sql[HowTo#sp_createtranupdatingpub](../../../relational-databases/replication/codesnippet/tsql/enable-updating-subscrip_1.sql)]  
  
## 参照  
 [更新の競合解決オプションはキューに置かれた &#40; 設定します。SQL Server Management Studio と #41 です。](../../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)   
 [トランザクション レプリケーションで使用するパブリケーションの種類](../../../relational-databases/replication/transactional/publication-types-for-transactional-replication.md)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)   
 [トランザクション パブリケーションの更新可能なサブスクリプションの作成](https://msdn.microsoft.com/library/mt740635.aspx)   
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sqlcmd でのスクリプト変数の使用](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  