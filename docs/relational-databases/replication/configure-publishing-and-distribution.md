---
title: "パブリッシングおよびディストリビューションの構成 | Microsoft Docs"
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
  - "replication [SQL Server], distribution"
  - "distribution configuration [SQL Server replication]"
  - "パブリッシング [SQL Server レプリケーション], 構成"
ms.assetid: 3cfc8966-833e-42fa-80cb-09175d1feed7
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# パブリッシングおよびディストリビューションの構成
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリッシングとディストリビューションを構成する方法について説明します。  
  

##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> Security  
 詳細については、「[セキュリティで保護された配置 &#40;レプリケーション&#41;](../../relational-databases/replication/security/secure-deployment-replication.md)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードまたはディストリビューションの構成ウィザードを使用して、ディストリビューションを構成します。 ディストリビューターを構成したら、**[ディストリビューターのプロパティ - \<ディストリビューター>**] ダイアログ ボックスでプロパティを表示および変更します。 **db_owner** 固定データベース ロールのメンバーがパブリケーションを作成できるようにディストリビューターを構成する場合、またはパブリッシャーではないリモート ディストリビューターを構成する必要がある場合は、ディストリビューションの構成ウィザードを使用します。  
  
#### ディストリビューションを構成するには  
  
1.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、ディストリビューターとなるサーバーに接続し (多くの場合、パブリッシャーとディストリビューターは同じサーバーです)、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを右クリックし、**[ディストリビューションの構成]** をクリックします。  
  
3.  ディストリビューションの構成ウィザードに従って、次の操作を実行します。  
  
    -   ディストリビューターを選択します。 ローカル ディストリビューターを使用するには、**['\<ServerName>' を独自のディストリビューターとする (SQL Server はディストリビューション データベースとログを作成します)]** を選択します。 リモート ディストリビューターを使用するには、 **[以下のサーバーをディストリビューターとして使用する]**を選択し、サーバーを選択します。 このサーバーは既にディストリビューターとして構成されている必要があり、パブリッシャーではこのディストリビューターを使用できるようになっている必要があります。 詳細については、「[ディストリビューターでのリモート パブリッシャーの有効化 &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/enable-a-remote-publisher-at-a-distributor-sql-server-management-studio.md)」を参照してください。  
  
         リモート ディストリビューターを選択した場合、パブリッシャーからディストリビューターへの接続に対して、 **[管理パスワード]** ページでパスワードを入力する必要があります。 このパスワードは、リモート ディストリビューターでパブリッシャーを有効にしたときに指定したパスワードと一致する必要があります。  
  
    -   ローカル ディストリビューターに対してルート スナップショット フォルダーを指定します。 スナップショット フォルダーは、共有として指定したディレクトリです。このフォルダーの読み取りと書き込みをするエージェントには、このフォルダーへのアクセスを可能にする十分な権限が必要です。 このディストリビューターを使用する各パブリッシャーによって、ルート フォルダーの下にフォルダーが作成され、各パブリケーションでは、パブリッシャー フォルダーの下にスナップショット ファイルを格納するフォルダーが作成されます。 フォルダーの適切なセキュリティ保護の詳細については、「[スナップショット フォルダーのセキュリティ保護](../../relational-databases/replication/security/secure-the-snapshot-folder.md)」を参照してください。  
  
    -   ローカル ディストリビューターに対してディストリビューション データベースを指定します。 ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションに対するトランザクションが格納されます。  
  
    -   必要に応じて、その他のパブリッシャーでディストリビューターを使用できるようにします。 その他のパブリッシャーがディストリビューターを使用できるようになっている場合は、これらのパブリッシャーからディストリビューターへの接続に対して、 **[ディストリビューター パスワード]** ページでパスワードを入力する必要があります。  
  
    -   必要に応じて、構成の設定のスクリプトを作成します。 詳しくは、「 [Scripting Replication](../../relational-databases/replication/scripting-replication.md)」をご覧ください。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーションのパブリッシングおよびディストリビューションは、レプリケーションのストアド プロシージャを使用してプログラムから構成できます。  
  
#### ローカル ディストリビューターを使用してパブリッシングを構成するには  
  
1.  [sp_get_distributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-distributor-transact-sql.md) を実行して、サーバーが既にディストリビューターとして構成されているかどうかを調べます。  
  
    -   結果セットの **installed** の値が **0** の場合は、ディストリビューターの master データベースで [sp_adddistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) を実行します。  
  
    -   結果セットの **distribution db installed** の値が **0** の場合は、ディストリビューターの master データベースで [sp_adddistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) を実行します。 このとき、 **@database**に、ディストリビューション データベースの名前を指定します。 必要に応じて、トランザクションの最大保有期間 (**@max_distretention**) および履歴保有期間 (**@history_retention**) を指定することもできます。 新しいデータベースを作成する場合は、必要なデータベース プロパティのパラメーターを指定します。  
  
2.  ディストリビューター (兼パブリッシャー) で、 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md) を実行します。このとき、**@working_directory** には、既定のスナップショット フォルダーとして使用する UNC 共有を指定します。  
  
3.  パブリッシャーで、[sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) を実行します。 このとき、 **@dbname**にはパブリッシュするデータベースを、 **@optname**にはレプリケーションの種類を、 **@value** の値には **true**を指定します。  
  
