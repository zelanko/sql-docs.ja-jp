---
title: クライアント接続 (OLE DB) でサービス プリンシパル名 (Spn) |Microsoft ドキュメント
description: クライアント接続 (OLE DB) でサービス プリンシパル名 (Spn)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 681d20a50a942f9b56aa03e44b4a0e7c519db8ac
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="service-principal-names-spns-in-client-connections-ole-db"></a>クライアント接続 (OLE DB) でのサービス プリンシパル名 (SPN)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  このトピックでは、クライアント アプリケーションでサービス プリンシパル名 (SPN) をサポートする OLE DB のプロパティとメンバー関数について説明します。 クライアント アプリケーションで Spn の詳細については、次を参照してください。[サービス プリンシパル名&#40;SPN&#41;クライアント接続でサポート](../../oledb/features/service-principal-name-spn-support-in-client-connections.md)です。 サンプルについては、次を参照してください。[統合 Kerberos 認証&#40;OLE DB&#41;](../../oledb/ole-db-how-to/integrated-kerberos-authentication-ole-db.md)です。  
  
## <a name="provider-initialization-string-keywords"></a>プロバイダー初期化文字列のキーワード  
 次に示すプロバイダー初期化文字列のキーワードは、OLE DB アプリケーションで SPN をサポートします。 次の表では、idbinitialize::initialize のプロバイダー文字列のキーワードの列の値を使用します。 [説明] 列の値は、ADO または idatainitialize::getdatasource を使用して接続するときに、初期化文字列で使用されます。  
  
|Keyword|Description|値|  
|-------------|-----------------|-----------|  
|ServerSPN|サーバー SPN|サーバーの SPN。 既定値は、これにより、OLE DB Driver for SQL Server を既定値を使用する、空の文字列は、SPN をプロバイダーが生成されます。|  
|FailoverPartnerSPN|フェールオーバー パートナー SPN|フェールオーバー パートナーの SPN。 既定値は、これにより、OLE DB Driver for SQL Server を既定値を使用する、空の文字列は、SPN をプロバイダーが生成されます。|  
  
## <a name="data-source-initialization-properties"></a>データ ソース初期化プロパティ  
 次のプロパティ、 **DBPROPSET_SQLSERVERDBINIT**プロパティ セットを使用すると、アプリケーションの Spn を指定します。  
  
|名前|型|使用方法|  
|----------|----------|-----------|  
|SSPROP_INIT_SERVERSPN|VT_BSTR、読み取り/書き込み|サーバーの SPN を指定します。 既定値は、これにより、OLE DB Driver for SQL Server を既定値を使用する、空の文字列は、SPN をプロバイダーが生成されます。|  
|SSPROP_INIT_FAILOVERPARTNERSPN|VT_BSTR、読み取り/書き込み|フェールオーバー パートナーの SPN を指定します。 既定値は、これにより、OLE DB Driver for SQL Server を既定値を使用する、空の文字列は、SPN をプロバイダーが生成されます。|  
  
## <a name="data-source-properties"></a>データ ソースのプロパティ  
 次のプロパティ、 **DBPROPSET_SQLSERVERDATASOURCEINFO**プロパティ セットを使用すると、認証方法を検出するアプリケーション。  
  
|名前|型|使用方法|  
|----------|----------|-----------|  
|SSPROP_INTEGRATEDAUTHENTICATIONMETHOD|VT_BSTR、読み取り専用|接続に使用された認証方法を返します。 アプリケーションに返される値は、SQL Server で OLE DB ドライバーを Windows から返される値です。 返される値は次のとおりです。 <br />"NTLM"。これは NTLM 認証を使用して接続を開いたときに返されます。<br />"Kerberos"。これは Kerberos 認証を使用して接続を開いたときに返されます。<br /><br /> 接続が開いていて認証方法を特定できない場合は、VT_EMPTY が返されます。<br /><br /> このプロパティは、データ ソースが初期化されている場合にのみ読み取ることができます。 データ ソースが初期化される前に、プロパティの読み取りを試みると、IDBProperties::GetProperies は DB_S_ERRORSOCCURRED または DB_E_ERRORSOCCURRED、必要に応じて、返し DBPROPSET_PROPERTIESINERROR に DBPROPSTATUS_NOTSUPPORTED が設定されます。このプロパティです。 この動作は、OLE DB のコア仕様に従っています。|  
|SSPROP_MUTUALLYAUTHENICATED|VT_BOOL、読み取り専用|接続されているサーバーが相互に認証されている場合は VARIANT_TRUE を返し、それ以外の場合は VARIANT_FALSE を返します。<br /><br /> このプロパティは、データ ソースが初期化されている場合にのみ読み取ることができます。 ある場合、データ ソースが初期化される前に、プロパティを読み取ろうとして、IDBProperties::GetProperies は DB_S_ERRORSOCCURRED または DB_E_ERRORSOCCURRED、必要に応じて、返し DBPROPSET_ に DBPROPSTATUS_NOTSUPPORTED が設定されます。このプロパティの PROPERTIESINERROR します。 この動作は、OLE DB のコア仕様に従って、します。<br /><br /> Windows 認証を使用していない接続に対してこの属性が照会されると、VARIANT_FALSE が返されます。|  
  
## <a name="ole-db-api-support-for-spns"></a>OLE DB API による SPN のサポート  
 次の表では、クライアント接続で SPN をサポートする OLE DB メンバー関数について説明します。  
  
|メンバー関数|Description|  
|---------------------|-----------------|  
|IDataInitialize::GetDataSource|*pwszInitializationString*新しいキーワードを含めることができます**ServerSPN**と**FailoverPartnerSPN**です。|  
|IDataInitialize::GetInitializationString|SSPROP_INIT_SERVERSPN と ssprop_init_failoverpartnerspn の値は、既定以外の値である場合は含めることが、初期化文字列内*ppwszInitString*のキーワードの値として**ServerSPN**と**FailoverPartnerSPN**です。 それ以外の場合、これらのキーワードは初期化文字列に取り込まれません。|  
|IDBInitialize::Initialize|データ ソース初期化プロパティに DBPROP_INIT_PROMPT を設定して入力要求を有効にすると、OLE DB の [ログイン] ダイアログ ボックスが表示されます。 これにより、プリンシパル サーバーとそのフェールオーバー パートナーの両方に対して SPN を入力できます。<br /><br /> DPPROP_INIT_PROVIDERSTRING、文字列を場合に、プロバイダーの設定、新しいキーワードが認識されます**ServerSPN**と**FailoverPartnerSPN** SSPROP_INIT_SERVER_ を初期化するために、存在する場合は、その値を使用して、SPN および SSPROP_INIT_FAILOVER_PARTNER_SPN です。<br /><br /> Idbinitialize::initialize が呼び出される前に、プロパティ SSPROP_INIT_SERVER_SPN および SSPROP_INIT_FAILOVER_PARTNER_SPN を設定する idbproperties::setproperties を呼び出すことができます。 この方法は、プロバイダー文字列を使用する代わりに使用できます。<br /><br /> プロパティが複数の場所で設定されている場合は、プログラムによって設定された値が、プロバイダー文字列に設定された値より優先されます。 初期化文字列に設定された値は、ログイン ダイアログ ボックスで設定された値より優先されます。<br /><br /> プロバイダー文字列に同じキーワードが複数回使用されている場合は、最初に使用された値が優先されます。|  
|IDBProperties::GetProperties|新しいデータ ソース初期化プロパティ SSPROP_INIT_SERVERSPN と ssprop_init_failoverpartnerspn の値、および、新しいデータ ソース プロパティ SSPROP_AUTHENTICATIONMETHOD と SSPROP_ の値を取得する IDBProperties::GetProperties を呼び出すことができます。MUTUALLYAUTHENTICATED です。|  
|IDBProperties::GetPropertyInfo|新しいデータ ソース初期化プロパティ SSPROP_INIT_SERVERSPN と SSPROP_INIT_FAILOVERPARTNERSPN、または新しいデータ ソース プロパティ SSPROP_AUTHENTICATION_METHOD と SSPROP_MUTUALLYAUTHENTICATED:getpropertyinfo が含まれます。|  
|IDBProperties::SetProperties|Idbproperties::setproperties は、新しいデータ ソースの値を設定するには、初期化プロパティ SSPROP_INITSERVERSPN と ssprop_init_failoverpartnerspn の値を呼び出すことができます。<br /><br /> これらのプロパティはいつでも設定できますが、データ ソースが既に開いている場合は、次のエラーが返されます。DB_E_ERRORSOCCURRED、"複数ステップの OLE DB の操作でエラーが発生しました。 各 OLE DB の状態の値を確認してください。 作業は終了しませんでした。"|  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  
