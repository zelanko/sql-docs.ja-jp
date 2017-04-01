---
title: "ディストリビューターとパブリッシャーのプロパティの表示および変更 | Microsoft Docs"
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
  - "viewing replication properties"
  - "Distributors [SQL Server replication], modifying"
  - "modifying replication properties, Distributors"
  - "ディストリビューター [SQL Server レプリケーション]、プロパティ"
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# ディストリビューターとパブリッシャーのプロパティの表示および変更
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、ディストリビューターとパブリッシャーのプロパティを表示および変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
     [セキュリティ](#Security)  
  
-   **ディストリビューターとパブリッシャーのプロパティを表示または変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-    [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]より前のバージョンのパブリッシャーでは、固定サーバー ロール **sysadmin** のユーザーが、 **[サブスクライバー]** ページでサブスクライバーを登録できます。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降では、サブスクライバーをレプリケーションに明示的に登録する必要はありません。  
  
###  <a name="Security"></a> セキュリティ  
 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### ディストリビューターのプロパティを表示および変更するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  右クリックし、 **レプリケーション** フォルダー、およびクリック **ディストリビューターのプロパティ**します。  
  
3.  プロパティで表示して、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックス。  
  
    -   表示し、ディストリビューション データベースのプロパティを変更、プロパティ ボタンをクリックします (**...**) 上のデータベースに対して、 **全般** ダイアログ ボックスのページです。  
  
    -   表示し、ディストリビューターに関連付けられているパブリッシャーのプロパティを変更、プロパティ ボタンをクリックします (**...**) パブリッシャー側での **パブリッシャー** ] ダイアログ ボックスのページです。  
  
    -   レプリケーション エージェントのプロファイルにアクセスするには、ダイアログ ボックスの **[全般]** ページの **[プロファイルの既定値]** をクリックします。 詳しくは、「 [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md)」をご覧ください。  
  
    -   パブリッシャーで管理用のストアド プロシージャを実行したり、ディストリビューターで情報を更新したりするときに使用するアカウントのパスワードを変更するには、ダイアログ ボックスの **[パブリッシャー]** ページで **[パスワード]** ボックスおよび **[パスワードの確認入力]** ボックスに新しいパスワードを入力します。 詳細については、次を参照してください。 [ディストリビューターのセキュリティ保護](../../relational-databases/replication/security/secure-the-distributor.md)します。  
  
4.  必要に応じてプロパティを変更し、 **[OK]**をクリックします。  
  
#### パブリッシャーのプロパティを表示および変更するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  右クリックし、 **レプリケーション** フォルダー、およびクリック **パブリッシャーのプロパティ**します。  
  
3.  プロパティで表示して、 **パブリッシャーのプロパティ - \< Publisher >** ] ダイアログ ボックス。  
  
    -   固定サーバー ロール **sysadmin** のユーザーは、 **[パブリケーション データベース]** のページでデータベースのレプリケーションを有効化できます。 データベースを有効にするがそのデータベースは公開されません。任意のユーザーを代わりに、これにより、 **db_owner** 、データベースに 1 つまたは複数のパブリケーションを作成するには、そのデータベースの固定データベース ロール。  
  
4.  必要に応じてプロパティを変更し、 **[OK]**をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 パブリッシャーとディストリビューターのプロパティは、プログラムからレプリケーション ストアド プロシージャを使用して表示できます。  
  
#### ディストリビューターとディストリビューション データベースのプロパティを表示するには  
  
1.  実行 [sp_helpdistributor](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md) ディストリビューター、ディストリビューション データベース、および作業ディレクトリに関する情報を返します。  
  
2.  実行 [sp_helpdistributiondb](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md) 指定されたディストリビューション データベースのプロパティを返します。  
  
#### ディストリビューターとディストリビューション データベースのプロパティを変更するには  
  
1.  ディストリビューターで実行 [sp_changedistributor_property](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md) ディストリビューターのプロパティを変更します。  
  
2.  ディストリビューターで実行 [sp_changedistributiondb](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md) をディストリビューション データベースのプロパティを変更します。  
  
