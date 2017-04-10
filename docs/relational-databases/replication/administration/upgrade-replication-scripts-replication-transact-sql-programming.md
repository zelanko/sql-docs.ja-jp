---
title: "レプリケーション スクリプトのアップグレード (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "スクリプト [SQL Server レプリケーション]、アップグレード"
  - "SQL Server のアップグレード、レプリケートされたデータベース"
  - "レプリケーション アプリケーションのアップグレード"
  - "レプリケーション [SQL Server]、スクリプトの作成"
  - "レプリケーション [SQL Server]、アップグレード"
  - "レプリケートされたデータベースのアップグレード"
ms.assetid: 0b8720bd-f339-4842-bc8f-b35a46f6d3ee
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# レプリケーション スクリプトのアップグレード (レプリケーション Transact-SQL プログラミング)
  [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプト ファイルを使用して、レプリケーション トポロジをプログラムで構成できます。 詳細については、次を参照してください。 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)します。  
  
> [!IMPORTANT]  
>  **sysadmin** ロールのメンバーが実行するスクリプトについては、アップグレードは必須ではありませんが、このトピックの説明に従って既存のスクリプトを変更することをお勧めします。 「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)」の「エージェントに必要な権限」に記載されている各レプリケーション エージェントの最小権限を持つアカウントを指定します。  
  
 このようにセキュリティが強化されたことで、レプリケーション エージェント ジョブの実行に使用される [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows アカウントを明示的に指定できるため、権限をより詳細に設定できます。既存のスクリプトに含まれる次のストアド プロシージャは、このセキュリティ強化の影響を受けます。  
  
-   **sp_addpublication_snapshot**:  
  
     今すぐとして Windows 資格情報を指定する必要があります **@job_login** と **@job_password** の実行時に [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) スナップショット エージェントがディストリビューターで実行するジョブを作成します。  
  
-   **sp_addpushsubscription_agent**:  
  
     今すぐ実行する必要があります [sp_addpushsubscription_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) 明示的にジョブを追加し、Windows 資格情報を入力 (**@job_login** と **@job_password**) ディストリビューターでディストリビューション エージェント ジョブを実行します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]では、プッシュ サブスクリプションが作成されるときにこの操作が自動的に実行されました。  
  
-   **sp_addmergepushsubscription_agent**:  
  
     今すぐ実行する必要があります [sp_addmergepushsubscription_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) 明示的にジョブを追加し、Windows 資格情報を入力 (**@job_login** と **@job_password**)、ディストリビューター側でマージ エージェント ジョブを実行します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]では、プッシュ サブスクリプションが作成されるときにこの操作が自動的に実行されました。  
  
-   **sp_addpullsubscription_agent**:  
  
     Windows 資格情報をここでする必要があります **@job_login** と **@job_password** の実行時に [sp_addpullsubscription_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) サブスクライバーでディストリビューション エージェントを実行するジョブを作成します。  
  
-   **sp_addmergepullsubscription_agent**:  
  
     Windows 資格情報をここでする必要があります **@job_login** と **@job_password** の実行時に [sp_addmergepullsubscription_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) サブスクライバーでマージ エージェントを実行するジョブを作成します。  
  
-   **sp_addlogreader_agent**:  
  
     今すぐ実行する必要があります [sp_addlogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md) 手動でジョブを追加し、ログ リーダー エージェントをディストリビューターで実行する Windows 資格情報を指定します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]では、トランザクション パブリケーションが作成されるときにこの操作が自動的に実行されました。  
  
-   **sp_addqreader_agent**:  
  
     今すぐ実行する必要があります [sp_addqreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md) 手動でジョブを追加し、キュー リーダー エージェントをディストリビューターで実行する Windows 資格情報を指定します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]では、キュー更新をサポートするトランザクション パブリケーションが作成されるときにこの操作が自動的に実行されました。  
  
 導入されたセキュリティ モデルで [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], 、レプリケーション エージェントは、必ずのローカル インスタンスへの接続 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で指定された資格情報を使用して Windows 認証 **@job_name** と **@job_password**です。 レプリケーション エージェント ジョブを実行する際に使用する Windows アカウントの要件の詳細については、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納した場合は、ファイル自体が暗号化されていることを確認してください。  
  
