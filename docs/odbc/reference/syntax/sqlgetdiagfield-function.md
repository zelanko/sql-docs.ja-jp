---
title: "SQLGetDiagField 関数 |Microsoft ドキュメント"
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
- SQLGetDiagField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagField
helpviewer_keywords:
- SQLGetDiagField function [ODBC]
ms.assetid: 1dbc4398-97a8-4585-bb77-1f7ea75e24c4
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0cd8f64eb18fc6e1fb456b03ef65ef2dc33cc140
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdiagfield-function"></a>SQLGetDiagField 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLGetDiagField**診断データ構造体の (指定されたハンドルに関連付けられた) エラー、警告、およびステータス情報が含まれるレコードのフィールドの現在の値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 [入力]対象の診断に必要なハンドルの種類を説明するハンドル型の識別子です。 次のいずれかを指定する必要があります。  
  
-   SQL_HANDLE_DBC として  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN ハンドルは、ドライバー マネージャーとドライバーのによってのみ使用されます。 アプリケーションでは、この種類のハンドルは使用しないでください。 SQL_HANDLE_DBC_INFO_TOKEN の詳細については、次を参照してください。 [ODBC ドライバーで接続プールの認識開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)です。  
  
 *Handle*  
 [入力]によって示される型の診断データの構造体へのハンドル*HandleType*です。 場合*HandleType*を sql_handle_env として、*処理*共有または共有されていない環境ハンドルのいずれかを指定できます。  
  
 *RecNumber*  
 [入力]アプリケーションが情報をシークする元となる状態レコードを示します。 状態レコードは、1 から番号が付けられます。 場合、 *DiagIdentifier*引数は、診断ヘッダーのすべてのフィールドを示す*RecNumber*は無視されます。 ストアド プロシージャを使用していない場合は、0 を超えること必要があります。  
  
 *DiagIdentifier*  
 [入力]値が返される診断フィールドを示します。 詳細については、次を参照してください、"*DiagIdentifier*引数"の"コメント"セクション。  
  
 *DiagInfoPtr*  
 [出力]診断情報を返すバッファーへのポインター。 データ型は、の値によって異なります。 *DiagIdentifier*です。 場合*DiagInfoPtr*は整数型、アプリケーションは SQLULEN のバッファーを使用する必要があります、および下位 32 ビットまたは 16 ビット、バッファーの作成の初期化、値をいくつかのドライバーとしてこの関数を呼び出す前に 0 がのみと、上位のままにビットは変更されません。  
  
 場合*DiagInfoPtr* null、 *StringLengthPtr*バイト (文字データの null 終端文字を除く) の合計数を返すはまだが指すバッファーに返される使用可能な*DiagInfoPtr*です。  
  
 *BufferLength*  
 [入力]場合*DiagIdentifier*は、ODBC で定義された診断と*DiagInfoPtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります\* *DiagInfoPtr*. 場合*DiagIdentifier* ODBC で定義されたフィールドと\* *DiagInfoPtr*整数*BufferLength*は無視されます。 場合の値* \*DiagInfoPtr* Unicode 文字列です (呼び出し時に**SQLGetDiagFieldW**) では、 *BufferLength*引数は偶数である必要があります。  
  
 場合*DiagIdentifier*ドライバーの定義済みのフィールドでは、アプリケーション、ドライバー マネージャーに、フィールドの性質を示す設定、 *BufferLength*引数。 *BufferLength*次の値を持つことができます。  
  
-   場合*DiagInfoPtr*文字の文字列を指すポインター *BufferLength* SQL_NTS または文字列の長さです。  
  
-   場合*DiagInfoPtr*バイナリのバッファー、アプリケーションの場所へのポインター、SQL_LEN_BINARY_ATTR の結果である (*長さ*) マクロで*BufferLength*です。 これにより、配置に負の値*BufferLength*です。  
  
-   場合*DiagInfoPtr*文字の文字列またはバイナリ文字列以外の値を指すポインター *BufferLength* SQL_IS_POINTER 値でなければなりません。  
  