#### リモート ディストリビューターを使用してパブリッシングを構成するには  
  
1.  [sp_get_distributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-distributor-transact-sql.md) を実行して、サーバーが既にディストリビューターとして構成されているかどうかを調べます。  
  
    -   結果セットの **installed** の値が **0** の場合は、ディストリビューターの master データベースで [sp_adddistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) を実行します。 **@password**には強力なパスワードを指定してください。 この **distributor_admin** アカウントのパスワードは、パブリッシャーがディストリビューターに接続する際に使用されます。  
  
    -   結果セットの **distribution db installed** の値が **0** の場合は、ディストリビューターの master データベースで [sp_adddistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) を実行します。 このとき、 **@database**に、ディストリビューション データベースの名前を指定します。 必要に応じて、トランザクションの最大保有期間 (**@max_distretention**) および履歴保有期間 (**@history_retention**) を指定することもできます。 新しいデータベースを作成する場合は、必要なデータベース プロパティのパラメーターを指定します。  
  
2.  ディストリビューターで、[sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md) を実行します。このとき、**@working_directory** には、既定のスナップショット フォルダーとして使用する UNC 共有を指定します。 ディストリビューターがパブリッシャーに接続する際に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合、さらに **@security_mode** に **0** を指定し、 **@login** と **@password** に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン情報を指定する必要があります。  
  
3.  パブリッシャーの master データベースで [sp_adddistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) を実行します。 **@password**には、手順 1. で使用した強力なパスワードを指定してください。 このパスワードは、パブリッシャーがディストリビューターに接続する際に使用されます。  
  
4.  パブリッシャーで、[sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) を実行します。 このとき、 **@dbname**にはパブリッシュするデータベースを、 **@optname**にはレプリケーションの種類を、 **@value**の値には true を指定します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例に、パブリッシングおよびディストリビューションをプログラムから構成する方法を示します。 この例では、パブリッシャーおよびローカル ディストリビューターとして構成するサーバーの名前をスクリプト変数を使って指定しています。 レプリケーションのパブリッシングおよびディストリビューションは、レプリケーションのストアド プロシージャを使用してプログラムから構成できます。  
  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/configure-publishing-and_1.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
  
#### パブリッシングおよびディストリビューションを単一サーバーで構成するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サーバーへの接続を作成します。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスです。 手順 1 から <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を渡します。  
  
3.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> クラスです。  
  
4.  設定、 <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> プロパティにデータベース名を設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. のです。  
  
5.  呼び出してディストリビューターをインストール、 <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> メソッドです。 渡す、 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 手順 3 からのオブジェクト。  
  
6.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> クラスです。  
  
7.  次のプロパティの設定 <xref:Microsoft.SqlServer.Replication.DistributionPublisher>:  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> - パブリッシャーの名前。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. のです。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> -手順 5. で作成したデータベースの名前。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> -スナップショット ファイルのアクセスに使用される共有します。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> -パブリッシャーへの接続時に使用するセキュリティ モード。 [<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> をお勧めします。  
  
8.  呼び出す、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> メソッドです。  
  
#### リモート ディストリビューターを使用してパブリッシングおよびディストリビューションを構成するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection>クラスを使用して、リモート ディストリビューター サーバーへの接続を作成します。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスです。 手順 1 から <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を渡します。  
  
3.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> クラスです。  
  
4.  設定、 <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> プロパティを設定し、データベース名、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. のです。  
  
5.  呼び出してディストリビューターをインストール、 <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> メソッドです。 セキュリティで保護されたパスワード (リモート ディストリビューターに接続するときは、パブリッシャーによって使用される) を指定し、 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 手順 3 からオブジェクトです。 詳細については、「[ディストリビューターのセキュリティ保護](../../relational-databases/replication/security/secure-the-distributor.md)」を参照してください。  
  
    > **重要!!** 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&amp;amp;#xA0;Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../includes/msconame-md.md)] を使用します。  
  
6.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> クラスです。  
  
7.  次のプロパティの設定 <xref:Microsoft.SqlServer.Replication.DistributionPublisher>:  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> - ローカル パブリッシャー サーバーの名前。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. のです。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> -手順 5. で作成したデータベースの名前。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> -スナップショット ファイルのアクセスに使用される共有します。  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> -パブリッシャーへの接続時に使用するセキュリティ モード。 [<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> をお勧めします。  
  
8.  呼び出す、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> メソッドです。  
  
9. <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ローカル パブリッシャー サーバーへの接続を作成します。  
  
10. インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスです。 手順 9 の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を渡します。  
  
11. 呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> メソッドです。 リモート ディストリビューターの名前、および手順 5. で指定したリモート ディストリビューターのパスワードを渡します。  
  
    > **重要!!**  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、Windows .NET Framework に用意されている [暗号化サービス](http://go.microsoft.com/fwlink/?LinkId=34733) を使用します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってレプリケーション パブリッシングおよびディストリビューションを構成できます。  
  
 [!code-csharp[HowTo#rmo_AddDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_adddistpub)]  
  
 [!code-vb[HowTo#rmo_vb_AddDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_adddistpub)]  
  
## 参照  
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Always On 可用性グループ用のレプリケーションの構成 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/configure-replication-for-always-on-availability-groups-sql-server.md)  
  
  