---
title: 検証を伴わない暗号化の使用 | Microsoft Docs
description: SQL Server Native Client OLE DB プロバイダーと ODBC ドライバーが、検証を行わずに暗号化をサポートする方法と、使用する場合の推奨事項について説明します。
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], encryption
- cryptography [SQL Server Native Client]
- SQLNCLI, encryption
- encryption [SQL Server Native Client]
- SQL Server Native Client, encryption
ms.assetid: f4c63206-80bb-4d31-84ae-ccfcd563effa
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bf5497fbddb255a9964d97094838dd3a7ece583e
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009855"
---
# <a name="using-encryption-without-validation"></a>検証を伴わない暗号化の使用
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、常に、ログインに関連するネットワーク パケットを暗号化します。 サーバーの起動時に証明書がサーバーに提供されないと、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はログイン パケットの暗号化に使用される自己署名入りの証明書を生成します。  

自己署名証明書では、セキュリティは保証されません。 暗号化されたハンドシェイクは、NT LAN Manager (NTLM) に基づいています。 セキュリティで保護された接続には、SQL Server で検証可能な証明書をプロビジョニングすることを強くお勧めします。 トランスポート層セキュリティ (TLS) は、証明書の検証によってのみセキュリティで保護することができます。

アプリケーションでは、接続文字列キーワードまたは接続プロパティを使用して、すべてのネットワーク トラフィックの暗号化を要求することもできます。 キーワードは、 **IDataInitialize**で初期化文字列を使用する場合に、 **IDbInitialize:: Initialize**でプロバイダー文字列を使用する場合は ODBC と OLE DB、OLE DB ADO の場合は "データの暗号化" を使用する場合は "暗号化" を使用します。 これは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager で **[プロトコルの暗号化を設定する]** オプションを使用して構成することも、暗号化された接続を要求するようにクライアントを構成することによって構成することもできます。 既定では、接続のネットワーク トラフィックをすべて暗号化するには、証明書をサーバーに提供する必要があります。 クライアントがサーバー上の証明書を信頼するように設定すると、中間者攻撃に対して脆弱になる可能性があります。 検証可能な証明書をサーバーに展開する場合は、証明書の信頼に関するクライアント設定を確実に FALSE に変更してください。

接続文字列キーワードの詳細については、「 [SQL Server Native Client での接続文字列キーワードの使用](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 証明書がサーバーに提供されていないときに暗号化を有効にするには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーを使用して **[Force Protocol Encryption]** オプションと **[Trust Server Certificate]** オプションの両方を設定できます。 この場合、検証可能な証明書がサーバーに提供されなかった場合は、暗号化には検証を伴わない自己署名入りのサーバー証明書を使用します。  
  
 アプリケーションでは、暗号化が行われることを保証するために "TrustServerCertificate" キーワードまたはそれに関連する接続属性も使用できます。 アプリケーションの設定によって、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント構成マネージャーで設定されるセキュリティのレベルを緩和することはできません。ただし、厳密にすることはできます。 たとえば、クライアントに **[Force Protocol Encryption]** オプションが設定されていない場合、アプリケーションから暗号化自体を要求することができます。 サーバー証明書が提供されなかった場合でも暗号化を保証するには、アプリケーションから暗号化と "TrustServerCertificate" を要求できます。 ただし、クライアントの構成で "TrustServerCertificate" が有効になっていない場合は、サーバー証明書を提供する必要があります。 次の表ですべてのケースを説明します。  
  
|[Force Protocol Encryption] クライアント設定|[Trust Server Certificate] クライアント設定|接続文字列/接続属性 Encrypt/Use Encryption for Data|接続文字列/接続属性 Trust Server Certificate|結果|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|いいえ|該当なし|いいえ (既定値)|無視|暗号化は行われません。|  
|いいえ|該当なし|はい|いいえ (既定値)|暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。|  
|いいえ|該当なし|はい|はい|暗号化は常に行われますが、自己署名入りのサーバー証明書を使用することがあります。|  
|はい|いいえ|無視|無視|暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。|  
|はい|はい|いいえ (既定値)|無視|暗号化は常に行われますが、自己署名入りのサーバー証明書を使用することがあります。|  
|はい|はい|はい|いいえ (既定値)|暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。|  
|はい|はい|はい|はい|暗号化は常に行われますが、自己署名入りのサーバー証明書を使用することがあります。|  
||||||

> [!CAUTION]
> 上の表では、さまざまな構成でのシステムの動作についてのみ説明しています。 セキュリティで保護された接続を実現するには、クライアントとサーバーの両方で暗号化が必要であることを確実にします。 また、確実にサーバーに検証可能な証明書があり、クライアントの **TrustServerCertificate** 設定が FALSE に設定されているようにします。

## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB プロバイダー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、DBPROPSET_SQLSERVERDBINIT プロパティセットに実装されている SSPROP_INIT_TRUST_SERVER_CERTIFICATE データソース初期化プロパティを追加することによって、検証を行わずに暗号化をサポートします。 また、新しい接続文字列のキーワードとして "TrustServerCertificate" が追加されました。 "TrustServerCertificate" は、yes または no を値として受け取ります。既定値は no です。 サービス コンポーネントを使用しているときは、"TrustServerCertificate" は true または false を値として受け取ります。既定値は false です。  
  
 DBPROPSET_SQLSERVERDBINIT プロパティ セットに行われた機能強化の詳細については、「[初期化プロパティと承認プロパティ](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)」を参照してください。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC ドライバー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)および[sqlgetconnectattr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)関数への追加によって、検証なしの暗号化がサポートされています。 SQL_TRUST_SERVER_CERTIFICATE_YES または SQL_TRUST_SERVER_CERTIFICATE_NO を受け取る、SQL_COPT_SS_TRUST_SERVER_CERTIFICATE が追加されました。既定値は SQL_TRUST_SERVER_CERTIFICATE_NO です。 また、新しい接続文字列のキーワードとして "TrustServerCertificate" が追加されました。 "TrustServerCertificate" は、"yes" または "no" を値として受け取ります。既定値は "no" です。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
