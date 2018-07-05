---
title: Windows と Linux に SQL Server Always On 可用性グループを構成する (クロス プラットフォーム) |Microsoft ドキュメント
description: Windows と Linux 上のレプリカでは、SQL Server の可用性グループ構成します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/31/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 9ccd5cb5fdc7d5c5bc6ff62b203bee0bbce6e5e8
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34322763"
---
# <a name="configure-sql-server-always-on-availability-group-on-windows-and-linux-cross-platform"></a>Windows と Linux に SQL Server Always On 可用性グループを構成する (クロス プラットフォーム)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

この記事では、Windows サーバー上の 1 つのレプリカと Linux サーバー上の他のレプリカで Always On 可用性グループ (AG) を作成する手順について説明します。 この構成は、レプリカが異なるオペレーティング システム上にあるために、クロス プラットフォームです。 あるプラットフォームから他のプラットフォームへの移行、または災害復旧 (DR) にこの構成を使用してください。 クロス プラットフォームの構成を管理するクラスター ソリューションがないために、この構成は高可用性をサポートしません。 

![ハイブリッドなし](./media/sql-server-linux-availability-group-overview/image1.png)

前に、Windows および Linux での SQL Server インスタンスのインストールと構成について熟知してください。 

## <a name="scenario"></a>Scenario

このシナリオでは、2 台のサーバーは、さまざまなオペレーティング システムではします。 という名前の Windows Server 2016`WinSQLInstance`プライマリ レプリカをホストします。 という名前の Linux サーバー`LinuxSQLInstance`セカンダリ レプリカをホストします。

## <a name="configure-the-ag"></a>可用性グループを構成します。 

可用性グループを作成する手順は、読み取りスケール ワークロードの可用性グループを作成する手順と同じです。 AG クラスター型は、クラスター マネージャーが存在しないため、[なし] です。 

   >[!NOTE]
   >この記事でスクリプトには、角かっこを山`<`と`>`環境に置き換える必要がある値を識別します。 山かっこ自体は、スクリプトの必要はありません。 

1. Windows Server 2016 での SQL Server 2017 のインストール、Always On 可用性グループから SQL Server 構成マネージャーを有効にし、混合モード認証を設定します。 

   >[!TIP]
   >Azure では、このソリューションを検証している場合は、同じ可用性セットのデータ センターで分離されていることを確認するに両方のサーバーを配置します。 

   **可用性グループを有効にします。**

   手順については、次を参照してください。[を有効にすると、Always On 可用性グループ (SQL Server) を無効にする](../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)です。

   ![可用性グループを有効にします。](./media/sql-server-linux-availability-group-cross-platform/1-sqlserver-configuration-manager.png)

   SQL Server 構成マネージャーでは、コンピューターがフェールオーバー クラスターのノードではないことを示します。 

   可用性グループを有効にした後は、SQL Server を再起動します。

   **混合モード認証を設定**

   手順については、次を参照してください。[サーバー認証モードの変更](../database-engine/configure-windows/change-server-authentication-mode.md#SSMSProcedure)です。

1. Linux 上の SQL Server 2017 年 1 をインストールします。 手順については、次を参照してください。[インストール SQL Sever](sql-server-linux-setup.md)です。 有効にする`hadr`mssql 構成を使用して

   有効にする`hadr`mssql conf シェル プロンプトを使用して、次のコマンドを発行します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
   ```

   有効にした後`hadr`、SQL Server インスタンスを再起動します。  

   次の図は、この手順を示します。

   ![可用性グループの Linux を有効にします。](./media/sql-server-linux-availability-group-cross-platform/2-sqlserver-linux-set-hadr.png)

1. 両方のサーバー上の hosts ファイルを構成するか、サーバー名を DNS に登録します。

1. 開くファイアウォール ポートを TPC の 1433 and 5022 Windows と Linux の両方でします。

1. プライマリ レプリカ上でデータベース ログインおよびパスワードを作成します。

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   ```

1. プライマリ レプリカでのマスター _ キーと証明書を作成し、秘密キーを持つ証明書をバックアップします。

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
   BACKUP CERTIFICATE dbm_certificate
   TO FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
       );
   GO
   ```

1. Linux サーバー (セカンダリ レプリカ) で、証明書と秘密キーをコピー`/var/opt/mssql/data`です。 使用することができます`pscp`Linux サーバーにファイルをコピーします。 

1. グループと、秘密キーと証明書の所有権を設定`mssql:mssql`です。

   次のスクリプトは、グループとファイルの所有権を設定します。 

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.pvk
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.cer
   ```

   次の図で所有権とグループが正しく設定の証明書とキー。

   ![可用性グループの Linux を有効にします。](./media/sql-server-linux-availability-group-cross-platform/3-cert-key-owner-group.png)


