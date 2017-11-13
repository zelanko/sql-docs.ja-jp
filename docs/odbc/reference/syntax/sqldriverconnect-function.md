---
title: "SQLDriverConnect 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLDriverConnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDriverConnect
helpviewer_keywords:
- SQLDriverConnect function [ODBC]
ms.assetid: e299be1d-5c74-4ede-b6a3-430eb189134f
caps.latest.revision: 50
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8b9576bf21c922c1e8d223710210a1703f1cbec3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqldriverconnect-function"></a>SQLDriverConnect 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLDriverConnect**に代わる**SQLConnect**です。 次の 3 つの引数よりも多くの接続情報を必要とするデータ ソースがサポートしています**SQLConnect**、すべての接続情報、およびシステムで定義されていないデータ ソースのユーザー入力を求めるダイアログ ボックス情報です。  
  
 **SQLDriverConnect**次の接続属性を提供します。  
  
-   データ ソースによってデータ ソース名、1 つまたは複数のユーザー Id、1 つまたは複数のパスワード、および必要なその他の情報を保持する接続文字列を使用して接続を確立します。  
  
-   部分的な接続文字列または追加情報はありません。 を使用して接続を確立します。ここでは、ドライバー マネージャーとドライバーできます各ユーザーに要求接続情報です。  
  
-   システム情報で定義されていないデータ ソースへの接続を確立します。 場合は、アプリケーションでは、部分的な接続文字列を指定、ドライバーは接続情報をユーザーに求めますことができます。  
  
-   .Dsn ファイル内の情報に基づいて構築された接続文字列を使用してデータ ソースへの接続を確立します。  
  
 接続が確立されると、 **SQLDriverConnect**完成した接続文字列を返します。 アプリケーションでは、以降の接続要求に対して、この文字列を使用できます。 詳細については、次を参照してください。 [SQLDriverConnect を使用した接続](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLDriverConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLHWND         WindowHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr,  
     SQLUSMALLINT    DriverCompletion);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
 *WindowHandle*  
 [入力]ウィンドウ ハンドル。 該当する場合、アプリケーションは、親ウィンドウのハンドルを渡すことができますか、null ポインターの場合は、いずれかのウィンドウ ハンドルは、該当するはまたは**SQLDriverConnect**一切 ダイアログ ボックスが表示されます。  
  
 *InConnectionString*  
 [入力]完全な接続文字列 (「コメント」内の構文を参照)、部分的な接続文字列、または空の文字列。  
  
 *StringLength1*  
 [入力]長さ **InConnectionString*、文字の文字列の場合、Unicode、またはバイトの文字列は ANSI または DBCS 場合。  
  
 *OutConnectionString*  
 [出力]完全な接続文字列のバッファーへのポインター。 ターゲット データ ソースへの接続に成功したときに、このバッファーには、完全な接続文字列が含まれています。 アプリケーションは、このバッファーの少なくとも 1,024 文字を割り当てる必要があります。  
  
 場合*OutConnectionString* null、 *StringLength2Ptr*は文字 (文字データの null 終端文字を除く) の合計数を返しますが、バッファーに返される使用可能なによって示される*OutConnectionString*です。  
  
 *BufferLength*  
 [入力]長さ、**OutConnectionString*文字バッファー。  
  
 *StringLength2Ptr*  
 [出力]文字 (null 終了文字を除く) の合計数を返すバッファーへのポインターで返される使用可能な\* *OutConnectionString*です。 返される文字数がより大きいかに等しい場合*BufferLength*、内の接続文字列を完了した\* *OutConnectionString*に切り捨てられます*BufferLength* null 終端文字の長さマイナスです。  
  
 *DriverCompletion*  
 [入力]ドライバー マネージャーまたはドライバーが接続の詳細について求める必要があるかどうかを示すフラグ。  
  
 SQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE、SQL_DRIVER_COMPLETE_REQUIRED、または SQL_DRIVER_NOPROMPT です。  
  
 (詳細については、「コメント」を参照してください)  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_STILL_EXECUTING です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLDriverConnect** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します、関連付けられた SQLSTATE 値を呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *fHandleType*sql_handle_dbc としての*hHandle*の*ConnectionHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLDriverConnect**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|バッファー \* *OutConnectionString*容量が不足を全体の接続文字列を返すため、接続文字列が切り捨てられました。 切り詰められていない接続文字列の長さが返される **StringLength2Ptr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S00|無効な接続文字列の属性|接続文字列に無効な属性キーワードが指定されました (*InConnectionString*) が、ドライバーが、データ ソースに接続できませんでした。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプション値が変更されました|ドライバーが指す指定の値をサポートしていません、 *ValuePtr*引数**SQLSetConnectAttr**と同様の値を置換します。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S08|ファイル DSN の保存エラー|内の文字列 *\*InConnectionString*に含まれる、 **FILEDSN**キーワード、ただし .dsn ファイルは保存されませんでした。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S09|無効なキーワード|(DM) 内の文字列 *\*InConnectionString*に含まれる、 **SAVEFILE**キーワードがない、**ドライバー**または**FILEDSN**キーワードです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08001|クライアント接続を確立できません。|ドライバーは、データ ソースとの接続を確立できませんでした。|  
