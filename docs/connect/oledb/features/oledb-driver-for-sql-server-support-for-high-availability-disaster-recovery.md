---
title: SQL Server Support for High Availability, Disaster Recovery の OLE DB Driver |Microsoft ドキュメント
description: OLE DB Driver for SQL Server は、高可用性、災害復旧のサポートします。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c915af2ec748c4b2c15882c9a643c8e200442e98
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="ole-db-driver-for-sql-server-support-for-high-availability-disaster-recovery"></a>SQL Server Support for High Availability, Disaster Recovery の OLE DB ドライバー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  この記事では、SQL Server のサポートの OLE DB Driver がについて説明します (で追加された[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) の[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]します。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の詳細については、「[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)」、「[可用性グループの作成と構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)」、「[フェールオーバー クラスタリングと AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)」、および「[アクティブなセカンダリ: 読み取り可能なセカンダリ レプリカ &#40;AlwaysOn 可用性グループ&#41;](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。  
  
 接続文字列で、特定の可用性グループの可用性グループ リスナーを指定できます。 OLE DB Driver for SQL Server アプリケーションがフェールオーバーする可用性グループ内のデータベースに接続されている場合は、元の接続が切断と、アプリケーションは、フェールオーバー後の作業を続行する新しい接続を開く必要があります。  
  
 場合は、可用性グループ リスナーに接続していないと、OLE DB Driver for SQL Server が、DNS エントリに関連付けられているすべての IP アドレスを順番に反復処理が複数の IP アドレスが、ホスト名に関連付けられている場合は、します。 DNS サーバーが最初に返した IP アドレスがネットワーク インターフェイス カード (NIC) にバインドされていない場合、この処理に時間がかかる可能性があります。 OLE DB Driver for SQL Server が並列ですべての IP アドレスへの接続を確立しようとした接続する場合、可用性グループ リスナー、および接続の試行が成功すると、ドライバーに保留中の接続しようとすると破棄されます。  
  
> [!NOTE]  
> 接続タイムアウト値を大きくし、接続再試行ロジックを実装することにより、アプリケーションが可用性グループに接続する確立が高まります。 また、可用性グループのフェールオーバーにより接続が失敗する可能性があるため、接続再試行ロジックを実装して、再接続されるまで、失敗した接続の再接続を試行する必要があります。  
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover を使用した接続  
 常に指定**MultiSubnetFailover = [はい]** SQL Server Always On 可用性グループ リスナーに接続するときまたは[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス。 **MultiSubnetFailover**すべての Always On 可用性グループおよびフェールオーバー クラスター インスタンスに対して高速フェールオーバーを有効に[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、し、単一およびマルチ サブネットの Alwayson トポロジにおけるフェールオーバー時間が大幅に低下します。 マルチサブネット フェールオーバーの際には、クライアントは複数の接続を並列で試行します。 サブネットのフェールオーバー中に OLE DB Driver for SQL Server は TCP 接続を再試行します。  
  
 **MultiSubnetFailover**接続プロパティことを示し、アプリケーションが可用性グループまたはフェールオーバー クラスター インスタンスに配置され、OLE DB Driver for SQL Server は、上のデータベースに接続しようとしています、プライマリ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]すべての ip アドレスに接続しようとしてのインスタンスに対応します。 接続に対して **MultiSubnetFailover=Yes** を指定した場合、クライアントは、オペレーティング システムの既定の TCP 再送信間隔より短い間隔で TCP 接続を再試行します。 これは、Always On 可用性グループまたはフェールオーバー クラスター インスタンスのいずれかのフェールオーバー後に高速再接続を有効とは、単一およびマルチ サブネットの可用性グループとフェールオーバー クラスター インスタンスの両方に適用します。  
  
 接続文字列キーワードの詳細については、次を参照してください。 [OLE DB Driver for SQL Server での接続文字列キーワードの使用](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)です。  
  
 可用性グループ リスナーまたはフェールオーバー クラスター インスタンス以外に接続するときに **MultiSubnetFailover=Yes** を指定するとパフォーマンスが低下する可能性があるため、このような指定はサポートされていません。  
  
 可用性グループまたはフェールオーバー クラスター インスタンス内のサーバーに接続する際には、次のガイドラインに従います。  
  
-   単一サブネットまたはマルチサブネットに接続する場合に **MultiSubnetFailover** 接続プロパティを使用すると、パフォーマンスを向上させることができます。  
  
-   可用性グループに接続するには、接続文字列でサーバーとして、可用性グループの可用性グループ リスナーを指定します。  
  
-   64 個を超える数の IP アドレスが構成された [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続すると、接続エラーが発生します。  
  
-   **MultiSubnetFailover** 接続プロパティを使用するアプリケーションの動作は、認証の種類 ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証、Kerberos 認証、または Windows 認証) の影響を受けません。  
  
-   **loginTimeout** の値を増やすことで、フェールオーバー時間に対応し、アプリケーションの接続試行回数を減らすことができます。  
  
-   分散トランザクションはサポートされていません。  
  
読み取り専用のルーティングが無効である場合、次の状況では可用性グループのセカンダリ レプリカの場所には接続できません。  
  
1.  セカンダリ レプリカの場所が、接続を許可するように構成されていない。  
  
2.  アプリケーションに **ApplicationIntent=ReadWrite** (後述します) が使用されているが、セカンダリ レプリカの場所が読み取り専用アクセスとして構成されている。  
  
プライマリ レプリカが読み取り専用ワークロードを拒否するように構成されているとき、接続文字列に **ApplicationIntent=ReadOnly** が含まれていると、接続は失敗します。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>データベース ミラーリングの使用からマルチサブネット クラスターの使用へのアップグレード  
接続文字列に **MultiSubnetFailover** および **Failover_Partner** の接続キーワードが存在する場合、接続エラーが発生します。 また、**MultiSubnetFailover** が使用されているとき、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から、データベース ミラーリング ペアに属していることを示すフェールオーバー パートナー応答が返された場合にも、エラーが発生します。  
  
アップグレードする場合は、OLE DB Driver for SQL Server アプリケーションが現在そのデータベースがマルチ サブネット シナリオにミラーリングを使用して、削除する必要があります、 **Failover_Partner**接続プロパティと、コードに置き換えます**MultiSubnetFailover** 'éý'**はい**し、接続文字列でサーバー名を可用性グループ リスナーに置き換えます。 接続文字列で **Failover_Partner** および **MultiSubnetFailover=Yes** が使用されている場合、ドライバーでエラーが発生します。 ただし、接続文字列に **Failover_Partner** と **MultiSubnetFailover=No** (または **ApplicationIntent=ReadWrite**) が使用されている場合、アプリケーションはデータベース ミラーリングを使用します。  
  
ドライバーは、可用性グループのプライマリ データベースでデータベース ミラーリングが使用されている場合、および可用性グループ リスナーではなくプライマリ データベースに接続する接続文字列内で **MultiSubnetFailover=Yes** が使用されている場合、エラーを返します。  
  
## <a name="specifying-application-intent"></a>アプリケーション インテントの指定  
ときに**ApplicationIntent = ReadOnly**、Alwayson が有効なデータベースに接続するときに、クライアントが読み取りワークロードを要求します。 接続時に、中に、サーバーの目的は強制する、`USE`がデータベースにのみ、Alwayson が有効なステートメントをデータベースします。  
  
**ApplicationIntent** キーワードは、従来の読み取り専用データベースに対しては無効です。  
  
データベースでは、許可したり、対象の Always On データベース ワークロードの読み取りを許可しないようにすることができます。 (これは、**PRIMARY_ROLE** および **SECONDARY_ROLE**[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントの **ALLOW_CONNECTIONS** 句で実行します)。  
  
読み取り専用ルーティングを有効にするには、**ApplicationIntent** キーワードを使用します。  
  
## <a name="read-only-routing"></a>読み取り専用ルーティング  
読み取り専用ルーティングは、データベースの読み取り専用レプリカの可用性を実現する機能です。 読み取り専用のルーティングを有効にするには  
  
1.  AlwaysOn 可用性グループ リスナーに接続する必要があります。  
  
2.  **ApplicationIntent** 接続文字列キーワードを **ReadOnly**に設定する必要があります。  
  
3.  データベース管理者は、読み取り専用ルーティングを有効にする、Always On 可用性グループを構成する必要があります。  
  
読み取り専用のルーティングを使用した複数の接続が同じ読み取り専用レプリカに接続されるとは限りません。 データベース同期の変更やサーバーのルーティング構成の変更によって、クライアントが別の読み取り専用レプリカに接続される場合があります。 すべての読み取り専用要求が同じ読み取り専用レプリカに接続を確認してください、渡さないで、Always On 可用性グループ リスナーを**サーバー**接続文字列キーワードです。 代わりに、読み取り専用インスタンスの名前を指定します。  
  
読み取り専用ルーティングでは、最初にプライマリに接続した後、使用できる最善の読み取り可能セカンダリが検索されます。このため、読み取り専用ルーティングに要する時間は、プライマリに接続するよりも長くなります。 このため、ログイン タイムアウトを大きくする必要があります。  
  
## <a name="ole-db"></a>OLE DB (OLE DB)  
SQL Server の OLE DB Driver は、両方をサポート、 **ApplicationIntent**と**MultiSubnetFailover**キーワード。   
  
2 つの OLE DB 接続文字列キーワードがサポートするために追加された[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]OLE DB Driver for SQL Server で。  
  
-   **ApplicationIntent** 
-   **MultiSubnetFailover**  
  
 SQL Server の OLE DB ドライバーで接続文字列キーワードの詳細については、次を参照してください。 [OLE DB Driver for SQL Server での接続文字列キーワードの使用](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)です。  

### <a name="application-intent"></a>アプリケーションの目的 

対応する接続プロパティは次のとおりです。  
  
-   **SSPROP_INIT_APPLICATIONINTENT**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  
  
OLE DB Driver for SQL Server アプリケーションは、アプリケーションの目的を指定するのにのいずれかを使用できます。  
  
 -   **Idbinitialize::initialize**  
 **IDBInitialize::Initialize** は、あらかじめ構成された一連のプロパティを使用して、データ ソースを初期化し、データ ソース オブジェクトを作成します。 アプリケーション インテントは、プロバイダーのプロパティとして指定するか、拡張プロパティ文字列の一部として指定します。  
  
 -   **Idatainitialize::getdatasource**  
 **IDataInitialize::GetDataSource** は **Application Intent** キーワードを格納できる入力接続文字列を受け取ります。  
  
 -   **IDBProperties::SetProperties**  
 **ApplicationIntent** プロパティ値を設定するには、**IDBProperties::SetProperties** を呼び出して、"**ReadWrite**" または "**ReadOnly**" の値で **SSPROP_INIT_APPLICATIONINTENT** プロパティを渡すか、または "**ApplicationIntent=ReadOnly**" または "**ApplicationIntent=ReadWrite**" を含む値で **DBPROP_INIT_PROVIDERSTRING** プロパティを渡します。  
  
アプリケーション インテントは、**[データ リンク プロパティ]** ダイアログ ボックスの [すべて] タブの [アプリケーション インテントのプロパティ] フィールドで指定できます。  
  
暗黙的な接続が確立された場合、その接続には、親の接続のアプリケーション インテント設定が使用されます。 同様に、同じデータ ソースから作成されたセッションはいずれも、そのデータ ソースのアプリケーション インテント設定を継承します。  
  
### <a name="multisubnetfailover"></a>MultiSubnetFailover

対応する接続プロパティは次のとおりです。  
  
-   **SSPROP_INIT_MULTISUBNETFAILOVER**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  

OLE DB Driver for SQL Server アプリケーションは、MultiSubnetFailover オプションの設定に、次のメソッドのいずれかを使用できます。  

 -   **Idbinitialize::initialize**  
 **IDBInitialize::Initialize** は、あらかじめ構成された一連のプロパティを使用して、データ ソースを初期化し、データ ソース オブジェクトを作成します。 アプリケーション インテントは、プロバイダーのプロパティとして指定するか、拡張プロパティ文字列の一部として指定します。  
  
 -   **Idatainitialize::getdatasource**  
 **Idatainitialize::getdatasource**は含めることができる入力接続文字列を受け取り、 **MultiSubnetFailover**キーワード。  

-   **IDBProperties::SetProperties**  
設定する、 **MultiSubnetFailover**プロパティ値、呼び出し**idbproperties::setproperties**を渡して、 **SSPROP_INIT_MULTISUBNETFAILOVER** の値を持つプロパティ**VARIANT_TRUE**または**VARIANT_FALSE**または**DBPROP_INIT_PROVIDERSTRING**プロパティを含む値を"**MultiSubnetFailover = Yes**「または」**MultiSubnetFailover = いいえ**"です。

#### <a name="example"></a>例

```
DBPROP rgPropMultisubnet;

rgPropMultisubnet.dwPropertyID = SSPROP_INIT_MULTISUBNETFAILOVER;
rgPropMultisubnet.dwOptions = DBPROPOPTIONS_REQUIRED;
rgPropMultisubnet.dwStatus = DBPROPSTATUS_OK;
rgPropMultisubnet.colid = DB_NULLID;
V_VT(&(rgPropMultisubnet.vValue)) = VT_BOOL;
V_BOOL(&(rgPropMultisubnet.vValue)) = VARIANT_TRUE;

DBPROPSET PropSet;

PropSet.rgProperties = &rgPropMultisubnet;
PropSet.cProperties = 1;
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;
IDBProperties* pIDBProperties = NULL;
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);
pIDBProperties->SetProperties(1, &PropSet);
```

## <a name="see-also"></a>参照  
 [SQL Server 機能の OLE DB ドライバー](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [OLE DB Driver for SQL Server での接続文字列キーワードの使用](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)  
  
  
