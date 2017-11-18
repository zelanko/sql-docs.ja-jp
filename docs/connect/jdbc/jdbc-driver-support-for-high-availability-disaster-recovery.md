---
title: "高可用性、災害復旧の JDBC ドライバー サポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 27b51025180a1c9a2463c49401589ab459e7ecaf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>高可用性、障害回復のための JDBC Driver のサポート
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  このトピックについて説明[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]の高可用性、災害復旧--サポート[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]です。 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]の詳細については、 [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] オンライン ブックを参照してください。  
  
 以降のバージョン 4.0 では、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]の可用性グループ リスナーを指定することができます (高可用性、災害復旧) 接続プロパティの可用性グループ (AG)。 場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]アプリケーションがフェールオーバーが発生した AlwaysOn データベースに接続している、元の接続が切断され、アプリケーションは、フェールオーバー後の作業を続行する新しい接続を開く必要があります。 次[接続プロパティ](../../connect/jdbc/setting-the-connection-properties.md)で追加された[!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]:  
  
-   **multiSubnetFailover**  
  
-   **applicationIntent**
 
MultiSubnetFailover を指定して、可用性グループまたはフェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する場合に true を = です。 なお**multiSubnetFailover**は既定で false に設定します。 使用して**applicationIntent**アプリケーション ワークロードの種類を宣言します。 詳細については次のセクションを参照してください。
 
以降、Microsoft JDBC Driver のバージョン 6.0 では、SQL Server の新しい接続プロパティの**transparentNetworkIPResolution** (TNIR) が Always On 可用性グループまたはがサーバーに透過的な接続の追加複数の IP アドレスが関連付けられています。 ときに**transparentNetworkIPResolution**が true の場合、ドライバーは最初の IP アドレスに接続しようとしています。 最初の試行が失敗すると、ドライバーはタイムアウトになると、それらのいずれかが成功した場合、保留中の接続試行を破棄するまで並列内のすべての IP アドレスに接続しようとします。   

注意してください。
* transparentNetworkIPResolution が既定では true
* multiSubnetFailover が true の場合、transparentNetworkIPResolution は無視されます。
* データベース ミラーリングを使用する場合、transparentNetworkIPResolution は無視されます。
* 64 を超える IP アドレスがある場合は、transparentNetworkIPResolution が無視されます。
* TransparentNetworkIPResolution が true の場合、最初の接続試行は、500 ミリ秒のタイムアウト値を使用します。 接続試行の残りの部分では、multiSubnetFailover 機能と同様に、同じロジックに従います。 

