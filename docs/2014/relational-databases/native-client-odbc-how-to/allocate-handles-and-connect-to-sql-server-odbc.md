---
title: ハンドルを割り当てて SQL Server に接続する (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 322120624c612371b56029c2cf29c9ab457c81b5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63225499"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>ハンドルの割り当てと SQL Server への接続 (ODBC)
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>ハンドルを割り当てて SQL Server に接続するには  
  
1.  ODBC ヘッダー ファイル Sql.h、Sqlext.h、Sqltypes.h を含めます。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドライバー固有のヘッダー ファイル Odbcss.h を含めます。  
  
3.  を[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)使用して`HandleType` SQLAllocHandle を呼び出し SQL_HANDLE_ENV、ODBC を初期化して環境ハンドルを割り当てます。  
  
4.  を SQL_ATTR_ODBC_VERSION に`Attribute`設定し、を`ValuePtr` SQL_OV_ODBC3 に設定して、アプリケーションが ODBC 3. x 形式の関数呼び出しを使用することを示すには、[を呼び出します](../native-client-odbc-api/sqlsetenvattr.md)。  
  
5.  必要に応じて、 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)を呼び出して他の環境オプションを設定するか、 [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403)を呼び出して環境オプションを取得します。  
  
6.  SQL_HANDLE_DBC [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)のを使用`HandleType`して SQLAllocHandle を呼び出し、接続ハンドルを割り当てます。  
  
7.  必要に応じて、 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出して接続オプションを設定するか、 [Sqlgetconnectattr](../native-client-odbc-api/sqlgetconnectattr.md)を呼び出して接続オプションを取得します。  
  
8.  SQLConnect を呼び出して、既存のデータソースを使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]してに接続します。  
  
     Or  
  
     接続[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)文字列を使用してに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続するには、SQLDriverConnect を呼び出します。  
  
     最小の完全な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続文字列は、次の 2 つの形式のいずれかになります。  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     接続文字列が完全でない場合は、`SQLDriverConnect` によって必要な情報の入力が要求される場合があります。 これは、 *Drivercompletion*パラメーターに指定された値によって制御されます。  
  
     \- または  
  
     反復的な方法で[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md)を複数回呼び出して、接続文字列を作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、に接続します。  
  
9. 必要に応じて、 [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md)を呼び出して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データソースのドライバー属性と動作を取得します。  
  
10. ステートメントを割り当てて使用します。  
  
11. 切断[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するには sqldisconnect を呼び出し、接続ハンドルを新しい接続に使用できるようにします。  
  
12. SQL_HANDLE_DBC のを`HandleType`使用して[sqlfreehandle](../native-client-odbc-api/sqlfreehandle.md)を呼び出し、接続ハンドルを解放します。  
  
13. `SQLFreeHandle` を SQL_HANDLE_ENV として `HandleType` を呼び出し、環境ハンドルを解放します。  
  
> [!IMPORTANT]  
>  可能な場合は、Windows 認証を使用します。 Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。 資格情報をファイルに保存するのは避けてください。 資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。  
  
## <a name="example"></a>例  
 次の例では、`SQLDriverConnect` を呼び出して、既存の ODBC データ ソースを要求せずに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する方法を示しています。 不完全な接続文字列を `SQLDriverConnect` に渡すと、ODBC ドライバーから不足情報を入力するように要求されます。  
  
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
  
  
