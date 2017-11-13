---
title: "SQLSetConnectAttr 関数 |Microsoft ドキュメント"
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
- SQLSetConnectAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectAttr
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC]
ms.assetid: 97fc7445-5a66-4eb9-8e77-10990b5fd685
caps.latest.revision: 83
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4006d05403781ada24cf43903cd14a971366e12a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectattr-function"></a>SQLSetConnectAttr 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLSetConnectAttr**接続の側面を制御する属性を設定します。  
  
> [!NOTE]  
>  詳細については、どのようなドライバー マネージャーは、この関数にする際にマップ ODBC 3*.x* ODBC 2 を利用するアプリケーション*.x*ドライバーを参照してください[後方の置換関数のマッピングアプリケーションの互換性を](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLSetConnectAttr(  
     SQLHDBC       ConnectionHandle,  
     SQLINTEGER    Attribute,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    StringLength);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
 *属性*  
 [入力]属性を設定すると、「コメント」に一覧表示  
  
 *ValuePtr*  
 [入力]関連付けられる値へのポインター*属性*です。 値に応じて*属性*、 *ValuePtr*符号なし整数値となるかが null で終わる文字列を指します。 整数型を*属性*引数がない固定長であること、詳細の [コメント] セクションを参照してください。  
  
 *StringLength*  
 [入力]場合*属性*ODBC で定義された属性と*ValuePtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります **ValuePtr*です。 文字の文字列データでは、この引数は、文字列のバイト数を含める必要があります。  
  
 場合*属性*ODBC で定義された属性と*ValuePtr*整数*StringLength*は無視されます。  
  
 場合*属性*ドライバーの定義済みの属性は、アプリケーション、ドライバー マネージャーに属性の性質を示す設定、 *StringLength*引数。 *StringLength*次の値を持つことができます。  
  
-   場合*ValuePtr*文字の文字列へのポインターが*StringLength* SQL_NTS または文字列の長さです。  
  
-   場合*ValuePtr*アプリケーションが、SQL_LEN_BINARY_ATTR の結果を配置し、バイナリのバッファーへのポインターは、(*長さ*) マクロで*StringLength*です。 これにより、配置に負の値*StringLength*です。  
  
-   場合*ValuePtr*文字の文字列またはバイナリ文字列以外の値へのポインターが*StringLength* SQL_IS_POINTER 値でなければなりません。  
  
-   場合*ValuePtr*し、固定長の値を含む*StringLength*は SQL_IS_INTEGER か SQL_IS_UINTEGER、必要に応じて。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_STILL_EXECUTING です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetConnectAttr** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*のSql_handle_dbc としてと*処理*の*ConnectionHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLSetConnectAttr**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
 ドライバーは、オプションの設定の結果に関する情報を提供する SQL_SUCCESS_WITH_INFO を返すことができます。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプション値が変更されました|ドライバーがで指定された値をサポートしていません*ValuePtr*と同様の値を置換します。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08002|使用されている接続名|*属性*引数 SQL_ATTR_ODBC_CURSORS、れ、ドライバーが既にデータ ソースに接続されています。|  
|08003|接続は開いていません|(DM)、*属性*、開いている接続を必要とする値が指定されましたが、 *ConnectionHandle*接続状態ではありませんでした。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|*属性*引数 SQL_ATTR_CURRENT_CATALOG、れ、結果セットが保留されていました。|  
|25000|ローカル トランザクションの実行中の無効な操作|接続は、接続の SQL_ATTR_ENLIST_IN_DTC 属性を設定して、分散トランザクションの接続 (DTC) に参加しようとしています。 ローカルのトランザクションでした。<br /><br /> 接続は既に、DTC に参加しています。<br /><br /> 接続は分散トランザクションの接続に参加しているし、SQL_ATTR_AUTOCOMMIT を SQL_AUTOCOMMIT_OFF に設定して、ローカル トランザクションが開始されました。|  
|3D000|無効なカタログ名|*属性*引数が SQL_CURRENT_CATALOG、および指定したカタログ名が無効でした。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *ConnectionHandle*です。 **SQLSetConnectAttr**関数が呼び出され、実行を完了する前に、 [SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)で呼び出されましたが、 *ConnectionHandle*、し、**SQLSetConnectAttr**関数がもう一度、 *ConnectionHandle*です。<br /><br /> また、 **SQLSetConnectAttr**関数が呼び出され、実行を完了する前に**SQLCancelHandle**で呼び出されましたが、 *ConnectionHandle*の別のスレッドからマルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|*属性*引数が文字列値を必要とする接続属性を識別し、 *ValuePtr*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*に関連付けられている、 *ConnectionHandle*ときに実行されていると**SQLSetConnectAttr**が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *ConnectionHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかで呼び出され、 *ConnectionHandle* SQL_PARAM_DATA_AVAILABLE を返されるとします。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle*に関連付けられている、 *ConnectionHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) **SQLBrowseConnect**で呼び出され、 *ConnectionHandle* SQL_NEED_DATA が返されます。 この関数が呼び出されました**SQLBrowseConnect** SQL_SUCCESS_WITH_INFO または SQL_SUCCESS が返されます。|  
|HY011|属性を設定できません。|*属性*引数が SQL_ATTR_TXN_ISOLATION、およびトランザクションが開かれていた。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY024|無効な属性値|指定した*属性*値で、無効な値が指定されました*ValuePtr*です。 (ドライバー マネージャーは、この SQLSTATE 接続と SQL_ATTR_ACCESS_MODE または SQL_ATTR_ASYNC_ENABLE などの値の個別のセットをそのまま使用するステートメント属性に対してのみを返します。 他のすべての接続とステートメント属性のドライバーがで指定された値を確認する必要があります*ValuePtr*)。<br /><br /> *属性*引数が SQL_ATTR_TRACEFILE または SQL_ATTR_TRANSLATE_LIB、および*ValuePtr*が空の文字列。|  
|HY090|文字列またはバッファーの長さが無効です。|*(DM) \*ValuePtr*文字の文字列、および*StringLength*引数が 0 未満の値がでした SQL_NTS です。|  
|HY092|無効な属性またはオプション識別子|引数の指定された値 (DM)*属性*が ODBC ドライバーでサポートされているのバージョンは無効です。<br /><br /> 引数の指定された値 (DM)*属性*読み取り専用の属性であった。|  
|HY114|ドライバーは接続レベルの非同期関数の実行をサポートしていません|(DM) アプリケーションは、非同期の接続操作をサポートしていないドライバーの SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE で非同期関数の実行を有効にしようとしました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HY121|同時に、カーソル ライブラリとドライバー対応プールが有効にすることはできません。|詳細については、次を参照してください。[ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)です。|  
|HYC00|省略可能な機能が実装されていません|引数が指定された値*属性*が有効な ODBC 接続または ODBC のバージョンのステートメント属性はドライバーによってサポートされていますが、ドライバーによってサポートされていませんでした。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *ConnectionHandle*関数をサポートしていません。|  
|IM009|トランスレーター DLL を読み込めません。|ドライバーは翻訳の接続に指定された DLL を読み込めませんでした。 このエラーを返すことがされる場合にのみ*属性*SQL_ATTR_TRANSLATE_LIB がします。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
|S1118|ドライバーは非同期通知をサポートしていません|(接続が行われた) 後 SQL_ATTR_ASYNC_DBC_EVENT で設定されましたが、非同期の通知は、ドライバーによってサポートされていません。|  
  
 ときに*属性*ステートメント属性は**SQLSetConnectAttr**によって返される任意の SQLSTATEs を返すことができる**SQLSetStmtAttr**です。  
  