1. セカンダリ レプリカ上でデータベース ログインとパスワードを作成し、マスター _ キーを作成します。

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<M@st3rKeyP@55w0rD!>'
   GO
   ```

1. セカンダリ レプリカにコピーした証明書を復元`/var/opt/mssql/data`です。 

   ```sql
   CREATE CERTIFICATE dbm_certificate   
       AUTHORIZATION dbm_user
       FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
       WITH PRIVATE KEY (
       FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
       DECRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
   )
   GO
   ```

1. プライマリ レプリカでは、エンドポイントを作成します。

   ```sql
   CREATE ENDPOINT [Hadr_endpoint]
       AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = 5022)
       FOR DATA_MIRRORING (
           ROLE = ALL,
           AUTHENTICATION = CERTIFICATE dbm_certificate,
           ENCRYPTION = REQUIRED ALGORITHM AES
           );
   ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
   GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login]
   GO
   ```

   >[!IMPORTANT]
   >ファイアウォールは、リスナーの TCP ポートを開く必要があります。 前のスクリプトでは、ポートは 5022 です。 使用可能な TCP ポートを使用します。 

1. セカンダリ レプリカの場合、エンドポイントを作成します。 エンドポイントの作成にセカンダリ レプリカでは、前述のスクリプトを繰り返します。 

1. プライマリ レプリカの場合で、可用性グループを作成`CLUSTER_TYPE = NONE`です。 スクリプトの例を使用して`SEEDING_MODE = AUTOMATIC`を可用性グループを作成します。 

   >[!NOTE]
   >SQL Server の Windows インスタンスがデータ ファイルとログ ファイル、自動、セカンダリ レプリカでこれらのパスが存在しないために、SQL Server の Linux インスタンスには失敗をシード処理のさまざまなパスを使用する場合。 クロス プラットフォームの可用性グループの次のスクリプトを使用するには、データベース、Windows server 上のデータとログ ファイルの同じパスする必要があります。 設定するスクリプトを更新するまたは`SEEDING_MODE = MANUAL`とし、バックアップし、復元を使用してデータベース`NORECOVERY`データベースのシードにします。 
   >
   >この動作は、Azure Marketplace イメージに適用されます。 
   >
   >自動シード処理の詳細については、次を参照してください。[自動シードの処理 - ディスク レイアウト](../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md#disklayout)です。 

   スクリプトを実行する前に、Ag の値を更新します。

      * 置き換える`<WinSQLInstance>`プライマリ レプリカの SQL Server インスタンスのサーバーの名前に置き換えます。

      * 置き換える`<LinuxSQLInstance>`セカンダリ レプリカの SQL Server インスタンスのサーバーの名前に置き換えます。 

   可用性グループを作成するには、値を更新し、プライマリ レプリカでスクリプトを実行します。  

   ```sql
   CREATE AVAILABILITY GROUP [ag1]
       WITH (CLUSTER_TYPE = NONE)
       FOR REPLICA ON
           N'<WinSQLInstance>' 
        WITH (
           ENDPOINT_URL = N'tcp://<WinSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            SEEDING_MODE = AUTOMATIC,
            FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
           N'<LinuxSQLInstance>' 
       WITH (
            ENDPOINT_URL = N'tcp://<LinuxSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
           SEEDING_MODE = AUTOMATIC,
           FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
           )
   GO
   ```
   
   詳細については、次を参照してください。 [CREATE AVAILABILITY GROUP (TRANSACT-SQL)](../t-sql/statements/create-availability-group-transact-sql.md)です。

1. セカンダリ レプリカの場合、可用性グループに参加します。

   ```sql
   ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE)
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE
   GO
   ```

1. 可用性グループのデータベースを作成します。 手順の例は、という名前のデータベースを使用して`<TestDB>`です。 自動シード処理を使用している場合は、データとログ ファイルの両方に同じパスを設定します。 

   スクリプトを実行する前に、データベースの値を更新します。

      * 置き換える`<TestDB>`データベースの名前に置き換えます。

      * 置き換える`<F:\Path>`データベースおよびログ ファイルのパスでします。 データベースとログ ファイルの同一のパスを使用します。 

      既定のパスを使用することもできます。 

    データベースを作成するには、スクリプトを実行します。 

   ```sql
   CREATE DATABASE [<TestDB>]
      CONTAINMENT = NONE
     ON  PRIMARY ( NAME = N'<TestDB>', FILENAME = N'<F:\Path>\<TestDB>.mdf')
     LOG ON ( NAME = N'<TestDB>_log', FILENAME = N'<F:\Path>\<TestDB>_log.ldf')
   GO
   ```

1. 完全なは、データベースのバックアップを作成します。 

1. 自動シード処理を使用しない場合は、セカンダリ レプリカ (Linux) サーバー上のデータベースを復元します。 [Windows からのバックアップと復元を使用して Linux に SQL Server データベースを移行](sql-server-linux-migrate-restore-database.md)です。 データベースを復元`WITH NORECOVERY`セカンダリ レプリカにします。 

1. データベースを可用性グループに追加します。 スクリプトの例を更新します。 置き換える`<TestDB>`データベースの名前に置き換えます。 プライマリ レプリカの場合、データベースを可用性グループに追加する SQL クエリを実行します。

   ```sql
   ALTER AG [ag1] ADD DATABASE <TestDB>
   GO
   ```

1. データベースがセカンダリ レプリカの設定を取得することを確認します。 

## <a name="fail-over-the-primary-replica"></a>プライマリ レプリカをフェールオーバーします。

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

この記事では、移行または読み取り小数点以下桁数のワークロードをサポートするプラットフォーム間の可用性グループを作成する手順を確認します。 手動による災害復旧のために使用できます。 可用性グループをフェールオーバーする方法についても説明します。 クロス プラットフォームの可用性グループがクラスターの種類を使用して`NONE`クラスター ツール - プラットフォーム間ではないため、高可用性をサポートしません。 

## <a name="next-steps"></a>次の手順

[Always On 可用性グループの概要](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

[Linux 展開用の SQL Server 可用性の基礎](sql-server-linux-ha-basics.md)
