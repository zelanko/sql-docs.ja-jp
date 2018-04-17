---
title: SQLBindParameter 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLBindParameter
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBindParameter
helpviewer_keywords:
- SQLBindParameter function [ODBC]
ms.assetid: 38349d4b-be03-46f9-9d6a-e50dd144e225
caps.latest.revision: 52
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 54a22ecb571f6a6831023ee5c5d6c18149bff575
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlbindparameter-function"></a>SQLBindParameter 関数
**準拠**  
 バージョンで導入されました ODBC 2.0 Standards 準拠: ODBC。  
  
 **概要**  
 **SQLBindParameter**バッファーを SQL ステートメントにパラメーター マーカーにバインドします。 **SQLBindParameter**基になるドライバーが Unicode データをサポートしていない場合でも、Unicode の C データ型へのバインドをサポートしています。  
  
> [!NOTE]  
>  この関数は、ODBC 1.0 関数を置き換えます**SQLSetParam**です。 詳細については、「コメント」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *ParameterNumber*  
 [入力]パラメーターの数、順序付けに順番にパラメーター、昇順に 1 から始まります。  
  
 *InputOutputType*  
 [入力]パラメーターの型。 詳細については、次を参照してください。"*InputOutputType*引数"で"コメント"です。  
  
 *ValueType*  
 [入力]パラメーターの C データ型。 詳細については、次を参照してください。"*ValueType*引数"で"コメント"です。  
  
 *ParameterType*  
 [入力]パラメーターの SQL データ型です。 詳細については、次を参照してください。"*ParameterType*引数"で"コメント"です。  
  
 *ColumnSize*  
 [入力]対応するパラメーター マーカーの式または列のサイズ。 詳細については、次を参照してください。"*ColumnSize*引数"で"コメント"です。  
  
 アプリケーションは、64 ビット Windows オペレーティング システムで実行される場合は、次を参照してください。 [ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)です。  
  
 *DecimalDigits*  
 [入力]対応するパラメーター マーカーの式または列の 10 進数字です。 列のサイズの詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)です。  
  
 *ParameterValuePtr*  
 [遅延の入力]パラメーターのデータ バッファーへのポインター。 詳細については、次を参照してください。"*ParameterValuePtr*引数"で"コメント"です。  
  
 *BufferLength*  
 [入力/出力]長さ、 *ParameterValuePtr*バッファーのバイト単位です。 詳細については、次を参照してください。"*BufferLength*引数"で"コメント"です。  
  
 参照してください[ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)、64 ビット オペレーティング システム、アプリケーションが実行される場合。  
  
 *StrLen_or_IndPtr*  
 [遅延の入力]パラメーターの長さを格納するバッファーへのポインター。 詳細については、次を参照してください。"*StrLen_or_IndPtr*引数"で"コメント"です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLBindParameter** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLBindParameter**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|識別されるデータ型、 *ValueType*引数で識別されるデータ型に変換することはできません、 *ParameterType*引数。 このエラーは、によって返される可能性がありますに注意してください**SQLExecDirect**、 **SQLExecute**、または**SQLPutData**ではなく、実行時に**SQLBindParameter**.|  
|07009|無効な記述子のインデックス|引数の指定された値 (DM) *ParameterNumber* 1 より小さいをでした。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、**MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY003|無効なアプリケーション バッファーの種類|引数に指定された値*ValueType*有効な C データ型または SQL_C_DEFAULT ありませんでした。|  
|HY004|無効な SQL データ型|引数が指定された値*ParameterType*が ODBC SQL データ型の有効な識別子でも、ドライバーでサポートされている個々 のドライバーの SQL データ型識別子。|  
|HY009|無効な引数の値|(DM) 引数*ParameterValuePtr*が null ポインターの場合、引数*StrLen_or_IndPtr*が null ポインターの場合と、引数*InputOutputType* SQL_PARAM_ でした出力です。<br /><br /> (DM) SQL_PARAM_OUTPUT 場所引数*ParameterValuePtr*が null ポインターでは、C 型が char 型または binary、および、BufferLength (*cbValueMax*) が 0 より大きい値です。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数ではときに実行されている**SQLBindParameter**が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY021|不整合な記述子情報|整合性チェック中にチェック記述子の情報が一致していません。 (「一貫性チェック」のセクションを参照して**SQLSetDescField**)。<br /><br /> 引数が指定された値*DecimalDigits*で指定された SQL データ型の列のデータ ソースによってサポートされる値の範囲外でした、 *ParameterType*引数。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) の値*BufferLength*が 0 未満です。 (SQL_DESC_DATA_PTR フィールドの説明を参照して**SQLSetDescField**)。|  
|HY104|有効桁数または小数点以下桁数の値が無効です。|引数が指定された値*ColumnSize*または*DecimalDigits*で指定された SQL データ型の列のデータ ソースによってサポートされる値の範囲外でした、 *ParameterType*引数。|  
|HY105|無効なパラメーターの型|引数の指定された値 (DM) *InputOutputType*が無効です。 (「コメント」を参照してください)|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースは、引数に指定された値の組み合わせで指定された変換をサポートしていない*ValueType*引数が指定されたドライバー固有の値と*ParameterType*.<br /><br /> 引数が指定された値*ParameterType* ODBC SQL データ型の有効な識別子が ODBC のバージョンは、ドライバーでサポートされていますが、ドライバーまたはデータ ソースによってサポートされていませんでした。<br /><br /> ドライバーには、ODBC 2 のみがサポートしています。*x*と引数*ValueType*次のいずれかの。<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> 表示されているすべての間隔 C データ型と[C データ型](../../../odbc/reference/appendixes/c-data-types.md)付録 d: データ型にします。<br /><br /> ドライバーのみがサポート 3.50、および引数の前に ODBC バージョン*ValueType* SQL_C_GUID がします。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 アプリケーションが呼び出す**SQLBindParameter** SQL ステートメントの各パラメーター マーカーをバインドします。 バインディングは、アプリケーションが有効になります**SQLBindParameter** 、もう一度呼び出す**SQLFreeStmt** SQL_RESET_PARAMS オプション、または呼び出しで**SQLSetDescField**にAPD の SQL_DESC_COUNT ヘッダー フィールドを 0 に設定します。  
  
 パラメーターの詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)です。 パラメーターのデータ型とパラメーター マーカーの詳細については、次を参照してください。[パラメーターのデータ型](../../../odbc/reference/appendixes/parameter-data-types.md)と[パラメーター マーカー](../../../odbc/reference/appendixes/parameter-markers.md)付録 c: SQL の文法でします。  
  
## <a name="parameternumber-argument"></a>ParameterNumber 引数  
 場合*ParameterNumber*への呼び出しで**SQLBindParameter** SQL_DESC_COUNT の値よりも大きい**SQLSetDescField** SQL_DESC_ の価値を高めるために呼び出されるカウントを*ParameterNumber*です。  
  
## <a name="inputoutputtype-argument"></a>InputOutputType 引数  
 *InputOutputType*引数パラメーターの型を指定します。 この引数は、IPD の SQL_DESC_PARAMETER_TYPE フィールドを設定します。 SQL ステートメントを呼び出すことはありません、プロシージャなどのすべてのパラメーター**挿入**ステートメント、*入力 * * パラメーター*です。 プロシージャ呼び出しのパラメーター入力として使用できる、入力/出力、または出力パラメーターです。 (アプリケーションを呼び出す**SQLProcedureColumns** ; プロシージャ呼び出しでパラメーターの型を特定の型を特定できないパラメーターは入力パラメーターと見なされます)。  
  
 *InputOutputType*引数は、次の値のいずれか。  
  
