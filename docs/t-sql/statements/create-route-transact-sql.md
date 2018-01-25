---
title: "ルート (TRANSACT-SQL) を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_ROUTE_TSQL
- ROUTE
- CREATE ROUTE
- ROUTE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- lifetimes [Service Broker]
- routes [Service Broker], creating
- forwarding brokers [SQL Server]
- service names [Service Broker]
- database mirroring [SQL Server], routing
- expired routes [SQL Server]
- activating routes
- CREATE ROUTE statement
ms.assetid: 7e695364-1a98-4cfd-8ebd-137ac5a425b3
caps.latest.revision: "42"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 767be5069d65c11dad849a8fc32f5b15296a4eda
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="create-route-transact-sql"></a>CREATE ROUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新しいルートを現在のデータベース用のルーティング テーブルに追加します。 送信メッセージで[!INCLUDE[ssSB](../../includes/sssb-md.md)]をローカルのデータベース内のルーティング テーブルを調べてルーティングを決定します。 別のインスタンスで発生するメッセージ交換でメッセージを含むメッセージを転送する[!INCLUDE[ssSB](../../includes/sssb-md.md)]ルートを調べます**msdb**です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE ROUTE route_name  
[ AUTHORIZATION owner_name ]  
WITH    
   [ SERVICE_NAME = 'service_name', ]  
   [ BROKER_INSTANCE = 'broker_instance_identifier' , ]  
   [ LIFETIME = route_lifetime , ]  
   ADDRESS =  'next_hop_address'  
   [ , MIRROR_ADDRESS = 'next_hop_mirror_address' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *route_name*  
 作成するルートの名前を指定します。 新しいルートが現在のデータベースで作成され、AUTHORIZATION 句で指定されるプリンシパルによって所有されます。 サーバー名、データベース名、スキーマ名は指定できません。 *Route_name*は有効な**sysname**です。  
  
 AUTHORIZATION *owner_name*  
 ルートの所有者を、指定したデータベース ユーザーまたはロールに設定します。 *Owner_name* 、現在のユーザーがいずれかのメンバーである任意の有効なユーザーまたはロールの名前にすることができます、 **db_owner**固定データベース ロール、または**sysadmin**固定サーバー ロール。 それ以外の場合、 *owner_name*現在のユーザーの名前、現在のユーザーが、IMPERSONATE 権限を持っているユーザーの名前または現在のユーザーが所属するロールの名前にする必要があります。 この句を省略すると、ルートは現在のユーザーに属します。  
  
 のすべてのメンションを  
 作成されるルートを定義するための句を、WITH の後に指定します。  
  
 SERVICE_NAME = **'***service_name***'**  
 このルートが示すリモート サービスの名前を指定します。 *Service_name*値に使用するリモート サービスの名前が一致する必要があります。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]一致するように、バイトごとの比較を使用して、 *service_name*です。 つまり、この比較では大文字と小文字が区別され、現在の照合順序は考慮されません。 SERVICE_NAME が省略されると、このルートはすべてのサービス名と照合されることになりますが、SERVICE_NAME が指定されたルートより照合の優先度が下がります。 サービス名を持つルート**'SQL/ServiceBroker/BrokerConfiguration'** Broker Configuration Notice サービスへのルートです。 このサービスへのルートは、ブローカー インスタンスを指定できない場合があります。  
  
 BROKER_INSTANCE = **'***broker_instance_identifier***'**  
 発信先サービスをホストするデータベースを指定します。 *Broker_instance_identifier*パラメーターは、選択したデータベースで次のクエリを実行して取得できますが、リモート データベースのブローカー インスタンス識別子である必要があります。  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID()  