|08002|使用されている接続名|(DM)、指定した*ConnectionHandle*データ ソースとの接続を確立するために既に使用されていた接続がまだ開かれていたとします。|  
|08004|サーバー接続を拒否しました|データ ソースには、実装定義上の理由から、接続の確立が拒否されました。|  
|08S01|通信リンクが失敗しました|前に、ドライバーとする、ドライバーが接続を試みたデータ ソース間の通信リンクが失敗しました、 **SQLDriverConnect**関数は完了しました処理します。|  
|28000|無効な権限の指定|ユーザー id、承認文字列またはその両方の接続文字列で指定されている (*InConnectionString*)、データ ソースで定義された制限に違反します。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*szMessageText*バッファーは、エラーとその原因について説明します。|  
|HY000|一般的なエラー: 無効なファイル dsn|(DM) 内の文字列 **InConnectionString* FILEDSN キーワードが含まれているが、.dsn ファイルの名前が見つかりませんでした。|  
|HY000|一般的なエラー: ファイル バッファーを作成できません。|(DM) 内の文字列 **InConnectionString* FILEDSN キーワードが含まれているが、.dsn ファイルを読み取れませんでした。|  
|HY001|メモリ割り当てエラー|ドライバー マネージャーが実行またはの完了をサポートするために必要なメモリを割り当てることができませんでした、 **SQLDriverConnect**関数。<br /><br /> ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *ConnectionHandle*です。 関数が呼び出された、および実行を完了する前に、 [SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)で呼び出されましたが、 *ConnectionHandle*、し、 **SQLDriverConnect**関数がもう一度、 *ConnectionHandle*です。<br /><br /> また、 **SQLDriverConnect**関数が呼び出され、実行を完了する前に**SQLCancelHandle**で呼び出されましたが、 *ConnectionHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM) 別の非同期的に実行中の関数 (いない**SQLDriverConnect**) で呼び出され、 *ConnectionHandle*ときに実行されていると、 **SQLDriverConnect**関数が呼び出されました。|  
|HY013|メモリ管理エラー|**SQLDriverConnect**基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|引数の指定された値 (DM) *StringLength1* 0 より小さい、SQL_NTS に等しいされませんでした。<br /><br /> 引数の指定された値 (DM) *BufferLength*が 0 未満です。|  
|HY092|無効な属性またはオプション識別子|(DM)、 *DriverCompletion*引数が SQL_DRIVER_PROMPT、および*WindowHandle*引数が null ポインターでした。|  
|HY110|ドライバーが正しく完了|(DM) 引数の値が指定された*DriverCompletion* SQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE、SQL_DRIVER_COMPLETE_REQUIRED、または SQL_DRIVER_NOPROMPT と等しいでした。<br /><br /> (DM) 接続プールが有効になり、引数が指定された値*DriverCompletion*を SQL_DRIVER_NOPROMPT に等しいでした。|  
|HYC00|省略可能な機能が実装されていません|ドライバーは、アプリケーションが要求した ODBC の動作のバージョンをサポートしていません。|  
|HYT00|タイムアウトが発生しました|完了したデータ ソースに接続する前に、ログイン タイムアウト期間が期限切れです。 によって、タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_LOGIN_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) 指定したデータ ソース名に対応するドライバーは、関数をサポートしていません。|  
|IM002|データ ソースが見つかりません、指定された既定のドライバー|(DM) データ ソースの接続文字列で指定された名前 (*InConnectionString*) が、システム情報に見つからなかったし、既定ドライバーの指定がありませんでした。<br /><br /> (DM) システム情報 ODBC データ ソースと既定のドライバー情報が見つかりませんでした。|  
|IM003|指定されたドライバーを読み込むことができませんでした。|(DM)、ドライバーは、システム情報でデータ ソースの指定に一覧表示またはで指定された、**ドライバー**キーワードが見つからなかったか、またはその他の何らかの理由をロードできませんでした。|  
|IM004|ドライバーの**SQLAllocHandle**を SQL_HANDLE_ENV に失敗しました|(DM) 中に**SQLDriverConnect**、ドライバー マネージャーがドライバーのと呼ばれる**SQLAllocHandle**で機能、 *fHandleType* SQL_HANDLE_ENV とドライバーの返される、エラーがあります。|  
|IM005|ドライバーの**SQLAllocHandle**を sql_handle_dbc としてできませんでした。|(DM) 中に**SQLDriverConnect**、ドライバー マネージャーがドライバーのと呼ばれる**SQLAllocHandle**で機能、 *fHandleType* sql_handle_dbc としてとドライバーの返される、エラーがあります。|  
|IM006|ドライバーの**SQLSetConnectAttr**できませんでした|(DM) 中に**SQLDriverConnect**、ドライバー マネージャーがドライバーのと呼ばれる**SQLSetConnectAttr**関数と、ドライバーにエラーが返されます。|  
|IM007|データ ソースまたは; 指定されたドライバーなしダイアログを表示できません。|データ ソース名またはドライバーが指定されていない接続文字列と*DriverCompletion* SQL_DRIVER_NOPROMPT がします。|  
|IM008|ダイアログに失敗しました|ドライバーは、[ログイン] ダイアログ ボックスを表示しようとし、失敗しました。<br /><br /> *WindowHandle*が null ポインターの場合と*DriverCompletion* SQL_DRIVER_NO_PROMPT でした。|  
|IM009|トランスレーター DLL を読み込めません。|ドライバーは、変換、データ ソースまたは接続の指定された DLL を読み込むことでした。|  
|IM010|データ ソース名が長すぎます|(DM) DSN キーワードの属性の値は、SQL_MAX_DSN_LENGTH 文字を超えていました。|  
|IM011|ドライバー名が長すぎます|(DM) の場合は、属性値、**ドライバー**キーワードが 255 文字より長かった。|  
|IM012|DRIVER キーワードの構文エラー|(DM) キーワードと値のペア、**ドライバー**キーワードには、構文エラーが含まれています。<br /><br /> (DM) 内の文字列 *\*InConnectionString*に含まれる、 **FILEDSN**キーワード、ただし .dsn ファイルがありませんでした、**ドライバー**キーワードまたは**DSN**キーワード。|  
|IM014|指定の DSN にはなアーキテクチャと一致しないドライバーとアプリケーションが含まれています|(DM) 32 ビット アプリケーションでは、64 ビット ドライバー; に接続する DSN を使用します。またはその逆です。|  
|IM015|ドライバーの SQLDriverConnect SQL_HANDLE_DBC_INFO_HANDLE に失敗しました|ドライバーでは、SQL_ERROR が返された場合、ドライバー マネージャーは、アプリケーションに SQL_ERROR を返し、接続は失敗します。<br /><br /> SQL_HANDLE_DBC_INFO_TOKEN の詳細については、次を参照してください。 [ODBC ドライバーで接続プールの認識開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)です。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
|S1118|ドライバーは非同期通知をサポートしていません|ドライバーが非同期通知をサポートしていない場合は、SQL_ATTR_ASYNC_DBC_EVENT または SQL_ATTR_ASYNC_DBC_RETCODE_PTR を設定できません。|  
  
