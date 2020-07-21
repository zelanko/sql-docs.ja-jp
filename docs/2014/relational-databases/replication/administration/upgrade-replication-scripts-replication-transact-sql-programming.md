---
title: レプリケーション スクリプトのアップグレード (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- scripts [SQL Server replication], upgrading
- upgrading SQL Server, replicated databases
- upgrading replication applications
- replication [SQL Server], scripting
- replication [SQL Server], upgrading
- upgrading replicated databases
ms.assetid: 0b8720bd-f339-4842-bc8f-b35a46f6d3ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c47101c76ca2c585accd493b74f0e59c56bf009e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055750"
---
# <a name="upgrade-replication-scripts-replication-transact-sql-programming"></a>レプリケーション スクリプトのアップグレード (レプリケーション Transact-SQL プログラミング)
  [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプト ファイルを使用して、レプリケーション トポロジをプログラムで構成できます。 詳細については、「[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)」 (レプリケーション システム ストアド プロシージャの概念) を参照してください。  
  
> [!IMPORTANT]  
>  `sysadmin` ロールのメンバーが実行するスクリプトについては、アップグレードは必須ではありませんが、このトピックの説明に従って既存のスクリプトを変更することをお勧めします。 「 [Replication Agent Security Model](../security/replication-agent-security-model.md)」の「エージェントに必要な権限」に記載されている各レプリケーション エージェントの最小権限を持つアカウントを指定します。  
  
 このようにセキュリティが強化されたことで、レプリケーション エージェント ジョブの実行に使用される [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows アカウントを明示的に指定できるため、権限をより詳細に設定できます。既存のスクリプトに含まれる次のストアド プロシージャは、このセキュリティ強化の影響を受けます。  
  
-   **sp_addpublication_snapshot**:  
  
     次に、Windows 資格情報をとして指定し **@job_login** **@job_password** [sp_addpublication_snapshot &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql)を実行して、ディストリビューターでスナップショットエージェントを実行するジョブを作成する必要があります。  
  
-   **sp_addpushsubscription_agent**:  
  
     [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql) を実行して、ジョブを明示的に追加し、ディストリビューション エージェント ジョブをディストリビューターで実行するときに Windows 資格情報 (**@job_login** および **@job_password**) を指定することが必要になりました。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]では、プッシュ サブスクリプションが作成されるときにこの操作が自動的に実行されました。  
  
-   **sp_addmergepushsubscription_agent**:  
  
     [sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql) を実行して、ジョブを明示的に追加し、マージ エージェント ジョブをディストリビューターで実行するときに Windows 資格情報 (**@job_login** および **@job_password**) を指定することが必要になりました。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]では、プッシュ サブスクリプションが作成されるときにこの操作が自動的に実行されました。  
  
-   **sp_addpullsubscription_agent**:  
  
     次に、Windows 資格情報をとして指定し **@job_login** **@job_password** [sp_addpullsubscription_agent &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)を実行して、サブスクライバーでディストリビューションエージェントを実行するジョブを作成する必要があります。  
  
-   **sp_addmergepullsubscription_agent**:  
  
     次に、Windows 資格情報をとして指定し **@job_login** **@job_password** [sp_addmergepullsubscription_agent &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)を実行して、サブスクライバーでマージエージェントを実行するジョブを作成する必要があります。  
  
-   **sp_addlogreader_agent**:  
  
     [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) を実行して、ジョブを手動で追加し、ログ リーダー エージェントをディストリビューターで実行するときに使用する Windows 資格情報を入力することが必要になりました。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]では、トランザクション パブリケーションが作成されるときにこの操作が自動的に実行されました。  
  
-   **sp_addqreader_agent**:  
  
     [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) を実行して、ジョブを手動で追加し、キュー リーダー エージェントをディストリビューターで実行するときに使用する Windows 資格情報を入力することが必要になりました。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]では、キュー更新をサポートするトランザクション パブリケーションが作成されるときにこの操作が自動的に実行されました。  
  
 で導入されたセキュリティモデルでは、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] レプリケーションエージェントは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] およびで指定された資格情報を使用して、Windows 認証を使用してのローカルインスタンスに常に接続し **@job_name** **@job_password** ます。 レプリケーション エージェント ジョブを実行する際に使用する Windows アカウントの要件の詳細については、「 [Replication Agent Security Model](../security/replication-agent-security-model.md)」を参照してください。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納した場合は、ファイル自体が暗号化されていることを確認してください。  
  
### <a name="to-upgrade-scripts-that-configure-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションを構成するスクリプトをアップグレードするには  
  
