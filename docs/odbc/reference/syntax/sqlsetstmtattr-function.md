---
title: "SQLSetStmtAttr 関数 |Microsoft ドキュメント"
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
- SQLSetStmtAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetStmtAttr
helpviewer_keywords:
- SQLSetStmtAttr function [ODBC]
ms.assetid: 7abc5260-733a-48d4-9974-2d1a6a9ea5f6
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d652d9e028cb9eb8edd2ec2865449a4b379c4c64
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetstmtattr-function"></a>SQLSetStmtAttr 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLSetStmtAttr**ステートメントに関連する属性を設定します。  
  
> [!NOTE]  
>  詳細については、どのようなドライバー マネージャーは、この関数にする際にマップ ODBC 3*.x* ODBC 2 を利用するアプリケーション*.x*ドライバーを参照してください[後方の置換関数のマッピングアプリケーションの互換性を](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLSetStmtAttr(  
     SQLHSTMT      StatementHandle,  
     SQLINTEGER    Attribute,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    StringLength);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *属性*  
 [入力]オプションを設定すると、「コメント」に一覧表示  
  
 *ValuePtr*  
 [入力]関連付けられる値*属性*です。 値に応じて*属性*、 *ValuePtr*次のいずれかになります。  
  
-   ODBC 記述子ハンドル。  
  
-   SQLUINTEGER 値です。  
  
-   SQLULEN 値です。  
  
-   次のいずれかへのポインター。  
  
    -   Null で終わる文字列を返します。  
  
    -   バイナリのバッファー。  
  
    -   値または SQLLEN、SQLULEN、または SQLUSMALLINT 型の配列。  
  
    -   ドライバーの定義済みの値です。  
  
 場合、*属性*引数は、ドライバー固有の値を*ValuePtr*符号付き整数である可能性があります。  
  
 *StringLength*  
 [入力]場合*属性*ODBC で定義された属性と*ValuePtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります\* *ValuePtr*. 場合*属性*ODBC で定義された属性と*ValuePtr*整数*StringLength*は無視されます。  
  
 場合*属性*ドライバーの定義済みの属性は、アプリケーション、ドライバー マネージャーに属性の性質を示す設定、 *StringLength*引数。 *StringLength*次の値を持つことができます。  
  
-   場合*ValuePtr*文字の文字列へのポインターが*StringLength* SQL_NTS または文字列の長さです。  
  
-   場合*ValuePtr*アプリケーションが、SQL_LEN_BINARY_ATTR の結果を配置し、バイナリのバッファーへのポインターは、(*長さ*) マクロで*StringLength*です。 これにより、配置に負の値*StringLength*です。  
  
-   場合*ValuePtr*文字の文字列またはバイナリ文字列以外の値へのポインターが*StringLength* SQL_IS_POINTER 値でなければなりません。  
  
-   場合*ValuePtr*し、固定長の値を含む*StringLength*は SQL_IS_INTEGER か SQL_IS_UINTEGER、必要に応じて。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetStmtAttr** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType* SQL の_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLSetStmtAttr**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプション値が変更されました|ドライバーがで指定された値をサポートしていません*ValuePtr*で指定された値または*ValuePtr*が正しくない実装の動作条件のため、ドライバーのような値を置換するようにします。 (**SQLGetStmtAttr**を一時的に置換された値の決定に呼び出すことができます)。代替値は有効、 *StatementHandle*カーソルが閉じられるまで、ステートメント属性はこの時点で、前の値に元に戻します。 変更可能なステートメント属性は次のとおりです。<br /><br /> SQL _ ATTR_CONCURRENCY SQL _ ATTR_CURSOR_TYPE SQL _ ATTR_KEYSET_SIZE SQL _ ATTR_MAX_LENGTH SQL _ ATTR_MAX_ROWS SQL _ ATTR_QUERY_TIMEOUT SQL_ATTR_ROW_ARRAY_SIZE SQL _ ATTR_SIMULATE_CURSOR<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|*属性*が SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_SIMULATE_CURSOR、または SQL_ATTR_USE_BOOKMARKS、およびカーソルが開かれていた。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|*属性*引数が文字列属性を必要とするステートメント属性を識別し、 *ValuePtr*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLSetStmtAttr**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY011|属性を設定できません。|*属性*SQL_ATTR_CONCURRENCY、_ ATTR_CURSOR_TYPE、_ ATTR_SIMULATE_CURSOR または _ ATTR_USE_BOOKMARKS、ステートメントを準備します。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY017|自動的に割り当てられた記述子ハンドルの使い方が正しくありません。|(DM)、*属性*因数が SQL_ATTR_IMP_ROW_DESC または SQL_ATTR_IMP_PARAM_DESC でした。<br /><br /> (DM)、*属性*引数された SQL_ATTR_APP_ROW_DESC または SQL_ATTR_APP_PARAM_DESC、および、値で*ValuePtr*ハンドル以外に暗黙的に割り当てられた記述子ハンドルであったARD または APD の割り当てください。|  
|HY024|無効な属性値|指定した*属性*値で、無効な値が指定されました*ValuePtr*です。 (ドライバー マネージャーは、この SQLSTATE 接続と SQL_ATTR_ACCESS_MODE または _ ATTR_ASYNC_ENABLE などの値の個別のセットをそのまま使用するステートメント属性に対してのみを返します。 他のすべての接続とステートメント属性のドライバーがで指定された値を確認する必要があります*ValuePtr*)。<br /><br /> *属性*引数が SQL_ATTR_APP_ROW_DESC または SQL_ATTR_APP_PARAM_DESC、および*ValuePtr*されたのと同じ接続上にないを明示的に割り当てられた記述子ハンドル、 *StatementHandle*引数。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM)  *\*ValuePtr*文字の文字列、および*StringLength*引数が 0 未満の値がでした SQL_NTS です。|  
|HY092|無効な属性またはオプション識別子|引数の指定された値 (DM)*属性*が ODBC ドライバーでサポートされているのバージョンは無効です。<br /><br /> 引数の指定された値 (DM)*属性*読み取り専用の属性であった。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|引数が指定された値*属性*有効な ODBC ステートメント属性が ODBC のバージョンは、ドライバーでサポートされていますが、ドライバーによってサポートされていませんでした。<br /><br /> *属性*引数を呼び出すと、SQL_ATTR_ASYNC_ENABLE **SQLGetInfo**で、*情報の種類*SQL_ASYNC_MODE の SQL_AM_CONNECTION を返します。<br /><br /> *属性*引数 SQL_ATTR_ENABLE_AUTO_IPD、SQL_ATTR_AUTO_IPD 接続属性の値が SQL_FALSE をでした。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|S1118|ドライバーは非同期通知をサポートしていません|呼び出す場合**SQLSetStmtAttr** SQL_ATTR_ASYNC_STMT_EVENT; を設定する非同期の通知は、ドライバーによってサポートされていません。|  
  