-   SQL_PARAM_INPUT です。 パラメーターなど、プロシージャを呼び出しませんする SQL ステートメント内のパラメーターをマークする、**挿入**ステートメント、または、プロシージャの入力パラメーターをマークします。 などのパラメーター**従業員の値に挿入 (しますか?、?、?)**は、入力パラメーターに対しでは、パラメーター **{AddEmp を呼び出す (しますか?、?、?)}**指定できますが、必ずしも、入力パラメーターではありません。  
  
     ドライバーが、データ ソースにパラメーターのデータを送信、ステートメントの実行時\* *ParameterValuePtr*バッファーは有効な入力値を含める必要があります、または **StrLen_or_IndPtr*バッファーが SQL_NULL_DATA、生成される場合、または、SQL_LEN_DATA_AT の結果を含める必要があります_Exec 系マクロです。  
  
     設定されている場合は、プロシージャ呼び出しでパラメーターの型を判断できないのは、アプリケーション、 *InputOutputType* SQL_PARAM_INPUT 以外に、データ ソースは、パラメーターの値を返す場合、ドライバーにそれを廃棄します。  
  
-   SQL_PARAM_INPUT_OUTPUT です。 パラメーターは、プロシージャ内の入力/出力パラメーターをマークします。 内のパラメーターなど、 **{call GetEmpDept(?)}**入力/出力パラメーターで、従業員の名前を受け取り、従業員の部署の名前を返します。  
  
     ドライバーが、データ ソースにパラメーターのデータを送信、ステートメントの実行時\* *ParameterValuePtr*バッファーは有効な入力値を含める必要がありますまたは\* *StrLen_or_IndPtr* SQL_NULL_DATA、生成される場合、または結果のバッファーを含める必要がありますSQL_LEN_DATA_AT_EXEC マクロです。 ステートメントが実行された後に、ドライバー、パラメーターのデータ、アプリケーションに返すです。ドライバーの設定、データ ソースが入力/出力パラメーターの値を返さない場合、**StrLen_or_IndPtr* SQL_NULL_DATA をバッファーします。  
  
    > [!NOTE]  
    >  ODBC 1.0 アプリケーションを呼び出すと**SQLSetParam**への呼び出しにこのドライバー マネージャーによって ODBC 2.0 のドライバーでは、変換**SQLBindParameter**を*InputOutputType*引数は、SQL_PARAM_INPUT_OUTPUT に設定されます。  
  
-   SQL_PARAM_OUTPUT です。 パラメーターは、プロシージャまたはプロシージャの出力パラメーターの戻り値を示しますどちらの場合、これらと呼ばれます。*出力パラメーター*です。 内のパラメーターなど、 **{? = GetNextEmpID を呼び出す}**出力パラメーターで、[次へ] の従業員 ID を返します。  
  
     ステートメントが実行された後に、ドライバーを返しますパラメーターのデータ、アプリケーションにしない限り、 *ParameterValuePtr*と*StrLen_or_IndPtr*引数が両方とも null ポインターをその場合は、ドライバーは、出力値を破棄します。 ドライバーの設定、データ ソースが出力パラメーターの値を返さない場合、**StrLen_or_IndPtr* SQL_NULL_DATA をバッファーします。  
  
-   SQL_PARAM_INPUT_OUTPUT_STREAM です。 入力/出力パラメーターをストリーミングすることを示します。 **SQLGetData**部分のパラメーター値を読み取ることができます。 *BufferLength*バッファーの長さは、の呼び出しで判断するために無視**SQLGetData**です。 値、 *StrLen_or_IndPtr*バッファーが SQL_NULL_DATA、SQL_DEFAULT_PARAM、生成される場合、または、SQL_LEN_DATA_AT_EXEC マクロの結果を含める必要があります。 パラメーターは、出力にストリーミングされる場合、入力で、実行時データ (DAE) パラメーターとしてバインドする必要があります。 *ParameterValuePtr*によって返される任意の null ポインター値を指定できます**SQLParamData**に渡されたトークンの値を持つユーザー定義として*ParameterValuePtr*の両方の入力と出力です。 詳細については、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)です。  
  
-   SQL_PARAM_OUTPUT_STREAM です。 SQL_PARAM_INPUT_OUTPUT_STREAM、出力パラメーターのと同じです。 **StrLen_or_IndPtr*入力では無視されます。  
  
 次の表に、さまざまな組み合わせの*InputOutputType*と **StrLen_or_IndPtr*:  
  
|*InputOutputType*|**StrLen_or_IndPtr*|結果|ParameterValuePtr をコメントします。|  
|-----------------------|----------------------------|-------------|---------------------------------|  
|SQL_PARAM_INPUT|SQL_LEN_DATA_AT_EXEC (*len*) または SQL_DATA_AT_EXEC|入力のパーツ|*ParameterValuePtr*によって返される任意のポインター値を指定できます**SQLParamData**に渡されたトークンの値を持つユーザー定義として*ParameterValuePtr*です。|  
|SQL_PARAM_INPUT|いない SQL_LEN_DATA_AT_EXEC (*len*) または SQL_DATA_AT_EXEC|入力バッファーをバインドします。|*ParameterValuePtr*入力バッファーのアドレスです。|  
|SQL_PARAM_OUTPUT|入力には無視されます。|出力バッファーをバインドします。|*ParameterValuePtr*出力バッファーのアドレスです。|  
|SQL_PARAM_OUTPUT_STREAM|入力には無視されます。|ストリーミングされる出力|*ParameterValuePtr*によって返される任意のポインター値を指定できます**SQLParamData**に渡されたトークンの値を持つユーザー定義として*ParameterValuePtr*です。|  
|SQL_PARAM_INPUT_OUTPUT|SQL_LEN_DATA_AT_EXEC (*len*) または SQL_DATA_AT_EXEC|入力のパーツと出力バインドされたバッファー|*ParameterValuePtr*も関数によって返される出力バッファーのアドレスは、 **SQLParamData**に渡されたトークンの値を持つユーザー定義として*ParameterValuePtr*です。|  
|SQL_PARAM_INPUT_OUTPUT|いない SQL_LEN_DATA_AT_EXEC (*len*) または SQL_DATA_AT_EXEC|入力は、バッファーと出力バインドされたバッファーのバインド|*ParameterValuePtr*共有入力/出力バッファーのアドレスです。|  
L_PARAM_INPUT_OUTPUT_STREAM|SQL_LEN_DATA_AT_EXEC (*len*) または SQL_DATA_AT_EXEC|入力のパーツとストリーミングされる出力|*ParameterValuePtr*によって返される任意の null ポインター値を指定できます**SQLParamData**に渡されたトークンの値を持つユーザー定義として*ParameterValuePtr*の両方の入力出力します。|  
  
> [!NOTE]  
>  ドライバーは、アプリケーションが出力パラメーターまたは入出力パラメーターをバインドそしてときにどの SQL 型が許可を決める必要があります。 ドライバー マネージャーでは、無効な SQL 型のエラーは生成されません。  
  
