---
title: SQL Database Managed Instance でのレプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Database replication
- replication, SQL Database
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8dd8931bcc3fdaaa489d0a190c5ce1f6210e5f64
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088651"
---
# <a name="replication-with-sql-database-managed-instance"></a>SQL Database Managed Instance でのレプリケーション

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Azure SQL Database Managed Instance (プレビュー) では、トランザクション レプリケーションがサポートされます。 Managed Instance では、パブリッシャー、ディストリビューター、サブスクライバーのデータベースをホストできます。

## <a name="common-configurations"></a>一般的な構成

一般に、パブリッシャーとディストリビューターの両方が、クラウドまたはオンプレミスのいずれかに存在する必要があります。 サポートされている構成は次のとおりです。

- **マネージド インスタンス上のパブリッシャーとローカル ディストリビューター**

   ![Replication-with-azure-sql-db-single-managed-instance-publisher-distributor](./media/replication-with-sql-database-managed-instance/01-single-instance-asdbmi-pubdist.png)

   パブリッシャーとディストリビューターのデータベースが、1 つのマネージド インスタンス上で構成されています。

- **マネージド インスタンス上のパブリッシャーとリモート ディストリビューター**

   ![Replication-with-azure-sql-db-separate-managed-instances-publisher-distributor](./media/replication-with-sql-database-managed-instance/02-separate-instances-asdbmi-pubdist.png)

   パブリッシャーとディストリビューターが、2 つのマネージド インスタンス上で構成されています。 この構成は次のようになります。

  - 両方のマネージド インスタンスが同じ vNet 内にあります。

  - 両方のマネージド インスタンスが同じ場所にあります。

- **オンプレミスのパブリッシャーおよびディストリビューターとマネージド インスタンス上のサブスクライバー**

   ![Replication-from-on-premises-to-azure-sql-db-subscriber](./media/replication-with-sql-database-managed-instance/03-azure-sql-db-subscriber.png)

   この構成では、Azure SQL Database がサブスクライバーとなります。 この構成では、オンプレミスから Azure への移行がサポートされます。 サブスクライバーの役割においては SQL データベースにマネージド インスタンスは必要ありません。ただし、SQL Database Managed Instance を、オンプレミスから Azure への移行の手順として使用することができます。 Azure SQL Database のサブスクライバーについて詳しくは、「[SQL Database へのレプリケーション](replication-to-sql-database.md)」をご覧ください。

## <a name="requirements"></a>必要条件

Azure SQL Database 上のパブリッシャーとディストリビューターの要件は次のとおりです。

- Azure SQL Database Managed Instance。

   >[!NOTE]
   >マネージド インスタンスを使用して構成されていない Azure SQL Database は、サブスクライバーにしかなれません。

- SQL Server のインスタンスが、すべて同じ vNet 上に存在すること。

- レプリケーションの参加者間の接続に、SQL 認証が使用されること。

- レプリケーション作業ディレクトリ用の Azure ストレージ アカウント共有。

## <a name="features"></a>[機能]

サポートするものは次のとおりです。

- トランザクション レプリケーションとスナップショット レプリケーションの、オンプレミスと Azure SQL Database Managed Instance のインスタンスの組み合わせ。

- オンプレミス、Azure SQL Database、エラスティック プールのサブスクライバー。

- 一方向または双方向のレプリケーション

## <a name="configure-publishing-and-distribution-example"></a>パブリッシングとディストリビューションの例の構成

1. ポータルで [Azure SQL Database Managed Instance を作成](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-create-tutorial-portal)します。

