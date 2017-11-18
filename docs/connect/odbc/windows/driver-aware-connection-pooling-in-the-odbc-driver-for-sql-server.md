---
title: "ODBC ドライバーの SQL Server のドライバー対応接続プール |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 455ab165-8e4d-4df9-a1d7-2b532bfd55d6
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cf44de6479d50e188b84679b5c09ce382e541391
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server"></a>OLE DB Provider for SQL Server のドライバー対応接続プール
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  ODBC Driver for[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]サポート[ドライバー対応接続プール](http://msdn.microsoft.com/library/hh405031(VS.85).aspx)です。 Microsoft ODBC Driver for でのドライバー対応接続プールに対する機能強化について説明[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]on Windows:  
  
-   接続のプロパティを使用する接続に関係なく`SQLDriverConnect`を使用する接続から別のプールに移動して`SQLConnect`です。
- 使用する場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]認証とドライバー対応接続プールをドライバーが Windows ユーザーのセキュリティ コンテキストは使用、現在のスレッド プール内の接続を分離します。 つまり、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 認証での Windows での権限借用シナリオでの接続と、接続パラメーターが同じで、バックエンドとの接続に同じ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 認証資格証明を使用する場合、別の Windows ユーザーが同じプール接続を使用できる可能性があります。 Windows 認証とドライバー対応接続プールを使用する場合、ドライバーは、プール内の接続を分離するために現在の Windows ユーザーのセキュリティ コンテキストを使用します。 つまり、Windows での権限借用のシナリオでは、接続で同じパラメーターを使用していても、別の Windows ユーザーは同じ接続を使用しません。
- Azure Active Directory とドライバー対応接続プールを使用する場合、ドライバーは接続プールのメンバーシップを決定する、認証の値も使用します。
  
-   ドライバー対応接続プールは、無効な接続がプールから返されないようにします。  
  
-   ドライバー対応接続プールは、ドライバーに固有の接続属性を認識します。 そのため、接続を使用している場合`SQL_COPT_SS_APPLICATION_INTENT`読み取り専用に設定すると、その接続は独自の接続プールを取得します。
-   設定、`SQL_COPT_SS_ACCESS_TOKEN`属性によって別々 にプールへの接続 
  
