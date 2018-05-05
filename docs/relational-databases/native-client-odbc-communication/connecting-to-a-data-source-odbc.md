---
title: データ ソース (ODBC) への接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-communication
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4daa642cbd60846cc4211de5e33cdad8e7a6d8db
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-a-data-source-odbc"></a>データ ソースへの接続 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションは、環境ハンドルと接続ハンドルを割り当て、任意の接続属性を設定してから、データ ソースまたはドライバーに接続します。 接続には、次の 3 つの関数を使用できます。  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 使用できる、さまざまな接続文字列オプションを含む、データ ソースに接続の詳細については、次を参照してください。[使用した Connection String Keywords with SQL Server Native Client を使用して](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)です。  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLConnect**最も簡単な接続関数です。 この関数は、データ ソース名、ユーザー ID、パスワードの 3 つのパラメーターを受け取ります。 使用して**SQLConnect**これら 3 つのパラメーターが、データベースへの接続に必要なすべての情報が含まれてとき。 これを行うには、ビルドを使用してデータ ソースの一覧**SQLDataSources**以外の場合は、ユーザーにデータ ソース、ユーザー ID とパスワードです。 確認し、呼び出す**SQLConnect**です。  
  
 **SQLConnect**データ ソース名、ユーザー ID とパスワードがデータ ソースに接続するための十分なことと、ODBC データ ソースに ODBC ドライバーが接続を確立する必要があるその他のすべての情報が含まれることを前提としています。 異なり[SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)と[SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)、 **SQLConnect**接続文字列を使用しません。  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SQLDriverConnect**データ ソース名、ユーザー ID、およびパスワードより多くの情報が必要な場合に使用します。 パラメーターのいずれかの**SQLDriverConnect**ドライバー固有の情報を含む接続文字列です。 使用する場合があります**SQLDriverConnect**の代わりに**SQLConnect**次の理由。  
  
-   接続時にドライバー固有の情報を指定する場合  
  
-   ドライバーがユーザーに対して接続情報を要求する場合  
  
-   ODBC データ ソースを使用せずに接続する場合  
  
 **SQLDriverConnect**接続文字列には、一連 ODBC ドライバーでサポートされているすべての接続情報を指定するキーワードと値のペアにはが含まれています。 各ドライバーでは、ドライバーでサポートされるすべての接続情報を表すドライバー固有のキーワード以外に、標準の ODBC キーワード (DSN、FILEDSN, DRIVER、UID、PWD、および SAVEFILE) をサポートします。 **SQLDriverConnect**せず、データ ソースの接続に使用できます。 たとえばのインスタンスに「DSN のない」接続を作成するように設計されたアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]呼び出すことができます**SQLDriverConnect**ログイン ID、パスワード、ネットワーク ライブラリ、サーバーの名前を定義する接続文字列を使用接続して、既定のデータベースを使用します。  
  
 使用する場合**SQLDriverConnect**、接続情報が必要なすべてのユーザーに確認の 2 つのオプションがあります。  
  
-   アプリケーション ダイアログ ボックス  
  
     接続情報の入力を要求しを呼び出してアプリケーション ダイアログ ボックスを作成することができます**SQLDriverConnect** NULL ウィンドウ ハンドルを持つと*DriverCompletion*に SQL_DRIVER_NOPROMPT を設定します。 このようにパラメーターを設定すると、ODBC ドライバー独自のダイアログ ボックスが開かれなくなります。 この方法は、アプリケーションでユーザー インターフェイスを制御することが重要な場合に使用します。  
  
-   ドライバー ダイアログ ボックス  
  
     有効なウィンドウ ハンドルを渡すためにアプリケーションをコーディングできます**SQLDriverConnect**設定と、 *DriverCompletion* SQL_DRIVER_COMPLETE、SQL_DRIVER_PROMPT、または SQL_DRIVER_COMPLETE_ パラメーター必須。 この場合、ドライバーがダイアログ ボックスを生成して、ユーザーに接続情報を要求します。 この方法を使用すると、アプリケーション コードが簡素化されます。  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **SQLBrowseConnect**と同様、 **SQLDriverConnect**、接続文字列を使用します。 使用して、ただし、 **SQLBrowseConnect**アプリケーションは、実行時に、データ ソースとやり取りしながら完全な接続文字列を構築できます。 この方法を使用すると、アプリケーションで次の 2 つのことを行えます。  
  
-   アプリケーション独自のダイアログ ボックスを作成して目的の情報を要求できるので、アプリケーションのユーザー インターフェイスで制御できます。  
  
-   特定のドライバーが使用できるデータ ソースをシステムから参照できます。これは複数の手順になる場合があります。  
  
     たとえば、ユーザーは最初にネットワークを介してサーバーを参照して、サーバーを選択します。次に、そのサーバーを介して、ドライバーがアクセスできるデータベースを参照するといった手順です。  
  
 ときに**SQLBrowseConnect**正常な接続が完了する後続の呼び出しで使用できる接続文字列を返します**SQLDriverConnect**です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは常に正常に実行で SQL_SUCCESS_WITH_INFO を返します**SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**です。 ODBC アプリケーションを呼び出すと**SQLGetDiagRec** SQL_SUCCESS_WITH_INFO を取得した後、次のメッセージを受信できます。  
  
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
  
 5701 と 5703 のメッセージは、情報提供だけを目的としているので無視できます。 ただし、SQL_SUCCESS_WITH_INFO リターン コードでは 5701 や 5703 以外のメッセージも返されることがあるので、そのようなリターン コードは無視しないでください。 ドライバーがのインスタンスを実行しているサーバーに接続する場合など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を通じて返さエラーのいずれかの古いカタログ ストアド プロシージャで**SQLGetDiagRec** SQL_SUCCESS_WITH_INFO 後。  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 エラー処理用のアプリケーションの関数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続を呼び出す必要があります**SQLGetDiagRec** sql_no_data が返されるまでです。 持つ方以外のすべてのメッセージでが機能し、 *pfNative* 5701 または 5703 のコード。  
  
## <a name="see-also"></a>参照  
 [SQL Server との通信&#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