-   場合* \*DiagInfoPtr* 、固定長データ型を含む*BufferLength*が SQL_IS_INTEGER、SQL_IS_UINTEGER、SQL_IS_SMALLINT、または SQL_IS_USMALLINT、必要に応じて。  
  
 *StringLengthPtr*  
 [出力]合計バイト数 (null 終端文字のために必要なバイト数を除く) を返すバッファーへのポインターで返される使用可能な\* *DiagInfoPtr*、文字データ用です。 場合は、使用できるバイト数を返すより大きいまたは等しい*BufferLength*、内のテキスト\* *DiagInfoPtr*に切り捨てられます*BufferLength*負符号null 終了文字の長さ。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_NO_DATA です。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetDiagField**自体の診断レコードが通知されません。 次の戻り値を使用して、独自の実行の結果を報告します。  
  
-   SQL_SUCCESS: 関数では診断情報が正常に返されます。  
  
-   SQL_SUCCESS_WITH_INFO: \* *DiagInfoPtr*小さすぎるため、要求された診断フィールドを保持します。 そのため、診断フィールド内のデータが切り捨てられました。 切り捨てが発生しました、アプリケーションを比較する必要がありますのことを確認する*BufferLength*実際に書き込まれますが、使用可能なバイト数へ **StringLengthPtr*です。  
  
-   SQL_INVALID_HANDLE: によってハンドルが示される*HandleType*と*処理*が有効なハンドル。  
  
-   SQL_ERROR: 次のいずれかが発生しました。  
  
    -   *DiagIdentifier*引数が有効な値のいずれか。  
  
    -   *DiagIdentifier*引数が SQL_DIAG_CURSOR_ROW_COUNT、SQL_DIAG_DYNAMIC_FUNCTION、SQL_DIAG_DYNAMIC_FUNCTION_CODE、または SQL_DIAG_ROW_COUNT が*処理*ステートメント ハンドルではありません。 (ドライバー マネージャーを診断します。)  
  
    -   *RecNumber*引数が負または 0 時に*DiagIdentifier*診断レコードからフィールドを表示します。 *RecNumber*ヘッダー フィールドは無視されます。  
  
    -   要求された値が文字の文字列と*BufferLength*が 0 未満です。  
  
    -   非同期の通知を使用する場合、ハンドルに非同期操作は完了しませんでした。  
  
-   SQL_NO_DATA: *RecNumber*診断レコードで指定されたハンドルに存在していた数よりも大きかった*を処理します。* 関数は、任意の正の SQL_NO_DATA が返さも*RecNumber*に対する診断レコードが存在しない場合*処理*です。  
  
## <a name="comments"></a>コメント  
 アプリケーションを呼び出す通常**SQLGetDiagField**を 3 つの目標の 1 つを実行します。  
  
1.  関数呼び出しで SQL_ERROR または sql_success_with_info が返されたがときに、特定のエラーまたは警告情報を取得する (またはの SQL_NEED_DATA、 **SQLBrowseConnect**関数)。  
  
2.  呼び出して、insert、delete、または更新操作が実行されたときの影響を受けたデータ ソース内の行の数を決定する**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos** (SQL_DIAG_ROW_COUNT ヘッダー フィールドから)、または、ドライバーは、この情報を提供できる場合は、現在開いているカーソル内に存在する行の数を決定する (から、SQL_DIAG_CURSOR_ROW_COUNT ヘッダー フィールド) です。  
  