## <a name="comments"></a>コメント  
 接続文字列には、次の構文があります。  
  
 *接続文字列*:: =*空文字列*[;] &#124;です。*属性*[;] &#124;です。*属性*です。*接続文字列*  
  
 *空の文字列*:: =*属性*:: =*属性キーワード*=*属性と値*&#124;です。ドライバー = [{}]*属性と値*[}]  
  
 *属性キーワード*:: = DSN &#124;です。UID &#124;です。PWD &#124;です。*ドライバーの定義の属性のキーワード*  
  
 *属性値*:: =*文字の文字列*  
  
 *ドライバーの定義の属性-キーワード*:: =*識別子*  
  
 ここで*文字列*0 個以上の文字です。*識別子*が 1 つ以上の文字です。*属性キーワード*; 大文字小文字を区別することはありません*属性と値*可能性があります。 大文字小文字を区別しの値、 **DSN**空白だけのキーワードはで構成されていません。  
  
 接続文字列および初期化ファイルの文法、キーワード、および属性値のため、文字を含む**{} ()、;?\*=! @**で囲まれていない中かっこを避ける必要があります。 値、 **DSN**キーワードは、空白のみ含めることはできませんし、先頭の空白を含めることはできません。 システム情報の文法、ためキーワードおよびデータ ソース名が円記号を含めることはできません (\\) 文字です。  
  
 アプリケーションは、後の属性値を囲む中かっこを追加する必要はありません、**ドライバー**キーワード属性をセミコロン (;) が含まれている場合を除き、その場合は、中かっこが必要です。 ドライバーが受信した属性値には、中かっこが含まれている場合、ドライバーは削除せずけれども、返される接続文字列の一部である必要があります。  
  
 DSN または接続文字列値を中かっこ ({}) の文字を含む**{} ()、;?\*=! @**ドライバーにそのまま渡されます。 ただしをキーワードには、これらの文字を使用して、ドライバー マネージャーはファイル Dsn を使用するときにエラーが返されますが、通常の接続文字列用のドライバーに接続文字列を渡します。 キーワードの値に埋め込まれた中かっこを使用しないでください。  
  
 接続文字列には、任意の数のドライバー定義のキーワードを含めることがあります。 **ドライバー**キーワードは、システム情報の情報を使用していない、ドライバーは、接続文字列に情報のみを使用してデータ ソースに接続できるように、ドライバーは十分なキーワードを定義する必要があります。 (詳細については、このセクションで後述の「ドライバー ガイドライン」を参照してください)。ドライバーは、データ ソースへの接続に必要などのキーワードを定義します。  
  
 次の表の属性値、 **DSN**、 **FILEDSN**、**ドライバー**、 **UID**、 **PWD**、および**SAVEFILE**キーワード。  
  
