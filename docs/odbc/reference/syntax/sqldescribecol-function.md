---
title: "SQLDescribeCol 関数 |Microsoft ドキュメント"
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
- SQLDescribeCol
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeCol
helpviewer_keywords:
- SQLDescribeCol function [ODBC]
ms.assetid: eddef353-83f3-4a3c-8f24-f9ed888890a4
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a6fcf834f88a1ecc609b56a0f8f493ee5a3c1ab
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqldescribecol-function"></a>SQLDescribeCol 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLDescribeCol**結果の記述子を返します: 列名、型、列のサイズ、10 進数字、および null 値許容属性 —、結果内の 1 つの列に対して設定します。 この情報もは、IRD のフィールドにします。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLDescribeCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLCHAR *      ColumnName,  
      SQLSMALLINT    BufferLength,  
      SQLSMALLINT *  NameLengthPtr,  
      SQLSMALLINT *  DataTypePtr,  
      SQLULEN *      ColumnSizePtr,  
      SQLSMALLINT *  DecimalDigitsPtr,  
      SQLSMALLINT *  NullablePtr);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *ColumnNumber*  
 [入力]結果のデータの列数は、列の昇順に、1 から始まります順番に順序付けします。 *ColumnNumber*ブックマーク列を記述する引数が 0 に設定することもできます。  
  
 *ColumnName*  
 [出力]列名を取得するための null で終わるバッファーへのポインター。 この値は、IRD の SQL_DESC_NAME フィールドから読み取られます。 列が名前付きでない、または列名を特定することはできません、ドライバーは、空の文字列を返します。  
  
 場合*ColumnName* null、 *NameLengthPtr*はまだ文字 (文字データの null 終端文字を除く) の合計数を返しますが指すバッファーに返される使用可能な*ColumnName*です。  
  
 *BufferLength*  
 [入力]長さ、**ColumnName*文字バッファー。  
  
 *NameLengthPtr*  
 [出力]文字 (終端の null を除く) の合計数を返すバッファーへのポインターで返される使用可能な\* *ColumnName*です。 返される文字数がより大きいかに等しい場合*BufferLength*、内の列名\* *ColumnName*に切り捨てられます*BufferLength*null 終端文字の長さマイナスです。  
  
 *DataTypePtr*  
 [出力]列の SQL データ型を返すバッファーへのポインター。 この値は、IRD の SQL_DESC_CONCISE_TYPE フィールドから読み取られます。 内の値の 1 つ[SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)、または個々 のドライバーの SQL データ型。 データ型を特定できない場合、ドライバーは SQL_UNKNOWN_TYPE を返します。  
  
 ODBC 3 です。*x*、SQL_TYPE_DATE、SQL_TYPE_TIME、または SQL_TYPE_TIMESTAMP で返される *\*DataTypePtr*の日付、時刻、またはタイムスタンプ データ、ODBC 2 にそれぞれ;.*x*SQL_DATE、SQL_TIME、または SQL_TIMESTAMP が返されます。 ドライバー マネージャーでは、ODBC 2 時に、必須のマッピングを実行します。*x* ODBC 3 を利用するアプリケーション*。x*ドライバーまたは ODBC 3 *。x* ODBC 2 を利用するアプリケーション*。x*ドライバー。  
  
 ときに*ColumnNumber*と等しいで 0 (ブックマーク列)、sql_binary 型が返されます *\*DataTypePtr*の可変長のブックマークです。 (SQL_INTEGER は ODBC 3 でブックマークが使用されている場合に返されます。*x* ODBC 2 を使用するアプリケーション*。x*ドライバーまたは ODBC 2 *。x* ODBC 3 を使用するアプリケーション*。x*ドライバーです)。  
  
 これらのデータ型の詳細については、次を参照してください。 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型にします。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。  
  
 *ColumnSizePtr*  
 [出力]データ ソースのサイズ (文字) の列を返すバッファーへのポインター。 列のサイズを特定できない場合、ドライバーは、0 を返します。 列のサイズの詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。  
  
 *DecimalDigitsPtr*  
 [出力]データ ソースの列の 10 進数字の数を返すバッファーへのポインター。 10 進数字の数は、特定できないまたは適用されません、ドライバーは、0 を返します。 小数点以下桁数の詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。  
  
 *NullablePtr*  
 [出力]列が NULL 値を許容するかどうかを示す値を返すバッファーへのポインター。 この値は、IRD の SQL_DESC_NULLABLE フィールドから読み取られます。 値は次のいずれかになります。  
  
 SQL_NO_NULLS: この列は NULL 値を使用していません。  
  
 SQL_NULLABLE: 列は、NULL 値を許容します。  
  
 SQL_NULLABLE_UNKNOWN: ドライバーを特定できません列で NULL 値が許容されているかどうか。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLDescribeCol** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec**で、 *HandleType*sql_handle_stmt としての*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLDescribeCol**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|バッファー \* *ColumnName*列全体の名前を返す、列の名前は切り詰められましたために大きさが不十分です。 切り詰められていない列名の長さが返される **NameLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07005|準備されたステートメントがない、*カーソルの指定*|関連付けられているステートメント、 *StatementHandle*結果セットを返しませんでした。 記述する列がありませんでした。|  
|07009|無効な記述子のインデックス|引数の指定された値 (DM) *ColumnNumber*を 0 に等しい、SQL_ATTR_USE_BOOKMARKS ステートメントのオプションでした SQL_UB_OFF です。<br /><br /> 引数が指定された値*ColumnNumber*が結果セット内の列の数を超えています。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てに失敗|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数ではときに実行されている**SQLDescribeCol**が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM)、関数が呼び出された呼び出しの前に**SQLPrepare**、 **SQLExecute**、または、ステートメント ハンドルでのカタログ関数。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|引数の指定された値 (DM) *BufferLength*が 0 未満です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
 **SQLDescribeCol**によって返される任意の SQLSTATE を返すことができる**SQLPrepare**または**SQLExecute**後に呼び出されたときに**SQLPrepare** 前に**SQLExecute**にデータ ソースが、ステートメント ハンドルに関連付けられている SQL ステートメントを評価するときに依存します。  
  
 パフォーマンス上の理由から、アプリケーションを呼び出す必要がありますいない**SQLDescribeCol**ステートメントを実行する前にします。  
  
## <a name="comments"></a>コメント  
 アプリケーションを呼び出す通常**SQLDescribeCol**への呼び出し後**SQLPrepare**の前に、または後に関連付けられている呼び出し**SQLExecute**です。 アプリケーションが呼び出すことができますも**SQLDescribeCol**への呼び出し後**SQLExecDirect**です。 詳細については、次を参照してください。[結果セットのメタデータ](../../../odbc/reference/develop-app/result-set-metadata.md)です。  
  
 **SQLDescribeCol**列名、型、およびによって生成される長さを取得、**選択**ステートメントです。 列が、式の場合 **ColumnName*が空の文字列またはドライバーの定義済みの名前。  
  
> [!NOTE]  
>  ODBC をサポートしている SQL_NULLABLE_UNKNOWN、拡張機能として、グループを開くと SQL アクセス グループ呼び出しレベル インターフェイスの指定がのオプションを指定しない場合でも**SQLDescribeCol**です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|複数行のデータのフェッチ|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|結果の数を返すセットの列|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|実行のためのステートメントを準備します。|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

