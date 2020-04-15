---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColAttribute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColAttribute
helpviewer_keywords:
- SQLColAttribute function [ODBC]
ms.assetid: 8c45c598-cb01-4789-a571-e93619a18ed9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c94de3dfc7036277f8be56c401326cdab07a9606
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301292"
---
# <a name="sqlcolattribute-function"></a>SQLColAttribute 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **結果**セット内の列の記述子情報を返します。 記述子情報は、文字ストリング、記述子依存値、または整数値として戻されます。  
  
> [!NOTE]  
>  ドライバー マネージャーは、ODBC 3 のときにこの関数をマップする方法の詳細について。*x*アプリケーションは ODBC 2 で動作しています。*x*ドライバについては、「[アプリケーションの下位互換性のための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLColAttribute (  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ColumnNumber,  
      SQLUSMALLINT    FieldIdentifier,  
      SQLPOINTER      CharacterAttributePtr,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLLEN *        NumericAttributePtr);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *ColumnNumber*  
 [入力]フィールド値を取得する IRD 内のレコードの番号。 この引数は、昇順の列順で並べ替えられた結果データの列番号に対応し、1 から始まります。 列は任意の順序で記述できます。  
  
 この引数には列 0 を指定できますが、SQL_DESC_TYPEとSQL_DESC_OCTET_LENGTH以外のすべての値は未定義の値を返します。  
  
 *FieldIdentifier*  
 [入力]記述子ハンドル。 このハンドルは、IRD 内のどのフィールドを照会するかを定義します (たとえば、SQL_COLUMN_TABLE_NAME)。  
  
 *CharacterAttributePtr*  
 [出力]IRD の*列番号*行の*フィールド識別子*フィールドの値を返すバッファーへのポインター (フィールドが文字列の場合)。 それ以外の場合、フィールドは使用されません。  
  
 *CharacterAttributePtr*が NULL の場合 *、StringLengthPtr*は、引き続き *、CharacterAttributePtr*が指すバッファーで返すバイトの総数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]*フィールド識別子*が ODBC で定義されたフィールド*で、文字*文字列またはバイナリ バッファを指す場合、この引数は\**CharacterAttributePtr*の長さである必要があります。 *フィールド識別子*が ODBC で定義されたフィールド\*で、*文字属性*Ptr が整数の場合、このフィールドは無視されます。 文字属性Ptr が Unicode 文字列の場合 **(SQLColAttributeW**を呼び出すとき *)、BufferLength*引数は偶数でなければなりません。 * \** *FieldIdentifier*がドライバー定義フィールドの場合、アプリケーションは *、BufferLength*引数を設定してドライバー マネージャーにフィールドの性質を示します。 *バッファー長*には、次の値を指定できます。  
  
-   *CharacterAttributePtr*がポインターへのポインターの場合 *、BufferLength*は値をSQL_IS_POINTER必要があります。  
  
-   文字文字列へのポインターである*場合*、*バッファー長*はバッファーの長さです。  
  
-   *CharacterAttributePtr*がバイナリ バッファへのポインタである場合、アプリケーションは SQL_LEN_BINARY_ATTR(*長さ*) マクロの結果を*BufferLength*に格納します。 この場合は、負の値を*BufferLength*に配置します。  
  