## <a name="comments"></a>コメント  
 別の呼び出しによって変更されるまで、ステートメントのステートメント属性を有効になります**SQLSetStmtAttr**を呼び出して、ステートメントが削除されるまで、または**SQLFreeHandle**です。 呼び出す**SQLFreeStmt** SQL_CLOSE、SQL_UNBIND、または SQL_RESET_PARAMS オプションはリセットされませんステートメント属性。  
  
 データ ソースがで指定された値をサポートしていない場合、いくつかのステートメント属性サポートのような値の置換*ValuePtr*です。 このような場合は、ドライバーは SQL_SUCCESS_WITH_INFO と SQLSTATE 01S02 を返します。 (オプションの値が変更されました)。 たとえば場合、*属性*SQL_ATTR_CONCURRENCY はおよび*ValuePtr* SQL_CONCUR_ROWVER、し、データ ソースはサポートしていない場合このドライバー SQL_CONCUR_VALUES で置き換え返さ sql _SUCCESS_WITH_INFO です。 置換された値を決定するには、アプリケーションが呼び出す**SQLGetStmtAttr**です。  
  
 情報の形式設定*ValuePtr*に指定された依存*属性*です。 **SQLSetStmtAttr**で 2 つの異なる形式のいずれかの属性情報を受け取ります。 文字の文字列または整数値。 それぞれの形式は、属性の説明に記録されます。 この形式は内の各属性に対して返される情報に適用されます**SQLGetStmtAttr**です。 指す文字列の文字、 *ValuePtr*の引数**SQLSetStmtAttr**の長を持つ*StringLength*です。  
  
> [!NOTE]  
>  呼び出して、接続レベルでのステートメント属性を設定する機能**SQLSetConnectAttr** ODBC 3 では廃止されて*.x*です。 ODBC 3*.x*アプリケーションは、接続レベルでステートメント属性を設定しない必要があります。 ODBC 3*.x*を除き、SQL_ATTR_METADATA_ID と SQL_ATTR_ASYNC_ENABLE 属性接続属性とステートメント属性の両方が可能であり、接続レベルでのステートメント属性を設定することはできません接続のレベルまたはステートメント レベルのいずれかに設定します。  
  
> [!NOTE]  
>  ODBC 3*.x* ODBC 2 で機能する場合、ドライバーはこの機能をサポートのみ必要*.x* ODBC 2 を設定するアプリケーションに*.x*接続レベルでステートメントのオプションです。 詳細については、下にある「設定ステートメント オプションで、接続レベル」を参照してください。 [SQLSetConnectOption マッピング](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)旧バージョンと互換性ための付録 g: ドライバーのガイドライン」にします。  
  
## <a name="statement-attributes-that-set-descriptor-fields"></a>記述子フィールドを設定するステートメント属性  
 多くのステートメント属性は、記述子のヘッダー フィールドに対応します。 記述子フィールドの設定でこれらの属性に実際に結果を設定します。 呼び出しによってフィールドの設定**SQLSetStmtAttr**ではなくに**SQLSetDescField**記述子ハンドルは、関数呼び出しを取得する必要がないという利点がします。  
  
> [!CAUTION]  
>  呼び出す**SQLSetStmtAttr**の 1 つのステートメントが他のステートメントを与えることができます。 これは、明示的に割り当てられているし、その他のステートメントに関連付けられても APD または ARD ステートメントに関連付けられているときに発生します。 **SQLSetStmtAttr** APD または ARD、変更、変更は、この記述子が関連付けられているすべてのステートメントに適用します。 アプリケーションが、他のステートメントからこの記述子の関連付けを解除する必要があります、必要な動作でない場合 (を呼び出して**SQLSetStmtAttr** SQL_ATTR_APP_ROW_DESC または SQL_ATTR_APP_PARAM_DESC フィールド別に設定するには記述子ハンドル) 呼び出しの前に**SQLSetStmtAttr**もう一度です。  
  
 によって識別されるステートメントに現在関連付けられている適用可能な記述子ののみ、フィールドが設定されて、記述子フィールドが設定されている対応するステートメント属性の結果として設定されている場合、 *StatementHandle*引数、および属性の設定には影響しません、記述子は、将来そのステートメントを関連付けることができます。 呼び出し、ステートメント属性になっている記述子フィールドを設定すると、 **SQLSetDescField**、対応するステートメント属性を設定します。 場合は、明示的に割り当てられた記述子は、ステートメントから関連付けが解除されました、ヘッダー フィールドに対応するステートメント属性は、暗黙的に割り当てられた記述子フィールドの値に戻ります。  
  
 ステートメントが割り当てられます (を参照してください[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md))、4 つの記述子ハンドルを自動的に割り当てられ、ステートメントに関連付けられています。 明示的に割り当てられた記述子ハンドル関連付けることができ、ステートメントで呼び出すことによって**SQLAllocHandle**で、 *fHandleType*記述子ハンドルおよび呼び出しますを割り当てるSQL_HANDLE_DESCの**SQLSetStmtAttr**に記述子ハンドルをステートメントに関連付けます。  
  
 次の表に、ステートメント属性は、記述子のヘッダー フィールドに対応します。  
  
|ステートメント属性|ヘッダー フィールド|Desc です。|  
|-------------------------|------------------|-----------|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_DESC_BIND_OFFSET_PTR|APD|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_DESC_BIND_TYPE|APD|  
|SQL_ATTR_PARAM_OPERATION_PTR|SQL_DESC_ARRAY_STATUS_PTR|APD|  
|SQL_ATTR_PARAM_STATUS_PTR|SQL_DESC_ARRAY_STATUS_PTR|IPD|  
|SQL_ATTR_PARAMS_PROCESSED_PTR|SQL_DESC_ROWS_PROCESSED_PTR|IPD|  
|SQL_ATTR_PARAMSET_SIZE|SQL_DESC_ARRAY_SIZE|APD|  
|SQL_ATTR_ROW_ARRAY_SIZE|SQL_DESC_ARRAY_SIZE|ARD|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR|SQL_DESC_BIND_OFFSET_PTR|ARD|  
|SQL_ATTR_ROW_BIND_TYPE|SQL_DESC_BIND_TYPE|ARD|  
|SQL_ATTR_ROW_OPERATION_PTR|SQL_DESC_ARRAY_STATUS_PTR|ARD|  
|SQL_ATTR_ROW_STATUS_PTR|SQL_DESC_ARRAY_STATUS_PTR|IRD|  
|SQL_ATTR_ROWS_FETCHED_PTR|SQL_DESC_ROWS_PROCESSED_PTR|IRD|  
  
