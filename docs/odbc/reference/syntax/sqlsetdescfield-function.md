---
title: 関数の設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 122d4b26d1d75811d4a8e252378ce8f81ca2c66b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299552"
---
# <a name="sqlsetdescfield-function"></a>SQLSetDescField 関数

**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **記述子**レコードの単一フィールドの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SQLRETURN SQLSetDescField(  
     SQLHDESC      DescriptorHandle,  
     SQLSMALLINT   RecNumber,  
     SQLSMALLINT   FieldIdentifier,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    BufferLength);  
```  
  
## <a name="arguments"></a>引数  
 *DescriptorHandle*  
 [入力]記述子ハンドル。  
  
 *RecNumber*  
 [入力]アプリケーションが設定しようとするフィールドを含む記述子レコードを示します。 記述子レコードには 0 から番号が付けられ、レコード番号 0 はブックマーク・レコードになります。 ヘッダー フィールドの*RecNumber*引数は無視されます。  
  
 *FieldIdentifier*  
 [入力]値を設定する記述子のフィールドを示します。 詳細については、「コメント」セクションの「*フィールド識別子*の引数」を参照してください。  
  
 *ValuePtr*  
 [入力]記述子情報を格納しているバッファーへのポインター、または整数値。 データ型は *、 FieldIdentifier*の値によって異なります。 *ValuePtr*が整数値の場合は *、FieldIdentifier*引数の値に応じて、8 バイト (SQLLEN)、4 バイト (SQLINTEGER) または 2 バイト (SQLSMALLINT) と見なされます。  
  
 *BufferLength*  
 [入力]*フィールド識別子*が ODBC で定義されたフィールドで *、ValuePtr*が文字列またはバイナリ バッファを指している場合、この引数は **ValuePtr*の長さになります。 文字列データの場合、この引数には文字列のバイト数を含める必要があります。  
  
 *フィールド識別子*が ODBC で定義されたフィールドで *、ValuePtr*が整数の場合、*バッファー長*は無視されます。  
  
 *FieldIdentifier*がドライバー定義フィールドの場合、アプリケーションは *、BufferLength*引数を設定してドライバー マネージャーにフィールドの性質を示します。 *バッファー長*には、次の値を指定できます。  
  
-   *ValuePtr*が文字列へのポインタである場合 *、BufferLength*は文字列またはSQL_NTSの長さです。  
  
-   *ValuePtr*がバイナリ バッファへのポインタである場合、アプリケーションは SQL_LEN_BINARY_ATTR(*長さ*) マクロの結果を*BufferLength*に格納します。 この場合は、負の値を*BufferLength*に配置します。  
  
-   *ValuePtr*が文字列またはバイナリ文字列以外の値へのポインターである場合 *、BufferLength*には値がSQL_IS_POINTER必要があります。  
  
-   *ValuePtr*に固定長の値が含まれている場合 *、BufferLength*は、必要に応じてSQL_IS_INTEGER、SQL_IS_UINTEGER、SQL_IS_SMALLINT、またはSQL_IS_USMALLINTになります。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLSetDescField**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_DESCの*ハンドル型*と*記述子ハンドル**を持*つ**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLSetDescField**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S02|オプション値が変更されました|ドライバーは*\*ValuePtr*で指定された値をサポートしていなかった *(ValuePtr*がポインターの場合)、ValuePtr の値 *(ValuePtr*が整数値の場合)、*\*または ValuePtr*が実装の動作条件のために無効であったため、ドライバーは、同様の値を置き換えました。 *ValuePtr* (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07009|記述子インデックスが無効です|引数*は*レコード フィールド *、RecNumber*引数は 0、引数*は*IPD ハンドルを参照します。<br /><br /> *引数が*0 未満であり、*引数は*ARD または APD を参照しました。<br /><br /> *RecNumber*引数は、データ ソースがサポートできる列またはパラメーターの最大数を超えており、引数*DescriptorHandle*は APD または ARD を参照しました。<br /><br /> (DM)*引数が*SQL_DESC_COUNTされ*\*、ValuePtr*引数が 0 未満でした。<br /><br /> *RecNumber*引数は 0 と等しく、*引数は*暗黙的に割り当てられた APD を参照しました。 (このエラーは、明示的に割り当てられたアプリケーション記述子が実行時間まで APD か ARD かは不明であるため、明示的に割り当てられたアプリケーション記述子では発生しません。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|22001|文字列データ(右切り捨て)|引数*が*SQL_DESC_NAMEされ *、BufferLength*引数がSQL_MAX_IDENTIFIER_LENより大きい値でした。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM) *DescriptorHandle*は、非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていた*ステートメント ハンドル*に関連付けられていた。<br /><br /> (DM) 記述子ハンドルが関連付けられ、SQL_NEED_DATA返された*ステートメント ハンドル*に対して **、SQL 実行****、SQLExecDirect、SQLBulkOperations**、または**SQLSetPos**が呼び出されました。 **SQLExecDirect** *DescriptorHandle* この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM)*記述子ハンドル*に関連付けられている接続ハンドルに対して非同期に実行する関数が呼び出されました。 この非同期関数は **、SQLSetDescField**関数が呼び出されたときに実行されていました。<br /><br /> (DM) 記述子*ハンドル*に関連付けられているステートメント ハンドルの 1 つに対して **、SQL 実行** **、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY016|実装行記述子を変更できません|引数*が*IRD に関連付けられており、*引数 FieldIdentifier*がSQL_DESC_ARRAY_STATUS_PTRまたはSQL_DESC_ROWS_PROCESSED_PTRされていません。|  
|HY021|記述子情報の不一致|SQL_DESC_TYPEおよびSQL_DESC_DATETIME_INTERVAL_CODEフィールドは、有効な ODBC SQL タイプ、または有効なドライバ固有の SQL タイプ (IPD の場合) または有効な ODBC C タイプ (APK または ARD の場合) を形成しません。<br /><br /> 整合性チェック中にチェックされた記述子情報が一貫していません。 **(SQLSetDescRec**の「整合性チェック」を参照してください。|  
|HY090|無効な文字列またはバッファ長|(DM) * \*ValuePtr*は文字列であり *、BufferLength*はゼロ未満でしたが、SQL_NTSと等しくありません。<br /><br /> (DM) ドライバーは ODBC 2 *.x*ドライバー、記述子は*ARD、ColumnNumber*引数は 0 に設定され、引数*BufferLength*に指定された値が 4 に等しめなかった。|  
|HY091|記述子フィールド ID が無効です|*FieldIdentifier*引数に指定された値は、ODBC 定義フィールドではなく、実装で定義された値ではありませんでした。<br /><br /> 引数に*対して**無効*な引数です。<br /><br /> *FieldIdentifier*引数は、読み取り専用の ODBC 定義フィールドでした。|  
|HY092|属性/オプション識別子が無効です|* \*ValuePtr*の値が *、引数 FieldIdentifier*に対して無効でした。<br /><br /> *引数*がSQL_DESC_UNNAMEDされ *、ValuePtr*がSQL_NAMEDされました。|  
|HY105|無効なパラメータタイプ|(DM) SQL_DESC_PARAMETER_TYPE フィールドに指定された値が無効です。 (詳細については **、SQLBindParameter**の「*入力出力型*引数」セクションを参照してください。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、ODBC 3.8 の新機能を](../../../odbc/reference/what-s-new-in-odbc-3-8.md)参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*記述子ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 アプリケーションは**SQLSetDescField**を呼び出して、記述子フィールドを一度に 1 つずつ設定できます。 1 回の呼び出し**では、1**つの記述子に 1 つのフィールドを設定します。 この関数は、フィールドを設定できる場合に、任意の記述子型の任意のフィールドを設定するために呼び出すことができます。 (このセクションの後半の表を参照してください。  
  
> [!NOTE]  
>  **SQLSetDescField**の呼び出しが失敗した場合 *、RecNumber*引数によって識別される記述子レコードの内容は未定義です。  
  
 その他の関数を呼び出して、関数の 1 回の呼び出しで複数の記述子フィールドを設定できます。 **SQLSetDescRec**関数は、列またはパラメーターにバインドされたデータ型とバッファーに影響を与えるさまざまなフィールド (SQL_DESC_TYPE、SQL_DESC_DATETIME_INTERVAL_CODE、SQL_DESC_OCTET_LENGTH、SQL_DESC_PRECISION、SQL_DESC_SCALE、SQL_DESC_DATA_PTR、SQL_DESC_OCTET_LENGTH_PTR、およびSQL_DESC_INDICATOR_PTRフィールド) を設定します。 **SQLBindCol**または**SQLBindParameter**を使用して、列またはパラメーターのバインディングの完全な仕様を作成できます。 これらの関数は、1 つの関数呼び出しで特定の記述子フィールドのグループを設定します。  
  
 **バインド**ポインター (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、またはSQL_DESC_OCTET_LENGTH_PTR) にオフセットを追加することによって、バインディング バッファーを変更するために呼び出すことができます。 これにより **、SQLBindCol**または**SQLBindParameter**を呼び出さずにバインディング バッファーが変更され、アプリケーションはSQL_DESC_DATA_TYPEなどの他のフィールドを変更せずにSQL_DESC_DATA_PTRを変更できます。  
  
 アプリケーションが**SQLSetDescField**を呼び出して、SQL_DESC_COUNT 以外のフィールド、またはSQL_DESC_DATA_PTR、SQL_DESC_OCTET_LENGTH_PTR、またはSQL_DESC_INDICATOR_PTRの遅延フィールドを設定すると、レコードは非バインドになります。  
  
 記述子ヘッダー フィールドは、適切な*フィールド識別子*を指定して**SQLSetDescField**を呼び出すことによって設定されます。 多くのヘッダー フィールドはステートメント属性でもあるため、 **SQLSetStmtAttr**の呼び出しによって設定することもできます。 これにより、アプリケーションは、最初に記述子ハンドルを取得せずに記述子フィールドを設定できます。 ヘッダー フィールドを設定するために**SQLSetDescField**が呼び出されると *、RecNumber*引数は無視されます。  
  
 *RecNumber* 0 は、ブックマーク フィールドを設定するために使用されます。  
  
> [!NOTE]  
>  ステートメント属性SQL_ATTR_USE_BOOKMARKSは、ブックマークフィールドを設定するために**SQLSetDescField を**呼び出す前に、常に設定する必要があります。 必須ではありませんが、強くお勧めします。  
  
## <a name="sequence-of-setting-descriptor-fields"></a>記述子フィールドの設定のシーケンス  
 **SQLSetDescField**を呼び出して記述子フィールドを設定する場合、アプリケーションは特定の順序に従う必要があります。  
  
1.  アプリケーションは、最初にSQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE、またはSQL_DESC_DATETIME_INTERVAL_CODEフィールドを設定する必要があります。  
  
2.  これらのフィールドの 1 つを設定した後、アプリケーションはデータ型の属性を設定し、ドライバーはデータ型の適切な既定値にデータ型の属性フィールドを設定します。 型属性フィールドの自動デフォルト設定により、アプリケーションがデータ型を指定した後で、記述子を常に使用できるようになります。 アプリケーションがデータ型属性を明示的に設定した場合、その属性はデフォルト属性をオーバーライドします。  
  
3.  手順 1 で示したフィールドの 1 つを設定し、データ型属性を設定した後、アプリケーションはSQL_DESC_DATA_PTR設定できます。 これにより、記述子フィールドの整合性チェックが要求されます。 アプリケーションがSQL_DESC_DATA_PTR フィールドを設定した後にデータ型または属性を変更すると、ドライバーはSQL_DESC_DATA_PTRを null ポインターに設定し、レコードのバインドを解除します。 これにより、アプリケーションは、記述子レコードが使用できるようになる前に、適切なステップを順番に完了させます。  
  
## <a name="initialization-of-descriptor-fields"></a>記述子フィールドの初期化  
 記述子が割り当てられると、記述子のフィールドを既定値に初期化したり、既定値なしで初期化したり、記述子の型に対して未定義にすることができます。 次の表は、記述子の各型の各フィールドの初期化を示し、"D" はフィールドが既定で初期化されていることを示し、"ND" はフィールドが既定なしで初期化されていることを示します。 数値が表示されている場合、フィールドの既定値はその数値です。 テーブルには、フィールドが読み取り/書き込み (R/W) と読み取り専用 (R) のどちらであるかも示されます。  
  
 IRD のフィールドには、ステートメントの準備または実行が完了し、IRD が設定された後にのみデフォルト値が設定されます。 IRD が設定されるまで、IRD のフィールドにアクセスしようとするとエラーが返されます。  
  
 記述子フィールドの中には、記述子タイプ (ARD および IID、および A/A- と IPD) の 1 つ以上の記述子フィールドが定義されていますが、すべてではありません。 記述子の型に対してフィールドが定義されていない場合、その記述子を使用する関数によってフィールドが定義されていない場合は必要ありません。  
  
 **SQLGetDescField**によってアクセスできるフィールドは、必ずしも**SQLSetDescField**によって設定されるとは限りません。 次の表に **、SQLSetDescField**で設定できるフィールドを示します。  
  
 ヘッダー フィールドの初期化については、次の表で説明します。  
  
|ヘッダー フィールド名|Type|R/W|Default|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_ALLOC_TYPE|SQLSMALLINT|ARD: R APD: R IRD: R IPD: R|ARD: 明示的な場合は、暗黙的またはSQL_DESC_ALLOC_USERのSQL_DESC_ALLOC_AUTO<br /><br /> APD: 明示的な場合は、暗黙的またはSQL_DESC_ALLOC_USERのSQL_DESC_ALLOC_AUTO<br /><br /> IRD: SQL_DESC_ALLOC_AUTO<br /><br /> IPD: SQL_DESC_ALLOC_AUTO|  
|SQL_DESC_ARRAY_SIZE|SQLULEN|ARD: R/W APD: R/W IRD: 未使用 IPD: 未使用|ARD:[1] APD:[1] IRD: 未使用 IPD: 未使用|  
|SQL_DESC_ARRAY_STATUS_PTR|SQLSmallint*|ARD: R/W APD: R/W IRD: R/W IPD: R/W|無効な ptr APD: null ptr IRD: null ptr IPD: null ptr|  
|SQL_DESC_BIND_OFFSET_PTR|SQLLEN*|ARD: R/W APD: R/W IRD: 未使用 IPD: 未使用|ARD: NULL ptr APD: NULL ptr IRD: 未使用 IPD: 未使用|  
|SQL_DESC_BIND_TYPE|SQLINTEGER|ARD: R/W APD: R/W IRD: 未使用 IPD: 未使用|ARD: SQL_BIND_BY_COLUMN<br /><br /> APD: SQL_BIND_BY_COLUMN<br /><br /> IRD: 未使用<br /><br /> IPD: 未使用|  
|SQL_DESC_COUNT|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: 0 APD: 0 IRD: D IPD: 0|  
|SQL_DESC_ROWS_PROCESSED_PTR|SQLULEN*|ARD: 未使用の APD: 未使用の IRD: R/W IPD: R/W|ARD: 未使用の APD: 未使用の IRD: null ptr IPD: null ptr|  
  
 [1] これらのフィールドは、IPD がドライバによって自動的に設定される場合にのみ定義されます。 定義されていない場合、それらは未定義です。 アプリケーションがこれらのフィールドを設定しようとすると、SQLSTATE HY091 (無効な記述子フィールド ID) が返されます。  
  
 レコード フィールドの初期化は、次の表に示すようにします。  
  
|レコード フィールド名|Type|R/W|Default|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_BASE_COLUMN_NAME|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_BASE_TABLE_NAME|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_CASE_SENSITIVE|SQLINTEGER|ARD: 未使用の APD: 未使用の IRD: R IPD: R|ARD: 未使用の APD: 未使用の IRD: D IPD: D[1]|  
|SQL_DESC_CATALOG_NAME|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_CONCISE_TYPE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: デフォルトの APD SQL_C_: デフォルトの IRD SQL_C_: D IPD: ND|  
|SQL_DESC_DATA_PTR|SQL ポインター|ARD: R/W APD: R/W IRD: 未使用 IPD: 未使用|ARD: NULL ptr APD: NULL ptr IRD: 未使用 IPD: 未使用[2]|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQLINTEGER|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_DISPLAY_SIZE|SQLLEN|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_FIXED_PREC_SCALE|SQLSMALLINT|ARD: 未使用の APD: 未使用の IRD: R IPD: R|ARD: 未使用の APD: 未使用の IRD: D IPD: D[1]|  
|SQL_DESC_INDICATOR_PTR|SQLLEN *|ARD: R/W APD: R/W IRD: 未使用 IPD: 未使用|ARD: NULL ptr APD: NULL ptr IRD: 未使用 IPD: 未使用|  
|SQL_DESC_LABEL|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_LENGTH|SQLULEN|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_LITERAL_PREFIX|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_LITERAL_SUFFIX|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_LOCAL_TYPE_NAME|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: R|ARD: 未使用の APD: 未使用の IRD: D IPD: D[1]|  
|SQL_DESC_NAME|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: R/W|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_NULLABLE|SQLSMALLINT|ARD: 未使用の APD: 未使用の IRD: R IPD: R|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_NUM_PREC_RADIX|SQLINTEGER|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH|SQLLEN|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH_PTR|SQLLEN *|ARD: R/W APD: R/W IRD: 未使用 IPD: 未使用|ARD: NULL ptr APD: NULL ptr IRD: 未使用 IPD: 未使用|  
|SQL_DESC_PARAMETER_TYPE|SQLSMALLINT|ARD: 未使用の APD: 未使用の IRD: 未使用 IPD: R/W|ARD: 未使用の APD: 未使用の IRD: 未使用 IPD: D=SQL_PARAM_INPUT|  
|SQL_DESC_PRECISION|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_ROWVER|SQLSMALLINT|ARD: 未使用<br /><br /> APD: 未使用<br /><br /> IRD: R<br /><br /> IPD: R|ARD: 未使用<br /><br /> APD: 未使用<br /><br /> RD: ND<br /><br /> IPD: ND|  
|SQL_DESC_SCALE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_SCHEMA_NAME|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_SEARCHABLE|SQLSMALLINT|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_TABLE_NAME|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
|SQL_DESC_TYPE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: SQL_C_DEFAULT APD: SQL_C_DEFAULT Rd: D IPD: ND|  
|SQL_DESC_TYPE_NAME|SQLCHAR *|ARD: 未使用の APD: 未使用の IRD: R IPD: R|ARD: 未使用の APD: 未使用の IRD: D IPD: D[1]|  
|SQL_DESC_UNNAMED|SQLSMALLINT|ARD: 未使用の APD: 未使用の IRD: R IPD: R/W|ARD: ND APD: ND RD: D IPD: ND|  
|SQL_DESC_UNSIGNED|SQLSMALLINT|ARD: 未使用の APD: 未使用の IRD: R IPD: R|ARD: 未使用の APD: 未使用の IRD: D IPD: D[1]|  
|SQL_DESC_UPDATABLE|SQLSMALLINT|ARD: 未使用の APD: 未使用の IRD: R IPD: 未使用|ARD: 未使用の APD: 未使用の IRD: D IPD: 未使用|  
  
 [1] これらのフィールドは、IPD がドライバによって自動的に設定される場合にのみ定義されます。 定義されていない場合、それらは未定義です。 アプリケーションがこれらのフィールドを設定しようとすると、SQLSTATE HY091 (無効な記述子フィールド ID) が返されます。  
  
 IPD のSQL_DESC_DATA_PTRフィールドを設定して、整合性チェックを強制することができます。 後続の呼び出しでは **、ドライバー**はSQL_DESC_DATA_PTR**SQLGetDescRec**設定された値を返す必要はありません。  
  
## <a name="fieldidentifier-argument"></a>フィールド識別子の引数  
 *FieldIdentifier*引数は、設定する記述子フィールドを示します。 記述子には、次のセクション「ヘッダー フィールド」で説明するヘッダー フィールドと、"ヘッダー フィールド" セクションの後のセクションで説明されているレコード フィールドから成る 0 個以上の*記述子レコード*から構成される*記述子ヘッダー*が含まれています。  
  
## <a name="header-fields"></a>ヘッダー フィールド  
 各記述子には、以下のフィールドから構成されるヘッダーがあります。  
  
 **SQL_DESC_ALLOC_TYPE [すべて]**  
 この読み取り専用の SQLSMALLINT ヘッダー フィールドは、記述子がドライバーによって自動的に割り当てられたか、アプリケーションによって明示的に割り当てられたかを指定します。 アプリケーションは、このフィールドを取得できますが、変更することはできません。 記述子がドライバーによって自動的に割り当てられた場合、フィールドは、ドライバーによってSQL_DESC_ALLOC_AUTOに設定されます。 記述子がアプリケーションによって明示的に割り当てられた場合は、ドライバーによってSQL_DESC_ALLOC_USERに設定されます。  
  
 **SQL_DESC_ARRAY_SIZE [アプリケーション記述子]**  
 ARD では、この SQLULEN ヘッダー・フィールドは行セット内の行数を指定します。 これは **、SQLFetch**または**SQLFetchScroll**の呼び出しによって返される行の数、または**SQLBulkOperations**または**SQLSetPos**の呼び出しによって操作される行の数です。  
  
 APK では、この SQLULEN ヘッダー・フィールドは、各パラメーターの値の数を指定します。  
  
 このフィールドのデフォルト値は 1 です。 SQL_DESC_ARRAY_SIZEが 1 より大きい場合、SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および APD または ARD のSQL_DESC_OCTET_LENGTH_PTRはアレイを指します。 各配列の基数は、このフィールドの値と等しくなります。  
  
 ARD のこのフィールドは、SQL_ATTR_ROW_ARRAY_SIZE属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。 APD のこのフィールドは、SQL_ATTR_PARAMSET_SIZE属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
 **SQL_DESC_ARRAY_STATUS_PTR [すべて]**  
 記述子の種類ごとに、この SQLUSMALLINT * ヘッダー フィールドは、SQLUSMALLINT 値の配列を指します。 これらの配列には、行状況配列 (IRD)、パラメーター状況配列 (IPD)、行操作配列 (ARD)、およびパラメーター操作配列 (APD) の名前が付けられます。  
  
 IRD では、このヘッダー フィールドは **、SQLBulkOperations** **、SQLFetch、SQLFetchScroll**、または**SQLSetPos**の呼び出し後に、状態値を含む行の状態配列を指します。 **SQLFetchScroll** 配列には、行セット内の行と同じ数の要素があります。 アプリケーションは、SQLUSMALLINTs の配列を割り当て、このフィールドを配列を指す設定する必要があります。 既定では、フィールドは null ポインターに設定されます。 ドライバーは、SQL_DESC_ARRAY_STATUS_PTRフィールドが null ポインターに設定されていない限り、配列を設定します。  
  
> [!CAUTION]  
>  アプリケーションが IRD のSQL_DESC_ARRAY_STATUS_PTR フィールドで指す行の状態配列の要素を設定する場合、ドライバーの動作は定義されません。  
  
 この配列は、最初は**SQL バルクオペレーション、SQLFetch、SQL****フェッチスクロール**、または**SQLSetPos**の呼び出しによって設定されます。 **SQLFetch** 呼び出しがSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さなかった場合、このフィールドが指す配列の内容は未定義です。 配列内の要素には、次の値を含めることができます。  
  
-   SQL_ROW_SUCCESS: 行は正常にフェッチされ、最後にフェッチされてから変更されていません。  
  
-   SQL_ROW_SUCCESS_WITH_INFO: 行は正常にフェッチされ、最後にフェッチされてから変更されていません。 ただし、行に関する警告が返されました。  
  
-   SQL_ROW_ERROR: 行のフェッチ中にエラーが発生しました。  
  
-   SQL_ROW_UPDATED: 行は正常にフェッチされ、最後にフェッチされてから更新されました。 行が再びフェッチされる場合、そのステータスはSQL_ROW_SUCCESS。  
  
-   SQL_ROW_DELETED: 最後にフェッチされてから行が削除されました。  
  
-   SQL_ROW_ADDED: 行は**SQLBulk オペレーション**によって挿入されました。 行が再びフェッチされる場合、そのステータスはSQL_ROW_SUCCESS。  
  
-   SQL_ROW_NOROW: 行セットが結果セットの末尾と重なり合っており、行ステータス配列のこの要素に対応する行は返されませんでした。  
  
 IRD のこのフィールドは、SQL_ATTR_ROW_STATUS_PTR属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
 IRD のSQL_DESC_ARRAY_STATUS_PTRフィールドは、SQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOが返された後にのみ有効です。 戻りコードがこれらのうちの 1 つでない場合、SQL_DESC_ROWS_PROCESSED_PTRが指す位置は未定義です。  
  
 IPD では、このヘッダー フィールドは **、SQLExecute**または**SQLExecDirect**の呼び出し後に、各パラメーター値のセットの状態情報を含むパラメーターの状態配列を指します。 **SQLExecute**または**SQLExecDirect**の呼び出しがSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さなかった場合、このフィールドが指す配列の内容は未定義です。 アプリケーションは、SQLUSMALLINTs の配列を割り当て、このフィールドを配列を指す設定する必要があります。 ドライバーは、SQL_DESC_ARRAY_STATUS_PTRフィールドが null ポインターに設定されていない限り、配列を設定します。 配列内の要素には、次の値を含めることができます。  
  
-   SQL_PARAM_SUCCESS: SQL ステートメントは、この一連のパラメーターに対して正常に実行されました。  
  
-   SQL_PARAM_SUCCESS_WITH_INFO: SQL ステートメントは、この一連のパラメーターに対して正常に実行されました。ただし、警告情報は、診断データ構造で使用できます。  
  
-   SQL_PARAM_ERROR: この一連のパラメーターの処理中にエラーが発生しました。 診断データ構造には、追加のエラー情報が含まれます。  
  
-   SQL_PARAM_UNUSED: このパラメーター・セットは、以前のパラメーター・セットによって、さらに処理を中止するエラーが発生したか、または、SQL_PARAM_IGNOREが、APD の SQL_DESC_ARRAY_STATUS_PTR フィールドで指定された配列内のパラメーター・セットに設定されたため、使用されていませんでした。  
  
-   SQL_PARAM_DIAG_UNAVAILABLE: 診断情報は使用できません。 たとえば、ドライバーがパラメーターの配列をモノリシック単位として扱い、このレベルのエラー情報を生成しない場合などがこれに当てはまりません。  
  
 IPD のこのフィールドは、SQL_ATTR_PARAM_STATUS_PTR属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
 ARD では、このヘッダー フィールドは **、SQLSetPos**操作でこの行を無視するかどうかを示すためにアプリケーションによって設定できる値の行操作配列を指します。 配列内の要素には、次の値を含めることができます。  
  
-   SQL_ROW_PROCEED: 行は**SQLSetPos**を使用して一括操作に含まれます。 (この設定では、行に対して操作が行われるという保証はありません。 行のステータスが IRD 行の状態配列にSQL_ROW_ERROR場合、ドライバーは、行の操作を実行できない可能性があります。  
  
-   SQL_ROW_IGNORE: この行は **、 SQLSetPos**を使用して一括操作から除外されます。  
  
 配列の要素が設定されていない場合、すべての行が一括操作に含まれます。 ARD の SQL_DESC_ARRAY_STATUS_PTR フィールドの値が null ポインターの場合、すべての行が一括操作に含まれます。この解釈は、ポインターが有効な配列を指し示し、配列のすべての要素がSQL_ROW_PROCEEDされた場合と同じです。 配列内の要素がSQL_ROW_IGNOREに設定されている場合、無視される行の行ステータス配列の値は変更されません。  
  
 ARD のこのフィールドは、SQL_ATTR_ROW_OPERATION_PTR属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
 APD では、このヘッダー フィールドは **、SQLExecute**または**SQLExecDirect**が呼び出されたときに、このパラメーターのセットを無視するかどうかを示すためにアプリケーションによって設定できる値のパラメーター操作配列を指します。 配列内の要素には、次の値を含めることができます。  
  
-   SQL_PARAM_PROCEED: パラメーターのセットは **、SQL 実行**または**SQLExecDirect**呼び出しに含まれています。  
  
-   SQL_PARAM_IGNORE: パラメーターのセットは **、SQL 実行**または**SQLExecDirect**呼び出しから除外されます。  
  
 配列の要素が設定されていない場合は、配列内のすべてのパラメーター セットが**SQLExecute**または**SQLExecDirect**呼び出しで使用されます。 APD のSQL_DESC_ARRAY_STATUS_PTR フィールドの値が null ポインターの場合は、すべてのパラメーター セットが使用されます。この解釈は、ポインタが有効な配列を指し示し、配列のすべての要素がSQL_PARAM_PROCEEDされた場合と同じです。  
  
 APD のこのフィールドは、SQL_ATTR_PARAM_OPERATION_PTR属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
 **SQL_DESC_BIND_OFFSET_PTR [アプリケーション記述子]**  
 この SQLLEN * ヘッダー フィールドは、バインド オフセットを指します。 既定では、null ポインターに設定されます。 このフィールドが null ポインターでない場合、ドライバーはポインターを逆参照し、フェッチ時に記述子レコード (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTR) に null 以外の値を持つ各遅延フィールドに逆参照値を追加し、バインド時に新しいポインター値を使用します。  
  
 バインディング オフセットは、常にSQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、およびSQL_DESC_OCTET_LENGTH_PTRフィールドの値に直接追加されます。 オフセットが別の値に変更された場合でも、新しい値は各記述子フィールドの値に直接追加されます。 新しいオフセットは、フィールド値にそれ以前のオフセットを加えた値には追加されません。  
  
 このフィールドは *、遅延フィールド*: 設定された時点では使用されませんが、データ バッファーのアドレスを決定する必要がある場合は、ドライバーによって後で使用されます。  
  
 ARD のこのフィールドは、SQL_ATTR_ROW_BIND_OFFSET_PTR属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。 ARD のこのフィールドは、SQL_ATTR_PARAM_BIND_OFFSET_PTR属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
 詳細については、 [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)および[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)の行方向バインディングの説明を参照してください。  
  
 **SQL_DESC_BIND_TYPE [アプリケーション記述子]**  
 この SQLUINTEGER ヘッダー フィールドは、列またはパラメーターのバインドに使用されるバインディングの方向を設定します。  
  
 ARD では、このフィールドは、関連付けられたステートメント ハンドルで**SQLFetchScroll**または**SQLFetch**が呼び出されたときに、バインディングの方向を指定します。  
  
 列に対する列方向のバインドを選択するには、このフィールドは SQL_BIND_BY_COLUMN (デフォルト) に設定されます。  
  
 ARD のこのフィールドは、 SQL_ATTR_ROW_BIND_TYPE*属性*を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
 APK では、このフィールドは、動的パラメータに使用するバインディングの方向を指定します。  
  
 パラメーターの列方向のバインドを選択するには、このフィールドは SQL_BIND_BY_COLUMN (デフォルト) に設定されます。  
  
 APD のこのフィールドは、 SQL_ATTR_PARAM_BIND_TYPE*属性*を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
 **SQL_DESC_COUNT [すべて]**  
 この SQLSMALLINT ヘッダー・フィールドは、データを含む最高番号のレコードの 1 から始まる索引を指定します。 ドライバーは、記述子のデータ構造を設定するときに、重要なレコードの数を示すSQL_DESC_COUNTフィールドも設定する必要があります。 アプリケーションがこのデータ構造のインスタンスを割り当てる場合、予約する領域の数を指定する必要はありません。 アプリケーションがレコードの内容を指定すると、ドライバーは、記述子ハンドルが適切なサイズのデータ構造を参照することを確認するために必要なアクションを実行します。  
  
 SQL_DESC_COUNTは、バインドされているすべてのデータ列 (フィールドが ARD 内にある場合) や、バインドされているすべてのパラメーター (フィールドが APD にある場合) のカウントではなく、番号が最も大きいレコードの数です。 番号が最も大きい列またはパラメーターがバインドされていない場合、SQL_DESC_COUNTは、次に番号が付けられた次の列またはパラメーターの番号に変更されます。 列または最も番号の大きい列の数より小さい数のパラメーターがバインドされていない場合 (*引数 TargetValuePtr*を NULL ポインターに設定した**SQLBindCol**を呼び出すか、引数*ParameterValuePtr*を null ポインターに設定した**SQLBindParameter**を呼び出しても)、SQL_DESC_COUNTは変更されません。 追加の列またはパラメーターが、データを含む最大のレコードよりも大きい番号でバインドされている場合、ドライバーは自動的にSQL_DESC_COUNT フィールドの値を増加します。 SQL_UNBINDオプションを指定して**SQLFreeStmt**を呼び出してすべての列のバインドが解除された場合、ARD および IRD のSQL_DESC_COUNTフィールドは 0 に設定されます。 SQL_RESET_PARAMSオプションを指定して**SQLFreeStmt**が呼び出された場合、APD および IPD のSQL_DESC_COUNTフィールドは 0 に設定されます。  
  
 SQL_DESC_COUNTの値は、 **SQLSetDescField**を呼び出すことによって、アプリケーションによって明示的に設定できます。 SQL_DESC_COUNTの値が明示的に減少した場合、SQL_DESC_COUNTの新しい値より大きい数値を持つすべてのレコードが事実上削除されます。 SQL_DESC_COUNTの値が明示的に 0 に設定され、フィールドが ARD 内にある場合、バインドされたブックマーク列を除くすべてのデータ バッファーが解放されます。  
  
 ARD のこのフィールドのレコード数には、連結ブックマーク列は含まれません。 ブックマーク列のバインドを解除する唯一の方法は、SQL_DESC_DATA_PTRフィールドを null ポインターに設定することです。  
  
 **SQL_DESC_ROWS_PROCESSED_PTR [実装記述子]**  
 IRD\*では、SQLULEN ヘッダー フィールドは、SQLFetch または**SQLFetchScroll**の呼び**SQLFetch**出し後にフェッチされた行数、または**SQLBulkOperations**または**SQLSetPos**の呼び出しによって実行される一括操作で影響を受ける行数を含むバッファーを指します。  
  
 IPD では、この SQLUINTEGER * ヘッダー フィールドは、エラー セットを含む、処理されたパラメーターのセットの数を含むバッファーを指します。 null ポインターの場合は、数値は返されません。  
  
 SQL_DESC_ROWS_PROCESSED_PTRは **、SQLFetch**または**SQLFetchScroll** (IRD フィールドの場合) または**SQL 実行、SQLExecDirect**、**SQLExecDirect**または**SQLParamData** (IPD フィールドの場合) の呼び出し後に、SQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOが返された後にのみ有効です。 このフィールドが指すバッファを埋める呼び出しがSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さない場合、バッファの内容は未定義です。SQL_NO_DATAを返す場合、バッファ内の値は 0 に設定されます。  
  
 ARD のこのフィールドは、SQL_ATTR_ROWS_FETCHED_PTR属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。 APD のこのフィールドは、SQL_ATTR_PARAMS_PROCESSED_PTR属性を指定して**SQLSetStmtAttr**を呼び出すことによっても設定できます。  
  
 このフィールドが指すバッファは、アプリケーションによって割り当てられます。 これは、ドライバーによって設定される遅延出力バッファーです。 既定では、null ポインターに設定されます。  
  
## <a name="record-fields"></a>レコード フィールド  
 各記述子には、記述子のタイプに応じて、列データまたは動的パラメーターを定義するフィールドから構成される 1 つ以上のレコードが含まれます。 各レコードは、単一の列またはパラメーターの完全な定義です。  
  
 **SQL_DESC_AUTO_UNIQUE_VALUE [IRDs]**  
 この読み取り専用 SQLINTEGER レコード・フィールドには SQL_FALSE、列が自動インクリメント列の場合はSQL_TRUEが入ります。 このフィールドは読み取り専用ですが、基になる自動インクリメント列は必ずしも読み取り専用ではありません。  
  
 **SQL_DESC_BASE_COLUMN_NAME [IRD]**  
 この読み取り専用 SQLCHAR * レコード・フィールドには、結果セット列の基本列名が入っています。 基本列名が存在しない場合 (式である列の場合のように)、この変数には空の文字列が含まれます。  
  
 **SQL_DESC_BASE_TABLE_NAME [IRDs]**  
 この読み取り専用 SQLCHAR * レコード・フィールドには、結果セット列の基本表名が入っています。 ベース テーブル名を定義できない場合、または適用できない場合、この変数には空の文字列が含まれます。  
  
 **SQL_DESC_CASE_SENSITIVE [実装記述子]**  
 この読み取り専用 SQLINTEGER レコード・フィールドには、列またはパラメーターが照合順序および比較の場合に大文字と小文字を区別する場合、または列が照合順序および比較の大文字と小文字を区別しない場合、または非文字列の場合にSQL_FALSE場合に、SQL_TRUEが含まれます。  
  
 **SQL_DESC_CATALOG_NAME [IRD]**  
 この読み取り専用 SQLCHAR * レコード・フィールドには、列を含む基本表のカタログが入っています。 列が式の場合、または列がビューの一部である場合、戻り値はドライバーに依存します。 データ ソースがカタログをサポートしていない場合、またはカタログを判別できない場合、この変数には空の文字列が含まれます。  
  
 **SQL_DESC_CONCISE_TYPE [すべて]**  
 この SQLSMALLINT ヘッダー・フィールドは、日時および間隔のデータ・タイプを含むすべてのデータ・タイプに対して、簡潔なデータ・タイプを指定します。  
  
 SQL_DESC_CONCISE_TYPE、SQL_DESC_TYPE、およびSQL_DESC_DATETIME_INTERVAL_CODEフィールドの値は相互に依存しています。 一方のフィールドが設定されるたびに、もう一方も設定する必要があります。 SQL_DESC_CONCISE_TYPEは **、SQLBindCol**または**SQLBindParameter**、または**SQLSetDescField**への呼び出しによって設定できます。 SQL_DESC_TYPEは、 **SQLSetDesc フィールド**または**SQLSetDescRec**の呼び出しによって設定できます。  
  
 SQL_DESC_CONCISE_TYPE間隔または日時以外のデータ型に設定されている場合、SQL_DESC_TYPEフィールドは同じ値に設定され、SQL_DESC_DATETIME_INTERVAL_CODEフィールドは 0 に設定されます。  
  
 SQL_DESC_CONCISE_TYPEが日時または間隔のデータ型を簡潔に設定すると、SQL_DESC_TYPEフィールドは対応する詳細タイプ (SQL_DATETIME または SQL_INTERVAL) に設定され、SQL_DESC_DATETIME_INTERVAL_CODE フィールドは適切なサブコードに設定されます。  
  
 **SQL_DESC_DATA_PTR [アプリケーション記述子と IPD]**  
 この SQLPOINTER レコード・フィールドは、パラメーター値 (APK の場合) または列値 (ARD の場合) を含む変数を指します。 このフィールドは *、"遅延フィールド*" です。 設定された時点では使用されませんが、後でデータを取得するためにドライバーによって使用されます。  
  
 **SQLBindCol**の呼び出しで *、引数 TargetValuePtr*が null ポインター、SQL_DESC_DATA_PTR または、SQLSetDescField または**SQLSetDescRec**への呼び**SQLSetDescField**出しによって設定されている場合、ARD のSQL_DESC_DATA_PTR フィールドによって指定された列はバインドされません。 SQL_DESC_DATA_PTR フィールドが null ポインターに設定されている場合、その他のフィールドは影響を受けません。  
  
 このフィールドが指すバッファーを埋める**SQLFetch**または**SQLFetchScroll**の呼び出しがSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さなかった場合、バッファーの内容は未定義です。  
  
 APD、ARD、または IPD のSQL_DESC_DATA_PTR フィールドが設定されている場合、ドライバーは、SQL_DESC_TYPE フィールドの値に有効な ODBC C データ型またはドライバー固有のデータ型のいずれかが含まれていること、およびデータ型に影響を与える他のすべてのフィールドが一貫していることを確認します。 整合性チェックのプロンプトは、IPD のSQL_DESC_DATA_PTRフィールドの唯一の使用です。 具体的には、アプリケーションが IPD のSQL_DESC_DATA_PTRフィールドを設定し、後でこのフィールドに**SQLGetDescField**を呼び出す場合、必ずしも設定した値が返されるとは限りません。 詳細については、 [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)の「整合性チェック」を参照してください。  
  
 **SQL_DESC_DATETIME_INTERVAL_CODE [すべて]**  
 この SQLSMALLINT レコード・フィールドには、SQL_DESC_TYPEフィールドがSQL_DATETIMEまたはSQL_INTERVALの場合に、特定の日時または間隔のデータ・タイプのサブコードが含まれます。 これは、SQL と C の両方のデータ型に当てはまります。 コードは、"TYPE" または "C_TYPE" (日付時型の場合) に置き換えた "CODE" を持つデータ型名、または "INTERVAL" または "C_INTERVAL" (間隔型の場合) に置き換えた "CODE" で構成されます。  
  
 アプリケーション記述子のSQL_DESC_TYPEとSQL_DESC_CONCISE_TYPEが SQL_C_DEFAULT に設定され、その記述子がステートメント・ハンドルに関連付けられていない場合、SQL_DESC_DATETIME_INTERVAL_CODEの内容は未定義です。  
  
 このフィールドは、次の表に示す日時データ型に設定できます。  
  
|日時型|DATETIME_INTERVAL_CODE|  
|--------------------|------------------------------|  
|SQL_TYPE_DATE/SQL_C_TYPE_DATE|SQL_CODE_DATE|  
|SQL_TYPE_TIME/SQL_C_TYPE_TIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP/SQL_C_TYPE_TIMESTAMP|SQL_CODE_TIMESTAMP|  
  
 このフィールドは、次の表に示す間隔データ型に対して設定できます。  
  
|[間隔の種類]|DATETIME_INTERVAL_CODE|  
|-------------------|------------------------------|  
|SQL_INTERVAL_DAY/SQL_C_INTERVAL_DAY|SQL_CODE_DAY|  
|SQL_INTERVAL_DAY_TO_HOUR/SQL_C_INTERVAL_DAY_TO_HOUR|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE/SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND/SQL_C_INTERVAL_DAY_TO_SECOND|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR/SQL_C_INTERVAL_HOUR|SQL_CODE_HOUR|  
|SQL_INTERVAL_HOUR_TO_MINUTE/SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND/SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE/SQL_C_INTERVAL_MINUTE|SQL_CODE_MINUTE|  
|SQL_INTERVAL_MINUTE_TO_SECOND/SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_CODE_MINUTE_TO_SECOND|  
|SQL_INTERVAL_MONTH/SQL_C_INTERVAL_MONTH|SQL_CODE_MONTH|  
|SQL_INTERVAL_SECOND/SQL_C_INTERVAL_SECOND|SQL_CODE_SECOND|  
|SQL_INTERVAL_YEAR/SQL_C_INTERVAL_YEAR|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH/SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_CODE_YEAR_TO_MONTH|  
  
 データの間隔とこのフィールドの詳細については、「[データ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)」を参照してください。  
  
 **SQL_DESC_DATETIME_INTERVAL_PRECISION [すべて]**  
 この SQLINTEGER レコード・フィールドには、SQL_DESC_TYPE・フィールドがSQL_INTERVALの場合に、先行する精度の間隔が入ります。 SQL_DESC_DATETIME_INTERVAL_CODEフィールドが間隔データ型に設定されている場合、このフィールドはデフォルトの間隔先行精度に設定されます。  
  
 **SQL_DESC_DISPLAY_SIZE [IRDs]**  
 この読み取り専用の SQLINTEGER レコード・フィールドには、列からのデータを表示するために必要な最大文字数が入っています。  
  
 **SQL_DESC_FIXED_PREC_SCALE [実装記述子]**  
 この読み取り専用の SQLSMALLINT レコード・フィールドは、列が正確な数値列であり、固定精度とゼロ以外の位取り値を持つ場合はSQL_TRUEに設定され、列が固定精度と位取り値を持つ正確な数値列でない場合はSQL_FALSEします。  
  
 **SQL_DESC_INDICATOR_PTR [アプリケーション記述子]**  
 ARD では、この SQLLEN * レコード・フィールドは標識変数を指します。 列の値が NULL の場合、この変数にはSQL_NULL_DATAが含まれます。 APK の場合、標識変数は null 動的引数を指定するためにSQL_NULL_DATAに設定されます。 それ以外の場合、変数はゼロになります (SQL_DESC_INDICATOR_PTRとSQL_DESC_OCTET_LENGTH_PTRの値が同じポインターでない限り)。  
  
 ARD のSQL_DESC_INDICATOR_PTR フィールドが null ポインターの場合、ドライバーは、列が NULL かどうかに関する情報を返すことを防ぎます。 列が NULL で、SQL_DESC_INDICATOR_PTRが null ポインターである場合、SQLFetch または**SQLFetchScroll**の呼び出し後にドライバーがバッファーにデータを設定しようとすると **、SQLSTATE** 22002 (インジケーター変数が必要ですが、指定されていない) が返されます。 SQLFetch または**SQLFetchScroll**の呼び出しがSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さなかった場合、バッファーの内容は未定義です。 **SQLFetchScroll**  
  
 SQL_DESC_INDICATOR_PTR フィールドは、SQL_DESC_OCTET_LENGTH_PTRが指すフィールドが設定されているかどうかを決定します。 列のデータ値が NULL の場合、ドライバーはインジケーター変数をSQL_NULL_DATAに設定します。 SQL_DESC_OCTET_LENGTH_PTRが指すフィールドは設定されません。 フェッチ中に NULL 値が検出されない場合、SQL_DESC_INDICATOR_PTR が指すバッファーはゼロに設定され、SQL_DESC_OCTET_LENGTH_PTRが指すバッファーはデータの長さに設定されます。  
  
 APD のSQL_DESC_INDICATOR_PTR フィールドが NULL ポインターの場合、アプリケーションはこの記述子レコードを使用して NULL 引数を指定することはできません。  
  
 このフィールドは *、遅延フィールド*: 設定された時点では使用されませんが、後でドライバーが NULL 値の許容を示したり (ARD の場合)、または NULL 許容を決定したりするために使用されます (APK の場合)。  
  
 **SQL_DESC_LABEL [IRD]**  
 この読み取り専用の SQLCHAR * レコード・フィールドには、列ラベルまたはタイトルが含まれています。 列にラベルがない場合、この変数には列名が含まれます。 列に名前が付かず、ラベルが付いていない場合、この変数には空の文字列が含まれます。  
  
 **SQL_DESC_LENGTH [すべて]**  
 この SQLULEN レコード・フィールドは、文字ストリングの最大長または実際の長さ (バイト単位のバイナリー・データ・タイプ) です。 これは、固定長データ・タイプの最大長、または可変長データ・タイプの実際の長さです。 その値は、文字ストリングを終了する NULL 終了文字を常に除外します。 型がSQL_TYPE_DATE、SQL_TYPE_TIME、SQL_TYPE_TIMESTAMP、または SQL 間隔データ型のいずれかの値の場合、このフィールドには、日時または間隔の値の文字ストリング表現の長さが文字数で示されます。  
  
 このフィールドの値は、ODBC 2 *.x*で定義されている "length" の値とは異なる場合があります。 詳細については、「[付録 D : データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」を参照してください。  
  
 **SQL_DESC_LITERAL_PREFIX [IRD]**  
 この読み取り専用の SQLCHAR * レコード フィールドには、ドライバーがこのデータ型のリテラルのプレフィックスとして認識する文字が含まれています。 この変数には、リテラルプレフィックスが適用されないデータ型の空の文字列が含まれています。  
  
 **SQL_DESC_LITERAL_SUFFIX [IRDs]**  
 この読み取り専用の SQLCHAR * レコード フィールドには、ドライバーがこのデータ型のリテラルのサフィックスとして認識する文字が含まれています。 この変数には、リテラルサフィックスが適用されないデータ型の空の文字列が含まれています。  
  
 **SQL_DESC_LOCAL_TYPE_NAME [実装記述子]**  
 この読み取り専用 SQLCHAR * レコード フィールドには、データ型の通常名とは異なるデータ型のローカライズされた (ネイティブ言語) 名が含まれています。 ローカライズされた名前がない場合は、空の文字列が返されます。 このフィールドは表示のみを目的とします。  
  
 **SQL_DESC_NAME [実装記述子]**  
 行記述子のこの SQLCHAR * レコード・フィールドには、列別名 (該当する場合) が含まれます。 列の別名が適用されない場合は、列名が返されます。 いずれの場合も、ドライバーは、SQL_DESC_NAME フィールドを設定するときにSQL_NAMEDにSQL_DESC_UNNAMEDフィールドを設定します。 列名または列のエイリアスがない場合、ドライバーはSQL_DESC_NAME フィールドに空の文字列を返し、SQL_DESC_UNNAMEDフィールドをSQL_UNNAMEDに設定します。  
  
 アプリケーションは、IPD のSQL_DESC_NAMEフィールドをパラメータ名またはエイリアスに設定して、ストアド プロシージャのパラメータを名前で指定できます。 (詳細については、「[名前によるパラメーターのバインド (名前付きパラメーター)」](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)を参照してください。IRD のSQL_DESC_NAME フィールドは読み取り専用フィールドです。アプリケーションが設定を試みた場合、SQLSTATE HY091 (無効な記述子フィールド ID) が戻されます。  
  
 IPD では、ドライバが名前付きパラメータをサポートしていない場合、このフィールドは未定義です。 ドライバーは、名前付きパラメーターをサポートし、パラメーターを記述する場合、パラメーター名は、このフィールドに返されます。  
  
 **SQL_DESC_NULLABLE [実装記述子]**  
 IID では、この読み取り専用の SQLSMALLINT レコード・フィールドは、列に NULL 値が含まれる可能性がある場合、列に NULL 値がない場合 SQL_NO_NULLS、または列が NULL 値を受け入れるかどうかが不明な場合はSQL_NULLABLE_UNKNOWN場合にSQL_NULLABLEされます。 このフィールドは、基本列ではなく、結果セット列に関係します。  
  
 IPD では、動的パラメーターは常に null 可能であり、アプリケーションで設定できないため、このフィールドは常に SQL_NULLABLE に設定されます。  
  
 **SQL_DESC_NUM_PREC_RADIX [すべて]**  
 SQL_DESC_TYPE フィールドのデータ型が概数値データ型である場合 SQL_DESC_PRECISION、この SQLINTEGER フィールドには 2 の値が含まれます。 SQL_DESC_PRECISION フィールドには 10 進数の桁数が含まれるので、SQL_DESC_TYPE フィールドのデータ型が完全な数値データ型の場合、このフィールドには 10 の値が含まれます。 このフィールドは、数値以外のすべてのデータ型に対して 0 に設定されます。  
  
 **SQL_DESC_OCTET_LENGTH [すべて]**  
 この SQLLEN レコード・フィールドには、文字ストリングまたはバイナリー・データ・タイプの長さ (バイト単位) が入っています。 固定長の文字型またはバイナリ型の場合、これは実際のバイト長です。 可変長の文字型またはバイナリ型の場合、これはバイト単位の最大長です。 この値は、実装記述子の NULL 終了文字用のスペースを常に除外し、アプリケーション記述子の NULL 終了文字用のスペースを常に含みます。 アプリケーション データの場合、このフィールドにはバッファーのサイズが含まれます。 APD の場合、このフィールドは出力パラメーターまたは入出力パラメーターに対してのみ定義されます。  
  
 **SQL_DESC_OCTET_LENGTH_PTR [アプリケーション記述子]**  
 この SQLLEN * レコード・フィールドは、動的引数 (パラメーター記述子の場合) またはバインドされた列値 (行記述子の場合) の合計長 (バイト単位) を含む変数を指します。  
  
 APD の場合、この値は文字列とバイナリを除くすべての引数で無視されます。このフィールドがSQL_NTSを指している場合、動的引数は NULL で終わる必要があります。 バインドされたパラメーターが実行時データ パラメーターであることを示すために、アプリケーションは、APD の適切なレコードにこのフィールドを変数 SQL_LEN_DATA_AT_EXEC SQL_DATA_AT_EXECに設定します。 このようなフィールドが複数ある場合、SQL_DESC_DATA_PTRは、要求されているパラメーターをアプリケーションが判別できるように、パラメーターを一意に識別する値に設定できます。  
  
 ARD のOCTET_LENGTH_PTR フィールドが null ポインターの場合、ドライバーは列の長さの情報を返しません。 APD のSQL_DESC_OCTET_LENGTH_PTR フィールドが null ポインターの場合、ドライバーは文字列とバイナリ値が null で終了すると見なします。 (バイナリ値は NULL で終わるべきではありませんが、切り捨てを避けるために長さを指定する必要があります)。  
  
 このフィールドが指すバッファーを埋める**SQLFetch**または**SQLFetchScroll**の呼び出しがSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さなかった場合、バッファーの内容は未定義です。 このフィールドは *、"遅延フィールド*" です。 設定時には使用されませんが、後でデータのオクテット長を決定または示すために、ドライバーによって使用されます。  
  
 **SQL_DESC_PARAMETER_TYPE [IPD]**  
 この SQLSMALLINT レコード・フィールドは、入力パラメーター、入力/出力パラメーターのSQL_PARAM_INPUT_OUTPUT、出力パラメーターのSQL_PARAM_OUTPUT、入出力ストリーム・パラメーターのSQL_PARAM_INPUT_OUTPUT_STREAM、または出力ストリーム・パラメーターの SQL_PARAM_OUTPUT_STREAMの場合は、SQL_PARAM_INPUTに設定されます。 既定では、SQL_PARAM_INPUTに設定されています。  
  
 IPD の場合、IPD がドライバーによって自動的に設定されない場合は、デフォルトでフィールドがSQL_PARAM_INPUTに設定されます (SQL_ATTR_ENABLE_AUTO_IPDステートメント属性がSQL_FALSE)。 アプリケーションは、入力パラメーターではないパラメーターに対して IPD でこのフィールドを設定する必要があります。  
  
 **SQL_DESC_PRECISION [すべて]**  
 この SQLSMALLINT レコード・フィールドには、正確な数値タイプの桁数、概算数値タイプの mantissa (2 進精度) のビット数、または SQL_TYPE_TIME、SQL_TYPE_TIMESTAMP、またはSQL_INTERVAL_SECONDのデータ・タイプの小数秒構成の桁数が入っています。 このフィールドは、他のすべてのデータ型に対して定義されていません。  
  
 このフィールドの値は、ODBC 2 *.x*で定義されている "精度" の値と異なる場合があります。 詳細については、「[付録 D : データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」を参照してください。  
  
 **SQL_DESC_ROWVER [実装記述子]**  
 この SQLSMALLINT レコード フィールドは、行が更新されたときに、列が DBMS によって自動的に変更されるかどうかを示します (たとえば、SQL Server の "timestamp" 型の列など)。 このレコード フィールドの値は、列が行のバージョン管理列の場合はSQL_TRUEに設定され、それ以外の場合はSQL_FALSEに設定されます。 この列属性は、列が自動的に更新されるかどうかを判断するSQL_ROWVERの識別子の型を使用して**SQLSpecialColumns**を呼び出すのと似ています。  
  
 **SQL_DESC_SCALE [すべて]**  
 この SQLSMALLINT レコード・フィールドには、10 進数および数値データ・タイプに対して定義された位取りが含まれています。 このフィールドは、他のすべてのデータ型に対して定義されていません。  
  
 このフィールドの値は、ODBC 2 *.x*で定義されている "scale" の値とは異なる場合があります。 詳細については、「[付録 D : データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」を参照してください。  
  
 **SQL_DESC_SCHEMA_NAME [IRD]**  
 この読み取り専用 SQLCHAR * レコード・フィールドには、列を含む基本表のスキーマ名が入っています。 列が式の場合、または列がビューの一部である場合、戻り値はドライバーに依存します。 データ ソースがスキーマをサポートしていない場合、またはスキーマ名を決定できない場合、この変数には空の文字列が含まれます。  
  
 **SQL_DESC_SEARCHABLE [IRD]**  
 この読み取り専用の SQLSMALLINT レコード・フィールドは、以下のいずれかの値に設定されます。  
  
-   列を**WHERE**句で使用できない場合はSQL_PRED_NONEします。 (これは、ODBC 2 *.x*のSQL_UNSEARCHABLE値と同じです。  
  
-   SQL_PRED_CHAR列を**WHERE**句で使用できても **、LIKE**述語でのみ使用できる場合。 (これは ODBC 2 *.x*のSQL_LIKE_ONLY値と同じです。  
  
-   列を**LIKE**以外のすべての比較演算子を使用して**WHERE**句で使用できる場合は、SQL_PRED_BASIC。 (これは ODBC 2 *.x*のSQL_EXCEPT_LIKE値と同じです。  
  
-   SQL_PRED_SEARCHABLE列を**WHERE**句で使用できる場合は、任意の比較演算子を使用します。  
  
 **SQL_DESC_TABLE_NAME [IRDs]**  
 この読み取り専用 SQLCHAR * レコード・フィールドには、この列を含む基本表の名前が入っています。 列が式の場合、または列がビューの一部である場合、戻り値はドライバーに依存します。  
  
 **SQL_DESC_TYPE [すべて]**  
 この SQLSMALLINT レコード・フィールドは、日時データ・タイプおよびインターバル・データ・タイプを除くすべてのデータ・タイプに対して、簡潔な SQL または C データ・タイプを指定します。 日時データ型および間隔データ型の場合、このフィールドは、SQL_DATETIMEまたはSQL_INTERVALされる詳細データ型を指定します。  
  
 このフィールドにSQL_DATETIMEまたはSQL_INTERVALが含まれる場合は、SQL_DESC_DATETIME_INTERVAL_CODEフィールドに簡潔な型の適切なサブコードが含まれている必要があります。 datetime データ型の場合、SQL_DESC_TYPEはSQL_DATETIMEを含み、SQL_DESC_DATETIME_INTERVAL_CODE フィールドには特定の日時データ型のサブコードが含まれます。 間隔データ型の場合、SQL_DESC_TYPEがSQL_INTERVALを含み、SQL_DESC_DATETIME_INTERVAL_CODE フィールドに特定の間隔データ型のサブコードが含まれます。  
  
 SQL_DESC_TYPEフィールドとSQL_DESC_CONCISE_TYPEフィールドの値は相互に依存しています。 一方のフィールドが設定されるたびに、もう一方も設定する必要があります。 SQL_DESC_TYPEは、 **SQLSetDesc フィールド**または**SQLSetDescRec**の呼び出しによって設定できます。 SQL_DESC_CONCISE_TYPEは **、SQLBindCol**または**SQLBindParameter**、または**SQLSetDescField**への呼び出しによって設定できます。  
  
 SQL_DESC_TYPE間隔または日時以外のデータ型に設定されている場合、SQL_DESC_CONCISE_TYPEフィールドは同じ値に設定され、SQL_DESC_DATETIME_INTERVAL_CODEフィールドは 0 に設定されます。  
  
 SQL_DESC_TYPEが詳細な日時または間隔のデータ型 (SQL_DATETIME または SQL_INTERVAL) に設定され、SQL_DESC_DATETIME_INTERVAL_CODE フィールドが適切なサブコードに設定されている場合、SQL_DESC_CONCISEの TYPE フィールドは対応する簡潔な型に設定されます。 SQL_DESC_TYPEを簡潔な日時型または間隔型のいずれかに設定しようとすると、SQLSTATE HY021 (一貫性のない記述子情報) が返されます。  
  
 SQL_DESC_TYPE フィールドが**SQLBindCol**、 **SQLBindParameter**、または**SQLSetDescField**の呼び出しによって設定されている場合、次のフィールドは次の既定値に設定されます ( 下の表を参照) します。 同じレコードの残りのフィールドの値は未定義です。  
  
|SQL_DESC_TYPEの値|その他のフィールドは暗黙的に設定される|  
|------------------------------|---------------------------------|  
|SQL_CHAR、SQL_VARCHAR、SQL_C_CHAR、SQL_C_VARCHAR|SQL_DESC_LENGTHは 1 に設定されます。 SQL_DESC_PRECISIONは 0 に設定されます。|  
|SQL_DATETIME|SQL_DESC_DATETIME_INTERVAL_CODEがSQL_CODE_DATEまたはSQL_CODE_TIMEに設定されている場合、SQL_DESC_PRECISIONは 0 に設定されます。 SQL_DESC_TIMESTAMPに設定すると、SQL_DESC_PRECISIONは 6 に設定されます。|  
|SQL_DECIMAL、SQL_NUMERIC、SQL_C_NUMERIC|SQL_DESC_SCALEは 0 に設定されます。 SQL_DESC_PRECISIONは、それぞれのデータ型の実装で定義された精度に設定されます。<br /><br /> SQL_C_NUMERIC値を手動でバインドする方法については[、「SQL to C: 数値](../../../odbc/reference/appendixes/sql-to-c-numeric.md)」を参照してください。|  
|SQL_FLOAT、SQL_C_FLOAT|SQL_DESC_PRECISIONは、SQL_FLOATの実装定義の既定の精度に設定されます。|  
|SQL_INTERVAL|SQL_DESC_DATETIME_INTERVAL_CODE間隔データ・タイプに設定すると、SQL_DESC_DATETIME_INTERVAL_PRECISIONは 2 (デフォルトの間隔先行精度) に設定されます。 間隔に秒の構成要素がある場合、SQL_DESC_PRECISIONは 6 (デフォルトの間隔の秒精度) に設定されます。|  
  
 アプリケーションが**SQLSetDescRec を**呼び出すのではなく、記述子のフィールドを設定するために**SQLSetDescField**を呼び出すとき、アプリケーションは最初にデータ型を宣言する必要があります。 その場合、前の表に示されている他のフィールドは暗黙的に設定されます。 暗黙的に設定された値のいずれかが許容できない場合、アプリケーションは**SQLSetDescField**または**SQLSetDescRec**を呼び出して、許容できない値を明示的に設定できます。  
  
 **SQL_DESC_TYPE_NAME [実装記述子]**  
 この読み取り専用の SQLCHAR * レコード・フィールドには、データ・ソースに依存するタイプ名 (例えば、「CHAR」、「VARCHAR」など) が入っています。 データ型名が不明な場合、この変数には空の文字列が含まれます。  
  
 **SQL_DESC_UNNAMED [実装記述子]**  
 行記述子のこの SQLSMALLINT レコード フィールドは、ドライバーがSQL_DESC_NAME フィールドを設定するときに、SQL_NAMEDまたはSQL_UNNAMEDに設定されます。 SQL_DESC_NAMEフィールドに列のエイリアスが含まれている場合、または列のエイリアスが適用されない場合、ドライバーはSQL_DESC_UNNAMEDフィールドをSQL_NAMEDに設定します。 アプリケーションが IPD のSQL_DESC_NAMEフィールドをパラメーター名または別名に設定すると、ドライバーは IPD のSQL_DESC_UNNAMEDフィールドをSQL_NAMEDに設定します。 列名または列のエイリアスがない場合、ドライバーはSQL_DESC_UNNAMEDフィールドをSQL_UNNAMEDに設定します。  
  
 アプリケーションは、IPD のSQL_DESC_UNNAMEDフィールドをSQL_UNNAMEDに設定できます。 アプリケーションが IPD のSQL_DESC_UNNAMEDフィールドを SQL_NAMED に設定しようとすると、ドライバーは SQLSTATE HY091 (無効な記述子フィールド識別子) を返します。 IRD のSQL_DESC_UNNAMEDフィールドは読み取り専用です。アプリケーションが設定を試みた場合、SQLSTATE HY091 (無効な記述子フィールド ID) が戻されます。  
  
 **SQL_DESC_UNSIGNED [実装記述子]**  
 この読み取り専用の SQLSMALLINT レコード・フィールドは、列タイプが符号なしまたは数値以外の場合はSQL_TRUEに設定され、列タイプが符号付きである場合はSQL_FALSE。  
  
 **SQL_DESC_UPDATABLE [IRDs]**  
 この読み取り専用の SQLSMALLINT レコード・フィールドは、以下のいずれかの値に設定されます。  
  
-   結果セット列が読み取り専用の場合はSQL_ATTR_READ_ONLYします。  
  
-   結果セット列が読み取り/書き込み可能かどうかをSQL_ATTR_WRITEします。  
  
-   結果セット列が更新可能かどうかが不明の場合は、SQL_ATTR_READWRITE_UNKNOWNします。  
  
 SQL_DESC_UPDATABLEは、基本表の列ではなく、結果セット内の列の更新可能性を記述します。 この結果セット列の基になる基本表の列の更新可能性は、このフィールドの値と異なる場合があります。 列が更新可能かどうかは、データ型、ユーザー特権、および結果セット自体の定義に基づいて行うことができます。 列が更新可能かどうかが不明な場合は、SQL_ATTR_READWRITE_UNKNOWN返す必要があります。  
  
## <a name="consistency-checks"></a>整合性チェック  
 アプリケーションが ARD、APD、または IPD のSQL_DESC_DATA_PTRフィールドの値を渡すたびに、ドライバーによって整合性チェックが自動的に実行されます。 いずれかのフィールドが他のフィールドと矛盾している場合 **、SQLSetDescField**は SQLSTATE HY021 (不整合な記述子情報) を返します。 詳細については、 [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)の「整合性チェック」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|列のバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|パラメーターのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|記述子フィールドの取得|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|複数の記述子フィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|複数の記述子フィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)
