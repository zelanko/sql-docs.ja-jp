---
title: "ALTER ROUTE (TRANSACT-SQL) |Microsoft ドキュメント"
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
- ALTER_ROUTE_TSQL
- ALTER ROUTE
dev_langs: TSQL
helpviewer_keywords:
- ALTER ROUTE statement
- dropping routes
- modifying routes
- removing routes
- routes [Service Broker], modifying
ms.assetid: 8dfb7b16-3dac-4e1e-8c97-adf2aad07830
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 221fcf4d801d062d491935c8380abd4f75b83285
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="alter-route-transact-sql"></a>ALTER ROUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のルートに関するルート情報を変更[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER ROUTE route_name  
WITH    
  [ SERVICE_NAME = 'service_name' [ , ] ]  
  [ BROKER_INSTANCE = 'broker_instance' [ , ] ]  
  [ LIFETIME = route_lifetime [ , ] ]  
  [ ADDRESS =  'next_hop_address' [ , ] ]  
  [ MIRROR_ADDRESS = 'next_hop_mirror_address' ]  
[ ; ]  
  
```  
  
## <a name="arguments"></a>引数  
 *route_name*  
 変更するルートの名前を指定します。 サーバー名、データベース名、スキーマ名は指定できません。  
  
 WITH  
 変更するルート情報を定義するための句を、WITH の後に指定します。  
  
 SERVICE_NAME **='***service_name***'**  
 このルートが示すリモート サービスの名前を指定します。 *Service_name*値に使用するリモート サービスの名前が一致する必要があります。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]一致するように、バイトごとの比較を使用して、 *service_name*です。 つまり、この比較では大文字と小文字が区別され、現在の照合順序は考慮されません。 サービス名を持つルート**'SQL/ServiceBroker/BrokerConfiguration'** Broker Configuration Notice サービスへのルートです。 このサービスへのルートは、ブローカー インスタンスを指定できない場合があります。  
  
 SERVICE_NAME 句を省略した場合、ルートのサービス名は変更されません。  
  
 BROKER_INSTANCE **='***broker_instance***'**  
 発信先サービスをホストするデータベースを指定します。 *Broker_instance*パラメーターは、選択したデータベースで次のクエリを実行して取得できますが、リモート データベースのブローカー インスタンス識別子である必要があります。  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID();  
```  
  
 BROKER_INSTANCE 句を省略した場合、ルートのブローカー インスタンスは変更されません。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 有効期間 **=**  *route_lifetime*  
 時間を秒単位で指定される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ルーティング テーブルにルートを保持します。 有効期間の最後に、ルートの有効期限、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]新しいメッセージ交換のルートを選択するときに、ルートを不可と見なされます。 この句を省略した場合、ルートの有効期限は変更されません。  
  
 アドレス**='***next_hop_address'*  
 ルート用のネットワーク アドレスを指定します。 *Next_hop_address*次の形式で TCP/IP アドレスを指定します。  
  
 **TCP://** { *dns_name* | *netbios_name* |*ip_address* } **:** *port_number*  
  
 指定した*port_number*のポート番号に一致する必要があります、[!INCLUDE[ssSB](../../includes/sssb-md.md)]のインスタンスのエンドポイント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定したコンピューターにします。 これは選択したデータベースで次のクエリを実行することにより取得できます。  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 ルート**'LOCAL'**の*next_hop_address*の現在のインスタンス内のサービスにメッセージを配信[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ルート**'TRANSPORT'**の*next_hop_address*、ネットワーク アドレスは、サービスの名前のネットワーク アドレスに基づいて決定されます。 指定するルート**'TRANSPORT'**サービス名またはブローカー インスタンスを指定できます。  
  
 ときに、 *next_hop_address*プリンシパル サーバーは、データベース ミラーは、ミラー サーバーの MIRROR_ADDRESS も指定する必要があります。 それ以外の場合、このルートではミラー サーバーへの自動フェールオーバーは行われません。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 MIRROR_ADDRESS **='***next_hop_mirror_address***'**  
 ミラー サーバーがプリンシパル サーバーが、ミラー化のネットワーク アドレスを指定します、 *next_hop_address*です。 *Next_hop_mirror_address*次の形式で TCP/IP アドレスを指定します。  
  
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
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
## <a name="remarks"></a>解説  
 ルートを格納するルーティング テーブルを読み取ることができるメタデータ テーブル、 **sys.routes**カタログ ビューです。 このルーティング テーブルは、CREATE ROUTE、ALTER ROUTE、および DROP ROUTE ステートメントでのみ更新できます。  
  
 ALTER ROUTE コマンドで指定できない句に関する情報は、変更されません。 したがって、ALTER を使用して、ルートのタイムアウトを無効にしたり、ルートをすべてのサービス名やブローカー インスタンスと照合するような変更はできません。 このようなルート情報を変更するには、既存のルートを削除して新しいルートを作成し、新しい情報を指定する必要があります。  
  
 ルート**'TRANSPORT'**の*next_hop_address*、ネットワーク アドレスは、サービスの名前に基づいて決定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有効な形式でネットワーク アドレスで始まるサービス名を正常に処理できる、 *next_hop_address*です。 名前に有効なネットワーク アドレスが含まれているサービスは、そのサービス名のネットワーク アドレスにルートされます。  
  
 ルートで指定されているサービス、ネットワーク アドレス、ブローカー インスタンス識別子のいずれか、またはすべてが同じであれば、ルーティング テーブルにはルートをいくつでも含めることができます。 このような場合、[!INCLUDE[ssSB](../../includes/sssb-md.md)] でルートを選択するときには、メッセージ交換で指定された情報とルーティング テーブル内の情報を照合して、最も正確に一致する情報を取得するためのプロシージャが使用されます。  
  
 サービスの AUTHORIZATION を変更するには、ALTER AUTHORIZATION ステートメントを使用します。  
  
## <a name="permissions"></a>Permissions  
 ルートを変更するためのアクセス許可の既定値は、ルートのメンバーの所有者、 **db_ddladmin**または**db_owner**固定データベース ロールのメンバー、 **sysadmin**固定サーバーの役割。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-service-for-a-route"></a>A. ルートのサービスを変更する  
 次の例では、`ExpenseRoute` ルートが示すサービスを、リモート サービス `//Adventure-Works.com/Expenses` に変更します。  
  
```  
ALTER ROUTE ExpenseRoute  
   WITH   
     SERVICE_NAME = '//Adventure-Works.com/Expenses';  
```  
  
### <a name="b-changing-the-target-database-for-a-route"></a>B. ルートの対象データベースを変更する  
 次の例では、`ExpenseRoute` ルートの対象データベースを、一意識別子 `D8D4D268-00A3-4C62-8F91-634B89B1E317.` によって指定されるデータベースに変更します。  
  
```  
ALTER ROUTE ExpenseRoute  
   WITH   
     BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89B1E317';  
```  
  
### <a name="c-changing-the-address-for-a-route"></a>C. ルートのアドレスを変更する  
 次の例は、ネットワーク アドレスを変更、 `ExpenseRoute` TCP ポートへのルート`1234`IP アドレスを持つホストで`10.2.19.72`です。  
  
```  
ALTER ROUTE ExpenseRoute   
   WITH   
     ADDRESS = 'TCP://10.2.19.72:1234';  
```  
  
### <a name="d-changing-the-database-and-address-for-a-route"></a>D. ルートのデータベースとアドレスを変更する  
 次の例では、`ExpenseRoute` ルートのネットワーク アドレスを、DNS 名 `1234` のホスト、TCP ポート `www.Adventure-Works.com` に変更します。 また、対象データベースを、一意識別子 `D8D4D268-00A3-4C62-8F91-634B89B1E317` によって指定されるデータベースに変更します。  
  
```  
ALTER ROUTE ExpenseRoute  
   WITH   
     BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89B1E317',  
     ADDRESS = 'TCP://www.Adventure-Works.com:1234';  
```  
  
## <a name="see-also"></a>参照  
 [CREATE ROUTE &#40;Transact-SQL&#41;](../../t-sql/statements/create-route-transact-sql.md)   
 [DROP ROUTE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-route-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