3.  呼び出しによって実行された場合の関数を決定する**SQLExecDirect**または**SQLExecute** (、SQL_DIAG_DYNAMIC_FUNCTION と SQL_DIAG_DYNAMIC_FUNCTION_CODE ヘッダー フィールドから)。  
  
 どの ODBC 関数を投稿できます 0 個以上の診断レコードことが呼び出されるたびにアプリケーションが呼び出すことができますので**SQLGetDiagField** ODBC 関数呼び出しの後にします。 任意の時点で格納できる診断レコードの数に制限はありません。 **SQLGetDiagField**最近で指定された診断データの構造に関連付けられている診断の情報のみを取得、*処理*引数。 アプリケーションが以外の場合、ODBC 関数を呼び出す場合**SQLGetDiagField**または**SQLGetDiagRec**、同じハンドルを使用して前の呼び出しから診断情報は失われます。  
  
 アプリケーションが増分してすべての診断レコードをスキャンできます*RecNumber*限り、 **SQLGetDiagField** SQL_SUCCESS を返します。 SQL_DIAG_NUMBER ヘッダー フィールドには、状態レコードの数が示されます。 呼び出す**SQLGetDiagField**ヘッダーとレコード フィールドに非破壊的です。 アプリケーションが呼び出すことができます**SQLGetDiagField**間に、同じハンドルにレコードを投稿は診断関数以外の関数が呼び出されていない限り、レコードからフィールドを取得する後でもう一度です。  
  
 アプリケーションが呼び出すことができます**SQLGetDiagField** SQL_DIAG_CURSOR_ROW_COUNT または場合、SQL_ERROR を返しますこれ SQL_DIAG_ROW_COUNT を除き、いつでも任意の診断フィールドを返す*処理*されませんが、ステートメント ハンドルです。 他の診断フィールドが定義されていない場合への呼び出し**SQLGetDiagField** (その他の診断が出現しない) 提供 SQL_SUCCESS が返され、フィールドの未定義の値が返されます。  
  
 詳細については、次を参照してください。[を使用して SQLGetDiagRec と SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)と[SQLGetDiagRec の実装と SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)です。  
  
 非同期的に実行されているもの以外の API を呼び出すと、HY010 が生成されます「関数のシーケンス エラー」です。 ただし、非同期操作が完了する前に、エラー レコードを取得できません。  
  
## <a name="handletype-argument"></a>HandleType 引数  
 各ハンドル型には、関連付けられている診断の情報を持つことができます。 *HandleType*引数のハンドル型を示す*処理*です。  
  
 いくつかのヘッダーとレコード フィールドは、環境、接続、ステートメント、および記述子ハンドル返されることはできません。 それらのハンドル フィールドは適用されませんが、「ヘッダー フィールド」と「レコードのフィールド」セクションでは、次に表示されます。  
  
 場合*HandleType*を sql_handle_env として、*処理*共有または共有されていない環境ハンドルのいずれかであることができます。  
  
 環境ハンドルに関連付けることはドライバー固有のヘッダーの診断フィールドはありません。  
  
 記述子ハンドルに対して定義されている診断のみヘッダー フィールドは、SQL_DIAG_NUMBER SQL_DIAG_RETURNCODE です。  
  
## <a name="diagidentifier-argument"></a>DiagIdentifier 引数  
 この引数は、診断データの構造から必要なフィールドの識別子を示します。 場合*RecNumber*がより大きい値が 1 に、フィールドのデータについて説明します、関数によって返される診断情報またはします。 場合*RecNumber*が 0 のフィールドは、診断データの構造のヘッダー内で診断の情報を特定の情報が返される関数呼び出しに関連するデータを含んでいます場合、。  
  
 ドライバーは、診断データ構造で、ドライバー固有のヘッダーとレコードのフィールドを定義できます。  
  
 ODBC 3*.x* ODBC 2 作業アプリケーション*.x*ドライバーが呼び出すできる**SQLGetDiagField**でのみ、 *DiagIdentifier*SQL_DIAG_CLASS_ORIGIN、SQL_DIAG_CLASS_SUBCLASS_ORIGIN、SQL_DIAG_CONNECTION_NAME、SQL_DIAG_MESSAGE_TEXT、SQL_DIAG_NATIVE、SQL_DIAG_NUMBER、SQL_DIAG_RETURNCODE、SQL_DIAG_SERVER_NAME、または SQL_DIAG_SQLSTATE の引数。 その他のすべての診断フィールドには、SQL_ERROR が返されます。  
  
## <a name="header-fields"></a>ヘッダー フィールド  
 次の表に記載されたヘッダー フィールドに含まれる、 *DiagIdentifier*引数。  
  