次のいずれかの接続属性 ID または接続文字列キーワードが、接続文字列と、プールされた接続文字列の間で異なる場合、ドライバーはプールされた接続を使用します。 ただし、すべての接続属性 ID または接続文字列キーワードが一致する場合、パフォーマンスは向上します。 (プール内で接続を一致させるために、ドライバーは属性をリセットします。 次のパラメーターをリセットする場合、ネットワーク呼び出しを追加で実行する必要があるので、パフォーマンスは低下します。  
  
-    次の接続属性または接続キーワードの 2 つ以上が異なる場合、プールされた接続は使用されません。  
  
  - `Language`  
  - `QuoteId`  
  - `SQL_ATTR_TXN_ISOLATION` 
  - `SQL_COPT_SS_QUOTED_IDENT`  
  
-   接続文字列とプールされた接続文字列の次のいずれかの接続キーワードの間に違いがある場合、プールされた接続は使用されません。  
  
    |Keyword|ODBC Driver 13|ODBC Driver 11|
    |-|-|-|
    |`Address`|はい|可|
    |`AnsiNPW`|可|可|
    |`App`|可|可|
    |`ApplicationIntent`|可|可|  
    |`Authentication`|可|いいえ|
    |`ColumnEncryption`|可|いいえ|
    |`Database`|はい|可|
    |`Encrypt`|可|可|  
    |`Failover_Partner`|可|可|
    |`FailoverPartnerSPN`|可|可|
    |`MARS_Connection`|可|可|
    |`Network`|可|可|
    |`PWD`|可|可|
    |`Server`|可|可|
    |`ServerSPN`|可|可|
    |`TransparentNetworkIPResolution`|可|可|
    |`Trusted_Connection`|可|可|
    |`TrustServerCertificate`|可|可|
    |`UID`|可|可|
    |`WSID`|可|はい|
    
- 接続文字列とプールされた接続文字列の次のいずれかの接続属性の間に違いがある場合、プールされた接続は使用されません。  
  
    |属性|ODBC Driver 13|ODBC Driver 11|  
    |-|-|-|  
    |`SQL_ATTR_CURRENT_CATALOG`|はい|可|
    |`SQL_ATTR_PACKET_SIZE`|可|可|
    |`SQL_COPT_SS_ANSI_NPW`|可|可|
    |`SQL_COPT_SS_ACCESS_TOKEN`|可|いいえ|
    |`SQL_COPT_SS_AUTHENTICATION`|可|いいえ|
    |`SQL_COPT_SS_ATTACHDBFILENAME`|はい|可|
    |`SQL_COPT_SS_BCP`|可|可|
    |`SQL_COPT_SS_COLUMN_ENCRYPTION`|可|いいえ|
    |`SQL_COPT_SS_CONCAT_NULL`|はい|可|
    |`SQL_COPT_SS_ENCRYPT`|可|可|
    |`SQL_COPT_SS_FAILOVER_PARTNER`|可|可|
    |`SQL_COPT_SS_FAILOVER_PARTNER_SPN`|可|可|
    |`SQL_COPT_SS_INTEGRATED_SECURITY`|可|可|
    |`SQL_COPT_SS_MARS_ENABLED`|可|可|
    |`SQL_COPT_SS_OLDPWD`|可|可|
    |`SQL_COPT_SS_SERVER_SPN`|可|可|
    |`SQL_COPT_SS_TRUST_SERVER_CERTIFICATE`|可|可|
    |`SSPROP_AUTH_REPL_SERVER_NAME`|可|可|
    |`SQL_COPT_SS_TNIR`|可|不可|
 
-   ドライバーは追加でネットワーク呼び出しを行うことなく、次の接続キーワードと属性をリセットおよび調整できます。 ドライバーは接続に誤った情報が含まれないように、これらのパラメーターをリセットします。  
  
     これらの接続キーワードは、ドライバー マネージャがプール内の接続とユーザーの接続を一致させるときには考慮されません (これらのいずれかのパラメーターを変更した場合でも、既存の接続を再利用できます。 ドライバーは、必要に応じてこれらのオプションをリセットします)。これらの属性は、追加でネットワーク呼び出しを行わず、クライアント側でリセットできます。  
  
    |Keyword|ODBC Driver 13|ODBC Driver 11|  
    |-|-|-|  
    |`AutoTranslate`|はい|可|
    |`Description`|可|可|
    |`MultisubnetFailover`|可|可|  
    |`QueryLog_On`|可|可|
    |`QueryLogFile`|可|可|
    |`QueryLogTime`|可|可|
    |`Regional`|可|可|
    |`StatsLog_On`|可|可|
    |`StatsLogFile`|  可|はい|
  
     次のいずれかの接続属性を変更した場合、既存の接続を再利用できます。  必要に応じて、ドライバーによって値がリセットされます。 ドライバーは追加のネットワーク呼び出しを行うことなく、クライアントでこれらの属性をリセットできます。  
  
    |属性|ODBC Driver 13|ODBC Driver 11|  
    |-|-|-|  
    |すべてのステートメント属性|はい|可|
    |`SQL_ATTR_AUTOCOMMIT`|可|可|
    |`SQL_ATTR_CONNECTION_TIMEOUT`|  可|可|
    |`SQL_ATTR_DISCONNECT_BEHAVIOR SQL_ATTR_CONNECTION_TIMEOUT`|可|可|
    |`SQL_ATTR_LOGIN_TIMEOUT`|可|可|
    |`SQL_ATTR_ODBC_CURSORS`|  可|可|
    |`SQL_COPT_SS_PERF_DATA`|可|可|
    |`SQL_COPT_SS_PERF_DATA_LOG`|可|可|
    |`SQL_COPT_SS_PERF_DATA_LOG_NOW`| 可|可| 
    |`SQL_COPT_SS_PERF_QUERY`|可|可|
    |`SQL_COPT_SS_PERF_QUERY_INTERVAL`|可|可|
    |`SQL_COPT_SS_PERF_QUERY_LOG`|  可|可|
    |`SQL_COPT_SS_PRESERVE_CURSORS`|可|可|
    |`SQL_COPT_SS_TRANSLATE`|可|可|
    |`SQL_COPT_SS_USER_DATA`|  可|可|
    |`SQL_COPT_SS_WARN_ON_CP_ERROR`|可|はい|  
  
## <a name="see-also"></a>参照  
 [Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  

