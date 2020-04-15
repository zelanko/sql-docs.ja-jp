---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDiagField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagField
helpviewer_keywords:
- SQLGetDiagField function [ODBC]
ms.assetid: 1dbc4398-97a8-4585-bb77-1f7ea75e24c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a26319868a4b94b895da73d39b284f612fe35889
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285432"
---
# <a name="sqlgetdiagfield-function"></a>SQLGetDiagField 関数

**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLGetDiagField は**、エラー、警告、および状態情報を含む (指定されたハンドルに関連付けられている) 診断データ構造体のレコードのフィールドの現在の値を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp

SQLRETURN SQLGetDiagField(  
     SQLSMALLINT     HandleType,  
     SQLHANDLE       Handle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     DiagIdentifier,  
     SQLPOINTER      DiagInfoPtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]診断が必要なハンドルのタイプを記述するハンドル型識別子。 次のいずれかである必要があります。  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN ハンドルは、ドライバー マネージャーとドライバーによってのみ使用されます。 アプリケーションでは、このハンドル型を使用しないでください。 SQL_HANDLE_DBC_INFO_TOKENの詳細については[、「ODBC ドライバーでの接続プール認識の開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)」を参照してください。  
  
 *Handle*  
 [入力]によって示される型の診断データ構造体*のハンドル*。 *HandleType*がSQL_HANDLE_ENV場合 *、Handle*は共有または非共有環境ハンドルのいずれかになります。  
  
 *RecNumber*  
 [入力]アプリケーションが情報を取得する状態レコードを示します。 状態レコードには 1 から番号が付きます。 *DiagIdentifier*引数が診断ヘッダーのいずれかのフィールドを示す場合 *、RecNumber*は無視されます。 それ以外の場合は、0 を超える必要があります。  
  
 *ディアグ識別子*  
 [入力]値を返す診断のフィールドを示します。 詳細については、「コメント」の *「DiagIdentifier*引数」を参照してください。  
  
 *ディアグインフォプター*  
 [出力]診断情報を返すバッファーへのポインター。 データ型は*DiagIdentifier*の値によって異なります。 *DiagInfoPtr*が整数型の場合、一部のドライバーは、バッファーの下位 32 ビットまたは 16 ビットのみを書き込み、高い順序のビットを変更せずに、この関数を呼び出す前に、SQLULEN のバッファーを使用して 0 に初期化する必要があります。  
  
 *DiagInfoPtr*が NULL の場合 *、StringLengthPtr*は *、DiagInfoPtr*が指すバッファーで返すバイトの合計数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]*DiagIdentifier*が ODBC で定義された診断であり、*文字*文字列またはバイナリ バッファを指す場合、この引数は\**DiagInfoPtr*の長さである必要があります。 *DiagIdentifier*が ODBC で定義された\*フィールドで *、整数の場合*は *、バッファー長*は無視されます。 * \*DiagInfoPtr*の値が Unicode 文字列の場合 **(SQLGetDiagFieldW**を呼び出すとき *)、BufferLength*引数は偶数でなければなりません。  
  
 *DiagIdentifier*がドライバー定義フィールドの場合、アプリケーションは *、BufferLength*引数を設定してドライバー マネージャーにフィールドの性質を示します。 *バッファー長*には、次の値を指定できます。  
  
-   *DiagInfoPtr*が文字列へのポインターである場合 *、BufferLength*は文字列またはSQL_NTSの長さを表します。  
  
-   *DiagInfoPtr*がバイナリ バッファへのポインタである場合、アプリケーションは SQL_LEN_BINARY_ATTR(*長さ*) マクロの結果を*BufferLength*に格納します。 この場合は、負の値を*BufferLength*に配置します。  
  
-   *DiagInfoPtr*が文字列またはバイナリ文字列以外の値へのポインターである場合 *、BufferLength*には値がSQL_IS_POINTER。  
  
