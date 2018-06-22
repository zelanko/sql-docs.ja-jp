---
title: ハンドルの割り当てを SQL Server (ODBC) 接続および |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: adf51bdb9181030079d8b3f94628a1280299c856
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072768"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>ハンドルの割り当てと SQL Server への接続 (ODBC)
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>ハンドルを割り当てて SQL Server に接続するには  
  
1.  ODBC ヘッダー ファイル Sql.h、Sqlext.h、Sqltypes.h を含めます。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドライバー固有のヘッダー ファイル Odbcss.h を含めます。  
  
3.  呼び出す[SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396)で、`HandleType`の ODBC を初期化し、環境ハンドルの割り当てを sql_handle_env として。  
  
4.  呼び出す[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)で`Attribute`またに設定し、 `ValuePtr` SQL_OV_ODBC3 に設定をアプリケーションで ODBC 3.x 形式の関数呼び出しが使用されていることを示します。  
  
5.  必要に応じて、呼び出し[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)他の環境を設定するオプション、または呼び出し[SQLGetEnvAttr](http://go.microsoft.com/fwlink/?LinkId=58403)環境オプションを取得します。  
  
6.  呼び出す[SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396)で、`HandleType`接続ハンドルの割り当てを sql_handle_dbc としてのです。  
  
7.  必要に応じて、呼び出す[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)接続オプションの設定、または呼び出しを[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md)接続オプションを取得します。  
  
8.  接続する既存のデータ ソースを使用する SQLConnect を呼び出す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
     スイッチまたは  
  
     呼び出す[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)に接続する接続文字列を使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
     最小の完全な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続文字列は、次の 2 つの形式のいずれかになります。  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     接続文字列が完全でない場合は、`SQLDriverConnect` によって必要な情報の入力が要求される場合があります。 指定された値によって制御されます、 *DriverCompletion*パラメーター。  
  
     \- または -  
  
     呼び出す[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md)反復的な接続文字列を作成しに接続する方法で複数回[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
9. 必要に応じて、呼び出す[SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md)ドライバー属性と動作を取得する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソース。  
  
10. ステートメントを割り当てて使用します。  
  
11. 切断する SQLDisconnect を呼び出す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、接続ハンドルを新しい接続を使用できるようにします。  
  
12. 呼び出す[SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md)で、 `HandleType` sql_handle_dbc として接続ハンドルを解放するのです。  
  
13. `SQLFreeHandle` を SQL_HANDLE_ENV として `HandleType` を呼び出し、環境ハンドルを解放します。  
  
> [!IMPORTANT]  
>  可能な場合は、Windows 認証を使用します。 Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。 資格情報をファイルに保存するのは避けてください。 資格情報を保持する必要がある場合は、[Win32 Crypto API](http://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。  
  
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
  
  