-   *CharacterAttributePtr*が固定長データ型へのポインターである場合、*バッファー長*は、SQL_IS_INTEGER、SQL_IS_UNINTEGER、SQL_SMALLINT、または SQLUSMALLINT のいずれかである必要があります。  
  
 *文字列を長くします。*  
 [出力]**CharacterAttributePtr*で返されるバイトの総数 (文字データの NULL 終了バイトを除く) を返すバッファーへのポインター。  
  
 文字データの場合、返されるバイト数が*BufferLength*以上の場合\**、CharacterAttributePtr*の記述子情報は*BufferLength*から null 終端文字の長さを引いた値に切り捨てられ、ドライバーによって null で終了します。  
  
 その他のすべてのデータ型の*場合、BufferLength*の値は無視され、ドライバーは **CharacterAttributePtr*のサイズが 32 ビットであると想定します。  
  
 *属性の設定*  
 [出力]IRD の*列番号*行の*FieldIdentifier*フィールドに値を返す整数バッファーへのポインター (フィールドがSQL_DESC_COLUMN_LENGTHなどの数値記述子型の場合)。 それ以外の場合、フィールドは使用されません。 一部のドライバは、下位の 32 ビットまたは 16 ビットのバッファしか書き込みず、上位ビットは変更しないままにする場合があります。 したがって、アプリケーションはこの関数を呼び出す前に値を 0 に初期化する必要があります。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLColAttribute**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返す場合、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec***を呼*び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLColAttribute**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|バッファー \* *CharacterAttributePtr*は文字列値全体を返すのに十分な大きさがなかったので、文字列値が切り捨てられました。 切り捨てられていない文字列値の長さは、 **StringLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07005|準備済みステートメントは*カーソル指定ではありません。*|*ステートメント ハンドル*に関連付けられているステートメントは結果セットを返さなかったし、*フィールド識別子*がSQL_DESC_COUNTされませんでした。 説明する列はありませんでした。|  
|07009|記述子インデックスが無効です|(DM) *ColumnNumber*に指定された値が 0 に等し、SQL_ATTR_USE_BOOKMARKSステートメント属性がSQL_UB_OFFされました。<br /><br /> 引数*ColumnNumber*に指定された値が、結果セット内の列数より大きかった。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 診断データ構造体から**SQLGetDiagField**によって返されるエラー メッセージは、エラーとその原因を記述します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この aynchronous 関数は、SQLColAttribute が呼び出されたときにまだ実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 関数は、ステートメント*ハンドル*の**SQLPrepare** **、SQLExecDirect**、またはカタログ関数を呼び出す前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM)*\*文字属性Ptr*は文字列であり、*バッファー長*は 0 未満でしたが、SQL_NTSと等しくありません。|  
|HY091|記述子フィールド ID が無効です|*引数 FieldIdentifier*に指定された値は、定義された値の 1 つではなく、実装で定義された値ではありませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|ドライバが不可能|*引数 FieldIdentifier*に指定された値は、ドライバーによってサポートされていません。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
 **SQLPrepare の**後および**SQL 実行の**前に呼び出された場合 **、SQLColAttribute**は、データ ソースが*ステートメント ハンドル*に関連付けられた SQL ステートメントを評価するタイミングに応じて **、SQLPrepare**または**SQLExecute**によって返される可能性のある SQLSTATE を返すことができます。  
  
 パフォーマンス上の理由から、アプリケーションはステートメントを実行する前に**SQLColAttribute**を呼び出す必要があります。  
  
## <a name="comments"></a>説明  
 アプリケーションが**SQLColAttribute**によって返される情報をどのように使用するかについては、「[結果セットのメタデータ](../../../odbc/reference/develop-app/result-set-metadata.md)」を参照してください。  
  
 **情報**を返す\*値*は、数値属性の Ptr*または\**文字属性 Ptr*のいずれかでです。 整数情報は、SQLLEN 値として\**数値属性Ptr*に返されます。その他の形式の情報はすべて\**、 CharacterAttributePtr*に返されます。 情報が\**返*されると、ドライバーは*文字属性 Ptr*、*バッファー長*、および*文字列長Ptr*を無視します。 情報が\**返される場合*は、ドライバーは *、数値属性Ptr*を無視します。  
  
 **IRD の**記述子フィールドから値を返します。 この関数は、記述子ハンドルではなく、ステートメント ハンドルを使用して呼び出されます。 このセクションで後述する*フィールド識別子*の値の**SQLColAttribute**によって返される値は、適切な IRD ハンドルを使用して**SQLGetDescField**を呼び出すことによっても取得できます。  
  
 現在定義されている記述子フィールド、それらのフィールドが導入された ODBC のバージョン、およびそれらの情報が返される引数については、このセクションの後半で説明します。さまざまなデータ ソースを利用するために、ドライバーによって、より多くの記述子の型を定義できます。  
  
 ODBC 3。*x*ドライバーは、記述子フィールドの各値を返す必要があります。 記述子フィールドがドライバーまたはデータ ソースに適用されない場合、特に明記されていない限り、ドライバーは\* *StringLengthPtr*で 0 を返すか、 **CharacterAttributePtr*に空の文字列を返します。  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 ODBC 3.*x*関数**SQLColAttribute は**、非推奨の ODBC 2 を置き換えます。*x*関数**SQLCol 属性**。 SQL**の属性**を**SQLCol 属性**にマップする場合 (ODBC 2 の場合。*x*アプリケーションは ODBC 3 で動作しています。*x*ドライバー)、または**SQLCol 属性を SQLCol 属性**にマッピングする **(ODBC** 3 の場合)。*x*アプリケーションは ODBC 2 で動作しています。*x*ドライバー) ドライバードライバーは、次のように *、フィールド識別子*の値を渡すか、新しい値にマップするか、エラーを返します。  
  