-   * \*DiagInfoPtr*に固定長データ型が含まれている場合 *、BufferLength*は、必要に応じてSQL_IS_INTEGER、SQL_IS_UINTEGER、SQL_IS_SMALLINT、またはSQL_IS_USMALLINTです。  
  
 *文字列を長くします。*  
 [出力]文字データの場合に\**DiagInfoPtr*に戻すために使用可能な合計バイト数 (NULL 終了文字に必要なバイト数を除く) を戻すバッファーへのポインター。 戻り値のバイト数が*BufferLength*以上の場合\**、DiagInfoPtr*のテキストは *、BufferLength*から NULL 終端文字の長さを引いた値に切り捨てられます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、またはSQL_NO_DATA。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetDiagField**は、それ自体の診断レコードをポストしません。 次の戻り値を使用して、自身の実行結果を報告します。  
  
-   SQL_SUCCESS: 関数が診断情報を正常に返しました。  
  
-   SQL_SUCCESS_WITH_INFO: \* *DiagInfoPtr*が小さすぎて、要求された診断フィールドを保持できませんでした。 したがって、診断フィールドのデータは切り捨てられました。 切り捨てが発生したことを確認するには、アプリケーションは*BufferLength*を使用可能な実際のバイト数と比較する必要*があります。*  
  
-   SQL_INVALID_HANDLE:*ハンドル型*とハンドルで示された*ハンドル*が有効なハンドルではありませんでした。  
  
