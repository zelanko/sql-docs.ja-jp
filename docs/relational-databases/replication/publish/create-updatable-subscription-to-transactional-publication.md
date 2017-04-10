---
title: "Transact-SQL を使用してトランザクション パブリケーションに対する更新可能なサブスクリプションを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "07/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "更新可能なトランザクション サブスクリプション、T-SQL"
ms.assetid: a6e80857-0a69-4867-b6b7-f3629d00c312
caps.latest.revision: 6
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 6
---
# Transact-SQL を使用してトランザクション パブリケーションに対する更新可能なサブスクリプションを作成する

> [!NOTE]  
>  この機能は、[!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)] 2012 から 2016 のバージョンでサポートされています。  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
トランザクション レプリケーションは、即時更新サブスクリプションまたはキュー更新サブスクリプションを使用して、サブスクライバーでの変更がパブリッシャーに反映されるようにします。 レプリケーション ストアド プロシージャを使用して、更新サブスクリプションをプログラムで作成できます。 (「[トランザクション パブリケーションに対して更新可能なサブスクリプションを作成する (Management Studio)](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md)」も参照してください)。 

## 即時更新プル サブスクリプションを作成するには ##

1. パブリッシャーで、[sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) を実行することにより、パブリケーションが即時更新サブスクリプションをサポートしていることを確認します。 

    * 結果セットの `allow_sync_tran` の値が `1` である場合、パブリケーションは即時更新サブスクリプションをサポートします。

    * 結果セットの `allow_sync_tran` の値が `0` である場合は、即時更新サブスクリプションを有効にしてパブリケーションを再作成する必要があります。

2. パブリッシャーで、[sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) を実行することにより、パブリケーションがプル サブスクリプションをサポートしていることを確認します。 

    * 結果セットの `allow_pull` の値が `1` である場合、パブリケーションはプル サブスクリプションをサポートします。

    * `allow_pull` の値が `0` である場合、`@property` には `allow_pull`、`@value` には `true` を指定して [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) を実行します。 

3. サブスクライバーで、[sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md) を実行します。 `@publisher` と `@publication` を指定し、`@update_mode` に次のいずれかの値を指定します。

    * `sync tran` - サブスクリプションの即時更新を有効にします。

    * `failover` キュー更新をフェールオーバー オプションとするサブスクリプションの即時更新を有効にします。

    > [!NOTE]  
>  `failover` では、パブリケーションでもキュー更新サブスクリプションが有効になっていることが必要です。 
 
4. サブスクライバーで、[sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) を実行します。 次の指定を行います。

    * `@publisher`、`@publisher_db`、および `@publication` パラメーター。 

    * `@job_login` および `@job_password` に、サブスクライバーでディストリビューション エージェントを実行するときに使用する Microsoft Windows 資格情報。 

    > [!NOTE]  
>  Windows 統合認証を使用して作成された接続では、常に、`@job_login` および `@job_password` で指定された Windows 資格情報が使用されます。 ディストリビューション エージェントは、常に Windows 統合認証を使用してサブスクライバーへのローカル接続を作成します。 既定では、エージェントは Windows 統合認証を使用してディストリビューターに接続します。 
 
    * (省略可能) ディストリビューターに接続するときに SQL Server 認証を使用する必要がある場合、`@distributor_security_mode` には `0`、`@distributor_login` と `@distributor_password` には Microsoft SQL Server ログイン情報の値。 

    * このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。 

5. サブスクライバー側のサブスクリプション データベースに対して、[sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) を実行します。 `@publisher`、`@publication`、`@publisher_db` のパブリケーション データベース名、および `@security_mode` の次のいずれかの値を指定します。 

    * `0` - パブリッシャーで更新を作成する場合に SQL Server 認証を使用します。 このオプションの場合、パブリッシャーで、`@login` および `@password` に有効なログインを指定する必要があります。

    * `1` - パブリッシャーへの接続時にサブスクライバーで変更するユーザーのセキュリティ コンテキストを使用します。 このセキュリティ モードに関連する制限の詳細については、[sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) のトピックを参照してください。

    * `2` - [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) を使って作成された、既存のユーザー定義リンク サーバー ログインを使用します。

6. パブリッシャーで、`@publication`、`@subscriber`、`@destination_db`、`@subscription_type` のプル値、`@update_mode` の手順 3 で指定したものと同じ値を指定し、[sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) を実行します。

これにより、パブリッシャーでプル サブスクリプションが登録されます。 


## 即時更新プッシュ サブスクリプションを作成するには ##

