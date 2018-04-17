---
title: SQLColAttribute 関数 |Microsoft ドキュメント
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
- SQLColAttribute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColAttribute
helpviewer_keywords:
- SQLColAttribute function [ODBC]
ms.assetid: 8c45c598-cb01-4789-a571-e93619a18ed9
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 765cdab2b8619501a29990c9b944b3b98797b4ed
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlcolattribute-function"></a>SQLColAttribute 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLColAttribute**結果セットの列の記述子情報を返します。 記述子の情報は、文字の文字列、記述子に依存する値または整数値として返されます。  
  
> [!NOTE]  
>  どのようなドライバー マネージャーの詳細と ODBC 3 には、この関数にマップします。*x* ODBC 2 を利用するアプリケーション*。x*ドライバーを参照してください[アプリケーションの旧バージョンと互換性を保つのための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *ColumnNumber*  
 [入力]フィールドの値を取得する元となる IRD 内のレコードの数。 この引数は、列の昇順に、1 から始まります順番に並べ替えられて、結果のデータの列番号に対応します。 列は、任意の順序で記述できます。  
  
 この引数では、列 0 を指定できますが、SQL_DESC_TYPE と SQL_DESC_OCTET_LENGTH を除くすべての値は未定義の値を返します。  
  
 *FieldIdentifier*  
 [入力]記述子のハンドルです。 このハンドルは、IRD のフィールドは (たとえば、SQL_COLUMN_TABLE_NAME) クエリを実行する必要がありますを定義します。  
  
 *CharacterAttributePtr*  
 [出力]値を返すバッファーへのポインター、 *FieldIdentifier*のフィールド、 *ColumnNumber*フィールドが文字の文字列である場合は、IRD の行。 それ以外の場合、フィールドは使用されません。  
  
 場合*CharacterAttributePtr*が NULL の場合、 *StringLengthPtr*はバイト (文字データの null 終端文字を除く) の合計数を返しますが、バッファーに返される使用可能なによって示される*CharacterAttributePtr*です。  
  
 *BufferLength*  
 [入力]場合*FieldIdentifier* ODBC で定義されたフィールドと*CharacterAttributePtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります\* *CharacterAttributePtr*です。 場合*FieldIdentifier* ODBC で定義されたフィールドと\* *CharacterAttribute*Ptr が整数では、このフィールドは無視されます。 場合、  *\*CharacterAttributePtr* Unicode 文字列です (呼び出し時に**SQLColAttributeW**) では、 *BufferLength*引数は偶数である必要があります。 場合*FieldIdentifier*ドライバーの定義済みのフィールドでは、アプリケーション、ドライバー マネージャーに、フィールドの性質を示す設定、 *BufferLength*引数。 *BufferLength*次の値を持つことができます。  
  
-   場合*CharacterAttributePtr* 、ポインターへのポインターは、 *BufferLength* SQL_IS_POINTER 値でなければなりません。  
  
-   場合*CharacterAttributePtr*文字の文字列へのポインター、 *BufferLength*バッファーの長さです。  
  
-   場合*CharacterAttributePtr*バイナリのバッファー、アプリケーションの場所へのポインター、SQL_LEN_BINARY_ATTR の結果である (*長さ*) マクロで*BufferLength*です。 これにより、配置に負の値*BufferLength*です。  
  
-   場合*CharacterAttributePtr* 、固定長のデータ型へのポインターは、 *BufferLength*次のいずれかを指定する必要があります: SQL_IS_INTEGER、SQL_IS_UNINTEGER、SQL_SMALLINT、または SQLUSMALLINT です。  
  
 *StringLengthPtr*  
 [出力]バイト (文字データの null 終了バイトを除く) の合計数を返すバッファーへのポインターで返される使用可能な **CharacterAttributePtr*です。  
  
 文字データの場合は、使用できるバイト数を返すより大きいまたは等しい*BufferLength*、記述子の情報は、 \* *CharacterAttributePtr* に切り捨てられます*BufferLength* null 終端文字の長さマイナスはドライバーによって null で終わるとします。  
  
 他のすべての種類の値のデータの*BufferLength*は無視されます、ドライバーのサイズを想定しています **CharacterAttributePtr* 32 ビットです。  
  
 *NumericAttributePtr*  
 [出力]値を返す整数バッファーへのポインター、 *FieldIdentifier*のフィールド、 *ColumnNumber*フィールドが SQL_DESC_COLUMN_LENGTH など、記述子の数値型である場合は、IRD の行。 それ以外の場合、フィールドは使用されません。 一部のドライバーのみ書き込むことが、下位 32 ビットまたは 16 ビットのバッファーとのままにして、上位ビットに変更されていないことに注意してください。 そのため、アプリケーションでは、この関数を呼び出す前に 0 に値を初期化する必要があります。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLColAttribute** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します、関連付けられた SQLSTATE 値を呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType*sql_handle_stmt としての*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLColAttribute**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|バッファー \* *CharacterAttributePtr*文字列全体の値を返す、文字列値が切り捨てられましたために大きさが不十分です。 切り詰められていない文字列値の長さが返される **StringLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07005|準備されたステートメントがない、*カーソルの指定*|関連付けられているステートメント、 *StatementHandle*結果セットを返しませんでしたと*FieldIdentifier* SQL_DESC_COUNT でした。 記述する列がありませんでした。|  
|07009|無効な記述子のインデックス|(DM) の指定された値*ColumnNumber*を 0 に等しい、SQL_ATTR_USE_BOOKMARKS ステートメント属性は SQL_UB_OFF をでした。<br /><br /> 引数が指定された値*ColumnNumber*が結果セット内の列の数を超えています。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagField**診断データから、構造体では、エラーとその原因がについて説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 SQLColAttribute が呼び出されたときに、この非同期関数が実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、関数が呼び出された呼び出しの前に**SQLPrepare**、 **SQLExecDirect**、またはのカタログ関数、 *StatementHandle*です。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM)  *\*CharacterAttributePtr*文字の文字列、および*BufferLength* SQL_NTS に等しくないが、0 より小さいをでした。|  
|HY091|無効な記述子フィールド識別子|引数が指定された値*FieldIdentifier*が定義されている値のいずれかと、実装定義の値ではありません。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|対応していないドライバー|引数が指定された値*FieldIdentifier*ドライバーによってサポートされていませんでした。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
 後に呼び出されたときに**SQLPrepare**前に**SQLExecute**、 **SQLColAttribute**によって返される任意の SQLSTATE を返すことができる**SQLPrepare**または**SQLExecute**に応じて、データ ソースが SQL ステートメントに関連付けられていると評価される場合、 *StatementHandle*です。  
  
 パフォーマンス上の理由から、アプリケーションを呼び出す必要がありますいない**SQLColAttribute**ステートメントを実行する前にします。  
  