|DiagIdentifier|戻り値の型|返します。|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CURSOR_ROW_COUNT|SQLLEN|このフィールドには、カーソル内の行の数が含まれています。 自身のセマンティクスが異なります、 **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES2、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2、SQL_KEYSET_CURSOR_ATTRIBUTES2、および SQL_STATIC_CURSOR_ATTRIBUTES2、いることを示す情報の種類各カーソルの種類 (SQL_CA2_CRC_EXACT と SQL_CA2_CRC_APPROXIMATE bits) の行カウントを利用できます。<br /><br /> このフィールドの内容がだけステートメント ハンドルおよび定義した後に**SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**が呼び出されました。 呼び出す**SQLGetDiagField**で、 *DiagIdentifier*ステートメント以外で SQL_DIAG_CURSOR_ROW_COUNT のハンドルは SQL_ERROR を返します。|  
|SQL_DIAG_DYNAMIC_FUNCTION|SQLCHAR *|これは、基になる関数を実行する SQL ステートメントを表す文字列です。 (特定の値を"フィールドの値を動的関数、"このセクションの後半を参照してください)。ステートメント ハンドルおよびのみ呼び出しの後にのみ、このフィールドの内容が定義された**SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**です。 呼び出す**SQLGetDiagField**で、 *DiagIdentifier*ステートメント以外で SQL_DIAG_DYNAMIC_FUNCTION のハンドルは SQL_ERROR を返します。 このフィールドの値が呼び出しの前に定義されていない**SQLExecute**または**SQLExecDirect**です。|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|SQLINTEGER|これは、基になる関数によって実行された SQL ステートメントを表す数値コードです。 (特定の値の「値の 動的関数フィールド、」このセクションの後半を参照してください)。ステートメント ハンドルおよびのみ呼び出しの後にのみ、このフィールドの内容が定義された**SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**です。 呼び出す**SQLGetDiagField**で、 *DiagIdentifier*ステートメント以外で SQL_DIAG_DYNAMIC_FUNCTION_CODE のハンドルは SQL_ERROR を返します。 このフィールドの値が呼び出しの前に定義されていない**SQLExecute**または**SQLExecDirect**です。|  
|SQL_DIAG_NUMBER|SQLINTEGER|指定されたハンドルで利用可能な状態レコードの数。|  
|SQL_DIAG_RETURNCODE|SQLRETURN|関数によって返されたコードを返します。 リターン コードの一覧は、次を参照してください。[のリターン コード](../../../odbc/reference/develop-app/return-codes-odbc.md)です。 ドライバーは SQL_DIAG_RETURNCODE; を実装する必要はありません。ドライバー マネージャーによって常に実装されます。 関数はまだで呼び出されていない場合、*処理*、SQL_DIAG_RETURNCODE に対して SQL_SUCCESS が返されます。|  
|SQL_DIAG_ROW_COUNT|SQLLEN|Insert、delete、またはを実行した更新によって影響を受けた行数**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**. ドライバーの定義後は、*カーソル仕様*は実行されていません。 このフィールドの内容は、ステートメント ハンドルに対してのみ定義されます。 呼び出す**SQLGetDiagField**で、 *DiagIdentifier*ステートメント以外で SQL_DIAG_ROW_COUNT のハンドルは SQL_ERROR を返します。 このフィールドのデータでもが返されます、 *RowCountPtr*の引数**SQLRowCount**です。 によって返される行の数が、このフィールドのデータはすべて nondiagnostic 関数の呼び出し後にリセット**SQLRowCount**ステートメントが準備または割り当て済みの状態に戻す設定されるまでは同じです。|  
  
## <a name="record-fields"></a>レコードのフィールド  
 次の表に記載されたレコード フィールドに含まれる、 *DiagIdentifier*引数。  
  