1. パブリッシャーで、[sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) を実行することにより、パブリケーションが即時更新サブスクリプションをサポートしていることを確認します。 

    * 結果セットの `allow_sync_tran` の値が `1` である場合、パブリケーションは即時更新サブスクリプションをサポートします。

    * 結果セットの `allow_sync_tran` の値が `0` である場合は、即時更新サブスクリプションを有効にしてパブリケーションを再作成する必要があります。

2. パブリッシャーで、[sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) を実行することにより、パブリケーションがプッシュ サブスクリプションをサポートしていることを確認します。 

    * 結果セットの `allow_push` の値が `1` である場合、パブリケーションはプッシュ サブスクリプションをサポートします。

    * `allow_push` の値が `0` である場合、`@property` には `allow_push`、`@value` には `true` を指定して [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) を実行します。 

3. パブリッシャーで、[sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) を実行します。 `@publication`、`@subscriber`、`@destination_db` を指定し、`@update_mode` に次のいずれかの値を指定します。

    * `sync tran` - 即時更新のサポートを有効にします。

    * `failover` - キュー更新をフェールオーバー オプションとする即時更新のサポートを有効にします。

    > [!NOTE]  
>  `failover` では、パブリケーションでもキュー更新サブスクリプションが有効になっていることが必要です。 
 
4. パブリッシャーで、[sp_addpushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) を実行します。 次のパラメーターを指定します。

    * `@subscriber`、`@subscriber_db`、および `@publication`。 

    * `@job_login` および `@job_password` のディストリビューターでディストリビューション エージェントを実行する際に使用する Windows 資格情報。 

    > [!NOTE]  
>  Windows 統合認証を使用して作成された接続では、常に、`@job_login` および `@job_password` で指定された Windows 資格情報が使用されます。 ディストリビューション エージェントは、常に Windows 統合認証を使用してディストリビューターにローカル接続します。 既定では、エージェントは Windows 統合認証を使用してサブスクライバーに接続します。 

    * (省略可能) サブスクライバーに接続するときに SQL Server 認証を使用する必要がある場合、`@subscriber_security_mode` には `0`、`@subscriber_login` と `@subscriber_password` には SQL Server ログイン情報の値。 

    * このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。

5. サブスクライバー側のサブスクリプション データベースに対して、[sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) を実行します。 `@publisher`、`@publication`、`@publisher_db` のパブリケーション データベース名、および `@security_mode` の次のいずれかの値を指定します。 

     * `0` - パブリッシャーで更新を作成する場合に SQL Server 認証を使用します。 このオプションの場合、パブリッシャーで、`@login` および `@password` に有効なログインを指定する必要があります。

     * `1` - パブリッシャーへの接続時にサブスクライバーで変更するユーザーのセキュリティ コンテキストを使用します。 このセキュリティ モードに関連する制限の詳細については、[sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) のトピックを参照してください。

     * `2` - [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) を使って作成された、既存のユーザー定義リンク サーバー ログインを使用します。


## キュー更新プル サブスクリプションを作成するには ##

1. パブリッシャーで、[sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) を実行することにより、パブリケーションがキュー更新サブスクリプションをサポートしていることを確認します。 

    * 結果セットの `allow_queued_tran` の値が `1` である場合、パブリケーションは即時更新サブスクリプションをサポートします。

    * 結果セットの `allow_queued_tran` の値が `0` である場合は、キュー更新サブスクリプションを有効にしてパブリケーションを再作成する必要があります。

2. パブリッシャーで、[sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) を実行することにより、パブリケーションがプル サブスクリプションをサポートしていることを確認します。 

    * 結果セットの `allow_pull` の値が `1` である場合、パブリケーションはプル サブスクリプションをサポートします。

    * `allow_pull` の値が `0` である場合、`@property` には `allow_pull`、`@value` には `true` を指定して [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) を実行します。 

3. サブスクライバーで、[sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md) を実行します。 `@publisher` と `@publication` を指定し、`@update_mode` に次のいずれかの値を指定します。

    * `queued tran` - サブスクリプションのキュー更新を有効にします。

    * `queued failover` - 即時更新をフェールオーバー オプションとするキュー更新のサポートを有効にします。

    > [!NOTE]  
>  `queued failover` では、パブリケーションでも即時更新サブスクリプションが有効になっていることが必要です。 即時更新へのフェールオーバーを行うために、[sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) を使って、サブスクライバーでの変更をパブリッシャーにレプリケートするときに使用する資格情報を定義する必要があります。
 