|Keyword|属性値の説明|  
|-------------|---------------------------------|  
|**DSN**|によって返されるデータ ソースの名前**SQLDataSources**または、データ ソース ダイアログ ボックスの**SQLDriverConnect**です。|  
|**FILEDSN**|データ ソースの接続文字列の作成元となる .dsn ファイルの名前。 これらのデータ ソースは、ファイルのデータ ソースと呼ばれます。|  
|**ドライバー**|によって返されるドライバーの説明、 **SQLDrivers**関数。 たとえば、Rdb または SQL Server。|  
|**UID**|ユーザーの id です。|  
|**PWD**|ユーザー ID のパスワードが存在しない場合は、ユーザー ID、または空の文字列に対応するパスワード (PWD =;)。|  
|**SAVEFILE**|現時点では、成功した接続の確立に使用されるキーワードの属性値を保存する .dsn ファイルのファイル名。|  
  
 アプリケーションがデータ ソースまたはドライバーを選択する方法については、次を参照してください。[データ ソースまたはドライバーを選択する](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)です。  
  
 で接続文字列のキーワードが繰り返される場合、ドライバーは、最初に見つかった、キーワードに関連付けられている値を使用します。 場合、 **DSN**と**ドライバー**キーワードは、同じ接続文字列に含まれる、ドライバー マネージャーとドライバーを使用して最初にどちらのキーワードが表示されます。  
  
 **FILEDSN**と**DSN**キーワードは相互に排他的: どちらのキーワードが最初に表示が使用され、2 番目に表示される 1 つは無視されます。 **FILEDSN**と**ドライバー**キーワード、その一方はいない相互に排他的です。 任意のキーワードが使用した接続文字列で表示された場合は**FILEDSN**、.dsn ファイルに同じキーワードの属性値ではなく、接続文字列内のキーワードの属性値が使用されます。  
  
 場合、 **FILEDSN**キーワードを使用して、.dsn ファイルで指定されたキーワードを使用して接続文字列を作成します。 (詳細については、「ファイル データ ソース、」このセクションの後半を参照してください)。**UID**キーワードは省略可能です。 .dsn ファイルが作成されるだけ、**ドライバー**キーワード。 **PWD**キーワードが .dsn ファイルに格納されません。 保存と読み込み .dsn ファイルの既定のディレクトリで指定されたパスの組み合わせになります**CommonFileDir** hkey_local_machine \software\microsoft\ Windows\CurrentVersion および"ODBC\DataSources"です。 (CommonFileDir"C:\Program files \common files Files"場合は、既定のディレクトリになります"C:\Program files \common files 場合 Sources"です。)  
  
