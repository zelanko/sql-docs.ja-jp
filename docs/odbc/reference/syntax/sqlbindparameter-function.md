---
title: 関数を使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBindParameter
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBindParameter
helpviewer_keywords:
- SQLBindParameter function [ODBC]
ms.assetid: 38349d4b-be03-46f9-9d6a-e50dd144e225
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02f50862bcfb0295c7f098afc6856c91e0249f66
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301362"
---
# <a name="sqlbindparameter-function"></a>SQLBindParameter 関数

**適合 性**  
 バージョン導入: ODBC 2.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQLBindParameter は**、SQL ステートメント内のパラメーター マーカーにバッファーをバインドします。 **SQLBindParameter**は、基になるドライバーが Unicode データをサポートしていない場合でも、Unicode C データ型へのバインドをサポートします。  
  
> [!NOTE]  
>  この関数は、ODBC 1.0 関数**SQLSetParam**を置き換えます。 詳細については、「コメント」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp
  
SQLRETURN SQLBindParameter(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT     InputOutputType,  
      SQLSMALLINT     ValueType,  
      SQLSMALLINT     ParameterType,  
      SQLULEN         ColumnSize,  
      SQLSMALLINT     DecimalDigits,  
      SQLPOINTER      ParameterValuePtr,  
      SQLLEN          BufferLength,  
      SQLLEN *        StrLen_or_IndPtr);  
