---
title: SQLSetDescField 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLSetDescField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescField
helpviewer_keywords:
- SQLSetDescField function [ODBC]
ms.assetid: 8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c09d341cc5f6f592d84dab06a5a6785e9514f78
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetdescfield-function"></a>SQLSetDescField 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **Sqlsetdescfield による**記述子レコードの 1 つのフィールドの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLSetDescField(  
     SQLHDESC      DescriptorHandle,  
     SQLSMALLINT   RecNumber,  
     SQLSMALLINT   FieldIdentifier,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    BufferLength);  
```  
  
## <a name="arguments"></a>引数  
 *DescriptorHandle*  
 [入力]記述子ハンドルです。  
  
 *RecNumber*  
 [入力]フィールドを設定しようとしているアプリケーションを含む記述子レコードを示します。 記述子レコードは、レコード番号 0 のブックマーク レコードの中で、0 から番号が付けられます。 *RecNumber*ヘッダー フィールドの引数は無視されます。  
  
 *FieldIdentifier*  
 [入力]値を設定する記述子フィールドを示します。 詳細については、次を参照してください。"*FieldIdentifier*引数"、"コメント"セクションでします。  
  
 *ValuePtr*  
 [入力]記述子の情報、または整数値を格納するバッファーへのポインター。 データ型は、の値によって異なります。 *FieldIdentifier*です。 場合*ValuePtr*整数値です (SQLLEN) は 8 バイト、4 バイト (SQLINTEGER) または 2 バイト (SQLSMALLINT) の値に応じてと見なすことが、 *FieldIdentifier*引数。  
  
 *BufferLength*  
 [入力]場合*FieldIdentifier* ODBC で定義されたフィールドと*ValuePtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります **ValuePtr*です。 文字の文字列データでは、この引数は、文字列のバイト数を含める必要があります。  
  
 場合*FieldIdentifier* ODBC で定義されたフィールドと*ValuePtr*整数*BufferLength*は無視されます。  
  
 場合*FieldIdentifier*ドライバーの定義済みのフィールドでは、アプリケーション、ドライバー マネージャーに、フィールドの性質を示す設定、 *BufferLength*引数。 *BufferLength*次の値を持つことができます。  
  
-   場合*ValuePtr*文字の文字列へのポインターが*BufferLength* SQL_NTS または文字列の長さです。  
  
-   場合*ValuePtr*アプリケーションが、SQL_LEN_BINARY_ATTR の結果を配置し、バイナリのバッファーへのポインターは、(*長さ*) マクロで*BufferLength*です。 これにより、配置に負の値*BufferLength*です。  
  
-   場合*ValuePtr*文字の文字列またはバイナリ文字列以外の値へのポインターが*BufferLength* SQL_IS_POINTER 値でなければなりません。  
  
-   場合*ValuePtr*し、固定長の値を含む*BufferLength*は必要に応じて SQL_IS_INTEGER、SQL_IS_UINTEGER、SQL_IS_SMALLINT、または SQL_IS_USMALLINT のいずれか。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetDescField** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_DESC と*処理*の*DescriptorHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLSetDescField**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプション値が変更されました|ドライバーがで指定された値をサポートしていません *\*ValuePtr* (場合*ValuePtr*ポインター) の値または*ValuePtr* (場合*ValuePtr*された整数値)、または *\*ValuePtr*が正しくない実装の動作条件のため、ドライバーのような値を置換するようにします。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07009|無効な記述子のインデックス|*FieldIdentifier*引数がレコードのフィールド、 *RecNumber*引数が 0 の場合、 *DescriptorHandle* IPD ハンドルへの引数と呼ばれます。<br /><br /> *RecNumber*引数は、0 より小さい、 *DescriptorHandle*引数が、ARD または、APD を参照します。<br /><br /> *RecNumber*引数が列またはデータ ソースをサポートできますが、パラメーターの最大数よりも大きかったと*DescriptorHandle* APD または ARD 引数と呼ばれます。<br /><br /> (DM)、 *FieldIdentifier*引数が SQL_DESC_COUNT、および *\*ValuePtr*引数が 0 未満です。<br /><br /> *RecNumber*引数が 0 に等しいと*DescriptorHandle*引数が暗黙的に割り当てられた APD と呼びます。 (これで、アプリケーションが明示的に割り当てられた記述子でエラーが発生しないアプリケーションが明示的に割り当てられた記述子が APD またはまで ARD かどうかが不明のために実行されます。)|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|22001|文字列データで、右側が切り捨てられました|*FieldIdentifier*引数が SQL_DESC_NAME、および*BufferLength*引数が SQL_MAX_IDENTIFIER_LEN より大きい値です。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、 *DescriptorHandle*が関連付けられて、 *StatementHandle*非同期的に実行中の関数 (いないこの 1 つ) が呼び出されたおよびこの関数が呼び出されたときに実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle*いる、 *DescriptorHandle*が関連付けられているし、SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *DescriptorHandle*です。 この非同期関数がまだ実行したときに、 **SQLSetDescField**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかで呼び出され、 *DescriptorHandle* SQL_PARAM_DATA_AVAILABLE を返されるとします。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY016|実装行記述子は変更できません。|*DescriptorHandle*引数は、IRD を関連付け、 *FieldIdentifier* SQL_DESC_ARRAY_STATUS_PTR または SQL_DESC_ROWS_PROCESSED_PTR 引数がありませんでした。|  
|HY021|不整合な記述子情報|SQL_DESC_TYPE と SQL_DESC_DATETIME_INTERVAL_CODE フィールドが形成されていません、有効な ODBC SQL 型または (Ipd) の有効なドライバー固有の SQL 型または有効な ODBC C 型 (Apd の標準)。<br /><br /> 整合性チェック中にチェック記述子の情報が一致していません。 (「整合性チェック」を参照してください**SQLSetDescRec**)。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM)  *\*ValuePtr*文字の文字列、および*BufferLength*ゼロより小さいは SQL_NTS に等しいでした。<br /><br /> (DM) ドライバーは ODBC 2 *.x*ドライバー、記述子が、ARD、 *ColumnNumber*引数が 0 であり、引数に指定された値に設定された*BufferLength*されました4 に等しくないです。|  
|HY091|無効な記述子フィールド識別子|指定された値、 *FieldIdentifier*引数を選択して、ODBC で定義されたフィールドでしたが、実装定義の値ではありません。<br /><br /> *FieldIdentifier*引数が、無効、 *DescriptorHandle*引数。<br /><br /> *FieldIdentifier*引数が ODBC で定義された、読み取り専用フィールドです。|  
|HY092|無効な属性またはオプション識別子|値 *\*ValuePtr*が、無効、 *FieldIdentifier*引数。<br /><br /> *FieldIdentifier*引数が SQL_DESC_UNNAMED、および*ValuePtr* SQL_NAMED がします。|  
|HY105|無効なパラメーターの型|(DM) SQL_DESC_PARAMETER_TYPE フィールドに指定された値が無効でした。 (詳細については、次を参照してください、"*InputOutputType*引数"」の「 **SQLBindParameter**。)。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [ODBC 3.8 新](../../../odbc/reference/what-s-new-in-odbc-3-8.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *DescriptorHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 アプリケーションが呼び出すことができます**SQLSetDescField**を一度にいずれかの任意の記述子フィールドを設定します。 1 回の呼び出し**SQLSetDescField**記述子を 1 つで 1 つのフィールドを設定します。 この関数は、記述子の型のいずれかのフィールドを設定すると呼ばれる、フィールドを設定することができますを提供できます。 (このセクションの後半の表を参照してください)。  
  
> [!NOTE]  
>  呼び出し**SQLSetDescField**で識別される記述子レコードの内容が失敗した、 *RecNumber*引数が定義されていません。  
  
 関数の 1 回の呼び出しで複数の記述子フィールドを設定する他の関数を呼び出すことができます。 **SQLSetDescRec**関数は、さまざまなフィールドを列またはパラメーター (、SQL_DESC_TYPE SQL_DESC_DATETIME_INTERVAL_CODE、SQL_DESC_OCTET_LENGTH、SQL_DESC_PRECISION sql _ にバインドされたバッファーとデータ型に影響する設定DESC_SCALE、SQL_DESC_DATA_PTR、SQL_DESC_OCTET_LENGTH_PTR、および SQL_DESC_INDICATOR_PTR フィールド) です。 **SQLBindCol**または**SQLBindParameter**列またはパラメーターのバインドの完全な仕様を使用することができます。 これらの関数は、1 つの関数の呼び出しによる記述子フィールドの特定のグループを設定します。  
  
 **Sqlsetdescfield による**バインディング ポインター (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、または SQL_DESC_OCTET_LENGTH_PTR) へのオフセットを追加することで、バインディングのバッファーを変更するのに呼び出せることができます。 これにより、変更を呼び出さずバインディング バッファー **SQLBindCol**または**SQLBindParameter**、SQL_DESC_DATA_ などの他のフィールドを変更することがなく SQL_DESC_DATA_PTR を変更するアプリケーションを許可します。入力します。  
  
 アプリケーションを呼び出す場合**SQLSetDescField** SQL_DESC_COUNT 以外の任意のフィールドまたは SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、SQL_DESC_OCTET_LENGTH_PTR、遅延のフィールドを設定するには、レコードがバインドされていません。  
  
 記述子のヘッダー フィールドを呼び出すことにより設定は**SQLSetDescField**と適切な*FieldIdentifier*です。 多くのヘッダー フィールドも、ステートメント属性への呼び出しで設定することも、 **SQLSetStmtAttr**です。 これにより記述子ハンドルを取得する最初に、記述子フィールドを設定するアプリケーション。 ときに**SQLSetDescField**ヘッダー フィールドを設定するために呼び出される、 *RecNumber*引数は無視されます。  
  
 A *RecNumber* 0 のブックマークのフィールドを設定に使用されます。  
  
> [!NOTE]  
>  ステートメント属性 SQL_ATTR_USE_BOOKMARKS は常に設定する呼び出しの前に**SQLSetDescField**ブックマーク フィールドを設定します。 これは必須ではなく、中に強くお勧めします。  
  
## <a name="sequence-of-setting-descriptor-fields"></a>一連の記述子フィールドの設定  
 呼び出すことにより記述子フィールドを設定するときに**SQLSetDescField**アプリケーションが特定の順序に従う必要があります。  
  
1.  アプリケーションでは、SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE、または SQL_DESC_DATETIME_INTERVAL_CODE フィールドをまず設定する必要があります。  
  
2.  これらのフィールドのいずれかが設定されたら、アプリケーションは、データ型の属性を設定でき、ドライバーはデータ型の適切な既定値をデータ型の属性フィールドを設定します。 型の属性フィールドの既定の自動により記述子が常に、アプリケーションのデータ型が指定した後で使用する準備がされます。 場合は、アプリケーションは、データ型の属性を明示的に設定、既定の属性をオーバーライドしています。  
  
3.  手順 1 で示されているフィールドのいずれかが設定されていると、データ型の属性が設定されている、アプリケーションは、SQL_DESC_DATA_PTR を設定できます。 これには、記述子フィールドの整合性チェックが求められます。 アプリケーションは、SQL_DESC_DATA_PTR フィールドを設定した後、データ型または属性を変更する場合、ドライバーは、null ポインターの場合、レコードをバインド解除する SQL_DESC_DATA_PTR を設定します。 これにより記述子レコードが使用できるようにする前に、順番に、適切な手順を実行するアプリケーションです。  
  
## <a name="initialization-of-descriptor-fields"></a>記述子フィールドの初期化  
 記述子が割り当てられている場合の記述子フィールドは、既定値に初期化することができます、既定値を持たない初期化するか、記述子の種類に対して定義できません。 次の表では、"D"は、既定値、フィールドが初期化されていることを示すと"ND"は、既定値なし、フィールドが初期化されていることを示す、記述子の種類ごとに各フィールドの初期化を示しています。 数値が表示されている場合は、その番号はフィールドの既定値です。 テーブルは、フィールドが (R/W) の読み取り/書き込みまたは読み取り専用 (R) かどうかも示します。  
  
 IRD のフィールドでは、ステートメント ハンドルまたは記述子が割り当てられるときではなく、IRD が設定されてと、ステートメントが準備または実行後にのみ、既定値があります。 IRD の読み込みが完了するまで、IRD のフィールドにアクセスするあらゆる試みがエラーを返します。  
  
 記述子の種類 (標準および IRDs、Apd と Ipd) のすべてではありませんが、1 つ以上の、いくつかの記述子フィールドが定義されます。 フィールドは、記述子の種類に対して定義されているが、ときに、その記述子を使用する関数のいずれかでは必要ありません。  
  
 アクセスできるフィールド**SQLGetDescField**必ずしも設定することはできません**SQLSetDescField**です。 設定できるフィールド**SQLSetDescField**次の表に一覧表示されます。  
  
 ヘッダー フィールドの初期化は、次の表で説明します。  
  
|ヘッダー フィールドの名前|型|R/W|既定値|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_ALLOC_TYPE|SQLSMALLINT|ARD: R APD: R IRD: R IPD: R|ARD: SQL_DESC_ALLOC_AUTO 暗黙または SQL_DESC_ALLOC_USER の明示的な<br /><br /> APD: SQL_DESC_ALLOC_AUTO の暗黙の SQL_DESC_ALLOC_USER または明示的な<br /><br /> IRD: SQL_DESC_ALLOC_AUTO<br /><br /> IPD: SQL_DESC_ALLOC_AUTO|  
|SQL_DESC_ARRAY_SIZE|SQLULEN|ARD: R/W APD: R/W IRD: 未使用の IPD: 使用されていません。|ARD: [1] APD: [1] IRD: 未使用の IPD: 使用されていません。|  
|SQL_DESC_ARRAY_STATUS_PTR|SQLUSMALLINT *|ARD: R/W APD: R/W IRD: IPD の R/W: 読み取り/書き込み|ARD: Null ptr APD: Null ptr IRD: ptr IPD を Null: ptr は Null|  
|SQL_DESC_BIND_OFFSET_PTR|SQLLEN *|ARD: R/W APD: R/W IRD: 未使用の IPD: 使用されていません。|ARD: Null ptr APD: Null ptr IRD: 未使用 IPD: 使用されていません。|  
|SQL_DESC_BIND_TYPE|SQLINTEGER|ARD: R/W APD: R/W IRD: 未使用の IPD: 使用されていません。|ARD: SQL_BIND_BY_COLUMN<br /><br /> APD: SQL_BIND_BY_COLUMN<br /><br /> IRD: 使用されていません。<br /><br /> IPD: 使用されていません。|  
SQL_DESC_COUNT|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: 0 APD: IRD 0: D IPD: 0|  
|SQL_DESC_ROWS_PROCESSED_PTR|SQLULEN *|ARD: 未使用 APD: 未使用 IRD: IPD R/W: 読み取り/書き込み|ARD: 未使用 APD: 未使用 IRD: Null ptr IPD: ptr は Null|  
  
 [1] フィールドは、IPD はドライバーによって自動的に設定する場合にのみ定義されます。 いない場合は、定義はありません。 アプリケーションが、これらのフィールド、SQLSTATE HY091 を設定しようとしています。 場合 (無効な記述子フィールド識別子) が返されます。  
  
 レコードのフィールドの初期化は、次の表に示すようにします。  
  
|レコード フィールド名|型|R/W|既定値|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_BASE_COLUMN_NAME|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_BASE_TABLE_NAME|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_CASE_SENSITIVE|SQLINTEGER|ARD: 未使用 APD: 未使用 IRD: R IPD: R|ARD: 未使用 APD: 未使用 IRD: D IPD: D [1]|  
|SQL_DESC_CATALOG_NAME|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_CONCISE_TYPE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: SQL_C_ 既定 APD: SQL_C_ 既定 IRD: D IPD: ND|  
|SQL_DESC_DATA_PTR|SQLPOINTER|ARD: R/W APD: R/W IRD: 未使用の IPD: 使用されていません。|ARD: Null ptr APD: Null ptr IRD: 未使用の IPD: 未使用 [2]|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQLINTEGER|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: ND APD: ND IRD: D IPD: ND|  
SQL_DESC_DISPLAY_SIZE|SQLLEN|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_FIXED_PREC_SCALE|SQLSMALLINT|ARD: 未使用 APD: 未使用 IRD: R IPD: R|ARD: 未使用 APD: 未使用 IRD: D IPD: D [1]|  
|SQL_DESC_INDICATOR_PTR|SQLLEN *|ARD: R/W APD: R/W IRD: 未使用の IPD: 使用されていません。|ARD: Null ptr APD: Null ptr IRD: 未使用 IPD: 使用されていません。|  
|SQL_DESC_LABEL|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_LENGTH|SQLULEN|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_LITERAL_PREFIX|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_LITERAL_SUFFIX|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_LOCAL_TYPE_NAME|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: R|ARD: 未使用 APD: 未使用 IRD: D IPD: D [1]|  
|SQL_DESC_NAME|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: 読み取り/書き込み|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_NULLABLE|SQLSMALLINT|ARD: 未使用 APD: 未使用 IRD: R IPD: R|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_NUM_PREC_RADIX|SQLINTEGER|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: ND APD: ND IRD: D IPD: ND|  
SQL_DESC_OCTET_LENGTH|SQLLEN|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH_PTR|SQLLEN *|ARD: R/W APD: R/W IRD: 未使用の IPD: 使用されていません。|ARD: Null ptr APD: Null ptr IRD: 未使用 IPD: 使用されていません。|  
|SQL_DESC_PARAMETER_TYPE|SQLSMALLINT|ARD: 未使用 APD: 未使用 IRD: 未使用の IPD: 読み取り/書き込み|ARD: 未使用 APD: 未使用 IRD: 未使用の IPD: D SQL_PARAM_INPUT を =|  
|SQL_DESC_PRECISION|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_ROWVER|SQLSMALLINT|ARD: 使用されていません。<br /><br /> APD: 使用されていません。<br /><br /> IRD: R<br /><br /> IPD: R|ARD: 使用されていません。<br /><br /> APD: 使用されていません。<br /><br /> IRD: ND<br /><br /> IPD: ND|  
|SQL_DESC_SCALE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_SCHEMA_NAME|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_SEARCHABLE|SQLSMALLINT|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_TABLE_NAME|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
|SQL_DESC_TYPE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: 読み取り/書き込み|ARD: SQL_C_DEFAULT APD: SQL_C_DEFAULT IRD: D IPD: ND|  
SQL_DESC_TYPE_NAME|SQLCHAR *|ARD: 未使用 APD: 未使用 IRD: R IPD: R|ARD: 未使用 APD: 未使用 IRD: D IPD: D [1]|  
|SQL_DESC_UNNAMED|SQLSMALLINT|ARD: 未使用 APD: 未使用 IRD: R IPD: 読み取り/書き込み|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_UNSIGNED|SQLSMALLINT|ARD: 未使用 APD: 未使用 IRD: R IPD: R|ARD: 未使用 APD: 未使用 IRD: D IPD: D [1]|  
|SQL_DESC_UPDATABLE|SQLSMALLINT|ARD: 未使用 APD: 未使用 IRD: R IPD: 使用されていません。|ARD: 未使用 APD: 未使用 IRD: D IPD: 使用されていません。|  
  
 [1] フィールドは、IPD はドライバーによって自動的に設定する場合にのみ定義されます。 いない場合は、定義はありません。 アプリケーションが、これらのフィールド、SQLSTATE HY091 を設定しようとしています。 場合 (無効な記述子フィールド識別子) が返されます。  
  
 [2] で、SQL_DESC_DATA_PTR フィールド、IPD では、整合性チェックを強制的に設定できます。 後続の呼び出しで**SQLGetDescField**または**SQLGetDescRec**ドライバーは、SQL_DESC_DATA_PTR に設定された値を返す必要はありません。  
  
## <a name="fieldidentifier-argument"></a>FieldIdentifier 引数  
 *FieldIdentifier*記述子フィールドを設定するかを指定します。 記述子が含まれています、*記述子のヘッダー、*次のセクションで、「ヘッダー フィールド」と 0 個以上で説明するヘッダー フィールドから成る*記述子レコード*レコード フィールドから成る「ヘッダー フィールド」セクションの次のセクションで説明します。  
  
## <a name="header-fields"></a>ヘッダー フィールド  
 各記述子には、次のフィールドから成るヘッダーがあります。  
  
 **[すべて] SQL_DESC_ALLOC_TYPE**  
 この読み取り専用 SQLSMALLINT ヘッダー フィールドでは、ドライバーによって、またはアプリケーションによって明示的に記述子の割り当てられた自動的に設定するかどうかを指定します。 このアプリケーションは、取得しますが、このフィールドは変更されません。 フィールドは、記述子が、ドライバーによって自動的に割り当てられた場合、ドライバーによって SQL_DESC_ALLOC_AUTO に設定されます。 記述子は、アプリケーションによって明示的に割り当てられた場合、ドライバーによって SQL_DESC_ALLOC_USER に設定にされます。  
  
 **SQL_DESC_ARRAY_SIZE [アプリケーションの記述子]**  
 標準では、この SQLULEN ヘッダー フィールドは、行セット内の行の数を指定します。 呼び出しによって返される行の数は、この**SQLFetch**または**SQLFetchScroll**またはへの呼び出しで処理される**SQLBulkOperations**または**SQLSetPos**.  
  
 Apd では、この SQLULEN ヘッダー フィールドは、各パラメーターの値の数を指定します。  
  
 このフィールドの既定値は 1 です。 SQL_DESC_ARRAY_SIZE が 1 より大きい場合は、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および ARD または APD の SQL_DESC_OCTET_LENGTH_PTR 配列をポイントします。 各配列の基数は、このフィールドの値と同じです。  
  
 呼び出して、ARD でこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_ROW_ARRAY_SIZE 属性を持つ。 呼び出して、APD のこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_PARAMSET_SIZE 属性を持つ。  
  
 **[すべて] SQL_DESC_ARRAY_STATUS_PTR**  
 記述子の種類ごと、この SQLUSMALLINT * SQLUSMALLINT 値の配列へのヘッダー フィールドのポインター。 これらのアレイが次のように名前付き: 行状態配列 (IRD)、パラメーター状態配列 (IPD)、行操作配列 (ARD)、およびパラメーター操作配列 (APD)。  
  
 このヘッダー フィールドが呼び出しの後に状態の値を含む行の状態配列を指す、IRD の**SQLBulkOperations**、 **SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**です。 配列には、行セットの行数が多くの要素があります。 アプリケーションは、SQLUSMALLINTs の配列を割り当て、このフィールドの配列を指すように設定する必要があります。 既定では、フィールドは null ポインターを設定します。 ドライバーは、配列への追加-SQL_DESC_ARRAY_STATUS_PTR フィールドが null ポインターの場合に設定されている場合のステータス値は生成されず、配列値を返さない限り、します。  
  
> [!CAUTION]  
>  アプリケーションは、IRD の SQL_DESC_ARRAY_STATUS_PTR フィールドによって示される行の状態配列の要素を設定する場合、ドライバーの動作は定義されません。  
  
 呼び出しによって、配列の初期値は**SQLBulkOperations**、 **SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**です。 呼び出しは SQL_SUCCESS または sql_success_with_info が返されませんでした、このフィールドによって示される配列の内容は未定義です。 配列内の要素には、次の値を含めることができます。  
  
-   SQL_ROW_SUCCESS: この行はフェッチに成功しましたれが最後にフェッチから変更されていません。  
  
-   SQL_ROW_SUCCESS_WITH_INFO: この行はフェッチに成功しましたれが最後にフェッチから変更されていません。 ただし、行に関する警告が返されました。  
  
-   SQL_ROW_ERROR: 行をフェッチ中にエラーが発生しました。  
  
-   SQL_ROW_UPDATED: この行はフェッチに成功しましたれ、最後にフェッチした後が更新されました。 行を再度フェッチは、その状態は SQL_ROW_SUCCESS がします。  
  
-   SQL_ROW_DELETED: 行が削除された前回のフェッチ後です。  
  
-   SQL_ROW_ADDED: によって行が挿入された**SQLBulkOperations**です。 行を再度フェッチは、その状態は SQL_ROW_SUCCESS がします。  
  
-   SQL_ROW_NOROW: 行セットは、結果セットの末尾をオーバー ラップされ、行の状態配列のこの要素に対応する行が返されません。  
  
 呼び出して、IRD でこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_ROW_STATUS_PTR 属性を持つ。  
  
 IRD の SQL_DESC_ARRAY_STATUS_PTR フィールドは SQL_SUCCESS または SQL_SUCCESS_WITH_INFO が返された後にのみ有効です。 場合は、リターン コードは、次のいずれかではない、SQL_DESC_ROWS_PROCESSED_PTR によって示される場所は定義されません。  
  
 このヘッダー フィールドが呼び出しの後にパラメーター値のセットごとに状態情報を含むパラメーター状態配列を指す、IPD で**SQLExecute**または**SQLExecDirect**です。 場合に呼び出し**SQLExecute**または**SQLExecDirect** SQL_SUCCESS または sql_success_with_info が、このフィールドによって示される配列の内容が定義されていないが返されませんでした。 アプリケーションは、SQLUSMALLINTs の配列を割り当て、このフィールドの配列を指すように設定する必要があります。 ドライバーは、配列への追加-SQL_DESC_ARRAY_STATUS_PTR フィールドが null ポインターの場合に設定されている場合のステータス値は生成されず、配列値を返さない限り、します。 配列内の要素には、次の値を含めることができます。  
  
-   SQL_PARAM_SUCCESS: SQL ステートメントが正常にこのパラメーターのセットの実行。  
  
-   SQL_PARAM_SUCCESS_WITH_INFO: このパラメーターのセットに対して SQL ステートメントが実行されましたが正常にただし、警告情報は、診断データの構造体で使用できます。  
  
-   SQL_PARAM_ERROR: このパラメーターのセットの処理中にエラーが発生しました。 追加のエラーについては、診断データの構造体です。  
  
-   SQL_PARAM_UNUSED: このパラメーターが設定された、使用可能性のあるためにいくつか前のパラメーター セットには、以降の処理を中止エラーが発生しました。 または、SQL_DESC_ARRAY_ で指定された配列内のパラメーターのセット SQL_PARAM_IGNORE が設定されているためAPD の STATUS_PTR フィールドです。  
  
-   SQL_PARAM_DIAG_UNAVAILABLE: 診断情報は使用できません。 この例であり、ドライバーでは、パラメーターの配列を扱いますモノリシックな単位としてときため、このレベルのエラー情報を生成しません。  
  
 呼び出して、IPD でこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_PARAM_STATUS_PTR 属性を持つ。  
  
 このヘッダー フィールドがこの行が無視するかどうかを示すために、アプリケーションによって設定できる値の行操作配列を指す、ARD で**SQLSetPos**操作します。 配列内の要素には、次の値を含めることができます。  
  
-   SQL_ROW_PROCEED: 使用して一括操作で行が含まれている**SQLSetPos**です。 (この設定は保証されませんいる操作が行に対して行われます。 行は、SQL_ROW_ERROR IRD 行の状態配列での状態が、ドライバーできないことがあります行の操作を実行します。)  
  
-   SQL_ROW_IGNORE: 行は、一括操作を使用して、除外されて**SQLSetPos**です。  
  
 配列の要素が設定されていない場合は、一括操作ですべての行が含まれます。 一括操作ですべての行が含まれる、ARD の SQL_DESC_ARRAY_STATUS_PTR フィールドの値が null ポインターの場合は、解釈は、有効な配列を指すポインター、配列のすべての要素が SQL_ROW_PROCEED 場合と同じです。 配列内の要素は、SQL_ROW_IGNORE に設定されている場合、無視された行の行の状態配列内の値は変更されません。  
  
 呼び出して、ARD でこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_ROW_OPERATION_PTR 属性を持つ。  
  
 このヘッダー フィールドがこのパラメーターのセットがあるかどうかを示すために、アプリケーションによって設定できる値のパラメーターの操作配列を指す、APD のするときに無視**SQLExecute**または**SQLExecDirect**と呼びます。 配列内の要素には、次の値を含めることができます。  
  
-   SQL_PARAM_PROCEED: パラメーターのセットに含まれる、 **SQLExecute**または**SQLExecDirect**呼び出します。  
  
-   SQL_PARAM_IGNORE: パラメーターのセットは除外されてから、 **SQLExecute**または**SQLExecDirect**呼び出します。  
  
 すべての配列内のパラメーターのセットが使用される配列の要素が設定されていない場合、 **SQLExecute**または**SQLExecDirect**呼び出しです。 APD の SQL_DESC_ARRAY_STATUS_PTR フィールドの値が null ポインターの場合は、すべてのパラメーターのセットが使用されます。解釈は、有効な配列を指すポインター、配列のすべての要素が SQL_PARAM_PROCEED 場合と同じです。  
  
 呼び出して、APD のこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_PARAM_OPERATION_PTR 属性を持つ。  
  
 **SQL_DESC_BIND_OFFSET_PTR [アプリケーションの記述子]**  
 この SQLLEN * ヘッダー フィールドがポイントするバインディングのオフセット。 既定では null ポインターに設定されます。 このフィールドが null ポインターでない場合は、ドライバーはポインターを逆参照し、各を記述子レコード (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR) に null 以外の値を持つ遅延フィールドに逆参照値を追加フェッチ時間と、新しいポインター値を使用してバインドするときにします。  
  
 バインディングのオフセットは常に、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR フィールドの値に直接追加します。 別の値にオフセットを変更すると、新しい値は各記述子フィールドの値に直接追加されます。 フィールドの値と、以前のオフセットには、新しいオフセットは追加されません。  
  
 このフィールドは、*遅延フィールド*: 時に設定されているが、使用は後で、ドライバーによってデータ バッファーのアドレスを判別する必要があるときに使用されることはありません。  
  
 呼び出して、ARD でこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_ROW_BIND_OFFSET_PTR 属性を持つ。 呼び出して、ARD でこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_PARAM_BIND_OFFSET_PTR 属性を持つ。  
  
 詳細については、行方向のバインドでの説明を参照してください。 [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)と[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)です。  
  
 **SQL_DESC_BIND_TYPE [アプリケーションの記述子]**  
 この SQLUINTEGER ヘッダー フィールドは、列またはパラメーターをバインドするために使用するバインディングの向きを設定します。  
  
 標準では、このフィールドは、バインディング向きを指定します。 ときに**SQLFetchScroll**または**SQLFetch** 、関連付けられているステートメント ハンドルで呼び出されるとします。  
  
 列の列方向のバインドを選択するには、このフィールドは SQL_BIND_BY_COLUMN (既定) に設定します。  
  
 呼び出して、ARD でこのフィールドを設定することも**SQLSetStmtAttr** 、SQL_ATTR_ROW_BIND_TYPE に*属性*です。  
  
 Apd には、このフィールドは、動的パラメーターを使用するバインディングの向きを指定します。  
  
 パラメーターの列方向のバインドを選択するには、このフィールドは SQL_BIND_BY_COLUMN (既定) に設定されます。  
  
 呼び出して、APD のこのフィールドを設定することも**SQLSetStmtAttr** 、SQL_ATTR_PARAM_BIND_TYPE を*属性*です。  
  
 **[すべて] SQL_DESC_COUNT**  
 この SQLSMALLINT ヘッダー フィールドでは、データが含まれる番号が最大レコードの 1 から始まるインデックスを指定します。 設定すると、ドライバー、記述子のデータ構造、それも、SQL_DESC_COUNT 表示するフィールドをレコードの数が大幅を設定する必要があります。 アプリケーションでは、このデータ構造体のインスタンスを割り当てます、ときの部屋を予約するレコードの数を指定することはありません。 アプリケーションでは、レコードの内容を指定するよう、ドライバーは、必要なアクション記述子ハンドルが適切なサイズのデータ構造体を指すことを確認するれます。  
  
 SQL_DESC_COUNT はすべてのデータ列 (フィールドが、ARD である場合) にバインドされているか (フィールドが、APD の場合) にバインドされる、すべてのパラメーターの数ではありませんが番号が最大レコード数です。 番号が最大の列またはパラメーターがバインドされている場合、SQL_DESC_COUNT は、次の番号が最大の列またはパラメーターの数に変更されます。 かどうか、列またはパラメーターを数値にするがよりも少ない番号が最大列数がバインドではありません (を呼び出して**SQLBindCol**で、 *TargetValuePtr*引数に null ポインター、または設定**SQLBindParameter**で、 *ParameterValuePtr*引数が null ポインターに設定)、SQL_DESC_COUNT は変更されません。 追加の列またはパラメーターがデータを格納する番号が最大レコードよりも大きい番号にバインドされている場合、ドライバーは SQL_DESC_COUNT フィールドの値を自動的に増加します。 呼び出してすべての列がバインドされていない場合**SQLFreeStmt** SQL_UNBIND オプションを使用して ARD および IRD SQL_DESC_COUNT フィールドが 0 に設定します。 場合**SQLFreeStmt**が呼び出された SQL_RESET_PARAMS オプションを使用して、APD と IPD に SQL_DESC_COUNT フィールドが 0 に設定します。  
  
 SQL_DESC_COUNT の値できる明示的に設定するアプリケーションで呼び出すことによって**SQLSetDescField**です。 SQL_DESC_COUNT の値が明示的に低下している SQL_DESC_COUNT に新しい値よりも大きい番号を持つすべてのレコード効果的に削除されます。 SQL_DESC_COUNT の値は 0 を明示的に設定すると、フィールドが、ARD 中、バインドされたブックマーク列を除くすべてのデータ バッファーが解放されます。  
  
 ARD のこのフィールドにレコード カウントには、バインドされたブックマーク列は含まれません。 ブックマーク列をバインド解除する唯一の方法では、SQL_DESC_DATA_PTR フィールドに null ポインターを設定します。  
  
 **SQL_DESC_ROWS_PROCESSED_PTR [実装記述子]**  
 この SQLULEN、IRD の\*ヘッダー フィールドがポイントする呼び出しの後にフェッチされた行の数を格納するバッファー **SQLFetch**または**SQLFetchScroll**、または、一括操作で影響を受ける行の数呼び出しによって実行される**SQLBulkOperations**または**SQLSetPos**エラー行も含まれます。  
  
 IPD では、この SQLUINTEGER * ヘッダー フィールドがポイントする処理された、エラーのセットを含むパラメーターのセットの数を格納するバッファー。 これが null ポインターの場合、数値は返されません。  
  
 SQL_DESC_ROWS_PROCESSED_PTR が有効では呼び出しの後に関係なく SQL_SUCCESS または SQL_SUCCESS_WITH_INFO が返された後にのみ**SQLFetch**または**SQLFetchScroll** (用、IRD フィールド) または**SQLExecute**、 **SQLExecDirect**、または**SQLParamData** (用、IPD フィールド)。 バッファーに格納する呼び出しを指す場合は、このフィールドは SQL_SUCCESS または SQL_SUCCESS_WITH_INFO を返しません、バッファーの内容は 0 に設定されている場合、バッファー内の値を sql_no_data が返される限り、未定義、します。  
  
 呼び出して、ARD でこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_ROWS_FETCHED_PTR 属性を持つ。 呼び出して、APD のこのフィールドを設定することも**SQLSetStmtAttr** SQL_ATTR_PARAMS_PROCESSED_PTR 属性を持つ。  
  
 このフィールドによって示されるバッファーは、アプリケーションによって割り当てられます。 ドライバーによって設定されている、遅延の出力バッファーすることをお勧めします。 既定では null ポインターに設定されます。  
  
## <a name="record-fields"></a>レコードのフィールド  
 各記述子には、列のデータまたは記述子の種類に応じて、動的パラメーターのいずれかを定義するフィールドから成る 1 つまたは複数のレコードが含まれています。 各レコードは、1 つの列またはパラメーターの完全な定義です。  
  
 **SQL_DESC_AUTO_UNIQUE_VALUE [IRDs]**  
 この読み取り専用 SQLINTEGER のレコードのフィールドには、列の場合、自動インクリメント列、または SQL_FALSE 列が自動インクリメント列ではない場合は SQL_TRUE が含まれています。 このフィールドは読み取り専用が、基になる自動インクリメント列読み取り専用とは限りません。  
  
 **SQL_DESC_BASE_COLUMN_NAME [IRDs]**  
 この読み取り専用の SQLCHAR * 結果セット列のレコードのフィールド データ ベースの列名を格納します。 (式である列の場合) と同じベースの列名が存在しない場合、この変数には、空の文字列が含まれています。  
  
 **SQL_DESC_BASE_TABLE_NAME [IRDs]**  
 この読み取り専用の SQLCHAR * レコードのフィールドは、結果セットの列にベース テーブル名を格納します。 ベース テーブル名は定義できません。 またはは適用されない場合、この変数には、空の文字列が含まれます。  
  
 **SQL_DESC_CASE_SENSITIVE [実装記述子]**  
 この読み取り専用 SQLINTEGER のレコードのフィールドが含まれる SQL_TRUE 列またはパラメーターが扱わの照合順序との比較、または SQL_FALSE と大文字小文字を区別、文字がある場合または場合は、列に照合順序との比較と大文字小文字を区別は扱われません列です。  
  
 **SQL_DESC_CATALOG_NAME [IRDs]**  
 この読み取り専用の SQLCHAR * レコードのフィールドには、列を含んだベース テーブルのカタログが含まれています。 戻り値にはドライバーによって異なりますが、列が式の場合、または列がビューの一部である場合です。 データ ソースはカタログをサポートしていないか、カタログを特定することはできない場合、この変数には、空の文字列が含まれています。  
  
 **[すべて] SQL_DESC_CONCISE_TYPE**  
 この SQLSMALLINT ヘッダー フィールドでは、すべてのデータ型、datetime および時間データ型を含む簡潔なデータ型を指定します。  
  
 SQL_DESC_CONCISE_TYPE、SQL_DESC_TYPE、および SQL_DESC_DATETIME_INTERVAL_CODE フィールドの値は相互に依存します。 たびに、フィールドのいずれかを設定、他の設定もあります。 呼び出しで設定できる SQL_DESC_CONCISE_TYPE **SQLBindCol**または**SQLBindParameter**、または**SQLSetDescField**です。 呼び出しで SQL_DESC_TYPE を設定できる**SQLSetDescField**または**SQLSetDescRec**です。  
  
 SQL_DESC_CONCISE_TYPE が期間または日時のデータ型以外の簡潔なデータ型に設定されている場合は、SQL_DESC_TYPE フィールドは同じ値に設定されてし、SQL_DESC_DATETIME_INTERVAL_CODE フィールドが 0 に設定します。  
  
 SQL_DESC_CONCISE_TYPE が、簡潔な datetime 型または interval データ型に設定されている場合は、SQL_DESC_TYPE フィールドは、対応する詳細な型 (SQL_DATETIME または SQL_INTERVAL) に設定されてし、SQL_DESC_DATETIME_INTERVAL_CODE フィールドが適切なサブコードに設定します。  
  
 **[アプリケーションの記述子と Ipd] SQL_DESC_DATA_PTR**  
 この SQLPOINTER レコード フィールドは、(Apd) のパラメーター値または (標準) の列の値を格納する変数を指します。 このフィールドは、*遅延フィールド*です。 設定されているが使用されますは後で、ドライバーによってデータの取得時に使用されません。  
  
 場合、ARD の SQL_DESC_DATA_PTR フィールドで指定された列がバインド解除、 *TargetValuePtr*への呼び出しで引数**SQLBindCol** null ポインター、または、ARD はによって設定されている場合は、SQL_DESC_DATA_PTR フィールドには呼び出す**SQLSetDescField**または**SQLSetDescRec**を null ポインターです。 その他のフィールドは、SQL_DESC_DATA_PTR フィールドが null ポインターに設定されている場合に影響しません。  
  
 場合に呼び出し**SQLFetch**または**SQLFetchScroll**ことでこのフィールドによって示されるバッファーがいっぱいになったが SQL_SUCCESS または sql_success_with_info が返されませんでした、バッファーの内容は未定義です。  
  
 APD、ARD、IPD の SQL_DESC_DATA_PTR フィールドが設定されるたびに、ドライバーは SQL_DESC_TYPE フィールドの値が有効な ODBC C データ型または、ドライバー固有のデータ型のいずれかが含まれていると、データ型に影響する他のすべてのフィールドに整合性があることを確認します。 整合性チェックのメッセージを表示は、のみ、IPD の SQL_DESC_DATA_PTR フィールドの使用です。 具体的には、アプリケーションが、IPD およびそれ以降の呼び出しの SQL_DESC_DATA_PTR フィールドを設定するかどうかは**SQLGetDescField**でこのフィールドが必ずしも返されないことが設定される値。 詳細についてを参照してください「整合性チェック」 [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)です。  
  
 **[すべて] SQL_DESC_DATETIME_INTERVAL_CODE**  
 この SQLSMALLINT レコード フィールドには、SQL_DESC_TYPE フィールドが SQL_DATETIME または SQL_INTERVAL の場合、特定 datetime 型または interval データ型のサブコードが含まれています。 これは、SQL と C の両方のデータ型の場合は true です。 コードは、"CODE"置き換え"TYPE"または"C_TYPE"のいずれかの (datetime 型の場合)、または"CODE"置き換え「間隔」または"C_INTERVAL"(interval 型) でデータ型の名前で構成されます。  
  
 SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE アプリケーション記述子が SQL_C_DEFAULT に設定されて、記述子は、ステートメント ハンドルに関連付けられていない場合は、SQL_DESC_DATETIME_INTERVAL_CODE の内容は未定義です。  
  
 このフィールドは、次の表に、datetime データ型を設定できます。  
  
|Datetime 型|DATETIME_INTERVAL_CODE|  
|--------------------|------------------------------|  
|SQL_TYPE_DATE/SQL_C_TYPE_DATE|SQL_CODE_DATE|  
|SQL_TYPE_TIME/SQL_C_TYPE_TIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP/SQL_C_TYPE_TIMESTAMP|SQL_CODE_TIMESTAMP|  
  
 このフィールドは、次の表に示す interval データ型を設定できます。  
  
|[間隔の種類]|DATETIME_INTERVAL_CODE|  
|-------------------|------------------------------|  
|SQL_INTERVAL_DAY/SQL_C_INTERVAL_DAY|SQL_CODE_DAY|  
|SQL_INTERVAL_DAY_TO_HOUR/SQL_C_INTERVAL_DAY_TO_HOUR|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE/SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND/SQL_C_INTERVAL_DAY_TO_SECOND|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR/SQL_C_INTERVAL_HOUR|SQL_CODE_HOUR|  
QL_INTERVAL_HOUR_TO_MINUTE/SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND/SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE/SQL_C_INTERVAL_MINUTE|SQL_CODE_MINUTE|  
|SQL_INTERVAL_MINUTE_TO_SECOND/SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_CODE_MINUTE_TO_SECOND|  
|SQL_INTERVAL_MONTH/SQL_C_INTERVAL_MONTH|SQL_CODE_MONTH|  
QL_INTERVAL_SECOND/SQL_C_INTERVAL_SECOND|SQL_CODE_SECOND|  
|SQL_INTERVAL_YEAR/SQL_C_INTERVAL_YEAR|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH/SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_CODE_YEAR_TO_MONTH|  
  
 データ間隔し、このフィールドの詳細については、次を参照してください。[のデータ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)です。  
  
 **[すべて] SQL_DESC_DATETIME_INTERVAL_PRECISION**  
 この SQLINTEGER レコード フィールドには、先頭の有効桁数の SQL_DESC_TYPE フィールドが SQL_INTERVAL の場合、間隔が含まれています。 SQL_DESC_DATETIME_INTERVAL_CODE フィールドは、interval データ型に設定されているときに、このフィールドは、先頭の有効桁数の既定の間隔に設定されます。  
  
 **SQL_DESC_DISPLAY_SIZE [IRDs]**  
 この読み取り専用 SQLINTEGER のレコードのフィールドには、列からデータを表示するために必要な文字の最大数が含まれています。  
  
 **SQL_DESC_FIXED_PREC_SCALE [実装記述子]**  
 この読み取り専用 SQLSMALLINT のレコードのフィールドがまたはに設定、列は正確な数値列であり、固定有効桁数と小数点以下桁数を 0 以外の場合は SQL_TRUE SQL_FALSE を場合は、列は固定有効桁数と小数点が正確な数値列ではありません。  
  
 **SQL_DESC_INDICATOR_PTR [アプリケーションの記述子]**  
 標準では、この SQLLEN で * をインジケーター変数フィールド ポイントを記録します。 この変数は、列の値が NULL の場合、SQL_NULL_DATA を格納します。 Apd、インジケーター変数に設定 SQL_NULL_DATA NULL 動的引数を指定します。 それ以外の場合、(場合を除く SQL_DESC_INDICATOR_PTR および SQL_DESC_OCTET_LENGTH_PTR 内の値は、同じポインター) に、変数は 0 です。  
  
 ARD SQL_DESC_INDICATOR_PTR フィールドが null ポインターの場合は、かどうか、列が NULL かに関する情報を返すからドライバーが回避されます。 列が NULL の場合 SQL_DESC_INDICATOR_PTR が null ポインター、SQLSTATE 22002 (インジケーター変数に必要なが指定されていません) が返されます、ドライバーが呼び出しの後にバッファーに格納しようとしたときと**SQLFetch**または**SQLFetchScroll**です。 場合に呼び出し**SQLFetch**または**SQLFetchScroll** SQL_SUCCESS または SQL_SUCCESS_WITH_INFO、バッファーの内容が定義されていないが返されませんでした。  
  
 SQL_DESC_INDICATOR_PTR フィールドは、SQL_DESC_OCTET_LENGTH_PTR によって示されるフィールドが設定されているかどうかを判断します。 列のデータ値が NULL の場合、ドライバーは SQL_NULL_DATA をインジケーター変数を設定します。 SQL_DESC_OCTET_LENGTH_PTR によって示されるフィールドは、設定されません。 NULL 値がフェッチ中に発生しない場合は、SQL_DESC_INDICATOR_PTR が指すバッファーが 0 に設定されているし、SQL_DESC_OCTET_LENGTH_PTR が指すバッファーが、データの長さに設定されています。  
  
 APD の SQL_DESC_INDICATOR_PTR フィールドが null ポインターの場合、アプリケーションは、NULL 引数を指定するこの記述子レコードを使用することはできません。  
  
 このフィールドは、*遅延フィールド*: 時に設定されているは後で、ドライバーによって (標準) の null 値許容属性を示すために、または使用 (Apd) の null 値許容属性を確認するのには使用されません。  
  
 **SQL_DESC_LABEL [IRDs]**  
 この読み取り専用の SQLCHAR * レコードのフィールドには、列のラベルまたはタイトルが含まれています。 列がラベルを持たない場合、この変数には、列名が含まれています。 列が名前のない、ラベルが付いていない場合は、この変数には、空の文字列が含まれています。  
  
 **[すべて] SQL_DESC_LENGTH**  
 SQLULEN レコード フィールドは、文字の文字列の最大値または実際の長さまたはバイトのバイナリ データ型のいずれかです。 これは、固定長のデータ型の最大長または可変長データ型の実際の長さ。 常に、その値には、文字の文字列を終了する null 終了文字が含まれません。 値の型がある SQL_TYPE_DATE、SQL_TYPE_TIME、sql_type_timestamp 型、または SQL interval データ型のいずれかの場合は、このフィールドは、datetime または間隔の値の文字の文字列表現の文字数で長さにします。  
  
 このフィールドの値が""として定義されている長さ ODBC 2 の値と異なる場合があります *.x*です。 詳細については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。  
  
 **SQL_DESC_LITERAL_PREFIX [IRDs]**  
 この読み取り専用の SQLCHAR * レコードのフィールドには、ドライバーはこのデータ型のリテラルのプレフィックスとして認識される文字が含まれています。 この変数には、リテラル プレフィックスは適用されませんデータ型の空の文字列が含まれています。  
  
 **SQL_DESC_LITERAL_SUFFIX [IRDs]**  
 この読み取り専用の SQLCHAR * レコードのフィールドには、このデータ型のリテラルのサフィックスとして、ドライバーが認識できる文字が含まれています。 この変数には、空の文字列データ型のリテラル サフィックスでは適用されませんが含まれています。  
  
 **SQL_DESC_LOCAL_TYPE_NAME [実装記述子]**  
 この読み取り専用の SQLCHAR * レコードのフィールドには、データ型の正規名と異なる可能性があるデータ型の任意のローカライズされた (ネイティブ言語) 名が含まれています。 ローカライズされた名前がない場合は、空の文字列が返されます。 このフィールドは、表示目的でのみです。  
  
 **SQL_DESC_NAME [実装記述子]**  
 この SQLCHAR * 行記述子レコードのフィールドが適用される場合に、列の別名では、含まれています。 列の別名が適用されない場合は、列名が返されます。 どちらの場合、ドライバーでは、SQL_DESC_NAME フィールドを設定するとき、SQL_DESC_UNNAMED フィールドを SQL_NAMED を設定します。 名前の列または列の別名がある場合、ドライバーは SQL_DESC_NAME フィールドの空の文字列を返します。 または、ときに SQL_DESC_UNNAMED フィールドを設定しません。  
  
 アプリケーションは、パラメーター名または名前でストアド プロシージャのパラメーターを指定するエイリアスに、IPD の SQL_DESC_NAME フィールドを設定できます。 (詳細については、次を参照してください[名前 (名前付きパラメーター) でのパラメーターのバインド](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)。)。IRD の SQL_DESC_NAME フィールドは読み取り専用フィールドです。SQLSTATE HY091 アプリケーション設定を試みる場合 (無効な記述子フィールド識別子) が返されます。  
  
 Ipd、ドライバーが名前付きパラメーターをサポートしていない場合は、このフィールドは定義されません。 ドライバーは、名前付きパラメーターをサポートし、パラメーターを記述するには、このフィールドに、パラメーター名が返されます。  
  
 **SQL_DESC_NULLABLE [実装記述子]**  
 IRDs、この読み取り専用 SQLSMALLINT のレコードのフィールドで SQL_NULLABLE 場合は、列が NULL 値を受け入れるかどうかが不明の場合、列は SQL_NO_NULLS 列に NULL 値がない場合または SQL_NULLABLE_UNKNOWN、NULL 値を持つことができます。 このフィールドは、基本列ではなく、結果セット列に関連します。  
  
 Ipd でこのフィールドは常に設定 SQL_NULLABLE のため、動的パラメーターは常に null を許容し、アプリケーションでは設定できません。  
  
 **[すべて] SQL_DESC_NUM_PREC_RADIX**  
 この SQLINTEGER フィールドが含まれます値が 2 の SQL_DESC_TYPE フィールドでのデータ型が、概数データ型の場合、SQL_DESC_PRECISION フィールドには、ビットの数が含まれているためです。 このフィールドは値 10 の SQL_DESC_TYPE フィールドでのデータ型が、正確な数値データ型の場合 SQL_DESC_PRECISION フィールドには、10 進数字の数が含まれているためです。 このフィールドは、すべての非数値データ型の場合は 0 に設定されます。  
  
 **[すべて] SQL_DESC_OCTET_LENGTH**  
 この SQLLEN レコード フィールドには、文字の文字列またはバイナリ データ型の長さ、(バイト単位) が含まれています。 固定長文字またはバイナリ型では、これは、実際の長さ (バイト単位) です。 可変長の文字またはバイナリ型では、これは、最大長 (バイト単位) です。 この値は、実装記述子の null 終端文字用の領域を常に除外され、常に アプリケーションの記述子の null 終端文字のためのスペースが含まれます。 アプリケーション データには、このフィールドには、バッファーのサイズが含まれています。 Apd、このフィールドは出力や入力/出力パラメーターに対してのみ定義されます。  
  
 **SQL_DESC_OCTET_LENGTH_PTR [アプリケーションの記述子]**  
 この SQLLEN * フィールドがポイントする、動的引数 (パラメーター記述子) か (行記述子) にバインドされた列の値の合計長 (バイト単位) を格納する変数を記録します。  
  
 すべての引数の文字の文字列およびバイナリを除く、APD のこの値が無視されます。このフィールドは、SQL_NTS をポイントしている場合、動的引数が null で終了する必要があります。 示していることを実行時データ パラメーターがバインドされたパラメーターになりますアプリケーションこのフィールドを設定、APD の適切なレコードを変数にする、実行時では、値またはを含む SQL_DATA_AT_EXEC SQL_LEN_DATA_AT_EXEC マクロの結果. このようなフィールドは 1 つ以上の場合は、SQL_DESC_DATA_PTR を決定するパラメーターが要求されているアプリケーションに役立つパラメーターを一意に識別する値を設定できます。  
  
 ARD OCTET_LENGTH_PTR フィールドが null ポインターの場合、ドライバーは、列の長さの情報を返しません。 APD の SQL_DESC_OCTET_LENGTH_PTR フィールドが null ポインターの場合、ドライバーでは、文字の文字列およびバイナリ値が null で終わる前提としています。 (バイナリ値は null で終了することはできませんが切り捨てられないようにする長さを指定する必要があります)。  
  
 場合に呼び出し**SQLFetch**または**SQLFetchScroll**ことでこのフィールドによって示されるバッファーがいっぱいになったが SQL_SUCCESS または sql_success_with_info が返されませんでした、バッファーの内容は未定義です。 このフィールドは、*遅延フィールド*です。 時に設定されているが使用されますは後で、ドライバーによって決定またはデータのオクテットの長さを示すためには使用されません。  
  
 **SQL_DESC_PARAMETER_TYPE [Ipd]**  
 この SQLSMALLINT レコードのフィールドの入力パラメーターの入力/出力パラメーター、出力パラメーター、入出力ストリーム パラメーター、SQL_PARAM_INPUT_OUTPUT_STREAM または sql _ SQL_PARAM_OUTPUT SQL_PARAM_INPUT_OUTPUT SQL_PARAM_INPUT に設定されています。ストリーム出力パラメーターの PARAM_OUTPUT_STREAM します。 既定では SQL_PARAM_INPUT に設定されます。  
  
 IPD フィールドが設定 SQL_PARAM_INPUT を既定では (SQL_ATTR_ENABLE_AUTO_IPD ステートメント属性は SQL_FALSE) ドライバーでは、IPD が自動的に設定されていない場合。 アプリケーションは、入力パラメーターではないパラメーターの IPD のこのフィールドを設定する必要があります。  
  
 **[すべて] SQL_DESC_PRECISION**  
 この SQLSMALLINT レコード フィールドには、正確な数値型 (バイナリ精度) が、概数型の仮数部のビット数か、SQL_TYPE_TIME、SQL_TYPE の秒部分の数字の数の桁の数字の数が含まれています_TIMESTAMP、または SQL_INTERVAL_SECOND データを入力します。 このフィールドは、他のすべてのデータ型に対して定義されていません。  
  
 このフィールドの値は"precision"として ODBC 2 で定義されているの値と異なる場合があります *.x*です。 詳細については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。  
  
 **SQL_DESC_ROWVER [実装記述子]**  
 この SQLSMALLINTrecord フィールドは、(たとえば、SQL Server では、"timestamp"型の列)、行が更新されたときに、列が自動的に、DBMS によって変更するかどうかを示します。 このレコード フィールドの値は、それ以外の場合に列が、行のバージョン管理の列の場合は SQL_TRUE および SQL_FALSE に設定されます。 この列の属性は、呼び出しに似ています**SQLSpecialColumns** IdentifierType の SQL_ROWVER 列が自動的に更新するかどうかを決定するとします。  
  
 **[すべて] SQL_DESC_SCALE**  
 この SQLSMALLINT レコード フィールドには、decimal および numeric データ型に対して定義された有効桁数が含まれています。 フィールドは、他のすべてのデータ型に対して定義されていません。  
  
 このフィールドの値は、ODBC 2 で定義されている"scale"の値と異なる場合があります *.x*です。 詳細については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。  
  
 **SQL_DESC_SCHEMA_NAME [IRDs]**  
 この読み取り専用の SQLCHAR * レコードのフィールドには、列を含んだベース テーブルのスキーマ名が含まれています。 戻り値にはドライバーによって異なりますが、列が式の場合、または列がビューの一部である場合です。 データ ソースはスキーマをサポートしていないか、スキーマ名を特定することはできない場合、この変数には、空の文字列が含まれています。  
  
 **SQL_DESC_SEARCHABLE [IRDs]**  
 この読み取り専用 SQLSMALLINT のレコードのフィールドは、次の値のいずれかに設定されます。  
  
-   SQL_PRED_NONE で列を使用できない場合、**場所**句。 (これは、ODBC 2 で SQL_UNSEARCHABLE 値として同じ *.x*)。  
  
-   SQL_PRED_CHAR では、列を使用する場合、**場所**されますが、句、**など**述語。 (これは、ODBC 2 で SQL_LIKE_ONLY 値として同じ *.x*)。  
  
-   SQL_PRED_BASIC では、列を使用する場合、**場所**を除くすべての比較演算子を含む句**など**です。 (これは、ODBC 2 で SQL_EXCEPT_LIKE 値として同じ *.x*)。  
  
-   SQL_PRED_SEARCHABLE では、列を使用する場合、**場所**任意の比較演算子を含む句。  
  
 **SQL_DESC_TABLE_NAME [IRDs]**  
 この読み取り専用の SQLCHAR * レコードのフィールドには、この列を含むベース テーブルの名前が含まれています。 戻り値にはドライバーによって異なりますが、列が式の場合、または列がビューの一部である場合です。  
  
 **[すべて] SQL_DESC_TYPE**  
 この SQLSMALLINT レコード フィールドは、datetime および間隔のデータ型を除くすべてのデータ型の簡潔な SQL または C データ型を指定します。 Datetime および時間データ型の場合は、このフィールドが SQL_DATETIME または SQL_INTERVAL 冗長データの種類を指定します。  
  
 このフィールドには、SQL_DATETIME または SQL_INTERVAL が含まれています、されるたびに SQL_DESC_DATETIME_INTERVAL_CODE フィールドは、簡潔な型の適切なサブコードを含める必要があります。 Datetime データ型の SQL_DESC_TYPE には、sql_datetime 型が含まれています、SQL_DESC_DATETIME_INTERVAL_CODE フィールドには、特定の datetime データ型のサブコードが含まれています。 Interval データ型の SQL_DESC_TYPE SQL_INTERVAL を含み SQL_DESC_DATETIME_INTERVAL_CODE フィールドには、特定の間隔のデータ型のサブコードが含まれています。  
  
 SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE フィールドの値は相互に依存します。 たびに、フィールドのいずれかを設定、他の設定もあります。 呼び出しで SQL_DESC_TYPE を設定できる**SQLSetDescField**または**SQLSetDescRec**です。 呼び出しで設定できる SQL_DESC_CONCISE_TYPE **SQLBindCol**または**SQLBindParameter**、または**SQLSetDescField**です。  
  
 SQL_DESC_TYPE が期間または日時のデータ型以外の簡潔なデータ型に設定されている場合、SQL_DESC_CONCISE_TYPE フィールドが同じ値に設定されているし、SQL_DESC_DATETIME_INTERVAL_CODE フィールドが 0 に設定します。  
  
 SQL_DESC_TYPE の詳細な datetime または interval データ型 (SQL_DATETIME または SQL_INTERVAL) に設定されている、適切なサブコードに SQL_DESC_DATETIME_INTERVAL_CODE フィールドが設定されている場合は、SQL_DESC_CONCISE 型のフィールドは対応する簡潔な型に設定されます。 SQLSTATE HY021 が返されます、簡潔な datetime 型または interval 型のいずれかに SQL_DESC_TYPE を設定しようとしています (不整合な記述子情報)。  
  
 呼び出し、SQL_DESC_TYPE フィールドを設定すると、 **SQLBindCol**、 **SQLBindParameter**、または**SQLSetDescField**、次のフィールドは、次の既定値に設定されます次の表のようです。 同じレコードの残りのフィールドの値は未定義です。  
  
|SQL_DESC_TYPE の値|その他のフィールドが暗黙的に設定します。|  
|------------------------------|---------------------------------|  
|SQL_CHAR、SQL_VARCHAR、SQL_C_CHAR、SQL_C_VARCHAR|SQL_DESC_LENGTH は 1 に設定されます。 SQL_DESC_PRECISION は 0 に設定されます。|  
|SQL_DATETIME|SQL_CODE_DATE または SQL_CODE_TIME に SQL_DESC_DATETIME_INTERVAL_CODE を設定すると、ときに、SQL_DESC_PRECISION は 0 に設定されます。 SQL_DESC_TIMESTAMP に設定されているときに、SQL_DESC_PRECISION は 6 に設定されます。|  
|SQL_DECIMAL、SQL_NUMERIC、SQL_C_NUMERIC|SQL_DESC_SCALE は 0 に設定されます。 SQL_DESC_PRECISION は、それぞれのデータ型の実装で定義された有効桁数に設定されます。<br /><br /> 参照してください[SQL から c: 数値へ](../../../odbc/reference/appendixes/sql-to-c-numeric.md)SQL_C_NUMERIC 値を手動でバインドする方法についてはします。|  
|SQL_C_FLOAT、使用できます。|SQL_DESC_PRECISION に設定されている既定の実装定義の有効桁数を使用できます。|  
|SQL_INTERVAL|Interval データ型を SQL_DESC_DATETIME_INTERVAL_CODE を設定すると、SQL_DESC_DATETIME_INTERVAL_PRECISION が 2 (既定の間隔先頭の有効桁数) に設定します。 間隔は、秒のコンポーネントを持つ、SQL_DESC_PRECISION が 6 (既定の間隔 (秒) の有効桁数) に設定されます。|  
  
 アプリケーションを呼び出すと**SQLSetDescField**の呼び出しではなく、記述子フィールドを設定する**SQLSetDescRec**アプリケーションは、データ型を宣言する必要がありますまずします。 ときに、前の表に示されている他のフィールドが暗黙的に設定します。 かどうか、値のいずれかに暗黙的にセットは使用できません、アプリケーションが呼び出すことができますし、 **SQLSetDescField**または**SQLSetDescRec**不正な値を明示的に設定します。  
  
 **SQL_DESC_TYPE_NAME [実装記述子]**  
 この読み取り専用の SQLCHAR * レコードのフィールドには、データ ソースに依存する型の名前 (たとえば、"CHAR"、"VARCHAR"、およびなど) が含まれています。 データ型の名前が不明な場合は、この変数には、空の文字列が含まれています。  
  
 **SQL_DESC_UNNAMED [実装記述子]**  
 この SQLSMALLINT レコード フィールドを行記述子では、SQL_DESC_NAME フィールドを設定するとき、SQL_NAMED またはときに、ドライバーによって設定されます。 SQL_DESC_NAME フィールドには、列の別名が含まれている場合、または列の別名が適用されない場合は、ドライバーは SQL_NAMED を SQL_DESC_UNNAMED フィールドを設定します。 アプリケーション SQL_DESC_NAME フィールドの場合、IPD のパラメーター名またはエイリアスに、ドライバーは、IPD の SQL_DESC_UNNAMED フィールドを SQL_NAMED に設定します。 名前のない列または列の別名がある場合、ドライバーは、ときに、SQL_DESC_UNNAMED フィールドを設定します。  
  
 アプリケーションは、ときに、IPD の SQL_DESC_UNNAMED フィールドを設定できます。 ドライバーは SQLSTATE HY091 を返します (無効な記述子フィールド識別子) 場合は、アプリケーションは、IPD の SQL_DESC_UNNAMED フィールド SQL_NAMED に設定しようとしています。 IRD の SQL_DESC_UNNAMED フィールドは読み取り専用です。SQLSTATE HY091 アプリケーション設定を試みる場合 (無効な記述子フィールド識別子) が返されます。  
  
 **SQL_DESC_UNSIGNED [実装記述子]**  
 列のデータ型が署名されている場合は、この読み取り専用 SQLSMALLINT のレコードのフィールドを列の型が符号なしまたは数値以外の場合は SQL_TRUE または SQL_FALSE に設定されます。  
  
 **SQL_DESC_UPDATABLE [IRDs]**  
 この読み取り専用 SQLSMALLINT のレコードのフィールドは、次の値のいずれかに設定されます。  
  
-   SQL_ATTR_READ_ONLY 場合は、結果セット列は、読み取り専用です。  
  
-   SQL_ATTR_WRITE 場合は、結果セット列は、読み取り/書き込みです。  
  
-   SQL_ATTR_READWRITE_UNKNOWN 結果セット列であるかどうかが不明な場合があるか更新可能です。  
  
 SQL_DESC_UPDATABLE では、ベース テーブルの列ではなく、結果セット内の列の更新機能について説明します。 この結果セット列の基になるベース テーブル内の列の更新は、このフィールドの値よりも異なる可能性があります。 列は更新可能であるかどうかは、データ型、ユーザー特権、および、結果セット自体の定義に基づくことができます。 明確ではない列は更新可能かどうか、SQL_ATTR_READWRITE_UNKNOWN が返されます。  
  
## <a name="consistency-checks"></a>整合性チェック  
 アプリケーションが ARD、APD、または IPD の SQL_DESC_DATA_PTR フィールドの値で渡すたびに、整合性チェックは、ドライバーによって自動的に実行します。 他のフィールドと一貫性のある任意のフィールドがない場合**SQLSetDescField** SQLSTATE HY021 が返されます (不整合な記述子情報)。 詳細についてを参照してください「整合性チェック」 [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|列のバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|パラメーターのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|記述子フィールドの取得|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|複数の記述子フィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|複数の記述子フィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)
