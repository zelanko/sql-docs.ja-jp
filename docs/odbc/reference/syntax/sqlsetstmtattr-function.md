---
title: 関数を設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetStmtAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetStmtAttr
helpviewer_keywords:
- SQLSetStmtAttr function [ODBC]
ms.assetid: 7abc5260-733a-48d4-9974-2d1a6a9ea5f6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dfbd2144e677d053f6154dfb3a1df1f6c25d9da5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287267"
---
# <a name="sqlsetstmtattr-function"></a>SQLSetStmtAttr 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **ステートメントに**関連する属性を設定します。  
  
> [!NOTE]
>  ODBC *3.x*アプリケーションが ODBC *2.x*ドライバーを使用して動作している場合にドライバー マネージャーがこの関数をマップする方法の詳細については、「[アプリケーションの下位互換性を確保するための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLSetStmtAttr(  
     SQLHSTMT      StatementHandle,  
     SQLINTEGER    Attribute,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    StringLength);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *属性*  
 [入力]「コメント」にリストされている設定オプション。  
  
 *ValuePtr*  
 [入力]*属性*に関連付ける値。 *属性*の値に応じて *、ValuePtr*は次のいずれかになります。  
  
-   ODBC 記述子ハンドル。  
  
-   整数の値。  
  
-   SQLULEN 値。  
  
-   次のいずれかへのポインター。  
  
    -   NULL で終わる文字列。  
  
    -   バイナリ バッファ。  
  
    -   SQLLEN、SQLULEN、または SQLUSMALLINT のタイプの値または配列。  
  
    -   ドライバー定義の値。  
  
 引数*Attribute*がドライバー固有の値である場合 *、ValuePtr*は符号付き整数である可能性があります。  
  
 *文字列の長さ*  
 [入力]*属性*が ODBC で定義された属性で *、ValuePtr*が文字列またはバイナリ バッファを指している場合、この引数は\* *ValuePtr*の長さになります。 *属性*が ODBC で定義された属性で *、ValuePtr*が整数の場合、*文字列長*は無視されます。  
  
 *属性*がドライバー定義の属性である場合、アプリケーションは*StringLength*引数を設定してドライバー マネージャーに属性の性質を示します。 *文字列長*には、次の値を指定できます。  
  
-   *ValuePtr*が文字列へのポインタである場合、*文字列*または文字列の長さSQL_NTS。  
  
-   *ValuePtr*がバイナリ バッファへのポインタである場合、アプリケーションは SQL_LEN_BINARY_ATTR(*長さ*) マクロの結果を*StringLength*に格納します。 この場合は、負の値が*文字列長に*設定されます。  
  
-   *ValuePtr*が文字列またはバイナリ文字列以外の値へのポインターである場合 *、StringLength*には値がSQL_IS_POINTER。  
  
-   *ValuePtr*に固定長の値が含まれている場合 *、StringLength*はSQL_IS_INTEGERまたはSQL_IS_UINTEGERのいずれかです。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLSetStmtAttr**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときに、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec** *を呼*び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLSetStmtAttr**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S02|オプション値が変更されました|ドライバーは*ValuePtr*で指定された値をサポートしていないか *、ValuePtr*で指定された値が無効な実装の動作条件のため、ドライバーは、同様の値を置き換えました。 (**SQLGetStmtAttr**を呼び出して、一時的に置換された値を決定できます。代替値は *、ステートメント ハンドル*に対して有効であり、カーソルが閉じられるまでは、ステートメント属性が以前の値に戻ります。 変更できるステートメント属性は次のとおりです。<br /><br /> SQL_ATTR_ROW_ARRAY_SIZESQL_ATTR_ROW_ARRAY_SIZESQL_ATTR_ROW_ARRAY_SIZEのATTR_SIMULATE_CURSORをSQL_ATTR_ROW_ARRAY_SIZEATTR_MAX_ROWSATTR_MAX_ROWSSQL_SQL_SQL_SQL_SQL_SQL_SQL_SQL_SQL_SQL_。 SQL_ ATTR_QUERY_TIMEOUT SQL_ SQL_ ATTR_MAX_LENGTH SQL_ ATTR_KEYSET_SIZE ATTR_CURSOR_TYPE SQL_ ATTR_CONCURRENCY<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*属性*がSQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_SIMULATE_CURSOR、またはSQL_ATTR_USE_BOOKMARKSされ、カーソルがオープンされました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|*Attribute*引数は、文字列属性を必要とするステートメント属性を識別し *、ValuePtr*引数は null ポインターです。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLSetStmtAttr**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 *StatementHandle、* この関数が呼び出されたときに実行されています。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY011|属性を今設定できません|*属性*はSQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_SIMULATE_CURSOR、またはSQL_ATTR_USE_BOOKMARKSであり、ステートメントが準備されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY017|自動割り当て記述子ハンドルの無効な使用|(DM)*属性*引数がSQL_ATTR_IMP_ROW_DESCまたはSQL_ATTR_IMP_PARAM_DESC。<br /><br /> (DM) *Attribute*引数がSQL_ATTR_APP_ROW_DESCまたはSQL_ATTR_APP_PARAM_DESCされ *、ValuePtr*の値は、最初に ARD または APD に割り当てられたハンドル以外の暗黙的に割り当てられた記述子ハンドルでした。|  
|HY024|属性値が無効です|指定された*属性*値を指定すると *、ValuePtr*に無効な値が指定されました。 (ドライバー マネージャーは、接続とステートメント属性の場合にのみ、SQL_ATTR_ACCESS_MODEやSQL_ATTR_ASYNC_ENABLEなどの値のセットを受け入れる場合にのみ、この SQLSTATE を返します。 その他の接続属性およびステートメント属性については、ドライバーは*ValuePtr*で指定された値を確認する必要があります。<br /><br /> *Attribute*引数がSQL_ATTR_APP_ROW_DESCまたはSQL_ATTR_APP_PARAM_DESCされ *、ValuePtr*は明示的に割り当てられた記述子ハンドルであり、*この*引数と同じ接続上にありません。|  
|HY090|無効な文字列またはバッファ長|(DM) * \*ValuePtr*は文字列であり *、StringLength*引数は 0 未満でしたが、SQL_NTSされませんでした。|  
|HY092|属性/オプション識別子が無効です|(DM) 引数*属性*に指定された値は、ドライバーでサポートされている ODBC のバージョンに対して無効です。<br /><br /> (DM) 引数*属性*に指定された値が読み取り専用属性です。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|引数*Attribute*に指定された値は、ドライバでサポートされている ODBC のバージョンに対する有効な ODBC ステートメント属性でしたが、ドライバではサポートされていませんでした。<br /><br /> *属性*引数がSQL_ATTR_ASYNC_ENABLEされ *、SQL_ASYNC_MODEの情報型*を持つ**SQLGetInfo**の呼び出しはSQL_AM_CONNECTIONを返します。<br /><br /> *Attribute*引数がSQL_ATTR_ENABLE_AUTO_IPDされ、接続属性SQL_ATTR_AUTO_IPDの値がSQL_FALSEされました。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|S1118|ドライバーは、非同期通知をサポートしていません。|SQL_ATTR_ASYNC_STMT_EVENTを設定するために**SQLSetStmtAttr**を呼び出す場合。非同期通知は、ドライバーではサポートされていません。|  
  
## <a name="comments"></a>説明  
 ステートメントのステートメント属性は **、SQLSetStmtAttr**の別の呼び出しによって変更されるか、または**SQLFreeHandle**を呼び出してステートメントが削除されるまで有効です。 SQL_CLOSE、SQL_UNBIND、またはSQL_RESET_PARAMSオプションを指定して**SQLFreeStmt**を呼び出しても、ステートメント属性はリセットされません。  
  
 一部のステートメント属性は、データ ソースが*ValuePtr*で指定された値をサポートしていない場合に、同様の値の置換をサポートします。 このような場合、ドライバーは、SQL_SUCCESS_WITH_INFOと SQLSTATE 01S02 (オプション値が変更されました) を返します。 たとえば *、Attribute*がSQL_ATTR_CONCURRENCYで *、ValuePtr*がSQL_CONCUR_ROWVER場合、データ ソースがこれをサポートしていない場合、ドライバーはSQL_CONCUR_VALUESを置き換え、SQL_SUCCESS_WITH_INFOを返します。 置換された値を決定するために、アプリケーションは**SQLGetStmtAttr を**呼び出します。  
  
 *ValuePtr*で設定される情報の形式は、指定された*属性*によって異なります。 **SQLSetStmtAttr**は、2 つの異なる形式 (文字ストリングまたは整数値) のいずれかで属性情報を受け取ります。 それぞれの形式は、属性の説明に記載されています。 この形式は **、SQLGetStmtAttr**の各属性に対して返される情報に適用されます。 **引数** *ValuePtr*が指す文字列は文字列*長を持ちます*。  
  
> [!NOTE]
>  **SQLSetConnectAttr**を呼び出して、接続レベルでステートメント属性を設定する機能は、ODBC *3.x*で非推奨になりました。 ODBC *3.x*アプリケーションは、接続レベルでステートメント属性を設定しないでください。 ODBC *3.x*ステートメント属性は、接続属性とステートメント属性の両方であるSQL_ATTR_METADATA_ID属性とSQL_ATTR_ASYNC_ENABLE属性を除き、接続レベルで設定することはできません。  
> 
> [!NOTE]
>  ODBC *3.x*ドライバは、ODBC *2.x*ステートメント オプションを接続レベルで設定する ODBC *2.x*アプリケーションで動作する場合にのみ、この機能をサポートする必要があります。 詳細については、「付録 G: 下位互換性のためのドライバガイドライン」の[「SQLSetConnectOption マッピング](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)」の「接続レベルでのステートメント オプションの設定」を参照してください。  
  
## <a name="statement-attributes-that-set-descriptor-fields"></a>記述子フィールドを設定するステートメント属性  
 多くのステートメント属性は、記述子のヘッダー フィールドに対応します。 これらの属性を設定すると、実際には記述子フィールドが設定されます。 呼び出しによってフィールドを設定する**SQLSetDescField**ではなく、SQLSetStmtAttr には、関数呼び出しに対して記述子ハンドルを取得する必要がなされないという利点があります。 **SQLSetStmtAttr**  
  
> [!CAUTION]  
>  1 つのステートメントに対して**SQLSetStmtAttr**を呼び出すと、他のステートメントに影響を与える可能性があります。 これは、ステートメントに関連付けられた APD または ARD が明示的に割り振られ、他のステートメントにも関連付けられている場合に発生します。 **SQLSetStmtAttr**は APD または ARD を変更するため、この記述子が関連付けられているすべてのステートメントに変更が適用されます。 これが必要な動作でない場合、アプリケーションは **、SQLSetStmtAttr**を再度呼び出す前に、他のステートメントからこの記述子を切り離す必要があります (SQL_ATTR_APP_ROW_DESCまたはSQL_ATTR_APP_PARAM_DESCフィールドを別の記述子ハンドルに設定するために**SQLSetStmtAttr**を呼び出すことによって)。  
  
 記述子フィールドが、対応するステートメント属性が設定された結果として設定されると、そのフィールドは *、現在、StatementHandle*引数によって識別されるステートメントに関連付けられている該当する記述子に対してのみ設定され、属性設定は将来そのステートメントに関連付けられる記述子には影響しません。 ステートメント属性でもある記述子フィールドが**SQLSetDescField**の呼び出しによって設定されると、対応するステートメント属性が設定されます。 明示的に割り当てられた記述子がステートメントから切り離されている場合、ヘッダー フィールドに対応するステートメント属性は、暗黙的に割り当てられた記述子のフィールドの値に戻ります。  
  
 ステートメントが割り振られている場合[(SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)を参照)、4 つの記述子ハンドルが自動的に割り振られ、ステートメントに関連付けられます。 明示的に割り当てられた記述子ハンドルは、記述子ハンドルを割り当てるSQL_HANDLE_DESCの*fHandleType*を使用して**SQLAllocHandle**を呼び出し、記述子ハンドルをステートメントに関連付けるために**SQLSetStmtAttr**を呼び出すことによって、ステートメントに関連付けることができます。  
  
 次の表のステートメント属性は、記述子ヘッダー フィールドに対応しています。  
  
|ステートメント属性|ヘッダー フィールド|Desc。|  
|-------------------------|------------------|-----------|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_DESC_BIND_OFFSET_PTR|APD|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_DESC_BIND_TYPE|APD|  
|SQL_ATTR_PARAM_OPERATION_PTR|SQL_DESC_ARRAY_STATUS_PTR|APD|  
|SQL_ATTR_PARAM_STATUS_PTR|SQL_DESC_ARRAY_STATUS_PTR|IPD|  
|SQL_ATTR_PARAMS_PROCESSED_PTR|SQL_DESC_ROWS_PROCESSED_PTR|IPD|  
|SQL_ATTR_PARAMSET_SIZE|SQL_DESC_ARRAY_SIZE|APD|  
|SQL_ATTR_ROW_ARRAY_SIZE|SQL_DESC_ARRAY_SIZE|Ard|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR|SQL_DESC_BIND_OFFSET_PTR|Ard|  
|SQL_ATTR_ROW_BIND_TYPE|SQL_DESC_BIND_TYPE|Ard|  
|SQL_ATTR_ROW_OPERATION_PTR|SQL_DESC_ARRAY_STATUS_PTR|Ard|  
|SQL_ATTR_ROW_STATUS_PTR|SQL_DESC_ARRAY_STATUS_PTR|Ird|  
|SQL_ATTR_ROWS_FETCHED_PTR|SQL_DESC_ROWS_PROCESSED_PTR|Ird|  
  
## <a name="statement-attributes"></a>ステートメント属性  
 現在定義されている属性と、その属性が導入された ODBC のバージョンを次の表に示します。さまざまなデータ ソースを利用するために、ドライバーによって定義される属性が増える可能性があります。 属性の範囲は ODBC によって予約されています。ドライバー開発者は、Open Group から独自のドライバー固有の使用の値を予約する必要があります。 詳細については、「[ドライバ固有のデータ型、記述子の型、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)」を参照してください。  
  
|属性|*値の内容*|  
|---------------|-------------------------|  
|SQL_ATTR_APP_PARAM_DESC (ODBC 3.0)|ステートメント ハンドルで**の SQLExecute**および**SQLExecDirect**への後続の呼び出しの APD へのハンドル。 この属性の初期値は、ステートメントが最初に割り振られたときに暗黙的に割り振られた記述子です。 この属性の値が SQL_NULL_DESC または記述子に割り当てられたハンドルに設定されている場合、ステートメント ハンドルに以前に関連付けられていた明示的に割り当てられた APD ハンドルは、そのハンドルから切り離され、ステートメント ハンドルは暗黙的に割り当てられた APD ハンドルに戻ります。<br /><br /> この属性は、別のステートメントに暗黙的に割り当てられた記述子ハンドル、または同じステートメントに暗黙的に設定された別の記述子ハンドルに設定することはできません。暗黙的に割り振られる記述子ハンドルは、複数のステートメントまたは記述子ハンドルに関連付けることはできません。|  
|SQL_ATTR_APP_ROW_DESC (ODBC 3.0)|ステートメント ハンドルの後続のフェッチの ARD へのハンドル。 この属性の初期値は、ステートメントが最初に割り振られたときに暗黙的に割り振られた記述子です。 この属性の値が SQL_NULL_DESC または記述子に割り当てられたハンドルに設定されている場合、ステートメント ハンドルに以前に関連付けられていた明示的に割り当てられた ARD ハンドルは、そのハンドルから切り離され、ステートメント ハンドルは暗黙的に割り当てられた ARD ハンドルに戻ります。<br /><br /> この属性は、別のステートメントに暗黙的に割り当てられた記述子ハンドル、または同じステートメントに暗黙的に設定された別の記述子ハンドルに設定することはできません。暗黙的に割り振られる記述子ハンドルは、複数のステートメントまたは記述子ハンドルに関連付けることはできません。|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 1.0)|指定されたステートメントで呼び出された関数を非同期に実行するかどうかを指定する SQLULEN 値。<br /><br /> SQL_ASYNC_ENABLE_OFF = ステートメント レベルの非同期実行サポートを無効にします (既定値)。<br /><br /> SQL_ASYNC_ENABLE_ON = ステートメント レベルの非同期実行のサポートを有効にします。<br /><br /> 詳細については、「[非同期実行 (ポーリング メソッド)」](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)を参照してください。<br /><br /> ステートメント レベルの非同期実行をサポートするドライバーの場合、ステートメント属性SQL_ATTR_ASYNC_ENABLE読み取り専用です。 この値は、ステートメント・ハンドルが割り振られた時点で同じ名前を持つ接続レベル属性の値と同じです。<br /><br /> SQL_ASYNC_MODE*インフォタイプ*が返SQL_AM_CONNECTION返すときにSQL_ATTR_ASYNC_ENABLEを設定するために**SQLSetStmtAttr**を呼び出すと、SQLSTATE HYC00 (オプション機能が実装されていません) が返されます。 詳細については[、SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)を参照してください。|  
|SQL_ATTR_ASYNC_STMT_EVENT (ODBC 3.8)|イベント ハンドルである SQLPOINTER 値。<br /><br /> 非同期関数の完了通知は **、SQLSetStmtAttr**を呼び出して**SQL_ATTR_ASYNC_STMT_EVENT**属性を設定し、イベント ハンドルを指定することで有効になります。|  
|SQL_ATTR_ASYNC_STMT_PCALLBACK (ODBC 3.8)|非同期コールバック関数への SQLPOINTER。<br /><br /> ドライバー マネージャーのみがこの属性を使用してドライバーの**SQLSetStmtAttr**関数を呼び出すことができます。|  
|SQL_ATTR_ASYNC_STMT_PCONTEXT (ODBC 3.8)|コンテキスト構造への SQLPOINTER<br /><br /> ドライバー マネージャーのみがこの属性を使用してドライバーの**SQLSetStmtAttr**関数を呼び出すことができます。|  
|SQL_ATTR_CONCURRENCY (ODBC 2.0)|カーソルの同時実行を指定する SQLULEN 値。<br /><br /> SQL_CONCUR_READ_ONLY = カーソルは読み取り専用です。 更新は許可されません。<br /><br /> SQL_CONCUR_LOCK = カーソルは、行を確実に更新するために十分な最低レベルのロックを使用します。<br /><br /> SQL_CONCUR_ROWVER = カーソルはオプティミスティック同時実行制御を使用し、SQLBase ROWID や Sybase TIMESTAMP などの行バージョンを比較します。<br /><br /> SQL_CONCUR_VALUES = カーソルはオプティミスティック同時実行制御を使用して値を比較します。<br /><br /> SQL_ATTR_CONCURRENCYの既定値はSQL_CONCUR_READ_ONLYです。<br /><br /> オープン・カーソルに対しては、この属性を指定できません。 詳細については、「[同時実行の種類](../../../odbc/reference/develop-app/concurrency-types.md)」を参照してください。<br /><br /> *SQL_ATTR_CURSOR_TYPE属性*が現在の値をサポートしていない型に変更SQL_ATTR_CONCURRENCY場合、SQL_ATTR_CONCURRENCYの値は実行時に変更され **、SQLExecDirect**または**SQLPrepare**が呼び出されたときに警告が発行されます。<br /><br /> ドライバーが SELECT **FOR UPDATE**ステートメントをサポートし、SQL_ATTR_CONCURRENCY の値が SQL_CONCUR_READ_ONLY に設定されている間にこのようなステートメントが実行される場合は、エラーが返されます。 SQL_ATTR_CONCURRENCYの値が、ドライバーがサポートする値がSQL_ATTR_CURSOR_TYPEの現在の値ではなく、SQL_ATTR_CURSOR_TYPEの現在の値に対して変更された場合、SQL_ATTR_CURSOR_TYPEの値は実行時に変更され **、SQLExecDirect**または**SQLPrepare**が呼び出されると SQLSTATE 01S02 (オプション値が変更されました) が発行されます。<br /><br /> 指定された同時実行がデータ ソースでサポートされていない場合、ドライバーは別の同時実行を置き換え、SQLSTATE 01S02 (オプション値が変更されました) を返します。 SQL_CONCUR_VALUESの場合、ドライバーはSQL_CONCUR_ROWVERに置き換え、その逆も同様です。 SQL_CONCUR_LOCKの場合、ドライバーは、順序、SQL_CONCUR_ROWVER、またはSQL_CONCUR_VALUESに置き換えられます。 置換された値の妥当性は、実行時間までチェックされません。<br /><br /> SQL_ATTR_CONCURRENCYと他のカーソル属性との関係の詳細については、[カーソルの特性とカーソルの種類](../../../odbc/reference/develop-app/cursor-characteristics-and-cursor-type.md)を参照してください。|  
|SQL_ATTR_CURSOR_SCROLLABLE (ODBC 3.0)|アプリケーションが必要とするサポートのレベルを指定する SQLULEN 値。 この属性を設定すると **、後続の SQLExecDirect**および**SQL 実行**の呼び出しに影響します。<br /><br /> SQL_NONSCROLLABLE = スクロール可能なカーソルは、ステートメント・ハンドルでは必要ありません。 アプリケーションがこのハンドルで**SQLFetchScroll を**呼び出す場合 *、FetchOrientation*の唯一の有効な値はSQL_FETCH_NEXT。 これは既定値です。<br /><br /> SQL_SCROLLABLE = スクロール可能なカーソルは、ステートメント・ハンドルに必要です。 **SQLFetchScroll**を呼び出すとき、アプリケーションは、連続モード以外のモードでカーソルの位置を指定する*FetchOrientation*の有効な値を指定できます。<br /><br /> スクロール可能なカーソルの詳細については、「[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)」を参照してください。 SQL_ATTR_CURSOR_SCROLLABLEと他のカーソル属性との関係の詳細については、[カーソルの特性およびカーソルの種類](../../../odbc/reference/develop-app/cursor-characteristics-and-cursor-type.md)を参照してください。|  
|SQL_ATTR_CURSOR_SENSITIVITY (ODBC 3.0)|ステートメント・ハンドル上のカーソルが、別のカーソルによって結果セットに加えられた変更を可視にするかどうかを指定する SQLULEN 値。 この属性を設定すると **、後続の SQLExecDirect**および**SQL 実行**の呼び出しに影響します。 アプリケーションは、この属性の値を読み取り戻して、アプリケーションによって設定された初期状態または状態を取得できます。<br /><br /> SQL_UNSPECIFIED = カーソルのタイプが何であるか、およびステートメント・ハンドル上のカーソルが、別のカーソルによって結果セットに加えられた変更を可視にするかどうかは指定されません。 ステートメント ハンドル上のカーソルは、表示されない、一部、またはすべての変更を行うことができます。 これは既定値です。<br /><br /> SQL_INSENSITIVE = ステートメント・ハンドルのすべてのカーソルは、他のカーソルによって行われた変更を反映せずに結果セットを表示します。 無神経なカーソルは読み取り専用です。 これは、読み取り専用の同時実行性を持つ静的カーソルに対応します。<br /><br /> SQL_SENSITIVE = ステートメント ハンドルのすべてのカーソルは、別のカーソルによって結果セットに加えられたすべての変更を表示します。<br /><br /> SQL_ATTR_CURSOR_SENSITIVITYと他のカーソル属性との関係の詳細については、「[カーソルの特性」および「カーソルの種類](../../../odbc/reference/develop-app/cursor-characteristics-and-cursor-type.md)」を参照してください。|  
|SQL_ATTR_CURSOR_TYPE (ODBC 2.0)|カーソル・タイプを指定する SQLULEN 値。<br /><br /> SQL_CURSOR_FORWARD_ONLY = カーソルは前方にのみスクロールします。<br /><br /> SQL_CURSOR_STATIC = 結果セット内のデータは静的です。<br /><br /> SQL_CURSOR_KEYSET_DRIVEN = ドライバーは、SQL_ATTR_KEYSET_SIZE ステートメント属性で指定された行数のキーを保存し、使用します。<br /><br /> SQL_CURSOR_DYNAMIC = ドライバは、行セット内の行のキーのみを保存して使用します。<br /><br /> 既定値は SQL_CURSOR_FORWARD_ONLY です。 SQL ステートメントの準備後にこの属性を指定することはできません。<br /><br /> 指定されたカーソルの種類がデータ ソースでサポートされていない場合、ドライバーは別のカーソルの種類を置き換え、SQLSTATE 01S02 (オプション値が変更されました) を返します。 混合カーソルまたは動的カーソルの場合、ドライバーはキーセット ドリブン カーソルまたは静的カーソルを順番に置き換えます。 キーセット ドリブン カーソルの場合、ドライバーは静的カーソルを置き換えます。<br /><br /> スクロール可能なカーソルの種類の詳細については、「[スクロール可能なカーソルの種類](../../../odbc/reference/develop-app/scrollable-cursor-types.md)」を参照してください。 SQL_ATTR_CURSOR_TYPEと他のカーソル属性との関係の詳細については、「[カーソルの特性」および「カーソルの種類](../../../odbc/reference/develop-app/cursor-characteristics-and-cursor-type.md)」を参照してください。|  
|SQL_ATTR_ENABLE_AUTO_IPD (ODBC 3.0)|IPD の自動作成を実行するかどうかを指定する SQLULEN 値。<br /><br /> SQL_TRUE = **SQLPrepare**の呼び出し後に IPD の自動作成を有効にします。 SQL_FALSE = **SQLPrepare**の呼び出し後に IPD の自動作成をオフにします。 (アプリケーションは、サポートされている場合は**SQLDescribeParam**を呼び出すことによって、IPD フィールド情報を取得できます。ステートメント属性SQL_ATTR_ENABLE_AUTO_IPDのデフォルト値はSQL_FALSEです。 詳細については、 [IPD の自動作成を](../../../odbc/reference/develop-app/automatic-population-of-the-ipd.md)参照してください。|  
|SQL_ATTR_FETCH_BOOKMARK_PTR (ODBC 3.0)|バイナリ ブックマーク\*値を指す SQLLEN。 SQL_FETCH_BOOKMARKと等しい*fFetchOrientation*で**SQLFetchScroll**が呼び出されると、ドライバーはこのフィールドからブックマーク値を取得します。 このフィールドは、デフォルトで null ポインターになります。 詳細については、「[ブックマークによるスクロール](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)」を参照してください。<br /><br /> このフィールドが指す値は、行セット バッファーにキャッシュされたブックマークを使用する**SQLBulkOperations**のブックマークによる削除、ブックマークによる更新、またはブックマーク操作によるフェッチには使用されません。|  
|SQL_ATTR_IMP_PARAM_DESC (ODBC 3.0)|IPD へのハンドル。 この属性の値は、ステートメントが最初に割り振られたときに割り当てられた記述子です。 アプリケーションはこの属性を設定できません。<br /><br /> この属性は **、SQLGetStmtAttr**の呼び出しによって取得できますが **、SQLSetStmtAttr**の呼び出しでは設定できません。|  
|SQL_ATTR_IMP_ROW_DESC (ODBC 3.0)|IRD へのハンドル。 この属性の値は、ステートメントが最初に割り振られたときに割り当てられた記述子です。 アプリケーションはこの属性を設定できません。<br /><br /> この属性は **、SQLGetStmtAttr**の呼び出しによって取得できますが **、SQLSetStmtAttr**の呼び出しでは設定できません。|  
|SQL_ATTR_KEYSET_SIZE (ODBC 2.0)|キーセット ドリブン カーソルのキーセット内の行数を指定する SQLULEN。 キーセットサイズが 0 (デフォルト) の場合、カーソルは完全にキーセット駆動になります。 キーセットサイズが 0 より大きい場合、カーソルは混合されます (キーセット内でキーセット駆動、キーセット外で動的)。 デフォルトのキーセットサイズは 0 です。 キーセット ドリブン カーソルの詳細については、「[キーセット ドリブン カーソル](../../../odbc/reference/develop-app/keyset-driven-cursors.md)」を参照してください。<br /><br /> 指定されたサイズが最大キーセット サイズを超える場合、ドライバーはそのサイズを置き換え、SQLSTATE 01S02 (オプション値が変更) を返します。<br /><br /> キーセット サイズが 0 より大きく、行セット サイズより小さい場合 **、SQLFetch**または**SQLFetchScroll**はエラーを返します。|  
|SQL_ATTR_MAX_LENGTH (ODBC 1.0)|ドライバーが文字またはバイナリ列から返すデータの最大量を指定する SQLULEN 値。 *ValuePtr*が使用可能なデータの長さより小さい場合 **、SQLFetch**または**SQLGetData**はデータを切り捨ててSQL_SUCCESS返します。 *ValuePtr*が 0 (既定値) の場合、ドライバーは、利用可能なすべてのデータを返そうとします。<br /><br /> 指定した長さが、データ ソースが返すことができるデータの最小量より小さいか、データ ソースが返すことができるデータの最大量よりも大きい場合、ドライバーはその値を置き換え、SQLSTATE 01S02 (オプション値が変更されました) を返します。<br /><br /> この属性の値は、オープン・カーソルに設定できます。ただし、この設定はすぐには有効になりませんが、この場合、ドライバーは SQLSTATE 01S02 (オプション値が変更されました) を返し、属性を元の値にリセットします。<br /><br /> この属性は、ネットワーク トラフィックを削減することを目的としており、多層ドライバーのデータ ソース (ドライバーとは対照的に) が実装できる場合にのみサポートする必要があります。 このメカニズムは、アプリケーションでデータを切り捨てるために使用しないでください。受信したデータを切り捨てるには、アプリケーションは**SQLBindCol**または**SQLGetData**の*引数 BufferLength*に最大バッファー長を指定する必要があります。|  
|SQL_ATTR_MAX_ROWS (ODBC 1.0)|**SELECT**ステートメントのアプリケーションに返される最大行数に対応する SQLULEN 値。 \* *ValuePtr*が 0 (既定値) に等しい場合、ドライバーはすべての行を返します。<br /><br /> この属性は、ネットワーク トラフィックを減らすことを目的としています。 概念的には、結果セットが作成されるときに適用され、結果セットが最初の*ValuePtr*行に制限されます。 結果セットの行数が*ValuePtr*より大きい場合、結果セットは切り捨てられます。<br /><br /> SQL_ATTR_MAX_ROWSは、 Catalog 関数によって返された結果セットを含め、 *Statement*のすべての結果セットに適用されます。 SQL_ATTR_MAX_ROWSカーソル行カウントの最大値を設定します。<br /><br /> ドライバーは、SQL_ATTR_MAX_ROWSが適切に実装されることを保証できない場合は **、SQLFetch**または**SQLFetchScroll**のSQL_ATTR_MAX_ROWS動作をエミュレートしないでください (結果セットのサイズ制限をデータ ソースで実装できない場合)。<br /><br /> これは、SELECT ステートメント (カタログ関数など) 以外のステートメントに対してSQL_ATTR_MAX_ROWSが適用されるかどうか、ドライバー定義です。<br /><br /> この属性の値は、オープン・カーソルに設定できます。ただし、この設定はすぐには有効になりませんが、この場合、ドライバーは SQLSTATE 01S02 (オプション値が変更されました) を返し、属性を元の値にリセットします。|  
|SQL_ATTR_METADATA_ID (ODBC 3.0)|カタログ関数の文字列引数の処理方法を決定する SQLULEN 値。<br /><br /> SQL_TRUE場合、カタログ関数の文字列引数は識別子として扱われます。 ケースは重要ではありません。 区切り文字を除く文字列の場合、ドライバーは末尾のスペースを削除し、文字列は大文字に折り返されます。 区切り文字列の場合、ドライバーは先頭または末尾の空白を削除し、区切り文字の間にあるものは、文字通り取ります。 これらの引数の 1 つが null ポインターに設定されている場合、関数は SQL_ERROR および SQLSTATE HY009 (ヌル・ポインターの無効な使用) を戻します。<br /><br /> SQL_FALSE場合、カタログ関数の文字列引数は識別子として扱われないです。 ケースは重要です。 引数に応じて、文字列検索パターンを含めるかどうかが考えます。<br /><br /> 既定値は SQL_FALSE です。<br /><br /> 値の一覧を受け取る**SQLTables**の*TableType*引数は、この属性の影響を受けません。<br /><br /> SQL_ATTR_METADATA_IDは、接続レベルでも設定できます。 (接続属性でもある唯一のステートメント属性は、そのステートメントとSQL_ATTR_ASYNC_ENABLEだけです。<br /><br /> 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。|  
|SQL_ATTR_NOSCAN (ODBC 1.0)|ドライバーがエスケープ シーケンスの SQL 文字列をスキャンする必要があるかどうかを示す SQLULEN 値:<br /><br /> SQL_NOSCAN_OFF = ドライバーは SQL 文字列をスキャンしてエスケープ シーケンス (既定値) を探します。<br /><br /> SQL_NOSCAN_ON = ドライバーは SQL 文字列をスキャンしてエスケープ シーケンスをスキャンしません。 代わりに、ドライバーは、データ ソースに直接ステートメントを送信します。<br /><br /> 詳細については[、「ODBC でのエスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)」を参照してください。|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR (ODBC 3.0)|動的パラメーターのバインディングを変更するためにポインターに追加されるオフセットを指す SQLULEN * 値。 このフィールドが null 以外の場合、ドライバーはポインターを逆参照し、記述子レコード (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTR) の各遅延フィールドに逆参照値を追加し、バインド時に新しいポインター値を使用します。 既定では null に設定されています。<br /><br /> バインド オフセットは、常にSQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTRの各フィールドに直接追加されます。 オフセットが別の値に変更された場合でも、新しい値は記述子フィールドの値に直接追加されます。 新しいオフセットは、フィールド値にそれ以前のオフセットを加えた値には追加されません。<br /><br /> 詳細については、「パラメータ[のバインド オフセット](../../../odbc/reference/develop-app/parameter-binding-offsets.md)」を参照してください。<br /><br /> このステートメント属性を設定すると、APD ヘッダーのSQL_DESC_BIND_OFFSET_PTRフィールドが設定されます。|  
|SQL_ATTR_PARAM_BIND_TYPE (ODBC 3.0)|動的パラメーターに使用されるバインディングの向きを示す SQLULEN 値。<br /><br /> このフィールドは、列方向のバインドを選択するために、SQL_PARAM_BIND_BY_COLUMN (既定値) に設定されます。<br /><br /> 行方向のバインドを選択するには、このフィールドは、動的パラメーターのセットにバインドされる構造体またはバッファーのインスタンスの長さに設定されます。 この長さには、バインドされたすべてのパラメーターと構造体またはバッファーの埋め込み用スペースを含めて、バインドされたパラメーターのアドレスが指定された長さでインクリメントされるときに、結果が次のパラメーター・セット内の同じパラメーターの先頭を指していることを確認する必要があります。 ANSI C で*sizeof*演算子を使用する場合、この動作は保証されます。<br /><br /> 詳細については、「[パラメータの配列のバインド](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)」を参照してください。<br /><br /> このステートメント属性を設定すると、APD ヘッダーのSQL_DESC_BIND_TYPEフィールドが設定されます。|  
|SQL_ATTR_PARAM_OPERATION_PTR (ODBC 3.0)|SQL ステートメントの実行中に\*パラメーターを無視するために使用される SQLUSMALLINT 値の配列を指す SQLUSMALLINT 値。 各値は、SQL_PARAM_PROCEED (実行されるパラメーターの場合) またはSQL_PARAM_IGNORE (パラメーターが無視される場合) に設定されます。<br /><br /> APD 内のSQL_DESC_ARRAY_STATUS_PTRが指すアレイ内のステータス値をSQL_PARAM_IGNOREに設定することで、処理時に一連のパラメーターを無視できます。 パラメーターのセットは、そのステータス値がSQL_PARAM_PROCEEDに設定されている場合、または配列内の要素が設定されていない場合に処理されます。<br /><br /> このステートメント属性は null ポインターに設定できます。 この属性はいつでも設定できますが、次に**SQLExecDirect**または**SQLExecute**が呼び出されるまで、新しい値は使用されません。<br /><br /> この属性は、バインドされたパラメーターがない場合は無視されます。<br /><br /> 詳細については、「[パラメータの配列の使用](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)」を参照してください。<br /><br /> このステートメント属性を設定すると、APD ヘッダーのSQL_DESC_ARRAY_STATUS_PTRフィールドが設定されます。|  
|SQL_ATTR_PARAM_STATUS_PTR (ODBC 3.0)|SQL 実行または\***SQLExecDirect**の呼び出し後に、パラメーター値の各行の状況情報を含む SQLUSMALLINT 値の配列を指す**値**。 このフィールドは、PARAMSET_SIZEが 1 より大きい場合にのみ必要です。<br /><br /> ステータス値には、次の値を含めることができます。<br /><br /> SQL_PARAM_SUCCESS: SQL ステートメントは、この一連のパラメーターに対して正常に実行されました。<br /><br /> SQL_PARAM_SUCCESS_WITH_INFO: SQL ステートメントは、この一連のパラメーターに対して正常に実行されました。ただし、警告情報は、診断データ構造で使用できます。<br /><br /> SQL_PARAM_ERROR: この一連のパラメーターの処理中にエラーが発生しました。 診断データ構造には、追加のエラー情報が含まれます。<br /><br /> SQL_PARAM_UNUSED: このパラメータ セットは、以前のパラメータ セットによってエラーが発生してさらに処理が中止されたか、またはSQL_ATTR_PARAM_OPERATION_PTRで指定された配列内のそのパラメータ セットに対してSQL_PARAM_IGNOREが設定されたため、使用されていませんでした。<br /><br /> SQL_PARAM_DIAG_UNAVAILABLE: ドライバーは、パラメーターの配列をモノリシック単位として扱うので、このレベルのエラー情報は生成されません。<br /><br /> このステートメント属性は null ポインターに設定できます。 この属性はいつでも設定できますが、次に**SQLExecute**または**SQLExecDirect**が呼び出されるまで、新しい値は使用されません。 この属性を設定すると、ドライバーによって実装される出力パラメーターの動作に影響する可能性があることに注意してください。<br /><br /> 詳細については、「[パラメータの配列の使用](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)」を参照してください。<br /><br /> このステートメント属性を設定すると、IPD ヘッダーの SQL_DESC_ARRAY_STATUS_PTR フィールドが設定されます。|  
|SQL_ATTR_PARAMS_PROCESSED_PTR (ODBC 3.0)|エラー・セットを\*含む、処理されたパラメーターのセットの数を戻すバッファーを指す SQLULEN レコード・フィールド。 null ポインターの場合は、数値は返されません。<br /><br /> このステートメント属性を設定すると、IPD ヘッダーのSQL_DESC_ROWS_PROCESSED_PTRフィールドが設定されます。<br /><br /> この属性が指すバッファを埋める**SQLExecDirect**または**SQLExecute**の呼び出しがSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さない場合、バッファの内容は未定義です。<br /><br /> 詳細については、「[パラメータの配列の使用](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)」を参照してください。|  
|SQL_ATTR_PARAMSET_SIZE (ODBC 3.0)|各パラメーターの値の数を指定する SQLULEN 値。 SQL_ATTR_PARAMSET_SIZEが 1 より大きい場合、apD のSQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTRはアレイを指します。 各配列の基数は、このフィールドの値と等しくなります。<br /><br /> この属性は、バインドされたパラメーターがない場合は無視されます。<br /><br /> 詳細については、「[パラメータの配列の使用](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)」を参照してください。<br /><br /> このステートメント属性を設定すると、APD ヘッダーのSQL_DESC_ARRAY_SIZEフィールドが設定されます。|  
|SQL_ATTR_QUERY_TIMEOUT (ODBC 1.0)|アプリケーションに戻る前に SQL ステートメントが実行されるまで待機する秒数に対応する SQLULEN 値。 *ValuePtr*が 0 (デフォルト) の場合、タイムアウトはありません。<br /><br /> 指定されたタイムアウトがデータ・ソースの最大タイムアウトを超えた場合、または最小タイムアウトより小さい場合 **、SQLSetStmtAttr**はその値を置き換えて SQLSTATE 01S02 (オプション値が変更) を戻します。<br /><br /> **アプリケーションは、SELECT ステートメント**がタイムアウトした場合にステートメントを再利用するために**SQLCloseCursor**を呼び出す必要はありません。<br /><br /> このステートメント属性で設定されたクエリ タイムアウトは、同期モードと非同期モードの両方で有効です。|  
|SQL_ATTR_RETRIEVE_DATA (ODBC 2.0)|SQLULEN 値:<br /><br /> SQL_RD_ON = **SQLFetchScroll**と、ODBC *3.x*では **、SQLFetch**は、指定された位置にカーソルを配置した後、データを取得します。 これは既定値です。<br /><br /> SQL_RD_OFF = **SQLFetchScroll**と、ODBC *3.x*では **、SQLFetch**はカーソルの位置の後にデータを取得しません。<br /><br /> SQL_RETRIEVE_DATAを SQL_RD_OFF に設定すると、アプリケーションは行の取得のオーバーヘッドを発生させることなく、行が存在するか、その行のブックマークを取得できるかどうかを確認できます。 詳細については、「[行のスクロールとフェッチ](../../../odbc/reference/develop-app/scrolling-and-fetching-rows-odbc.md)」を参照してください。<br /><br /> この属性の値は、オープン・カーソルに設定できます。ただし、この設定はすぐには有効になりませんが、この場合、ドライバーは SQLSTATE 01S02 (オプション値が変更されました) を返し、属性を元の値にリセットします。|  
|SQL_ATTR_ROW_ARRAY_SIZE (ODBC 3.0)|SQLFetch または SQL フェッチ**スクロール**の各呼び出しによって返される行の数を指定する**SQLULEN**値。 また **、SQLBulkOperations**で一括ブックマーク操作で使用されるブックマーク配列の行数でもあります。 既定値は 1 です。<br /><br /> 指定した行セットサイズがデータ ソースでサポートされている最大行セット サイズを超える場合、ドライバーはその値を置き換え、SQLSTATE 01S02 (オプション値が変更) を返します。<br /><br /> 詳細については、「[行セットのサイズ](../../../odbc/reference/develop-app/rowset-size.md)」を参照してください。<br /><br /> このステートメント属性を設定すると、ARD ヘッダーのSQL_DESC_ARRAY_SIZEフィールドが設定されます。|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR (ODBC 3.0)|列データのバインディングを変更するためにポインターに追加されたオフセットを指す SQLULEN * 値。 このフィールドが null 以外の場合、ドライバーはポインターを逆参照し、記述子レコード (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTR) の各遅延フィールドに逆参照値を追加し、バインド時に新しいポインター値を使用します。 既定では null に設定されています。<br /><br /> このステートメント属性を設定すると、ARD ヘッダーのSQL_DESC_BIND_OFFSET_PTRフィールドが設定されます。|  
|SQL_ATTR_ROW_BIND_TYPE (ODBC 1.0)|関連付けられたステートメントで SQLFetch または**SQLFetchScroll**が呼び出されたときに使用されるバインディングの方向を設定する**SQLULEN**値。 列方向のバインドは、値を SQL_BIND_BY_COLUMN に設定することによって選択されます。 行方向のバインドは、結果列がバインドされる構造体またはバッファーのインスタンスの長さに値を設定することによって選択されます。<br /><br /> 長さを指定する場合は、バインドされたすべての列のスペースと構造体またはバッファーの埋め込みスペースを含めて、バインドされた列のアドレスが指定された長さでインクリメントされるときに、結果が次の行の同じ列の先頭を指していることを確認する必要があります。 ANSI C で構造体または共用体を持つ**sizeof**演算子を使用する場合、この動作は保証されます。<br /><br /> 列方向のバインディングは **、SQLFetch**および**SQLFetchScroll**の既定のバインディング方向です。<br /><br /> 詳細については、「[ブロック カーソルで使用する列のバインド](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)」を参照してください。<br /><br /> このステートメント属性を設定すると、ARD ヘッダーのSQL_DESC_BIND_TYPEフィールドが設定されます。|  
|SQL_ATTR_ROW_NUMBER (ODBC 2.0)|結果セット全体の現在の行の数を示す SQLULEN 値。 現在の行の番号を確認できない場合、または現在の行がない場合、ドライバーは 0 を返します。<br /><br /> この属性は **、SQLGetStmtAttr**の呼び出しによって取得できますが **、SQLSetStmtAttr**の呼び出しでは設定できません。|  
|SQL_ATTR_ROW_OPERATION_PTR (ODBC 3.0)|\* **SQLSetPos**を使用して一括操作中に行を無視するために使用される SQLUSMALLINT 値の配列を指す値。 各値は、SQL_ROW_PROCEED (一括操作に含める行の場合) またはSQL_ROW_IGNORE (一括操作から除外する行の場合) のいずれかに設定されます。 **(SQLBulkOperations の**呼び出し中にこの配列を使用して行を無視することはできません。<br /><br /> このステートメント属性は null ポインターに設定できます。 この属性はいつでも設定できますが、次に**SQLSetPos**が呼び出されるまで新しい値は使用されません。<br /><br /> 詳細については、「 [SQLSetPos を使用した行セットの行の更新](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)」および「 [SQLSetPos を使用した行セットの行の削除](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)」を参照してください。<br /><br /> このステートメント属性を設定すると、ARD のSQL_DESC_ARRAY_STATUS_PTRフィールドが設定されます。|  
|SQL_ATTR_ROW_STATUS_PTR (ODBC 3.0)|SQLFetch または SQL\*フェッチスクロールの呼び出し後に行の状態値を含む SQLUSMALLINT**SQLFetchScroll**値の配列を指す**値**。 配列には、行セット内の行と同じ数の要素があります。<br /><br /> このステートメント属性は null ポインターに設定できます。 この属性はいつでも設定できますが、新しい値は、次に**SQLBulkOperations** **、SQLFetch、SQLFetchScroll、** または**SQLSetPos**が呼び出されるまで使用されません。 **SQLFetchScroll**<br /><br /> 詳しくは、[フェッチされた行数および状況を](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)参照してください。<br /><br /> このステートメント属性を設定すると、IRD ヘッダーのSQL_DESC_ARRAY_STATUS_PTRフィールドが設定されます。<br /><br /> この属性は、ODBC *2.x*ドライバーによって **、SQLExtendedFetch**の呼び出しで*rgbRowStatus*配列にマップされます。|  
|SQL_ATTR_ROWS_FETCHED_PTR (ODBC 3.0)|SQLFetch または\* **SQLFetchScroll**の呼び出し後にフェッチされた行の数を返すバッファーを指**SQLFetchScroll**す SQLULEN 値。SQL_REFRESH の*操作*引数を指定して**SQLSetPos**の呼び出しによって実行される一括操作によって影響を受ける行の数。または**SQLBulkOperations**によって実行される一括操作の影響を受ける行の数 。 この数にはエラー行が含まれます。<br /><br /> 詳しくは、[フェッチされた行数および状況を](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)参照してください。<br /><br /> このステートメント属性を設定すると、IRD ヘッダーのSQL_DESC_ROWS_PROCESSED_PTRフィールドが設定されます。<br /><br /> この属性が指すバッファーを埋める**SQLFetch**または**SQLFetchScroll**の呼び出しがSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さない場合、バッファーの内容は未定義です。|  
|SQL_ATTR_SIMULATE_CURSOR (ODBC 2.0)|位置指定更新および削除ステートメントをシミュレートするドライバーが、このようなステートメントが 1 つの行にのみ影響することを保証するかどうかを指定する SQLULEN 値。<br /><br /> 位置指定更新および削除ステートメントをシミュレートするために、ほとんどのドライバーは、現在の行の各列の値を指定する**WHERE**句を含む検索**UPDATE**または**DELETE**ステートメントを構築します。 これらの列が一意のキーを構成しない限り、このようなステートメントは複数の行に影響を与える可能性があります。<br /><br /> このようなステートメントが 1 つの行にのみ影響することを保証するには、ドライバーは、一意のキーの列を決定し、結果セットにこれらの列を追加します。 アプリケーションが結果セット内の列が一意のキーを構成することを保証する場合、ドライバーは、そのキーを作成する必要はありません。 これにより、実行時間が短縮される可能性があります。<br /><br /> SQL_SC_NON_UNIQUE = ドライバーは、シミュレートされた位置指定更新または削除ステートメントが 1 つの行にのみ影響することを保証しません。それは、アプリケーションの責任です。 ステートメントが複数の行に影響を与える場合は **、SQLExecute** **、SQLExecDirect、** または**SQLSetPos**が SQLSTATE 01001 (カーソル操作の競合) を返します。<br /><br /> SQL_SC_TRY_UNIQUE = ドライバーは、シミュレートされた位置指定更新または削除ステートメントが 1 つの行にのみ影響することを保証しようとします。 ドライバーは、一意のキーがない場合など、複数の行に影響する可能性がある場合でも、常にこのようなステートメントを実行します。 ステートメントが複数の行に影響を与える場合は **、SQLExecute** **、SQLExecDirect、** または**SQLSetPos**が SQLSTATE 01001 (カーソル操作の競合) を返します。<br /><br /> SQL_SC_UNIQUE = ドライバーは、シミュレートされた位置指定更新または削除ステートメントが 1 つの行にのみ影響することを保証します。 ドライバが特定のステートメントに対してこれを保証できない**SQLExecDirect**場合は、エラー**が返されます**。<br /><br /> データ ソースが位置指定更新および削除ステートメントに対してネイティブ SQL サポートを提供し、ドライバーがカーソルをシミュレートしない場合、SQL_SC_UNIQUEがSQL_SIMULATE_CURSOR要求されたときにSQL_SUCCESSが返されます。 SQL_SC_TRY_UNIQUEまたはSQL_SC_NON_UNIQUEが要求された場合、SQL_SUCCESS_WITH_INFOが返されます。 データ ソースがSQL_SC_TRY_UNIQUE レベルのサポートを提供し、ドライバーが提供しない場合、SQL_SUCCESSSQL_SC_TRY_UNIQUEに対して返され、SQL_SUCCESS_WITH_INFOがSQL_SC_NON_UNIQUE返されます。<br /><br /> 指定されたカーソル シミュレーションタイプがデータ ソースでサポートされていない場合、ドライバは別のシミュレーション タイプを置き換え、SQLSTATE 01S02 (オプション値が変更) を返します。 SQL_SC_UNIQUEの場合、ドライバーは順序に従って、SQL_SC_TRY_UNIQUEまたはSQL_SC_NON_UNIQUE。 SQL_SC_TRY_UNIQUEの場合、ドライバーはSQL_SC_NON_UNIQUEに置き換えられます。<br /><br /> デフォルトはSQL_SC_UNIQUEです。<br /><br /> 詳細については、「[位置指定更新ステートメントと削除ステートメントのシミュレート](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)」を参照してください。|  
|SQL_ATTR_USE_BOOKMARKS (ODBC 2.0)|アプリケーションがカーソルを持つブックマークを使用するかどうかを指定する SQLULEN 値。<br /><br /> SQL_UB_OFF = オフ (デフォルト)<br /><br /> SQL_UB_VARIABLE = アプリケーションはカーソルを持つブックマークを使用し、ドライバーはサポートされている場合は可変長のブックマークを提供します。 SQL_UB_FIXEDは ODBC *3.x*では推奨されていません。 ODBC *3.x*アプリケーションでは、ODBC *2.x*ドライバ (4 バイト固定長のブックマークのみをサポート) を使用する場合でも、常に可変長ブックマークを使用する必要があります。 これは、固定長ブックマークは可変長ブックマークの特殊なケースにすぎないからです。 ODBC *2.x*ドライバーを操作する場合、ドライバー マネージャーは、SQL_UB_FIXEDにSQL_UB_VARIABLEをマップします。<br /><br /> カーソルでブックマークを使用するには、カーソルを開く前に、SQL_UB_VARIABLE値を指定する必要があります。<br /><br /> 詳細については、「[ブックマークの取得](../../../odbc/reference/develop-app/retrieving-bookmarks.md)」を参照してください。|  
  
 これらの関数は、記述子がアプリケーション記述子ではなく実装記述子である場合にのみ、非同期的に呼び出すことができます。  
  
 [「列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)」および[「行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|接続属性の設定を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|ステートメント属性の設定を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|記述子の単一フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