## <a name="valuetype-argument"></a>値型引数  
 *ValueType*引数パラメーターの C データ型を指定します。 この引数は、APD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE、および SQL_DESC_DATETIME_INTERVAL_CODE のフィールドを設定します。 これは内の値のいずれかをする必要があります、 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)付録 d: データ型のセクションでします。  
  
 場合、 *ValueType* interval データ型の SQL_DESC_TYPE フィールドのいずれかの引数は、 *ParameterNumber* APD のレコードが SQL_INTERVAL に設定されている、APD の SQL_DESC_CONCISE_TYPE フィールドに設定されています。簡潔な interval データ型との SQL_DESC_DATETIME_INTERVAL_CODE フィールド、 *ParameterNumber*レコードが特定の間隔のデータ型のサブコードに設定します。 (を参照してください[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md))。データの先頭の有効桁数 (2) と既定の間隔 (秒) の有効桁数 (6)、APD の SQL_DESC_DATETIME_INTERVAL_PRECISION および SQL_DESC_PRECISION フィールドで設定されている、それぞれ既定の間隔が使用されます。 いずれかの既定の有効桁数が適切でない場合、アプリケーションを明示的に設定記述子フィールドへの呼び出しによって**SQLSetDescField**または**SQLSetDescRec**です。  
  
 場合、 *ValueType*引数は、の SQL_DESC_TYPE フィールドの datetime データ型のいずれか、 *ParameterNumber* APD のレコードが SQL_DATETIME、のSQL_DESC_CONCISE_TYPEフィールドに設定されている*ParameterNumber* APD のレコードが、簡潔な datetime C データ型、およびの SQL_DESC_DATETIME_INTERVAL_CODE フィールドに設定されている、 *ParameterNumber*レコードが特定の datetime のサブコードに設定されています。データ型です。 (を参照してください[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md))。  
  
 場合、 *ValueType*引数、SQL_C_NUMERIC データ型は、既定の有効桁数 (これは、ドライバーで定義)、既定の小数点以下桁数 (0)、APD の SQL_DESC_PRECISION および SQL_DESC_SCALE フィールドで設定されているがデータに使用します。 既定の有効桁数または小数点以下桁数が適切でない場合、アプリケーションを明示的に設定記述子フィールドへの呼び出しによって**SQLSetDescField**または**SQLSetDescRec**です。  
  
 SQL_C_DEFAULT は、すべてのユーザーを SQL データ型で指定の C の既定のデータ型から転送されるパラメーターの値を指定します*ParameterType*です。  
  
 拡張の C データ型を指定することもできます。 詳細については、次を参照してください。 [ODBC における C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)です。  
  
 詳細については、次を参照してください。 [C データ型の既定の](../../../odbc/reference/appendixes/default-c-data-types.md)、[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)、および[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)付録 d: データ型にします。  
  
## <a name="parametertype-argument"></a>ParameterType 引数  
 これに示された値のいずれかをする必要があります、 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型、またはこれのセクションでは、ドライバー固有の値である必要があります。 この引数は、IPD の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE、および SQL_DESC_DATETIME_INTERVAL_CODE フィールドを設定します。  
  
 場合、 *ParameterType* datetime 識別子のいずれかの引数は、sql_datetime 型に、IPD の SQL_DESC_TYPE フィールドが設定されている、簡潔な datetime の SQL データ型、および、SQL_DESC_ に、IPD の SQL_DESC_CONCISE_TYPE フィールドが設定されています。DATETIME_INTERVAL_CODE フィールドは、適切な datetime サブコード値に設定されます。  
  
 場合*ParameterType*は 1 つ SQL_INTERVAL に設定されている、IPD の SQL_DESC_TYPE フィールド間隔識別子の簡潔な SQL interval データ型と、SQL_DESC_DATETIME_ に、IPD の SQL_DESC_CONCISE_TYPE フィールドが設定されています。IPD の INTERVAL_CODE フィールドは、適切な間隔サブコードに設定されます。 間隔の主要な精度、IPD の SQL_DESC_DATETIME_INTERVAL_PRECISION フィールドが設定され、SQL_DESC_PRECISION フィールドに設定されている間隔の秒の有効桁数に、該当する場合。 SQL_DESC_DATETIME_INTERVAL_PRECISION または SQL_DESC_PRECISION の既定値が適切でない場合、アプリケーションを明示的に設定が呼び出すことによって**SQLSetDescField**です。 これらのフィールドのいずれかの詳細については、次を参照してください。 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。  
  
 場合、 *ValueType*引数、SQL_NUMERIC データ型は、既定の有効桁数 (これは、ドライバーで定義)、既定の小数点以下桁数 (0)、IPD の SQL_DESC_PRECISION および SQL_DESC_SCALE フィールドで設定されているがデータに使用します。 既定の有効桁数または小数点以下桁数が適切でない場合、アプリケーションを明示的に設定記述子フィールドへの呼び出しによって**SQLSetDescField**または**SQLSetDescRec**です。  
  
 データを変換する方法については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)と[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)付録 d: データ型にします。  
  
## <a name="columnsize-argument"></a>ColumnSize 引数  
 *ColumnSize*引数が列またはパラメーター マーカー、データ、またはその両方の長さに対応する式のサイズを指定します。 この引数は、SQL データ型に応じて、IPD のさまざまなフィールドを設定します。 (、 *ParameterType*引数)。 このマッピングに、次の規則が適用されます。  
  