4. サブスクライバーで、[sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) を実行します。 次のパラメーターを指定します。

    * @publisher、`@publisher_db`、`@publication`。 

    * `@job_login` および `@job_password` に、サブスクライバーでディストリビューション エージェントを実行するときに使用する Windows 資格情報。 

    > [!NOTE]  
>  Windows 統合認証を使用して作成された接続では、常に、`@job_login` および `@job_password` で指定された Windows 資格情報が使用されます。 ディストリビューション エージェントは、常に Windows 統合認証を使用してサブスクライバーへのローカル接続を作成します。 既定では、エージェントは Windows 統合認証を使用してディストリビューターに接続します。 
 
    * (省略可能) ディストリビューターに接続するときに SQL Server 認証を使用する必要がある場合、`@distributor_security_mode` には `0`、`@distributor_login` と `@distributor_password` には SQL Server ログイン情報の値。 

    * このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。

5. パブリッシャーで、`@publication`、`@subscriber`、`@destination_db`、`@subscription_type` のプル値、`@update_mode` の手順 3 で指定したものと同じ値を指定して [sp_addsubscriber](../../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md) を実行し、パブリッシャーにサブスクライバーを登録します。

これにより、パブリッシャーでプル サブスクリプションが登録されます。 


## キュー更新プッシュ サブスクリプションを作成するには ##

1. パブリッシャーで、[sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) を実行することにより、パブリケーションがキュー更新サブスクリプションをサポートしていることを確認します。 

    * 結果セットの allow_queued_tran の値が 1 である場合、パブリケーションは即時更新サブスクリプションをサポートします。

    * 結果セットの allow_queued_tran の値が 0 である場合は、キュー更新サブスクリプションを有効にしてパブリケーションを再作成する必要があります。 詳細については、「トランザクション パブリケーションに対するサブスクリプションの更新を有効にする方法 (レプリケーション Transact-SQL プログラミング)」を参照してください。

2. パブリッシャーで、[sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) を実行することにより、パブリケーションがプッシュ サブスクリプションをサポートしていることを確認します。 

    * 結果セットの `allow_push` の値が `1` である場合、パブリケーションはプッシュ サブスクリプションをサポートします。

    * `allow_push` の値が `0` である場合、`@property` には allow_push、`@value` には `true` を指定して [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) を実行します。 

3. パブリッシャーで、[sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) を実行します。 `@publication`、`@subscriber`、`@destination_db` を指定し、`@update_mode` に次のいずれかの値を指定します。

    * `queued tran` - サブスクリプションのキュー更新を有効にします。

    * `queued failover` - 即時更新をフェールオーバー オプションとするキュー更新のサポートを有効にします。

    > [!NOTE]  
>  queued failover オプションでは、パブリケーションでも即時更新サブスクリプションが有効になっていることが必要です。 即時更新へのフェールオーバーを行うために、[sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) を使って、サブスクライバーでの変更をパブリッシャーにレプリケートするときに使用する資格情報を定義する必要があります。

4. パブリッシャーで、[sp_addpushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md) を実行します。 次のパラメーターを指定します。

    * `@subscriber`、`@subscriber_db`、および `@publication`。 

    * `@job_login` および `@job_password` のディストリビューターでディストリビューション エージェントを実行する際に使用する Windows 資格情報。 

    > [!NOTE]  
>  Windows 統合認証を使用して作成された接続では、常に、`@job_login` および `@job_password` で指定された Windows 資格情報が使用されます。 ディストリビューション エージェントは、常に Windows 統合認証を使用してディストリビューターにローカル接続します。 既定では、エージェントは Windows 統合認証を使用してサブスクライバーに接続します。 
 
    * (省略可能) サブスクライバーに接続するときに SQL Server 認証を使用する必要がある場合、`@subscriber_security_mode` には `0`、`@subscriber_login` と `@subscriber_password` には SQL Server ログイン情報の値。 

    * このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。


## 例 ##

この例では、即時更新サブスクリプションをサポートするパブリケーションに対する即時更新プル サブスクリプションを作成します。 ログインとパスワードの値は、実行時に sqlcmd スクリプト変数を使用して入力されます。

> [!NOTE]  
>  このスクリプトでは sqlcmd スクリプト変数を使用します。 `$(MyVariable)` という形式です。 コマンド ラインと SQL Server Management Studio でスクリプト変数を使用する方法については、「[レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)」トピックの「**レプリケーション スクリプトの実行**」セクションを参照してください。

```
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## 参照 ##

[Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)

[sqlcmd でのスクリプト変数の使用](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)

[トランザクション パブリケーションに対して更新可能なサブスクリプションを作成する (Management Studio)](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md)