```  
  
 BROKER_INSTANCE 句を省略すると、このルートはすべてのブローカー インスタンスと照合されます。 ブローカー インスタンスを指定しないメッセージ交換では、すべてのブローカー インスタンスと照合されるルートは、明示的なブローカー インスタンスを持つルートよりも照合の優先度が高くなります。 ブローカー インスタンスを指定するメッセージ交換では、ブローカー インスタンスを持つルートの方が、すべてのブローカー インスタンスと照合されるルートより優先度が高くなります。  
  
 有効期間 **= * * * route_lifetime*  
 時間を秒単位で指定される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ルーティング テーブルにルートを保持します。 有効期間の最後に、ルートの有効期限、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]新しいメッセージ交換のルートを選択するときに、ルートを不可と見なされます。 この句を省略した場合、 *route_lifetime*が NULL で、ルートの有効期限が切れることはありません。  
  
 ADDRESS **='***next_hop_address***'**  
 ルート用のネットワーク アドレスを指定します。 *Next_hop_address*次の形式で TCP/IP アドレスを指定します。  
  
 **TCP://**{ *dns_name* | *netbios_name* | *ip_address* } **:***port_number*  
  
 指定した*port_number*のポート番号に一致する必要があります、[!INCLUDE[ssSB](../../includes/sssb-md.md)]のインスタンスのエンドポイント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定したコンピューターにします。 これは選択したデータベースで次のクエリを実行することにより取得できます。  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 ミラー化されたデータベースでサービスがホストされる場合、ミラー化されたデータベースをホストする別のインスタンスに対しても、MIRROR_ADDRESS を指定する必要があります。 それ以外の場合は、このルートはミラーに対してフェールオーバーしません。  
  
 ルート**'LOCAL'**の*next_hop_address*の現在のインスタンス内のサービスにメッセージを配信[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ルート**'TRANSPORT'**の*next_hop_address*、ネットワーク アドレスは、サービスの名前のネットワーク アドレスに基づいて決定されます。 指定するルート**'TRANSPORT'**サービス名またはブローカー インスタンスを指定しない場合があります。  
  
 MIRROR_ADDRESS **='***next_hop_mirror_address***'**  
 ミラー化されたデータベースがホストされているいずれかでミラー化されたデータベースのネットワーク アドレスを指定します、 *next_hop_address*です。 *Next_hop_mirror_address*次の形式で TCP/IP アドレスを指定します。  
  
 **TCP://**{ *dns_name* | *netbios_name* | *ip_address* } **:** *port_number*  
  
 指定した*port_number*のポート番号に一致する必要があります、[!INCLUDE[ssSB](../../includes/sssb-md.md)]のインスタンスのエンドポイント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定したコンピューターにします。 これは選択したデータベースで次のクエリを実行することにより取得できます。  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 MIRROR_ADDRESS が指定されている場合、ルートには SERVICE_NAME 句と BROKER_INSTANCE 句を指定する必要があります。 指定するルート**'LOCAL'**または**'TRANSPORT'**の*next_hop_address*ミラー アドレスを指定しない場合があります。  
  
## <a name="remarks"></a>解説  
 ルートを格納するルーティング テーブルを読み取ることができるメタデータ テーブル、 **sys.routes**カタログ ビューです。 このカタログ ビューを更新できるのは、CREATE ROUTE、ALTER ROUTE、および DROP ROUTE ステートメントだけです。  
  
 既定では、各ユーザー データベースにあるルーティング テーブルには 1 つのルートが含まれています。 このルートの名前は**AutoCreatedLocal**です。 ルート**'LOCAL'**の*next_hop_address*任意のサービス名およびブローカー インスタンス識別子と一致するとします。  
  
 ルート**'TRANSPORT'**の*next_hop_address*、ネットワーク アドレスは、サービスの名前に基づいて決定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有効な形式でネットワーク アドレスで始まるサービス名を正常に処理できる、 *next_hop_address*です。  
  
 ルートで指定されているサービス、ネットワーク アドレス、およびブローカー インスタンス識別子が同じであれば、ルーティング テーブルにはルートをいくつでも含めることができます。 このような場合、[!INCLUDE[ssSB](../../includes/sssb-md.md)] でルートを選択するときには、メッセージ交換で指定された情報とルーティング テーブル内の情報を照合して、最も正確に一致する情報を取得するためのプロシージャが使用されます。  
  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)]ルーティング テーブルから期限の切れたルートは削除されません。 期限の切れたルートは、ALTER ROUTE ステートメントを使用してアクティブにすることができます。  
  
 ルートは一時オブジェクトとして指定できません。 ルート名で始まる **#** 許可されますが、パーマネント オブジェクト。  
  
## <a name="permissions"></a>権限  
 ルートの既定値のメンバーを作成するためのアクセス許可、 **db_ddladmin**または**db_owner**固定データベース ロールおよび**sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-tcpip-route-by-using-a-dns-name"></a>A. DNS 名を使用して TCP/IP ルートを作成する  
 次の例では、サービスへのルート`//Adventure-Works.com/Expenses`です。 このルートでは、このサービスへのメッセージが、TCP 経由で DNS 名 `1234` に対応するホスト上のポート `www.Adventure-Works.com` に伝達されるように指定します。 対象サーバーは、一意の識別子によって識別されるブローカー インスタンスに到着したときにメッセージを配信`D8D4D268-00A3-4C62-8F91-634B89C1E315`です。  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89C1E315',  
    ADDRESS = 'TCP://www.Adventure-Works.com:1234' ;  