1.  既存のスクリプトで、[sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) の前に、パブリッシャー側のパブリケーション データベースに [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) を実行します。 とのログリーダーエージェントを実行するときに使用する Windows 資格情報を指定し **@job_name** **@job_password** ます。 エージェントがパブリッシャーに接続する際に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用する場合、さらに **@publisher_security_mode** @allow_subscriber_initiated_snapshot **@publisher_security_mode** に指定し、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と **@publisher_login** と **@publisher_password**」をご覧ください。 これにより、パブリケーション データベース用のログ リーダー エージェント ジョブが作成されます。  
  
    > [!NOTE]  
    >  この手順はトランザクション パブリケーションにのみ適用されます。スナップショット パブリケーションの場合は不要です。  
  
2.  (省略可能) [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) の前に、ディストリビューター側のディストリビューション データベースに [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) を実行します。 とのキューリーダーエージェントを実行するときに使用する Windows 資格情報を指定し **@job_name** **@job_password** ます。 これにより、ディストリビューター用のキュー リーダー エージェント ジョブが作成されます。  
  
    > [!NOTE]  
    >  この手順は、キュー更新サブスクライバーをサポートするトランザクション パブリケーションでのみ必要です。  
  
3.  (省略可) [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) の実行を更新して、新しいレプリケーション機能を実装するパラメーターに既定以外の値を設定します。  
  
4.  パブリッシャー側のパブリケーション データベースに対して、[sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) の後に、[sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) を実行します。 **@publication**とにスナップショットエージェントを実行するときに使用する Windows 資格情報を指定し **@job_name** **@job_password** ます。 エージェントがパブリッシャーに接続する際に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用する場合、さらに **@publisher_security_mode** @allow_subscriber_initiated_snapshot **@publisher_security_mode** に指定し、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と **@publisher_login** と **@publisher_password**」をご覧ください。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。  
  
5.  (省略可) [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) の実行を更新して、新しいレプリケーション機能を実装するパラメーターに既定以外の値を設定します。  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションにサブスクリプションを追加するスクリプトをアップグレードするには  
  
1.  サブスクリプションを作成するストアド プロシージャを実行した後、ディストリビューション エージェント ジョブを作成するストアド プロシージャを実行して、サブスクリプションを同期するようにしてください。 使用するストアド プロシージャは、サブスクリプションの種類に応じて変わります。  
  
    -   プル サブスクリプションの場合、[sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) の実行を更新して、サブスクライバーでディストリビューション エージェントを実行するときの Windows 資格情報を **@job_name** と **@job_password** に指定します。 この操作は、 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)の実行後に行われます。 詳細については、「 [プル サブスクリプションの作成](../create-a-pull-subscription.md)」をご覧ください。  
  
    -   プッシュ サブスクリプションの場合、パブリッシャーで、[sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql) を実行します。 **@subscriber**、、 **@subscriber_db** **@publication** 、ディストリビューションエージェントをディストリビューターで実行するときに使用する Windows 資格情報 **@job_name** と、 **@job_password** このエージェントジョブのスケジュールを指定します。 詳細については、「[同期スケジュールの指定](../specify-synchronization-schedules.md)」を参照してください。 この操作は、 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)の実行後に行われます。 詳細については、「 [プッシュ サブスクリプションの作成](../create-a-push-subscription.md)」をご覧ください。  
  
### <a name="to-upgrade-scripts-that-configure-a-merge-publication"></a>マージ パブリケーションを構成するスクリプトをアップグレードするには  
  
1.  (省略可) 既存のスクリプトで、[sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) の実行を更新して、新しいレプリケーション機能を実装するパラメーターに既定以外の値を設定します。  
  
2.  パブリッシャー側のパブリケーション データベースに対して、[sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) の後に、[sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) を実行します。 **@publication**とにスナップショットエージェントを実行するときに使用する Windows 資格情報を指定し **@job_name** **@job_password** ます。 エージェントがパブリッシャーに接続する際に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用する場合、さらに **@publisher_security_mode** @allow_subscriber_initiated_snapshot **@publisher_security_mode** に指定し、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と **@publisher_login** と **@publisher_password**」をご覧ください。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。  
  
3.  (省略可) [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) の実行を更新して、新しいレプリケーション機能を実装するパラメーターに既定以外の値を設定します。  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-merge-publication"></a>マージ パブリケーションにサブスクリプションを追加するスクリプトをアップグレードするには  
  
