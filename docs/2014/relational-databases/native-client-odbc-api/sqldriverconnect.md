---
title: SQLDriverConnect |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5f5ef42a9d04a4d1ae72382f44fdf01b62fc6b14
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706280"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、接続文字列のキーワードを置き換えたり、拡張したりするための接続属性を定義します。 接続文字列のいくつかのキーワードには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが指定する既定値があります。  
  
 Native Client ODBC ドライバーで使用できるキーワードの一覧については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server Native Client での接続文字列キーワードの使用](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続属性とドライバーの既定の動作の詳細については、「 [SQLSetConnectAttr](sqlsetconnectattr.md)」を参照してください。  
  
 Native Client で有効な接続文字列キーワードの詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server Native Client での接続文字列キーワードの使用](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 `SQLDriverConnect` *Drivercompletion*パラメーター値が SQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE、または SQL_DRIVER_COMPLETE_REQUIRED の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、表示されるダイアログボックスからキーワード値を取得します。 接続文字列でキーワード値が渡され、ユーザーがダイアログ ボックスでキーワードの値を変更しなかった場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは接続文字列の値を使用します。 接続文字列で値が設定されていない場合、ユーザーがダイアログ ボックスで割り当てを行わないと、ドライバーは既定値を使用します。  
  
 `SQLDriverConnect`*Drivercompletion*の値がドライバーの接続ダイアログボックスを表示する必要がある (または必要になる可能性がある) 場合は、有効な*WindowHandle*を指定する必要があります。 無効なハンドルを指定すると、SQL_ERROR が返されます。  
  
 DRIVER キーワードまたは DSN キーワードを指定します。 ODBC は、これらの 2 つのキーワードが両方指定されている場合、左側に指定されているキーワードを使用し、他方を無視するように指示します。 DRIVER が指定されている場合、またはが2つの左端で、 `SQLDriverConnect` *drivercompletion*パラメーター値が SQL_DRIVER_NOPROMPT の場合は、SERVER キーワードと適切な値が必要です。  
  
 SQL_DRIVER_NOPROMPT が指定されているときは、ユーザー認証に関するキーワードに値が指定されている必要があります。 ドライバーは、文字列 "Trusted_Connection=yes" または UID キーワードと PWD キーワードの両方が指定されていることを確認します。  
  
 *Drivercompletion*パラメーター値が SQL_DRIVER_NOPROMPT または SQL_DRIVER_COMPLETE_REQUIRED であり、言語またはデータベースが接続文字列から取得されていて、かつ無効である場合、は `SQLDriverConnect` SQL_ERROR を返します。  
  
 *Drivercompletion*パラメーターの値が SQL_DRIVER_NOPROMPT または SQL_DRIVER_COMPLETE_REQUIRED で、言語またはデータベースが ODBC データソースの定義から取得され、その言語またはデータベースが無効である場合、は、 `SQLDriverConnect` 指定されたユーザー ID の既定の言語またはデータベースを使用して SQL_SUCCESS_WITH_INFO を返します。  
  
 *Drivercompletion*パラメーター値が SQL_DRIVER_COMPLETE または SQL_DRIVER_PROMPT で、言語またはデータベースが無効である場合は、に `SQLDriverConnect` よってダイアログボックスが再されます。  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>SQLDriverConnect の HADR サポート  
 を使用したクラスターへの接続の詳細については `SQLDriverConnect` [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 、「[高可用性、ディザスターリカバリーのサポートの SQL Server Native Client](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)」を参照してください。  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>SQLDriverConnect によるサービス プリンシパル名 (SPN) のサポート  
 SQLDDriverConnect では、プロンプトが有効になっているときに ODBC ログインダイアログボックスが使用されます。 これにより、プリンシパル サーバーとそのフェールオーバー パートナーの両方に対して SPN を入力できます。  
  
 SQLDriverConnect は新しい接続文字列キーワード `ServerSPN` とを受け取り、 `FailoverPartnerSPN` 新しい接続属性 SQL_COPT_SS_SERVER_SPN と SQL_COPT_SS_FAILOVER_PARTNER_SPN を認識します。  
  
 接続属性の値が複数指定されている場合は、DSN の値や接続文字列の値より、プログラムによって設定された値が優先されます。 DSN の値は接続文字列の値より優先されます。  
  
 接続が開いている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、SQL_COPT_SS_MUTUALLY_AUTHENTICATED および SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD が、接続を開くときに使用された認証方式に設定されます。  
  
 Spn の詳細については、「[クライアント接続 &#40;ODBC&#41;のサービスプリンシパル名 &#40;spn&#41; ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の呼び出しは、に必要なデータ量の最小値を示してい `SQLDriverConnect` ます。  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 次の接続文字列は、 *Drivercompletion*パラメーター値が SQL_DRIVER_NOPROMPT 場合に最低限必要なデータを示しています。  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>参照  
 [SQLDriverConnect 関数](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [ODBC API の実装の詳細](odbc-api-implementation-details.md)   
 [SET ANSI_NULLS &#40;Transact-sql&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)   
 [SET ANSI_PADDING &#40;Transact-sql&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
