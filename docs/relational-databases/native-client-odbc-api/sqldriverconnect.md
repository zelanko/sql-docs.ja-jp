---
title: コネクト |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8d1455f0b91313ea137ec9c13a2d318fba0807b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302553"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、接続文字列のキーワードを置き換えたり、拡張したりするための接続属性を定義します。 接続文字列のいくつかのキーワードには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが指定する既定値があります。  
  
 ネイティブ クライアント ODBC ドライバで使用できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キーワードの一覧については、「 [SQL Server ネイティブ クライアントでの接続文字列キーワードの使用](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 接続属性とドライバー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既定の動作の詳細については、「 [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)」を参照してください。  
  
 ネイティブ クライアントで有効な接続文字列キーワードについては、「 [SQL Server ネイティブ クライアントでの接続文字列キーワードの使用](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 **SQLDriverConnect**_ドライバー補完_パラメーター値がSQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE、またはSQL_DRIVER_COMPLETE_REQUIRED場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、表示されたダイアログ ボックスからキーワード値を取得します。 接続文字列でキーワード値が渡され、ユーザーがダイアログ ボックスでキーワードの値を変更しなかった場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは接続文字列の値を使用します。 接続文字列で値が設定されていない場合、ユーザーがダイアログ ボックスで割り当てを行わないと、ドライバーは既定値を使用します。  
  
 *ドライバー補完*値がドライバーの接続ダイアログ ボックスの表示を必要とする (または必要な場合がある) 場合は、**有効**な*ウィンドウ ハンドル*を与える必要があります。 無効なハンドルを指定すると、SQL_ERROR が返されます。  
  
 DRIVER キーワードまたは DSN キーワードを指定します。 ODBC は、これらの 2 つのキーワードが両方指定されている場合、左側に指定されているキーワードを使用し、他方を無視するように指示します。 DRIVER が指定されているか、または 2 つの左端で **、SQLDriverConnect**_ドライバー完了_パラメーター値がSQL_DRIVER_NOPROMPT場合、SERVER キーワードと適切な値が必要です。  
  
 SQL_DRIVER_NOPROMPT が指定されているときは、ユーザー認証に関するキーワードに値が指定されている必要があります。 ドライバーは、文字列 "Trusted_Connection=yes" または UID キーワードと PWD キーワードの両方が指定されていることを確認します。  
  
 *DriverCompletion*パラメーターの値がSQL_DRIVER_NOPROMPTまたはSQL_DRIVER_COMPLETE_REQUIRED、言語またはデータベースが接続文字列から取得され、いずれかが無効である場合 **、SQLDriverConnect**はSQL_ERRORを返します。  
  
 *DriverCompletion*パラメーター値がSQL_DRIVER_NOPROMPTまたはSQL_DRIVER_COMPLETE_REQUIREDで、言語またはデータベースが ODBC データ・ソース定義から取得され、いずれかが無効である場合 **、SQLDriverConnect**は指定されたユーザー ID にデフォルトの言語またはデータベースを使用して、SQL_SUCCESS_WITH_INFOを返します。  
  
 *DriverCompletion*パラメーターの値がSQL_DRIVER_COMPLETEまたはSQL_DRIVER_PROMPT、言語またはデータベースが無効な**場合は、** ダイアログ ボックスが再表示されます。  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>SQLDriverConnect の HADR サポート  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] **SQLDriverConnect**を使用してクラスターに接続する方法の詳細については、「 [SQL Server ネイティブ クライアントの高可用性サポート、ディザスタ リカバリ](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)」を参照してください。  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>SQLDriverConnect によるサービス プリンシパル名 (SPN) のサポート  
 プロンプトが有効になっている場合、ODBC ログイン ダイアログ ボックスが使用されます。 これにより、プリンシパル サーバーとそのフェールオーバー パートナーの両方に対して SPN を入力できます。  
  
 新しい接続文字列キーワード**ServerSPN**および**フェールオーバー パートナーSPN**を受け入れ、新しい接続属性SQL_COPT_SS_SERVER_SPNとSQL_COPT_SS_FAILOVER_PARTNER_SPNを認識します。  
  
 接続属性の値が複数指定されている場合は、DSN の値や接続文字列の値より、プログラムによって設定された値が優先されます。 DSN の値は接続文字列の値より優先されます。  
  
 接続が開いている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、SQL_COPT_SS_MUTUALLY_AUTHENTICATED および SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD が、接続を開くときに使用された認証方式に設定されます。  
  
 SPN の詳細については、「 [ODBC&#41;のクライアント接続で&#41;されるサービス プリンシパル名&#40;SPN &#40;」](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)を参照してください。  
  
## <a name="examples"></a>使用例  
 次の呼び出しは **、SQLDriverConnect**に必要なデータの最小量を示しています。  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 次の接続文字列は *、DriverCompletion*パラメーター値がSQL_DRIVER_NOPROMPTされている場合の最低限必要なデータを示しています。  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>参照  
 [関数を接続します。](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [ODBC API の実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [&#41;&#40;ANSI_NULLSを設定します。](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [&#40;ANSI_PADDINGの設定&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
