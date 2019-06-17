---
title: 高可用性、ディザスター リカバリーのための JDBC Driver のサポート | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6e760523026251463f80d7f7e3e14b7e52b36ab2
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781536"
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>高可用性、障害回復のための JDBC Driver のサポート
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  このトピックでは、高可用性のディザスター リカバリーを実現する [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] のための [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] のサポートについて説明します。 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]の詳細については、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] オンライン ブックを参照してください。  
  
 Version 4.0 以降の [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では、接続プロパティを使用して、(高可用性のディザスター リカバリー) 可用性グループ (AG) の可用性グループ リスナーを指定できます。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] アプリケーションを AlwaysOn データベースに接続しているときにフェールオーバーが発生した場合、元の接続は切断され、アプリケーションではフェールオーバー後に処理を続行するために新しい接続を開く必要があります。 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] では、次の[接続プロパティ](../../connect/jdbc/setting-the-connection-properties.md)が追加されました。  
  
-   **multiSubnetFailover**  
  
-   **applicationIntent**
 
可用性グループまたはフェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、multiSubnetFailover=true を指定してください。 なお**multiSubnetFailover**は既定では false。 使用**applicationIntent**アプリケーション ワークロードの種類を宣言します。 詳細については、以下のセクションを参照してください。
 
Microsoft JDBC Driver 6.0 for SQL Server では、新しい接続プロパティ以降**transparentNetworkIPResolution** (TNIR) が Always On 可用性グループまたはサーバーに透過的な接続の追加複数の IP アドレスが関連付けられています。 ときに**transparentNetworkIPResolution**が true の場合、ドライバーは、最初の IP アドレスに接続を試行します。 最初の試行に失敗した場合、ドライバーはタイムアウトになると、それらのいずれかが成功すると、保留中の接続の試行を破棄するまで、並列ですべての IP アドレスに接続しようとします。   

注意してください。
* transparentNetworkIPResolution は既定で true
* multiSubnetFailover が true の場合は、transparentNetworkIPResolution が無視されます。
* データベース ミラーリングを使用する場合、transparentNetworkIPResolution は無視されます。
* 64 を超える IP アドレスがある場合は、transparentNetworkIPResolution が無視されます。
* TransparentNetworkIPResolution が true の場合、最初の接続試行は 500 ミリ秒のタイムアウト値を使用します。 接続の試行の残りの部分では、multiSubnetFailover 機能と同じロジックに従います。 

> [!NOTE]
> ユーザーは Microsoft JDBC Driver 4.2 を使用して (または削減) SQL Server の場合、 **multiSubnetFailover**が false の場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]最初の IP アドレスに接続しようとしています。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] が 1 つ目の IP アドレスとの間に接続を確立できない場合、接続は失敗します。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では、サーバーに関連付けられているその他の IP アドレスとの接続は試行されません。 
> 
> 
> [!NOTE]
>  接続タイムアウト値を大きくし、接続再試行ロジックを実装することにより、アプリケーションが可用性グループに接続する確立が高まります。 また、可用性グループのフェールオーバーにより接続が失敗する可能性があるため、接続再試行ロジックを実装して、再接続されるまで、失敗した接続の再接続を試行する必要があります。  
  
 
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover を使用した接続  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 可用性グループまたは [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず **multiSubnetFailover=true** を指定してください。 **multiSubnetFailover** を使用することで、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のすべての可用性グループおよびフェールオーバー クラスター インスタンスに対して高速フェールオーバーが有効化され、単一サブネットおよびマルチサブネットの AlwaysOn トポロジにおけるフェールオーバー時間が大幅に短縮されます。 マルチサブネット フェールオーバーの際には、クライアントは複数の接続を並列で試行します。 サブネット フェールオーバー中、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では TCP 接続が積極的に再試行されます。  
  
 **multiSubnetFailover** 接続プロパティを指定すると、アプリケーションが可用性グループまたはフェールオーバー クラスター インスタンスに配置され、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ではすべての IP アドレスに対して接続を試行することで、プライマリ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上のデータベースに接続が試行されます。 接続に対して **MultiSubnetFailover=true** を指定した場合、オペレーティング システムの既定の TCP 再送信間隔より短い間隔で、クライアントにより TCP 接続が再試行されます。 これにより、AlwaysOn 可用性グループまたは AlwaysOn フェールオーバー クラスター インスタンスのフェールオーバー後、再接続されるまでの時間を短縮することができます。単一サブネットとマルチサブネットの可用性グループ インスタンスおよびフェールオーバー クラスター インスタンスに適用することができます。  
  
 接続文字列キーワードの詳細については、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を参照してください[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)します。  
  
 可用性グループ リスナーまたはフェールオーバー クラスター インスタンス以外に接続するときに **multiSubnetFailover=true** を指定すると、パフォーマンスが低下する可能性があるため、このような指定はサポートされていません。  
  
 セキュリティ マネージャーがインストールされていない場合、Java 仮想マシンにより仮想 IP アドレス (VIP) が期限付きでキャッシュされます。この期限は、既定で JDK 実装および Java プロパティ (networkaddress.cache.ttl および networkaddress.cache.negative.ttl) によって定義されます。 JDK セキュリティ マネージャーがインストールされている場合、Java 仮想マシンにより VIP がキャッシュされます。このキャッシュは、既定で更新されません。 Java 仮想マシン キャッシュの "有効期限" (networkaddress.cache.ttl) を 1 日に設定する必要があります。 既定値を 1 日 (またはその他の値) に変更しない場合、VIP が追加または更新されたときに Java 仮想マシン キャッシュから古い値が削除されません。 Networkaddress.cache.ttl と networkaddress.cache.negative.ttl の詳細については、次を参照してください。 [ https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html)します。  
  
 可用性グループまたはフェールオーバー クラスター インスタンス内のサーバーに接続する際には、次のガイドラインに従います。  
  
-   場合、ドライバーのエラーが発生する、 **instanceName**と同じ接続文字列で接続プロパティが使用される、 **multiSubnetFailover**接続プロパティです。 これは、SQL ブラウザーは可用性グループ内で使用されないという事実を反映しています。 ただし場合、 **portNumber**接続プロパティが指定されても、ドライバーは無視**instanceName**して**portNumber**します。  
  
-   単一サブネットまたはマルチサブネットに接続する場合に **multiSubnetFailover** 接続プロパティを使用すると、両方の場合のパフォーマンスを向上させることができます。  
  
-   可用性グループに接続するには、接続文字列でサーバーとして、可用性グループの可用性グループ リスナーを指定します。 たとえば、jdbc:sqlserver://VNN1 のように指定します。  
  
-   64 個を超える数の IP アドレスが構成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続すると、接続エラーが発生します。  
  
-   **multiSubnetFailover** 接続プロパティを使用するアプリケーションの動作は、認証の種類 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証、Kerberos 認証、または Windows 認証) の影響を受けません。  
  