> [!NOTE]  
>  .Dsn ファイルを呼び出すことによって直接操作できる、 [SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)と[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)インストーラー DLL で機能します。  
  
 場合、 **SAVEFILE**キーワードを使用して、現時点では、成功した接続の確立に使用されるキーワードの属性値がの属性値の名前を持つ .dsn ファイルとして保存されます、 **SAVEFILE**キーワードです。 **SAVEFILE**キーワードを組み合わせて使用する必要があります、**ドライバー** 、キーワード、 **FILEDSN**キーワード、またはその両方か、関数と SQL_SUCCESS_WITH_INFO が返されますSQLSTATE 01S09 (無効なキーワード) です。 **SAVEFILE**キーワードを記述する前に、**ドライバー**キーワード、接続文字列、または結果が定義されていることができます。  
  
## <a name="driver-manager-guidelines"></a>ドライバー マネージャーのガイドライン  
 ドライバー マネージャーがドライバーに渡す接続文字列を構築、 *InConnectionString*のドライバーの引数**SQLDriverConnect**関数。 ドライバー マネージャーでは変更されません、 *InConnectionString*にアプリケーションによって渡される引数。  
  
 操作の Driver Manager の値に基づいて、 *DriverCompletion*引数。  
  
-   SQL_DRIVER_PROMPT: いずれかの接続文字列が含まれない場合、**ドライバー**、 **DSN**、または**FILEDSN**キーワード、ドライバー マネージャーがデータ ソース ダイアログ ボックスを表示します。 ダイアログ ボックスによって返されるデータ ソース名と、アプリケーションによって渡されたその他のキーワードから接続文字列を構築します。 ドライバー マネージャーが、DSN キーワードと値のペアを指定します ダイアログ ボックスによって返されるデータ ソース名が空の場合は、既定値を = です。 (このダイアログ ボックスは、"Default"の名前を持つデータ ソースを表示はされません)。  
  
-   SQL_DRIVER_COMPLETE または SQL_DRIVER_COMPLETE_REQUIRED: アプリケーションによって指定された接続文字列が含まれている場合、 **DSN**キーワード、ドライバー マネージャーが、アプリケーションで指定された接続文字列をコピーします。 それ以外の場合、同じはアクションを実行時に*DriverCompletion* SQL_DRIVER_PROMPT がします。  
  
-   SQL_DRIVER_NOPROMPT: ドライバー マネージャーは、アプリケーションで指定された接続文字列をコピーします。  
  
 アプリケーションで指定された接続文字列が含まれている場合、**ドライバー**キーワード、ドライバー マネージャーが、アプリケーションで指定された接続文字列をコピーします。  
  
 構築、接続文字列を使用して、ドライバー マネージャーは、使用するドライバーを決定、そのドライバーに接続し、接続文字列が構築ドライバーに渡します、です。ドライバー マネージャーとドライバーの相互動作に関する詳細についてを参照してください「コメント」 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)です。 接続文字列が含まれていない場合、**ドライバー**キーワード、ドライバー マネージャーは、次のように使用するドライバーを決定します。  
  
1.  接続文字列が含まれている場合、 **DSN**キーワード、ドライバー マネージャーは、システムについては、元のデータ ソースに関連付けられたドライバを取得します。  
  
2.  接続文字列が含まれていない場合、 **DSN**キーワードまたはデータ ソースが見つからないと、ドライバー マネージャーは、システム情報の既定のデータ ソースに関連付けられたドライバを取得します。 (詳細については、次を参照してください[サブキーの既定の](../../../odbc/reference/install/default-subkey.md)。)。ドライバー マネージャーの値を変更する、 **DSN** "DEFAULT"への接続文字列キーワードです。  
  
3.  場合、 **DSN**接続文字列キーワードでは、"DEFAULT"に設定されて、ドライバー マネージャーは、システム情報の既定のデータ ソースに関連付けられたドライバを取得します。  
  
4.  ドライバー マネージャーが SQLSTATE IM002 で SQL_ERROR を返します、データ ソースが見つからない場合は、既定のデータ ソースが見つからない場合は、(データ ソースが見つかりません。 および指定された既定のドライバー)。  
  