-   場合*ParameterType* SQL_CHAR、SQL_VARCHAR、SQL_LONGVARCHAR、sql_binary 型、SQL_VARBINARY、SQL_LONGVARBINARY、またはの値に設定されている、簡潔なSQLdatetimeまたはintervalデータ型に、IPDのSQL_DESC_LENGTHフィールドのいずれか*ColumnSize*です。 (詳細については、次を参照してください、[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にはセクションです。)。  
  
-   場合*ParameterType* SQL_DECIMAL、SQL_NUMERIC、使用できます、SQL_REAL、または SQL_DOUBLE の値に、IPD の SQL_DESC_PRECISION フィールドが設定されている*ColumnSize*です。  
  
-   他のデータ型、 *ColumnSize*引数は無視されます。  
  
 詳細についてを参照してください「を渡すパラメーターの値」とで SQL_DATA_AT_EXEC"*StrLen_or_IndPtr*引数"。  
  
## <a name="decimaldigits-argument"></a>DecimalDigits 引数  
 場合*ParameterType* SQL_TYPE_TIME、SQL_TYPE_TIMESTAMP、SQL_INTERVAL_SECOND、SQL_INTERVAL_DAY_TO_SECOND、SQL_INTERVAL_HOUR_TO_SECOND、または、SQL_INTERVAL_MINUTE_TO_SECOND、IPD の SQL_DESC_PRECISION フィールドが設定されています。*DecimalDigits*です。 場合*ParameterType* SQL_NUMERIC または SQL_DECIMAL には、IPD の SQL_DESC_SCALE フィールドに設定されて*DecimalDigits*です。 他のすべてのデータ型、 *DecimalDigits*引数は無視されます。  
  
## <a name="parametervalueptr-argument"></a>ParameterValuePtr 引数  
 *ParameterValuePtr*引数が指すバッファーされるときに、 **SQLExecute**または**SQLExecDirect**を呼び出すと、パラメーターの実際のデータが含まれています。 データがで指定された形式である必要があります、 *ValueType*引数。 この引数は、APD の SQL_DESC_DATA_PTR フィールドを設定します。 アプリケーション設定、 *ParameterValuePtr* null ポインターの場合と同じくらいに渡す引数 *\*StrLen_or_IndPtr* SQL_NULL_DATA または SQL_DATA_AT_EXEC です。 (これは適用のみを入力パラメーターまたは入出力パラメーターです)。  
  
 場合\* *StrLen_or_IndPtr* 、SQL_LEN_DATA_AT_EXEC の結果である (*長さ*) マクロまたは SQL_DATA_AT_EXEC し*ParameterValuePtr*は、パラメーターに関連付けられているアプリケーション定義のポインターの値。 経由でアプリケーションに返される**SQLParamData**です。 たとえば、 *ParameterValuePtr*パラメーター番号、データへのポインター、またはアプリケーションの入力パラメーターをバインドするために使用する構造体へのポインターなどの 0 以外のトークンがあります。 ただし、その場合、パラメーターは入力/出力パラメーター、 *ParameterValuePtr*出力値を格納するバッファーへのポインターにする必要があります。 SQL_ATTR_PARAMSET_SIZE ステートメント属性の値が 1 より大きい場合は、アプリケーションがと共に、SQL_ATTR_PARAMS_PROCESSED_PTR ステートメント属性によって示される値を使用して、 *ParameterValuePtr*引数。 たとえば、 *ParameterValuePtr*値の配列を指すこともあり、アプリケーションは、配列から、適切な値を取得する SQL_ATTR_PARAMS_PROCESSED_PTR によって示される値を使用する場合があります。 詳細については、「パラメーターの値の引き渡し」このセクションの後半を参照してください。  
  
 場合、 *InputOutputType*引数が SQL_PARAM_INPUT_OUTPUT または SQL_PARAM_OUTPUT、 *ParameterValuePtr*ドライバーが出力値を返すバッファーを指します。 プロシージャが 1 つまたは複数の結果セットを返す場合、 \* *ParameterValuePtr*バッファーはすべての結果セットまたは行カウントが処理されるまでに設定することが保証されません。 処理が完了するまで、バッファーが設定されていない場合、出力パラメーターと戻り値がご利用いただけませんまで**SQLMoreResults** SQL_NO_DATA が返されます。 呼び出す**SQLCloseCursor**または**SQLFreeStmt**オプションの SQL_CLOSE が発生することはこれらの値を破棄します。  
  
 SQL_ATTR_PARAMSET_SIZE ステートメント属性の値が 1 より大きい場合*ParameterValuePtr*配列を指します。 1 つの SQL ステートメントは、パラメーターまたは入出力パラメーターの入力値の完全な配列を処理し、入力/出力の出力値または出力パラメーターの配列を返します。  
  
## <a name="bufferlength-argument"></a>BufferLength 引数  
 文字やバイナリの C データ、 *BufferLength*引数の長さを指定する、 \* *ParameterValuePtr*バッファー (1 つの要素の場合) または、内の要素の長さ\**ParameterValuePtr* (SQL_ATTR_PARAMSET_SIZE ステートメント属性の値が 1 より大きい場合) の配列。 この引数は、APD の SQL_DESC_OCTET_LENGTH レコードのフィールドを設定します。 アプリケーションが、複数の値を指定する場合*BufferLength*内の値の場所を特定するために使用します **ParameterValuePtr*入力と出力の両方の配列。 入力/出力呼び出し力パラメーターの場合は、文字とバイナリの C データ出力を切り捨てるかどうかを決定に使用されます。  
  
-   返される使用可能なバイト数がより大きいまたは等しい場合は、C の文字データの*BufferLength*、内のデータ\* *ParameterValuePtr*に切り捨てられます*BufferLength* null 終端文字の長さ以下は、ドライバーが null で終わるとします。  
  
-   返される使用可能なバイト数がより大きい場合、バイナリの C データの*BufferLength*、内のデータ\* *ParameterValuePtr*に切り捨てられます*BufferLength*バイトです。  
  
 すべての他の種類の C データ、 *BufferLength*引数は無視されます。 長さ、 \* *ParameterValuePtr*バッファー (1 つの要素の場合) または内の要素の長さ、 \* *ParameterValuePtr* (を呼び出す場合の配列**SQLSetStmtAttr**で、*属性*SQL_ATTR_PARAMSET_SIZE パラメーターごとに複数の値を指定の引数) は、C データ型の長さを使用すると見なされます。  
  
 ストリーミングされる出力のストリームの入力/出力パラメーター、 *BufferLength*でバッファーの長さが指定されているために、引数は無視されます**SQLGetData**です。  
  
> [!NOTE]  
>  ODBC 1.0 アプリケーションを呼び出すと**SQLSetParam** ODBC 3 *。x*ドライバー、ドライバー マネージャーに変換しますこのへの呼び出しに**SQLBindParameter**を*BufferLength*引数が SQL_SETPARAM_VALUE_MAX では常にします。 ドライバー マネージャーは、ODBC 3 の場合、エラーを返します。*x*アプリケーション セット*BufferLength* SQL_SETPARAM_VALUE_MAX、ODBC 3 にします*。x*ドライバーを使用してこの ODBC 1.0 アプリケーションによって呼び出されたときを判断します。  
  
> [!NOTE]  
>  **SQLSetParam**、アプリケーションがの長さを指定する方法、**ParameterValuePtr*バッファーに格納できるように、ドライバーは、文字またはバイナリ データ、およびアプリケーションを送信する方法を返すことができます、配列の文字またはドライバーにバイナリ パラメーター値では、ドライバーで定義されています。  
  
## <a name="strlenorindptr-argument"></a>StrLen_or_IndPtr 引数  
 *StrLen_or_IndPtr*引数が指すバッファーされるときに、 **SQLExecute**または**SQLExecDirect**を呼び出すと、次のいずれかが含まれています。 (この引数は、アプリケーション パラメーター ポインターの SQL_DESC_OCTET_LENGTH_PTR および SQL_DESC_INDICATOR_PTR レコード フィールドを設定します)。  
  
-   格納されているパラメーター値の長さ **ParameterValuePtr*です。 これは、文字またはバイナリの C データ以外は無視されます。  
  
-   SQL_NTS です。 パラメーターの値は、null で終わる文字列です。  
  
-   SQL_NULL_DATA です。 パラメーターの値は NULL です。  
  
-   SQL_DEFAULT_PARAM です。 プロシージャでは、アプリケーションから取得した値ではなく、パラメーターの既定値を使用します。 この値は ODBC 標準構文で呼び出されたプロシージャでのみ有効し、場合にのみ、 *InputOutputType*引数は SQL_PARAM_INPUT、SQL_PARAM_INPUT_OUTPUT、または SQL_PARAM_INPUT_OUTPUT_STREAM です。 ときに\* *StrLen_or_IndPtr* SQL_DEFAULT_PARAM は、 *ValueType*、 *ParameterType*、 *ColumnSize*、 *DecimalDigits*、 *BufferLength*、および*ParameterValuePtr*引数が入力パラメーターを無視して、入力の出力パラメーターの値を定義にのみ使用されます/出力パラメーターです。  
  
-   結果の SQL_LEN_DATA_AT_EXEC (*長さ*) マクロです。 パラメーターのデータは送信されます**SQLPutData**です。 場合、 *ParameterType*引数は SQL_LONGVARBINARY、SQL_LONGVARCHAR、または時間の長い、データ ソース固有のデータ型、およびドライバーは"Y"SQL_NEED_LONG_DATA_LEN 情報の種類に対してを返します**SQLGetInfo**、*長さ*; パラメーターに送信されるデータのバイト数は、それ以外の場合、*長さ*負でない値である必要は無視されます。 詳細については、「を渡すパラメーターの値、」このセクションの後半を参照してください。  
  
     たとえば、データのバイト数を 10,000 に送信されることを指定する**SQLPutData** SQL_LONGVARCHAR パラメーターの場合、1 つまたは複数の呼び出しでは、アプリケーション、設定 **StrLen_or_IndPtr*を SQL_LEN_DATA_AT_EXEC (10000)。  
  
-   SQL_DATA_AT_EXEC です。 パラメーターのデータは送信されます**SQLPutData**です。 この値は、ODBC 3 を呼び出すときに、ODBC 1.0 アプリケーションによって使用されます。*x*ドライバー。 詳細については、「を渡すパラメーターの値、」このセクションの後半を参照してください。  
  
 場合*StrLen_or_IndPtr* null ポインターでは、ドライバーでは、すべての入力パラメーター値が NULL 以外であることと文字やバイナリ データが null で終わる前提としています。 場合*InputOutputType* SQL_PARAM_OUTPUT または SQL_PARAM_OUTPUT_STREAM と*ParameterValuePtr*と*StrLen_or_IndPtr*は両方とも null ポインター、ドライバーの破棄出力値。  
  
> [!NOTE]  
>  アプリケーション開発者は、の null ポインターを指定することを強くお勧め*StrLen_or_IndPtr*パラメーターのデータ型の SQL_C_BINARY はときにします。 ドライバーによって SQL_C_BINARY データは予期せず切り捨てられませんようにかどうかを確認する*StrLen_or_IndPtr*有効な長さの値へのポインターを含める必要があります。  
  
 場合、 *InputOutputType*引数は SQL_PARAM_INPUT_OUTPUT、SQL_PARAM_OUTPUT、SQL_PARAM_INPUT_OUTPUT_STREAM、または SQL_PARAM_OUTPUT_STREAM、 *StrLen_or_IndPtr*れるバッファーを指す、ドライバーは SQL_NULL_DATA で返される使用可能なバイト数を返します\* *ParameterValuePtr* (null 終了バイトの文字データを除く)、または SQL_NO_TOTAL (場合に使用できるバイト数戻り値を特定できません)。 プロシージャが 1 つまたは複数の結果セットを返す場合、**StrLen_or_IndPtr*バッファーはすべての結果がフェッチされるまでに設定することが保証されません。  
  
 SQL_ATTR_PARAMSET_SIZE ステートメント属性の値が 1 より大きい場合*StrLen_or_IndPtr* SQLLEN 値の配列を指します。 これらは、このセクションで示した値のいずれかのされ、1 つの SQL ステートメントで処理されます。  
  
## <a name="passing-parameter-values"></a>パラメーター値の受け渡し  
 アプリケーションは、パラメーターの値を渡すことができますに、 \* *ParameterValuePtr*バッファーまたは 1 つまたは複数の呼び出しを**SQLPutData**です。 パラメーターに渡されるデータを含む**SQLPutData**と呼ばれる*実行時データ*パラメーター。 これらは通常は SQL_LONGVARBINARY データ型と SQL_LONGVARCHAR のパラメーターのデータ送信に使用およびその他のパラメーターとを混在させることができます。  
  
 パラメーターの値を渡すには、アプリケーションは、次の一連の手順を実行します。  
  
1.  呼び出し**SQLBindParameter**パラメーターの値のバッファーをバインドするには、各パラメーターの (*ParameterValuePtr*引数) および長さ/インジケーター (*StrLen_or_IndPtr*引数)。 実行時データ パラメーターの*ParameterValuePtr*パラメーター番号やデータへのポインターなど、アプリケーションで定義されたポインター値です。 値は、後で返されるされ、パラメーターを識別するために使用できます。  
  
2.  パラメーター入力および入力/出力パラメーターの値を格納、 \* *ParameterValuePtr*と **StrLen_or_IndPtr*バッファー。  
  
    -   アプリケーションがパラメーター値を配置する通常のパラメーターに対して、 \* *ParameterValuePtr*バッファーと内でその値の長さ、**StrLen_or_IndPtr*バッファー。 詳細については、次を参照してください。[パラメーター値の設定](../../../odbc/reference/develop-app/setting-parameter-values.md)です。  
  
    -   アプリケーションが、SQL_LEN_DATA_AT_EXEC の結果を格納する、実行時データ パラメーターの (*長さ*) でのマクロ (ODBC 2.0 ドライバーを呼び出す) 場合、**StrLen_or_IndPtr*バッファー。  
  
3.  呼び出し**SQLExecute**または**SQLExecDirect** SQL ステートメントを実行します。  
  
    -   実行時データ パラメーターがない場合、プロセスが完了しました。  
  
    -   実行時データ パラメーターがある場合は、SQL_NEED_DATA を返します。  
  
4.  呼び出し**SQLParamData**で指定されたアプリケーション定義の値を取得する、 *ParameterValuePtr*の引数**SQLBindParameter**最初処理する実行時データ パラメーター。 **SQLParamData** SQL_NEED_DATA を返します。  
  
    > [!NOTE]  
    >  値がによって返される実行時データ パラメーターには、実行時データ列が似ています、 **SQLParamData**はごとに異なります。 実行時データ パラメーターと、データを送信する SQL ステートメントのパラメーターには、 **SQLPutData**でステートメントを実行すると**SQLExecDirect**または**SQLExecute**. バインドされている**SQLBindParameter**です。 によって返される値**SQLParamData**へのポインター値が渡された**SQLBindParameter**で、 *ParameterValuePtr*引数。 実行時データ列は列のデータを送信する行セットで**SQLPutData**行が更新または追加**SQLBulkOperations**またはで更新された**SQLSetPos**. バインドされている**SQLBindCol**です。 によって返される値**SQLParamData**内の行のアドレスは、**TargetValuePtr*バッファー (への呼び出しによって設定**SQLBindCol**) を処理しています。  
  
5.  呼び出し**SQLPutData**パラメーターのデータを送信する 1 つ以上の時間。 データ値がより大きい場合、複数の呼び出しが必要な\* *ParameterValuePtr*で指定されたバッファー **SQLPutData**; を複数回呼び出す**SQLPutData**文字、バイナリ、またはデータ ソース固有のデータ型の列に文字データを送信するときにのみ、または列を文字、バイナリ、C のバイナリ データを送信するときに、同じパラメーターは許可されているか、データ ソース固有のデータ型します。  
  
6.  呼び出し**SQLParamData**パラメーターのすべてのデータが送信されたことを通知するには、もう一度です。  
  
    -   複数の実行時データ パラメーターがある場合**SQLParamData**処理するには、SQL_NEED_DATA と [次へ] の実行時データ パラメーターのアプリケーション定義の値を返します。 アプリケーションでは、手順 4. と 5. を繰り返します。  
  
    -   これ以上の実行時データ パラメーターがある場合、プロセスが完了しました。 場合は、ステートメントが正常に実行される、 **SQLParamData** SQL_SUCCESS または; SQL_SUCCESS_WITH_INFO が返されます場合は、実行に失敗しました、SQL_ERROR を返します。 この時点では、 **SQLParamData**ステートメントを実行するために使用する関数によって返される任意の SQLSTATE を返すことができます (**SQLExecDirect**または**SQLExecute**)。  
  
         使用可能な任意の入力/出力パラメーターまたは出力パラメーターの出力値、 \* *ParameterValuePtr*と **StrLen_or_IndPtr*バッファーのアプリケーションは、すべての結果セットを取得した後ステートメントによって生成されます。  
  
 呼び出す**SQLExecute**または**SQLExecDirect**ステートメントによって、SQL_NEED_DATA 状態にします。 この時点では、アプリケーションはのみ呼び出すことができます**SQLCancel**、 **SQLGetDiagField**、 **SQLGetDiagRec**、 **SQLGetFunctions**、 **SQLParamData**、または**SQLPutData**ステートメントを使用して、または*接続ハンドル*ステートメントに関連付けられています。 ステートメントまたはステートメントに関連付けられている接続と共に他の関数を呼び出して、返します SQLSTATE HY010 (関数のシーケンス エラーです)。 状態のときに、SQL_NEED_DATA ステートメント リーフ**SQLParamData**または**SQLPutData** 、エラーを返します**SQLParamData** SQL_SUCCESS、SQL_SUCCESS_WITH_INFO を返しますまたはステートメントが取り消されました。  
  
 アプリケーションを呼び出す場合**SQLCancel**ドライバーがステートメントの実行をキャンセルするときに、ドライバーでは、実行時データ パラメーターのデータが引き続き必要があります、以外の場合は、アプリケーションを呼び出すことができますし、 **SQLExecute**または**SQLExecDirect**もう一度です。  
  
## <a name="retrieving-streamed-output-parameters"></a>ストリーミングされる出力パラメーターを取得します。  
 アプリケーションの設定と*InputOutputType* SQL_PARAM_INPUT_OUTPUT_STREAM または SQL_PARAM_OUTPUT_STREAM には、1 つまたは複数の呼び出しで、出力パラメーターの値を取得**SQLGetData**です。 次の機能への呼び出しに応答 SQL_PARAM_DATA_AVAILABLE が返されます、ドライバーがアプリケーションに返されるストリームの出力パラメーター値を持つ、: **SQLMoreResults**、 **SQLExecute**、および**SQLExecDirect**です。 アプリケーションが呼び出す**SQLParamData**されるパラメーター値が使用できるかを判断します。  
  
 SQL_PARAM_DATA_AVAILABLE とストリーム出力パラメーターの詳細については、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)です。  
  