> [!NOTE]  
>  ODBC 3 の*フィールド識別子*の値で使用されるプレフィックス。*x*は ODBC 2 で使用されていたものから変更されました。*x .* 新しいプレフィックスは "SQL_DESC" です。古いプレフィックスは "SQL_COLUMN" でした。  
  
-   ODBC 2 の **#define**値の場合。*x* *フィールド識別子*は ODBC 3 の **#define**値と同じです。*x* *フィールド識別子*を指定すると、関数呼び出しの値が渡されます。  
  
-   ODBC 2 の **#define**値。*x* *フィールド識別子*SQL_COLUMN_LENGTH、SQL_COLUMN_PRECISION、およびSQL_COLUMN_SCALEは、ODBC 3 の **#define**値とは異なります。*x* *フィールド識別子SQL_DESC_PRECISION、SQL_DESC_SCALE、* およびSQL_DESC_LENGTH。 ODBC 2。*x*ドライバは ODBC 2 をサポートするだけで済む。*x*値。 ODBC 3。*x*ドライバーは、これら 3 つの*フィールド識別子*の"SQL_COLUMN"と"SQL_DESC"の両方の値をサポートする必要があります。 精度、小数点以下桁数、および長さが ODBC 3 で定義されるのが異なるため、これらの値は異なります。*x*は ODBC 2 の場合と比べてあります。*x .* 詳細については、「[列サイズ、10 進数、オクテット長の転送、および表示サイズ」を参照してください](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。  
  
-   ODBC 2 の **#define**値の場合。*x* *フィールド識別子*は ODBC 3 の **#define**値とは異なります。*x* *フィールド識別子*は、COUNT、NAME、および NULLABLE 値で発生すると、関数呼び出しの値が対応する値にマップされます。 たとえば、SQL_COLUMN_COUNTはSQL_DESC_COUNTにマップされ、SQL_DESC_COUNTはマッピングの方向に応じてSQL_COLUMN_COUNTにマップされます。  
  
-   *フィールド識別子*が ODBC 3 の新しい値の場合。*x*に対して、ODBC 2 に対応する値が存在しません。*x*の場合、ODBC 3 の場合はマップされません。*x*アプリケーションは、ODBC 2 で**SQLCol 属性**の呼び出しで使用します。*x*ドライバー、および呼び出しは、SQLSTATE HY091 (無効な記述子フィールド識別子) を返します。  
  
 次の表は **、SQLColAttribute**によって返される記述子の型を示しています。 *値*の型は**SQLLEN\*** です。  
  