> [!NOTE]  
ユーザーは Microsoft JDBC Driver 4.2 を使用して (または削減) for SQL Server で、 **multiSubnetFailover**が false の場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]最初の IP アドレスに接続しようとしています。 場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]接続に失敗した最初の IP アドレスとの接続を確立できません。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]サーバーに関連付けられているその他の IP アドレスに接続することはしません。 

  
> [!NOTE]  
>  接続タイムアウト値を大きくし、接続再試行ロジックを実装することにより、アプリケーションが可用性グループに接続する確立が高まります。 また、可用性グループのフェールオーバーにより接続が失敗する可能性があるため、接続再試行ロジックを実装して、再接続されるまで、失敗した接続の再接続を試行する必要があります。  
  
 
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover を使用した接続  
 常に指定**multiSubnetFailover = true**の可用性グループ リスナーに接続するときに、[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]可用性グループ、または[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]フェールオーバー クラスター インスタンス。 **multiSubnetFailover**すべての可用性グループおよびフェールオーバー クラスター インスタンスに対して高速フェールオーバーを有効に[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]し、単一サブネットおよびマルチ サブネットの AlwaysOn トポロジにおけるフェールオーバー時間が大幅に低下します。 マルチサブネット フェールオーバーの際には、クライアントは複数の接続を並列で試行します。 サブネットのフェールオーバー中に、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]は積極的に TCP 接続を再試行します。  
  
 **MultiSubnetFailover**接続プロパティは、可用性グループまたはフェールオーバー クラスター インスタンスで、アプリケーションが展開されていることを示します、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] プライマリ上のデータベースに接続しようとして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]すべての ip アドレスに接続しようとしてのインスタンスに対応します。 ときに**MultiSubnetFailover = true**が指定されている接続の場合、クライアントは、オペレーティング システムの既定の TCP 再転送間隔よりも高速接続試行を再試行します。 これにより、AlwaysOn 可用性グループまたは AlwaysOn フェールオーバー クラスター インスタンスのフェールオーバー後、再接続されるまでの時間を短縮することができます。単一サブネットとマルチサブネットの可用性グループ インスタンスおよびフェールオーバー クラスター インスタンスに適用することができます。  
  
 接続文字列キーワードの詳細については、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を参照してください[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
 指定する**multiSubnetFailover = true**可用性グループ リスナーまたはフェールオーバー クラスター インスタンス以外のものへの接続は負の値のパフォーマンスに影響されない可能性があり、サポートされていません。  
  
 セキュリティ マネージャーがインストールされていない場合、Java 仮想マシンにより仮想 IP アドレス (VIP) が期限付きでキャッシュされます。この期限は、既定で JDK 実装および Java プロパティ (networkaddress.cache.ttl および networkaddress.cache.negative.ttl) によって定義されます。 JDK セキュリティ マネージャーがインストールされている場合、Java 仮想マシンにより VIP がキャッシュされます。このキャッシュは、既定で更新されません。 Java 仮想マシン キャッシュの "有効期限" (networkaddress.cache.ttl) を 1 日に設定する必要があります。 既定値を 1 日 (またはその他の値) に変更しない場合、VIP が追加または更新されたときに古い値が削除されません。 Networkaddress.cache.ttl と networkaddress.cache.negative.ttl の詳細については、次を参照してください。 [http://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](http://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html)です。  
  
 可用性グループまたはフェールオーバー クラスター インスタンス内のサーバーに接続する際には、次のガイドラインに従います。  
  
-   場合に、ドライバーがエラーを生成、 **instanceName**と同じ接続文字列で接続プロパティが使用される、 **multiSubnetFailover**接続プロパティです。 これは、SQL ブラウザーは可用性グループ内で使用されないという事実を反映しています。 ただし場合、 **portNumber**接続プロパティが指定されても、ドライバーは無視されます**instanceName**して**portNumber**です。  
  
-   使用して、 **multiSubnetFailover**接続プロパティの両方のパフォーマンスの向上が単一のサブネットまたはマルチ サブネットに接続する、ときにします。  
  
-   可用性グループに接続するには、接続文字列でサーバーとして、可用性グループの可用性グループ リスナーを指定します。 たとえば、jdbc:sqlserver://VNN1 のように指定します。  
  
-   64 個を超える数の IP アドレスが構成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンスに接続すると、接続エラーが発生します。  
  
-   使用するアプリケーションの動作、 **multiSubnetFailover**接続プロパティが認証の種類に基づく影響を受けません。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]認証、Kerberos 認証、または Windows 認証です。  
  
-   値を大きく**loginTimeout**フェールオーバー時間に対応し、アプリケーションの接続再試行回数を削減します。  
  
-   分散トランザクションはサポートされていません。  
  
 読み取り専用のルーティングが無効である場合、次の状況では可用性グループのセカンダリ レプリカの場所には接続できません。  
  
1.  セカンダリ レプリカの場所が、接続を許可するように構成されていない。  
  
2.  アプリケーションで使用する場合**applicationIntent = ReadWrite** (後述) セカンダリ レプリカの場所は読み取り専用アクセス用に構成されたとします。  
  
 プライマリ レプリカが読み取り専用ワークロードを拒否するように構成されているとき、接続文字列に **ApplicationIntent=ReadOnly** が含まれていると、接続は失敗します。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>データベース ミラーリングの使用からマルチサブネット クラスターの使用へのアップグレード  
 アップグレードする場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]アプリケーション現在データベース ミラーリングを使用して、マルチ サブネットのシナリオでは、削除する必要あります、 **failoverPartner**接続プロパティと、コードに置き換えます**multiSubnetFailover** 'éý' **true**し、接続文字列でサーバー名を可用性グループ リスナーに置き換えます。 接続文字列で使用する場合**failoverPartner**と**multiSubnetFailover = true**ドライバーでエラーが発生します。 ただし、接続文字列で使用する場合**failoverPartner**と**multiSubnetFailover = false** (または**ApplicationIntent = ReadWrite**)、アプリケーション データベースが使用されますミラー化できます。  
  
 ドライバーが場合と、AG のプライマリ データベースでデータベース ミラーリングを使用する場合に、エラーが返されます**multiSubnetFailover = true**は可用性グループにはなく、プライマリ データベースに接続する接続文字列で使用リスナー。  
  
