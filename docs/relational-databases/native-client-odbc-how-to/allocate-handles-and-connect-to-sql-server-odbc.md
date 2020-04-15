---
title: ハンドルの割り当てと SQL サーバーへの接続 (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d26af711c07c4ea296d5351d0fcb0d1f9710706
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294526"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>ハンドルの割り当てと SQL Server への接続 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>ハンドルを割り当てて SQL Server に接続するには  
  
1.  ODBC ヘッダー ファイル Sql.h、Sqlext.h、Sqltypes.h を含めます。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドライバー固有のヘッダー ファイル Odbcss.h を含めます。  
  
3.  ODBC を初期化し、環境ハンドルを割り当てるには、ハンドル**のSQL_HANDLE_ENVを**使用して[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)を呼び出します。  
  
4.  SQL_ATTR_ODBC_VERSION に**設定された属性**と**ValuePtr**を SQL_OV_ODBC3 に設定して、アプリケーションが ODBC 3.x 形式の関数呼び出しを使用することを示す[SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)を呼び出します。  
  
5.  必要に応じて[、SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)を呼び出して他の環境オプションを設定するか[、SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403)を呼び出して環境オプションを取得します。  
  
6.  接続ハンドルを割り当てるには、SQL_HANDLE_DBCの**ハンドル型**を使用して[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)を呼び出します。  
  
7.  必要に応じて、接続オプションを設定するために[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)を呼び出すか、接続オプションを取得するために[SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)を呼び出します。  
  
8.  SQLConnect を呼び出して既存のデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ソースを使用して に接続します。  
  
     Or  
  
     に接続するために接続文字列を使用するには[、SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を呼び出します。  
  
     最小の完全な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続文字列は、次の 2 つの形式のいずれかになります。  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     接続文字列が完全でない**場合は、** 必要な情報を求めるメッセージを表示できます。 これは *、DriverCompletion*パラメーターに指定された値によって制御されます。  
  
     \- または  
  
     [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)を反復的に複数回呼び出して接続文字列を作成し、 に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続します。  
  
9. 必要に応じて[、SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md)を呼び出して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソースのドライバー属性と動作を取得します。  
  
10. ステートメントを割り当てて使用します。  
  
11. SQLDisconnect を呼び[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]出して、接続ハンドルを切断し、新しい接続で使用できるようにします。  
  
12. 接続ハンドルを解放するには、SQL_HANDLE_DBCの**ハンドル型**を使用して[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)を呼び出します。  
  
13. 環境ハンドルを解放するSQL_HANDLE_ENVの**ハンドル型**で**SQLFreeHandle**を呼び出します。  
  
> [!IMPORTANT]  
>  可能な場合は、Windows 認証を使用します。 Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。 資格情報をファイルに保存するのは避けてください。 資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。  
  
## <a name="example"></a>例  
 この例では、既存の ODBC データ ソースを必要[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とせずにインスタンスに接続するための**SQLDriverConnect**の呼び出しを示します。 不完全な接続文字列を**SQLDriverConnect**に渡すことにより、ODBC ドライバは、不足している情報を入力するようにユーザーに求めるプロンプトを表示します。  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