### スナップショット パブリケーションまたはトランザクション パブリケーションを構成するスクリプトをアップグレードするには  
  
1.  既存のスクリプトにする前に [sp_addpublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), 、実行 [sp_addlogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 ログ リーダー エージェントを実行する Windows 資格情報を指定 **@job_name** と **@job_password**します。 エージェントが使用する場合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャーに接続するときに、認証の値も指定する必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション データベース用のログ リーダー エージェント ジョブが作成されます。  
  
    > [!NOTE]  
    >  この手順はトランザクション パブリケーションにのみ適用されます。スナップショット パブリケーションの場合は不要です。  
  
2.  (省略可能)前に [sp_addpublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), 、実行 [sp_addqreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md) ディストリビューター側でディストリビューション データベースです。 キュー リーダー エージェントを実行する Windows 資格情報を指定 **@job_name** と **@job_password**します。 これにより、ディストリビューター用のキュー リーダー エージェント ジョブが作成されます。  
  
    > [!NOTE]  
    >  この手順は、キュー更新サブスクライバーをサポートするトランザクション パブリケーションでのみ必要です。  
  
3.  (省略可能)更新の実行 [sp_addpublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) 新しいレプリケーション機能を実装するパラメーターの既定以外の値を設定します。  
  
4.  後に [sp_addpublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), 、実行 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 指定 **@publication** とスナップショット エージェントを実行する Windows 資格情報 **@job_name** と **@job_password**します。 エージェントが使用する場合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャーに接続するときに、認証の値も指定する必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。  
  
5.  (省略可能)更新の実行 [sp_addarticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) 新しいレプリケーション機能を実装するパラメーターの既定以外の値を設定します。  
  
### スナップショット パブリケーションまたはトランザクション パブリケーションにサブスクリプションを追加するスクリプトをアップグレードするには  
  
1.  サブスクリプションを作成するストアド プロシージャを実行した後、ディストリビューション エージェント ジョブを作成するストアド プロシージャを実行して、サブスクリプションを同期するようにしてください。 使用するストアド プロシージャは、サブスクリプションの種類に応じて変わります。  
  
    -   プル サブスクリプションの更新の実行 [sp_addpullsubscription_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) サブスクライバーでディストリビューション エージェントを実行する Windows 資格情報を提供する **@job_name** と **@job_password**します。 実行後にこれは、 [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)します。 詳細については、「 [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
    -   プッシュ サブスクリプションでは、実行 [sp_addpushsubscription_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) パブリッシャーです。 指定 **@subscriber**, 、**@subscriber_db**, 、**@publication**, 、パブリッシャー、ディストリビューター、ディストリビューション エージェントを実行する Windows 資格情報 **@job_name** と **@job_password**, 、およびこのエージェント ジョブのスケジュール。 詳しくは、「 [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md)」をご覧ください。 実行後にこれは、 [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)します。 詳しくは、「 [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md)」をご覧ください。  
  
### マージ パブリケーションを構成するスクリプトをアップグレードするには  
  
1.  (省略可能)既存のスクリプトでの実行を更新 [sp_addmergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) 新しいレプリケーション機能を実装するパラメーターの既定以外の値を設定します。  
  
2.  後に [sp_addmergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), 、実行 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 指定 **@publication** とスナップショット エージェントを実行する Windows 資格情報 **@job_name** と **@job_password**します。 エージェントが使用する場合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャーに接続するときに、認証の値も指定する必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。  
  
3.  (省略可能)更新の実行 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) 新しいレプリケーション機能を実装するパラメーターの既定以外の値を設定します。  
  
### マージ パブリケーションにサブスクリプションを追加するスクリプトをアップグレードするには  
  
1.  サブスクリプションを作成するストアド プロシージャを実行した後、マージ エージェント ジョブを作成するストアド プロシージャを実行して、サブスクリプションを同期するようにしてください。 使用するストアド プロシージャは、サブスクリプションの種類に応じて変わります。  
  
    -   プル サブスクリプションの更新の実行 [sp_addmergepullsubscription_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) マージ エージェントでは、サブスクライバーで実行する Windows 資格情報を提供する **@job_name** と **@job_password**します。 実行後にこれは、 [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)します。 詳細については、「 [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
    -   プッシュ サブスクリプションでは、実行 [sp_addmergepushsubscription_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) パブリッシャーです。 指定 **@subscriber**, 、**@subscriber_db**, 、**@publication**, 、ディストリビューターでマージ エージェントを実行する Windows 資格情報 **@job_name** と **@job_password**, 、およびこのエージェント ジョブのスケジュール。 詳しくは、「 [Specify Synchronization Schedules](../../../relational-databases/replication/specify-synchronization-schedules.md)」をご覧ください。 実行後にこれは、 [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)します。 詳しくは、「 [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md)」をご覧ください。  
  
## 例  
 次に、Product テーブルに関するトランザクション パブリケーションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 このパブリケーションでは、フェールオーバーとしてキュー更新を使用する即時更新がサポートされます。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createtranpub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_1.sql)]  
  
