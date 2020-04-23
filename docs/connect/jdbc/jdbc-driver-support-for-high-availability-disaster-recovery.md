---
title: 高可用性、ディザスター リカバリーのための JDBC ドライバーのサポート
description: このトピックでは、高可用性、ディザスター リカバリー (AlwaysOn 可用性グループ) のための Microsoft JDBC Driver for SQL Server のサポートについて説明します。
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 941136eb74d217f0af7b2687e618bf93f2454b8f
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2020
ms.locfileid: "81635063"
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>高可用性、ディザスター リカバリーのための JDBC ドライバーのサポート
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  このトピックでは、高可用性のディザスター リカバリーを実現する [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] のための [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] のサポートについて説明します。 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]の詳細については、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] オンライン ブックを参照してください。  
  
 Version 4.0 以降の [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では、接続プロパティを使用して、(高可用性のディザスター リカバリー) 可用性グループ (AG) の可用性グループ リスナーを指定できます。 フェールオーバーが発生した AlwaysOn データベースに [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] アプリケーションが接続されていた場合、元の接続は切断され、アプリケーションではフェールオーバー後に処理を続行するために新しい接続を開く必要があります。 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] では、次の[接続プロパティ](setting-the-connection-properties.md)が追加されました。  
  
-   **multiSubnetFailover**  
  
-   **applicationIntent**
 
可用性グループまたはフェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、multiSubnetFailover=true を指定してください。 既定では、**multiSubnetFailover** は false であることに注意してください。 **applicationIntent** を使用してアプリケーションのワークロードの種類を宣言します。 詳細については、以下のセクションを参照してください。
 
Microsoft JDBC Driver for SQL Server のバージョン 6.0 以降では、Always On 可用性グループまたは複数の IP アドレスが関連付けられているサーバーに透過的に接続するために、新しい接続プロパティ **transparentNetworkIPResolution** (TNIR) が追加されています。 **transparentNetworkIPResolution** が true の場合、ドライバーは、使用可能な最初の IP アドレスへの接続を試みます。 最初の試行が失敗した場合、ドライバーは、タイムアウトになるまですべての IP アドレスに並行して接続を試みます。いずれかの試行に成功すると、保留中の接続試行はすべて破棄されます。   

以下の点に注意してください。
* transparentNetworkIPResolution は既定で true に設定されます。
* multiSubnetFailover が true の場合、transparentNetworkIPResolution は無視されます。
* データベース ミラーリングが使用されている場合、transparentNetworkIPResolution は無視されます。
* IP アドレスが 64 個を超える場合、transparentNetworkIPResolution は無視されます。
* transparentNetworkIPResolution が true の場合、最初の接続試行では、タイムアウト値として 500 ミリ秒が使用されます。 残りの接続試行は、multiSubnetFailover 機能と同じロジックに従います。 

> [!NOTE]
> Microsoft JDBC Driver for SQL Server の 4.2 (以前) を使用しており、**multiSubnetFailover** が false の場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は、最初の IP アドレスへの接続を試みます。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] が 1 つ目の IP アドレスとの間に接続を確立できない場合、接続は失敗します。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では、サーバーに関連付けられているその他の IP アドレスとの接続は試行されません。 
> 
> 
> [!NOTE]
>  接続タイムアウト値を大きくし、接続再試行ロジックを実装することにより、アプリケーションが可用性グループに接続する確立が高まります。 また、可用性グループのフェールオーバーにより接続が失敗する可能性があるため、接続再試行ロジックを実装して、再接続されるまで、失敗した接続の再接続を試行する必要があります。  
  
 
  
## <a name="connecting-with-multisubnetfailover"></a>multiSubnetFailover を使用した接続  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 可用性グループまたは [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] フェールオーバー クラスター インスタンスの可用性グループ リスナーに接続する際には、必ず **multiSubnetFailover=true** を指定してください。 **multiSubnetFailover** を使用することで、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のすべての可用性グループおよびフェールオーバー クラスター インスタンスに対して高速フェールオーバーが有効化され、単一サブネットおよびマルチサブネットの AlwaysOn トポロジにおけるフェールオーバー時間が大幅に短縮されます。 マルチサブネット フェールオーバーの際には、クライアントは複数の接続を並列で試行します。 サブネット フェールオーバー中、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では TCP 接続が積極的に再試行されます。  
  
 **multiSubnetFailover** 接続プロパティを指定すると、アプリケーションが可用性グループまたはフェールオーバー クラスター インスタンスに配置され、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ではすべての IP アドレスに対して接続を試行することで、プライマリ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上のデータベースに接続が試行されます。 接続に対して **MultiSubnetFailover=true** を指定した場合、オペレーティング システムの既定の TCP 再送信間隔より短い間隔で、クライアントにより TCP 接続が再試行されます。 この動作により、AlwaysOn 可用性グループまたは AlwaysOn フェールオーバー クラスター インスタンスのフェールオーバー後、再接続されるまでの時間を短縮することができます。これは、単一サブネットとマルチサブネット両方の可用性グループ インスタンスおよびフェールオーバー クラスター インスタンスに適用できます。  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]の接続文字列キーワードの詳細については、「[接続プロパティの設定](setting-the-connection-properties.md)」を参照してください。  
  
 可用性グループ リスナーまたはフェールオーバー クラスター インスタンス以外に接続するときに **multiSubnetFailover=true** を指定すると、パフォーマンスが低下する可能性があるため、このような指定はサポートされていません。  
  
 セキュリティ マネージャーがインストールされていない場合、Java 仮想マシンにより仮想 IP アドレス (VIP) が期限付きでキャッシュされます。この期限は、既定で JDK 実装および Java プロパティ (networkaddress.cache.ttl および networkaddress.cache.negative.ttl) によって定義されます。 JDK セキュリティ マネージャーがインストールされている場合、Java 仮想マシンにより VIP がキャッシュされます。このキャッシュは、既定で更新されません。 Java 仮想マシン キャッシュの "有効期限" (networkaddress.cache.ttl) を 1 日に設定する必要があります。 既定値を 1 日 (またはその他の値) に変更しない場合、VIP が追加または更新されたときに Java 仮想マシン キャッシュから古い値が削除されません。 networkaddress.cache.ttl および networkaddress.cache.negative.ttl の詳細については、[https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html) を参照してください。  
  
 可用性グループまたはフェールオーバー クラスター インスタンス内のサーバーに接続する際には、次のガイドラインに従います。  
  