## <a name="specifying-application-intent"></a>アプリケーション インテントの指定  
 ときに**applicationIntent = ReadOnly**、AlwaysOn 対応データベースに接続するときに、クライアントが読み取り専用ワークロードを要求します。 サーバーは、接続時およびデータベース ステートメントの使用時にインテントを強制しますが、その対象は AlwaysOn 対応データベースのみです。  
  
 **ApplicationIntent**キーワードは、レガシの読み取り専用データベースでは機能しません。  
  
 対象の AlwaysOn データベースのワークロードの読み取りを許可または禁止することができます (これは、**PRIMARY_ROLE** および **SECONDARY_ROLE**[!INCLUDE[tsql](../../includes/tsql_md.md)] ステートメントの **ALLOW_CONNECTIONS** 句で実行します)。  
  
 **ApplicationIntent**読み取り専用ルーティングを有効にするキーワードを使用します。  
  
## <a name="read-only-routing"></a>読み取り専用ルーティング  
 読み取り専用ルーティングは、データベースの読み取り専用レプリカの可用性を実現する機能です。 読み取り専用のルーティングを有効にするには  
  
1.  AlwaysOn 可用性グループの可用性グループ リスナーに接続している。  
  
2.  **ApplicationIntent**接続文字列キーワードに設定する必要があります**ReadOnly**です。  
  
3.  データベース管理者が可用性グループを構成し、読み取り専用のルーティングを有効にする必要があります。  
  
 読み取り専用のルーティングを使用した複数の接続が同じ読み取り専用レプリカに接続されるとは限りません。 データベース同期の変更やサーバーのルーティング構成の変更によって、クライアントが別の読み取り専用レプリカに接続される場合があります。 すべての読み取り専用要求が同じ読み取り専用レプリカに接続を確認してください、渡さないで、可用性グループ リスナーまたは仮想 IP アドレスを**serverName**接続文字列キーワードです。 代わりに、読み取り専用インスタンスの名前を指定します。  
  
 読み取り専用ルーティングでは、最初にプライマリに接続した後、使用できる最善の読み取り可能セカンダリが検索されます。このため、読み取り専用ルーティングに要する時間は、プライマリに接続するよりも長くなります。 このため、ログイン タイムアウトを大きくする必要があります。  
  
## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>multiSubnetFailover および applicationIntent をサポートする新しいメソッド  
 次の方法では、プログラムによるアクセスを**multiSubnetFailover**、 **applicationIntent**と**transparentNetworkIPResolution**接続文字列キーワード:  
  
-   [SQLServerDataSource.getApplicationIntent](../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setApplicationIntent](../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDriver.getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md)  

-   SQLServerDataSource.setTransparentNetworkIPResolution

-   SQLServerDataSource.getTransparentNetworkIPResolution
  
 **GetMultiSubnetFailover**、 **setMultiSubnetFailover**、 **getApplicationIntent**、 **setApplicationIntent**、 **getTransparentNetworkIPResolution**と**setTransparentNetworkIPResolution**にメソッドが追加されても[SQLServerDataSource クラス](../../connect/jdbc/reference/sqlserverdatasource-class.md)、 [SQLServerConnectionPoolDataSource クラス](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)、および[SQLServerXADataSource クラス](../../connect/jdbc/reference/sqlserverxadatasource-class.md)です。  
  
## <a name="ssl-certificate-validation"></a>SSL 証明書の検証  
 可用性グループは、複数の物理サーバーで構成されます。 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]サポートが追加されました**サブジェクト代替名**で SSL 証明書の複数のホストは、同じ証明書を関連付けることができるようにします。 SSL の詳細については、次を参照してください。[について SSL サポート](../../connect/jdbc/understanding-ssl-support.md)です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーで SQL Server に接続します。](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)   
 [接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)  
  
  