## <a name="file-data-sources"></a>[ファイル データ ソース]  
 呼び出しで、アプリケーションによって接続文字列が指定されている場合**SQLDriverConnect**が含まれています、 **FILEDSN**キーワード、およびこのキーワードは、いずれかでが置き換えられない、 **DSN**または**ドライバー** .dsn ファイルに情報を使用して接続文字列を作成し、キーワードで、ドライバー マネージャー、および*InConnectionString*引数。 ドライバー マネージャーは、次のように処理されます。  
  
1.  .Dsn ファイルのファイル名が有効かどうかを確認します。 Not、SQLSTATE IM014 で SQL_ERROR が返された場合 (ファイル DSN の名が無効です)。 ファイル名が空の文字列である場合 ("") SQL_DRIVER_NOPROMPT がないと、指定された、**ファイルを開く** ダイアログ ボックスが表示されます。 有効なパスが、ファイル名のない、または無効なファイル名、ファイル名が含まれていて、SQL_DRIVER_NOPROMPT が指定されていない場合、**ファイルを開く**現在のディレクトリとファイル名で指定されたいずれかに設定 ダイアログ ボックスが表示されます。 ファイル名が空の文字列である場合 ("") またはファイル名には、有効なパスが、ファイル名のない、または、無効なファイル名が含まれている SQL_DRIVER_NOPROMPT が指定されているし、SQLSTATE IM014 と共に SQL_ERROR が返されます (ファイル DSN の名が無効です)。  
  
2.  .Dsn ファイルの [ODBC] セクションですべてのキーワードを読み取ります。 場合、**ドライバー**キーワードが存在しない、SQLSTATE IM012 で SQL_ERROR が返されます (ドライバー キーワードの構文エラー)、.dsn ファイルが共有可能ではないと、したがってのみが含まれますを除く、 **DSN**キーワード。  
  
     ドライバー マネージャーがの値を読み取るファイルのデータ ソースが共有可能でない場合、 **DSN**キーワードし、必要に応じて、ユーザーまたはシステム データ ソースを指す共有不能なファイルのデータ ソースに接続します。 手順 3. ~ 5. を実行しません。  
  
3.  ドライバーの接続文字列を構築します。 ドライバーの接続文字列は、.dsn ファイルで指定されたキーワードと、元のアプリケーション接続文字列で指定されている和集合です。 ドライバーの接続文字列キーワードと重なる部分を構築するための規則は次のとおりです。  
  
    -   場合、**ドライバー**キーワードは、アプリケーションの接続文字列とで指定されたドライバーが存在する、**ドライバー**キーワードが同じでない .dsn ファイル サービスおよびアプリケーションの接続文字列で、.dsn ファイル内のドライバー情報は無視され、アプリケーションの接続文字列内のドライバー情報を使用します。 ドライバーが指定されている場合、**ドライバー**キーワードは、同じ .dsn ファイル サービスおよびアプリケーションの接続文字列より優先順位があるアプリケーションの接続文字列で指定されているすべてのキーワードが重なると、場所.dsn ファイルで指定します。  
  
    -   新しい接続文字列で、 **FILEDSN**キーワードを削除します。  
  
4.  レジストリ エントリ見つかりましたでを調べることで、ドライバーを読み込みます。INI\\< ドライバー名\>\Driver 場所\<ドライバー名 > で指定された、**ドライバー**キーワード。  
  
5.  ドライバーの新しい接続文字列を渡します。  
  
 .Dsn ファイルの例については、次を参照してください。[を使用してファイル データ ソースの接続](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)です。  
  
## <a name="savefile-keyword"></a>SAVEFILE キーワード  
 アプリケーションで指定された接続文字列が含まれている場合、 **SAVEFILE**キーワード、そのドライバー マネージャーは、.dsn ファイルに接続文字列を保存します。 ドライバー マネージャーは、次のように処理されます。  
  