```  
  
### <a name="b-creating-a-tcpip-route-by-using-a-netbios-name"></a>B. NetBIOS 名を使用して TCP/IP ルートを作成する  
 次の例では、サービスへのルート`//Adventure-Works.com/Expenses`です。 このルートでは、このサービスへのメッセージが、TCP 経由で NetBIOS 名 `1234` に対応するホスト上のポート `SERVER02` へ伝達されるように指定します。 ターゲット、到着したときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一意識別子で識別されるデータベース インスタンスにメッセージが配信`D8D4D268-00A3-4C62-8F91-634B89C1E315`です。  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH   
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89C1E315',  
    ADDRESS = 'TCP://SERVER02:1234' ;  
```  
  
### <a name="c-creating-a-tcpip-route-by-using-an-ip-address"></a>C. IP アドレスを使用して TCP/IP ルートを作成する  
 次の例では、サービスへのルート`//Adventure-Works.com/Expenses`です。 このルートでは、このサービスへのメッセージが、TCP 経由で IP アドレス `1234` にあるホスト上のポート `192.168.10.2` へ伝達されるように指定します。 ターゲット、到着したときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一意識別子で識別されるブローカー インスタンスにメッセージが配信`D8D4D268-00A3-4C62-8F91-634B89C1E315`です。  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89C1E315',  
    ADDRESS = 'TCP://192.168.10.2:1234' ;  
```  
  
### <a name="d-creating-a-route-to-a-forwarding-broker"></a>D. 転送ブローカーへのルートを作成する  
 次の例では、サーバー `dispatch.Adventure-Works.com` の転送ブローカーへのルートを作成します。 サービス名とブローカー インスタンス識別子の両方が指定されていないため[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このルートを他のルートが定義されているを持たないサービスを使用します。  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    ADDRESS = 'TCP://dispatch.Adventure-Works.com' ;   
```  
  
### <a name="e-creating-a-route-to-a-local-service"></a>E. ローカル サービスへのルートを作成する  
 次の例では、サービスへのルート`//Adventure-Works.com/LogRequests`ルートと同じインスタンスにします。  
  
```  
CREATE ROUTE LogRequests  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/LogRequests',  
    ADDRESS = 'LOCAL' ;  
```  
  
### <a name="f-creating-a-route-with-a-specified-lifetime"></a>F. 有効期間が指定されたルートを作成する  
 次の例では、サービスへのルート`//Adventure-Works.com/Expenses`です。 ルートの有効期間は、`259200` 秒、つまり 72 時間です。  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    LIFETIME = 259200,  
    ADDRESS = 'TCP://services.Adventure-Works.com:1234' ;  
```  
  
### <a name="g-creating-a-route-to-a-mirrored-database"></a>G. ミラー化されたデータベースへのルートを作成する  
 次の例では、サービスへのルート`//Adventure-Works.com/Expenses`です。 サービスは、ミラー化されたデータベースでホストされています。 ミラー化されたデータベースの 1 つは、アドレスにある`services.Adventure-Works.com:1234`、他のデータベースが、アドレスであると`services-mirror.Adventure-Works.com:1234`です。  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = '69fcc80c-2239-4700-8437-1001ecddf933',  
    ADDRESS = 'TCP://services.Adventure-Works.com:1234',   
    MIRROR_ADDRESS = 'TCP://services-mirror.Adventure-Works.com:1234' ;  
```  
  
### <a name="h-creating-a-route-that-uses-the-service-name-for-routing"></a>H. ルーティング用のサービス名を使用するルートを作成する  
 次の例では、メッセージの送信先となるネットワーク アドレスを判別するためにサービス名が使用されるルートを作成します。 ネットワーク アドレスとして `'TRANSPORT'` を指定するルートは、他のルートより照合の優先度が低いことに注意してください。  
  
```  
CREATE ROUTE TransportRoute  
    WITH ADDRESS = 'TRANSPORT' ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER ROUTE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-route-transact-sql.md)   
 [DROP ROUTE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-route-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
