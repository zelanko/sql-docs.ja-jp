---
title: 関数の記述 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c727f6b36930b0d2ad0d5a61592b83bcd4995426
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301172"
---
# <a name="sqldescribecol-function"></a>SQLDescribeCol 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **結果**セット内の 1 つの列に対して、結果記述子 (列名、型、列サイズ、10 進数、および NULL 値の許容可能性) を返します。 この情報は、IRD のフィールドでも使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *ColumnNumber*  
 [入力]結果データの列番号は、昇順で順次に並べ替え、1 から始まる。 *ColumnNumber*引数は、ブックマーク列を記述するために 0 に設定することもできます。  
  
 *[ColumnName]*  
 [出力]列名を返す NULL で終わるバッファーへのポインター。 この値は、IRD のSQL_DESC_NAMEフィールドから読み取られます。 列に名前が付いていない場合、または列名を判別できない場合、ドライバーは空の文字列を返します。  
  
 *列名*が NULL の場合 *、NameLengthPtr*は *、ColumnName*が指すバッファーで返される文字の合計数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]**列名*バッファーの長さ (文字数)。  
  
 *名前の長さプター*  
 [出力]\* *ColumnName*で返される文字の合計数 (NULL 終端を除く) を返すバッファーへのポインター。 戻り値の文字数が*BufferLength*以上の場合、\**列名*の列名は*BufferLength*から NULL 終端文字の長さを引いた値に切り捨てられます。  
  
 *データ型Ptr*  
 [出力]列の SQL データ・タイプを戻すバッファーへのポインター。 この値は、IRD のSQL_DESC_CONCISE_TYPEフィールドから読み取られます。 これは SQL[データ型](../../../odbc/reference/appendixes/sql-data-types.md)の値の 1 つ、またはドライバー固有の SQL データ型です。 データ型を特定できない場合、ドライバーはSQL_UNKNOWN_TYPEを返します。  
  
 ODBC 3 で。日付、時刻、またはタイムスタンプの*\*データのそれぞれについて、DataTypePtr*に*x*、SQL_TYPE_DATE、SQL_TYPE_TIME、またはSQL_TYPE_TIMESTAMPが返されます。ODBC 2 で使用します。*x*、SQL_DATE、SQL_TIME、またはSQL_TIMESTAMPが返されます。 ドライバー マネージャーは、ODBC 2 の場合に必要なマッピングを実行します。*x*アプリケーションは ODBC 3 で動作しています。*x*ドライバまたは ODBC 3 の場合。*x*アプリケーションは ODBC 2 で動作しています。*x*ドライバ。  
  
 *ColumnNumber*が 0 (ブックマーク列の場合) の場合、可変長ブックマークの場合は*\*DataTypePtr*にSQL_BINARYが返されます。 (ODBC 3 でブックマークが使用されている場合は、SQL_INTEGERが返されます。*x*アプリケーションは ODBC 2 で動作します。*x*ドライバまたは ODBC 2 を使用します。*x*アプリケーションは ODBC 3 で動作します。*x*ドライバ。  
  
 これらのデータ型の詳細については、「付録 D:[データ型](../../../odbc/reference/appendixes/sql-data-types.md)」の SQL データ型を参照してください。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。  
  
 *サイズ変更*  
 [出力]データ ソースの列のサイズ (文字数) を返すバッファーへのポインター。 列のサイズを決定できない場合、ドライバーは 0 を返します。 列サイズの詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。  
  
 *10 進数の桁数Ptr*  
 [出力]データ ソースの列の 10 進数の桁数を返すバッファーへのポインター。 小数点以下の桁数を判別できない場合、または適用できない場合、ドライバーは 0 を戻します。 小数点以下の桁数の詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。  
  
 *Null 可能なPtr*  
 [出力]列が NULL 値を許可するかどうかを示す値を返すバッファーへのポインター。 この値は、IRD の SQL_DESC_NULLABLE フィールドから読み取られます。 値は次のいずれかです。  
  
 SQL_NO_NULLS: 列に NULL 値を指定できません。  
  
 SQL_NULLABLE: 列は NULL 値を許可します。  
  
 SQL_NULLABLE_UNKNOWN: 列が NULL 値を許可するかどうかをドライバーが判断できません。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLDescribeCol**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返す場合は、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLDescribeCol**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|ColumnName\**ColumnName*バッファーの大きさが列名全体を返すほど大きくなかったので、列名が切り捨てられました。 切り捨てられていない列名の長さは、 **NameLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07005|準備済みステートメントは*カーソル指定ではありません。*|*ステートメント ハンドル*に関連付けられたステートメントが結果セットを返しませんでした。 説明する列はありませんでした。|  
|07009|記述子インデックスが無効です|(DM)*引数 ColumnNumber*に指定された値が 0 であり、SQL_ATTR_USE_BOOKMARKSステートメント オプションがSQL_UB_OFF。<br /><br /> 引数*ColumnNumber*に指定された値が、結果セット内の列数より大きかった。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLDescribeCol**が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM) ステートメント ハンドルで SQLPrepare **、SQLExecute、** またはカタログ関数を呼び出す前に、関数が呼び出されました。 **SQLPrepare**<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*BufferLength*に指定された値が 0 より小さかった。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
 **SQLPrepare** **の後および**SQL**実行の**前に呼び出されたときに**SQLPrepare**または**SQL**実行によって返される SQLSTATE を返すことができます。  
  
 パフォーマンス上の理由から、アプリケーションはステートメントを実行する前に**SQLDescribeCol**を呼び出してはいけません。  
  
## <a name="comments"></a>説明  
 アプリケーションは通常 **、SQLPrepare**の呼び出しの後、および関連付けられた**SQLExecute**の呼び出しの前または後に**SQLDescribeCol**を呼び出します。 アプリケーションは **、SQLExecDirect**への呼び出しの後に**SQLDescribeCol**を呼び出すこともできます。 詳細については、「[結果セットのメタデータ](../../../odbc/reference/develop-app/result-set-metadata.md)」を参照してください。  
  
 **SELECT**ステートメントによって生成された列名、型、および長さを取得します**SELECT**。 列が式の場合、**ColumnName*は空の文字列またはドライバー定義の名前のいずれかです。  
  
> [!NOTE]  
>  ODBC では、オープン グループおよび SQL アクセス グループ呼び出しレベル インターフェイスの仕様では**SQLDescribeCol**のオプションが指定されていない場合でも、ODBC は拡張としてSQL_NULLABLE_UNKNOWNをサポートしています。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|複数行のデータのフェッチ|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|結果セット列の数を返す|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|実行のためのステートメントの準備|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