## <a name="comments"></a>コメント  
 アプリケーションがによって返される情報を使用する方法に関する情報の**SQLColAttribute**を参照してください[結果セットのメタデータ](../../../odbc/reference/develop-app/result-set-metadata.md)です。  
  
 **SQLColAttribute**か、情報を返しますで\* *NumericAttributePtr*または\* *CharacterAttributePtr*です。 整数の情報が返される\* *NumericAttributePtr* SQLLEN 値としては情報の他のすべての形式で返される\* *CharacterAttributePtr*です。 情報が返される場合\* *NumericAttributePtr*、ドライバーは無視されます*CharacterAttributePtr*、 *BufferLength*、および*StringLengthPtr*です。 情報が返される場合\* *CharacterAttributePtr*、ドライバーは無視されます*NumericAttributePtr*です。  
  
 **SQLColAttribute** IRD の記述子フィールドの値を返します。 記述子ハンドルではなく、ステートメント ハンドルで呼び出されます。 によって返される値**SQLColAttribute**の*FieldIdentifier*も呼び出すことによってこのセクションの後半に示す値を取得できます**SQLGetDescField**で、適切な IRD ハンドルです。  
  
 定義済みの記述子フィールドで導入された、およびそれらの情報が返されますの引数は、後でこのセクションで示した; ODBC のバージョンさまざまなデータ ソースを活用するためにドライバーでは、他の記述子の種類を定義できます。  
  
 ODBC 3 です。*x*ドライバーは、の各記述子フィールドの値を返す必要があります。 記述子フィールドは、ドライバーまたはデータ ソースには適用されませんし、ドライバーに 0 を返します、明記しない限り場合\* *StringLengthPtr*または空の文字列で **CharacterAttributePtr*です。  
  