## 例  
 次に、トランザクション パブリケーションを作成する古いスクリプトをアップグレードする例を示します。これは [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 このパブリケーションでは、フェールオーバーとしてキュー更新を使用する即時更新がサポートされます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報が使用して、ランタイムで提供されている **sqlcmd** スクリプト変数です。  
  
 [!code-sql[HowTo#sp_createtranpub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_2.sql)]  
  
## 例  
 次に、Customers テーブルに関するマージ パブリケーションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createmergepub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_3.sql)]  
  
## 例  
 次に、マージ パブリケーションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報が使用して、ランタイムで提供されている **sqlcmd** スクリプト変数です。  
  
 [!code-sql[HowTo#sp_createmergepub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_4.sql)]  
  
## 例  
 次に、トランザクション パブリケーションへのプッシュ サブスクリプションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_5.sql)]  
  
## 例  
 次に、トランザクション パブリケーションへのプッシュ サブスクリプションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報が使用して、ランタイムで提供されている **sqlcmd** スクリプト変数です。  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_6.sql)]  
  
## 例  
 次に、マージ パブリケーションへのプッシュ サブスクリプションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_7.sql)]  
  
## 例  
 次に、マージ パブリケーションへのプッシュ サブスクリプションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報が使用して、ランタイムで提供されている **sqlcmd** スクリプト変数です。  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_8.sql)]  
  
## 例  
 次に、トランザクション パブリケーションへのプル サブスクリプションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_7.sql)]  
  
## 例  
 次に、トランザクション パブリケーションへのプル サブスクリプションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報が使用して、ランタイムで提供されている **sqlcmd** スクリプト変数です。  
  
 [!code-sql[HowTo#sp_createtranpullsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_9.sql)]  
  
## 例  
 次に、マージ パブリケーションへのプル サブスクリプションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpreupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_10.sql)]  
  
## 例  
 次に、マージ パブリケーションへのプル サブスクリプションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報が使用して、ランタイムで提供されている **sqlcmd** スクリプト変数です。  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpostupgrade](../../../relational-databases/replication/codesnippet/tsql/upgrade-replication-scri_11.sql)]  
  
## 参照  
 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Push Subscription](../../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md)   
 [View and Modify Replication Security Settings](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [MSSQL_ENG021797](../../../relational-databases/replication/mssql-eng021797.md)   
 [MSSQL_ENG021798](../../../relational-databases/replication/mssql-eng021798.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [レプリケートされたデータベースのアップグレード](../../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  