|DiagIdentifier|戻り値の型|返します。|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CLASS_ORIGIN|SQLCHAR *|このレコードの SQLSTATE 値のクラスの部分を定義するドキュメントを示す文字列です。 その値が、Open Group および ISO 呼び出しレベルのインターフェイスで定義されたすべての SQLSTATEs"ISO 9075"。 (すべての人が SQLSTATE クラスは、"IM") に固有の ODBC SQLSTATEs、その値は"ODBC 3.0" です。|  
|SQL_DIAG_COLUMN_NUMBER|SQLINTEGER|SQL_DIAG_ROW_NUMBER フィールドが、行セットまたはパラメーターのセットの有効な行番号の場合は、このフィールドには、結果セット内の列番号または一連のパラメーターでパラメーターの番号を表す値が含まれています。 結果セット列の番号は常に 1 から始まりますこの状態レコードは、ブックマーク列を示し、フィールドが 0 にすることができます。 パラメーター番号は、1 から始まります。 状態レコードは、列番号やパラメーター番号に関連付けられていない場合は、値 SQL_NO_COLUMN_NUMBER を持ちます。 ドライバーが、列番号またはこのレコードに関連付けられているパラメーターの数を判別できない場合、このフィールドは値 SQL_COLUMN_NUMBER_UNKNOWN を持ちます。<br /><br /> このフィールドの内容は、ステートメント ハンドルに対してのみ定義されます。|  
|SQL_DIAG_CONNECTION_NAME|SQLCHAR *|診断レコードに関連する接続の名前を示す文字列です。 このフィールドは、ドライバーの定義です。 環境ハンドルに関連付けられている診断データの構造体との接続に関連していない診断では、このフィールドは長さ 0 の文字列です。|  
|SQL_DIAG_MESSAGE_TEXT|SQLCHAR *|エラーまたは警告の情報メッセージです。 このフィールドは」の説明に従って書式設定[診断メッセージ](../../../odbc/reference/develop-app/diagnostic-messages.md)です。 診断メッセージのテキストを最大長はありません。|  
|SQL_DIAG_NATIVE|SQLINTEGER|ドライバー/データ ソース固有のネイティブ エラー コード。 ネイティブ エラー コードが存在しない場合、ドライバーは、0 を返します。|  
|SQL_DIAG_ROW_NUMBER|SQLLEN|このフィールドには、行セットの行番号または状態レコードが関連付けられているパラメーターのセット内のパラメーター番号が含まれています。 行番号およびパラメーターの番号は、1 から始まります。 このフィールドは、この状態レコードは、行番号やパラメーター番号に関連付けられていない場合、値 SQL_NO_ROW_NUMBER を持ちます。 ドライバーが、行番号またはこのレコードに関連付けられているパラメーターの数を判別できない場合、このフィールドは値 SQL_ROW_NUMBER_UNKNOWN を持ちます。<br /><br /> このフィールドの内容は、ステートメント ハンドルに対してのみ定義されます。|  
|SQL_DIAG_SERVER_NAME|SQLCHAR *|診断レコードに関連するサーバー名を示す文字列です。 呼び出しに対して返される値と同じである**SQLGetInfo** SQL_DATA_SOURCE_NAME オプションを使用します。 環境ハンドルに関連付けられている診断データの構造体と任意のサーバーに関連していない診断では、このフィールドは長さ 0 の文字列です。|  
|SQL_DIAG_SQLSTATE|SQLCHAR *|5 文字の SQLSTATE 診断コード。 詳細については、次を参照してください。 [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md)です。|  
|SQL_DIAG_SUBCLASS_ORIGIN|SQLCHAR *|有効な値と同じ形式で文字列として SQL_DIAG_CLASS_ORIGIN、SQLSTATE コードのサブクラスの一部の定義の部分を識別します。 "ODBC 3.0"を返す基になる ODBC 固有 SQLSTATES、次のとおりです。<br /><br /> 01S00、01S01、01S02、01S06、01S07、07S01、08S01、21S01、21S02、25S01、25S02、25S03、42S01、42S02、42S11、42S12、42S21、42S22、HY095、HY097、HY098、HY099、HY100、HY101、HY105、HY107、HY109、HY110、HY111、HYT00、HYT01、IM001、IM002、IM003、IM004、IM005、IM006、IM007 IM008、IM010、IM011 IM012 です。|  
  
