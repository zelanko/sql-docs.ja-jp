---
title: "検証を伴わない暗号化を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], encryption
- cryptography [SQL Server Native Client]
- SQLNCLI, encryption
- encryption [SQL Server Native Client]
- SQL Server Native Client, encryption
ms.assetid: f4c63206-80bb-4d31-84ae-ccfcd563effa
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1d29061f3c43735b9a3855cee0dd635face3db00
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="using-encryption-without-validation"></a>検証を伴わない暗号化の使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、常に、ログインに関連するネットワーク パケットを暗号化します。 サーバーの起動時に証明書がサーバーに提供されないと、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はログイン パケットの暗号化に使用される自己署名入りの証明書を生成します。  
  
 アプリケーションでは、接続文字列キーワードまたは接続プロパティを使用して、すべてのネットワーク トラフィックの暗号化を要求することもできます。 キーワードは、ODBC および OLE DB の"Encrypt"のプロバイダー文字列の使用時**idbinitialize::initialize**、または"Use Encryption for Data"ADO および OLE DB 初期化文字列を使用する場合の**IDataInitialize**. これによっても構成可能性があります[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager を使用して、 **Force Protocol Encryption**オプション。 既定では、接続のネットワーク トラフィックをすべて暗号化するには、証明書をサーバーに提供する必要があります。  
  
 接続文字列キーワードについては、次を参照してください。[使用した Connection String Keywords with SQL Server Native Client を使用して](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)です。  
  
 サーバーで、証明書がプロビジョニングされていないときに使用される暗号化を有効にする[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]構成マネージャーを使用して、両方を設定できます、 **Force Protocol Encryption**と**Trust Server Certificate**オプション。 この場合、検証可能な証明書がサーバーに提供されなかった場合は、暗号化には検証を伴わない自己署名入りのサーバー証明書を使用します。  
  
 アプリケーションでは、暗号化が行われることを保証するために "TrustServerCertificate" キーワードまたはそれに関連する接続属性も使用できます。 アプリケーションの設定によって、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント構成マネージャーで設定されるセキュリティのレベルを緩和することはできません。ただし、厳密にすることはできます。 たとえば場合、 **Force Protocol Encryption**が設定されていないアプリケーションはクライアントは、暗号化自体を要求する可能性があります。 サーバー証明書が提供されなかった場合でも暗号化を保証するには、アプリケーションから暗号化と "TrustServerCertificate" を要求できます。 ただし、クライアントの構成で "TrustServerCertificate" が有効になっていない場合は、サーバー証明書を提供する必要があります。 次の表ですべてのケースを説明します。  
  
|[Force Protocol Encryption] クライアント設定|[Trust Server Certificate] クライアント設定|接続文字列/接続属性 Encrypt/Use Encryption for Data|接続文字列/接続属性 Trust Server Certificate|結果|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|不可|なし|いいえ (既定値)|無視|暗号化は行われません。|  
|不可|なし|可|いいえ (既定値)|暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。|  
|不可|なし|可|可|暗号化は常に行われますが、自己署名入りのサーバー証明書を使用することがあります。|  
|可|不可|無視|無視|暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。|  
|可|可|いいえ (既定値)|無視|暗号化は常に行われますが、自己署名入りのサーバー証明書を使用することがあります。|  
|可|可|可|いいえ (既定値)|暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。|  
|可|可|可|可|暗号化は常に発生するが自己署名サーバー証明書を使用する場合があります。|  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB プロバイダー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーには、DBPROPSET_SQLSERVERDBINIT プロパティで実装される SSPROP_INIT_TRUST_SERVER_CERTIFICATE データ ソース初期化プロパティの追加によって検証を伴わない暗号化がサポートしています設定します。 さらに、新しい接続文字列キーワード、"TrustServerCertificate"のように追加されました。 "TrustServerCertificate" は、yes または no を値として受け取ります。既定値は no です。 サービス コンポーネントを使用しているときは、"TrustServerCertificate" は true または false を値として受け取ります。既定値は false です。  
  
 DBPROPSET_SQLSERVERDBINIT プロパティ セットへの拡張機能の詳細については、次を参照してください。[初期化プロパティと承認プロパティ](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)です。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC ドライバー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーには、検証への追加を伴わない暗号化がサポートしている、 [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)と[SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)関数。 SQL_TRUST_SERVER_CERTIFICATE_YES または SQL_TRUST_SERVER_CERTIFICATE_NO を受け取る、SQL_COPT_SS_TRUST_SERVER_CERTIFICATE が追加されました。既定値は SQL_TRUST_SERVER_CERTIFICATE_NO です。 また、新しい接続文字列のキーワードとして "TrustServerCertificate" が追加されました。 "TrustServerCertificate" は、"yes" または "no" を値として受け取ります。既定値は "no" です。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