## <a name="backward-compatibility"></a>旧バージョンとの互換性  
 ODBC 3 です。*x*関数**SQLColAttribute**非推奨の ODBC 2 が置き換えられます*。x*関数**SQLColAttributes**です。 マップするとき**SQLColAttributes**に**SQLColAttribute** (ときに ODBC 2 *。x* ODBC 3 を利用するアプリケーション*。x*ドライバー)、またはマッピング**SQLColAttribute**に**SQLColAttributes** (ときに ODBC 3 *。x* ODBC 2 を利用するアプリケーション*。x*ドライバー)、ドライバー マネージャーがいずれかの値を渡します*FieldIdentifier*を通じて、新しい値にマップまたは次のように、エラーが返されます。  
  
> [!NOTE]  
>  使用されるプレフィックス*FieldIdentifier* ODBC 3 の値*。x*で使用される ODBC 2 から変更されました*。x*です。 新しいプレフィックスは"SQL_DESC"です。古いプレフィックスは、"SQL_COLUMN"でした。  
  
-   場合、 **#define** ODBC 2 の値*。x* *FieldIdentifier*と同じ、 **#define** ODBC 3 の値*。x* *FieldIdentifier*、関数呼び出しで値が渡されるだけです。  
  
-   **#Define** ODBC 2 の値*。x* *FieldIdentifiers* SQL_COLUMN_LENGTH、SQL_COLUMN_PRECISION、および SQL_COLUMN_SCALE は異なる、 **#define** ODBC 3 の値*。x* *FieldIdentifiers* SQL_DESC_PRECISION、SQL_DESC_SCALE、および SQL_DESC_LENGTH です。 ODBC 2 です。*x*ドライバーでは、ODBC 2 をサポートする必要がのみ*。x*値。 ODBC 3 です。*x*ドライバーがこれら 3 つの"SQL_COLUMN"と"SQL_DESC"の両方の値をサポートする必要があります*FieldIdentifiers*です。 ODBC 3 に有効桁数、小数点以下桁数、および長さが異なる方法でに定義されるため、これらの値が異なります。*x* ODBC 2 よりも*。x*です。 詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)です。  
  
-   場合、 **#define** ODBC 2 の値*。x* *FieldIdentifier*とは異なる、 **#define** ODBC 3 の値*。x* *FieldIdentifier*、カウント、名前、としてが発生し、関数呼び出しで値、null 許容の値は、対応する値にマップします。 SQL_DESC_COUNT に SQL_COLUMN_COUNT をマップするなど、SQL_DESC_COUNT がマッピングの方向に応じて SQL_COLUMN_COUNT にマップされているとします。  
  
-   場合*FieldIdentifier* ODBC 3 内の新しい値です*。x*、これがありませんでした対応する値では、ODBC 2 のです*。x*、ODBC 3 時にマップできません*。x*アプリケーションでの呼び出しで使用**SQLColAttribute** ODBC 2 *。x*ドライバー、および呼び出しは SQLSTATE HY091 を返します (無効な記述子フィールド識別子)。  
  
 次の表に、によって返される記述子型**SQLColAttribute**です。 型は、 *NumericAttributePtr*値は**SQLLEN \***です。  
  
