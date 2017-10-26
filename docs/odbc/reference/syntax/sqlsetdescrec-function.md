---
title: "SQLSetDescRec 関数 |Microsoft ドキュメント"
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
- SQLSetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescRec
helpviewer_keywords:
- SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b0702448c1252db57d47dfaf265c2f0b83192b3d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetdescrec-function"></a>SQLSetDescRec 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLSetDescRec**関数は、データ型に影響する複数の記述子フィールドを設定し、データの列またはパラメーターにバインドされたバッファー。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLSetDescRec(  
      SQLHDESC      DescriptorHandle,  
      SQLSMALLINT   RecNumber,  
      SQLSMALLINT   Type,  
      SQLSMALLINT   SubType,  
      SQLLEN        Length,  
      SQLSMALLINT   Precision,  
      SQLSMALLINT   Scale,  
      SQLPOINTER    DataPtr,  
      SQLLEN *      StringLengthPtr,  
      SQLLEN *      IndicatorPtr);  
```  
  
## <a name="arguments"></a>引数  
 *DescriptorHandle*  
 [入力]記述子ハンドルです。 IRD ハンドルは指定できません。  
  
 *RecNumber*  
 [入力]記述子レコードを設定するフィールドを含んでいることを示します。 記述子レコードは、レコード番号 0 のブックマーク レコードの中で、0 から番号が付けられます。 この引数は、0 以上にする必要があります。 場合*RecNumber* SQL_DESC_COUNT、SQL_DESC_COUNTis の値に変更の値よりも大きい*RecNumber*です。  
  
 *型*  
 [入力]記述子レコードの SQL_DESC_TYPE フィールドを設定する値です。  
  
 *サブタイプ*  
 [入力]型を持つが SQL_DATETIME または SQL_INTERVAL のレコード、これに SQL_DESC_DATETIME_INTERVAL_CODE フィールドを設定する値です。  
  
 *長さ*  
 [入力]記述子レコードの SQL_DESC_OCTET_LENGTH フィールドを設定する値です。  
  
 *有効桁数*  
 [入力]記述子レコードの SQL_DESC_PRECISION フィールドを設定する値です。  
  
 *Scale*  
 [入力]記述子レコードの SQL_DESC_SCALE フィールドを設定する値です。  
  
 *DataPtr*  
 [遅延の入力または出力]記述子レコードの SQL_DESC_DATA_PTR フィールドを設定する値です。 *DataPtr* null ポインターを設定することができます。  
  
 *DataPtr*引数は、SQL_DESC_DATA_PTR フィールドに null ポインターを設定に null ポインターを設定することができます。 場合のハンドル、 *DescriptorHandle*引数が、ARD に関連付けられた、この列をバインド解除します。  
  
 *StringLengthPtr*  
 [遅延の入力または出力]記述子レコードの SQL_DESC_OCTET_LENGTH_PTR フィールドを設定する値です。 *StringLengthPtr* SQL_DESC_OCTET_LENGTH_PTR フィールドを null ポインターを設定する null ポインターを設定することができます。  
  
 *IndicatorPtr*  
 [遅延の入力または出力]記述子レコードの SQL_DESC_INDICATOR_PTR フィールドを設定する値です。 *IndicatorPtr*フィールドを設定、SQL_DESC_INDICATOR_PTR null ポインターに null ポインターを設定できます。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetDescRec** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_DESC と*処理*の*DescriptorHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLSetDescRec**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07009|無効な記述子のインデックス|*RecNumber*引数が 0 に設定して、 *DescriptorHandle* IPD ハンドルと呼ばれます。<br /><br /> *RecNumber*引数が 0 未満です。<br /><br /> *RecNumber*引数が列またはデータ ソースをサポートできますが、パラメーターの最大数よりも大きかったと*DescriptorHandle*因数が APD、IPD、または ARD でした。<br /><br /> *RecNumber*引数が 0 に等しいと*DescriptorHandle*引数が暗黙的に割り当てられた APD と呼びます。 (このエラーは発生しません明示的に割り当てられているアプリケーション記述子を使用して実行時間を明示的に割り当てられているアプリケーション記述子が APD またはまで ARD かどうかが不明なためです)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 * \*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、 *DescriptorHandle*が関連付けられて、 *StatementHandle*非同期的に実行中の関数 (いないこの 1 つ) が呼び出されたおよびこの関数が呼び出されたときに実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle*いる、 *DescriptorHandle*が関連付けられているし、SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *DescriptorHandle*です。 この非同期関数がまだ実行したときに、 **SQLSetDescRec**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかで呼び出され、 *DescriptorHandle* SQL_PARAM_DATA_AVAILABLE を返されるとします。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY016|実装行記述子は変更できません。|*DescriptorHandle*引数が、IRD に関連付けられました。|  
|HY021|不整合な記述子情報|*型*フィールド、または、記述子の SQL_DESC_TYPE フィールドに関連付けられた、他のフィールドが無効であるか、一貫性のあります。<br /><br /> 整合性チェック中にチェック記述子の情報が一致していません。 (「一貫性チェック、」このセクションの後半を参照してください)。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) ドライバーは ODBC 2*.x*ドライバー、記述子が、ARD、 *ColumnNumber*引数が 0 であり、引数に指定された値に設定された*BufferLength*されました4 に等しくないです。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *DescriptorHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 アプリケーションが呼び出すことができます**SQLSetDescRec**を 1 つの列またはパラメーターに対して、次のフィールドを設定します。  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (の型を持つが SQL_DATETIME または SQL_INTERVAL レコード)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  呼び出し**SQLSetDescRec**で識別される記述子レコードの内容が失敗した、 *RecNumber*引数が定義されていません。  
  
 列またはパラメーターをバインドするときに**SQLSetDescRec**呼び出さずに、バインドに影響する複数のフィールドを変更することができます**SQLBindCol**または**SQLBindParameter**または複数の呼び出しを行う**SQLSetDescField**です。 **SQLSetDescRec**されていないステートメントに関連付けられた、記述子のフィールドを設定することができます。 なお**SQLBindParameter**より多くのフィールドを設定**SQLSetDescRec**APD と 1 つの呼び出しで、IPD の両方のフィールドを設定することができます、および記述子ハンドルは必要ありません。  
  
> [!NOTE]  
>  ステートメント属性 SQL_ATTR_USE_BOOKMARKS は常に設定する呼び出しの前に**SQLSetDescRec**で、 *RecNumber*ブックマークのフィールドを設定する場合は 0 の引数。 これは必須ではなく、中に強くお勧めします。  
  
## <a name="consistency-checks"></a>整合性チェック  
 アプリケーションが、ARD、または IPD APD の SQL_DESC_DATA_PTR フィールドを設定するたびに、整合性チェックは、ドライバーによって自動的に実行します。 他のフィールドと一貫性のある任意のフィールドがない場合**SQLSetDescRec** SQLSTATE HY021 が返されます (不整合な記述子情報)。  
  
 アプリケーションが、ARD、または IPD APD の SQL_DESC_DATA_PTR フィールドを設定するたびに、SQL_DESC_TYPE フィールドの値との SQL_DESC_TYPE フィールドに適用可能な値が有効と一貫性があるドライバーを確認します。 このチェックは、常に際に実行**SQLBindParameter**または**SQLBindCol**が呼び出された場合や**SQLSetDescRec** APD、ARD、または IPD と呼びます。 この一貫性チェックには、記述子フィールドに対しては、次のチェックが含まれています。  
  
-   SQL_DESC_TYPE フィールドは、有効な ODBC C または SQL 型またはドライバー固有の SQL 型のいずれかにする必要があります。 SQL_DESC_CONCISE_TYPE フィールドは、有効な ODBC C または SQL 型または簡潔な日時および間隔の種類など、個々 のドライバーの C または SQL 型のいずれかにする必要があります。  
  
-   レコードの SQL_DESC_TYPE フィールドが SQL_DATETIME または SQL_INTERVAL の場合は、SQL_DESC_DATETIME_INTERVAL_CODE フィールドは有効な日付型または interval コードのいずれかをする必要があります。 (SQL_DESC_DATETIME_INTERVAL_CODE のフィールドの説明を参照して[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md))。  
  
-   SQL_DESC_TYPE フィールドには、数値型が示されている場合は、有効である、SQL_DESC_PRECISION および SQL_DESC_SCALE フィールドが検証されます。  
  
-   SQL_DESC_CONCISE_TYPE フィールドが、時間またはタイムスタンプ データ型の場合は、間隔を入力秒の部分または時刻部分、interval データ型のいずれかで SQL_DESC_PRECISION フィールドが検証済み有効秒の有効桁数にします。  
  
-   SQL_DESC_CONCISE_TYPE が interval データ型の場合は、有効な間隔の先頭の有効桁数値であること、SQL_DESC_DATETIME_INTERVAL_PRECISION フィールドが検証されます。  
  
 通常、IPD の SQL_DESC_DATA_PTR フィールドを設定がないです。ただし、アプリケーションでは、IPD フィールドの整合性チェックを強制的に行うことができます。 整合性チェックは、IRD では実行できません。 IPD の SQL_DESC_DATA_PTR フィールドに設定する値が実際に格納されていないとへの呼び出しによって取得することはできません**SQLGetDescField**または**SQLGetDescRec**; のみを強制的には、設定、整合性チェックです。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|列のバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|パラメーターのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|1 つの記述子フィールドの取得|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|複数の記述子フィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|1 つの記述子フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