1.  サブスクリプションを作成するストアド プロシージャを実行した後、マージ エージェント ジョブを作成するストアド プロシージャを実行して、サブスクリプションを同期するようにしてください。 使用するストアド プロシージャは、サブスクリプションの種類に応じて変わります。  
  
    -   プル サブスクリプションの場合、[sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql) の実行を更新して、サブスクライバーでマージ エージェントを実行するときの Windows 資格情報を **@job_name** と **@job_password** に指定します。 この操作は、 [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)の実行後に行われます。 詳細については、「 [プル サブスクリプションの作成](../create-a-pull-subscription.md)」をご覧ください。  
  
    -   プッシュ サブスクリプションの場合、パブリッシャーで、[sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql) を実行します。 、、を指定し、 **@subscriber** **@subscriber_db** **@publication** ディストリビューターでのマージエージェントの実行に使用する Windows 資格情報をおよびに指定し、 **@job_name** **@job_password** このエージェントジョブのスケジュールを指定します。 詳細については、「[同期スケジュールの指定](../specify-synchronization-schedules.md)」を参照してください。 この操作は、 [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql)の実行後に行われます。 詳細については、「 [プッシュ サブスクリプションの作成](../create-a-push-subscription.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次に、Product テーブルに関するトランザクション パブリケーションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 このパブリケーションでは、フェールオーバーとしてキュー更新を使用する即時更新がサポートされます。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createtranpub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpub80.sql#sp_createtranpub_nwpreupgrade)]  
  
## <a name="example"></a>例  
 次に、トランザクション パブリケーションを作成する古いスクリプトをアップグレードする例を示します。これは [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 このパブリケーションでは、フェールオーバーとしてキュー更新を使用する即時更新がサポートされます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報は、 **sqlcmd** スクリプト変数を使用して実行時に指定されます。  
  
 [!code-sql[HowTo#sp_createtranpub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpublication.sql#sp_createtranpub_nwpostupgrade)]  
  
## <a name="example"></a>例  
 次に、Customers テーブルに関するマージ パブリケーションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createmergepub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepub80.sql#sp_createmergepub_nwpreupgrade)]  
  
## <a name="example"></a>例  
 次に、マージ パブリケーションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報は、 **sqlcmd** スクリプト変数を使用して実行時に指定されます。  
  
 [!code-sql[HowTo#sp_createmergepub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepublication.sql#sp_createmergepub_nwpostupgrade)]  
  
## <a name="example"></a>例  
 次に、トランザクション パブリケーションへのプッシュ サブスクリプションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpushsub80.sql#sp_createtranpushsub_nwpreupgrade)]  
  
## <a name="example"></a>例  
 次に、トランザクション パブリケーションへのプッシュ サブスクリプションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報は、 **sqlcmd** スクリプト変数を使用して実行時に指定されます。  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpushsub.sql#sp_createtranpushsub_nwpostupgrade)]  
  
## <a name="example"></a>例  
 次に、マージ パブリケーションへのプッシュ サブスクリプションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepushsub80.sql#sp_createmergepushsub_nwpreupgrade)]  
  
## <a name="example"></a>例  
 次に、マージ パブリケーションへのプッシュ サブスクリプションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報は、 **sqlcmd** スクリプト変数を使用して実行時に指定されます。  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpushsub.sql#sp_createmergepushsub_nwpostupgrade)]  
  
## <a name="example"></a>例  
 次に、トランザクション パブリケーションへのプル サブスクリプションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepushsub80.sql#sp_createmergepushsub_nwpreupgrade)]  
  
## <a name="example"></a>例  
 次に、トランザクション パブリケーションへのプル サブスクリプションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報は、 **sqlcmd** スクリプト変数を使用して実行時に指定されます。  
  
 [!code-sql[HowTo#sp_createtranpullsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpullsub.sql#sp_createtranpullsub_nwpostupgrade)]  
  
## <a name="example"></a>例  
 次に、マージ パブリケーションへのプル サブスクリプションを作成する [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] スクリプトの例を示します。 読みやすくするために、既定のパラメーターは削除されています。  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepullsub80.sql#sp_createmergepullsub_nwpreupgrade)]  
  
## <a name="example"></a>例  
 次に、マージ パブリケーションへのプル サブスクリプションを作成する古いスクリプトの例を示します。アップグレードすることにより、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンで正常に実行されます。 新しいパラメーターの既定値は、明示的に宣言されています。  
  
> [!NOTE]  
>  Windows 資格情報は、 **sqlcmd** スクリプト変数を使用して実行時に指定されます。  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpullsub.sql#sp_createmergepullsub_nwpostupgrade)]  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../publish/create-a-publication.md)   
 [プッシュサブスクリプションを作成する](../create-a-push-subscription.md)   
 [Create a Pull Subscription](../create-a-pull-subscription.md)   
 [レプリケーションのセキュリティ設定を表示および変更する](../security/view-and-modify-replication-security-settings.md)   
 [MSSQL_ENG021797](../mssql-eng021797.md)   
 [MSSQL_ENG021798](../mssql-eng021798.md)   
 [レプリケーションシステムストアドプロシージャの概念](../concepts/replication-system-stored-procedures-concepts.md)   
 [レプリケートされたデータベースのアップグレード](../../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