1. 作業ディレクトリ用に [Azure ストレージ アカウントを作成](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account)します。 ストレージ キーを忘れずにコピーします。 「[ストレージ アクセス キーの表示とコピー](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#manage-your-storage-access-keys)」をご覧ください。

1. パブリッシャーのデータベースを作成します。

   以下のスクリプト例では、`<Publishing_DB>` をこのデータベースの名前に置き換えます。

1. ディストリビューターに向けて SQL 認証を使用するデータベース ユーザーを作成します。 「[データベース ユーザーの作成](http://docs.microsoft.com/azure/sql-database/sql-database-security-tutorial#creating-database-users)」をご覧ください。 セキュリティで保護されたパスワードを使用します。

   以下のスクリプト例では、この SQL Server アカウントのデータベース ユーザーとパスワードと共に、`<SQL_USER>` と `<PASSWORD>` を使用します。

1. [SQL Database Managed Instance に接続します](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ssms)。

1. 次のクエリを実行して、ディストリビューターとディストリビューション データベースを追加します。

   ```sql
   USE [master]
   GO
   EXEC sp_adddistributor @distributor = @@ServerName;
   EXEC sp_adddistributiondb @database = N'distribution';
   ```

1. 指定されたディストリビューション データベースを使用するパブリッシャーを構成するには、次のクエリを更新して実行します。

   `<SQL_USER>` と `<PASSWORD>` を、SQL Server アカウントとパスワードに置き換えます。

   `\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>` をご自身のストレージ アカウントの値に置き換えます。 

   `<STORAGE_CONNECTION_STRING>` をご自身のアクセス キーの値に置き換えます。

   次のクエリを更新した後、実行します。 

   ```sql
   USE [master]
   EXEC sp_adddistpublisher @publisher = @@ServerName,
                @distribution_db = N'distribution',
                @security_mode = 0,
                @login = N'<SQL_USER>',
                @password = N'<PASSWORD>',
                @working_directory = N'\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>',
                @storage_connection_string = N'<STORAGE_CONNECTION_STRING>';
   GO
   ```

1. レプリケーションのためにパブリッシャーを構成します。 

    次のクエリで、`<Publishing_DB>` をパブリッシャー データベースの名前に置き換えます。

    `<Publication_Name>` をパブリケーションの名前に置き換えます。

    `<SQL_USER>` と `<PASSWORD>` を、SQL Server アカウントとパスワードに置き換えます。

    クエリを更新した後で実行して、パブリケーションを作成します。

   ```sql
   USE [<Publishing_DB>]
   EXEC sp_replicationdboption @dbname = N'<Publishing_DB>',
                @optname = N'publish',
                @value = N'true';

   EXEC sp_addpublication @publication = N'<Publication_Name>',
                @status = N'active';

   EXEC sp_changelogreader_agent @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>';

   EXEC sp_addpublication_snapshot @publication = N'<Publication_Name>',
                @frequency_type = 1,
                @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>'
   ```

1. アーティクル、サブスクリプション、プッシュ サブスクリプションのエージェントを追加します。 

   これらのオブジェクトを追加するために、次のスクリプトを更新します。

   `<Object_Name>` をパブリケーション オブジェクトの名前に置き換えます。

   `<Object_Schema>` を送信元スキーマの名前に置き換えます。 

   山かっこ `<>` 内のその他のパラメーターを、前のスクリプト内の値と一致するように置き換えます。 

   ```sql
   EXEC sp_addarticle @publication = N'<Publication_Name>',
                @type = N'logbased',
                @article = N'<Object_Name>',
                @source_object = N'<Object_Name>',
                @source_owner = N'<Object_Schema>'

   EXEC sp_addsubscription @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @destination_db = N'<Subscribing_DB>',
                @subscription_type = N'Push'

   EXEC sp_addpushsubscription_agent @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @subscriber_db = N'<Subscribing_DB>',
                @subscriber_security_mode = 0,
                @subscriber_login = N'<SQL_USER>',
                @subscriber_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>', 
                @job_password = N'<PASSWORD>'
   GO
   ```

## <a name="limitations"></a>制限事項

サポートされない機能は次のとおりです。

- 更新可能なサブスクリプション

- アクティブ geo レプリケーション

## <a name="see-also"></a>参照

- [マネージド インスタンス (プレビュー) とは?](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)