## <a name="statement-attributes"></a>ステートメント属性  
 現在定義されている属性と導入された ODBC のバージョンは、次の表に表示されます。多くの属性が異なるデータ ソースを活用するためにドライバーによって定義されることが必要です。 属性の範囲は ODBC; によって予約されています。ドライバーの開発者は、Open Group から独自ドライバー固有の値を予約する必要があります。 詳細については、次を参照してください。[ドライバー固有のデータ型、記述子の種類、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)です。  
  
|属性|*ValuePtr*内容|  
|---------------|-------------------------|  
|SQL_ATTR_APP_PARAM_DESC (ODBC 3.0)|APD の後続の呼び出しを識別するハンドル**SQLExecute**と**SQLExecDirect**ステートメント ハンドルにします。 この属性の初期値は、ステートメントが最初に割り当てられたときに暗黙的に割り当てられた記述子です。 そこから、以前は、ステートメント ハンドルに関連付けられていた明示的に割り当てられている APD ハンドルの関連付けを解除し、ステートメント ハンドルに戻しますこの属性の値が SQL_NULL_DESC または記述子の最初に割り当てられたハンドルに設定されている場合、APD のハンドルを暗黙的に割り当てられます。<br /><br /> 別のステートメントに暗黙的に割り当てられた記述子ハンドルにまたは同じのステートメントで暗黙的に設定された別の記述子ハンドルには、この属性を設定することはできません。暗黙的に割り当てられた記述子ハンドルは、複数のステートメントまたは記述子ハンドルに関連付けすることはできません。|  
|SQL_ATTR_APP_ROW_DESC (ODBC 3.0)|ステートメント ハンドルに対する以降のフェッチの ARD へのハンドル。 この属性の初期値は、ステートメントが最初に割り当てられたときに暗黙的に割り当てられた記述子です。 そこから、以前は、ステートメント ハンドルに関連付けられていた明示的に割り当てられている ARD ハンドルの関連付けを解除し、ステートメント ハンドルに戻しますこの属性の値が SQL_NULL_DESC または記述子の最初に割り当てられたハンドルに設定されている場合、ARD ハンドルを暗黙的に割り当てられます。<br /><br /> 別のステートメントに暗黙的に割り当てられた記述子ハンドルにまたは同じのステートメントで暗黙的に設定された別の記述子ハンドルには、この属性を設定することはできません。暗黙的に割り当てられた記述子ハンドルは、複数のステートメントまたは記述子ハンドルに関連付けすることはできません。|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 1.0)|指定されたステートメントで呼び出される関数を非同期的に実行するかどうかを示す SQLULEN 値です。<br /><br /> SQL_ASYNC_ENABLE_OFF = 無効にするステートメント レベルの非同期実行のサポート (既定)。<br /><br /> SQL_ASYNC_ENABLE_ON = ステートメント レベルの非同期実行のサポートを有効にします。<br /><br /> 詳細については、次を参照してください。[非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)です。<br /><br /> ステートメント レベルの非同期実行のサポートとドライバーの場合、ステートメント属性 SQL_ATTR_ASYNC_ENABLE は読み取り専用です。 その値は、ステートメント ハンドルの割り当て時に同じ名前の接続レベルの属性の値として同じです。<br /><br /> 呼び出す**SQLSetStmtAttr** SQL_ATTR_ASYNC_ENABLE を設定するときに、SQL_ASYNC_MODE*情報の種類*SQL_AM_CONNECTION 返します SQLSTATE HYC00 を返します (省略可能な機能が実装されていません)。 詳細については、次を参照してください。 [SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)詳細についてはします。|  
|SQL_ATTR_ASYNC_STMT_EVENT (ODBC 3.8)|イベント ハンドルである SQLPOINTER 値。<br /><br /> 呼び出して非同期関数の完了の通知が有効になっている**SQLSetStmtAttr**を設定する、 **SQL_ATTR_ASYNC_STMT_EVENT**属性をイベント ハンドルを指定します。|  
|SQL_ATTR_ASYNC_STMT_PCALLBACK (ODBC 3.8)|非同期コールバック関数への SQLPOINTER。<br /><br /> ドライバー マネージャーは、運転免許を呼び出すことができますのみ**SQLSetStmtAttr**この属性を持つ関数です。|  
|SQL_ATTR_ASYNC_STMT_PCONTEXT (ODBC 3.8)|Context 構造体への SQLPOINTER<br /><br /> ドライバー マネージャーは、運転免許を呼び出すことができますのみ**SQLSetStmtAttr**この属性を持つ関数です。|  
|SQL_ATTR_CONCURRENCY (ODBC 2.0)|カーソルの同時実行を指定する SQLULEN 値:<br /><br /> SQL_CONCUR_READ_ONLY = カーソルは読み取り専用です。 更新は許可されません。<br /><br /> SQL_CONCUR_LOCK、行を更新することを確認するための十分なロックの最も低いレベルのカーソルの使用を = です。<br /><br /> SQL_CONCUR_ROWVER SQLBase ROWID または Sybase タイムスタンプなどの行のバージョンを比較する、カーソルはオプティミスティック同時実行制御を = です。<br /><br /> SQL_CONCUR_VALUES 値を比較する、カーソルはオプティミスティック同時実行制御を = です。<br /><br /> SQL_ATTR_CONCURRENCY の既定値は、SQL_CONCUR_READ_ONLY です。<br /><br /> この属性は、開いているカーソルに指定できません。 詳細については、次を参照してください。[同時実行の種類](../../../odbc/reference/develop-app/concurrency-types.md)です。<br /><br /> 場合、SQL_ATTR_CURSOR_TYPE*属性*が変更された SQL_ATTR_CONCURRENCY の現在の値をサポートしていない型、SQL_ATTR_CONCURRENCY の値には変更の実行時間、および警告を発行すると**SQLExecDirect**または**SQLPrepare**と呼びます。<br /><br /> ドライバーがサポートされている場合、 **SELECT FOR UPDATE**ステートメントと、このようなステートメントが実行される SQL_CONCUR_READ_ONLY に SQL_ATTR_CONCURRENCY の値を設定中にエラーが返されます。 実行時および SQLSTATE 01S02 SQL_ATTR_CURSOR_TYPE の値は変更 SQL_ATTR_CONCURRENCY の値が変更された場合、ドライバーは、SQL_ATTR_CURSOR_TYPE のいくつかの値のではなく SQL_ATTR_CURSOR_TYPE の現在の値をサポートする値を(オプションの値が変更された) が発行された**SQLExecDirect**または**SQLPrepare**と呼びます。<br /><br /> ドライバーが別の同時実行に置き換えられ、SQLSTATE 01S02 を返す場合は、データ ソースでは、指定した同時実行はサポートされていない、(オプションの値が変更されました)。 置き換えます SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES、ドライバーまたはその逆です。 SQL_CONCUR_LOCK、ドライバーに置き換えます、SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES またはの順序で。 置換された値の有効性は、実行時まではチェックされません。<br /><br /> SQL_ATTR_CONCURRENCY と他のカーソルの属性間のリレーションシップの詳細については、次を参照してください。[カーソルの種類のカーソルの特性と](../../../odbc/reference/develop-app/cursor-characteristics-and-cursor-type.md)です。|  
|SQL_ATTR_CURSOR_SCROLLABLE (ODBC 3.0)|アプリケーションに必要なサポートのレベルを示す SQLULEN 値。 この属性を設定する後続の呼び出しに影響を与える**SQLExecDirect**と**SQLExecute**です。<br /><br /> SQL_NONSCROLLABLE = Scrollable カーソルは、ステートメント ハンドルでは必要ありません。 アプリケーションを呼び出す場合**SQLFetchScroll**の唯一の有効な値は、このハンドルで*FetchOrientation* SQL_FETCH_NEXT がします。 これは既定値です。<br /><br /> SQL_SCROLLABLE = スクロール可能、ステートメント ハンドルでカーソルが必要です。 呼び出すときに**SQLFetchScroll**、アプリケーションが任意の有効な値を指定できます*FetchOrientation*、シーケンシャル モード以外のモードのカーソルの位置決めを実現するためです。<br /><br /> スクロール可能なカーソルの詳細については、次を参照してください。[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)です。 SQL_ATTR_CURSOR_SCROLLABLE と他のカーソルの属性間のリレーションシップの詳細については、次を参照してください[カーソルの特性とカーソルの種類。](../../../odbc/reference/develop-app/cursor-characteristics-and-cursor-type.md)|  
|SQL_ATTR_CURSOR_SENSITIVITY (ODBC 3.0)|ステートメント ハンドルにカーソルが表示されるようにするかどうかを指定する SQLULEN 値の結果に行われた変更は、別のカーソルによって設定されます。 この属性を設定する後続の呼び出しに影響を与える**SQLExecDirect**と**SQLExecute**です。 アプリケーションは、または取得する初期状態の状態として最も最近のこの属性の値は、アプリケーションによって設定戻る読み取ることができます。<br /><br /> SQL_UNSPECIFIED = 指定されていない、カーソルの種類とかどうかのカーソル ステートメント ハンドルに表示されるように別のカーソルが結果セットへの変更。 ステートメント ハンドルにカーソルが表示されるようになしでは、このようないくつか、またはすべての変更。 これは既定値です。<br /><br /> SQL_INSENSITIVE 任意の他のカーソルが結果セットのことに加えられた変更を反映せず、ステートメント ハンドル上のすべてのカーソルを = です。 Insensitive カーソルは読み取り専用です。 これは、静的カーソルは、読み取り専用である同時実行に対応します。<br /><br /> SQL_SENSITIVE = すべてのカーソルに対して、ステートメント ハンドル make 表示結果に加えられたすべての変更が別のカーソルで設定します。<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY と他のカーソルの属性間のリレーションシップの詳細については、次を参照してください。[カーソルの種類のカーソルの特性と](../../../odbc/reference/develop-app/cursor-characteristics-and-cursor-type.md)です。|  
|SQL_ATTR_CURSOR_TYPE (ODBC 2.0)|カーソルの種類を指定する SQLULEN 値:<br /><br /> SQL_CURSOR_FORWARD_ONLY カーソルだけスクロール フォワードを = です。<br /><br /> SQL_CURSOR_STATIC = データ結果セットが静的です。<br /><br /> SQL_CURSOR_KEYSET_DRIVEN = ドライバー保存および SQL_ATTR_KEYSET_SIZE ステートメント属性で指定された行の数のキーを使用します。<br /><br /> SQL_CURSOR_DYNAMIC = ドライバー保存し、行セット内の行キーのみを使用します。<br /><br /> 既定値は、SQL_CURSOR_FORWARD_ONLY です。 SQL ステートメントが準備した後、この属性を指定することはできません。<br /><br /> ドライバーが別のカーソルの種類に置き換えられ、SQLSTATE 01S02 を返します、指定されたカーソルの種類は、データ ソースによってサポートされていない場合、(オプションの値が変更されました)。 混在モードまたは動的カーソルの場合、ドライバーに置換されます、キーセット ドリブンまたは静的カーソルの順序で。 キーセット ドリブン カーソルの場合は、ドライバーには、静的カーソルが置換されます。<br /><br /> スクロール可能なカーソルの種類の詳細については、次を参照してください。[スクロール可能なカーソルの種類](../../../odbc/reference/develop-app/scrollable-cursor-types.md)です。 SQL_ATTR_CURSOR_TYPE およびその他のカーソルの属性間のリレーションシップに関する詳細については、次を参照してください。[カーソルの種類のカーソルの特性と](../../../odbc/reference/develop-app/cursor-characteristics-and-cursor-type.md)です。|  
|SQL_ATTR_ENABLE_AUTO_IPD (ODBC 3.0)|SQLULEN 値、IPD の自動作成を実行するかどうかを示すです。<br /><br /> SQL_TRUE への呼び出し後、IPD の自動作成の順番を = **SQLPrepare**です。 SQL_FALSE = への呼び出し後、IPD の自動設定をオフに**SQLPrepare**です。 (アプリケーションを呼び出して IPD フィールド情報を取得するまだ**SQLDescribeParam**サポートされている場合、します)。ステートメント属性 SQL_ATTR_ENABLE_AUTO_IPD の既定値は、SQL_FALSE です。 詳細については、次を参照してください。 [、IPD の自動設定](../../../odbc/reference/develop-app/automatic-population-of-the-ipd.md)です。|  
|SQL_ATTR_FETCH_BOOKMARK_PTR (ODBC 3.0)|SQLLEN\*バイナリのブックマークの値を指し示します。 ときに**SQLFetchScroll**で呼び出された*fFetchOrientation* SQL_FETCH_BOOKMARK 等しい、ドライバーは、ブックマークのこのフィールド値を取得します。 このフィールドの既定値は null ポインターです。 詳細については、次を参照してください。[ブックマークでスクロール](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)です。<br /><br /> このフィールドによって示される値は使用されません削除のブックマークで、ブックマークで更新または内のブックマーク操作によりフェッチ**SQLBulkOperations**ブックマーク行セットのバッファーにキャッシュを使用します。|  
|SQL_ATTR_IMP_PARAM_DESC (ODBC 3.0)|IPD へのハンドル。 この属性の値は、ステートメントが最初に割り当てられたときに割り当てられた記述子です。 アプリケーションでは、この属性を設定できません。<br /><br /> この属性への呼び出しによって取得できる**SQLGetStmtAttr**への呼び出しでは設定されませんが、 **SQLSetStmtAttr**です。|  
|SQL_ATTR_IMP_ROW_DESC (ODBC 3.0)|IRD のハンドルです。 この属性の値は、ステートメントが最初に割り当てられたときに割り当てられた記述子です。 アプリケーションでは、この属性を設定できません。<br /><br /> この属性への呼び出しによって取得できる**SQLGetStmtAttr**への呼び出しでは設定されませんが、 **SQLSetStmtAttr**です。|  
|SQL_ATTR_KEYSET_SIZE (ODBC 2.0)|キーセット ドリブン カーソルのキーセットに行の数を指定する SQLULEN です。 キーセットのサイズが 0 (既定値) の場合は、完全にキーセット ドリブン カーソルです。 キーセットのサイズが 0 より大きい場合は、カーソルを混合 (キーセット ドリブンのキーセット内とキーセットの外部で動的)。 既定のキーセットのサイズは 0 です。 キーセット ドリブン カーソルの詳細については、次を参照してください。[キーセット ドリブン カーソル](../../../odbc/reference/develop-app/keyset-driven-cursors.md)です。<br /><br /> ドライバーが、そのサイズに置き換えられ、SQLSTATE 01S02 を返します、指定されたサイズが最大キーセットのサイズを超える場合 (オプションの値が変更されました)。<br /><br /> **SQLFetch**または**SQLFetchScroll**キーセットのサイズが 0 より大きい行セットのサイズよりも小さい場合はエラーを返します。|  
|SQL_ATTR_MAX_LENGTH (ODBC 1.0)|ドライバーが文字またはバイナリ列から返されるデータの最大サイズを指定する SQLULEN 値です。 場合*ValuePtr*が、使用可能なデータの長さよりも小さい**SQLFetch**または**SQLGetData**データが切り捨てられるし、関係なく SQL_SUCCESS を返します。 場合*ValuePtr*が 0 (既定値) の場合、ドライバーが利用可能なすべてのデータを返そうとします。<br /><br /> 指定された長さがデータ ソースを返すことができるデータ量の最小値より小さい場合か、データ ソースを返すことができます、値を返す SQLSTATE 01S02 ドライバー代用データの上限を超えて (オプションの値が変更されました)。<br /><br /> 開いているカーソル; でこの属性の値を設定することができます。ただし、設定がすぐに反映されませんである場合、ドライバーは SQLSTATE 01S02 を返します (オプションの変更された値) と属性を元の値にリセットします。<br /><br /> この属性は、ネットワーク トラフィックを削減するためのものでは、複数層のドライバー (driver) ではなく、データ ソースを実装できる場合にのみサポートされている必要があります。 このメカニズム必要がありますいないを使用するアプリケーションでデータを切り捨てるアプリケーションを受信したデータを切り捨てるで最大バッファー長を指定する必要があります、 *BufferLength*引数**SQLBindCol**または**SQLGetData**です。|  
|SQL_ATTR_MAX_ROWS (ODBC 1.0)|アプリケーションに返される行の最大数に対応する SQLULEN 値、**選択**ステートメントです。 場合\* *ValuePtr*が 0 (既定) と等しい、ドライバーは、すべての行を返します。<br /><br /> この属性は、ネットワーク トラフィックを削減するためのものです。 結果セットが作成され、最初に結果セットの制限の適用概念的には、 *ValuePtr*行です。 結果セット内の行の数がより大きいかどうか*ValuePtr*、結果セットが切り詰められています。<br /><br /> すべての結果セットに SQL_ATTR_MAX_ROWS が適用されます、*ステートメント*、カタログ関数によって返されるものなどです。 SQL_ATTR_MAX_ROWS は、カーソル行の数の値の最大値を設定します。<br /><br /> ドライバーは SQL_ATTR_MAX_ROWS の動作をエミュレートしなければなりません**SQLFetch**または**SQLFetchScroll** (かどうかは結果セットのサイズ制限実装できない、データ ソース) が保証できない場合その SQL_ATTRMAX_ROWS は正しく実装されます。<br /><br /> これはドライバー定義 SQL_ATTR_MAX_ROWS を SELECT ステートメント (カタログ関数など) 以外のステートメントに適用するかどうかです。<br /><br /> 開いているカーソル; でこの属性の値を設定することができます。ただし、設定がすぐに反映されませんである場合、ドライバーは SQLSTATE 01S02 を返します (オプションの変更された値) と属性を元の値にリセットします。|  
|SQL_ATTR_METADATA_ID (ODBC 3.0)|カタログ関数の文字列引数の処理方法を決定する SQLULEN 値です。<br /><br /> 場合は SQL_TRUE、カタログ関数の文字列引数は、識別子として扱われます。 大文字と小文字は大きくありません。 規格文字列の場合、ドライバーが末尾のスペースを削除し、文字列が大文字に折りたたまれません。 区切られた文字列の場合は、ドライバーは、先頭または末尾の空白を削除し、受け取る文字どおり区切り記号の間は何でもは。 これらの引数の 1 つは、null ポインターに設定されている、関数を返します SQL_ERROR と SQLSTATE HY009 (null ポインターの使い方が正しくありません)。<br /><br /> 場合は SQL_FALSE、カタログ関数の文字列引数は、識別子としては扱われません。 大文字と小文字は重要です。 含めることができますか、文字列、検索パターンもそうでない引数に応じて。<br /><br /> 既定値は、SQL_FALSE です。<br /><br /> *TableType*の引数**SQLTables**値の一覧を取得するは、この属性して影響はありません。<br /><br /> SQL_ATTR_METADATA_ID は、接続レベルで設定することもできます。 (して SQL_ATTR_ASYNC_ENABLE はも、接続属性の唯一のステートメント属性) です。<br /><br /> 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)です。|  
|SQL_ATTR_NOSCAN (ODBC 1.0)|ドライバーが SQL 文字列のエスケープ シーケンスをスキャンするかどうかを示す SQLULEN 値:<br /><br /> SQL_NOSCAN_OFF ドライバー スキャン (既定値) のエスケープ シーケンスの SQL 文字列を = です。<br /><br /> SQL_NOSCAN_ON = SQL 文字列のエスケープ シーケンスのスキャン、ドライバーは行いません。 代わりに、ドライバーは、データ ソースに直接、ステートメントを送信します。<br /><br /> 詳細については、次を参照してください。 [odbc エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)です。|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR (ODBC 3.0)|SQLULEN * 動的パラメーターのバインドの変更へのポインターに追加のオフセットを示す値。 ドライバーにポインターを逆参照し、遅延フィールド (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR) 記述子レコード内のそれぞれに逆参照された値を追加し、新しいポインター値を使用してこのフィールドが null 以外の場合は、バインドするときにします。 設定されている既定によって null にします。<br /><br /> バインドのオフセットは常に、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR フィールドを直接追加します。 別の値にオフセットを変更すると、新しい値は、記述子フィールドの値に直接追加されます。 フィールドの値と、以前のオフセットには、新しいオフセットは追加されません。<br /><br /> 詳細については、次を参照してください。[パラメーターをオフセット バインド](../../../odbc/reference/develop-app/parameter-binding-offsets.md)です。<br /><br /> このステートメント属性を設定すると、APD ヘッダー SQL_DESC_BIND_OFFSET_PTR フィールドが設定されます。|  
|SQL_ATTR_PARAM_BIND_TYPE (ODBC 3.0)|動的パラメーターを使用するバインディングの方向を示す SQLULEN 値。<br /><br /> このフィールドは、列方向のバインドを選択する SQL_PARAM_BIND_BY_COLUMN (既定) に設定されます。<br /><br /> 行方向のバインドを選択するには、このフィールドは構造体、または一連の動的パラメーターをバインドするバッファーのインスタンスの長さに設定されます。 この長さは、すべてのバインドされたパラメーターと構造体またはバインドされたパラメーターのアドレスは、指定した長さでインクリメントは、ときに、結果は、次に、同じパラメーターの先頭にポイントすることを確認するバッファーの埋め込み領域を含める必要があります。パラメーターのセット。 使用する場合、 *sizeof* ANSI c 演算子は、この動作が保証されます。<br /><br /> 詳細については、次を参照してください。[パラメーターの配列のバインド](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)です。<br /><br /> このステートメント属性を設定すると、APD ヘッダー SQL_DESC_ BIND_TYPE フィールドが設定されます。|  
|SQL_ATTR_PARAM_OPERATION_PTR (ODBC 3.0)|SQLUSMALLINT \* SQLUSMALLINT 値の配列を指す値を SQL ステートメントの実行中にパラメーターを無視するために使用します。 各値は、(実行されるパラメーター) の SQL_PARAM_PROCEED または SQL_PARAM_IGNORE (用、パラメーターが無視されます) のいずれかに設定されます。<br /><br /> SQL_PARAM_IGNORE に APD の SQL_DESC_ARRAY_STATUS_PTR が指す配列で状態値を設定して、パラメーターのセットを処理中に無視できます。 SQL_PARAM_PROCEED にその状態の値が設定されている場合、または配列内の要素が設定されていない場合は、パラメーターのセットが処理されます。<br /><br /> このステートメント属性は、null ポインターでいる場合、ドライバーは返しませんパラメーター状態の値を設定できます。 この属性は、いつでも設定できますが、新しい値は、次回まで使用されません**SQLExecDirect**または**SQLExecute**と呼びます。<br /><br /> バインドされたパラメーターがない場合に、この属性は無視されます。<br /><br /> 詳細については、次を参照してください。[パラメーターの配列を使用して](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)です。<br /><br /> このステートメント属性を設定すると、APD ヘッダー SQL_DESC_ARRAY_STATUS_PTR フィールドが設定されます。|  
|SQL_ATTR_PARAM_STATUS_PTR (ODBC 3.0)|SQLUSMALLINT\*値 SQLUSMALLINT の配列を指す値が呼び出しの後にパラメーター値の行ごとの状態情報を含む**SQLExecute**または**SQLExecDirect**です。 このフィールドは、PARAMSET_SIZE が 1 より大きい場合にのみ必要です。<br /><br /> 状態の値は、次の値を含めることができます。<br /><br /> SQL_PARAM_SUCCESS: SQL ステートメントが正常にこのパラメーターのセットの実行。<br /><br /> SQL_PARAM_SUCCESS_WITH_INFO: このパラメーターのセットに対して SQL ステートメントが実行されましたが正常にただし、警告情報は、診断データの構造体で使用できます。<br /><br /> SQL_PARAM_ERROR: このパラメーターのセットの処理でエラーが発生しました。 追加のエラーについては、診断データの構造体です。<br /><br /> SQL_PARAM_UNUSED: このパラメーターが設定された、使用可能性のあるためにいくつか前のパラメーター セットには、以降の処理を中止エラーが発生しました。 または、SQL_ATTR_PARAM_ で指定された配列内のパラメーターのセット SQL_PARAM_IGNORE が設定されているためOPERATION_PTR です。<br /><br /> SQL_PARAM_DIAG_UNAVAILABLE: ドライバーは、パラメーターの配列をモノリシックな単位として処理し、のでこのレベルのエラー情報を生成しません。<br /><br /> このステートメント属性は、null ポインターでいる場合、ドライバーは返しませんパラメーター状態の値を設定できます。 この属性は、いつでも設定できますが、新しい値は、次回まで使用されません**SQLExecute**または**SQLExecDirect**と呼びます。 この属性の設定は影響ドライバーによって実装される出力パラメーターの動作に注意してください。<br /><br /> 詳細については、次を参照してください。[パラメーターの配列を使用して](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)です。<br /><br /> このステートメント属性を設定すると、IPD ヘッダー SQL_DESC_ARRAY_STATUS_PTR フィールドが設定されます。|  
|SQL_ATTR_PARAMS_PROCESSED_PTR (ODBC 3.0)|SQLULEN\*を処理した、エラーのセットを含むパラメーターのセットの数を返すバッファーを指すレコードのフィールドです。 これが null ポインターの場合、数値は返されません。<br /><br /> このステートメント属性を設定すると、IPD ヘッダー SQL_DESC_ROWS_PROCESSED_PTR フィールドが設定されます。<br /><br /> 場合に呼び出し**SQLExecDirect**または**SQLExecute**ことでこの属性が指すバッファーがいっぱいになった返さない SQL_SUCCESS または SQL_SUCCESS_WITH_INFO、バッファーの内容は未定義です。<br /><br /> 詳細については、次を参照してください。[パラメーターの配列を使用して](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)です。|  
|SQL_ATTR_PARAMSET_SIZE (ODBC 3.0)|各パラメーターの値の数を指定する SQLULEN 値です。 SQL_ATTR_PARAMSET_SIZE が 1 より大きい場合は、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および APD の SQL_DESC_OCTET_LENGTH_PTR 配列をポイントします。 各配列の基数は、このフィールドの値と同じです。<br /><br /> バインドされたパラメーターがない場合に、この属性は無視されます。<br /><br /> 詳細については、次を参照してください。[パラメーターの配列を使用して](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)です。<br /><br /> このステートメント属性を設定すると、APD ヘッダー SQL_DESC_ARRAY_SIZE フィールドが設定されます。|  
|SQL_ATTR_QUERY_TIMEOUT (ODBC 1.0)|アプリケーションに返す前に実行する SQL ステートメントを待機する秒数に対応する SQLULEN 値です。 場合*ValuePtr*は 0 (既定値) に等しい、タイムアウトが存在しません。<br /><br /> 指定したタイムアウト時間がデータ ソースのタイムアウトの最大値を超えていますまたは最小のタイムアウトよりも小さい場合**SQLSetStmtAttr**その値に置き換えられ、SQLSTATE 01S02 を返します (オプションの値が変更されました)。<br /><br /> アプリケーションを呼び出す必要がありますいないことに注意してください**SQLCloseCursor**場合、ステートメントを再利用する、**選択**ステートメントがタイムアウトしました。<br /><br /> このステートメント属性に設定されているクエリ タイムアウトは、同期および非同期の両方のモードで有効です。|  
|SQL_ATTR_RETRIEVE_DATA (ODBC 2.0)|SQLULEN 値の場合:<br /><br /> SQL_RD_ON = **SQLFetchScroll**と ODBC 3*.x*、 **SQLFetch**指定した場所にカーソルを配置した後にデータを取得します。 これは既定値です。<br /><br /> SQL_RD_OFF = **SQLFetchScroll**と ODBC 3*.x*、 **SQLFetch**カーソルを配置した後にデータを取得できません。<br /><br /> アプリケーションには、SQL_RETRIEVE_DATA SQL_RD_OFF に設定により、行が存在するか、行を取得する操作のオーバーヘッドは要しません行のブックマークを取得することを検証できます。 詳細については、次を参照してください。[のスクロールとフェッチ行](../../../odbc/reference/develop-app/scrolling-and-fetching-rows-odbc.md)です。<br /><br /> 開いているカーソル; でこの属性の値を設定することができます。ただし、設定がすぐに反映されませんである場合、ドライバーは SQLSTATE 01S02 を返します (オプションの変更された値) と属性を元の値にリセットします。|  
|SQL_ATTR_ROW_ARRAY_SIZE (ODBC 3.0)|各呼び出しによって返される行の数を指定する SQLULEN 値**SQLFetch**または**SQLFetchScroll**です。 一括ブックマーク操作で使用されるブックマーク配列内の行の数も**SQLBulkOperations**です。 既定値は 1 です。<br /><br /> ドライバーがその値に置き換えられ、SQLSTATE 01S02 を返します、指定した行セット サイズは、データ ソースによってサポートされる最大の行セットのサイズを超えている場合 (オプションの値が変更されました)。<br /><br /> 詳細については、次を参照してください。[行セット サイズ](../../../odbc/reference/develop-app/rowset-size.md)です。<br /><br /> このステートメント属性を設定すると、ARD ヘッダー SQL_DESC_ARRAY_SIZE フィールドが設定されます。|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR (ODBC 3.0)|SQLULEN * 列のデータのバインドの変更へのポインターに追加のオフセットを示す値。 ドライバーにポインターを逆参照し、遅延フィールド (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR) 記述子レコード内のそれぞれに逆参照された値を追加し、新しいポインター値を使用してこのフィールドが null 以外の場合は、バインドするときにします。 設定されている既定によって null にします。<br /><br /> このステートメント属性を設定すると、ARD ヘッダー SQL_DESC_BIND_OFFSET_PTR フィールドが設定されます。|  
|SQL_ATTR_ROW_BIND_TYPE (ODBC 1.0)|バインディングの向きを設定する SQLULEN 値ときに使用する**SQLFetch**または**SQLFetchScroll**関連するステートメントで呼び出されるとします。 列方向のバインドは、値を SQL_BIND_BY_COLUMN に設定で選択されます。 行方向のバインドは、構造体または結果の列のバインド先のバッファーのインスタンスの長さの値の設定で選択されます。<br /><br /> すべてのバインドされた列および構造体またはバインドされた列のアドレスの指定した長さでインクリメント時に、結果が th 内の同じ列の先頭を指すがバッファーの埋め込み用の領域を含める必要があります、長さが指定されている場合次の行を e です。 使用する場合、 **sizeof**構造体または共用体では、ANSI C 演算子は、この動作が保証されます。<br /><br /> 既定のバインディングの向きは、列方向のバインド**SQLFetch**と**SQLFetchScroll**です。<br /><br /> 詳細については、次を参照してください。[ブロック カーソルで使用するための列のバインド](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)です。<br /><br /> このステートメント属性を設定すると、ARD ヘッダー SQL_DESC_BIND_TYPE フィールドが設定されます。|  
|SQL_ATTR_ROW_NUMBER (ODBC 2.0)|全体の結果の現在の行の数を表す SQLULEN 値を設定します。 現在の行の数を特定することはできませんか、現在の行がない場合、ドライバーは、0 を返します。<br /><br /> この属性への呼び出しによって取得できる**SQLGetStmtAttr**への呼び出しでは設定されませんが、 **SQLSetStmtAttr**です。|  
|SQL_ATTR_ROW_OPERATION_PTR (ODBC 3.0)|SQLUSMALLINT \* SQLUSMALLINT 値の配列を指す値を使用して一括操作中に行を無視するために使用**SQLSetPos**です。 各値は、(一括操作に含まれる行) の SQL_ROW_PROCEED または SQL_ROW_IGNORE (用、一括操作から除外するのには、行) のいずれかに設定されます。 (の呼び出し中に、この配列を使用して行を無視することはできません**SQLBulkOperations**)。<br /><br /> このステートメント属性は、行の状態の値は、ドライバーの場合に返されません、null ポインターを設定できます。 この属性は、いつでも設定できますが、新しい値は、次回まで使用されません**SQLSetPos**と呼びます。<br /><br /> 詳細については、次を参照してください。 [SQLSetPos で行セット内の行の更新](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)と[SQLSetPos を含む行セットの行を削除する](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)です。<br /><br /> このステートメント属性を設定すると、ARD で SQL_DESC_ARRAY_STATUS_PTR フィールドが設定されます。|  
|SQL_ATTR_ROW_STATUS_PTR (ODBC 3.0)|SQLUSMALLINT\*値 SQLUSMALLINT の配列を指す値が呼び出しの後に行の状態値を含む**SQLFetch**または**SQLFetchScroll**です。 配列には、行セットの行数が多くの要素があります。<br /><br /> このステートメント属性は、行の状態の値は、ドライバーの場合に返されません、null ポインターを設定できます。 この属性は、いつでも設定できますが、新しい値は、次回まで使用されません**SQLBulkOperations**、 **SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**と呼びます。<br /><br /> 詳細については、次を参照してください。[フェッチされた行の数と状態](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)です。<br /><br /> このステートメント属性を設定すると、IRD のヘッダーに SQL_DESC_ARRAY_STATUS_PTR フィールドが設定されます。<br /><br /> この属性は、ODBC 2 によってもマップ*.x*へのドライバー、 *rgbRowStatus*配列への呼び出しで**SQLExtendedFetch**です。|  
|SQL_ATTR_ROWS_FETCHED_PTR (ODBC 3.0)|SQLULEN\*呼び出しの後にフェッチされた行の数を取得するためのバッファーを指す値**SQLFetch**または**SQLFetchScroll**; 行われた一括操作によって影響を受ける行の数呼び出しによって**SQLSetPos**で、*操作*SQL_REFRESH; またはを実行する一括操作によって影響を受ける行の数の引数**SQLBulkOperations**. この数には、エラー行が含まれます。<br /><br /> 詳細については、次を参照してください。[フェッチされた行の数と状態](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)です。<br /><br /> このステートメント属性を設定すると、IRD のヘッダーに SQL_DESC_ROWS_PROCESSED_PTR フィールドが設定されます。<br /><br /> 場合に呼び出し**SQLFetch**または**SQLFetchScroll**ことでこの属性が指すバッファーがいっぱいになった返さない SQL_SUCCESS または SQL_SUCCESS_WITH_INFO、バッファーの内容は未定義です。|  
|SQL_ATTR_SIMULATE_CURSOR (ODBC 2.0)|配置をシミュレートするドライバーが update および delete ステートメントであるかどうかを示す SQLULEN 値は、このようなステートメントが 1 つだけの単一行に影響することを保証します。<br /><br /> 位置指定更新をシミュレートを delete ステートメントは、ほとんどのドライバーが、検索した構築**更新**または**削除**ステートメントを含む、**場所**句を指定する、現在の行の各列の値です。 これらの列は、一意のキーを構成、しない限り、このようなステートメントに複数行に影響します。<br /><br /> このようなステートメントが 1 行のみに影響することを保証するには、ドライバーは一意のキーの列を決定し、結果セットにこれらの列を追加します。 アプリケーションでは、結果セット内の列が一意のキーを構成することを保証する場合、ドライバーでは、これを行う必要はありません。 これにより、実行時間が低下します。<br /><br /> SQL_SC_NON_UNIQUE ドライバーを = がシミュレートされるという保証されません更新または位置指定 delete ステートメントが 1 つの行には影響そのためには、アプリケーションの責任です。 ステートメントが複数の行に影響する場合**SQLExecute**、 **SQLExecDirect**、または**SQLSetPos** SQLSTATE 01001 (カーソル操作 conflict) を返します。<br /><br /> SQL_SC_TRY_UNIQUE = シミュレートされた更新プログラムの配置を保証するためにドライバー試行またはステートメントに与える影響の 1 つだけ行を削除します。 ドライバーはこのようなステートメントを常に実行する場合など、複数の行に影響を与える可能性がある場合でも一意のキーはありません。 ステートメントが複数の行に影響する場合**SQLExecute**、 **SQLExecDirect**、または**SQLSetPos** SQLSTATE 01001 (カーソル操作 conflict) を返します。<br /><br /> SQL_SC_UNIQUE 位置指定更新をシミュレートしたドライバーの保証を = = またはステートメントに与える影響の 1 つだけ行を削除します。 ドライバーは特定のステートメントでは、これを保証できない場合**SQLExecDirect**または**SQLPrepare**はエラーを返します。<br /><br /> データ ソースは、ドライバーがカーソルをシミュレートできませんおよびネイティブ SQL が位置指定更新のサポート、および delete ステートメントを提供する場合は、SQL_SIMULATE_CURSOR の SQL_SC_UNIQUE が要求されたときに SQL_SUCCESS が返されます。 SQL_SC_TRY_UNIQUE または SQL_SC_NON_UNIQUE が要求される場合は、SQL_SUCCESS_WITH_INFO が返されます。 データ ソースが SQL_SC_TRY_UNIQUE レベルのサポートを提供し、ドライバーは、SQL_SC_TRY_UNIQUE および SQL_SUCCESS_WITH_INFO が返されます SQL_SC_NON_UNIQUE の SQL_SUCCESS が返されます。<br /><br /> ドライバーがさまざまなシミュレーション型に置き換えられ、SQLSTATE 01S02 を返します、指定されたカーソルのシミュレーションの種類は、データ ソースによってサポートされていない場合、(オプションの値が変更されました)。 SQL_SC_UNIQUE、ドライバーに置き換えます、SQL_SC_TRY_UNIQUE または SQL_SC_NON_UNIQUE の順序で。 SQL_SC_TRY_UNIQUE、ドライバーは SQL_SC_NON_UNIQUE を置き換えます。<br /><br /> 既定値は、SQL_SC_UNIQUE です。<br /><br /> 詳細については、次を参照してください。[をシミュレートする位置指定更新と削除ステートメント](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)です。|  
|SQL_ATTR_USE_BOOKMARKS (ODBC 2.0)|アプリケーションが、カーソルにブックマークを使用するかどうかを指定する SQLULEN 値:<br /><br /> SQL_UB_OFF = Off (既定)<br /><br /> SQL_UB_VARIABLE = アプリケーションは、カーソル、カーソルとブックマークを使用して、サポートされている場合、ドライバーは可変長のブックマークになります。 ODBC 3 SQL_UB_FIXED は推奨されなくなりました*.x*です。 ODBC 3*.x*アプリケーション必ず使用して可変長のブックマーク、ODBC 2 を使用する場合にも*.x*ドライバーのみの 4 バイトの固定長のブックマークをサポート)。 これは、固定長のブックマークが可変長のブックマークの特殊なケースのみであるためです。 ODBC 2 を使用するときに*.x* SQL_UB_FIXED にドライバーをドライバー マネージャーのマップ SQL_UB_VARIABLE です。<br /><br /> ブックマークをカーソルで使用するには、アプリケーション SQL_UB_VARIABLE 値を持つこの属性必要があります、カーソルを開く前に指定します。<br /><br /> 詳細については、次を参照してください。[を取得するブックマーク](../../../odbc/reference/develop-app/retrieving-bookmarks.md)です。|  
  
 [1] これらの関数は、記述子が、実装の記述子アプリケーション記述子ではない場合にのみ、非同期的に呼び出すことができます。  
  
 参照してください[列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)と[行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|接続属性の設定値を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|ステートメント属性の設定値を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|記述子の 1 つのフィールドを設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