```
  
## <a name="arguments"></a>引数

 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *パラメータ番号*  
 [入力]パラメータ番号は、1 から始まる、増加パラメーター順で順番に並べ替えられます。  
  
 *InputOutputType*  
 [入力]パラメーターの型。 詳細については、「コメント」*の「入力出力型*引数」を参照してください。  
  
 *Valuetype*  
 [入力]パラメーターの C データ型。 詳細については、「コメント」の *「ValueType*引数」を参照してください。  
  
 *パラメータータイプ*  
 [入力]パラメータの SQL データ型。 詳細については、「コメント」の「*パラメータ型*引数」を参照してください。  
  
 *ColumnSize*  
 [入力]対応するパラメーター マーカーの列または式のサイズ。 詳細については、「コメント」の *「ColumnSize*引数」を参照してください。  
  
 アプリケーションが 64 ビット Windows オペレーティング システムで実行される場合は[、「ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)」を参照してください。  
  
 *DecimalDigits*  
 [入力]対応するパラメーター・マーカーの列または式の 10 進数の数字。 列サイズの詳細については、「[列サイズ、10 進数、オクテット長の転送、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。  
  
 *パラメーター値Ptr*  
 [遅延入力]パラメーターのデータのバッファーへのポインター。 詳細については、「コメント」*の「ParameterValuePtr*引数」を参照してください。  
  
 *BufferLength*  
 [入出力]バイト単位の*パラメーター値Ptr*バッファーの長さ。 詳細については、「コメント」の *「BufferLength*引数」を参照してください。  
  
 アプリケーションが 64 ビット オペレーティング システムで実行される場合は[、「ODBC 64](../../../odbc/reference/odbc-64-bit-information.md)ビット情報」を参照してください。  
  
 *StrLen_or_IndPtr*  
 [遅延入力]パラメーターの長さのバッファーへのポインター。 詳細については、「コメント」の *「StrLen_or_IndPtr*引数」を参照してください。  
  
## <a name="returns"></a>戻り値

 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断

 **SQLBindParameter**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLBindParameter**によって返される SQLSTATE 値の一覧と、この関数のコンテキストでの各値を示しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  

|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|引数*ValueType*で指定されたデータ型を、*引数 ParameterType*で識別されるデータ型に変換することはできません。 このエラーは **、SQLBindParameter**ではなく、実行時に**SQLExecDirect** **、SQLExecute、** または**SQLPutData**によって返される可能性があることに注意してください。|  
|07009|記述子インデックスが無効です|(DM)*引数パラメータ数*に指定された値が 1 未満でした。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 **メッセージ テキスト*バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY003|無効なアプリケーション バッファ タイプ|*引数 ValueType*で指定された値が有効な C データ型またはSQL_C_DEFAULT。|  
|HY004|無効な SQL データ型|*引数 ParameterType*に指定された値は、有効な ODBC SQL データ型識別子でも、ドライバがサポートするドライバ固有の SQL データ型識別子でもありませんでした。|  
|HY009|引数の値が無効です|(DM) 引数*ParameterValuePtr*は null ポインターであり *、StrLen_or_IndPtr引数*は null ポインターであり、引数*InputOutputType*はSQL_PARAM_OUTPUTされませんでした。<br /><br /> (DM) SQL_PARAM_OUTPUT引数*ParameterValuePtr*が null ポインターであり、C 型が char またはバイナリであり、BufferLength (*cbValueMax*) が 0 より大きかった。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLBindParameter**が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 *StatementHandle、* この関数が呼び出されたときに実行されています。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY021|記述子情報の不一致|整合性チェック中にチェックされた記述子情報が一貫していません。 **(SQLSetDescField**の「整合性チェック」セクションを参照してください。<br /><br /> *引数 DecimalDigits*に指定された値が、*引数 ParameterType*で指定された SQL データ型の列のデータ ソースでサポートされている値の範囲外でした。|  
|HY090|無効な文字列またはバッファ長|(DM)*バッファ長*の値が 0 未満でした。 (SQL_DESC_DATA_PTRフィールドの説明**を**参照してください。|  
|HY104|有効桁数または小数点以下桁数の値が無効です|*引数 ColumnSize*または*DecimalDigits*に指定された値が、*引数 ParameterType*引数で指定された SQL データ型の列に対して、データ ソースでサポートされている値の範囲外でした。|  
|HY105|無効なパラメータタイプ|(DM) 引数*の入力出力タイプ*に指定された値が無効でした。 (「コメント」を参照してください。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|ドライバまたはデータ ソースは、引数*ValueType*に指定された値と、引数*ParameterType*に指定されたドライバ固有の値の組み合わせによって指定された変換をサポートしていません。<br /><br /> *引数 ParameterType*に指定された値は、ドライバーでサポートされている ODBC のバージョンの有効な ODBC SQL データ型識別子でしたが、ドライバーまたはデータ ソースでサポートされていませんでした。<br /><br /> ドライバーは ODBC 2 のみをサポートします。*x*と引数*ValueType*は、次のいずれかでした。<br /><br /> SQL_C_SBIGINTSQL_C_UBIGINTSQL_C_NUMERIC<br /><br /> 「付録 D: データ型」の[C データ型](../../../odbc/reference/appendixes/c-data-types.md)にリストされているすべての間隔 C データ型。<br /><br /> ドライバーは、3.50 より前の ODBC バージョンのみをサポートし、引数*ValueType*がSQL_C_GUIDされました。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明

 アプリケーションは、SQL ステートメント内の各パラメーター・マーカーをバインドするために**SQLBindParameter**を呼び出します。 バインディングは、アプリケーションが**SQLBindParameter**を再度呼び出すか、SQL_RESET_PARAMS オプションを指定して**SQLFreeStmt**を呼び出すか **、SQLSetDescField**を呼び出して APD のSQL_DESC_COUNT ヘッダー フィールドを 0 に設定するまで有効です。  
  
 パラメータの詳細については、「ステートメント[パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。 パラメーターのデータ型とパラメーター マーカーの詳細については、「付録 C: SQL 文法」の[「パラメーター データ型](../../../odbc/reference/appendixes/parameter-data-types.md)と[パラメーター マーカー](../../../odbc/reference/appendixes/parameter-markers.md) 」を参照してください。  
  
## <a name="parameternumber-argument"></a>パラメータ番号の引数  
 **SQLBindParameter**の呼び出しの*パラメーター番号*がSQL_DESC_COUNTの値より大きい場合は、SQL_DESC_COUNTの値を*パラメータ番号*に増やすために**呼**び出されます。  
  
## <a name="inputoutputtype-argument"></a>入力出力タイプの引数  
 引数は *、* パラメーターの型を指定します。 この引数は、IPD のSQL_DESC_PARAMETER_TYPEフィールドを設定します。 **INSERT**ステートメントなど、プロシージャを呼び出さない SQL ステートメント内のすべてのパラメーターは *、入力**パラメーターです*。 プロシージャ コールのパラメータは、入力パラメータ、入出力パラメータ、出力パラメータです。 (アプリケーションは、プロシージャ呼び出しのパラメーターの型を決定するために**SQLProcedureColumns**を呼び出します。  
  
 *InputOutputType* 引数は、次にいずれかの値になります。  
  
-   SQL_PARAM_INPUT。 このパラメーターは **、INSERT**ステートメントなどのプロシージャーを呼び出さない SQL ステートメント内のパラメーター、またはプロシージャー内の入力パラメーターにマークを付けます。 たとえば **、INSERT INTO 従業員の値 (?, ?, ?)** のパラメーターは入力パラメーターですが **、{call AddEmp(?, ?, ?)}** のパラメーターは入力パラメーターである可能性がありますが、必ずしも入力パラメーターであるとは限りません。  
  
     ステートメントが実行されると、ドライバーはパラメーターのデータをデータ ソースに送信します。\* *ParameterValuePtr*バッファーには、有効な入力値を含める必要があります、または **StrLen_or_IndPtr*バッファーは、SQL_NULL_DATA、SQL_DATA_AT_EXEC、またはSQL_LEN_DATA_AT_EXECマクロの結果を含める必要があります。  
  
     アプリケーションがプロシージャ呼び出しでパラメーターの型を判断できない場合は *、InputOutputType*を SQL_PARAM_INPUT に設定します。データ ソースがパラメーターの値を返す場合、ドライバーはパラメーターを破棄します。  
  
-   SQL_PARAM_INPUT_OUTPUT。 このパラメーターは、プロシージャー内の入出力パラメーターをマークします。 たとえば **、{call GetEmpDept(?)} の**パラメータは、従業員の名前を受け入れ、従業員の部署の名前を返す入出力パラメータです。  
  
     ステートメントが実行されると、ドライバーはパラメーターのデータをデータ ソースに送信します。\* *ParameterValuePtr*バッファーには、有効な入力値を含める\*必要があります、または*StrLen_or_IndPtr*バッファーは、SQL_NULL_DATA、SQL_DATA_AT_EXEC、またはSQL_LEN_DATA_AT_EXECマクロの結果を含める必要があります。 ステートメントが実行されると、ドライバーは、パラメーターのデータをアプリケーションに返します。データ ソースが入力/出力パラメーターの値を返さない場合、ドライバーは、SQL_NULL_DATAに **StrLen_or_IndPtr*バッファーを設定します。  
  
    > [!NOTE]  
    >  ODBC 1.0 アプリケーションが ODBC 2.0 ドライバーで**SQLSetParam**を呼び出すと、ドライバー マネージャーは、これを *、引数の入力出力の型*がSQL_PARAM_INPUT_OUTPUTに設定されている**SQLBindParameter**の呼び出しに変換します。  
  
-   SQL_PARAM_OUTPUT。 このパラメーターは、プロシージャの戻り値またはプロシージャの出力パラメーターをマークします。どちらの場合も、これらは*出力パラメータ*と呼ばれます。 たとえば **、{?=call GetNextEmpID} の**パラメータは、次の従業員 ID を返す出力パラメータです。  
  
     ステートメントが実行された後、パラメーターのデータを返す、パラメーター、引数、 *ParameterValuePtr*と*StrLen_or_IndPtr*引数が両方とも null ポインターを場合、ドライバーは出力値を破棄します。 データ ソースが出力パラメーターの値を返さない場合、ドライバーは、SQL_NULL_DATAに **StrLen_or_IndPtr*バッファーを設定します。  
  
-   SQL_PARAM_INPUT_OUTPUT_STREAM。 入出力パラメーターをストリーミングする必要があることを示します。 **SQLGetData は**、パラメーター値を部分で読み取ることができます。 *バッファ長*は**SQLGetData**の呼び出し時に決定されるため、バッファ長は無視されます。 *StrLen_or_IndPtr*バッファーの値には、SQL_NULL_DATA、SQL_DEFAULT_PARAM、SQL_DATA_AT_EXEC、またはSQL_LEN_DATA_AT_EXECマクロの結果が含まれている必要があります。 パラメーターが出力時にストリーム配信される場合は、パラメーターを入力時に実行時データ (DAE) パラメーターとしてバインドする必要があります。 *ParameterValuePtr*は、入力と出力の両方に対して*ParameterValuePtr*で渡された値を持つユーザー定義トークンとして**SQLParamData**によって返される任意の非 NULL ポインター値です。 詳細については、「 [SQLGetData を使用した出力パラメータの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください。  
  
-   SQL_PARAM_OUTPUT_STREAM。 出力パラメーターの場合は、SQL_PARAM_INPUT_OUTPUT_STREAMと同じです。 **StrLen_or_IndPtr*は入力時に無視されます。  
  
 次の表は、*入力出力タイプ*と **StrLen_or_IndPtr*の異なる組み合わせを示しています。  
  
|*InputOutputType*|**StrLen_or_IndPtr*|結果|パラメーター値Ptr に対する備値|  
|-----------------------|----------------------------|-------------|---------------------------------|  
|SQL_PARAM_INPUT|SQL_LEN_DATA_AT_EXEC(*len*) または SQL_DATA_AT_EXEC|パーツ内の入力|*値*が渡されたユーザー定義トークンとして**SQLParamData**によって返される任意のポインター値を*指定*できます。|  
|SQL_PARAM_INPUT|*SQL_LEN_DATA_AT_EXEC(len)* またはSQL_DATA_AT_EXEC|入力バインド バッファー|*入力*バッファーのアドレスです。|  
|SQL_PARAM_OUTPUT|入力時に無視されます。|出力バインド バッファー|*パラメーター値Ptr*は、出力バッファーのアドレスです。|  
|SQL_PARAM_OUTPUT_STREAM|入力時に無視されます。|ストリーミング出力|*任意の*ポインター値を指定*できます。* **SQLParamData**|  
|SQL_PARAM_INPUT_OUTPUT|SQL_LEN_DATA_AT_EXEC(*len*) または SQL_DATA_AT_EXEC|パーツおよび出力バインド バッファでの入力|*ParameterValuePtr*は出力バッファーのアドレスであり、値が*ParameterValuePtr*で渡されたユーザー定義トークンとして**SQLParamData**によっても返されます。|  
|SQL_PARAM_INPUT_OUTPUT|*SQL_LEN_DATA_AT_EXEC(len)* またはSQL_DATA_AT_EXEC|入力バインド バッファーと出力バインド バッファー|*パラメーター値Ptr*は、共有入出力バッファーのアドレスです。|
|SQL_PARAM_INPUT_OUTPUT_STREAM|SQL_LEN_DATA_AT_EXEC(*len*) または SQL_DATA_AT_EXEC|パートとストリーム出力での入力|*ParameterValuePtr*は、入力と出力の両方に対して*ParameterValuePtr*で渡された値を持つユーザー定義トークンとして**SQLParamData**によって返される null 以外のポインター値にすることができます。|  
  
> [!NOTE]  
>  ドライバーは、アプリケーションがストリームとして出力または入力出力パラメーターをバインドするときに許可される SQL の種類を決定する必要があります。 ドライバー マネージャーは、無効な SQL の種類のエラーを生成しません。  
  
## <a name="valuetype-argument"></a>値型引数

 *ValueType*引数は、パラメーターの C データ型を指定します。 この引数は、APD のSQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE、およびSQL_DESC_DATETIME_INTERVAL_CODEフィールドを設定します。 これは付録 D:[データ型の C データ型](../../../odbc/reference/appendixes/c-data-types.md)セクションの値のいずれかである必要があります。  
  
 *ValueType*引数が間隔データ型の 1 つである場合、APD の*ParameterNumber*レコードのSQL_DESC_TYPEフィールドは SQL_INTERVAL に設定され、APD のSQL_DESC_CONCISE_TYPEフィールドは簡潔な間隔データ型に設定され *、ParameterNumber*レコードのSQL_DESC_DATETIME_INTERVAL_CODEフィールドは特定の間隔データ型のサブコードに設定されます。 ([付録 D: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)を参照してください。APD のSQL_DESC_DATETIME_INTERVAL_PRECISIONフィールドとSQL_DESC_PRECISION フィールドで設定されているデフォルトの間隔先行精度 (2) とデフォルトの間隔秒精度 (6) が、それぞれデータに使用されます。 いずれかのデフォルト精度が適切でない場合は、アプリケーションは**SQLSetDescField**または**SQLSetDescRec**の呼び出しによって記述子フィールドを明示的に設定する必要があります。  
  
 *ValueType*引数が日時データ型の 1 つである場合、APD の*ParameterNumber*レコードのSQL_DESC_TYPEフィールドが SQL_DATETIME に設定され、APD の*パラメーター番号*レコードのSQL_DESC_CONCISE_TYPEフィールドは簡潔な日時 C データ型に設定され、*パラメータ番号*レコードのSQL_DESC_DATETIME_INTERVAL_CODEフィールドは特定の日時データ型のサブコードに設定されます。 ([付録 D: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)を参照してください。  
  
 *ValueType*引数がSQL_C_NUMERICデータ型の場合、APD のSQL_DESC_PRECISIONフィールドとSQL_DESC_SCALE フィールドに設定されている既定の精度 (ドライバー定義) と既定のスケール (0) がデータに使用されます。 デフォルトの精度または位取りが適切でない場合、アプリケーションは**SQLSetDescField**または**SQLSetDescRec**の呼び出しによって記述子フィールドを明示的に設定する必要があります。  
  
 SQL_C_DEFAULTは *、ParameterType*で指定された SQL データ型の既定の C データ型からパラメータ値を転送することを指定します。  
  
 拡張 C データ型を指定することもできます。 詳細については[、「ODBC での C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)」を参照してください。  
  
 詳細については、「付録[D: データ型」の「既定の C データ型](../../../odbc/reference/appendixes/default-c-data-types.md)」、[データを C から SQL データ型に変換](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)する、および[SQL から C データ型へのデータの変換](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)を参照してください。  
  
## <a name="parametertype-argument"></a>パラメータ型引数

 これは、「付録 D:[データ型」の「SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)」セクションに記載されている値のいずれかであるか、ドライバー固有の値である必要があります。 この引数は、IPD のSQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE、およびSQL_DESC_DATETIME_INTERVAL_CODEフィールドを設定します。  
  
 引数*ParameterType*が日時識別子の 1 つである場合、IPD のSQL_DESC_TYPEフィールドは SQL_DATETIME に設定され、IPD のSQL_DESC_CONCISE_TYPEフィールドは簡潔な日時 SQL データ型に設定され、SQL_DESC_DATETIME_INTERVAL_CODEフィールドは適切な日時サブコード値に設定されます。  
  
 *ParameterType*が間隔識別子の 1 つである場合、IPD のSQL_DESC_TYPE フィールドは SQL_INTERVAL に設定され、IPD のSQL_DESC_CONCISE_TYPE フィールドは SQL 間隔データ型の簡潔な値に設定され、IPD のSQL_DESC_DATETIME_INTERVAL_CODE フィールドは適切な間隔サブコードに設定されます。 IPD のSQL_DESC_DATETIME_INTERVAL_PRECISIONフィールドは、間隔先行精度に設定され、該当する場合は SQL_DESC_PRECISION フィールドが間隔秒精度に設定されます。 SQL_DESC_DATETIME_INTERVAL_PRECISIONまたはSQL_DESC_PRECISIONのデフォルト値が適切でない場合、アプリケーションは**SQLSetDescField**を呼び出して明示的に設定する必要があります。 これらのフィールドの詳細については、「 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)」を参照してください。  
  
 *ValueType*引数がSQL_NUMERICデータ型の場合、IPD のSQL_DESC_PRECISIONフィールドとSQL_DESC_SCALEフィールドに設定されている既定の精度 (ドライバー定義) と既定のスケール (0) がデータに使用されます。 デフォルトの精度または位取りが適切でない場合、アプリケーションは**SQLSetDescField**または**SQLSetDescRec**の呼び出しによって記述子フィールドを明示的に設定する必要があります。  
  
 データの変換方法については、「付録 D:[データ型」の「データを C から SQL データ型に変換する](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)」および[「SQL から C データ型へのデータ変換](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)」を参照してください。  
  
## <a name="columnsize-argument"></a>列サイズ引数

 *ColumnSize*引数は、パラメーター マーカーに対応する列または式のサイズ、そのデータの長さ、またはその両方を指定します。 この引数は、SQL データ型 *(ParameterType*引数) に応じて、IPD の異なるフィールドを設定します。 このマッピングには、次の規則が適用されます。  
  
-   *ParameterType*がSQL_CHAR、SQL_VARCHAR、SQL_LONGVARCHAR、SQL_BINARY、SQL_VARBINARY、SQL_LONGVARBINARY、または SQL の簡潔な日時または間隔のデータ型の 1 つである場合、IPD のSQL_DESC_LENGTH フィールドは*ColumnSize*の値に設定されます。 (詳細については、「付録 D: データ型」の[「列サイズ、10 進数、オクテット長の転送、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」セクションを参照してください。  
  
-   *ParameterType*がSQL_DECIMAL、SQL_NUMERIC、SQL_FLOAT、SQL_REAL、またはSQL_DOUBLEの場合、IPD のSQL_DESC_PRECISION フィールドは*ColumnSize*の値に設定されます。  
  
-   その他のデータ型の場合、*引数 ColumnSize*は無視されます。  
  
 詳細については、「パラメータ値の引き渡し」および *「StrLen_or_IndPtr*引数」のSQL_DATA_AT_EXECを参照してください。  
  
## <a name="decimaldigits-argument"></a>10 進数の引数

 *ParameterType*がSQL_TYPE_TIME、SQL_TYPE_TIMESTAMP、SQL_INTERVAL_SECOND、SQL_INTERVAL_DAY_TO_SECOND、SQL_INTERVAL_HOUR_TO_SECOND、またはSQL_INTERVAL_MINUTE_TO_SECONDの場合、IPD のSQL_DESC_PRECISION フィールドは*DecimalDigits*に設定されます。 *ParameterType*がSQL_NUMERICまたはSQL_DECIMALの場合、IPD のSQL_DESC_SCALE フィールドは*10 進数に設定されます*。 その他のすべてのデータ型では、*引数 DecimalDigits*は無視されます。  
  
## <a name="parametervalueptr-argument"></a>引数

 引数*は***、SQLExecute**または**SQLExecDirect**が呼び出されたときに、パラメーターの実際のデータを格納するバッファーを指します。 データは *、ValueType*引数で指定された形式である必要があります。 この引数は APD のSQL_DESC_DATA_PTRフィールドを設定します。 アプリケーションは*\*、StrLen_or_IndPtr*がSQL_NULL_DATAまたはSQL_DATA_AT_EXECである限り、*引数 ParameterValuePtr*を null ポインターに設定できます。 (これは、入力パラメータまたは入出力パラメータにのみ適用されます。  
  
 \* *StrLen_or_IndPtr*が SQL_LEN_DATA_AT_EXEC(*length*) マクロまたはSQL_DATA_AT_EXECの結果である場合 *、ParameterValuePtr*は、パラメーターに関連付けられているアプリケーション定義のポインター値です。 これは **、SQLParamData**を使用してアプリケーションに返されます。 たとえば *、ParameterValuePtr*は、パラメーター番号、データへのポインター、またはアプリケーションが入力パラメーターをバインドするために使用した構造体へのポインターなどの 0 以外のトークンです。 ただし、パラメーターが入出力パラメーターの場合 *、ParameterValuePtr*は出力値が格納されるバッファーへのポインターである必要があることに注意してください。 SQL_ATTR_PARAMSET_SIZEステートメント属性の値が 1 より大きい場合、アプリケーションは、SQL_ATTR_PARAMS_PROCESSED_PTRステートメント属性によって示される値を*ParameterValuePtr*引数と共に使用できます。 たとえば *、ParameterValuePtr*は値の配列を指し示し、アプリケーションはSQL_ATTR_PARAMS_PROCESSED_PTRが指す値を使用して、配列から正しい値を取得します。 詳細については、このセクションの「パラメータ値の引き渡し」を参照してください。  
  
 *引数*がSQL_PARAM_INPUT_OUTPUTまたはSQL_PARAM_OUTPUT場合 *、ParameterValuePtr*は、ドライバーが出力値を返すバッファーを指します。 プロシージャが 1 つ以上の結果セットを\*返す場合、すべての結果セット/行カウントが処理されるまで *、ParameterValuePtr*バッファーは設定されません。 処理が完了するまでバッファが設定されていない場合、出力パラメータと戻り値は **、SQLMoreResults**がSQL_NO_DATAを返すまで使用できません。 オプションをSQL_CLOSEで指定して**SQLCloseCursor**または**SQLFreeStmt**を呼び出すと、これらの値が破棄されます。  
  
 SQL_ATTR_PARAMSET_SIZE ステートメント属性の値が 1 より大きい場合 *、ParameterValuePtr*は配列を指します。 単一の SQL ステートメントは、入力パラメーターまたは入出力パラメーターの入力値の完全な配列を処理し、入出力パラメーターまたは出力パラメーターの出力値の配列を戻します。  
  
## <a name="bufferlength-argument"></a>バッファ長引数

 文字およびバイナリ C データの場合、*引数 BufferLength*引数\**は、バッファー*の長さ (単一の要素の場合) または\**ParameterValuePtr*配列内の要素の長さを指定します (SQL_ATTR_PARAMSET_SIZEステートメント属性の値が 1 より大きい場合)。 この引数は、APD のSQL_DESC_OCTET_LENGTHレコード・フィールドを設定します。 アプリケーションが複数の値を指定する場合は、入力時と出力時の両方で、 **ParameterValuePtr*配列内の値の位置を決定するために*BufferLength*が使用されます。 入出力パラメーターの場合、出力時に文字およびバイナリー C データを切り捨てるかどうかを判別するために使用されます。  
  
-   文字 C データの場合、返されるバイト数が*BufferLength*以上の場合\**、ParameterValuePtr*のデータは*BufferLength*に切り捨てられ、null 終端文字の長さが減り、ドライバーによって null で終了します。  
  
-   バイナリ C データの場合、返されるバイト数が*BufferLength*より大きい場合\**、ParameterValuePtr*のデータは*BufferLength*バイトに切り捨てられます。  
  
 その他の C データの種類はすべて *、BufferLength*引数は無視されます。 \* *ParameterValuePtr*バッファーの長さ (単一の要素の場合) または\**ParameterValuePtr*配列内の要素の長さ (アプリケーションが各パラメーターに複数の値を指定する*属性*引数を SQL_ATTR_PARAMSET_SIZE持つ**SQLSetStmtAttr**を呼び出す場合) は、C データ型の長さであると想定されます。  
  
 ストリーム出力またはストリーム出力入出力パラメーターの場合、バッファー長が**SQLGetData**で指定されているため *、BufferLength*引数は無視されます。  
  
> [!NOTE]  
>  ODBC 1.0 アプリケーションが ODBC 3 で**SQLSetParam**を呼び出すとします。*x*ドライバー、ドライバー マネージャーは、*バッファー*長引数が常にSQL_SETPARAM_VALUE_MAXされている**SQLBind パラメーター**の呼び出しにこれを変換します。 ドライバー マネージャーは、ODBC 3 の場合にエラーを返すため。*x*アプリケーションは *、バッファ長*を ODBC 3 SQL_SETPARAM_VALUE_MAXに設定します。*x*ドライバは、ODBC 1.0 アプリケーションから呼び出されたタイミングを判断するためにこれを使用できます。  
  
> [!NOTE]  
>  **SQLSetParam**では、ドライバーが文字またはバイナリ データを返すことができるようにアプリケーションが **ParameterValuePtr*バッファーの長さを指定する方法、およびアプリケーションが文字またはバイナリ パラメーター値の配列をドライバーに送信する方法は、ドライバー定義されます。  
  
## <a name="strlen_or_indptr-argument"></a>StrLen_or_IndPtr引数

 *StrLen_or_IndPtr*引数は **、SQLExecute**または**SQLExecDirect**が呼び出されたときに、次のいずれかを含むバッファーを指します。 (この引数は、アプリケーション・パラメーター・ポインターのSQL_DESC_OCTET_LENGTH_PTRおよびSQL_DESC_INDICATOR_PTRレコード・フィールドを設定します。  
  
-   * パラメータ値に格納されているパラメータ値の長*さ。* これは、文字またはバイナリー C データを除いて無視されます。  
  
-   SQL_NTS。 パラメーター値は、NULL で終わる文字列です。  
  
-   SQL_NULL_DATA。 パラメーター値が NULL です。  
  
-   SQL_DEFAULT_PARAM。 プロシージャでは、アプリケーションから取得した値ではなく、パラメーターの既定値を使用します。 この値は、ODBC 標準構文で呼び出されるプロシージャでのみ有効であり、*引数 InputOutputType*がSQL_PARAM_INPUT、SQL_PARAM_INPUT_OUTPUT、またはSQL_PARAM_INPUT_OUTPUT_STREAMの場合にのみ有効です。 \* *StrLen_or_IndPtr*がSQL_DEFAULT_PARAMされている場合、*入力パラメーターでは、値型*、*パラメーター型*、*列サイズ**、10 進数 、**バッファー長*、および*パラメーター値Ptr*の引数は無視され、入力/出力パラメーターの出力パラメーター値を定義するためだけに使用されます。  
  
-   SQL_LEN_DATA_AT_EXEC(*長さ*) マクロの結果。 パラメータのデータは**SQLPutData**と共に送信されます。 引数*ParameterType*がSQL_LONGVARBINARY、SQL_LONGVARCHAR、または長いデータ ソース固有のデータ型であり、ドライバーが**SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報型に対して "Y" を返す場合、*長さは*パラメーターに送信されるデータのバイト数です。それ以外の場合、*長さは*負でない値でなければならず、無視されます。 詳細については、このセクションの「パラメータ値の引き渡し」を参照してください。  
  
     たとえば、1 つ以上の呼び出しで**SQLPutData**と共に 10,000 バイトのデータを送信するように指定するには、SQL_LONGVARCHAR パラメーターの場合、アプリケーションは **StrLen_or_IndPtr*を SQL_LEN_DATA_AT_EXEC(10000) に設定します。  
  
-   SQL_DATA_AT_EXEC。 パラメータのデータは**SQLPutData**と共に送信されます。 この値は、ODBC 1.0 アプリケーションが ODBC 3 を呼び出すときに使用されます。*x*ドライバ。 詳細については、このセクションの「パラメータ値の引き渡し」を参照してください。  
  
 *StrLen_or_IndPtr*が null ポインターの場合、ドライバーは、すべての入力パラメーター値が NULL でないと想定し、文字とバイナリ データが NULL で終了します。 *InputOutputType*がSQL_PARAM_OUTPUTまたはSQL_PARAM_OUTPUT_STREAMされ *、ParameterValuePtr*と*StrLen_or_IndPtr*が両方とも null ポインターである場合、ドライバーは出力値を破棄します。  
  
> [!NOTE]  
>  アプリケーション開発者は、パラメーターのデータ型がSQL_C_BINARY場合 *、StrLen_or_IndPtr*に null ポインターを指定しないことを強くお勧めします。 ドライバーが予期せずSQL_C_BINARYデータを切り捨てないようにするには *、StrLen_or_IndPtr*有効な長さの値へのポインターを含める必要があります。  
  
 *引数が*SQL_PARAM_INPUT_OUTPUT、SQL_PARAM_OUTPUT、SQL_PARAM_INPUT_OUTPUT_STREAM、またはSQL_PARAM_OUTPUT_STREAM、StrLen_or_IndPtrドライバーがSQL_NULL_DATAを*StrLen_or_IndPtr*返すバッファーを指している場合\**、ParameterValuePtr*で返されるバイト数 (文字データの null 終了バイトを除く)、またはSQL_NO_TOTAL (返されるバイト数を決定できない場合) 。 プロシージャが 1 つ以上の結果セットを返す場合、すべての結果がフェッチされるまで、 **StrLen_or_IndPtr*バッファは設定されません。  
  
 SQL_ATTR_PARAMSET_SIZEステートメント属性の値が 1 より大きい場合 *、StrLen_or_IndPtr*は SQLLEN 値の配列を指します。 これらの値は、このセクションで前述した値のいずれかであり、1 つの SQL ステートメントで処理されます。  
  
## <a name="passing-parameter-values"></a>パラメータ値の引き渡し

 アプリケーションは、パラメーターの値を渡すことができます\*、 *ParameterValuePtr*バッファーまたは**SQLPutData**への 1 つ以上の呼び出しを使用します。 **SQLPutData**を使用してデータが渡されるパラメーターは、*実行時データ*パラメーターと呼ばれます。 これらは通常、SQL_LONGVARBINARYおよびSQL_LONGVARCHARパラメーターのデータを送信するために使用され、他のパラメーターと混合できます。  
  
 パラメーター値を渡すために、アプリケーションは次の手順のシーケンスを実行します。  
  
1.  各パラメーターの値 *(ParameterValuePtr*引数) と長さ/インジケーター *(StrLen_or_IndPtr*引数) のバッファーをバインドする各パラメーターの**SQLBindParameter**を呼び出します。 実行時のデータ パラメーターの*場合、ParameterValuePtr*は、パラメーター番号やデータへのポインターなどのアプリケーション定義のポインター値です。 値は後で返され、パラメーターを識別するために使用できます。  
  
2.  入力および入出力パラメーターの値を\* *ParameterValuePtr*および **StrLen_or_IndPtr*バッファーに配置します。  
  
    -   通常のパラメーターの場合、アプリケーションはパラメーター値を\* *ParameterValuePtr*バッファーに格納し、その値の長さを **StrLen_or_IndPtr*バッファーに格納します。 詳細については、「[パラメータ値の設定」を](../../../odbc/reference/develop-app/setting-parameter-values.md)参照してください。  
  
    -   実行時データ パラメーターの場合、アプリケーションは SQL_LEN_DATA_AT_EXEC(*length*) マクロの結果を ( ODBC 2.0 ドライバーを呼び出すとき ) を*StrLen_or_IndPtr*バッファーに格納します。  
  
3.  SQL ステートメントを実行するために**SQL 実行または** **SQLExecDirect**を呼び出します。  
  
    -   実行時データパラメータがない場合、プロセスは完了です。  
  
    -   実行時のデータパラメーターがある場合、関数はSQL_NEED_DATAを返します。  
  
4.  **SQLParamData**を呼び出して、最初に処理される実行時データ パラメーターの引数*ParameterValuePtr*で指定されたアプリケーション定義の値を取得します。 **SQLBindParameter** **SQL_NEED_DATAを返します**。  
  
    > [!NOTE]  
    >  実行時のデータ パラメーターは実行時のデータ列に似ていますが **、SQLParamData**によって返される値はそれぞれ異なります。 実行時データ パラメーターは、SQL ステートメントのパラメーターであり、SQLPutData ステートメントが**SQLExecDirect**または**SQLExecute**を使用して実行されるときに **、SQLPutData**と共にデータが送信されます。 これらは **、SQLBindParameter**でバインドされます。 **返**される値は、*引数の*引数で**SQLBind パラメーター**に渡されるポインター値です。 実行データ列は、行が**SQLBulkOperations**で更新または追加されるか **、SQLSetPos**で更新されたときに、データが**SQLPutData**と共に送信される行セット内の列です。 これらの値は **、SQLBindCol**にバインドされています。 **SQLParamData**によって返される値は、処理されている **TargetValuePtr*バッファー ( **SQLBindCol**の呼び出しによって設定された ) 内の行のアドレスです。  
  
5.  **SQLPutData を**1 回以上呼び出して、パラメーターのデータを送信します。 データ値が\***SQLPutData**で指定された*ParameterValuePtr*バッファーより大きい場合は、複数の呼び出しが必要です。同じパラメーターに対する**SQLPutData**の複数回の呼び出しは、文字 C データを文字、バイナリ、またはデータ ソース固有のデータ型を持つ列に送信する場合、または文字、バイナリ、またはデータ ソース固有のデータ型を持つ列にバイナリ C データを送信する場合にのみ許可されます。  
  
6.  **SQLParamData**を再度呼び出して、パラメーターに対してすべてのデータが送信されたことを通知します。  
  
    -   実行時のデータ・パラメーターがさらにある場合 **、SQLParamData**は、次に処理される実行時データ・パラメーターの SQL_NEED_DATAとアプリケーション定義値を戻します。 アプリケーションは、手順 4 と 5 を繰り返します。  
  
    -   実行時のデータ・パラメーターがこれ以上ない場合、プロセスは完了です。 ステートメントが正常に実行された場合は **、SQL_SUCCESS**またはSQL_SUCCESS_WITH_INFOが返されます。実行が失敗した場合は、SQL_ERRORを返します。 この時点で **、SQLParamData**は、ステートメントの実行に使用される関数 **(SQLExecDirect**または**SQLExecute)** によって返される可能性のある任意の SQLSTATE を返すことができます。  
  
         アプリケーションがステートメントによって生成されたすべての結果セットを\*取得した後、任意の入出力パラメーターまたは出力パラメーターの出力値は *、ParameterValuePtr*および **StrLen_or_IndPtr*バッファーで使用できます。  
  
 呼び出し**SQLExecute**または**SQLExecDirect**ステートメントをSQL_NEED_DATA状態にします。 この時点で、アプリケーションは、ステートメントまたはステートメントに関連付けられた*接続ハンドル*を使用して **、SQLCancel** **、SQLGetDiagField** **、SQLGetDiagRec** **、SQLParamData、** または**SQLPutData**のみを呼び出すことができます。 **SQLGetFunctions** ステートメントまたはステートメントに関連付けられた接続を使用して他の関数を呼び出す場合、関数は SQLSTATE HY010 (関数シーケンスエラー) を戻します。 **ステートメントは、SQLParamData**または**SQLPutData**がエラーを返した場合 **、SQLParamData**がSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを戻すか、またはステートメントが取り消された場合、SQL_NEED_DATA状態を残します。  
  
 ドライバーが実行時データ パラメーターのデータを必要としている間にアプリケーションが**SQLCancel**を呼び出す場合、ドライバーはステートメントの実行をキャンセルします。アプリケーションは、再び**SQL 実行または** **SQLExecDirect を**呼び出すことができます。  
  
## <a name="retrieving-streamed-output-parameters"></a>ストリーミング出力パラメーターの取得

 アプリケーションが*InputOutputType*を SQL_PARAM_INPUT_OUTPUT_STREAM またはSQL_PARAM_OUTPUT_STREAMに設定する場合は **、SQLGetData**への 1 回以上の呼び出しによって出力パラメーター値を取得する必要があります。 ドライバーがストリーム出力パラメーター値を持つ場合、アプリケーションに返す、次の関数への呼び出しに応答してSQL_PARAM_DATA_AVAILABLE返します **。** **SQLExecute** **SQLExecDirect** アプリケーションは**SQLParamData**を呼び出して、どのパラメーター値が使用可能かを判別します。  
  
 SQL_PARAM_DATA_AVAILABLEおよびストリーム出力パラメーターの詳細については、「 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください。  
  
## <a name="using-arrays-of-parameters"></a>パラメーターの配列の使用

 アプリケーションがパラメーター・マーカーを使用してステートメントを準備し、パラメーターの配列を渡す場合、この実行方法は 2 つあります。 1 つの方法は、ドライバーがバックエンドの配列処理機能に依存する方法です。 Oracle は、配列処理機能をサポートするデータ ソースの例です。 この機能を実装するもう 1 つの方法は、パラメーター配列内のパラメーターのセットごとに 1 つの SQL ステートメントを生成し、バッチを実行する SQL ステートメントのバッチをドライバーに対して行う方法です。 パラメーターの配列は **、UPDATE WHERE CURRENT OF**ステートメントと共に使用することはできません。  
  
 パラメータの配列が処理される場合、個々の結果セット/行数 (各パラメータ セットに 1 つ) を使用したり、結果セット/行数を 1 つにロールアップしたりできます。 **SQLGetInfo**のSQL_PARAM_ARRAY_ROW_COUNTS オプションは、各パラメーターセット (SQL_PARC_BATCH) に対して行カウントを使用できるか、または 1 つの行カウントのみが使用可能 (SQL_PARC_NO_BATCH) であるかを示します。  
  
 **SQLGetInfo**のSQL_PARAM_ARRAY_SELECTS オプションは、パラメーターのセット (SQL_PAS_BATCH) ごとに結果セットを使用できるか、または 1 つの結果セットだけが使用可能 (SQL_PAS_NO_BATCH) かどうかを示します。 ドライバーが結果セット生成ステートメントをパラメーターの配列で実行することを許可しない場合、SQL_PARAM_ARRAY_SELECTSはSQL_PAS_NO_SELECTを返します。  
  
 詳細については、「 [SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)」を参照してください。  
  
 パラメーターの配列をサポートするために、SQL_ATTR_PARAMSET_SIZEステートメント属性は、各パラメーターの値の数を指定するように設定されます。 フィールドが 1 より大きい場合、APD のSQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTRフィールドは配列を指している必要があります。 各配列の基数は、SQL_ATTR_PARAMSET_SIZEの値と等しくなります。  
  
 APD のSQL_DESC_ROWS_PROCESSED_PTR フィールドは、エラー セットを含む、処理されたパラメーターのセットの数を含むバッファーを指します。 パラメーターの各セットが処理されると、ドライバーはバッファーに新しい値を格納します。 null ポインターの場合は、数値は返されません。 パラメータの配列を使用する場合、設定関数によってSQL_ERRORが返された場合でも、APD のSQL_DESC_ROWS_PROCESSED_PTRフィールドが指す値が設定されます。 SQL_NEED_DATAが返された場合、APD の SQL_DESC_ROWS_PROCESSED_PTR フィールドが指す値は、処理されるパラメーターのセットに設定されます。  
  
 パラメータの配列がバインドされ **、UPDATE WHERE CURRENT OF**ステートメントが実行される場合に何が起こるかは、ドライバー定義です。  
  
## <a name="column-wise-parameter-binding"></a>カラムワイズパラメータバインディング

 列方向バインディングでは、アプリケーションは、各パラメーターに個別のパラメーターと長さ/インジケーター配列をバインドします。  
  
 列方向のバインディングを使用するには、アプリケーションは最初に SQL_ATTR_PARAM_BIND_TYPE ステートメント属性を SQL_PARAM_BIND_BY_COLUMN に設定します。 (これがデフォルトです。バインドする各列に対して、アプリケーションは次の手順を実行します。  
  
1.  パラメーター バッファー配列を割り当てます。  
  
2.  長さ/インジケーター バッファーの配列を割り当てます。  
  
    > [!NOTE]  
    >  列方向のバインディングを使用するときにアプリケーションが記述子に直接書き込む場合は、長さデータと標識データに別々の配列を使用できます。  
  
3.  次の引数を指定して**SQLBind パラメーター**を呼び出します。  
  
    -   *ValueType*は、パラメーター バッファー配列内の 1 つの要素の C 型です。  
  
    -   *パラメーターの種類*は、パラメーターの SQL 型です。  
  
    -   *パラメーター*バッファー配列のアドレスです。  
  
    -   *バッファー長*は、パラメーター バッファー配列内の 1 つの要素のサイズです。 *引数 BufferLength*は、データが固定長データの場合は無視されます。  
  
    -   *StrLen_or_IndPtr*は長さ/インジケーター配列のアドレスです。  
  
 この情報の使用方法の詳細については、このセクションの「コメント」の「ParameterValuePtr 引数」を参照してください。 パラメーターの列方向のバインドの詳細については、「パラメーターの[配列のバインド](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)」を参照してください。  
  
## <a name="row-wise-parameter-binding"></a>行方向パラメーターのバインド

 行方向のバインドでは、バインドする各パラメーターのパラメーターバッファーと長さ/インジケーター バッファーを含む構造体が定義されます。  
  
 行方向のバインドを使用するには、アプリケーションは次の手順を実行します。  
  
1.  パラメータの単一のセット (パラメータと長さ/インジケーター バッファの両方を含む) を保持する構造体を定義し、これらの構造体の配列を割り当てます。  
  
    > [!NOTE]  
    >  行方向のバインドが使用されているときにアプリケーションが記述子に直接書き込む場合は、長さデータと標識データに別々のフィールドを使用できます。  
  
2.  SQL_ATTR_PARAM_BIND_TYPEステートメント属性を、単一のパラメーター セットを含む構造体のサイズ、またはパラメーターがバインドされるバッファーのインスタンスのサイズに設定します。 長さには、バインドされたすべてのパラメーターのスペース、および構造体またはバッファーの埋め込みスペースを含めて、バインドされたパラメーターのアドレスが指定された長さでインクリメントされるときに、結果が次の行の同じパラメーターの先頭を指していることを確認する必要があります。 ANSI C で*sizeof*演算子を使用すると、この動作が保証されます。  
  
3.  バインドする各パラメーターに対して、次の引数を指定して**SQLBindParameter**を呼び出します。  
  
    -   *ValueType*は、列にバインドされるパラメーター バッファー メンバーの型です。  
  
    -   *パラメーターの種類*は、パラメーターの SQL 型です。  
  
    -   *パラメーター値Ptr*は、最初の配列要素のパラメーター バッファー メンバーのアドレスです。  
  
    -   *バッファー長*は、パラメーター バッファー メンバーのサイズです。  
  
    -   *StrLen_or_IndPtr*は、バインドされる長さ/標識メンバーのアドレスです。  
  
 この情報の使用方法の詳細については、このセクションの後半の *「ParameterValuePtr*引数」を参照してください。 パラメータの行方向のバインドの詳細については、「 パラメータの[配列のバインド](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)」を参照してください。  
  
## <a name="error-information"></a>エラー情報

 ドライバーがパラメーター配列をバッチとして実装しない場合 (SQL_PARAM_ARRAY_ROW_COUNTSオプションはSQL_PARC_NO_BATCHに等しい)、エラーの状況は、1 つのステートメントが実行されたかのように処理されます。 ドライバーがバッチとしてパラメーター配列を実装する場合、アプリケーションは、SQL ステートメントのSQL_DESC_ARRAY_STATUS_PTR ヘッダー フィールドを使用して、SQL ステートメントのパラメーターまたはパラメーターの配列内で**SQLExecDirect**または**SQLExecute**がエラーを返す原因となるパラメーターを決定できます。 このフィールドには、パラメーター値の各行の状態情報が含まれます。 エラーが発生したことがフィールドで示されている場合、診断データ構造のフィールドは、失敗したパラメーターの行とパラメーター番号を示します。 配列内の要素の数は、SQL_ATTR_PARAMSET_SIZEステートメント属性で設定できる APD のSQL_DESC_ARRAY_SIZEヘッダー フィールドによって定義されます。  
  
> [!NOTE]  
>  APD のSQL_DESC_ARRAY_STATUS_PTRヘッダー フィールドは、パラメーターを無視するために使用されます。 パラメーターの無視の詳細については、次の「パラメーターのセットを無視する」を参照してください。  
  
 **SQLExecute**または**SQLExecDirect**がSQL_ERRORを返す場合、IPD のSQL_DESC_ARRAY_STATUS_PTR フィールドが指す配列内の要素には、SQL_PARAM_ERROR、SQL_PARAM_SUCCESS、SQL_PARAM_SUCCESS_WITH_INFO、SQL_PARAM_UNUSED、またはSQL_PARAM_DIAG_UNAVAILABLEが含まれます。  
  
 この配列の各要素について、診断データ構造体には 1 つ以上の状態レコードが含まれます。 構造体のSQL_DIAG_ROW_NUMBERフィールドは、エラーの原因となったパラメーター値の行番号を示します。 エラーの原因となったパラメータの行の特定のパラメータを特定できる場合は、パラメータ番号がSQL_DIAG_COLUMN_NUMBERフィールドに入力されます。  
  
 **SQL_PARAM_UNUSEDは、SQLExecute**または**SQLExecDirect**を強制的に中止する以前のパラメーターでエラーが発生したために、パラメーターが使用されていない場合に入力されます。 たとえば **、50**個のパラメーターがあり、SQLExecute または**SQLExecDirect**が中止する原因となった 40 番目のパラメーター セットの実行中にエラーが発生した場合、SQL_PARAM_UNUSEDは、パラメーター 41 から 50 の状態配列に入力されます。  
  
 SQL_PARAM_DIAG_UNAVAILABLEは、ドライバーがパラメーターの配列をモノリシック単位として扱う場合に入力されるため、このパラメーター レベルのエラー情報は生成されません。  
  
 単一のパラメーター・セットの処理でエラーが発生した場合、配列内の後続のパラメーター・セットの処理が停止します。 その他のエラーは、後続のパラメーターの処理には影響しません。 どのエラーが処理を停止するのかは、ドライバー定義です。 処理が停止しない場合、配列内のすべてのパラメーターが処理され、SQL_SUCCESS_WITH_INFOがエラーの結果として返され、SQL_ATTR_PARAMS_PROCESSED_PTRによって定義されたバッファーは、処理されたパラメーターのセットの合計数 (SQL_ATTR_PARAMSET_SIZE ステートメント属性で定義された値) に設定されます。  
  
> [!CAUTION]  
>  パラメータ配列の処理でエラーが発生した場合の ODBC 動作は、ODBC 3 では異なります。*x*は ODBC 2 の場合よりもです。*x .* ODBC 2 で。*x*を指定すると、関数はSQL_ERROR返され、処理は中止されました。 **SQLParamOptions**の*pirow*引数が指すバッファーには、エラー行の番号が含まれていました。 ODBC 3 で。*x*を指定すると、関数はSQL_SUCCESS_WITH_INFOを返し、処理は停止または続行する可能性があります。 続行すると、SQL_ATTR_PARAMS_PROCESSED_PTRで指定されたバッファーは、エラーが発生したパラメーターを含め、処理されたすべてのパラメーターの値に設定されます。 この動作の変更は、既存のアプリケーションに問題を引き起こす可能性があります。  
  
 SQL_ERRORまたはSQL_NEED_DATAが返される場合など、パラメーター配列内のすべてのパラメーター セットの処理を完了する前に**SQLExecute**または**SQLExecDirect**が戻ると、状態配列には、既に処理されているパラメーターの状態が含まれます。 IPD の SQL_DESC_ROWS_PROCESSED_PTR フィールドが指す場所には、SQL_ERRORまたはSQL_NEED_DATAエラー コードの原因となったパラメータ配列内の行番号が含まれています。 パラメーターの配列が SELECT ステートメントに送信されると、状態の配列の値の可用性はドライバー定義します。ステートメントが実行された後、または結果セットがフェッチされた後に使用できます。  
  
## <a name="ignoring-a-set-of-parameters"></a>パラメーターのセットを無視する

 APD のSQL_DESC_ARRAY_STATUS_PTR フィールド (SQL_ATTR_PARAM_STATUS_PTR ステートメント属性によって設定される) を使用して、SQL ステートメント内のバインドされたパラメーターのセットを無視することを示すことができます。 実行時に 1 つ以上のパラメーターセットを無視するようにドライバーに指示するには、アプリケーションで次の手順を実行する必要があります。  
  
1.  ステータス情報を格納する SQLUSMALLINT 値の配列を指す APD のSQL_DESC_ARRAY_STATUS_PTRヘッダー フィールドを設定するには **、SQLSetDescField**を呼び出します。 このフィールドは、SQL_ATTR_PARAM_OPERATION_PTRの*属性*を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
2.  APD のSQL_DESC_ARRAY_STATUS_PTRフィールドで定義される配列の各要素を次の 2 つの値のいずれかに設定します。  
  
    -   SQL_PARAM_IGNORE、行がステートメント実行から除外されることを示します。  
  
    -   SQL_PARAM_PROCEED、行がステートメント実行に含まれることを示します。  
  
3.  準備されたステートメントを実行するには **、SQLExecDirect**または**SQLExecute**を呼び出します。  
  
 APD のSQL_DESC_ARRAY_STATUS_PTR フィールドで定義されたアレイには、次の規則が適用されます。  
  
-   ポインターは、既定では null に設定されています。  
  
-   ポインターが null の場合、すべての要素がSQL_ROW_PROCEEDに設定されているかのように、すべてのパラメーターのセットが使用されます。  
  
-   要素をSQL_PARAM_PROCEEDに設定しても、その特定のパラメーター セットが操作で使用されるとは保証されません。  
  
-   SQL_PARAM_PROCEEDは、ヘッダー ファイルで 0 として定義されます。  
  
 アプリケーションは、IRD のSQL_DESC_ARRAY_STATUS_PTR フィールドが指す配列と同じ配列を指すように、APD のSQL_DESC_ARRAY_STATUS_PTRフィールドを設定できます。 これは、パラメータを行データにバインドする場合に便利です。 その後、行データのステータスに従ってパラメータを無視できます。 SQL_PARAM_IGNOREに加えて、次のコードは、SQL ステートメント内のパラメーター (SQL_ROW_DELETED、SQL_ROW_UPDATED、およびSQL_ROW_ERROR) を無視します。 SQL_PARAM_PROCEEDに加えて、次のコードによって、SQL ステートメントが SQL_ROW_SUCCESS、SQL_ROW_SUCCESS_WITH_INFO、およびSQL_ROW_ADDED処理を続行します。  
  
## <a name="rebinding-parameters"></a>パラメーターの再バインド

 アプリケーションは、バインディングを変更するために、次の 2 つの操作のいずれかを実行できます。  
  
-   **SQLBindParameter**を呼び出して、既にバインドされている列の新しいバインドを指定します。 ドライバーは、古いバインドを新しいバインドで上書きします。  
  
-   **SQLBindParameter**へのバインディング呼び出しで指定されたバッファー アドレスに追加するオフセットを指定します。 詳細については、次の「オフセットを使用して再バインドする」を参照してください。  
  
## <a name="rebinding-with-offsets"></a>オフセットを使用した再バインド

 パラメーターの再バインドは、アプリケーションに多数のパラメーターを含むことができるバッファー域のセットアップがあるが **、SQLExecDirect**または**SQLExecute**の呼び出しでは、パラメーターのほんの一部しか使用できない場合に特に便利です。 バッファー領域の残りのスペースは、オフセットによって既存のバインディングを変更することで、次のパラメーター・セットに使用できます。  
  
 APD のSQL_DESC_BIND_OFFSET_PTRヘッダー フィールドは、バインディング オフセットを指します。 フィールドが null 以外の場合、ドライバーはポインターを逆参照し、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTRフィールドの値のいずれも null ポインターでない場合は、実行時に記述子レコード内のこれらのフィールドに逆参照値を追加します。 新しいポインター値は、SQL ステートメントの実行時に使用されます。 オフセットは、再バインド後も有効です。 SQL_DESC_BIND_OFFSET_PTRはオフセット自体ではなくオフセットへのポインターであるため、アプリケーションは、記述子フィールドを変更するために[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)または[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)を呼び出すことなく、オフセットを直接変更できます。 ポインターは、既定では null に設定されています。 ARD のSQL_DESC_BIND_OFFSET_PTR フィールドは[、SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)への呼び出しまたは SQL_ATTR_PARAM_BIND_OFFSET_PTR の*fAttribute*を使用した[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)の呼び出しによって設定できます。  
  
 バインディング オフセットは、常にSQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTRフィールドの値に直接追加されます。 オフセットが別の値に変更された場合でも、新しい値は各記述子フィールドの値に直接追加されます。 新しいオフセットは、フィールド値とそれ以前のオフセットの合計には追加されません。  
  
## <a name="descriptors"></a>記述子

 パラメーターのバインド方法は、APD および IPD のフィールドによって決定されます。 **SQLBindParameter**の引数は、これらの記述子フィールドを設定するために使用されます。 **SQLBindParameter**関数によってフィールドを設定することもできますが、アプリケーションは SQLBindParameter を呼び出すために記述子ハンドルを取得する必要がないため **、SQLBindParameter**の**SQLBindParameter**方が効率的です。  
  
> [!CAUTION]  
>  1 つのステートメントに対して**SQLBindParameter**を呼び出すと、他のステートメントに影響を与える可能性があります。 これは、ステートメントに関連付けられた ARD が明示的に割り当てられ、他のステートメントにも関連付けられている場合に発生します。 **SQLBindParameter は**APD のフィールドを変更するため、この記述子が関連付けられているすべてのステートメントに変更が適用されます。 これが必要な動作でない場合、アプリケーションは**SQLBindParameter**を呼び出す前に、他のステートメントからこの記述子を切り離す必要があります。  
  
 概念的には **、SQLBindParameter**は次の手順を順番に実行します。  
  
1.  APD ハンドルを取得するために[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)を呼び出します。  
  
2.  呼び出しは、APD のSQL_DESC_COUNT フィールドを取得するために[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)を呼び出し、引数*の*値がSQL_DESC_COUNTの値を超えた場合は、*列番号*にSQL_DESC_COUNTの値を増やすために**SQLSetDescField**を呼び出します。  
  
3.  APD の次のフィールドに値を割り当てる[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)を複数回呼び出します。  
  
    -   *ValueType*が日時または間隔のサブタイプの簡潔な識別子の 1 つである場合、SQL_DESC_TYPEをそれぞれSQL_DATETIME または SQL_INTERVAL に設定し、SQL_DESC_CONCISE_TYPEを簡潔な識別子に設定し、SQL_DESC_DATETIME_INTERVAL_CODEに対応する日時または間隔サブコードに設定することを除き、SQL_DESC_TYPEとSQL_DESC_CONCISE_TYPEを*ValueType*の値に設定します。  
  
    -   SQL_DESC_OCTET_LENGTHフィールドを*BufferLength*の値に設定します。  
  
    -   SQL_DESC_DATA_PTRフィールドを *[パラメーター値*] の値に設定します。  
  
    -   SQL_DESC_OCTET_LENGTH_PTR フィールドを*StrLen_or_Ind*の値に設定します。  
  
    -   SQL_DESC_INDICATOR_PTR フィールドも*StrLen_or_Ind*の値に設定します。  
  
     *StrLen_or_Ind*パラメーターは、標識情報とパラメーター値の長さの両方を指定します。  
  
4.  IPD ハンドルを取得するために[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)を呼び出します。  
  
5.  呼び出しは、IPD のSQL_DESC_COUNT フィールドを取得するために[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)を呼び出し、引数*の*値がSQL_DESC_COUNTの値を超えた場合は、*列番号*にSQL_DESC_COUNTの値を増やすために**SQLSetDescField**を呼び出します。  
  
6.  IPD の次のフィールドに値を割り当てる[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)を複数回呼び出します。  
  
    -   SQL_DESC_TYPEおよびSQL_DESC_CONCISE_TYPEを*ParameterType*の値に設定しますが *、ParameterType*が日時または間隔のサブタイプの簡潔な識別子の 1 つである場合、SQL_DESC_TYPEをそれぞれSQL_DATETIME または SQL_INTERVAL に設定し、SQL_DESC_CONCISE_TYPEを簡潔な識別子に設定し、対応する日時または間隔サブコードにSQL_DESC_DATETIME_INTERVAL_CODEを設定します。  
  
    -   *ParameterType*に応じて、1 つ以上のSQL_DESC_LENGTH、SQL_DESC_PRECISION、およびSQL_DESC_DATETIME_INTERVAL_PRECISIONを設定します。  
  
    -   SQL_DESC_SCALEを*10 進数*の値に設定します。  
  
 **SQLBindParameter**の呼び出しが失敗した場合、APD で設定した記述子フィールドの内容は未定義になり、APD のSQL_DESC_COUNTフィールドは変更されません。 さらに、IPD 内の適切なレコードのSQL_DESC_LENGTH、SQL_DESC_PRECISION、SQL_DESC_SCALE、およびSQL_DESC_TYPEフィールドは未定義であり、IPD のSQL_DESC_COUNTフィールドは変更されません。  
  
## <a name="conversion-of-calls-to-and-from-sqlsetparam"></a>呼び出しの変換との呼び出しの変換

 ODBC 1.0 アプリケーションが ODBC 3 で**SQLSetParam**を呼び出すとします。*x*ドライバ、ODBC 3.*x*ドライバー マネージャーは、次の表に示すように呼び出しをマップします。  
  
|ODBC 1.0 アプリケーションによる呼び出し|ODBC 3 を呼び出します。*x*ドライバ|  
|----------------------------------|-------------------------------|  
|ステートメントハンドル、パラメーター番号、値型、パラメーター型、長精度、パラメーター スケール、パラメーター値Ptr、StrLen_or_IndPtr)。|ステートメントハンドル、パラメーター番号、SQL_PARAM_INPUT_OUTPUT、値型、パラメーター型、*列サイズ**、10 進数*、パラメーター値ptr、SQL_SETPARAM_VALUE_MAX、StrLen_or_IndPtr)。|  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションが、データを ORDERS テーブルに挿入する SQL ステートメントを準備しています。 ステートメント内の各パラメーターに対して、アプリケーションは**SQLBindParameter**を呼び出して、ODBC C データ型とパラメーターの SQL データ型を指定し、バッファーを各パラメーターにバインドします。 アプリケーションは、データの各行に対して、各パラメーターにデータ値を割り当て **、SQLExecute**を呼び出してステートメントを実行します。  
  
 次のサンプルでは、Northwind データベースに関連付けられている Northwind という名前の ODBC データ ソースがコンピュータ上に用意されていることを前提としています。  
  
 その他のコード例については、「 [SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md) [、SQL プロシージャ関数](../../../odbc/reference/syntax/sqlprocedures-function.md) [、SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)、および[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。  
  
```cpp
// SQLBindParameter_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
#define EMPLOYEE_ID_LEN 10  
  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLRETURN retcode;  