-   SQL_ERROR: 次のいずれかが発生しました。  
  
    -   *引数が*有効な値の 1 つではありませんでした。  
  
    -   *DiagIdentifier*引数はSQL_DIAG_CURSOR_ROW_COUNT、SQL_DIAG_DYNAMIC_FUNCTION、SQL_DIAG_DYNAMIC_FUNCTION_CODE、またはSQL_DIAG_ROW_COUNTでしたが *、Handle*はステートメント ハンドルではありませんでした。 (ドライバー マネージャーは、この診断を返します。  
  
    -   *RecNumber*引数は負の値または 0 を*DiagIdentifier が*診断レコードからフィールドを示した場合。 ヘッダー フィールドでは *、RecNumber*は無視されます。  
  
    -   要求された値は文字列で *、BufferLength*は 0 未満でした。  
  
    -   非同期通知を使用する場合、ハンドルに対する非同期操作は完了しませんでした。  
  
-   SQL_NO_DATA: *RecNumber*が *、[ハンドル*] で指定されたハンドルに存在する診断レコードの数より多かった。 この関数は、*ハンドル*の診断レコードがない場合は、正の*RecNumber*のSQL_NO_DATAも返します。  
  
## <a name="comments"></a>説明  
 アプリケーションは通常、次の 3 つの目標のいずれかを達成するために**SQLGetDiagField**を呼び出します。  
  
1.  関数呼び出しがSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返した場合 (**または SQLBrowseConnect**関数のSQL_NEED_DATA) に、特定のエラーまたは警告情報を取得します。  
  
2.  挿入、削除、または更新操作が**SQLExecute、SQLExecDirect** **、SQLBulkOperations**、または**SQLSetPos** (SQL_DIAG_ROW_COUNT ヘッダー フィールドから) への呼び出しで実行された場合に影響を受けたデータ ソース内の行数を確認したり、現在のオープン カーソルに存在する行数を確認したりするには (SQL_DIAG_CURSOR_ROW_COUNT ヘッダー フィールドから) 。 **SQLExecute**  
  
3.  **SQLExecDirect**または**SQLExecute**の呼び出しによって実行された関数を確認する (SQL_DIAG_DYNAMIC_FUNCTIONおよびSQL_DIAG_DYNAMIC_FUNCTION_CODE ヘッダー フィールドから)。  
  
 どの ODBC 関数も、呼び出されるたびに 0 個以上の診断レコードをポストできるため、アプリケーションは ODBC 関数呼び出しの後に**SQLGetDiagField**を呼び出すことができます。 一度に保存できる診断レコードの数に制限はありません。 **SQLGetDiagField**は、*ハンドル*引数で指定された診断データ構造体に関連付けられた最も最近の診断情報のみを取得します。 アプリケーションが**SQLGetDiagField または SQLGetDiagRec**以外の ODBC 関数を呼び出すと、同じハンドルを持つ前の呼び出しからの診断情報はすべて失われます。 **SQLGetDiagRec**  
  
 **アプリケーションは、SQLGetDiagField**がSQL_SUCCESSを返す限り *、RecNumber*をインクリメントすることによってすべての診断レコードをスキャンできます。 SQL_DIAG_NUMBERヘッダー フィールドには、ステータス レコードの数が示されます。 **SQLGetDiagField**への呼び出しは、ヘッダーフィールドおよびレコードフィールドに対して非破壊的です。 診断関数以外の関数が中間で呼び出されていない限り、アプリケーションは後で**SQLGetDiagField**を呼び出してレコードからフィールドを取得できます。  
  
 アプリケーションは **、sqlGetDiagField**を呼び出して、SQL_DIAG_CURSOR_ROW_COUNTまたはSQL_DIAG_ROW_COUNTを除き、任意の時点で任意の診断*Handle*フィールドを SQL_ERROR返すことができます。 他の診断フィールドが定義されていない場合 **、SQLGetDiagField**の呼び出しはSQL_SUCCESSを返し (他の診断が検出されない場合)、フィールドに対して未定義の値が返されます。  
  
 詳細については[、「SQLGetDiagRec および SQLGetDiagField の使用」](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)および[「SQLGetDiagRec および SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)の実装」を参照してください。  
  
 非同期に実行されている API 以外の API を呼び出すと、HY010 「関数シーケンスエラー」が生成されます。 ただし、非同期操作が完了する前にエラー レコードを取得することはできません。  
  
## <a name="handletype-argument"></a>ハンドル型引数  
 各ハンドルタイプには、診断情報を関連付けることができます。 *引数 HandleType*はハンドルの種類を*示*します。  
  
 一部のヘッダーフィールドおよびレコード・フィールドは、環境、接続、ステートメント、および記述子ハンドルでは戻すことができません。 フィールドが適用できないハンドルについては、後の「ヘッダー フィールド」と「レコード フィールド」のセクションに示されています。  
  
 *HandleType*がSQL_HANDLE_ENV場合 *、Handle*は共有環境ハンドルまたは非共有環境ハンドルのいずれかになります。  
  
 ドライバー固有のヘッダー診断フィールドは、環境ハンドルに関連付ける必要があります。  
  
 記述子ハンドルに対して定義されている診断ヘッダー・フィールドは、SQL_DIAG_NUMBERされ、SQL_DIAG_RETURNCODEだけです。  
  
## <a name="diagidentifier-argument"></a>識別子の引数  
 この引数は、診断データ構造から必要なフィールドの ID を示します。 *RecNumber*が 1 以上の場合、フィールド内のデータは、関数によって返される診断情報を示します。 *RecNumber*が 0 の場合、フィールドは診断データ構造体のヘッダーに含まれるため、特定の情報ではなく診断情報を返した関数呼び出しに関連するデータが含まれます。  
  
 ドライバーは、診断データ構造体のドライバー固有のヘッダーとレコード フィールドを定義できます。  
  
 ODBC 2 *.x*ドライバーを使用する ODBC 3 *.x*アプリケーションは、SQL_DIAG_CLASS_ORIGIN、SQL_DIAG_CLASS_SUBCLASS_ORIGIN、SQL_DIAG_CONNECTION_NAME、SQL_DIAG_MESSAGE_TEXT、SQL_DIAG_NATIVE、SQL_DIAG_NUMBER、SQL_DIAG_RETURNCODE、SQL_DIAG_SERVER_NAME、またはSQL_DIAG_SQLSTATEの*DiagIdentifier*引数を使用してのみ**SQLGetDiagField**を呼び出すことができる。 その他のすべての診断フィールドは、SQL_ERROR返します。  
  
## <a name="header-fields"></a>ヘッダー フィールド  
 次の表に示すヘッダー フィールドは *、DiagIdentifier*引数に含めることができます。  
  
|ディアグ識別子|の戻り値の型 : |戻り値|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CURSOR_ROW_COUNT|SQLLEN|このフィールドには、カーソル内の行数が含まれます。 このセマンティクスは、各カーソルの種類 (SQL_CA2_CRC_EXACT ビットとSQL_CA2_CRC_APPROXIMATE ビット) で使用できる行数を示す**sqlGetInfo**情報の種類SQL_DYNAMIC_CURSOR_ATTRIBUTES2、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2、SQL_KEYSET_CURSOR_ATTRIBUTES2、およびSQL_STATIC_CURSOR_ATTRIBUTES2によって異なります。<br /><br /> このフィールドの内容は、ステートメント ハンドルに対してのみ定義され **、SQL 実行****、SQLExecDirect**、または**SQLMoreResults**が呼び出された後にのみ定義されます。 ステートメント ハンドル以外の SQL_DIAG_CURSOR_ROW_COUNT の*DiagIdentifier*を指定して**SQLGetDiagField**を呼び出すと、SQL_ERROR返されます。|  
|SQL_DIAG_DYNAMIC_FUNCTION|SQLCHAR *|これは、基になる関数が実行した SQL ステートメントを記述する文字列です。 (特定の値については、このセクションの「動的関数フィールドの値」を参照してください。このフィールドの内容は、ステートメント ハンドルに対してのみ定義され **、SQLExecute** **、SQLExecDirect**、または**SQLMoreResults**を呼び出した後にのみ定義されます。 ステートメント ハンドル以外の SQL_DIAG_DYNAMIC_FUNCTION の*DiagIdentifier*を指定して**SQLGetDiagField**を呼び出すと、SQL_ERROR返されます。 このフィールドの値は **、SQLExecute**または**SQLExecDirect**の呼び出しの前に未定義です。|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|SQLINTEGER|これは、基になる関数によって実行された SQL ステートメントを記述する数値コードです。 (特定の値については、このセクションの後半の「動的関数フィールドの値」を参照してください。このフィールドの内容は、ステートメント ハンドルに対してのみ定義され **、SQLExecute** **、SQLExecDirect**、または**SQLMoreResults**を呼び出した後にのみ定義されます。 ステートメント ハンドル以外の SQL_DIAG_DYNAMIC_FUNCTION_CODEの*DiagIdentifier*を使用して**SQLGetDiagField**を呼び出すと、SQL_ERROR返されます。 このフィールドの値は **、SQLExecute**または**SQLExecDirect**の呼び出しの前に未定義です。|  
|SQL_DIAG_NUMBER|SQLINTEGER|指定されたハンドルで使用可能な状態レコードの数。|  
|SQL_DIAG_RETURNCODE|SQL リターン|関数によって返される戻りコード。 リターン コードの一覧については、「[リターン コード](../../../odbc/reference/develop-app/return-codes-odbc.md)」を参照してください。 ドライバーは、SQL_DIAG_RETURNCODEを実装する必要はありません。常にドライバー マネージャーによって実装されます。 *Handle*でまだ関数が呼び出されていない場合、SQL_DIAG_RETURNCODEのSQL_SUCCESSが返されます。|  
|SQL_DIAG_ROW_COUNT|SQLLEN|挿入、削除、または更新によって実行される行の数は **、SQL 実行****、SQLExecDirect、SQLBulkOperations**、または**SQLBulkOperations****SQLSetPos によって実行されます**。 *これは、カーソル指定*が実行された後にドライバ定義されます。 このフィールドの内容は、ステートメント・ハンドルに対してのみ定義されます。 ステートメント ハンドル以外の SQL_DIAG_ROW_COUNT の*DiagIdentifier*を使用して**SQLGetDiagField**を呼び出すと、SQL_ERROR返されます。 このフィールドのデータは **、SQLRowCount**の*引数*にも返されます。 このフィールドのデータは、すべての非診断関数呼び出し後にリセットされますが **、SQLRowCount**によって返される行数は、ステートメントが準備済みまたは割り当て済み状態に戻るまで同じままです。|  
  
## <a name="record-fields"></a>レコード フィールド  
 次の表に示すレコード フィールドは *、DiagIdentifier*引数に含めることができます。  
  
|ディアグ識別子|の戻り値の型 : |戻り値|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CLASS_ORIGIN|SQLCHAR *|このレコード内の SQLSTATE 値のクラス部分を定義する文書を示すストリング。 その値は、オープングループおよびISO呼び出しレベルインタフェースによって定義されるすべてのSQLSTATEsに対して「ISO 9075」です。 ODBC 固有の SQLSTATE (SQLSTATE クラスが "IM" であるすべてのオブジェクト) の場合、その値は "ODBC 3.0" です。|  
|SQL_DIAG_COLUMN_NUMBER|SQLINTEGER|SQL_DIAG_ROW_NUMBER フィールドが行セットまたはパラメーターのセット内の有効な行番号である場合、このフィールドには、結果セット内の列番号またはパラメーターセットのパラメーター番号を表す値が含まれます。 結果セット列番号は常に 1 から始まります。この状態レコードがブックマーク列に関連する場合、フィールドはゼロにすることができます。 パラメータ番号は 1 から始まります。 ステータス レコードが列番号またはパラメーター番号に関連付けられていない場合は、値がSQL_NO_COLUMN_NUMBER。 ドライバーは、このレコードに関連付けられている列番号またはパラメーター番号を決定できない場合、このフィールドは、SQL_COLUMN_NUMBER_UNKNOWN値を持ちます。<br /><br /> このフィールドの内容は、ステートメント・ハンドルに対してのみ定義されます。|  
|SQL_DIAG_CONNECTION_NAME|SQLCHAR *|診断レコードが関連する接続の名前を示す文字列。 このフィールドはドライバー定義です。 環境ハンドルに関連付けられている診断データ構造体、およびどの接続にも関連しない診断の場合、このフィールドは長さ 0 の文字列です。|  
|SQL_DIAG_MESSAGE_TEXT|SQLCHAR *|エラーまたは警告に関する情報メッセージ。 このフィールドは、[診断メッセージ](../../../odbc/reference/develop-app/diagnostic-messages.md)の説明に従ってフォーマットされます。 診断メッセージ・テキストに最大長はありません。|  
|SQL_DIAG_NATIVE|SQLINTEGER|ドライバー/データ ソース固有のネイティブ エラー コード。 ネイティブ エラー コードがない場合、ドライバーは 0 を返します。|  
|SQL_DIAG_ROW_NUMBER|SQLLEN|このフィールドには、行セットの行番号、またはステータス レコードが関連付けられているパラメーターセット内のパラメーター番号が含まれます。 行番号とパラメータ番号は 1 から始まります。 このステータス レコードが行番号またはパラメータ番号に関連付けられていない場合、このフィールドにはSQL_NO_ROW_NUMBER値が設定されます。 ドライバーは、このレコードに関連付けられている行番号またはパラメーター番号を決定できない場合、このフィールドは、SQL_ROW_NUMBER_UNKNOWN値を持ちます。<br /><br /> このフィールドの内容は、ステートメント・ハンドルに対してのみ定義されます。|  
|SQL_DIAG_SERVER_NAME|SQLCHAR *|診断レコードが関連するサーバー名を示す文字列。 これは、SQL_DATA_SOURCE_NAME オプションを指定して**SQLGetInfo**を呼び出す場合に返される値と同じです。 環境ハンドルに関連付けられている診断データ構造体、およびどのサーバーにも関連しない診断の場合、このフィールドは長さ 0 の文字列です。|  
|SQL_DIAG_SQLSTATE|SQLCHAR *|5 文字の SQLSTATE 診断コード。 詳細については[、SQLSTATE を](../../../odbc/reference/develop-app/sqlstates.md)参照してください。|  
|SQL_DIAG_SUBCLASS_ORIGIN|SQLCHAR *|SQLSTATE コードのサブクラス部分の定義部分を識別する、SQL_DIAG_CLASS_ORIGINと同じ形式および有効な値を持つ文字列。 "ODBC 3.0" が返される ODBC 固有の SQLSTATES には、次のものがあります。<br /><br /> 01S00, 01S01, 01S02, 01S06, 01S07, 07S01, 08S01, 21S01, 21S02, 25S01, 25S02, 42S01, 42S12, 42S21, 42S21, HY095, HY099, HY099, HY099, HY099, HY100, HY101, HY105, HY107, HY109, HY110, HY111, HY111, HY111, HYT00, HYT01, IM001, IM002, IM004, IM005, IM006, IM000, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, IM010, HY1111,HY1111,HY1111,HY101,HY001,IM001,IM001,IM001,IM0010,IM004,IM002,IM004,IM005,IM005, IM010, IM010, IM010, IM010, IM010, IM010,|  
  
## <a name="values-of-the-dynamic-function-fields"></a>動的関数フィールドの値  
 次の表は **、SQLExecute**または**SQLExecDirect**の呼び出しによって実行される SQL ステートメントの種類ごとに適用されるSQL_DIAG_DYNAMIC_FUNCTIONとSQL_DIAG_DYNAMIC_FUNCTION_CODEの値を示しています。 ドライバーは、ドライバー定義の値を追加できます。  
  
|SQL ステートメント<br /><br /> 実行| の値<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION| の値<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION_CODE|  
|--------------------------------|-----------------------------------------------|-----------------------------------------------------|  
|*ドメイン変更ステートメント*|「ドメインの変更」|SQL_DIAG_ALTER_DOMAIN|  
|*表の変更ステートメント*|"テーブルを変更"|SQL_DIAG_ALTER_TABLE|  
|*アサーション定義*|"アサーションの作成"|SQL_DIAG_CREATE_ASSERTION|  
|*文字セット定義*|"文字セットの作成"|SQL_DIAG_CREATE_CHARACTER_SET|  
|*照合順序定義*|"照合順序の作成"|SQL_DIAG_CREATE_COLLATION|  
|*ドメイン定義*|"ドメインの作成"|SQL_DIAG_CREATE_DOMAIN|
|*作成インデックスステートメント*|"インデックスの作成"|SQL_DIAG_CREATE_INDEX|  
|*テーブルの作成-ステートメント*|"テーブルの作成"|SQL_DIAG_CREATE_TABLE|  
|*作成ビュー ステートメント*|"ビューの作成"|SQL_DIAG_CREATE_VIEW|  
|*カーソル仕様*|"カーソルを選択"|SQL_DIAG_SELECT_CURSOR|  
|*ステートメントの配置を削除する*|"動的削除カーソル"|SQL_DIAG_DYNAMIC_DELETE_CURSOR|  
|*ステートメントの削除 - 検索*|"場所を削除する"|SQL_DIAG_DELETE_WHERE|  
|*ドロップアサーションステートメント*|"アサーションのドロップ"|SQL_DIAG_DROP_ASSERTION|  
|*ドロップ文字セット-stmt*|"文字セットを削除"|SQL_DIAG_DROP_CHARACTER_SET|  
|*ドロップ照合順序-ステートメント*|"ドロップ照合順序"|SQL_DIAG_DROP_COLLATION|  
|*ドロップ ドメイン ステートメント*|"ドメインをドロップ"|SQL_DIAG_DROP_DOMAIN|  
|*ドロップインデックスステートメント*|"インデックスを削除"|SQL_DIAG_DROP_INDEX|  
|*ドロップスキーマステートメント*|"スキーマのドロップ"|SQL_DIAG_DROP_SCHEMA|  
|*ドロップ テーブルステートメント*|"テーブルをドロップ"|SQL_DIAG_DROP_TABLE|  
|*ドロップ・トランスレーション・ステートメント*|「翻訳を落とす」|SQL_DIAG_DROP_TRANSLATION|  
|*ドロップビューステートメント*|"ドロップビュー"|SQL_DIAG_DROP_VIEW|  
|*助成金書*|「グラント」|SQL_DIAG_GRANT|
|*挿入ステートメント*|"挿入"|SQL_DIAG_INSERT|  
|*ODBC プロシージャ拡張*|「呼び出す」|SQL_DIAG_コール|  
|*取り消しステートメント*|"取り消し"|SQL_DIAG_REVOKE|  
|*スキーマ定義*|"スキーマの作成"|SQL_DIAG_CREATE_SCHEMA|  
|*翻訳定義*|「翻訳の作成」|SQL_DIAG_CREATE_TRANSLATION|  
|*ステートメントの位置を更新する*|"動的更新カーソル"|SQL_DIAG_DYNAMIC_UPDATE_CURSOR|  
|*ステートメントの更新 - 検索*|"更新場所"|SQL_DIAG_UPDATE_WHERE|  
|Unknown|*空の文字列*|SQL_DIAG_UNKNOWN_STATEMENT|  

<!--
These two malformed table rows were fixed by educated GUESS only.
Each pair starts with the original flawed row.
Flawed because treated as only two cells by HTML render,
and because missing info anyway.
Also, these flawed rows lacked '|' as their first nonWhitespace character (although markdown technically allows this omission, unfortunately).
Arguably the following SQL.H file shows the sequence of the flawed rows in the table was suboptimal also.

ftp://www.fpc.org/fpc32/VS6Disk1/VC98/INCLUDE/SQL.H

GeneMi , 2019/01/19
- - - - - - - - - - - - - -

n-definition*|"CREATE DOMAIN"|SQL_DIAG_CREATE_DOMAIN|  

|*domain-definition*|"CREATE DOMAIN"|SQL_DIAG_CREATE_DOMAIN|

-statement*|"GRANT"|SQL_DIAG_GRANT|  

|*grant-statement*|"GRANT"|SQL_DIAG_GRANT|

-->

## <a name="sequence-of-status-records"></a>状態レコードのシーケンス

 ステータス レコードは、行番号と診断の種類に基づいて順序に配置されます。 ドライバー マネージャーは、最終的に生成する状態レコードを返す順序を決定します。 ドライバーは、それが生成する状態レコードを返す最終的な順序を決定します。  
  
 診断レコードがドライバー マネージャーとドライバーの両方によってポストされる場合、ドライバー マネージャーは、それらを順序付けします。  
  
 2 つ以上の状態レコードがある場合、レコードの順序は行番号によって最初に決定されます。 行ごとの診断レコードの順序の決定には、次の規則が適用されます。  
  
-   SQL_NO_ROW_NUMBERが -1 として定義されているため、どの行にも対応しないレコードは、特定の行に対応するレコードの前に表示されます。  
  
-   行番号が不明なレコードは、SQL_ROW_NUMBER_UNKNOWNが -2 として定義されているため、他のすべてのレコードの前に表示されます。  
  
-   特定の行に関連するすべてのレコードについて、レコードは SQL_DIAG_ROW_NUMBER フィールドの値で並べ替えられます。 影響を受ける最初の行のすべてのエラーと警告が一覧表示され、次の行のすべてのエラーと警告が影響を受けます。  
  
> [!NOTE]
>  ODBC 3 *.x*ドライバー マネージャーは、SQLSTATE 01S01 (行のエラー) が ODBC 2 *.x*ドライバーによって返された場合、または SQLExtendedFetch が呼び出されたときに ODBC 3 *.x*ドライバーによって SQLSTATE 01S01 (行のエラー) が返された場合、または**SQLExtendedFetch**で配置されたカーソルに対して**SQLSetPos**が呼び出された場合、診断キューの状態レコードを順序付けしません。 **SQLExtendedFetch**  
  
 各行内、または行番号が不明な行に対応していないすべてのレコード、または行番号が SQL_NO_ROW_NUMBER に等しいすべてのレコードについて、一連の並べ替え規則を使用して、最初のレコードが決定されます。 最初のレコードの後で、行に影響を与える他のレコードの順序は未定義です。 アプリケーションは、最初のレコードの後にエラーが警告の前に置かれないと仮定することはできません。 アプリケーションは、関数の呼び出しが失敗した場合に関する完全な情報を取得するために、完全な診断データ構造をスキャンする必要があります。  
  
 行内の最初のレコードを決定するには、次の規則が使用されます。 最高ランクのレコードが最初のレコードです。 レコードのソース (ドライバー マネージャー、ドライバー、ゲートウェイなど) は、レコードのランク付け時には考慮されません。  
  
-   **エラー**エラーを記述する状態レコードのランクが最も高い。 ソートエラーには、次の規則が適用されます。  
  
    -   トランザクションの失敗またはトランザクションの失敗の可能性を示すレコードは、他のすべてのレコードを上回ります。  
  
    -   2 つ以上のレコードが同じエラー条件を記述している場合、オープン・グループ CLI 仕様 (クラス 03 から HZ) によって定義された SQLSTATE は、ODBC およびドライバー定義の SQLSTATE を上回ります。  
  
-   **実装定義のデータなし値**ドライバー定義の No Data 値 (クラス 02) を記述する状態レコードは、2 番目に高いランクを持ちます。  
  
-   **警告**警告を記述する状態レコード (クラス 01) のランクは最も低くなります。 2 つ以上のレコードが同じ警告条件を記述している場合、オープン・グループ CLI 仕様で定義された SQLSTATE が ODBC 定義およびドライバー定義の SQLSTATE を上回る警告 SQLSTATE を警告します。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|診断データ構造の複数のフィールドの取得|[SQLGetDiagRec 関数](sqlgetdiagrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
