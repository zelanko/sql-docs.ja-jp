---
title: Windows と Linux に SQL Server Always On 可用性グループを構成する (クロス プラットフォーム) |Microsoft ドキュメント
description: Windows および Linux 上のレプリカでは、SQL Server の可用性グループ構成。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/31/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 6160010d02482f9ffd4ed1a4306ae064607b7d75
ms.sourcegitcommit: f62f70298651d6223fa5d215b6a7a0d2ffecbd0d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2018
ms.locfileid: "51947576"
---
# <a name="configure-sql-server-always-on-availability-group-on-windows-and-linux-cross-platform"></a>Windows と Linux に SQL Server Always On 可用性グループを構成する (クロス プラットフォーム)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

この記事では、Windows サーバー上の 1 つのレプリカと Linux サーバー上の他のレプリカで Always On 可用性グループ (AG) を作成する手順について説明します。 この構成は、レプリカが異なるオペレーティング システム上にあるために、クロス プラットフォームです。 あるプラットフォームから他のプラットフォームへの移行、または災害復旧 (DR) にこの構成を使用してください。 クロス プラットフォームの構成を管理するクラスター ソリューションがないために、この構成は高可用性をサポートしません。 

![ハイブリッドなし](./media/sql-server-linux-availability-group-overview/image1.png)

続ける前に、Windows および Linux での SQL Server インスタンスのインストールと構成について熟知してください。 

## <a name="scenario"></a>シナリオ

このシナリオでは、2 台のサーバーは、別々のオペレーティング システムにあります。 `WinSQLInstance` という名前の Windows Server 2016 がプライマリ レプリカをホストします。 `LinuxSQLInstance` という名前の Linux サーバーがセカンダリ レプリカをホストします。

## <a name="configure-the-ag"></a>可用性グループを構成します。 

可用性グループを作成する手順は、読み取りスケール ワークロード用の AG を作成する手順と同じです。 可用性グループのクラスターの種類が NONE、クラスター マネージャーがないためです。 

   >[!NOTE]
   >この記事のスクリプトでは、環境に合わせて置き換える必要のある値を山かっこ `<`と`>` で識別します。 山かっこ自体は、スクリプトには必要ありません。 