## <a name="values-of-the-dynamic-function-fields"></a>動的関数フィールドの値  
 次の表に、SQL_DIAG_DYNAMIC_FUNCTION と SQL_DIAG_DYNAMIC_FUNCTION_CODE の値への呼び出しによって実行された SQL ステートメントの種類ごとに適用される**SQLExecute**または**SQLExecDirect**. ドライバーは、記載されているドライバーの定義済みの値を追加できます。  
  
|SQL ステートメント (SQL statement)<br /><br /> 実行|値<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION|値<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION_CODE|  
|--------------------------------|-----------------------------------------------|-----------------------------------------------------|  
|*alter ドメイン ステートメント*|「ALTER ドメイン」|SQL_DIAG_ALTER_DOMAIN|  
|*alter table ステートメント*|"ALTER TABLE"|SQL_DIAG_ALTER_TABLE|  
|*アサーション定義*|「アサーションの作成」|SQL_DIAG_CREATE_ASSERTION|  
|*文字セットの定義*|「文字セットの作成」|SQL_DIAG_CREATE_CHARACTER_SET|  
|*照合順序定義*|「照合順序の作成」|SQL_DIAG_CREATE_COLLATION|  
|*create index ステートメント*|「インデックスの作成」|SQL_DIAG_CREATE_INDEX|  
|*作成テーブル ステートメント*|「テーブルの作成」|SQL_DIAG_CREATE_TABLE|  
|*create view ステートメント*|「ビューの作成」|SQL_DIAG_CREATE_VIEW|  
|*カーソルの指定*|"カーソルを SELECT"|SQL_DIAG_SELECT_CURSOR|  
|*delete ステートメント配置*|"動的な削除の CURSOR"|SQL_DIAG_DYNAMIC_DELETE_CURSOR|  
|*delete ステートメントの検索*|「WHERE の削除」|SQL_DIAG_DELETE_WHERE|  
n-定義 *|「ドメインの作成」|SQL_DIAG_CREATE_DOMAIN|  
|*ドロップ アサート ステートメント*|「ドロップ アサーション」|SQL_DIAG_DROP_ASSERTION|  
|*ドロップ文字セット stmt*|「ドロップ文字セット」|SQL_DIAG_DROP_CHARACTER_SET|  
|*drop-照合順序のステートメント*|「照合順序をドロップ」|SQL_DIAG_DROP_COLLATION|  
|*ドロップ ドメイン ステートメント*|「ドメイン」をドロップ|SQL_DIAG_DROP_DOMAIN|  
|*drop index ステートメント*|"DROP INDEX"|SQL_DIAG_DROP_INDEX|  
|*drop schema ステートメント*|"DROP SCHEMA"|SQL_DIAG_DROP_SCHEMA|  
|*drop table ステートメント*|"DROP TABLE"|SQL_DIAG_DROP_TABLE|  
|*drop-変換-ステートメント*|「変換してドロップ」|SQL_DIAG_DROP_TRANSLATION|  
|*drop view ステートメント*|"DROP VIEW"|SQL_DIAG_DROP_VIEW|  
-ステートメント *|「許可」|SQL_DIAG_GRANT|  
|*insert ステートメント*|"INSERT"|SQL_DIAG_INSERT|  
|*ODBC の手順-拡張機能*|「呼び出し」|SQL_DIAG_ 呼び出し|  
|*revoke ステートメント*|"REVOKE"|SQL_DIAG_REVOKE|  
|*スキーマ定義*|「スキーマの作成」|SQL_DIAG_CREATE_SCHEMA|  
|*翻訳の定義*|「翻訳の作成」|SQL_DIAG_CREATE_TRANSLATION|  
|*update ステートメント配置*|「動的な更新カーソル」|SQL_DIAG_DYNAMIC_UPDATE_CURSOR|  
|*update ステートメントの検索*|"WHERE を更新する|SQL_DIAG_UPDATE_WHERE|  
|Unknown|*空の文字列*|SQL_DIAG_UNKNOWN_STATEMENT|  
  