SQLHSTMT hstmt = NULL;  
SQLSMALLINT sCustID;  
  
SQLCHAR szEmployeeID[EMPLOYEE_ID_LEN];  
SQL_DATE_STRUCT dsOrderDate;  
SQLINTEGER cbCustID = 0, cbOrderDate = 0, cbEmployeeID = SQL_NTS;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, EMPLOYEE_ID_LEN, 0, szEmployeeID, 0, &cbEmployeeID);  
   retcode = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sCustID, 0, &cbCustID);  
   retcode = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TIMESTAMP, sizeof(dsOrderDate), 0, &dsOrderDate, 0, &cbOrderDate);  
  
   retcode = SQLPrepare(hstmt, (SQLCHAR*)"INSERT INTO Orders(CustomerID, EmployeeID, OrderDate) VALUES (?, ?, ?)", SQL_NTS);  
  
   strcpy_s((char*)szEmployeeID, _countof(szEmployeeID), "BERGS");  
   sCustID = 5;  
   dsOrderDate.year = 2006;  
   dsOrderDate.month = 3;  
   dsOrderDate.day = 17;  
  
   retcode = SQLExecute(hstmt);  
}  
```  
  
## <a name="code-example"></a>コード例

 次の例では、アプリケーションは名前付きパラメーターを使用して SQL Server ストアド プロシージャを実行します。  
  
```cpp
// SQLBindParameter_Function_2.cpp  
// compile with: ODBC32.lib  
// sample assumes the following stored procedure:  
// use northwind  
// DROP PROCEDURE SQLBindParameter  
// GO  
//   
// CREATE PROCEDURE SQLBindParameter @quote int  
// AS  
// delete from orders where OrderID >= @quote  
// GO  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
SQLHDESC hIpd = NULL;  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLRETURN retcode;  
SQLHSTMT hstmt = NULL;  
SQLCHAR szQuote[50] = "100084";  
SQLINTEGER cbValue = SQL_NTS;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retcode = SQLPrepare(hstmt, (SQLCHAR*)"{call SQLBindParameter(?)}", SQL_NTS);  
   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 50, 0, szQuote, 0, &cbValue);  
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &hIpd, 0, 0);  
   retcode = SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);  
  
   retcode = SQLExecute(hstmt);  
}  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ステートメント内のパラメーターに関する情報を返す|[SQLDescribeParam 関数](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|ステートメントでのパラメーター・バッファーの解放|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|ステートメント・パラメーターの数を戻す|[SQLNumParams 関数](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|データを送信する次のパラメータを返す|[SQLParamData 関数](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|複数のパラメーター値の指定|[SQLParamOptions 関数](../../../odbc/reference/syntax/sqlparamoptions-function.md)|  
|実行時にパラメータデータを送信する|[SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>参照

 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