1.  属性値として .dsn ファイルのファイル名が含まれるかどうかを確認、 **SAVEFILE**キーワードは無効です。 Not、SQLSTATE IM014 で SQL_ERROR が返された場合 (ファイル DSN の名が無効です)。 ファイル名の有効性は、標準のシステムの名前付け規則によって決定されます。 ファイル名が空の文字列である場合 ("")、および*DriverCompletion*引数が SQL_DRIVER_NOPROMPT ではありませんし、ファイル名が無効です。 場合は、ファイル名が存在し、場合*DriverCompletion* SQL_DRIVER_NOPROMPT には、ファイルが上書きされます。 場合*DriverCompletion* SQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE、または SQL_DRIVER_COMPLETE_REQUIRED の場合は、求めるダイアログ ボックスが、ユーザーをファイルを上書きするかどうかを指定します。 × の場合は、**ファイルの保存** ダイアログ ボックスが表示されます。  
  
2.  かどうか、ドライバーは SQL_SUCCESS を返しますとファイル名が空の文字列ではありませんし、ドライバー マネージャーは、出力で返される接続情報、 *OutConnectionString*で指定された形式で指定したファイルへの引数このセクションの前半「接続文字列」セクションです。  
  
3.  ドライバーは SQL_SUCCESS を返し、ファイル名は空の文字列 ("")、ドライバー マネージャーは呼び出して、**ファイルの保存**で共通のダイアログ ボックス、 *hwnd*指定し、接続情報を書き込みます返される*OutConnectionString*ファイルの保存のコモン ダイアログ ボックスのこのセクションで、「接続文字列」セクションで指定された形式で指定されたファイルにします。  
  
4.  かどうか、ドライバーは SQL_SUCCESS を返しますが返されます、 *OutConnectionString*アプリケーションへの接続文字列が含まれる引数。  
  
5.  ドライバーは、SQL_SUCCESS_WITH_INFO または SQL_ERROR を返します場合、ドライバー マネージャーを返します、SQLSTATE、アプリケーションにします。  
  
## <a name="driver-guidelines"></a>ドライバーのガイドライン  
 ドライバーがドライバー マネージャーによって渡された接続文字列に含まれるかどうかを確認、 **DSN**または**ドライバー**キーワード。 接続文字列が含まれている場合、**ドライバー**キーワード、ドライバーは、システム情報からデータ ソースに関する情報を取得することはできません。 接続文字列が含まれている場合、 **DSN**キーワードが含まれていないか、または、 **DSN**または**ドライバー**キーワード、ドライバーは、データ ソースに関する情報を取得できます次のようにシステム情報。  
  
1.  接続文字列が含まれている場合、 **DSN**キーワード、ドライバーは、指定したデータ ソースの情報を取得します。  
  
2.  接続文字列が含まれていない場合、 **DSN**キーワードを指定したデータ ソースが見つからない、または**DSN**キーワードは、"DEFAULT"に設定されて、ドライバーは、既定のデータ ソースの情報を取得.  
  
 ドライバーでは、接続文字列で渡された情報を拡張するためにシステム情報から取得任意の情報が使用されます。 システム情報の情報は、接続文字列の情報が重複する場合、ドライバーは、接続文字列に情報を使用します。  
  
 値に基づく*DriverCompletion*ドライバーは、ユーザー、ユーザー ID とパスワードなどの接続情報を要求し、データ ソースに接続します。  
  
-   SQL_DRIVER_PROMPT: ドライバーには、値を使用して、接続文字列とシステム情報 (存在する場合) の初期値として、ダイアログ ボックスが表示されます。 ユーザーは、ダイアログ ボックスを終了すると、ドライバーは、データ ソースに接続します。 値からの接続文字列を構築、 **DSN**または**ドライバー**キーワード\* *InConnectionString*から返される情報、ダイアログ ボックス。 この接続文字列を配置、**OutConnectionString*バッファー。  
  
-   SQL_DRIVER_COMPLETE または SQL_DRIVER_COMPLETE_REQUIRED: 接続文字列には、十分な情報が含まれています、その情報が正しい場合は、ドライバーは、データ ソースとコピーに接続\* *InConnectionString*に\* *OutConnectionString*です。 情報が不足または無効の場合は、ドライバー同じはアクションを実行時に*DriverCompletion*似ているが、SQL_DRIVER_PROMPT は、 *DriverCompletion* SQL_DRIVER_COMPLETE_ には必要に応じて、ドライバーはいないデータ ソースに接続するために必要な情報のコントロールを無効にします。  
  