## <a name="using-arrays-of-parameters"></a>パラメーターの配列の使用  
 アプリケーションでは、パラメーター マーカーとパラメーターの配列でパス ステートメントを準備、ときにこれを実行する 2 つの方法があります。 1 つの方法は、パラメーターの配列とステートメント全体の場合は 1 つのアトミック単位として扱われます、バックエンドの配列の処理機能に依存するドライバーです。 Oracle では、配列の処理機能をサポートするデータ ソースの例を示します。 この機能を実装する別の方法は、ドライバーが SQL ステートメント、パラメーター配列内のパラメーターのセットごとに 1 つの SQL ステートメントのバッチを生成し、バッチを実行するためです。 パラメーターの配列は使用できません、**更新 WHERE CURRENT OF**ステートメントです。  
  
 パラメーターの配列が処理されるときに個々 の結果セット/行数 (1 つは各パラメーター セット) が利用できるまたは結果を設定/行カウントを 1 つにロール アップできます。 オプション、SQL_PARAM_ARRAY_ROW_COUNTS **SQLGetInfo**行カウントがパラメーター (SQL_PARC_BATCH) のセットごとに使用できるか、1 つだけの行の数が使用可能な (SQL_PARC_NO_BATCH) かどうかを示します。  
  
 オプション、SQL_PARAM_ARRAY_SELECTS **SQLGetInfo**パラメーター (SQL_PAS_BATCH) のセットごとの結果セットがあるか、1 つだけの結果セットが使用可能な (SQL_PAS_NO_BATCH) かどうかを示します。 ドライバーでは、結果セットの生成 – ステートメント パラメーターの配列を使って実行することはできません、SQL_PARAM_ARRAY_SELECTS は SQL_PAS_NO_SELECT を返します。  
  
 詳細については、次を参照してください。 [SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)です。  
  
 パラメーターの配列をサポートするためには、SQL_ATTR_PARAMSET_SIZE ステートメント属性は、各パラメーターの値の数を指定に設定されます。 フィールドが 1 より大きい場合、APD の SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR フィールドは配列を指す必要があります。 各配列の基数は、SQL_ATTR_PARAMSET_SIZE の値と同じです。  
  
 APD の SQL_DESC_ROWS_PROCESSED_PTR フィールドは、処理された、エラーのセットを含むパラメーターのセットの数を格納するバッファーを指します。 各パラメーターのセットが処理されると、ドライバーは、バッファー内の新しい値を格納します。 これが null ポインターの場合、数値は返されません。 パラメーターの配列を使用している場合は、設定関数によって SQL_ERROR が返される場合でも、APD の SQL_DESC_ROWS_PROCESSED_PTR フィールドによって示される値が設定されます。 SQL_NEED_DATA が返される場合は、APD の SQL_DESC_ROWS_PROCESSED_PTR フィールドによって示される値は、処理されているパラメーターのセットに設定されます。  
  
 パラメーターの配列がバインドされている場合、何が発生した**更新 WHERE CURRENT OF**ステートメントが実行されるドライバーで定義されます。  
  
