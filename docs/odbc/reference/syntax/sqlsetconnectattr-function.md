---
title: 関数を接続する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8424462ddde4f99196e26d633fddfa5bb2ed6ee9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301938"
---
# <a name="sqlsetconnectattr-function"></a>SQLSetConnectAttr 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **接続**の側面を制御する属性を設定します。  
  
> [!NOTE]
>  ODBC 3 *.x*アプリケーションが ODBC 2 *.x*ドライバーを使用して動作している場合にドライバー マネージャーがこの関数をマップする方法の詳細については、「[アプリケーションの下位互換性を確保するための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLSetConnectAttr(  
     SQLHDBC       ConnectionHandle,  
     SQLINTEGER    Attribute,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    StringLength);  
```  
  
## <a name="arguments"></a>引数  
 *接続ハンドル*  
 [入力] 接続ハンドル。  
  
 *属性*  
 [入力]「コメント」にリストされている、設定する属性。  
  
 *ValuePtr*  
 [入力]*属性*に関連付ける値へのポインター。 *属性*の値に応じて*ValuePtr*は符号なし整数値になるか、NULL で終わる文字列を指します。 *Attribute*引数の整数型は固定長でない場合がありますので、詳細についてはコメントセクションを参照してください。  
  
 *文字列の長さ*  
 [入力]*属性*が ODBC で定義された属性で *、ValuePtr*が文字列またはバイナリ バッファを指している場合、この引数は **ValuePtr*の長さになります。 文字列データの場合、この引数には文字列のバイト数を含める必要があります。  
  
 *属性*が ODBC で定義された属性で *、ValuePtr*が整数の場合、*文字列長*は無視されます。  
  
 *属性*がドライバー定義の属性である場合、アプリケーションは*StringLength*引数を設定してドライバー マネージャーに属性の性質を示します。 *文字列長*には、次の値を指定できます。  
  
-   *ValuePtr*が文字列へのポインタである場合、*文字列*または文字列の長さSQL_NTS。  
  
-   *ValuePtr*がバイナリ バッファへのポインタである場合、アプリケーションは SQL_LEN_BINARY_ATTR(*長さ*) マクロの結果を*StringLength*に格納します。 この場合は、負の値が*文字列長に*設定されます。  
  
-   *ValuePtr*が文字列またはバイナリ文字列以外の値へのポインターである場合 *、StringLength*には値がSQL_IS_POINTER。  
  
-   *ValuePtr*に固定長の値が含まれている場合 *、StringLength*はSQL_IS_INTEGERまたはSQL_IS_UINTEGERのいずれかです。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、またはSQL_STILL_EXECUTING。  
  
## <a name="diagnostics"></a>診断  
 **SQLSetConnectAttr**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_DBCの*ハンドル型*と*接続ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLSetConnectAttr**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれの値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
 ドライバーは、オプションを設定した結果に関する情報を提供するSQL_SUCCESS_WITH_INFOを返すことができます。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S02|オプション値が変更されました|ドライバーは *、ValuePtr*で指定された値をサポートしておらず、同様の値を置き換えました。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08002|使用中の接続名|*Attribute*引数がSQL_ATTR_ODBC_CURSORSされ、ドライバは既にデータ ソースに接続されています。|  
|08003|接続が開かない|(DM) 開いている接続を必要とする*属性*値が指定されましたが、*接続ハンドル*が接続状態ではありませんでした。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*Attribute*引数がSQL_ATTR_CURRENT_CATALOGされ、結果セットが保留されています。|  
|25000|ローカル トランザクション中に不正な操作を実行する|接続属性を設定して、分散トランザクション接続 (DTC) に参加しようとしているときに、ローカル トランザクションに接続SQL_ATTR_ENLIST_IN_DTC。<br /><br /> 接続は既に DTC に参加しています。<br /><br /> 接続が分散トランザクション接続に参加し、ローカル トランザクションがSQL_AUTOCOMMIT_OFF に設定SQL_ATTR_AUTOCOMMIT開始されました。|  
|3D000|無効なカタログ名です|*Attribute*引数がSQL_CURRENT_CATALOGされ、指定されたカタログ名が無効です。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|非同期処理が*有効*にされました。 関数**が**呼び出され、実行が完了する前に[、SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)が呼び出された後、*接続ハンドル*で再び**呼**び出されました。 *ConnectionHandle*<br /><br /> または **、SQLSetConnectAttr**関数が呼び出され、実行が完了する前に、マルチスレッド アプリケーションの別のスレッドから*接続ハンドル*に対して**SQLCancelHandle**が呼び出されました。|  
|HY009|無効な null ポインターの使用|*Attribute*引数は、文字列値を必要とする接続属性を識別し *、ValuePtr*引数は null ポインターです。|  
|HY010|関数シーケンス エラー|(DM) 非同期に実行される関数は *、接続ハンドル*に関連付けられた*ステートメント ハンドル*に対して呼び出され **、SQLSetConnectAttr**が呼び出されたときにまだ実行されていました。<br /><br /> (DM) 非同期実行関数 (この関数ではない) は *、ConnectionHandle*に対して呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM) 接続*ハンドル*に関連付けられているステートメント ハンドルの 1 つに対して **、SQLExecute** **、SQLExecDirect**、または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) **SQL 実行****、SQLExecDirect、SQLBulkOperations**、または**SQLSetPos**が *、接続ハンドル*に関連付けられた*ステートメント ハンドル*に対して呼び出され、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM) **SQLBrowseConnect**が*接続ハンドル*に対して呼び出され、SQL_NEED_DATA返されました。 この関数は **、SQLBrowseConnect**がSQL_SUCCESS_WITH_INFOまたはSQL_SUCCESSを返す前に呼び出されました。|  
|HY011|属性を今設定できません|*Attribute*引数がSQL_ATTR_TXN_ISOLATIONされ、トランザクションがオープンされました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY024|属性値が無効です|指定された*属性*値を指定すると *、ValuePtr*に無効な値が指定されました。 (ドライバー マネージャーは、接続とステートメント属性の場合にのみ、SQL_ATTR_ACCESS_MODEやSQL_ATTR_ASYNC_ENABLEなどの値の個別のセットを受け入れる場合にのみ、この SQLSTATE を返します。 その他の接続属性およびステートメント属性については、ドライバーは*ValuePtr*で指定された値を確認する必要があります。<br /><br /> *Attribute*引数がSQL_ATTR_TRACEFILEまたはSQL_ATTR_TRANSLATE_LIBされ *、ValuePtr*が空の文字列でした。|  
|HY090|無効な文字列またはバッファ長|*(DM) \*ValuePtr*は文字列であり *、StringLength*引数は 0 未満でしたが、SQL_NTSされませんでした。|  
|HY092|属性/オプション識別子が無効です|(DM) 引数*属性*に指定された値は、ドライバーでサポートされている ODBC のバージョンに対して無効です。<br /><br /> (DM) 引数*属性*に指定された値が読み取り専用属性です。|  
|HY114|ドライバは接続レベルの非同期関数の実行をサポートしていません|(DM) アプリケーションは、非同期接続操作をサポートしていないドライバーのSQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLEで非同期関数の実行を有効にしようとしました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|HY121|カーソル ライブラリとドライバー対応プールを同時に有効にすることはできません。|詳細については、「[ドライバ対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)」を参照してください。|  
|ハイク00|オプション機能が実装されていません|引数*Attribute*に指定された値は、ドライバでサポートされている ODBC のバージョンに対する有効な ODBC 接続またはステートメント属性でしたが、ドライバではサポートされていませんでした。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) に関連付けられているドライバー、 *ConnectionHandle*関数をサポートしていません。|  
|IM009|変換 DLL を読み込めません|ドライバは、接続に指定された変換 DLL を読み込めませんでした。 このエラーは *、Attribute*がSQL_ATTR_TRANSLATE_LIBされている場合にのみ返されます。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
|S1118|ドライバーは、非同期通知をサポートしていません。|SQL_ATTR_ASYNC_DBC_EVENT (接続が行われた後) が設定されましたが、非同期通知はドライバーによってサポートされていません。|  
  
 *属性*がステートメント属性である場合 **、SQLSetConnectAttr**は**SQLSetStmtAttr**によって返される任意の SQLSTATE を返すことができます。  
  
## <a name="comments"></a>説明  
 接続属性の一般情報については、[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)を参照してください。  
  
 現在定義されている属性と、属性が導入された ODBC のバージョンについては、このセクションの後半の表に示します。異なるデータ ソースを利用するために、より多くの属性が定義されると予想されます。 属性の範囲は ODBC によって予約されています。ドライバー開発者は、Open Group から独自のドライバー固有の使用の値を予約する必要があります。  
  
> [!NOTE]
>  **SQLSetConnectAttr**を呼び出して、接続レベルでステートメント属性を設定する機能は、ODBC 3 *.x*で非推奨になりました。 ODBC 3 *.x*アプリケーションでは、接続レベルでステートメント属性を設定しないでください。 ODBC 3 *.x*ステートメント属性は、接続属性とステートメント属性の両方であるSQL_ATTR_METADATA_ID属性とSQL_ATTR_ASYNC_ENABLE属性を除き、接続レベルで設定することはできません。  
> 
>  ODBC 3 *.x*ドライバは、ODBC 2 *.x*ステートメント オプションを接続レベルで設定する ODBC 2 *.x*アプリケーションで動作する場合にのみ、この機能をサポートする必要があります。 詳細については、「付録 G: 下位互換性のためのドライバガイドライン」の[SQLSetConnect オプション マッピング](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)を参照してください。  
  
 アプリケーションは、接続が割り当てられた時点から解放されるまでの任意の時点で**SQLSetConnectAttr**を呼び出すことができます。 接続に対してアプリケーションによって正常に設定されたすべての接続属性とステートメント属性は、接続で**SQLFreeHandle**が呼び出されるまで保持されます。 たとえば、アプリケーションがデータ ソースに接続する前に**SQLSetConnectAttr**を呼び出した場合、アプリケーションがデータ ソースに接続したときに**SQLSetConnectAttr**がドライバーで失敗した場合でも、この属性は保持されます。アプリケーションがドライバー固有の属性を設定した場合、アプリケーションが接続時に別のドライバーに接続しても、その属性は保持されます。  
  
 接続属性の中には、接続が確立される前にしか設定できないものがあります。他の接続は、接続が確立された後にのみ設定できます。 次の表は、接続が確立される前または後に設定する必要がある接続属性を示しています。 *どちらかは*、接続の前または後に属性を設定できることを示します。  
  
|属性|接続前または接続後に設定しますか?|  
|---------------|-------------------------------------|  
|SQL_ATTR_ACCESS_MODE|どちらか[1]|  
|SQL_ATTR_ASYNC_DBC_EVENT|接続前/接続後|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE|どちらか[4]|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK|接続前/接続後|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT|接続前/接続後|  
|SQL_ATTR_ASYNC_ENABLE|どちらか[2]|  
|SQL_ATTR_AUTO_IPD|接続前/接続後|  
|SQL_ATTR_AUTOCOMMIT|どちらか[5]|  
|SQL_ATTR_CONNECTION_DEAD|After|  
|SQL_ATTR_CONNECTION_TIMEOUT|接続前/接続後|  
|SQL_ATTR_CURRENT_CATALOG|どちらか[1]|  
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
|SQL_ATTR_TXN_ISOLATION|どちらか[3]|  
  
 [1] SQL_ATTR_ACCESS_MODEとSQL_ATTR_CURRENT_CATALOGは、ドライバに応じて、接続前または接続後に設定できます。 ただし、接続後にこれらの変更をサポートしていないドライバもあるため、相互運用可能なアプリケーションは接続前に設定します。  
  
 [2] アクティブなステートメントが存在する前に、SQL_ATTR_ASYNC_ENABLEを設定する必要があります。  
  
 [3] SQL_ATTR_TXN_ISOLATIONは、接続上に開いているトランザクションがない場合にのみ設定できます。 一部の接続属性は、データ ソースが\**ValuePtr*で指定された値をサポートしていない場合に、同様の値の置換をサポートします。 このような場合、ドライバーは、SQL_SUCCESS_WITH_INFOと SQLSTATE 01S02 (オプション値が変更されました) を返します。 たとえば、*属性*がSQL_ATTR_PACKET_SIZEされ\**、ValuePtr*が最大パケット サイズを超えた場合、ドライバーは最大サイズを置き換えます。 置換値を決定するために、アプリケーションは**SQLGetConnectAttr**を呼び出します。  
  
 接続が開く前にSQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLEが設定されている場合、ドライバ マネージャは **、ドライバが SQLBrowseConnect** **、SQLConnect、** または**SQLDriverConnect**の呼び出し中に読み込まれるときにドライバの属性を設定します。 **SQLBrowseConnect** **、SQLConnect**、または**SQLDriverConnect**への呼び出しの前に、ドライバー マネージャーは接続するドライバーを認識せず、ドライバーが非同期接続操作をサポートしているかどうかを知りません。 したがって、ドライバー マネージャーは常にSQL_SUCCESS返します。 ただし、ドライバーが非同期接続操作をサポートしていない場合は **、SQLBrowseConnect** **、SQLConnect**、または**SQL ドライバ接続**への呼び出しが失敗します。  
  
 SQL_ATTR_AUTOCOMMITが FALSE に設定されている場合、アプリケーションは、トランザクションの一貫性を確保するために、SQL_ERRORを返す API がある場合に SQLEndTran(SQL_ROLLBACK) を呼び出す必要があります。  
  
 \* *ValuePtr*バッファに設定される情報の形式は、指定された*属性*によって異なります。 **SQLSetConnectAttr**は、2 つの異なる形式の属性情報を受け取ります: NULL で終わる文字ストリングまたは整数値。 それぞれの形式は、属性の説明に記載されています。 **引数** *ValuePtr*が指す文字列は、*文字列長*のバイト長を持ちます。  
  
 長さが属性によって定義されている場合、ODBC 2 *.x*以前で導入されたすべての属性の場合と同様に *、StringLength*引数は無視されます。  
  
|*属性*|*値の内容*|  
|-----------------|-------------------------|  
|SQL_ATTR_ACCESS_MODE (ODBC 1.0)|整数の値。 SQL_MODE_READ_ONLYは、更新が発生する SQL ステートメントをサポートするために接続が必要ないことを示すインジケーターとして、ドライバーまたはデータ ソースによって使用されます。 このモードを使用すると、ドライバーまたはデータ ソースに適したロック戦略、トランザクション管理、またはその他の領域を最適化できます。 ドライバーは、このようなステートメントがデータ ソースに送信されるのを防ぐために必要ありません。 読み取り専用接続中に読み取り専用ではない SQL ステートメントを処理するように求められた場合のドライバーとデータ ソースの動作は、実装定義されます。 SQL_MODE_READ_WRITEがデフォルトです。|  
|SQL_ATTR_ASYNC_DBC_EVENT (ODBC 3.8)|イベント ハンドルである SQLPOINTER 値。<br /><br /> 非同期関数の完了通知は、SQL_ATTR_ASYNC_STMT_EVENT属性を指定して**SQLSetConnectAttr**を呼び出し、イベント ハンドルを指定することで有効になります。 **注:** 通知方法は、カーソル ライブラリではサポートされていません。 アプリケーションは、通知メソッドが有効になっているときに、SQLSetConnectAttr を使用してカーソル ライブラリを有効にしようとすると、エラー メッセージを受け取ります。|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE (ODBC 3.8)|接続ハンドルで選択した関数の非同期実行を有効または無効にする SQLUINTEGER 値。 詳細については、「[非同期実行 (ポーリング メソッド)」](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)を参照してください。<br /><br /> SQL_ASYNC_DBC_ENABLE_ON = 指定された接続関連関数の非同期操作を有効にします。<br /><br /> SQL_ASYNC_DBC_ENABLE_OFF = (デフォルト) 指定された接続関連関数の非同期操作を無効にします。<br /><br /> SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE設定は常に同期的です (つまり、SQL_STILL_EXECUTING返すことはありません)。<br /><br /> SQL_ATTR_ASYNC_ENABLEを使用して、ステートメント操作の非同期実行が有効になります。|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK (ODBC 3.8)|コンテキスト構造を指す SQLPOINTER 値。<br /><br /> ドライバー マネージャーのみがこの属性を使用してドライバーの**SQLSetStmtAttr**関数を呼び出すことができます。|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT (ODBC 3.8)|コンテキスト構造を指す SQLPOINTER 値。<br /><br /> ドライバー マネージャーのみがこの属性を使用してドライバーの**SQLSetStmtAttr**関数を呼び出すことができます。|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 3.0)|指定された接続のステートメントで呼び出された関数を非同期的に実行するかどうかを指定する SQLULEN 値。<br /><br /> SQL_ASYNC_ENABLE_OFF = ステートメント操作の接続レベルの非同期実行サポートを無効にします (既定値)。<br /><br /> SQL_ASYNC_ENABLE_ON = ステートメント操作の接続レベルの非同期実行サポートを有効にします。<br /><br /> この属性は、SQL_ASYNC_MODE情報型の**SQLGetInfo**がSQL_AM_CONNECTIONを返すか、SQL_AM_STATEMENTを返すかを設定できます。|  
|SQL_ATTR_AUTO_IPD (ODBC 3.0)|**SQLPrepare**の呼び出し後に IPD の自動作成がサポートされるかどうかを指定する読み取り専用の SQLUINTEGER 値。<br /><br /> SQL_TRUE = **SQLPrepare**の呼び出し後の IPD の自動作成は、ドライバーによってサポートされます。<br /><br /> SQL_FALSE = **SQLPrepare**の呼び出し後の IPD の自動作成は、ドライバーでサポートされていません。 準備済みステートメントをサポートしないサーバーは、IPD を自動的に設定することはできません。<br /><br /> SQL_ATTR_AUTO_IPD接続属性に対してSQL_TRUEが返される場合、ステートメント属性SQL_ATTR_ENABLE_AUTO_IPD IPD の自動作成をオンまたはオフにするように設定できます。 SQL_ATTR_AUTO_IPDがSQL_FALSE場合、SQL_ATTR_ENABLE_AUTO_IPDをSQL_TRUEに設定することはできません。 SQL_ATTR_ENABLE_AUTO_IPDのデフォルト値は、SQL_ATTR_AUTO_IPDの値と等しくなります。<br /><br /> この接続属性は **、SQLGetConnectAttr**によって返すことができますが **、SQLSetConnectAttr**によって設定することはできません。|  
|SQL_ATTR_AUTOCOMMIT (ODBC 1.0)|自動コミットモードと手動コミット モードのどちらを使用するかを指定する SQLUINTEGER 値。<br /><br /> SQL_AUTOCOMMIT_OFF = ドライバーは手動コミット モードを使用し、アプリケーションは**SQLEndTran**を使用してトランザクションを明示的にコミットまたはロールバックする必要があります。<br /><br /> SQL_AUTOCOMMIT_ON = ドライバーは自動コミット モードを使用します。 各ステートメントは、実行後すぐにコミットされます。 これは既定値です。 接続上のオープン・トランザクションは、SQL_ATTR_AUTOCOMMITが手動コミット・モードから自動コミット・モードに変更SQL_AUTOCOMMIT_ONに設定されている場合にコミットされます。<br /><br /> 詳細については、「コミット[モード](../../../odbc/reference/develop-app/commit-mode.md)」を参照してください。 **重要:** 一部のデータ・ソースは、アクセス・プランを削除し、ステートメントがコミットされるたびに、接続上のすべてのステートメントのカーソルをクローズします。autocommit モードでは、各非クエリ ステートメントが実行された後、またはクエリのカーソルが閉じられたときに、この問題が発生することがあります。 詳細については、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)のSQL_CURSOR_COMMIT_BEHAVIORおよびSQL_CURSOR_ROLLBACK_BEHAVIOR情報の種類、および[カーソルおよび準備されたステートメントに対するトランザクションの影響](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)を参照してください。 <br /><br /> バッチが自動コミット モードで実行される場合、2 つの処理が可能です。 バッチ全体を自動コミット可能ユニットとして扱うか、またはバッチ内の各ステートメントを自動コミット可能単位として扱うことができます。 特定のデータ ソースは、これらの動作の両方をサポートし、どちらか一方を選択する方法を提供します。 これは、バッチが自動コミット可能なユニットとして扱われるかどうか、またはバッチ内の個々のステートメントが自動コミット可能かどうか、ドライバー定義です。|  
|SQL_ATTR_CONNECTION_DEAD<br /><br /> (ODBC 3.5)|接続の状態を示す読み取り専用の SQLUINTEGER 値。 SQL_CD_TRUE場合、接続は失われています。 SQL_CD_FALSE場合、接続はアクティブです。|  
|SQL_ATTR_CONNECTION_TIMEOUT (ODBC 3.0)|接続の要求が完了するまで待機する秒数に対応する SQLUINTEGER 値が、アプリケーションに戻ります。 ドライバーは、クエリの実行またはログインに関連付けられていない状況でタイムアウトが発生する可能性がある場合は、いつでも SQLSTATE HYT00 (タイムアウトの期限が切れた) を返す必要があります。<br /><br /> *ValuePtr*が 0 (デフォルト) の場合、タイムアウトはありません。|  
|SQL_ATTR_CURRENT_CATALOG (ODBC 2.0)|データ ソースで使用されるカタログの名前を含む文字列。 たとえば、SQL Server ではカタログがデータベースであるため、ドライバは USE**USE**_データベース_ステートメントをデータ ソースに送信します *。* \* *ValuePtr* 単層ドライバーの場合、カタログはディレクトリである可能性があるため、ドライバーは現在のディレクトリを **ValuePtr*で指定されたディレクトリに変更します。|  
|SQL_ATTR_DBC_INFO_TOKEN (ODBC 3.8|SQLRateConnection の (\**pRating*) パラメーターが 100 に等しくない場合に、接続情報トークンを DBC ハンドルに戻すために使用される[SQLPOINTER](../../../odbc/reference/syntax/sqlrateconnection-function.md)値。<br /><br /> SQL_ATTR_DBC_INFO_TOKENは設定専用です。 この値を取得するのに**は、SQLGetConnectAttr**または**SQLGetConnect オプション**を使用することはできません。 アプリケーションはこの属性を設定してはならないので、ドライバー マネージャーの**SQLSetConnectAttr**はSQL_ATTR_DBC_INFO_TOKENを受け入れません。<br /><br /> SQL_ATTR_DBC_INFO_TOKEN設定した後にドライバがSQL_ERRORを返すと、プールから取得した接続が解放されます。 ドライバー マネージャーは、プールから別の接続を取得しようとします。 詳細については[、ODBC ドライバーでの接続プール対応の開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)を参照してください。|  
|SQL_ATTR_ENLIST_IN_DTC (ODBC 3.0)|MICROSOFT コンポーネント サービスによって調整された分散トランザクションで ODBC ドライバーを使用するかどうかを指定する SQLPOINTER 値。<br /><br /> SQL Server にエクスポートするトランザクションを指定する DTC OLE トランザクション オブジェクトを渡すか、接続の DTC 関連付けを終了SQL_DTC_DONE。<br /><br /> クライアントは、MICROSOFT 分散トランザクション コーディネーター (MS DTC) OLE ITransactionDispenser::BeginTransaction メソッドを呼び出して、MS DTC トランザクションを開始し、トランザクションを表す MS DTC トランザクション オブジェクトを作成します。 アプリケーションは、ODBC 接続にトランザクション オブジェクトを関連付けるSQL_ATTR_ENLIST_IN_DTC オプションを使用して SQLSetConnectAttr を呼び出します。 関連のあるすべてのデータベース操作は、MS DTC トランザクションで保護されます。 アプリケーションでは、SQL_DTC_DONE 値を指定して SQLSetConnectAttr を呼び出し、接続と DTC の関連付けを完了します。 詳細については、MS DTC のドキュメントを参照してください。|  
|SQL_ATTR_LOGIN_TIMEOUT (ODBC 1.0)|ログイン要求が完了するまで待機する秒数に対応する SQLUINTEGER 値が、アプリケーションに戻ります。 デフォルトはドライバ依存です。 *ValuePtr*が 0 の場合、タイムアウトは無効になり、接続の試行は無期限に待機します。<br /><br /> 指定されたタイムアウトがデータ ソースの最大ログイン タイムアウトを超えた場合、ドライバーはその値を置き換え、SQLSTATE 01S02 (オプション値が変更されました) を返します。|  
|SQL_ATTR_METADATA_ID (ODBC 3.0)|カタログ関数の文字列引数の処理方法を決定する SQLUINTEGER 値。<br /><br /> SQL_TRUE場合、カタログ関数の文字列引数は識別子として扱われます。 ケースは重要ではありません。 区切り文字を除く文字列の場合、ドライバーは末尾のスペースを削除し、文字列は大文字に折り返されます。 区切り文字列の場合、ドライバーは先頭または末尾の空白を削除し、区切り文字の間にあるものを文字通り受け取ります。 これらの引数の 1 つが null ポインターに設定されている場合、関数は SQL_ERROR および SQLSTATE HY009 (ヌル・ポインターの無効な使用) を戻します。<br /><br /> SQL_FALSE場合、カタログ関数の文字列引数は識別子として扱われないです。 ケースは重要です。 引数に応じて、文字列検索パターンを含めるかどうかが考えます。<br /><br /> 既定値は SQL_FALSE です。<br /><br /> 値の一覧を受け取る**SQLTables**の*TableType*引数は、この属性の影響を受けません。<br /><br /> SQL_ATTR_METADATA_IDは、ステートメント・レベルでも設定できます。 (これは、ステートメント属性でもある唯一の接続属性です。<br /><br /> 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。|  
|SQL_ATTR_ODBC_CURSORS (ODBC 2.0)|ドライバー・マネージャーが ODBC カーソル・ライブラリーをどのように使用するかを指定する SQLULEN 値。<br /><br /> SQL_CUR_USE_IF_NEEDED = ドライバー マネージャーは、必要な場合にのみ ODBC カーソル ライブラリを使用します。 ドライバーは **、SQLFetchScroll**でSQL_FETCH_PRIOR オプションをサポートしている場合、ドライバー マネージャーは、ドライバーのスクロール機能を使用します。 それ以外の場合は、ODBC カーソル ライブラリを使用します。<br /><br /> SQL_CUR_USE_ODBC = ドライバー マネージャーは、ODBC カーソル ライブラリを使用します。<br /><br /> SQL_CUR_USE_DRIVER = ドライバー マネージャーは、ドライバーのスクロール機能を使用します。 これが既定の設定です。<br /><br /> ODBC カーソル ライブラリの詳細については、「[付録 F: ODBC カーソル ライブラリ](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md)」を参照してください。 **警告:** カーソル ライブラリは、将来のバージョンの Windows で削除されます。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。|  
|SQL_ATTR_PACKET_SIZE (ODBC 2.0)|ネットワーク パケット サイズをバイト単位で指定する SQLUINTEGER 値。 **注:** 多くのデータ ソースは、このオプションをサポートしていないか、ネットワーク パケット サイズを設定できますが、戻り値のみを返すことができます。 <br /><br /> 指定されたサイズが最大パケット サイズを超えているか、または最小パケット サイズよりも小さい場合、ドライバーはその値を置き換えて SQLSTATE 01S02 (オプション値が変更) を返します。<br /><br /> 接続が確立された後にアプリケーションがパケットサイズを設定した場合、ドライバは SQLSTATE HY011 を返します(属性を設定することはできません)。|  
|SQL_ATTR_QUIET_MODE (ODBC 2.0)|ウィンドウ ハンドル (HWND)<br /><br /> ウィンドウ ハンドルが null ポインターの場合、ドライバーはダイアログ ボックスを表示しません。<br /><br /> ウィンドウ ハンドルが null ポインターでない場合は、アプリケーションの親ウィンドウ ハンドルにする必要があります。 これは既定値です。 ドライバーは、ダイアログ ボックスを表示するのにこのハンドルを使用します。 **注:** SQL_ATTR_QUIET_MODE接続属性は **、 SQLDriverConnect**によって表示されるダイアログ ボックスには適用されません。|  
|SQL_ATTR_TRACE (ODBC 1.0)|ドライバー マネージャーにトレースを実行するかどうかを示す SQLUINTEGER 値:<br /><br /> SQL_OPT_TRACE_OFF = トレースオフ (デフォルト)<br /><br /> SQL_OPT_TRACE_ON = トレースオン<br /><br /> トレースがオンの場合、ドライバー マネージャーは、各 ODBC 関数呼び出しをトレース ファイルに書き込みます。 **注:** トレースがオンの場合、ドライバー マネージャーは、任意の関数から SQLSTATE IM013 (トレース ファイル エラー) を返すことができます。 <br /><br /> アプリケーションは、SQL_ATTR_TRACEFILE オプションを使用してトレース ファイルを指定します。 ファイルが既に存在する場合、ドライバー マネージャーは、ファイルに追加します。 それ以外の場合は、ファイルが作成されます。 トレースがオンで、トレース ファイルが指定されていない場合、ドライバー マネージャーは、ファイル SQL に書き込みます。ルート ディレクトリに LOG を入力します。<br /><br /> アプリケーションは、動的にトレースを有効にする変数**ODBCSharedTraceFlag**を設定できます。 トレースは、現在実行されているすべての ODBC アプリケーションで有効になります。 アプリケーションでトレースがオフになった場合、そのアプリケーションに対してのみオフになります。<br /><br /> アプリケーションが SQL_HANDLE_ENV*ハンドル型*の**SQLAllocHandle**を呼び出すときにシステム情報の**Trace**キーワードが 1 に設定されている場合、トレースはすべてのハンドルに対して有効になります。 このメソッドは **、SQLAllocHandle**を呼び出したアプリケーションに対してのみ有効になります。<br /><br /> SQL_ATTR_TRACE*の属性*を指定して**SQLSetConnectAttr**を呼び出すと、*引数*が SQL_ERROR有効である必要はありません*ConnectionHandle*。 この属性はすべての接続に適用されます。|  
|SQL_ATTR_TRACEFILE (ODBC 1.0)|トレース ファイルの名前を含む NULL で終わる文字列。<br /><br /> SQL_ATTR_TRACEFILE属性のデフォルト値は、システム情報の**TraceFile**キーワードで指定されます。 詳細については、「 [ODBC サブキー](../../../odbc/reference/install/odbc-subkey.md)」を参照してください。<br /><br /> SQL_ATTR_ TRACEFILE の*属性*を指定して**SQLSetConnectAttr**を呼び出しても、*引数が*SQL_ERROR有効である*ConnectionHandle*必要はありません。 この属性はすべての接続に適用されます。|  
|SQL_ATTR_TRANSLATE_LIB (ODBC 1.0)|関数**を**含むライブラリの名前を含む null で終わる文字列を**返します。** このオプションは、ドライバがデータ ソースに接続されている場合にのみ指定できます。 この属性の設定は、接続間で保持されます。 データの変換の詳細については、「変換[DLL」および「変換](../../../odbc/reference/develop-app/translation-dlls.md) [DLL 関数リファレンス」を参照してください](../../../odbc/reference/syntax/translation-dll-api-reference.md)。|  
|SQL_ATTR_TRANSLATE_OPTION (ODBC 1.0)|変換 DLL に渡される 32 ビット フラグ値。 この属性は、ドライバーがデータ ソースに接続されている場合にのみ指定できます。 データの変換については、「[変換 DLL 」を](../../../odbc/reference/develop-app/translation-dlls.md)参照してください。|  
|SQL_ATTR_TXN_ISOLATION (ODBC 1.0)|現在の接続のトランザクション分離レベルを設定する 32 ビット ビットマスク。 アプリケーションは **、SQLSetConnectAttr**をこのオプションで呼び出す前に、接続上のすべてのオープン・トランザクションをコミットまたはロールバックするために **、SQLEndTran**を呼び出す必要があります。<br /><br /> *値の有効*な値は、SQL_TXN_ISOLATION_OPTIONSに等しい*情報の種類*を使用して**SQLGetInfo**を呼び出すことによって決定できます。<br /><br /> トランザクション分離レベルの詳細については、「 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) 」 および「[トランザクション分離レベル](../../../odbc/reference/develop-app/transaction-isolation-levels.md)」のSQL_DEFAULT_TXN_ISOLATION情報タイプの説明を参照してください。|  
  
 これらの関数は、記述子がアプリケーション記述子ではなく実装記述子である場合にのみ、非同期的に呼び出すことができます。  
  
## <a name="code-example"></a>コード例  
 [「SQLConnect」](../../../odbc/reference/syntax/sqlconnect-function.md)を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ハンドルの割り当て|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|接続属性の設定を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
