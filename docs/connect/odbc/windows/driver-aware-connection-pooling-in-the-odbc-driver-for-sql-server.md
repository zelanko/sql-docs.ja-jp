---
title: ODBC ドライバーの SQL Server のドライバー対応接続プール |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 455ab165-8e4d-4df9-a1d7-2b532bfd55d6
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f3cc9428f84db56675dbf58c977078fa4dcca6ae
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
    |`Address`|はい|[ユーザー アカウント制御]|
    |`AnsiNPW`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`App`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`ApplicationIntent`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
    |`Authentication`|[ユーザー アカウント制御]|いいえ|
    |`ColumnEncryption`|可|いいえ|
    |`Database`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`Encrypt`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
    |`Failover_Partner`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`FailoverPartnerSPN`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`MARS_Connection`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`Network`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`PWD`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`Server`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`ServerSPN`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`TransparentNetworkIPResolution`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`Trusted_Connection`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`TrustServerCertificate`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`UID`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`WSID`|[ユーザー アカウント制御]|はい|
    
- 接続文字列とプールされた接続文字列の次のいずれかの接続属性の間に違いがある場合、プールされた接続は使用されません。  
  
    |属性|ODBC Driver 13|ODBC Driver 11|  
    |-|-|-|  
    |`SQL_ATTR_CURRENT_CATALOG`|はい|[ユーザー アカウント制御]|
    |`SQL_ATTR_PACKET_SIZE`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_ANSI_NPW`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_ACCESS_TOKEN`|[ユーザー アカウント制御]|いいえ|
    |`SQL_COPT_SS_AUTHENTICATION`|可|いいえ|
    |`SQL_COPT_SS_ATTACHDBFILENAME`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_BCP`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_COLUMN_ENCRYPTION`|[ユーザー アカウント制御]|いいえ|
    |`SQL_COPT_SS_CONCAT_NULL`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_ENCRYPT`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_FAILOVER_PARTNER`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_FAILOVER_PARTNER_SPN`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_INTEGRATED_SECURITY`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_MARS_ENABLED`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_OLDPWD`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_SERVER_SPN`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_TRUST_SERVER_CERTIFICATE`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SSPROP_AUTH_REPL_SERVER_NAME`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_TNIR`|[ユーザー アカウント制御]|いいえ|
 
-   ドライバーは追加でネットワーク呼び出しを行うことなく、次の接続キーワードと属性をリセットおよび調整できます。 ドライバーは接続に誤った情報が含まれないように、これらのパラメーターをリセットします。  
  
     これらの接続キーワードは、ドライバー マネージャがプール内の接続とユーザーの接続を一致させるときには考慮されません (これらのいずれかのパラメーターを変更した場合でも、既存の接続を再利用できます。 ドライバーは、必要に応じてこれらのオプションをリセットします)。これらの属性は、追加でネットワーク呼び出しを行わず、クライアント側でリセットできます。  
  
    |Keyword|ODBC Driver 13|ODBC Driver 11|  
    |-|-|-|  
    |`AutoTranslate`|はい|[ユーザー アカウント制御]|
    |`Description`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`MultisubnetFailover`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|  
    |`QueryLog_On`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`QueryLogFile`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`QueryLogTime`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`Regional`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`StatsLog_On`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`StatsLogFile`|  [ユーザー アカウント制御]|はい|
  
     次のいずれかの接続属性を変更した場合、既存の接続を再利用できます。  必要に応じて、ドライバーによって値がリセットされます。 ドライバーは追加のネットワーク呼び出しを行うことなく、クライアントでこれらの属性をリセットできます。  
  
    |属性|ODBC Driver 13|ODBC Driver 11|  
    |-|-|-|  
    |すべてのステートメント属性|はい|[ユーザー アカウント制御]|
    |`SQL_ATTR_AUTOCOMMIT`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_ATTR_CONNECTION_TIMEOUT`|  [ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_ATTR_DISCONNECT_BEHAVIOR SQL_ATTR_CONNECTION_TIMEOUT`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_ATTR_LOGIN_TIMEOUT`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_ATTR_ODBC_CURSORS`|  [ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_PERF_DATA`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_PERF_DATA_LOG`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_PERF_DATA_LOG_NOW`| [ユーザー アカウント制御]|[ユーザー アカウント制御]| 
    |`SQL_COPT_SS_PERF_QUERY`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_PERF_QUERY_INTERVAL`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_PERF_QUERY_LOG`|  [ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_PRESERVE_CURSORS`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_TRANSLATE`|[ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_USER_DATA`|  [ユーザー アカウント制御]|[ユーザー アカウント制御]|
    |`SQL_COPT_SS_WARN_ON_CP_ERROR`|[ユーザー アカウント制御]|はい|  
  
## <a name="see-also"></a>参照  
 [Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
