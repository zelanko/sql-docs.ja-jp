---
title: 高可用性、ディザスターリカバリーをサポートする SQL Server Native ClientMicrosoft Docs
ms.custom: ''
ms.date: 08/31/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2b06186b-4090-4728-b96b-90d6ebd9f66f
author: rothja
ms.author: jroth
ms.openlocfilehash: 2f2909747ba42aaa3ff5c07777149fbcff5500f4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011183"
---
# <a name="sql-server-native-client-support-for-high-availability-disaster-recovery"></a>SQL Server Native Client の HADR サポート
  このトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client のサポート ([!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で追加) について説明します。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の詳細については、「[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../../database-engine/listeners-client-connectivity-application-failover.md)」、「[可用性グループの作成と構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)」、「[フェールオーバー クラスタリングと AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)」、および「[アクティブなセカンダリ: 読み取り可能なセカンダリ レプリカ (AlwaysOn 可用性グループ)](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。  
  
 接続文字列で、特定の可用性グループの可用性グループ リスナーを指定できます。 フェールオーバーする可用性グループ内のデータベースに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client アプリケーションが接続されている場合、元の接続が切断されるため、フェールオーバー後にアプリケーションが動作を継続するには新しい接続を開く必要があります。  
  
 可用性グループ リスナーに接続しておらず、ホスト名に複数の IP アドレスが関連付けられている場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は DNS エントリに関連付けられているすべての IP アドレスを順次繰り返し処理します。 これは、DNS サーバーによって返された最初の IP アドレスがネットワーク インターフェイス カード (NIC) にバインドされていない場合、時間がかかります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client が可用性グループ リスナーに接続するとき、すべての IP アドレスに対して並列で接続を試行します。1 つの接続試行が成功すると、保留中の接続試行はすべて破棄されます。  
  
> [!NOTE]  
>  接続タイムアウト値を大きくし、接続再試行ロジックを実装することにより、アプリケーションが可用性グループに接続する確立が高まります。 また、可用性グループのフェールオーバーにより接続が失敗する可能性があるため、接続再試行ロジックを実装して、再接続されるまで、失敗した接続の再接続を試行する必要があります。  
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover を使用した接続  
 SQL Server 2012 可用性グループ リスナーまたは SQL Server 2012 フェールオーバー クラスター インスタンスに接続する際には、必ず `MultiSubnetFailover=Yes` を指定してください。 `MultiSubnetFailover` を指定することで、SQL Server 2012 のすべての可用性グループおよびフェールオーバー クラスター インスタンスに対して高速フェールオーバーが有効化され、単一サブネットおよびマルチサブネットの AlwaysOn トポロジにおけるフェールオーバー時間が大幅に短縮されます。 複数のサブネットのフェールオーバーでは、クライアントは並列接続を試みます。 サブネット フェールオーバーの際には、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は積極的に TCP 接続を再試行します。  
  
 `MultiSubnetFailover` 接続プロパティを指定すると、アプリケーションが可用性グループまたはフェールオーバー クラスター インスタンスに配置され、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client がすべての IP アドレスに対して接続を試行することでプライマリ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス上のデータベースに接続を試みます。 `MultiSubnetFailover=Yes`が接続に対して指定されている場合、クライアントは、オペレーティングシステムの既定の tcp 再送信間隔よりも速く tcp 接続の試行を再試行します。 これは、AlwaysOn 可用性グループまたは AlwaysOn フェールオーバー クラスター インスタンスのフェールオーバー後のより高速な再接続を可能にし、単一および複数のサブネットの可用性グループおよびフェールオーバー クラスター インスタンスの両方に適用可能です。  
  
 接続文字列キーワードの詳細については、「[SQL Server Native Client での接続文字列キーワードの使用](../applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 接続先が可用性グループ リスナーでもフェールオーバー クラスター インスタンスでもないときに `MultiSubnetFailover=Yes` を指定すると、パフォーマンスが低下する可能性があるため、このような指定はサポートされません。  
  
 可用性グループまたはフェールオーバー クラスター インスタンス内のサーバーに接続する際には、次のガイドラインに従います。  
  
-   単一のサブネットまたは複数のサブネットへの接続時には、`MultiSubnetFailover` 接続プロパティを使用します。これにより、両方の場合でパフォーマンスが向上します。  
  
-   可用性グループに接続するには、使用する接続文字列でサーバーとして可用性グループの可用性グループ リスナーを指定します。  
  
-   64 個を超える数の IP アドレスが構成された [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続すると、接続エラーが発生します。  
  
-   `MultiSubnetFailover` 接続プロパティを使用するアプリケーションの動作は、認証の種類 ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証、Kerberos 認証、または Windows 認証) の影響を受けません。  
  
-   `loginTimeout` の値を増やすことで、フェールオーバー時間に対応し、アプリケーションの接続試行回数を減らすことができます。  
  
-   分散トランザクションはサポートされません。  
  
 読み取り専用のルーティングが無効である場合、次の状況では可用性グループのセカンダリ レプリカの場所には接続できません。  
  
1.  セカンダリ レプリカの場所が接続を受け入れないように構成されている場合。  
  
2.  アプリケーションが `ApplicationIntent=ReadWrite` (後で説明) を使用している場合、セカンダリ レプリカの場所は読み取り専用アクセスとして構成されます。  
  
 プライマリ レプリカが読み取り専用のワークロードを拒否するように設定され、接続文字列が  `ApplicationIntent=ReadOnly` を含んでいる場合、接続は失敗します。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>データベース ミラーリングから複数のサブネット クラスターを使用するためのアップグレード  
 接続文字列に `MultiSubnetFailover` および `Failover_Partner` の接続キーワードが存在する場合、接続エラーが発生します。 また、`MultiSubnetFailover` が使用されているとき、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から、データベース ミラーリング ペアに属していることを示すフェールオーバー パートナー応答が返された場合にも、エラーが発生します。  
  
 データベース ミラーリングを現在使用している [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client アプリケーションをマルチサブネットのシナリオにアップグレードする場合、`Failover_Partner` 接続プロパティを削除して `MultiSubnetFailover` に置き換え、それを `Yes` に設定し、接続文字列内のサーバー名を可用性グループ リスナーの名前に置き換えます。 接続文字列が `Failover_Partner` および `MultiSubnetFailover=Yes` を使用していると、ドライバーがエラーを生成します。 ただし、接続文字列が `Failover_Partner` および `MultiSubnetFailover=No` (または  `ApplicationIntent=ReadWrite`) を使用している場合、アプリケーションはデータベース ミラーリングを使用します。  
  
 可用性グループのプライマリデータベースでデータベースミラーリングが使用されていて、 `MultiSubnetFailover=Yes` 可用性グループリスナーではなくプライマリデータベースに接続する接続文字列でが使用されている場合、ドライバーはエラーを返します。  
  
## <a name="specifying-application-intent"></a>アプリケーションの目的の指定  
 `ApplicationIntent=ReadOnly` の場合、クライアントは AlwaysOn が有効になったデータベースに接続する場合に、読み取られたワークロードを要求します。 サーバーは、接続時および USE データベース ステートメントの間、その目的を強制しますが、AlwaysOn が有効になったデータベースに対してのみ、これを行います。  
  
 `ApplicationIntent` キーワードは従来の読み取り専用のデータベースでは機能しません。  
  
 データベースは、対象となる AlwaysOn データベースのワークロードの読み取りを許可または拒否できます。 (これは `ALLOW_CONNECTIONS` の `PRIMARY_ROLE` 句および `SECONDARY_ROLE`[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用して行います。)  
  
 `ApplicationIntent` キーワードは、読み取り専用のルーティングを有効にするために使用されます。  
  
## <a name="read-only-routing"></a>読み取り専用ルーティング  
 読み取り専用のルーティングはデータベースの読み取り専用のレプリカの可用性を確保できる機能です。 読み取り専用のルーティングを有効にするには次のことが必要です。  
  
1.  AlwaysOn 可用性グループの可用性グループ リスナーに接続する必要があります。  
  
2.  `ApplicationIntent` 接続文字列キーワードを `ReadOnly` に設定する必要があります。  
  
3.  可用性グループは、データベース管理者によって、読み取り専用のルーティングを有効にするように構成される必要があります。  
  
 読み取り専用のルーティングを使用する複数の接続のすべてが、同じ読み取り専用のレプリカに接続しないようにすることができます。 データベースの同期変更またはサーバーのルーティング構成の変更は、異なる読み取り専用のレプリカに対するクライアントの接続につながることがあります。 すべての読み取り専用の要求が、確実に同じ読み取り専用のレプリカに接続するようにするには、`Server` 接続文字列キーワードに可用性グループ リスナーを渡さないでください。 代わりに、読み取り専用のインスタンスの名前を指定します。  
  
 読み取り専用のルーティングでは、最初にプライマリに接続し、最適な可用性の読み取り可能なセカンダリを検索するため、プライマリに接続するよりも時間がかかる場合があります。 そのため、ログインのタイムアウトを増やす必要があります。  
  
## <a name="odbc"></a>ODBC  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] をサポートするために、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client には、次の 2 つの ODBC 接続文字列キーワードが追加されています。  
  
-   `ApplicationIntent`  
  
-   `MultiSubnetFailover`  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の ODBC 接続文字列キーワードの詳細については、「[SQL Server Native Client での接続文字列キーワードの使用](../applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 対応する接続プロパティは次のとおりです。  
  
-   `SQL_COPT_SS_APPLICATION_INTENT`  
  
-   `SQL_COPT_SS_MULTISUBNET_FAILOVER`  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の ODBC 接続文字列プロパティの詳細については、「[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)」を参照してください。  
  
 `ApplicationIntent` キーワードと `MultiSubnetFailover` キーワードの機能は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ドライバーを使用する DSN の ODBC データ ソース アドミニストレーターで公開されます ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降)。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC アプリケーションは、次に示した 3 つの関数のいずれかを使用して、接続を行うことができます。  
  
|機能|説明|  
|--------------|-----------------|  
|[SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)|`SQLBrowseConnect` から返されるサーバーの一覧に VNN は含まれません。 確認できるのはサーバーの一覧だけです。スタンドアロン サーバーであるのか、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が有効な 2 つ以上の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] インスタンスが含まれる Windows Server フェールオーバー クラスタリング (WSFC) クラスターのうちのプライマリ サーバーまたはセカンダリ サーバーであるのかは示されません。 サーバーへの接続時にエラーが返された場合、接続先のサーバーの構成に `ApplicationIntent` 設定との互換性がないことが原因として考えられます。<br /><br /> `SQLBrowseConnect` は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が有効な 2 つ以上の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] インスタンスが含まれる Windows Server フェールオーバー クラスタリング (WSFC) クラスター内のサーバーを認識しません。このため、`SQLBrowseConnect` 接続文字列キーワードは、`MultiSubnetFailover` では無視されます。|  
|[SQLConnect](../../native-client-odbc-api/sqlconnect.md)|`SQLConnect` は、データ ソース名 (DSN) または接続プロパティを介して、`ApplicationIntent` と `MultiSubnetFailover` の両方をサポートします。|  
|[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)|`SQLDriverConnect` は、接続文字列キーワード、接続プロパティ、または DSN を介して、`ApplicationIntent` と `MultiSubnetFailover` をサポートします。|  
  
## <a name="ole-db"></a>OLE DB (OLE DB)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の OLE DB では、`MultiSubnetFailover` キーワードはサポートされません。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の OLE DB では、アプリケーション インテントがサポートされます。 OLE DB アプリケーションにおけるアプリケーション インテントの動作は、ODBC アプリケーションの場合と同じです (上記を参照)。  
  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] をサポートするため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client には、次の OLE DB 接続文字列キーワードが追加されています。  
  
-   `Application Intent`  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の接続文字列キーワードの詳細については、「[SQL Server Native Client での接続文字列キーワードの使用](../applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 対応する接続プロパティは次のとおりです。  
  
-   `SSPROP_INIT_APPLICATIONINTENT`  
  
-   `DBPROP_INIT_PROVIDERSTRING`  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB アプリケーションは、次のいずれかの方法で、アプリケーション インテントを指定できます。  
  
 `IDBInitialize::Initialize`  
 `IDBInitialize::Initialize` は、あらかじめ構成された一連のプロパティを使用して、データ ソースを初期化し、データ ソース オブジェクトを作成します。 アプリケーション インテントは、プロバイダーのプロパティとして指定するか、拡張プロパティ文字列の一部として指定します。  
  
 `IDataInitialize::GetDataSource`  
 `IDataInitialize::GetDataSource` には、`Application Intent` キーワードを含んだ入力接続文字列を渡すことができます。  
  
 `IDBProperties::GetProperties`  
 `IDBProperties::GetProperties` は、現在データ ソースに設定されているプロパティの値を取得します。  `Application Intent` の値は、DBPROP_INIT_PROVIDERSTRING プロパティおよび SSPROP_INIT_APPLICATIONINTENT プロパティを通じて取得できます。  
  
 `IDBProperties::SetProperties`  
 `ApplicationIntent` プロパティの値を設定するには、`IDBProperties::SetProperties` を呼び出します。このとき、引数として、"`SSPROP_INIT_APPLICATIONINTENT`" または "`ReadWrite`" を値として持つ `ReadOnly` プロパティを指定するか、"`DBPROP_INIT_PROVIDERSTRING`" または "`ApplicationIntent=ReadOnly`" を値として持つ `ApplicationIntent=ReadWrite` プロパティを指定します。  
  
 アプリケーション インテントは、**[データ リンク プロパティ]** ダイアログ ボックスの [すべて] タブの [アプリケーション インテントのプロパティ] フィールドで指定できます。  
  
 暗黙的な接続が確立された場合、その接続には、親の接続のアプリケーション インテント設定が使用されます。 同様に、同じデータ ソースから作成されたセッションはいずれも、そのデータ ソースのアプリケーション インテント設定を継承します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)   
 [SQL Server Native Client での接続文字列キーワードの使用](../applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
  
