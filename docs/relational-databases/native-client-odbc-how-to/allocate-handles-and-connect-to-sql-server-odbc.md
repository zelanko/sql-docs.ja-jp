---
title: ハンドルの割り当て (ODBC) の SQL Server に接続および |マイクロソフトのドキュメント
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0dc7cad1d720489db4044bbd34c6516035305365
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090820"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>ハンドルの割り当てと SQL Server への接続 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>ハンドルを割り当てて SQL Server に接続するには  
  
1.  ODBC ヘッダー ファイル Sql.h、Sqlext.h、Sqltypes.h を含めます。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドライバー固有のヘッダー ファイル Odbcss.h を含めます。  
  
3.  呼び出す[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)で、 **HandleType**を ODBC を初期化して環境ハンドルを割り当てる sql_handle_env としての。  
  
4.  呼び出す[SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)で**属性**SQL_ATTR_ODBC_VERSION に設定し、 **ValuePtr**をアプリケーションで ODBC 3.x 形式の関数が使用されていることを示す SQL_OV_ODBC3 に設定呼び出されます。  
  
5.  必要に応じて、呼び出す[SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)他の環境を設定するオプション、または呼び出し[SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403)環境オプションを取得します。  
  
6.  呼び出す[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)で、 **HandleType**接続ハンドルの割り当てを sql_handle_dbc としての。  
  
7.  必要に応じて、呼び出す[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)接続オプションの設定、または呼び出し[SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)接続オプションを取得します。  
  
8.  接続する既存のデータ ソースを使用する SQLConnect を呼び出す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
     または  
  
     呼び出す[SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)に接続する接続文字列を使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
     最小の完全な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続文字列は、次の 2 つの形式のいずれかになります。  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     接続文字列が完了していない場合**SQLDriverConnect**必要な情報を求めることもできます。 指定された値によって制御されます、 *DriverCompletion*パラメーター。  
  
     \- または -  
  
     呼び出す[SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)接続文字列を作成しに接続する、反復的な方法で複数回[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
9. 必要に応じて、呼び出す[SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md)ドライバーの属性と動作を取得する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソース。  
  
10. ステートメントを割り当てて使用します。  
  
11. 呼び出しから切断する SQLDisconnect[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続ハンドルを新しい接続で使用できるようにします。  
  
12. 呼び出す[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)で、 **HandleType**の sql_handle_dbc として接続ハンドルを解放します。  
  
13. 呼び出す**SQLFreeHandle**で、 **HandleType**の sql_handle_env として環境ハンドルを解放します。  
  
> [!IMPORTANT]  
>  可能な場合は、Windows 認証を使用します。 Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。 資格情報をファイルに保存するのは避けてください。 資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。  
  
## <a name="example"></a>例  
 この例への呼び出しを示しています。 **SQLDriverConnect**のインスタンスに接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]せず、既存の ODBC データ ソース。 不完全な接続文字列を渡すことによって**SQLDriverConnect**と不足情報を入力するようにユーザーに、ODBC ドライバー。  
  
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
  
  