|*FieldIdentifier*|Information<br /><br /> に戻される|説明|  
|-----------------------|---------------------------------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE (ODBC 1.0)|*属性の設定*|列が自動増分列の場合にSQL_TRUEします。<br /><br /> SQL_FALSEカラムが自動増分カラムでないか、数値でない場合に使用します。<br /><br /> このフィールドは、数値データ型列にのみ有効です。 アプリケーションは、オートインクリメント列を含む行に値を挿入できますが、通常は列の値を更新することはできません。<br /><br /> 挿入がオートインクリメント列に作成されると、挿入時に一意の値が列に挿入されます。 増分は定義されていませんが、データ ソース固有です。 アプリケーションは、オートインクリメント列が特定のポイントで開始されるか、特定の値で増分されると想定しないでください。|  
|SQL_DESC_BASE_COLUMN_NAME (ODBC 3.0)|*CharacterAttributePtr*|結果セット列の基本列名。 ベース列名が存在しない場合 (式の列の場合)、この変数には空の文字列が含まれます。<br /><br /> この情報は、読み取り専用フィールドである IRD のSQL_DESC_BASE_COLUMN_NAMEレコード・フィールドから戻されます。|  
|SQL_DESC_BASE_TABLE_NAME (ODBC 3.0)|*CharacterAttributePtr*|列を含むベース テーブルの名前。 ベース テーブル名を定義できない場合、または適用できない場合、この変数には空の文字列が含まれます。<br /><br /> この情報は、読み取り専用フィールドである IRD のSQL_DESC_BASE_TABLE_NAMEレコード・フィールドから戻されます。|  
|SQL_DESC_CASE_SENSITIVE (ODBC 1.0)|*属性の設定*|列が照合順序および比較で大文字と小文字を区別する場合にSQL_TRUEします。<br /><br /> 列が照合順序および比較で大文字と小文字を区別する場合、または非文字として扱われる場合は、SQL_FALSEします。|  
|SQL_DESC_CATALOG_NAME (ODBC 2.0)|*CharacterAttributePtr*|列を含むテーブルのカタログ。 列が式の場合、または列がビューの一部である場合、戻り値は実装で定義されます。 データ ソースがカタログをサポートしていない場合、またはカタログ名を判別できない場合は、空の文字列が返されます。 この VARCHAR レコード・フィールドは 128 文字に制限されません。|  
|SQL_DESC_CONCISE_TYPE (ODBC 1.0)|*属性の設定*|簡潔なデータ型。<br /><br /> 日時データ型と間隔データ型の場合、このフィールドは簡潔なデータ型を返します。たとえば、SQL_TYPE_TIMEやSQL_INTERVAL_YEAR。 (詳細については、「付録 D:[データ型」の「データ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)」を参照してください。<br /><br /> この情報は、IRD のSQL_DESC_CONCISE_TYPEレコード・フィールドから戻されます。|  
|SQL_DESC_COUNT (ODBC 1.0)|*属性の設定*|結果セットで使用可能な列の数。 結果セットに列がない場合は 0 が返されます。 *引数 ColumnNumber*の値は無視されます。<br /><br /> この情報は、IRD のSQL_DESC_COUNTヘッダー・フィールドから返されます。|  
|SQL_DESC_DISPLAY_SIZE (ODBC 1.0)|*属性の設定*|列のデータを表示するために必要な最大文字数。 表示サイズの詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|SQL_DESC_FIXED_PREC_SCALE (ODBC 1.0)|*属性の設定*|列にデータ ソース固有の固定精度とゼロ以外のスケールがある場合にSQL_TRUEします。<br /><br /> 列にデータ ソース固有の固定精度とゼロ以外のスケールがない場合にSQL_FALSEします。|  
|SQL_DESC_LABEL (ODBC 2.0)|*CharacterAttributePtr*|列のラベルまたはタイトル。 たとえば、EmpName という名前の列に従業員名というラベルを付けたり、別名でラベル付けしたりできます。<br /><br /> 列にラベルがない場合は、その列名が返されます。 列にラベルが付いていない場合、空の文字列が返されます。|  
|SQL_DESC_LENGTH (ODBC 3.0)|*属性の設定*|文字ストリングまたはバイナリー・データ・タイプの最大または実際の文字長を表す数値。 これは、固定長データ・タイプの最大文字長、または可変長データ・タイプの実際の文字長です。 その値は、文字ストリングを終了する NULL 終了バイトを常に除外します。<br /><br /> この情報は、IRD のSQL_DESC_LENGTHレコード・フィールドから戻されます。<br /><br /> 長さの詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|SQL_DESC_LITERAL_PREFIX (ODBC 3.0)|*CharacterAttributePtr*|この VARCHAR(128) レコード フィールドには、ドライバーがこのデータ型のリテラルのプレフィックスとして認識する文字が含まれています。 このフィールドには、リテラルプレフィックスが適用されないデータ型の空の文字列が含まれています。 詳細については、「[リテラルプレフィックスとサフィックス](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)」を参照してください。|  
|SQL_DESC_LITERAL_SUFFIX (ODBC 3.0)|*CharacterAttributePtr*|この VARCHAR(128) レコード フィールドには、ドライバーがこのデータ型のリテラルのサフィックスとして認識する文字が含まれています。 このフィールドには、リテラルサフィックスが適用されないデータ型の空の文字列が含まれています。 詳細については、「[リテラルプレフィックスとサフィックス](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)」を参照してください。|  
|SQL_DESC_LOCAL_TYPE_NAME (ODBC 3.0)|*CharacterAttributePtr*|この VARCHAR(128) レコードフィールドには、データ型の通常名とは異なるデータ型のローカライズされた (ネイティブ言語) 名が含まれます。 ローカライズされた名前がない場合は、空の文字列が返されます。 このフィールドは表示のみを目的とします。 文字列の文字セットはロケールに依存し、通常はサーバーの既定の文字セットです。|  
|SQL_DESC_NAME (ODBC 3.0)|*CharacterAttributePtr*|列の別名 (該当する場合)。 列の別名が適用されない場合は、列名が返されます。 どちらの場合も、SQL_DESC_UNNAMEDはSQL_NAMEDに設定されます。 列名または列の別名がない場合は、空の文字列が返され、SQL_DESC_UNNAMEDSQL_UNNAMEDに設定されます。<br /><br /> この情報は、IRD のSQL_DESC_NAMEレコード・フィールドから戻されます。|  
|SQL_DESC_NULLABLE (ODBC 3.0)|*属性の設定*|列に NULL 値を指定できる場合は、null 可能SQL_。列に NULL 値がない場合はSQL_NO_NULLS。列が NULL 値を受け入れるかどうかが不明な場合はSQL_NULLABLE_UNKNOWN。<br /><br /> この情報は、IRD のSQL_DESC_NULLABLEレコード・フィールドから戻されます。|  
|SQL_DESC_NUM_PREC_RADIX (ODBC 3.0)|*属性の設定*|SQL_DESC_TYPE フィールドのデータ型が概数値データ型の場合、SQL_DESC_PRECISION フィールドにはビット数が含まれるため、この SQLINTEGER フィールドには 2 の値が含まれます。 SQL_DESC_TYPE フィールドのデータ型が正確な数値データ型の場合、SQL_DESC_PRECISION フィールドには 10 桁の桁数が含まれるため、このフィールドには 10 の値が含まれます。 このフィールドは、数値以外のすべてのデータ型に対して 0 に設定されます。|  
|SQL_DESC_OCTET_LENGTH (ODBC 3.0)|*属性の設定*|文字列またはバイナリ データ型の長さ (バイト単位)。 固定長の文字型またはバイナリ型の場合、これは実際のバイト長です。 可変長の文字型またはバイナリ型の場合、これはバイト単位の最大長です。 この値には、NULL 終端文字は含まれません。<br /><br /> この情報は、IRD のSQL_DESC_OCTET_LENGTHレコード・フィールドから戻されます。<br /><br /> 長さの詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|SQL_DESC_PRECISION (ODBC 3.0)|*属性の設定*|数値データ型の数値は、適用可能な精度を示します。 データ型SQL_TYPE_TIME、SQL_TYPE_TIMESTAMP、および時間間隔を表すすべての間隔データ型の場合、その値は秒の小数部のコンポーネントの適用可能な精度です。<br /><br /> この情報は、IRD のSQL_DESC_PRECISIONレコード・フィールドから戻されます。|  
|SQL_DESC_SCALE (ODBC 3.0)|*属性の設定*|数値データ型に適用できるスケールである数値。 DECIMAL および NUMERIC データ・タイプの場合、これは定義された位取りです。 他のすべてのデータ型に対しては定義されていません。<br /><br /> この情報は、IRD の SCALE レコード・フィールドから戻されます。|  
|SQL_DESC_SCHEMA_NAME (ODBC 2.0)|*CharacterAttributePtr*|列を含むテーブルのスキーマ。 列が式の場合、または列がビューの一部である場合、戻り値は実装で定義されます。 データ ソースがスキーマをサポートしていない場合、またはスキーマ名を決定できない場合は、空の文字列が返されます。 この VARCHAR レコード・フィールドは 128 文字に制限されません。|  
|SQL_DESC_SEARCHABLE (ODBC 1.0)|*属性の設定*|列を WHERE 句で使用できない場合にSQL_PRED_NONEします。 (これは、ODBC 2 のSQL_UNSEARCHABLE値と同じです。*x.*<br /><br /> SQL_PRED_CHAR列を WHERE 句で使用できるが、LIKE 述語と一緒にしか使用できない場合。 (これは、ODBC 2 のSQL_LIKE_ONLY値と同じです。*x.*<br /><br /> SQL_PRED_BASIC列を WHERE 句で使用し、LIKE 以外のすべての比較演算子を使用できる場合です。 (これは ODBC 2 のSQL_EXCEPT_LIKE値と同じです。*x.*<br /><br /> SQL_PRED_SEARCHABLE列を WHERE 句で使用できる場合は、任意の比較演算子を使用します。<br /><br /> SQL_LONGVARCHAR型およびSQL_LONGVARBINARY型の列は、通常、SQL_PRED_CHARを返します。|  
|SQL_DESC_TABLE_NAME (ODBC 2.0)|*CharacterAttributePtr*|列を含むテーブルの名前です。 列が式の場合、または列がビューの一部である場合、戻り値は実装で定義されます。<br /><br /> テーブル名を特定できない場合は、空の文字列が返されます。|  
|SQL_DESC_TYPE (ODBC 3.0)|*属性の設定*|SQL データ型を指定する数値。<br /><br /> *ColumnNumber*が 0 の場合、可変長のブックマークに対してSQL_BINARYが返され、固定長のブックマークに対してSQL_INTEGERが返されます。<br /><br /> 日時データ型および間隔データ型の場合、このフィールドは、SQL_DATETIME またはSQL_INTERVALの詳細データ型を返します。 (詳細については、「付録 D:[データ型」のデータ型識別子と記述子を](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)参照してください。<br /><br /> この情報は、IRD のSQL_DESC_TYPEレコード・フィールドから戻されます。 **注:** ODBC 2 に対して動作します。*x*ドライバを使用する場合は、代わりにSQL_DESC_CONCISE_TYPEを使用します。|  
|SQL_DESC_TYPE_NAME (ODBC 1.0)|*CharacterAttributePtr*|データ ソース依存のデータ型名。たとえば、"CHAR" "VARCHAR" "VARCHAR" "、"MONEY"、"ロング VARBINARY"、または "CHAR ( ) (ビット データ" の場合) などです。<br /><br /> 型が不明な場合は、空の文字列が返されます。|  
|SQL_DESC_UNNAMED (ODBC 3.0)|*属性の設定*|SQL_NAMEDまたはSQL_UNNAMED。 IRD のSQL_DESC_NAMEフィールドに列の別名または列名が含まれている場合は、SQL_NAMEDが返されます。 列名または列の別名がない場合は、SQL_UNNAMEDが返されます。<br /><br /> この情報は、IRD のSQL_DESC_UNNAMEDレコード・フィールドから戻されます。|  
|SQL_DESC_UNSIGNED (ODBC 1.0)|*属性の設定*|列が符号なし (または数値ではない) の場合にSQL_TRUEします。<br /><br /> 列が署名されている場合はSQL_FALSEします。|  
|SQL_DESC_UPDATABLE (ODBC 1.0)|*属性の設定*|列は、定義された定数の値によって記述されます。<br /><br /> SQL_ATTR_WRITESQL_ATTR_READWRITE_UNKNOWNSQL_ATTR_READONLY<br /><br /> SQL_DESC_UPDATABLEは、基本表の列ではなく、結果セット内の列の更新可能性を記述します。 結果セット列の基になる基本列の更新可能性は、このフィールドの値と異なる場合があります。 列が更新可能かどうかは、データ型、ユーザー特権、および結果セット自体の定義に基づいて行うことができます。 列が更新可能かどうかが不明な場合は、SQL_ATTR_READWRITE_UNKNOWN返す必要があります。|  
  
 **SQLCol 属性**は、拡張可能な代替手段**です**。 **SQLDescribeCol** ANSI-89 SQL に基づいて、固定された記述子情報のセットを返します。 **SQLColAttribute**を使用すると、ANSI SQL-92 および DBMS ベンダー拡張で使用できる、より広範な記述子情報セットにアクセスできます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|複数行のデータのフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
  
## <a name="example"></a>例  
 次のサンプル コードでは、ハンドルと接続を解放しません。 ハンドルとステートメントを解放するコード サンプルについては、「 [SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)、[サンプル ODBC プログラム](../../../odbc/reference/sample-odbc-program.md)、および[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)」を参照してください。  
  
```cpp  
// SQLColAttibute.cpp  
// compile with: user32.lib odbc32.lib  
  
#define UNICODE  
  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printStatementResult(SQLHSTMT hstmt) {  
   int bufferSize = 1024, i;  
   SQLRETURN retCode;  
   SQLSMALLINT numColumn = 0, bufferLenUsed;
   
   retCode = SQLNumResultCols(hstmt, &numColumn);  
   
   SQLPOINTER* columnLabels = (SQLPOINTER *)malloc( numColumn * sizeof(SQLPOINTER*) );  
   struct DataBinding* columnData = (struct DataBinding*)malloc( numColumn * sizeof(struct DataBinding) );  
  
   printf( "Columns from that table:\n" );  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnLabels[i] = (SQLPOINTER)malloc( bufferSize*sizeof(char) );  
  
      retCode = SQLColAttribute(hstmt, (SQLUSMALLINT)i + 1, SQL_DESC_LABEL, columnLabels[i], (SQLSMALLINT)bufferSize, &bufferLenUsed, NULL);  
      wprintf( L"Column %d: %s\n", i, (wchar_t*)columnLabels[i] );  
   }  
  
   // allocate memory for the binding  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnData[i].TargetType = SQL_C_CHAR;  
      columnData[i].BufferLength = (bufferSize+1);  
      columnData[i].TargetValuePtr = malloc( sizeof(unsigned char)*columnData[i].BufferLength );  
   }  
  
   // setup the binding   
   for ( i = 0 ; i < numColumn ; i++ ) {  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, columnData[i].TargetType,   
         columnData[i].TargetValuePtr, columnData[i].BufferLength, &(columnData[i].StrLen_or_Ind));  
   }  
  
   printf( "Data from that table:\n" );  
   // fetch the data and print out the data  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt) ) {  
      int j;  
      for ( j = 0 ; j < numColumn ; j++ )  
         wprintf( L"%s: %hs\n", columnLabels[j], columnData[j].TargetValuePtr );  
      printf( "\n" );  
   }  
   printf( "\n" );   
}  
  
int main() {  
   int bufferSize = 1024, i, count = 1, numCols = 5;  
   wchar_t firstTableName[1024], * dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize ), * userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen, bufferLen;  
   SQLRETURN retCode;  
  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   SQLWCHAR* selectAllQuery = (SQLWCHAR *)malloc( sizeof(SQLWCHAR) * bufferSize );  
  
   // connect to database  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLCHAR *)(void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, L"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // display the database information  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferLen);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, &bufferLen);  
  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // Set up the binding. This can be used even if the statement is closed by closeStatementHandle  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   retCode = SQLTables( hstmt, (SQLWCHAR*)SQL_ALL_CATALOGS, SQL_NTS, L"", SQL_NTS, L"", SQL_NTS, L"", SQL_NTS );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   retCode = SQLTables( hstmt, dbName, SQL_NTS, userName, SQL_NTS, L"%", SQL_NTS, L"TABLE", SQL_NTS );  
  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt), ++count )  
      if ( count == 1 )  
         StringCchPrintfW( firstTableName, 1024, L"%hs", catalogResult[2].TargetValuePtr );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   wprintf( L"Select all data from the first table (%s)\n", firstTableName );  
   StringCchPrintfW( selectAllQuery, bufferSize, L"SELECT * FROM %s", firstTableName );  
  
   retCode = SQLExecDirect(hstmt, selectAllQuery, SQL_NTS);  
   printStatementResult(hstmt);  
}  
```  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC のサンプル プログラム](../../../odbc/reference/sample-odbc-program.md)