## <a name="column-wise-parameter-binding"></a>列方向のパラメーターのバインド  
 列方向のバインドでは、アプリケーションは、パラメーターごとに個別のパラメーターおよび長さ/インジケーターの配列をバインドします。  
  
 列方向のバインドを使用するには、アプリケーションはまず SQL_PARAM_BIND_BY_COLUMN を SQL_ATTR_PARAM_BIND_TYPE ステートメント属性を設定します。 (これは、既定値です)。各列をバインドするには、アプリケーションは、次の手順を実行します。  
  
1.  パラメーターのバッファー配列を割り当てます。  
  
2.  長さ/インジケーター バッファーの配列を割り当てます。  
  
    > [!NOTE]  
    >  アプリケーションは、列方向のバインドを使用する場合に、記述子に直接書き込まれる場合、は、データの長さとインジケーター データの別の配列を使用できます。  
  
3.  呼び出し**SQLBindParameter**次の引数で。  
  
    -   *ValueType*パラメーターのバッファー配列内の単一要素の C 型です。  
  
    -   *ParameterType*パラメーターの SQL 型です。  
  
    -   *ParameterValuePtr*パラメーターのバッファー配列のアドレスです。  
  
    -   *BufferLength*パラメーターのバッファー配列内の単一要素のサイズです。 *BufferLength*データが固定長のデータの場合、引数は無視されます。  
  
    -   *StrLen_or_IndPtr*長さ/インジケーター配列のアドレスです。  
  
 この情報を使用する方法の詳細については、「ParameterValuePtr 引数コメントには"、"このセクション後半を参照してください。 パラメーターの列方向のバインドの詳細については、次を参照してください。[バインド パラメーターの配列](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)です。  
  
## <a name="row-wise-parameter-binding"></a>行方向のパラメーターのバインド  
 行方向のバインドでは、アプリケーションは、バインドするには、各パラメーターのパラメーターおよび長さ/インジケーター バッファーを格納する構造体を定義します。  
  
 行方向のバインドを使用するのには、アプリケーションは、次の手順を実行します。  
  
1.  パラメーター (両方のパラメーターおよび長さ/インジケーター バッファーを含む) の 1 つのセットを保持する構造体を定義し、これらの構造体の配列を割り当てます。  
  
    > [!NOTE]  
    >  アプリケーションは、行方向のバインドを使用する場合に、記述子に直接書き込まれる場合、は、データの長さとインジケーター データの個別のフィールドを使用できます。  
  
2.  パラメーターの 1 つのセットを格納する構造体のサイズまたはパラメーターのバインド先のバッファーのインスタンスのサイズには、SQL_ATTR_PARAM_BIND_TYPE ステートメント属性を設定します。 長さは、バインドされたパラメーターの場合、および構造体またはバッファーにある場合、バインドされたパラメーターのアドレスは、指定した長さでインクリメントは、結果はポイントで同じパラメーターの先頭にいるかどうかを確認するの埋め込み用の領域を含める必要があります、次の行。 使用すると、 *sizeof* ANSI c 演算子は、この動作が保証されます。  
  
3.  呼び出し**SQLBindParameter**をバインドするパラメーターごとに次の引数で。  
  
    -   *ValueType*を列にバインドするパラメーターのバッファーのメンバーの種類です。  
  
    -   *ParameterType*パラメーターの SQL 型です。  
  
    -   *ParameterValuePtr*パラメーター バッファー内のメンバー配列の最初の要素のアドレスです。  
  
    -   *BufferLength*パラメーター バッファーのメンバーのサイズです。  
  
    -   *StrLen_or_IndPtr*バインドされる長さ/インジケーター メンバーのアドレスです。  
  
 この情報を使用する方法の詳細については、次を参照してください。"*ParameterValuePtr*引数、"このセクションで後述します。 パラメーターの行方向のバインドの詳細については、次を参照してください。、[バインド パラメーターの配列](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)です。  
  
## <a name="error-information"></a>エラー情報  
 ドライバーが (SQL_PARAM_ARRAY_ROW_COUNTS オプションは SQL_PARC_NO_BATCH に等しい)、バッチとしてパラメーター配列を実装しない場合、エラー状況は、1 つのステートメントが実行されたかのように処理されます。 ドライバーは、バッチとしてパラメーター配列を実装する場合、アプリケーション、SQL_DESC_ARRAY_STATUS_PTR ヘッダー フィールドを使用できます、IPD の SQL ステートメントまたはパラメーターの配列にパラメーターの原因となったのパラメーターを決定**SQLExecDirect**または**SQLExecute**にエラーが返されます。 このフィールドには、パラメーター値の行ごとの状態に関する情報が含まれています。 フィールドが、エラーが発生したことを示している場合、診断データの構造体のフィールドは失敗した、パラメーターの行とパラメーターの数を示します。 配列内の要素の数は、SQL_ATTR_PARAMSET_SIZE ステートメント属性によって設定できる、APD の SQL_DESC_ARRAY_SIZE ヘッダー フィールドによって定義されます。  
  