-   SQL_DRIVER_NOPROMPT: 接続文字列に十分な情報が含まれている場合、ドライバーで接続をデータ ソースとコピー \* *InConnectionString*に\* *OutConnectionString*. ドライバーは SQL_ERROR を返しますそれ以外の場合、 **SQLDriverConnect**です。  
  
 ドライバーのデータ ソースへの接続に成功の設定も\* *StringLength2Ptr*で返される使用可能な出力の接続文字列の長さ **OutConnectionString*です。  
  
 ユーザーが、ドライバー マネージャー、または、ドライバーによって提示されるダイアログ ボックスを取り消す場合**SQLDriverConnect** SQL_NO_DATA が返されます。  
  
 ドライバー マネージャーとドライバーが接続プロセス中にどのように対話する方法については、次を参照してください。 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)です。  
  
 ドライバーがサポートする場合は**SQLDriverConnect**のシステム情報、ドライバーをドライバー キーワード セクションに含める必要があります、 **ConnectFunctions**キーワード 2 番目の文字では、"Y"に設定します。  
  
## <a name="connecting-when-connection-pooling-is-enabled"></a>接続プールが有効になっているときに接続します。  
 接続プールと、アプリケーションを既に作成されている接続を再利用ができます。 ときに**SQLDriverConnect**が呼び出されると、ドライバー マネージャーの試行の接続プールに指定されている環境での接続のプールの一部である接続を使用して接続を作成します。 接続プールの詳細については、次を参照してください。 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)です。  
  
 アプリケーションでは、プールが有効になる接続で SQLDisconnect を呼び出す前に、SQL_ATTR_RESET_CONNECTION を設定できます。 詳細については、次を参照してください。 [SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)です。  
  
 アプリケーションを呼び出すときに、次の制限が適用**SQLDriverConnect**プールされた接続に接続します。  
  
-   接続プールの処理は行われませんときに、 **SAVEFILE**接続文字列でキーワードを指定します。  
  
-   接続プールを有効にすると場合、 **SQLDriverConnect**でのみ呼び出すことができる、 *DriverCompletion* SQL_DRIVER_NOPROMPT の引数以外の場合は**SQLDriverConnect**は呼び出されますその他の*DriverCompletion*、SQLSTATE HY110 (ドライバーが正しく完了) が返されます。  
  
## <a name="connection-attributes"></a>接続属性  
 使用して設定、SQL_ATTR_LOGIN_TIMEOUT 接続属性**SQLSetConnectAttr**、ログイン要求をアプリケーションに返す前に、ドライバーで接続に成功すると完了するまで待機する秒数を定義します。 ユーザーは、接続文字列を完了するように求められたら、ドライバーは接続プロセスの開始時に各ログイン要求の待機時間を開始します。  
  
 ドライバーは、既定では、SQL_MODE_READ_WRITE アクセス モードで接続を開きます。 アプリケーションを呼び出す必要があります、アクセス モードに設定する SQL_MODE_READ_ONLY、 **SQLSetConnectAttr**呼び出しの前に SQL_ATTR_ACCESS_MODE 属性を持つ**SQLDriverConnect**です。  
  
 既定のライブラリは翻訳がデータ ソースのシステム情報で指定されている場合に、ドライバーが読み込まれます。 呼び出して、別の翻訳ライブラリを読み込むことができます**SQLSetConnectAttr** SQL_ATTR_TRANSLATE_LIB 属性を持つ。 呼び出して変換オプションを指定できます**SQLSetConnectAttr** SQL_ATTR_TRANSLATE_OPTION オプションを使用します。  
  
 詳細については、次を参照してください。 [SQLDriverConnect を使用した接続](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)です。  
  
```  
// SQLDriverConnect_ref.cpp  
// compile with: odbc32.lib user32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
  
   SQLCHAR OutConnStr[255];  
   SQLSMALLINT OutConnStrLen;  
  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            retcode = SQLDriverConnect( // SQL_NULL_HDBC  
               hdbc,   
               desktopHandle,   
               (SQLCHAR*)"driver=SQL Server",   
               _countof("driver=SQL Server"),  
               OutConnStr,  
               255,   
               &OutConnStrLen,  
               SQL_DRIVER_PROMPT );  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {                 
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 参照してください[サンプル ODBC プログラム](../../../odbc/reference/sample-odbc-program.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|検出して、データ ソースへの接続に必要な値を列挙します。|[SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|データ ソースからの切断|[SQLDisconnect 関数](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|ドライバーの説明と属性を返す|[SQLDrivers 関数](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|ハンドルを解放します。|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