|*FieldIdentifier*|情報<br /><br /> 返される|Description|  
|-----------------------|---------------------------------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE (ODBC 1.0)|*NumericAttributePtr*|列が自動増分列の場合は SQL_TRUE にします。<br /><br /> 列が自動増分列でないかが数値でない場合は SQL_FALSE にします。<br /><br /> このフィールドは数値データ型の列にのみ有効です。 アプリケーションは、自動増分列を含む行に値を挿入することができますが、通常、列の値を更新することはできません。<br /><br /> Autoincrement 列に挿入が行われると、挿入時に、一意の値が列に挿入されます。 増分値は定義されていませんがデータ ソース固有です。 アプリケーションは autoincrement 列がする特定の値によって、特定の時点または単位で開始されると想定する必要があります。|  
|SQL_DESC_BASE_COLUMN_NAME (ODBC 3.0)|*CharacterAttributePtr*|結果をベースの列名は、列を設定します。 (式である列の場合) と同じベースの列名が存在しない場合、この変数は、空の文字列を格納します。<br /><br /> この情報は、IRD フィールドは読み取り専用の SQL_DESC_BASE_COLUMN_NAME レコード フィールドから返されます。|  
|SQL_DESC_BASE_TABLE_NAME (ODBC 3.0)|*CharacterAttributePtr*|列を含んだベース テーブルの名前。 ベース テーブル名は、定義することはできませんまたは適用されない場合、この変数は、空の文字列を格納します。<br /><br /> この情報は、IRD フィールドは読み取り専用の SQL_DESC_BASE_TABLE_NAME レコード フィールドから返されます。|  
|SQL_DESC_CASE_SENSITIVE (ODBC 1.0)|*NumericAttributePtr*|列は、照合順序との比較と大文字小文字を区別で扱われる場合は SQL_TRUE します。<br /><br /> 列の照合順序との比較と大文字小文字を区別は扱われませんが非文字である場合は SQL_FALSE にします。|  
|SQL_DESC_CATALOG_NAME (ODBC 2.0)|*CharacterAttributePtr*|列を含むテーブルのカタログです。 列が式の場合、または列がビューの一部である場合に、返される値は、実装定義はします。 データ ソースはカタログをサポートしていないか、カタログ名を特定することはできません、空の文字列が返されます。 この VARCHAR レコード フィールドは、128 文字に制限はありません。|  
|SQL_DESC_CONCISE_TYPE (ODBC 1.0)|*NumericAttributePtr*|簡潔なデータを入力します。<br /><br /> Datetime および時間データ型の場合は、このフィールドは、簡潔なデータ型を返します。たとえば、SQL_TYPE_TIME または SQL_INTERVAL_YEAR です。 (詳細については、次を参照してください[のデータ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)付録 d: データ型にします。)。<br /><br /> この情報は、IRD の SQL_DESC_CONCISE_TYPE レコード フィールドから返されます。|  
|SQL_DESC_COUNT (ODBC 1.0)|*NumericAttributePtr*|結果セットで使用できる列の数。 これは、結果セットの列が存在しない場合で、0 を返します。 値、 *ColumnNumber*引数は無視されます。<br /><br /> この情報は、IRD の SQL_DESC_COUNT ヘッダー フィールドから返されます。|  
|SQL_DESC_DISPLAY_SIZE (ODBC 1.0)|*NumericAttributePtr*|列からデータを表示するために必要な文字の最大数。 表示サイズの詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。|  
|SQL_DESC_FIXED_PREC_SCALE (ODBC 1.0)|*NumericAttributePtr*|列があるデータ ソース固有の固定有効桁数とスケールを 0 以外の場合は SQL_TRUE にします。<br /><br /> データ ソース固有の固定有効桁数とスケールを 0 以外に、列が持っていない場合は SQL_FALSE にします。|  
|SQL_DESC_LABEL (ODBC 2.0)|*CharacterAttributePtr*|列のラベルまたはタイトルです。 など、EmpName をという名前の列は従業員名にラベルを付けることがあります。 またはエイリアスにラベルを付けることがあります。<br /><br /> 列がラベルを持たない場合、列名が返されます。 列がラベルが付いていないし、名前のない、空の文字列が返されます。|  
|SQL_DESC_LENGTH (ODBC 3.0)|*NumericAttributePtr*|数値の値は、文字の文字列またはバイナリ データの最大値または実際の文字の長さを入力します。 これは、固定長のデータ型の最大文字数または可変長データ型の実際の文字の長さ。 常に、その値は、文字の文字列を終了する null 終了バイトを除外します。<br /><br /> この情報は、IRD の SQL_DESC_LENGTH レコード フィールドから返されます。<br /><br /> 長さの詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。|  
|SQL_DESC_LITERAL_PREFIX (ODBC 3.0)|*CharacterAttributePtr*|この varchar (128) レコードのフィールドには、ドライバーはこのデータ型のリテラルのプレフィックスとして認識される文字が含まれています。 このフィールドには、リテラル プレフィックスは適用されませんデータ型の空の文字列が含まれています。 詳細については、次を参照してください。[リテラル プレフィックスおよびサフィックス](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)です。|  
|SQL_DESC_LITERAL_SUFFIX (ODBC 3.0)|*CharacterAttributePtr*|この varchar (128) レコードのフィールドには、このデータ型のリテラルのサフィックスとして、ドライバーが認識できる文字が含まれています。 このフィールドには、空の文字列データ型のリテラル サフィックスでは適用されませんが含まれています。 詳細については、次を参照してください。[リテラル プレフィックスおよびサフィックス](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)です。|  
|SQL_DESC_LOCAL_TYPE_NAME (ODBC 3.0)|*CharacterAttributePtr*|この varchar (128) レコードのフィールドには、データ型の正規名と異なる可能性があるデータ型の任意のローカライズされた (ネイティブ言語) 名が含まれています。 ローカライズされた名前がない場合は、空の文字列が返されます。 このフィールドは、表示目的でのみです。 文字列の文字セットは、ロケールに依存するでは、通常、サーバーの既定の文字セット。|  
|SQL_DESC_NAME (ODBC 3.0)|*CharacterAttributePtr*|列の別名、適用される場合。 列の別名が適用されない場合は、列名が返されます。 どちらの場合は、SQL_DESC_UNNAMED が SQL_NAMED に設定されます。 名前のない列または列の別名がある場合、空の文字列が返され、SQL_DESC_UNNAMED がときに設定されています。<br /><br /> この情報は、IRD の SQL_DESC_NAME レコード フィールドから返されます。|  
|SQL_DESC_NULLABLE (ODBC 3.0)|*NumericAttributePtr*|Sql _ null 許容列の NULL 値であることができる場合SQL_NO_NULLS 列に NULL 値がない場合または、SQL_NULLABLE_UNKNOWN 列が NULL 値を受け入れるかどうかが不明の場合。<br /><br /> この情報は、IRD の SQL_DESC_NULLABLE レコード フィールドから返されます。|  
|SQL_DESC_NUM_PREC_RADIX (ODBC 3.0)|*NumericAttributePtr*|SQL_DESC_TYPE フィールドでのデータ型が概数データ型の場合は、この SQLINTEGER フィールドには、SQL_DESC_PRECISION フィールドには、ビットの数が含まれているために、2 の値が含まれています。 SQL_DESC_TYPE フィールドでのデータ型が真数データ型の場合は、このフィールドには、SQL_DESC_PRECISION フィールドには、10 進数字の数が含まれているために、10 の値が含まれています。 このフィールドは、すべての非数値データ型の場合は 0 に設定されます。|  
|SQL_DESC_OCTET_LENGTH (ODBC 3.0)|*NumericAttributePtr*|文字の文字列またはバイナリ データ型の長さ、(バイト単位)。 固定長文字またはバイナリ型では、これは、実際の長さ (バイト単位) です。 可変長の文字またはバイナリ型では、これは、最大長 (バイト単位) です。 この値では、終端の null は含まれません。<br /><br /> この情報は、IRD の SQL_DESC_OCTET_LENGTH レコード フィールドから返されます。<br /><br /> 長さの詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。|  
|SQL_DESC_PRECISION (ODBC 3.0)|*NumericAttributePtr*|数値データ型の適用可能な有効桁数を表す数値。 データ型のデータ型 SQL_TYPE_TIME、sql_type_timestamp 型、および時間間隔、その値を表すすべての interval データ型は、秒の小数部のコンポーネントの該当する有効桁数です。<br /><br /> この情報は、IRD の SQL_DESC_PRECISION レコード フィールドから返されます。|  
|SQL_DESC_SCALE (ODBC 3.0)|*NumericAttributePtr*|数値データ型の適用可能な小数点以下桁数を示す数値。 DECIMAL および NUMERIC データ型では、これは定義された有効桁数です。 その他のすべてのデータ型に対して定義されていることはできません。<br /><br /> この情報は、IRD の小数点以下桁数のレコード フィールドから返されます。|  
|SQL_DESC_SCHEMA_NAME (ODBC 2.0)|*CharacterAttributePtr*|列を含むテーブルのスキーマです。 列が式の場合、または列がビューの一部である場合に、返される値は、実装定義はします。 データ ソースはスキーマをサポートしていないか、スキーマ名を特定することはできません、空の文字列が返されます。 この VARCHAR レコード フィールドは、128 文字に制限はありません。|  
|SQL_DESC_SEARCHABLE (ODBC 1.0)|*NumericAttributePtr*|SQL_PRED_NONE WHERE 句で列を使用できない場合。 (これは ODBC 2 で SQL_UNSEARCHABLE 値と同じです。*x*)。<br /><br /> SQL_PRED_CHAR 場合は、列は、WHERE 句では、LIKE 述語と共にのみ使用できます。 (これは ODBC 2 で SQL_LIKE_ONLY 値と同じです。*x*)。<br /><br /> SQL_PRED_BASIC 似たを除くすべての比較演算子と共に WHERE 句で列を使用できる場合です。 (これは ODBC 2 で SQL_EXCEPT_LIKE 値と同じです。*x*)。<br /><br /> SQL_PRED_SEARCHABLE 場合は、列は、任意の比較演算子と共に WHERE 句で使用できます。<br /><br /> 列は、SQL_LONGVARCHAR と SQL_LONGVARBINARY 通常戻り SQL_PRED_CHAR を入力します。|  
|SQL_DESC_TABLE_NAME (ODBC 2.0)|*CharacterAttributePtr*|列を含むテーブルの名前です。 列が式の場合、または列がビューの一部である場合に、返される値は、実装定義はします。<br /><br /> テーブル名を特定できない場合は、空の文字列が返されます。|  
|SQL_DESC_TYPE (ODBC 3.0)|*NumericAttributePtr*|SQL データ型を指定する数値。<br /><br /> ときに*ColumnNumber*と等しいの可変長のブックマークを 0 に sql_binary 型が返され、固定長のブックマークの SQL_INTEGER が返されます。<br /><br /> Datetime および時間データ型の場合は、このフィールドは、詳細なデータ型を返します。: SQL_DATETIME または SQL_INTERVAL です。 (詳細については、次を参照してください。[のデータ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)付録 d: データ型にします。<br /><br /> この情報は、IRD の SQL_DESC_TYPE レコード フィールドから返されます。 **注:** ODBC 2 を操作する*。x*ドライバー、SQL_DESC_CONCISE_TYPE を代わりに使用します。|  
|SQL_DESC_TYPE_NAME (ODBC 1.0)|*CharacterAttributePtr*|データ ソースに依存するデータ型の名前です。たとえば、"CHAR"、"VARCHAR"、"MONEY"、"LONG VARBINARY"、または「CHAR () FOR BIT DATA」です。<br /><br /> 型が不明な場合は、空の文字列が返されます。|  
|SQL_DESC_UNNAMED (ODBC 3.0)|*NumericAttributePtr*|SQL_NAMED またはとき。 場合は、IRD の SQL_DESC_NAME フィールドには、列の別名または列の名前が含まれています、SQL_NAMED が返されます。 列名または列の別名がない場合は、ときが返されます。<br /><br /> この情報は、IRD の SQL_DESC_UNNAMED レコード フィールドから返されます。|  
|SQL_DESC_UNSIGNED (ODBC 1.0)|*NumericAttributePtr*|この列は署名されていない (または数値ではありません) の場合は SQL_TRUE にします。<br /><br /> 列が署名されている場合は SQL_FALSE にします。|  
|SQL_DESC_UPDATABLE (ODBC 1.0)|*NumericAttributePtr*|列が定義されている定数の値について説明します。<br /><br /> SQL_ATTR_READONLY SQL_ATTR_WRITE SQL_ATTR_READWRITE_UNKNOWN<br /><br /> SQL_DESC_UPDATABLE では、ベース テーブルの列ではなく、結果セット内の列の更新機能について説明します。 結果セット列の基になる基本列の更新は、このフィールドの値を異なる可能性があります。 列は更新可能であるかどうかは、データ型、ユーザー特権、および、結果セット自体の定義に基づくことができます。 明確ではない列は更新可能かどうか、SQL_ATTR_READWRITE_UNKNOWN が返されます。|  
  
 **SQLColAttribute**拡張可能な代替手段は、 **SQLDescribeCol**です。 **SQLDescribeCol** ANSI 89 SQL に基づいて記述子情報の固定セットを返します。 **SQLColAttribute**より広範な ANSI sql-92 および DBMS のベンダー拡張機能で使用できる記述子情報にアクセスできるようにします。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|複数行のデータのフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
  
## <a name="example"></a>例  
 次のサンプル コードでは、ハンドルと接続は解放されません。 参照してください[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)、[サンプル ODBC プログラム](../../../odbc/reference/sample-odbc-program.md)、および[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)ハンドルおよびステートメントを解放するコード サンプルについてはします。  
  
```  
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
   SQLPOINTER* columnLabels = (SQLPOINTER *)malloc( numColumn * sizeof(SQLPOINTER*) );  
   struct DataBinding* columnData = (struct DataBinding*)malloc( numColumn * sizeof(struct DataBinding) );  
  
   retCode = SQLNumResultCols(hstmt, &numColumn);  
  
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