-   **loginTimeout** の値を増やすことで、フェールオーバー時間に対応し、アプリケーションの接続試行回数を減らすことができます。  
  
-   分散トランザクションはサポートされていません。  
  
 読み取り専用のルーティングが無効である場合、次の状況では可用性グループのセカンダリ レプリカの場所には接続できません。  
  
1.  セカンダリ レプリカの場所が、接続を許可するように構成されていない。  
  
2.  アプリケーションに **applicationIntent=ReadWrite** (後述します) が使用されているが、セカンダリ レプリカの場所が読み取り専用アクセスとして構成されている。  
  
 プライマリ レプリカが読み取り専用ワークロードを拒否するように構成されているとき、接続文字列に **ApplicationIntent=ReadOnly** が含まれていると、接続は失敗します。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>データベース ミラーリングの使用からマルチサブネット クラスターの使用へのアップグレード  
 現在、データベース ミラーリングを使用している [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] アプリケーションをマルチサブネットのシナリオにアップグレードする場合、**failoverPartner** 接続プロパティを削除して **multiSubnetFailover** に置き換え、それを **true** に設定し、接続文字列内のサーバー名を可用性グループ リスナーの名前に置き換えます。 接続文字列で **failoverPartner** および **multiSubnetFailover=true** が使用されている場合、ドライバーによってエラーが生成されます。 ただし、接続文字列に **failoverPartner** と **multiSubnetFailover=false** (または **ApplicationIntent=ReadWrite**) が使用されている場合、アプリケーションではデータベース ミラーリングが使用されます。  
  
 AG のプライマリ データベースでデータベース ミラーリングが使用されている場合、および可用性グループ リスナーではなく、プライマリ データベースに接続する接続文字列内で **multiSubnetFailover=true** が使用されている場合、ドライバーによってエラーが返されます。  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>multiSubnetFailover および applicationIntent をサポートする新しいメソッド  
 次のメソッドを使用するプログラムによるアクセス、 **multiSubnetFailover**、 **applicationIntent**と**transparentNetworkIPResolution**接続文字列キーワード:  
  
-   [SQLServerDataSource.getApplicationIntent](../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setApplicationIntent](../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDriver.getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md)  

-   SQLServerDataSource.setTransparentNetworkIPResolution

-   SQLServerDataSource.getTransparentNetworkIPResolution
  
 **GetMultiSubnetFailover**、 **setMultiSubnetFailover**、 **getApplicationIntent**、 **setApplicationIntent**、 **getTransparentNetworkIPResolution**と**setTransparentNetworkIPResolution**にメソッドが追加されても[SQLServerDataSource クラス](../../connect/jdbc/reference/sqlserverdatasource-class.md)、 [SQLServerConnectionPoolDataSource クラス](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)、および[SQLServerXADataSource クラス](../../connect/jdbc/reference/sqlserverxadatasource-class.md)します。  
  
## <a name="ssl-certificate-validation"></a>SSL 証明書の検証  
 可用性グループは、複数の物理サーバーで構成されます。 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] では、SSL 証明書における **Subject Alternate Name** のサポートが追加されているため、複数のホストを同じ証明書に関連付けることができます。 SSL の詳細については、「[SSL のサポートについて](../../connect/jdbc/understanding-ssl-support.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)   
 [接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)  
  
  
