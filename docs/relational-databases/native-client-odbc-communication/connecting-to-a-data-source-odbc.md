---
title: データ ソースへの接続 (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- checking connection states
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- SQLBrowseConnect function
- ODBC applications, connections
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLConnect function
- SQLDriveConnect function
- verifying connection states
- SQL Server Native Client ODBC driver, data sources
- SQL Server Native Client ODBC driver, connections
ms.assetid: ae30dd1d-06ae-452b-9618-8fd8cd7ba074
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ae59e0bdb005d296341970f4582100b15a0dfdf7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307723"
---
# <a name="connecting-to-a-data-source-odbc"></a>データ ソースへの接続 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  アプリケーションは、環境ハンドルと接続ハンドルを割り当て、任意の接続属性を設定してから、データ ソースまたはドライバーに接続します。 接続には、次の 3 つの関数を使用できます。  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 さまざまな接続文字列オプションを含むデータ ソースへの接続の詳細については、「 SQL Server[ネイティブ クライアントでの接続文字列キーワードの使用](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLConnect**は、最も簡単な接続関数です。 この関数は、データ ソース名、ユーザー ID、パスワードの 3 つのパラメーターを受け取ります。 これら 3 つのパラメータにデータベースへの接続に必要なすべての情報が含まれている場合は **、SQLConnect**を使用します。 これを行うには **、SQLDataSources**を使用してデータ ソースの一覧を作成します。データ ソース、ユーザー ID、およびパスワードをユーザーに要求する。をクリックしてから **、SQLConnect**を呼び出します。  
  
 **SQLConnect**では、データ ソース名、ユーザー ID、およびパスワードがデータ ソースに接続するのに十分であり、ODBC データ ソースには ODBC ドライバーが接続を行うために必要なその他すべての情報が含まれていることを前提としています。 [SQL ドライバー接続](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)および[SQL ブラウズ接続](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)とは異なり、**接続文字列**は使用されません。  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **データ ソース**名、ユーザー ID、およびパスワードよりも多くの情報が必要な場合に使用されます。 **SQLDriverConnect**のパラメーターの 1 つは、ドライバー固有の情報を含む接続文字列です。 次の理由により **、SQL 接続**の代わりに**SQL ドライバ接続**を使用する場合があります。  
  
-   接続時にドライバー固有の情報を指定する場合  
  
-   ドライバーがユーザーに対して接続情報を要求する場合  
  
-   ODBC データ ソースを使用せずに接続する場合  
  
 **接続文字列**には、ODBC ドライバーでサポートされているすべての接続情報を指定する一連のキーワードと値のペアが含まれています。 各ドライバーでは、ドライバーでサポートされるすべての接続情報を表すドライバー固有のキーワード以外に、標準の ODBC キーワード (DSN、FILEDSN, DRIVER、UID、PWD、および SAVEFILE) をサポートします。 **データ ソース**なしで接続するには、接続に使用できます。 たとえば、インスタンスへの "DSN レス" 接続を行うアプリケーションは、ログイン ID、パスワード、ネットワーク ライブラリ、接続先のサーバー名、および使用する既定の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースを定義する接続文字列を使用して**SQLDriverConnect**を呼び出すことができます。  
  
 **SQLDriverConnect**を使用する場合、必要な接続情報をユーザーに確認する 2 つのオプションがあります。  
  
-   アプリケーション ダイアログ ボックス  
  
     接続情報を要求するアプリケーション ダイアログ ボックスを作成し、NULL ウィンドウ ハンドルと *[ドライバ完了]* を SQL_DRIVER_NOPROMPT に設定して**SQLDriverConnect**を呼び出すことができます。 このようにパラメーターを設定すると、ODBC ドライバー独自のダイアログ ボックスが開かれなくなります。 この方法は、アプリケーションでユーザー インターフェイスを制御することが重要な場合に使用します。  
  
-   ドライバー ダイアログ ボックス  
  
     有効なウィンドウ ハンドルを**SQLDriverConnect**に渡し、*ドライバー補完*パラメーターをSQL_DRIVER_COMPLETE、SQL_DRIVER_PROMPT、またはSQL_DRIVER_COMPLETE_REQUIREDに設定するようにアプリケーションをコーディングできます。 この場合、ドライバーがダイアログ ボックスを生成して、ユーザーに接続情報を要求します。 この方法を使用すると、アプリケーション コードが簡素化されます。  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **SQLBrowseConnect**は、**接続文字列**を使用します。 ただし **、SQLBrowseConnect**を使用すると、アプリケーションは実行時にデータ ソースとの完全な接続文字列を繰り返し作成できます。 この方法を使用すると、アプリケーションで次の 2 つのことを行えます。  
  
-   アプリケーション独自のダイアログ ボックスを作成して目的の情報を要求できるので、アプリケーションのユーザー インターフェイスで制御できます。  
  
-   特定のドライバーが使用できるデータ ソースをシステムから参照できます。これは複数の手順になる場合があります。  
  
     たとえば、ユーザーは最初にネットワークを介してサーバーを参照して、サーバーを選択します。次に、そのサーバーを介して、ドライバーがアクセスできるデータベースを参照するといった手順です。  
  
 **接続**が正常に完了すると、その後の**SQLDriverConnect**の呼び出しで使用できる接続文字列が返されます。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバは、成功した**SQLConnect 、SQL****ドライバ接続**、または**SQLBrowseConnect**でSQL_SUCCESS_WITH_INFOを常に返します。 ODBC アプリケーションがSQL_SUCCESS_WITH_INFOを取得した後**に SQLGetDiagRec**を呼び出すと、次のメッセージを受信できます。  
  
 5701  
 このメッセージは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が、ユーザーのコンテキストをデータ ソースで定義されている既定のデータベースに登録したことを示します。または、データ ソースに既定のデータベースが定義されていない場合は、接続で使用したログイン ID に対して定義されている既定のデータベースに登録したことを示します。  
  
 5703  
 このメッセージは、その言語がサーバーで使用されていることを示します。  
  
 次の例では、システム管理者によって接続が正常に確立されたときに返されるメッセージを示します。  
  
```  
szSqlState = "01000", *pfNativeError = 5701,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed database context to 'pubs'."  
szSqlState = "01000", *pfNativeError = 5703,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed language setting to 'us_english'."  
```  
  
 5701 と 5703 のメッセージは、情報提供だけを目的としているので無視できます。 ただし、SQL_SUCCESS_WITH_INFO リターン コードでは 5701 や 5703 以外のメッセージも返されることがあるので、そのようなリターン コードは無視しないでください。 たとえば、ドライバが古いカタログ ストアド プロシージャ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を持つ インスタンスを実行しているサーバーに接続した場合、SQL_SUCCESS_WITH_INFO後に**SQLGetDiagRec**を通じて返されるエラーの 1 つは次のようになります。  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 接続用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアプリケーションのエラー処理関数は、SQL_NO_DATAを返すまで**SQLGetDiagRec**を呼び出す必要があります。 pfNative コードが 5701 または*pfNative*5703 のメッセージ以外のメッセージに対して動作する必要があります。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;SQL Server との通信](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