> [!NOTE]  
>  APD の SQL_DESC_ARRAY_STATUS_PTR ヘッダー フィールドはパラメーターを無視するために使用します。 詳細については、パラメーターは無視、「パラメーターのセットは無視されます。」次のセクションを参照してください。  
  
 ときに**SQLExecute**または**SQLExecDirect** SQL_PARAM_ERROR、SQL_PARAM_SUCCESS、sql _ を SQL_ERROR を返します、IPD で SQL_DESC_ARRAY_STATUS_PTR フィールドによって示される配列内の要素が含まれますPARAM_SUCCESS_WITH_INFO、SQL_PARAM_UNUSED、または SQL_PARAM_DIAG_UNAVAILABLE します。  
  
 この配列内の各要素には、診断データの構造体には、1 つまたは複数の状態レコードが含まれています。 構造体の SQL_DIAG_ROW_NUMBER フィールドでは、エラーが発生したパラメーター値の行の数を示します。 エラーの原因となったパラメーターの行に、特定のパラメーターを判断することである場合、パラメーター数は SQL_DIAG_COLUMN_NUMBER フィールドに入力されます。  
  
 強制を以前のパラメーターでエラーが発生したため、パラメーターが使用されていないと、SQL_PARAM_UNUSED は入力**SQLExecute**または**SQLExecDirect**を中止します。 たとえば、50 のパラメーターがある場合、エラーが発生しました、fortieth の原因となったパラメーターのセットの実行中に**SQLExecute**または**SQLExecDirect**中止するには SQL_PARAM_UNUSED を入力し、パラメーターを 50 41 の状態の配列。  
  
 この個別のパラメーターのレベルのエラー情報を生成しないため、ドライバーがモノリシックの単位としてパラメーターの配列を扱いますと SQL_PARAM_DIAG_UNAVAILABLE が入力されます。  
  
 パラメーターの 1 つのセットの処理のエラーの一部では、停止する配列で、後続のパラメーターのセットの処理が発生します。 その他のエラーは、後続のパラメーターの処理には影響しません。 ドライバーの定義は、どのエラーの処理が停止します。 処理は停止されません、配列内のすべてのパラメーターが処理される、SQL_SUCCESS_WITH_INFO が、エラーの結果として返されるおよび SQL_ATTR_PARAMS_PROCESSED_PTR によって定義されたバッファーが処理されたパラメーターのセットの合計数に設定されている場合 (で定義されている、SQL_ATTR_PARAMSET_SIZE ステートメント属性)、エラー セットが含まれます。  
  
> [!CAUTION]  
>  パラメーターの配列の処理中にエラーが発生したときに、ODBC の動作は、ODBC 3 異なります。*x* ODBC 2 の場合よりも*。x*です。 ODBC 2 です。*x*SQL_ERROR と処理が中断されること、関数が返されます。 バッファーを指す、 *pirow*の引数**SQLParamOptions**エラー行の数が含まれています。 ODBC 3 です。*x*SQL_SUCCESS_WITH_INFO を返します、および停止するか続行するか月を処理します。 問題が解決しない場合は、SQL_ATTR_PARAMS_PROCESSED_PTR で指定したバッファーがでエラーが発生するものも含めすべてのパラメーター、処理の値に設定されます。 この動作の変更の既存のアプリケーションの問題が発生する可能性があります。  
  
 ときに**SQLExecute**または**SQLExecDirect** SQL_ERROR または SQL_NEED_DATA が返されると、状態配列を含むように、パラメーター配列内のすべてのパラメーター セットの処理を完了する前に返します。既に処理されているこれらのパラメーターの状態。 IPD で SQL_DESC_ROWS_PROCESSED_PTR フィールドが指す位置には、SQL_ERROR または SQL_NEED_DATA エラー コードの原因となったパラメーター配列内の行番号が含まれています。 SELECT ステートメントにパラメーターの配列を送信すると、配列の値の状態の可用性はドライバーで定義されます。セットのフェッチの結果として、ステートメントが実行される、または後に、使用可能な必要があります。  
  
## <a name="ignoring-a-set-of-parameters"></a>一連のパラメーターは無視されます。  
 (また、SQL_ATTR_PARAM_STATUS_PTR ステートメント属性で設定) として APD の SQL_DESC_ARRAY_STATUS_PTR フィールドは、SQL ステートメントにバインドされたパラメーターのセットを無視することを示すために使用できます。 実行中にパラメーターの 1 つ以上のセットを無視するドライバーを指示するには、アプリケーションは以下の手順を実行する必要があります。  
  
1.  呼び出す**SQLSetDescField**ステータス情報が含まれる SQLUSMALLINT 値の配列を指す APD の SQL_DESC_ARRAY_STATUS_PTR ヘッダー フィールドを設定します。 このフィールドは、呼び出すことによって設定することも**SQLSetStmtAttr**で、*属性*SQL_ATTR_PARAM_OPERATION_PTR で、アプリケーションは、記述子ハンドルの取得にフィールドを設定するのです。  
  
2.  2 つの値のいずれかに APD の SQL_DESC_ARRAY_STATUS_PTR フィールドによって定義された配列の各要素を設定します。  
  
    -   SQL_PARAM_IGNORE、行はステートメントの実行から除外されていることを示すためにします。  
  
    -   SQL_PARAM_PROCEED、ステートメントの実行で、行が含まれていることを示すためにします。  
  
3.  呼び出す**SQLExecDirect**または**SQLExecute**準備されたステートメントを実行します。  
  
 APD の SQL_DESC_ARRAY_STATUS_PTR フィールドによって定義された配列に、次の規則が適用されます。  
  
-   ポインターが設定されている既定によって null にします。  
  
-   ポインターが null で、パラメーターのセットはすべて使用、SQL_ROW_PROCEED にすべての要素が設定された場合とされます。  
  
-   SQL_PARAM_PROCEED に要素を設定しても、操作がその特定のパラメーターのセットを使用するとは限りません。  
  
-   SQL_PARAM_PROCEED は、ヘッダー ファイルでは 0 として定義されます。  
  
 アプリケーションは、IRD の SQL_DESC_ARRAY_STATUS_PTR フィールドのフィールドと同じ配列を指す APD の指す SQL_DESC_ARRAY_STATUS_PTR を設定できます。 これは、機能は、パラメーターを行のデータにバインドする場合に便利です。 パラメーターは、行データの状態に応じて、無視されます。 次のコードが無視するように SQL ステートメント内のパラメーターが SQL_PARAM_IGNORE、に加えて: SQL_ROW_DELETED、SQL_ROW_ERROR、SQL_ROW_UPDATED、します。 SQL_PARAM_PROCEED、に加えて、次のコードが発生する、SQL ステートメントに進みます: SQL_ROW_SUCCESS、SQL_ROW_SUCCESS_WITH_INFO、および SQL_ROW_ADDED です。  
  
## <a name="rebinding-parameters"></a>パラメーターを再バインド  
 アプリケーションは、バインディングを変更する 2 つの操作のいずれかを実行できます。  
  
-   呼び出す**SQLBindParameter**は既にバインドされている列の新しいバインディングを指定します。 ドライバーでは、新しい古いバインドが上書きされます。  
  
-   バインディングの呼び出しによって指定されたバッファーのアドレスに追加するオフセットを指定する**SQLBindParameter**です。 詳細については、次のセクションを参照してください「の再バインドをオフセットします」。  
  