3.  ディストリビューターで実行 [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md) ディストリビューターのパスワードを変更します。  
  
    > [!IMPORTANT]  
    >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報をスクリプト ファイルに含める必要がある場合は、不正なアクセスが行われないようにファイルをセキュリティで保護してください。  
  
4.  ディストリビューターで実行 [sp_changedistpublisher](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md) ディストリビューターを使用するパブリッシャーのプロパティを変更します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトによってディストリビューターおよびディストリビューション データベースに関する情報を返します。  
  
 [!code-sql[HowTo#sp_helpdistributor](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_1.sql)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_2.sql)]  
  
 次の例では、ディストリビューターの保有期間、ディストリビューターへの接続時に使用されるパスワード、およびディストリビューターが各種レプリケーション エージェントの状態を確認する間隔 (ハートビート間隔) を変更します。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報をスクリプト ファイルに含める必要がある場合は、不正なアクセスが行われないようにファイルをセキュリティで保護してください。  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_3.sql)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_4.sql)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../relational-databases/replication/codesnippet/tsql/view-and-modify-distribu_5.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
  
#### ディストリビューターのプロパティを表示および変更するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスです。 渡す、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1 のオブジェクト。  
  
3.  (省略可能)チェック、 <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> プロパティを現在接続しているサーバーがディストリビューターであることを確認します。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> サーバーからプロパティを取得します。  
  
5.  (省略可能)プロパティを変更するには、ディストリビューターのプロパティで設定できるは 1 つ以上の新しい値を設定、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> オブジェクトです。  
  
6.  (省略可能)場合、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationServer> にオブジェクトが設定されている **true**, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドをサーバーに変更をコミットします。  
  
#### ディストリビューション データベースのプロパティを表示および変更するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> クラスです。 Name プロパティを指定して渡す、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1 のオブジェクト。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> サーバーからプロパティを取得します。 このメソッドから **false**が返された場合、指定した名前のデータベースはサーバー上に存在しません。  
  
4.  (省略可能)プロパティを変更するには、いずれかの新しい値を設定、 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> プロパティを設定できます。  
  
5.  (省略可能)場合、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> プロパティを <xref:Microsoft.SqlServer.Replication.DistributionDatabase> にオブジェクトが設定されている **true**, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドをサーバーに変更をコミットします。  
  
#### パブリッシャーのプロパティを表示および変更するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> クラスです。 指定、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> プロパティとパス、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1 のオブジェクト。  
  
3.  (省略可能)プロパティを変更するには、いずれかの新しい値を設定、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> プロパティを設定できます。  
  
4.  (省略可能)場合、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> プロパティを <xref:Microsoft.SqlServer.Replication.DistributionPublisher> にオブジェクトが設定されている **true**, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドをサーバーに変更をコミットします。  
  
#### パブリッシャーからディストリビューターへの管理接続に使用されているパスワードを変更するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> オブジェクトのプロパティを取得します。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> メソッドです。 新しいパスワード値を *password* パラメーターに渡します。  
  
    > [!IMPORTANT]  
    >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&amp;amp;#xA0;Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../includes/msconame-md.md)] を使用します。  
  
6.  (省略可) このディストリビューターを使用している各リモート パブリッシャーでパスワードを変更するには、次の手順に従います。  
  
    1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
    2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスです。  
  
    3.  設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 6 a. で作成された接続。  
  
    4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> オブジェクトのプロパティを取得します。  
  
    5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> メソッドです。 手順 5. の新しいパスワード値を *password* パラメーターに渡します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例に、ディストリビューションのプロパティおよびディストリビューション データベースのプロパティを変更する方法を示します。  
  
> [!IMPORTANT]  
>  資格情報をコードに記述するのを避けるため、新しいディストリビューター パスワードは実行時に指定するようにしています。  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## 参照  
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [パブリッシングおよびディストリビューションの無効化](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [ディストリビューターおよびパブリッシャーの情報スクリプト](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [情報を表示し、パブリッシャーおよび #40; のタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
  
  