## <a name="sequence-of-status-records"></a>状態レコードのシーケンス  
 状態レコードは、行番号と診断の種類に基づいて、シーケンスに配置されます。 ドライバー マネージャーでは、生成された状態レコードを返す最終的な順序を決定します。 ドライバーでは、生成された状態レコードを返す最終的な順序を決定します。  
  
 診断レコードは、ドライバー マネージャーとドライバーの両方によって送信されたが場合、は、ドライバー マネージャーを順序付ける担当します。  
  
 2 つ以上の状態レコードがある場合は、行の数によって、レコードのシーケンスが最初に決定されます。 行によって診断レコードのシーケンスを判断するために、次の規則が適用されます。  
  
-   任意の行に対応していないレコードを-1 SQL_NO_ROW_NUMBER が定義されているために、特定の行に対応するレコードの前に表示されます。  
  
-   対象の行番号が不明のレコードは、– 2 である SQL_ROW_NUMBER_UNKNOWN が定義されているため、他のすべてのレコードの前に表示されます。  
  
-   特定の行に関連するすべてのレコードのレコードが SQL_DIAG_ROW_NUMBER フィールドの値によって並べ替えられます。 すべてのエラーと最初の影響を受ける行の警告が表示され、し、すべてのエラーと警告は、次の行、影響を受けるおよびなどです。  
  
> [!NOTE]  
>  ODBC 3*.x*ドライバー マネージャーの順序付けしません状態レコード診断のキューに場合 SQLSTATE 01S01 (行でエラー) は、ODBC 2 によって返される*.x*ドライバー場合、または SQLSTATE 01S01 (行でエラー) は、ODBC によって返される3*.x*ドライバーと**SQLExtendedFetch**が呼び出されたまたは**SQLSetPos**に位置付けられているカーソルに対してを呼び出した**SQLExtendedFetch**.  
  
 各行では、またはそれらすべてのレコードにも、または行の番号が指定されて、既知の行に対応していないまたは SQL_NO_ROW_NUMBER と等しい行番号を持つそれらすべてのレコードの表示されている最初のレコードは、並べ替え規則のセットを使用してによって決定されます。 最初のレコードの後の行に影響するその他のレコードの順序は定義されません。 アプリケーションは、警告のエラーは、最初のレコードの後に前に限りません。 アプリケーションでは、完全な関数呼び出しが失敗した情報を入手する診断データの完全な構造をスキャンする必要があります。  
  
 次の規則は、行内の最初のレコードの決定に使用されます。 最高のランクを持つレコードは、最初のレコードです。 (ドライバー マネージャー、ドライバー、ゲートウェイ、およびなど) のレコードのソースとは見なされませんときにレコードを順位付けされます。  
  
-   **エラー**状態レコードのエラーを記述する最高ランクであります。 エラーを並べ替えるには、次の規則が適用されます。  
  
    -   トランザクションの失敗または可能なトランザクションの失敗を示すレコードは、他のすべてのレコードを outrank です。  
  
    -   場合は 2 つまたは複数のレコードには、同じエラー条件について説明する、開くグループ CLI 仕様 (HZ を通じてクラス 03) で定義される SQLSTATEs outrank SQLSTATEs の ODBC およびドライバーの定義とします。  
  
-   **No データ値の実装で定義された**なしのデータ値 (クラス 02) のドライバーの定義を記述する状態レコードがある、2 つ目最高ランクです。  
  
-   **警告**警告 (クラス 01) を示す状態レコード最低ランクであります。 2 つまたは複数のレコード SQLSTATEs 開くグループ CLI 仕様によって定義されているが、警告、同じ警告の状態を記述する場合は、ODBC で定義され、ドライバーの定義済みの SQLSTATEs を outrank です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|診断データの構造体の複数のフィールドを取得します。|[SQLGetDiagRec 関数](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