-   **multiSubnetFailover** 接続プロパティと同じ接続文字列内で **instanceName** 接続プロパティを使用した場合、ドライバーはエラーを生成します。 このエラーは、SQL Browser が可用性グループ内で使用されていないという事実を反映しています。 ただし、**portNumber** 接続プロパティも指定した場合、ドライバーは、**instanceName** を無視して、**portNumber** を使用します。  
  
-   単一サブネットまたはマルチサブネットに接続する場合に **multiSubnetFailover** 接続プロパティを使用すると、両方の場合のパフォーマンスを向上させることができます。  
  
-   可用性グループに接続するには、接続文字列でサーバーとして、可用性グループの可用性グループ リスナーを指定します。 たとえば、jdbc:sqlserver://VNN1 のように指定します。  
  
-   64 個を超える数の IP アドレスが構成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続すると、接続エラーが発生します。  
  
-   **multiSubnetFailover** 接続プロパティを使用するアプリケーションの動作は、次の認証の種類に影響されません。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証、Kerberos 認証、または Windows 認証。  
  
-   **loginTimeout** の値を増やすことで、フェールオーバー時間に対応し、アプリケーションの接続試行回数を減らすことができます。  
  
-   分散トランザクションはサポートされません。  
  
 読み取り専用のルーティングが無効である場合、次の状況では可用性グループのセカンダリ レプリカの場所には接続できません。  
  
1.  セカンダリ レプリカの場所が、接続を許可するように構成されていない。  
  
2.  アプリケーションに **applicationIntent=ReadWrite** (後述します) が使用されているが、セカンダリ レプリカの場所が読み取り専用アクセスとして構成されている。  
  
 プライマリ レプリカが読み取り専用ワークロードを拒否するように構成されているとき、接続文字列に **ApplicationIntent=ReadOnly** が含まれていると、接続は失敗します。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>データベース ミラーリングからマルチサブネット クラスターの使用へのアップグレード  
 現在、データベース ミラーリングを使用している [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] アプリケーションをマルチサブネットのシナリオにアップグレードする場合、**failoverPartner** 接続プロパティを削除して **multiSubnetFailover** に置き換え、それを **true** に設定し、接続文字列内のサーバー名を可用性グループ リスナーに置き換える必要があります。 接続文字列で **failoverPartner** および **multiSubnetFailover=true** が使用されている場合、ドライバーによってエラーが生成されます。 ただし、接続文字列に **failoverPartner** と **multiSubnetFailover=false** (または **ApplicationIntent=ReadWrite**) が使用されている場合、アプリケーションではデータベース ミラーリングが使用されます。  
  
 AG のプライマリ データベースでデータベース ミラーリングが使用されている場合、および可用性グループ リスナーではなく、プライマリ データベースに接続する接続文字列内で **multiSubnetFailover=true** が使用されている場合、ドライバーによってエラーが返されます。  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>multiSubnetFailover および applicationIntent をサポートする新しいメソッド  
 次のメソッドを使用すると、プログラムから **multiSubnetFailover**、**applicationIntent**、**transparentNetworkIPResolution** 接続文字列キーワードにアクセスできます。  
  
-   [SQLServerDataSource.getApplicationIntent](reference/getapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setApplicationIntent](reference/setapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.getMultiSubnetFailover](reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setMultiSubnetFailover](reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDriver.getPropertyInfo](reference/getpropertyinfo-method-sqlserverdriver.md)  

-   SQLServerDataSource.setTransparentNetworkIPResolution

-   SQLServerDataSource.getTransparentNetworkIPResolution
  
 **getMultiSubnetFailover**、**setMultiSubnetFailover**、**getApplicationIntent**、**setApplicationIntent**、**getTransparentNetworkIPResolution**、**setTransparentNetworkIPResolution** の各メソッドも [SQLServerDataSource クラス](reference/sqlserverdatasource-class.md)、[SQLServerConnectionPoolDataSource クラス](reference/sqlserverconnectionpooldatasource-class.md)、[SQLServerXADataSource クラス](reference/sqlserverxadatasource-class.md) に追加されます。  
  
## <a name="tlsssl-certificate-validation"></a>TLS/SSL 証明書の検証  
 可用性グループは、複数の物理サーバーで構成されます。 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] で、TLS/SSL 証明書に対する **Subject Alternate Name** のサポートが追加されたため、複数のホストを同じ証明書に関連付けることができるようになりました。 TLS の詳細については、「[暗号化のサポートについて](understanding-ssl-support.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [JDBC ドライバーによる SQL Server への接続](connecting-to-sql-server-with-the-jdbc-driver.md)  
 [接続プロパティの設定](setting-the-connection-properties.md)  
  
  