1. Windows Server 2016 で SQL Server 2017 のインストールし、SQL Server 構成マネージャーから Always On 可用性グループを有効にし、混合モード認証を設定します。 

   >[!TIP]
   >Azure でこのソリューションを検証している場合は、データ センターで分離されていることを確認するために両方のサーバーを同じ可用性セットに配置します。 

   **可用性グループを有効にします。**

   手順については、[AlwaysOn 可用性グループの有効化と無効化 (SQL Server)](../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md) を参照してください。

   ![可用性グループを有効にします。](./media/sql-server-linux-availability-group-cross-platform/1-sqlserver-configuration-manager.png)

   SQL Server 構成マネージャーでは、コンピューターがフェールオーバー クラスター内のノードでないことを示します。 

   可用性グループを有効にした後は、SQL Server を再起動します。

   **混合モード認証を設定**

    手順については、[サーバーの認証モードの変更](../database-engine/configure-windows/change-server-authentication-mode.md#SSMSProcedure) を参照してください。

1. Linux で SQL Server 2017 をインストールします。 手順については、[SQL Server のインストール](sql-server-linux-setup.md)を参照してください。 mssql-conf を使用して `hadr` を有効にします。

   シェル プロンプトから mssql-conf を使用して `hadr` を有効にするには、次のコマンドを発行します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
   ```

   `hadr` を有効にした後は、SQL Server インスタンスを再起動します。  

   次の図は、この手順を示します。

   ![可用性グループの Linux を有効にします。](./media/sql-server-linux-availability-group-cross-platform/2-sqlserver-linux-set-hadr.png)

1. 両方のサーバー上の hosts ファイルを構成またはサーバー名を DNS に登録します。

1. Windows と Linux の両方で TPC 1433 と 5022 のファイアウォール ポートを開きます。

1. プライマリ レプリカで、データベース ログインおよびパスワードを作成します。

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   ```

1. プライマリ レプリカで、マスター キーと証明書を作成し、秘密キーを持つ証明書をバックアップします。

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

1. 証明書と秘密キーを Linux サーバー (セカンダリ レプリカ) の `/var/opt/mssql/data` にコピーします。 Linux サーバーにファイルをコピーするには `pscp` を使用することができます。 

1. 秘密キーと証明書のグループと所有権を `mssql:mssql` に設定します。

   次のスクリプトは、ファイルのグループと所有権を設定します。 

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.pvk
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.cer
   ```

   次の図では所有権とグループが証明書とキーに正しく設定されています。

   ![可用性グループの Linux を有効にします。](./media/sql-server-linux-availability-group-cross-platform/3-cert-key-owner-group.png)


1. セカンダリ レプリカで、データベース ログインとパスワードを作成し、マスター キーを作成します。

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<M@st3rKeyP@55w0rD!>'
   GO
   ```

1. セカンダリ レプリカで、`/var/opt/mssql/data` にコピーした証明書を復元します。 

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

1. プライマリ レプリカで、エンドポイントを作成します。

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
   >ファイアウォールは、リスナーの TCP ポートを開く必要があります。 前のスクリプトでは、ポートは 5022 です。 利用可能な TCP ポートを使用します。 

1. セカンダリ レプリカで、エンドポイントを作成します。 エンドポイントを作成するには、前述のスクリプトをセカンダリ レプリカで繰り返します。 

1. プライマリ レプリカで、`CLUSTER_TYPE = NONE` を使用して可用性グループを作成します。 スクリプトの例では `SEEDING_MODE = AUTOMATIC` を使用して可用性グループを作成します。 

   >[!NOTE]
   >SQL Server の Windows インスタンスがデータ ファイルとログ ファイルとで別々のパスを使用する場合、自動シード処理は、セカンダリ レプリカでこれらのパスが存在しないために、SQL Server の Linux インスタンスで失敗します。 クロス プラットフォームの可用性グループで次のスクリプトを使用するには、データベースは、Windows Server 上のデータ ファイルとログ ファイルで同じパスを必要とします。 または、スクリプトを更新して、`SEEDING_MODE = MANUAL` と設定し、`NORECOVERY` を使用してデータベースをバックアップおよび復元し、データベースにシード処理を行うこともできます。 
   >
   >この動作は、Azure Marketplace イメージに適用されます。 
   >
   >自動シード処理の詳細については、[自動シードの処理 - ディスク レイアウト](../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md#disklayout) を参照してください。 

   スクリプトを実行する前に、可用性グループ (AG) の値を更新します。

      * `<WinSQLInstance>` をプライマリ レプリカの SQL Server インスタンスのサーバーの名前に置き換えます。

      * `<LinuxSQLInstance>` をセカンダリ レプリカの SQL Server インスタンスのサーバーの名前に置き換えます。 

   AG を作成するには、値を更新し、プライマリ レプリカでスクリプトを実行します。  

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
   
   詳細については、[CREATE AVAILABILITY GROUP (TRANSACT-SQL)](../t-sql/statements/create-availability-group-transact-sql.md) を参照してください。

1. セカンダリ レプリカで、可用性グループに参加します。

   ```sql
   ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE)
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE
   GO
   ```

1. 可用性グループのデータベースを作成します。 手順の例では、`<TestDB>` という名前のデータベースを使用しています。 自動シード処理を使用している場合は、データ ファイルとログ ファイルの両方に同じパスを設定します。 

   スクリプトを実行する前に、データベースの値を更新します。

      * `<TestDB>` をデータベースの名前に置き換えます。

      * `<F:\Path>` をデータベースおよびログ ファイルのパスに置き換えます。 データベースとログ ファイルには同一のパスを使用します。 

      既定のパスを使用することもできます。 

    データベースを作成するには、スクリプトを実行します。 

   ```sql
   CREATE DATABASE [<TestDB>]
      CONTAINMENT = NONE
     ON  PRIMARY ( NAME = N'<TestDB>', FILENAME = N'<F:\Path>\<TestDB>.mdf')
     LOG ON ( NAME = N'<TestDB>_log', FILENAME = N'<F:\Path>\<TestDB>_log.ldf')
   GO
   ```

1. データベースの完全なバックアップを作成します。 

1. 自動シード処理を使用していない場合は、セカンダリ レプリカ (Linux) サーバー上のデータベースを復元します。 [バックアップと復元を使用して Windows から Linux に SQL Server データベースを移行します](sql-server-linux-migrate-restore-database.md)。 セカンダリ レプリカでデータベース `WITH NORECOVERY` を復元します。 

1. データベースを可用性グループに追加します。 スクリプトの例を更新します。 `<TestDB>` をデータベースの名前に置き換えます。 プライマリ レプリカで、データベースを可用性グループに追加する SQL クエリを実行します。

   ```sql
   ALTER AG [ag1] ADD DATABASE <TestDB>
   GO
   ```

1. データベースをセカンダリ レプリカで入力を取得することを確認します。 

## <a name="fail-over-the-primary-replica"></a>プライマリ レプリカをフェールオーバーします。

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

この記事では、移行または読み取りスケールのワークロードをサポートするプラットフォーム間の可用性グループを作成する手順を確認しました。 手動による災害復旧のために使用できます。 可用性グループをフェールオーバーする方法についても説明しました。 クロス プラットフォームのクラスター ツールが無いため、クロス プラットフォームの可用性グループはクラスターの種類 `NONE` を使用し、高可用性をサポートしません。 

## <a name="next-steps"></a>次の手順

[Always On 可用性グループの概要](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

[Linux 展開用の SQL Server 可用性の基礎](sql-server-linux-ha-basics.md)