## <a name="comments"></a>コメント  
 一般的な接続属性については、次を参照してください。[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)です。  
  
 現在定義されている属性と導入された ODBC のバージョンです。 このセクションの後半の表に表示されます。さまざまなデータ ソースを活用するために多くの属性が定義されることが必要です。 属性の範囲は ODBC; によって予約されています。ドライバーの開発者は、Open Group から独自ドライバー固有の値を予約する必要があります。  
  
> [!NOTE]  
>  呼び出して、接続レベルでのステートメント属性を設定する機能**SQLSetConnectAttr** ODBC 3 では廃止されて*.x*です。 ODBC 3*.x*アプリケーションは、接続レベルでステートメント属性を設定しない必要があります。 ODBC 3*.x*を除き、SQL_ATTR_METADATA_ID と SQL_ATTR_ASYNC_ENABLE 属性は、接続属性とステートメント属性の両方とは、接続レベルでのステートメント属性を設定することはできません接続のレベルまたはステートメント レベルのいずれかに設定します。  
>   
>  ODBC 3*.x* ODBC 2 で機能する場合、ドライバーはこの機能をサポートのみ必要*.x* ODBC 2 を設定するアプリケーションに*.x*接続レベルでステートメントのオプションです。 詳細については、次を参照してください。 [SQLSetConnectOption マッピング](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
  
 アプリケーションが呼び出すことができます**SQLSetConnectAttr**までの間には、いつでも、接続が割り当てられ、解放します。 まで正常にアプリケーションによって設定される接続の接続とステートメントのすべての属性が永続化**SQLFreeHandle**接続で呼び出されます。 たとえば、アプリケーションを呼び出す**SQLSetConnectAttr**データ ソースに接続する、前に、属性が解決しない場合でも**SQLSetConnectAttr**ドライバーでアプリケーションが接続するときに失敗した、データ ソースです。アプリケーションでは、ドライバー固有の属性を設定、属性が解決しない場合、アプリケーションの接続で別のドライバーに接続する場合でもです。  
  
 接続が確立されました。 前にのみ、いくつかの接続属性を設定できます。他のユーザーは、接続が確立した後にのみ設定できます。 次の表では前に、または接続が確立した後に設定する必要があるこれらの接続属性を示します。 *いずれか*前に、または後の接続属性を設定できることを示します。  
  
|属性|前に、または後の接続を設定しますか。|  
|---------------|-------------------------------------|  
|SQL_ATTR_ACCESS_MODE|[1]|  
|SQL_ATTR_ASYNC_DBC_EVENT|接続前/接続後|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE|[4]|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK|接続前/接続後|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT|接続前/接続後|  
|SQL_ATTR_ASYNC_ENABLE|[2]|  
|SQL_ATTR_AUTO_IPD|接続前/接続後|  
|SQL_ATTR_AUTOCOMMIT|[5]|  
|SQL_ATTR_CONNECTION_DEAD|After|  
|SQL_ATTR_CONNECTION_TIMEOUT|接続前/接続後|  
|SQL_ATTR_CURRENT_CATALOG|[1]|  
|SQL_ATTR_DBC_INFO_TOKEN|After|  
|SQL_ATTR_ENLIST_IN_DTC|After|  
|SQL_ATTR_LOGIN_TIMEOUT|[指定日付より前]|  
|SQL_ATTR_METADATA_ID|接続前/接続後|  
|SQL_ATTR_ODBC_CURSORS|[指定日付より前]|  
|SQL_ATTR_PACKET_SIZE|[指定日付より前]|  
|SQL_ATTR_QUIET_MODE|接続前/接続後|  
|SQL_ATTR_TRACE|接続前/接続後|  
|SQL_ATTR_TRACEFILE|接続前/接続後|  
|SQL_ATTR_TRANSLATE_LIB|After|  
|SQL_ATTR_TRANSLATE_OPTION|After|  
|SQL_ATTR_TXN_ISOLATION|[3]|  
  
 [前に、または接続した後、ドライバーによっては、1] SQL_ATTR_ACCESS_MODE と SQL_ATTR_CURRENT_CATALOG を設定できます。 ただし、相互運用可能なアプリケーション設定に接続する前に一部のドライバーは接続後にこれらの変更をサポートしていないためです。  
  
 [アクティブなステートメントがある前に、2] SQL_ATTR_ASYNC_ENABLE を設定する必要があります。  
  
 [3] SQL_ATTR_TXN_ISOLATION は、接続で開かれたトランザクションがない場合にのみ設定できます。 データ ソースがで指定された値をサポートしていない場合、いくつかの接続属性サポートのような値の置換\* *ValuePtr*です。 このような場合は、ドライバーは SQL_SUCCESS_WITH_INFO と SQLSTATE 01S02 を返します。 (オプションの値が変更されました)。 たとえば場合、*属性*SQL_ATTR_PACKET_SIZE と\* *ValuePtr*パケットの最大サイズを超える場合、ドライバーは、最大サイズを置換します。 置換された値を決定するには、アプリケーションが呼び出す**SQLGetConnectAttr**です。  
  
 [呼び出し中にドライバーが読み込まれるときに 4] SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE は設定されている接続が開いて前に場合、ドライバー マネージャーでは、ドライバーの属性を設定は**SQLBrowseConnect**、 **SQLConnect**、または**SQLDriverConnect**です。 呼び出す前に**SQLBrowseConnect**、 **SQLConnect**、または**SQLDriverConnect**、ドライバー マネージャーに接続するには、どのドライバーが認識していないとが認識していないかどうか、ドライバーは、非同期の接続操作をサポートします。 そのため、ドライバー マネージャーでは、常に関係なく SQL_SUCCESS を返します。 ただし、ドライバーが非同期の接続操作への呼び出しをサポートしていない場合は、 **SQLBrowseConnect**、 **SQLConnect**、または**SQLDriverConnect**は失敗します。  
  
 [SQL_ATTR_AUTOCOMMIT は、FALSE に設定されているときに 5]、アプリケーションは任意の API には、トランザクションの一貫性を確保する SQL_ERROR が返されます場合 SQLEndTran(SQL_ROLLBACK) を呼び出す必要があります。  
  
 情報セットの形式、 \* *ValuePtr*バッファーが指定した依存*属性*です。 **SQLSetConnectAttr**で 2 つの異なる形式のいずれかの属性情報を受け取ります。 null で終わる文字列または整数値。 それぞれの形式は、属性の説明に記録されます。 指す文字列の文字、 *ValuePtr*の引数**SQLSetConnectAttr**の長を持つ*StringLength*バイトです。  
  
 *StringLength*引数は、属性によって、長さが定義されている場合は、ODBC 2 で導入されたすべての属性の場合と同様、無視されます*.x*以前のバージョン。  
  
|*属性*|*ValuePtr*内容|  
|-----------------|-------------------------|  
|SQL_ATTR_ACCESS_MODE (ODBC 1.0)|SQLUINTEGER 値です。 SQL_MODE_READ_ONLY は、ドライバー、またはデータ ソース接続が発生する更新を実行する SQL ステートメントをサポートするために必要なことを示すインジケーターとして使用されます。 このモードは、ロックの戦略、トランザクション管理、または、ドライバーまたはデータ ソースに適したものを他の領域を最適化するために使用できます。 このようなステートメント、データ ソースに送信されないようにするのには、ドライバーは必要はありません。 データ ソースは読み取り専用、読み取り専用の接続中に SQL ステートメントを処理するように求められたら、ドライバーの動作では、実装定義されます。 SQL_MODE_READ_WRITE では、既定値です。|  
|SQL_ATTR_ASYNC_DBC_EVENT (ODBC 3.8)|イベント ハンドルである SQLPOINTER 値。<br /><br /> 呼び出して非同期関数の完了の通知が有効になっている**SQLSetConnectAttr** SQL_ATTR_ASYNC_STMT_EVENT 属性イベント ハンドルを指定するとします。 **注:**通知方法は、カーソル ライブラリではサポートされません。 アプリケーションでは、通知方法を有効にすると、SQLSetConnectAttr 経由でのカーソル ライブラリを有効にしようとしている場合は、エラー メッセージが表示されます。|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE (ODBC 3.8)|またはの非同期実行を無効にする SQLUINTEGER 値は、接続ハンドルで関数を選択します。 詳細については、次を参照してください。[非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)です。<br /><br /> SQL_ASYNC_DBC_ENABLE_ON = 指定した接続に関連する機能を有効にする非同期操作です。<br /><br /> SQL_ASYNC_DBC_ENABLE_OFF = 指定した接続に関連する関数の非同期操作を (既定値) の無効化します。<br /><br /> 設定 SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE は同期では常に (つまり、これは返されません SQL_STILL_EXECUTING)。<br /><br /> ステートメントの非同期操作を実行は SQL_ATTR_ASYNC_ENABLE を有効になります。|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK (ODBC 3.8)|Context 構造体を指す SQLPOINTER 値。<br /><br /> ドライバー マネージャーは、運転免許を呼び出すことができますのみ**SQLSetStmtAttr**この属性を持つ関数です。|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT (ODBC 3.8)|Context 構造体を指す SQLPOINTER 値。<br /><br /> ドライバー マネージャーは、運転免許を呼び出すことができますのみ**SQLSetStmtAttr**この属性を持つ関数です。|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 3.0)|指定した接続でステートメントを使用して関数が呼び出されたかどうかを指定する SQLULEN 値は非同期的に実行されます。<br /><br /> SQL_ASYNC_ENABLE_OFF = ステートメント操作 (既定値) を無効にする接続レベルの非同期実行のサポート。<br /><br /> SQL_ASYNC_ENABLE_ON = ステートメント操作のための接続レベルの非同期実行のサポートを有効にします。<br /><br /> この属性ができるかどうかを設定**SQLGetInfo** SQL_AM_CONNECTION または SQL_AM_STATEMENT SQL_ASYNC_MODE 情報を使用して型を返します。|  
|SQL_ATTR_AUTO_IPD (ODBC 3.0)|読み取り専用 SQLUINTEGER 値を指定するかどうかを呼び出した後、IPD の自動作成**SQLPrepare**はサポートされて。<br /><br /> SQL_TRUE を呼び出した後、IPD の自動作成を = **SQLPrepare**ドライバーでサポートされています。<br /><br /> SQL_FALSE を呼び出した後、IPD の自動作成を = **SQLPrepare**はドライバーによってサポートされていません。 準備されたステートメントをサポートしていないサーバーは、IPD を自動的に設定できません。<br /><br /> 接続属性で SQL_ATTR_AUTO_IPD SQL_TRUE が返される場合は、IPD の自動設定を有効または無効にする SQL_ATTR_ENABLE_AUTO_IPD ステートメント属性を設定できます。 SQL_ATTR_AUTO_IPD が SQL_FALSE の場合は、SQL_ATTR_ENABLE_AUTO_IPD が SQL_TRUE に設定できません。 SQL_ATTR_ENABLE_AUTO_IPD の既定値は SQL_ATTR_AUTO_IPD の値と等しいです。<br /><br /> この接続属性によって返される**SQLGetConnectAttr**設定することはできませんが、 **SQLSetConnectAttr**です。|  
|SQL_ATTR_AUTOCOMMIT (ODBC 1.0)|自動コミット、または手動コミット モードを使用するかどうかを指定する SQLUINTEGER 値です。<br /><br /> SQL_AUTOCOMMIT_OFF = ドライバー手動コミット モードを使用して、アプリケーションのコミットまたはでのトランザクションをロールバックする必要があります明示的に**SQLEndTran**です。<br /><br /> Sql_autocommit_on の状態、ドライバーは自動コミット モードを = です。 各ステートメントが実行された直後後に努めています。 これは既定値です。 手動コミット モードから自動コミット モードに変更する sql_autocommit_on の状態を SQL_ATTR_AUTOCOMMIT に設定された接続で開かれたトランザクションはコミットされます。<br /><br /> 詳細については、次を参照してください。[コミット モード](../../../odbc/reference/develop-app/commit-mode.md)です。 **重要:**一部のデータ ソースの削除アクセスの計画と閉じるたびに、接続ですべてのステートメントのカーソル ステートメントがコミットされる以外の場合は、これを返さないの各ステートメントが実行された後に、またはカーソルがある場合に発生する自動コミット モード可能性がありますクエリを終了します。 詳細についてで SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR 情報の種類を参照してください。 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)と[カーソルおよび準備されたステートメントでトランザクションの効果](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)です。 <br /><br /> バッチが自動コミット モードで実行されると、2 つのことが可能です。 バッチ全体を示す autocommitable 単位として扱うことができます、またはバッチ内の各ステートメントは autocommitable 単位として扱われます。 特定のデータ ソースは、これら両方の動作をサポートできるし、どちらか一方を選択する方法を提供することがあります。 バッチが autocommitable 単位として扱われるかどうか、またはバッチ内で個々 のステートメント autocommitable ドライバーで定義されていることをお勧めします。|  
|SQL_ATTR_CONNECTION_DEAD<br /><br /> (ODBC 3.5)|接続の状態を示す読み取り専用 SQLUINTEGER 値。 場合は SQL_CD_TRUE、接続が失われました。 場合は SQL_CD_FALSE、接続は、アクティブなままです。|  
|SQL_ATTR_CONNECTION_TIMEOUT (ODBC 3.0)|すべての要求の接続がアプリケーションに返す前に完了するまで待機する秒数に対応する SQLUINTEGER 値です。 ドライバーは SQLSTATE HYT00 を返す必要があります (タイムアウト) いつでもクエリの実行またはログインに関連付けられていない状況ではタイムアウトが発生することであること。<br /><br /> 場合*ValuePtr*は 0 (既定) に等しい、タイムアウトが存在しません。|  
|SQL_ATTR_CURRENT_CATALOG (ODBC 2.0)|データ ソースで使用するカタログの名前を示す文字列です。 たとえば、SQL Server で、カタログは、データベース、そのドライバーを送信、**使用***データベース*ステートメント、データ ソースを場所*データベース*で指定したデータベース\* *ValuePtr*です。 1 階層のドライバーでは、カタログがあります、ディレクトリ、ドライバーでは、現在のディレクトリを変更で指定したディレクトリによう **ValuePtr*です。|  
|SQL_ATTR_DBC_INFO_TOKEN (ODBC 3.8|設定するための SQLPOINTER 値戻す、DBC に接続情報トークン時に処理[SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)の (\**pRating*) パラメーターが 100 ではありません。<br /><br /> SQL_ATTR_DBC_INFO_TOKEN は、セットのみです。 使用することはできません**SQLGetConnectAttr**または**SQLGetConnectOption**この値を取得します。 ドライバー マネージャーの**SQLSetConnectAttr**アプリケーションはこの属性を設定していないので、SQL_ATTR_DBC_INFO_TOKEN は受け入れられません。<br /><br /> ドライバーは SQL_ERROR を返します SQL_ATTR_DBC_INFO_TOKEN を設定した後、プールから取得した接続が解放されます。 ドライバー マネージャー、しようと別の接続プールから取得します。 参照してください[ODBC ドライバーで接続プールの認識開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)詳細についてはします。|  
|SQL_ATTR_ENLIST_IN_DTC (ODBC 3.0)|マイクロソフト コンポーネント サービスで調整される分散トランザクションで ODBC ドライバーを使用するかどうかを指定する SQLPOINTER 値。<br /><br /> DTC OLE トランザクションを指定するオブジェクトを接続の DTC の関連付けを終了するには、SQL Server、または sql_dtc_done を指定してエクスポートするトランザクションを渡します。<br /><br /> クライアントは、MS DTC トランザクションを開始し、トランザクションを表す MS DTC トランザクション オブジェクトを作成するには、Microsoft 分散トランザクション コーディネーター (MS DTC) OLE itransactiondispenser::begintransaction メソッドを呼び出します。 その後、アプリケーションは、ODBC 接続をトランザクション オブジェクトを関連付ける SQL_ATTR_ENLIST_IN_DTC オプションと SQLSetConnectAttr を呼び出します。 関連のあるすべてのデータベース操作は、MS DTC トランザクションで保護されます。 アプリケーションでは、接続の DTC の関連付けを終了する SQL_DTC_DONE を SQLSetConnectAttr を呼び出します。 詳細については、MS DTC のドキュメントを参照してください。|  
|SQL_ATTR_LOGIN_TIMEOUT (ODBC 1.0)|ログイン要求をアプリケーションに返す前に完了するまで待機する秒数に対応する SQLUINTEGER 値です。 既定値は、ドライバーによって異なります。 場合*ValuePtr* 0 は、タイムアウトが無効になり、接続試行は無期限に待機します。<br /><br /> ドライバーがその値に置き換えられ、SQLSTATE 01S02 を返します、指定のタイムアウトを超えた場合、データ ソースの最大ログイン タイムアウト、(オプションの値が変更されました)。|  
|SQL_ATTR_METADATA_ID (ODBC 3.0)|カタログ関数の文字列引数の処理方法を決定する SQLUINTEGER 値です。<br /><br /> 場合は SQL_TRUE、カタログ関数の文字列引数は、識別子として扱われます。 大文字と小文字は大きくありません。 規格文字列の場合、ドライバーが末尾のスペースを削除し、文字列が大文字に折りたたまれません。 区切られた文字列の場合は、ドライバーは、先頭または末尾の空白を削除し、区切り記号の間は何でもは文字どおり。 これらの引数の 1 つは、null ポインターに設定されている、関数を返します SQL_ERROR と SQLSTATE HY009 (null ポインターの使い方が正しくありません)。<br /><br /> 場合は SQL_FALSE、カタログ関数の文字列引数は、識別子としては扱われません。 大文字と小文字は重要です。 含めることができますか、文字列、検索パターンもそうでない引数に応じて。<br /><br /> 既定値は、SQL_FALSE です。<br /><br /> *TableType*の引数**SQLTables**値の一覧を取得するは、この属性して影響はありません。<br /><br /> SQL_ATTR_METADATA_ID は、ステートメント レベルで設定することもできます。 (これは、ステートメント属性になっている唯一の接続属性です)。<br /><br /> 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)です。|  
|SQL_ATTR_ODBC_CURSORS (ODBC 2.0)|ドライバー マネージャーが、ODBC カーソル ライブラリを使用する方法を指定する SQLULEN 値:<br /><br /> SQL_CUR_USE_IF_NEEDED が必要な場合にのみ、ドライバー マネージャーは、使用して、ODBC カーソル ライブラリを = です。 ドライバーの SQL_FETCH_PRIOR オプションをサポートする場合は**SQLFetchScroll**、ドライバー マネージャーは、ドライバーのスクロール機能を使用します。 それ以外の場合、ODBC カーソル ライブラリを使用します。<br /><br /> SQL_CUR_USE_ODBC ドライバー マネージャーは、使用して、ODBC カーソル ライブラリを = です。<br /><br /> Sql_cur_use_driver を設定したドライバーのスクロール機能のドライバー マネージャーは、使用を = です。 これが既定の設定です。<br /><br /> ODBC カーソル ライブラリの詳細については、次を参照してください。[付録 f: ODBC カーソル ライブラリ](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md)です。 **警告:**カーソル ライブラリは、Windows の将来のバージョンで削除される予定です。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。|  
|SQL_ATTR_PACKET_SIZE (ODBC 2.0)|ネットワーク パケット サイズをバイト単位で示す SQLUINTEGER 値です。 **注:**多くのデータ ソースは、このオプションをサポートしてまたはのみできます戻り値が未設定ネットワーク パケット サイズ。 <br /><br /> ドライバーがその値に置き換えられ、SQLSTATE 01S02 を返します、指定したサイズ、パケットの最大サイズを超えているまたは最小パケットのサイズよりも小さい、(オプションの値が変更されました)。<br /><br /> アプリケーションは、接続は既に行われた後に、パケット サイズを設定、ドライバーは SQLSTATE HY011 を返します (属性はここで設定することはできません)。|  
|SQL_ATTR_QUIET_MODE (ODBC 2.0)|ウィンドウ ハンドル (HWND))。<br /><br /> ウィンドウ ハンドルが null ポインターの場合、ドライバーはすべてのダイアログ ボックスが表示されません。<br /><br /> ウィンドウ ハンドルが null ポインターでない場合は、アプリケーションの親ウィンドウ ハンドルになります。 これは既定値です。 ドライバーでは、このハンドルを使用して、ダイアログ ボックスを表示します。 **注:** SQL_ATTR_QUIET_MODE 接続属性は、によって表示されるダイアログ ボックスには適用されません**SQLDriverConnect**です。|  
|SQL_ATTR_TRACE (ODBC 1.0)|ドライバー マネージャーは、トレースを実行するかどうかを示す SQLUINTEGER 値:<br /><br /> SQL_OPT_TRACE_OFF off (既定) のトレースを =<br /><br /> SQL_OPT_TRACE_ON でトレースを =<br /><br /> トレースが on の場合、ドライバー マネージャーは、トレース ファイルに各 ODBC 関数呼び出しを書き込みます。 **注:**トレースが on の場合、ドライバー マネージャーが SQLSTATE IM013 を返すことができます (ファイルのエラーをトレース) 任意の関数から。 <br /><br /> アプリケーションは、SQL_ATTR_TRACEFILE オプションを使用してトレース ファイルを指定します。 ファイルが既に存在する場合、ドライバー マネージャーは、ファイルを追加します。 それ以外の場合、ファイルを作成します。 トレースがオン、トレース ファイルが指定されていない場合は、ドライバー マネージャーは SQL ファイルに書き込みます。ルート ディレクトリにログインします。<br /><br /> アプリケーションは、変数を設定できます**ODBCSharedTraceFlag**を動的にトレースを有効にします。 現在実行されているすべての ODBC アプリケーションは、トレースを有効にし。 場合は、アプリケーションは、トレースをオフに、そのアプリケーションでのみオフにされています。<br /><br /> 場合、**トレース**アプリケーションを呼び出すときは、システム情報のキーワードを 1 に設定**SQLAllocHandle**で、 *HandleType* SQL_HANDLE_ENV のすべてのトレースが有効処理します。 呼び出したアプリケーションに対してのみ有効になっている**SQLAllocHandle**です。<br /><br /> 呼び出す**SQLSetConnectAttr**で、*属性*SQL_ATTR_TRACE のいる必要はありません、 *ConnectionHandle*引数が有効である場合は SQL_ERROR は返されません*ConnectionHandle*は NULL です。 この属性は、すべての接続に適用されます。|  
|SQL_ATTR_TRACEFILE (ODBC 1.0)|トレース ファイルの名前を表す null で終わる文字の文字列。<br /><br /> SQL_ATTR_TRACEFILE 属性の既定値が指定されています、 **TraceFile**システム情報のキーワードです。 詳細については、次を参照してください。 [ODBC サブキー](../../../odbc/reference/install/odbc-subkey.md)です。<br /><br /> 呼び出す**SQLSetConnectAttr**で、*属性*SQL_ATTR TRACEFILE は必要ありません、 *ConnectionHandle*引数に有効な場合 SQL_ERROR は返されません*ConnectionHandle*が無効です。 この属性は、すべての接続に適用されます。|  
|SQL_ATTR_TRANSLATE_LIB (ODBC 1.0)|関数を含むライブラリの名前を表す null で終わる文字列**SQLDriverToDataSource**と**SQLDataSourceToDriver**タスクを実行するように、ドライバーにアクセスします。文字セットを変換します。 このオプションがあります、ドライバーは、データ ソースに接続されているかどうかにのみ指定します。 この属性の設定は、接続間で保持されます。 データの翻訳の詳細については、次を参照してください。[翻訳 Dll](../../../odbc/reference/develop-app/translation-dlls.md)と[DLL 関数の参照を翻訳](../../../odbc/reference/syntax/translation-dll-api-reference.md)です。|  
|SQL_ATTR_TRANSLATE_OPTION (ODBC 1.0)|トランスレーター DLL に渡される 32 ビット フラグ値です。 この属性を指定できます、ドライバーは、データ ソースに接続されているかどうかにのみ指定します。 データを変換する方法については、次を参照してください。[翻訳 Dll](../../../odbc/reference/develop-app/translation-dlls.md)です。|  
|SQL_ATTR_TXN_ISOLATION (ODBC 1.0)|現在の接続のトランザクション分離レベルを設定する 32 ビット ビットマスク。 アプリケーションを呼び出す必要があります**SQLEndTran**をコミットまたは接続には、呼び出す前にすべての開いているトランザクションはロールバック**SQLSetConnectAttr**このオプションを使用します。<br /><br /> 有効値、 *ValuePtr*呼び出すことで決定できます**SQLGetInfo**で*情報の種類*SQL_TXN_ISOLATION_OPTIONS に等しい。<br /><br /> トランザクション分離レベルについてで SQL_DEFAULT_TXN_ISOLATION 情報の種類の説明を参照してください。 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)と[トランザクション分離レベル](../../../odbc/reference/develop-app/transaction-isolation-levels.md)です。|  
  
 [1] これらの関数は、記述子が、実装の記述子アプリケーション記述子ではない場合にのみ、非同期的に呼び出すことができます。  
  
## <a name="code-example"></a>コード例  
 参照してください[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|接続属性の設定値を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