## <a name="rebinding-with-offsets"></a>オフセットで再バインド  
 パラメーターの再バインドは、アプリケーションがあるバッファー領域のセットアップへの呼び出しが、多くのパラメーターを含めることができる場合に特に便利です**SQLExecDirect**または**SQLExecute**パラメーターの一部のみを使用します。 バッファー領域の残りの領域は、オフセットによって既存のバインドを変更することで、次のパラメーターのセットを使用できます。  
  
 APD の SQL_DESC_BIND_OFFSET_PTR ヘッダー フィールドは、バインディングのオフセットを指します。 フィールドが null 以外の場合は、ドライバー、ポインターを逆参照し、null ポインターでは、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR フィールドの値の場合は、記述子にそれらのフィールドに逆参照の値を追加実行時に記録します。 新しいポインター値は、SQL ステートメントが実行されるときに使用されます。 オフセットは、再バインド後に有効です。 SQL_DESC_BIND_OFFSET_PTR がそれ自体のオフセットではなくオフセットへのポインターであるため、アプリケーションのオフセットを直接ことがなく変更できますを呼び出す[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)または[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)に記述子フィールドを変更します。 ポインターが設定されている既定によって null にします。 呼び出しによって、ARD の SQL_DESC_BIND_OFFSET_PTR フィールドを設定することができます[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)またはへの呼び出しによって[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)で、*された*SQL_ATTR_PARAM_BIND_ のOFFSET_PTR です。  
  
 バインディングのオフセットは常に、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR フィールドの値に直接追加します。 別の値にオフセットを変更すると、新しい値は各記述子フィールドの値に直接追加されます。 フィールドの値と、以前のオフセットの合計には、新しいオフセットは追加されません。  
  
## <a name="descriptors"></a>記述子  
 パラメーターをバインドする方法については、Ipd、Apd のフィールドによって決まります。 引数は、 **SQLBindParameter**を使用する記述子フィールドを設定します。 、フィールドを設定することも、 **SQLSetDescField**関数が**SQLBindParameter** を呼び出す記述子ハンドルを取得するアプリケーションがないために、使用する方が効率的です**SQLBindParameter**です。  
  
> [!CAUTION]  
>  呼び出す**SQLBindParameter**の 1 つのステートメントが他のステートメントを与えることができます。 これは、ステートメントに関連付けられている ARD が明示的に割り当てられているし、その他のステートメントに関連付けられてもときに発生します。 **SQLBindParameter**フィールドを変更、APD の変更はこの記述子が関連付けられているすべてのステートメントに適用します。 呼び出す前に場合は、必要な動作でない場合は、アプリケーションが、他のステートメントからこの記述子の関連付けを解除する必要があります**SQLBindParameter**です。  
  
 概念的には、 **SQLBindParameter**シーケンスでは、次の手順を実行します。  
  
1.  呼び出し[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) APD ハンドルを取得します。  
  
2.  呼び出し[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) APD の SQL_DESC_COUNT のフィールドを取得する場合の値、 *ColumnNumber*引数が SQL_DESC_COUNT、呼び出しの値を超える**SQLSetDescField**に SQL_DESC_COUNT の値を大きく*ColumnNumber*です。  
  
3.  呼び出し[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) APD の次のフィールドに値を割り当てるを複数回します。  
  
    -   SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE の値に設定*ValueType*する点を除いて、場合*ValueType*は 1 つ、datetime または間隔サブタイプの簡潔な識別子の SQL_DESC_TYPE に設定 sql _DATETIME フィールド型または SQL_INTERVAL は、それぞれ、簡潔な識別子に SQL_DESC_CONCISE_TYPE を設定し、対応する日付時刻または間隔サブコードに SQL_DESC_DATETIME_INTERVAL_CODE を設定します。  
  
    -   SQL_DESC_OCTET_LENGTH フィールドの値に設定*BufferLength*です。  
  
    -   SQL_DESC_DATA_PTR フィールドの値に設定*ParameterValue*です。  
  
    -   SQL_DESC_OCTET_LENGTH_PTR フィールドの値に設定*StrLen_or_Ind*です。  
  
    -   値を SQL_DESC_INDICATOR_PTR フィールドにも設定*StrLen_or_Ind*です。  
  
     *StrLen_or_Ind*パラメーターは、インジケーターの情報とパラメーター値の長さの両方を指定します。  
  
4.  呼び出し[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) IPD ハンドルを取得します。  
  
5.  呼び出し[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) IPD の SQL_DESC_COUNT のフィールドを取得する場合の値、 *ColumnNumber*引数が SQL_DESC_COUNT、呼び出しの値を超える**SQLSetDescField**に SQL_DESC_COUNT の値を大きく*ColumnNumber*です。  
  
6.  呼び出し[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) IPD の次のフィールドに値を割り当てるを複数回します。  
  
    -   SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE の値に設定*ParameterType*する点を除いて、場合*ParameterType*がいずれかの SQL_DESC_TYPE、datetime または間隔サブタイプの簡潔な識別子の設定SQL_DATETIME または SQL_INTERVAL は、それぞれ、簡潔な識別子は、およびデータセット SQL_DESC_DATETIME_INTERVAL_CODE に対応する日付時刻や間隔サブコードに SQL_DESC_CONCISE_TYPE を設定します。  
  
    -   必要に応じて 1 つ以上の SQL_DESC_LENGTH、SQL_DESC_PRECISION、および SQL_DESC_DATETIME_INTERVAL_PRECISION を設定*ParameterType*です。  
  
    -   SQL_DESC_SCALE の値に設定*DecimalDigits*です。  
  
 場合に呼び出し**SQLBindParameter**失敗は、APD の設定が記述子フィールドの内容が定義し、APD の SQL_DESC_COUNT フィールドは変更されません。 さらに、IPD で適切なレコードの SQL_DESC_LENGTH、SQL_DESC_PRECISION、SQL_DESC_SCALE、および SQL_DESC_TYPE フィールドが定義されていると、IPD の SQL_DESC_COUNT フィールドは変更されません。  
  
## <a name="conversion-of-calls-to-and-from-sqlsetparam"></a>呼び出し SQLSetParam との間の変換  
 ODBC 1.0 アプリケーションを呼び出すと**SQLSetParam** ODBC 3 *。x*ドライバー、ODBC 3 *。x*ドライバー マネージャーは、次の表に示すように呼び出しをマップします。  
  
|ODBC 1.0 アプリケーションを呼び出す|ODBC 3 の呼び出しです。*x*ドライバー|  
|----------------------------------|-------------------------------|  
|SQLSetParam (StatementHandle ParameterNumber、ValueType、ParameterType、LengthPrecision、ParameterScale、ParameterValuePtr StrLen_or_IndPtr) です。|SQLBindParameter (StatementHandle、ParameterNumber、SQL_PARAM_INPUT_OUTPUT、ValueType、ParameterType、 *ColumnSize*、 *DecimalDigits*ParameterValuePtr、SQL_SETPARAM_VALUE_MAX、     StrLen_or_IndPtr) です。|  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションは、ORDERS テーブルにデータを挿入する SQL ステートメントを準備します。 アプリケーションを呼び出し、ステートメントの各パラメーター **SQLBindParameter** ODBC C データ型とパラメーターの SQL データ型を指定し、各パラメーターにバッファーをバインドします。 データの行ごとに、アプリケーションがパラメーターとその呼び出しにデータ値を割り当てます**SQLExecute**ステートメントを実行します。  
  
 次の例では、Northwind データベースに関連付けられている Northwind という名前のコンピューターでの ODBC データ ソースがあることを前提としています。  
  
 コード例については、次を参照してください[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、 [SQLProcedures 関数](../../../odbc/reference/syntax/sqlprocedures-function.md)、 [SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)、および[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```  
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
 次の例では、アプリケーションは、名前付きパラメーターを使用して、SQL Server のストアド プロシージャを実行します。  
  
```  
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
  
|詳細|参照先|  
|---------------------------|---------|  
|ステートメント内のパラメーターに関する情報を返す|[SQLDescribeParam 関数](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|ステートメントでパラメーターのバッファーを解放します。|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|ステートメントのパラメーターの数を返す|[SQLNumParams 関数](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|データを送信する次のパラメーターを返す|[SQLParamData 関数](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|複数のパラメーター値を指定します。|[SQLParamOptions 関数](../../../odbc/reference/syntax/sqlparamoptions-function.md)|  
|実行時にパラメーターのデータを送信します。|[SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
