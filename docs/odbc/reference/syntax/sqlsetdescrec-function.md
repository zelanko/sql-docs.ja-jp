---
title: SQLSetDescRec 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3a733c2b88954c9937e8a170b949535ffa118bad
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039735"
---
# <a name="sqlsetdescrec-function"></a>SQLSetDescRec 関数
**準拠**  
 バージョンが導入されました。ODBC 3.0 規格に準拠します。ISO 92  
  
 **概要**  
 **SQLSetDescRec**関数は、データ型に影響する複数の記述子フィールドを設定し、データの列またはパラメーターにバインドされたバッファー。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 [入力]記述子ハンドル。 IRD ハンドルとがあります。  
  
 *RecNumber*  
 [入力]記述子のレコードを設定するフィールドが含まれることを示します。 記述子のレコードは、レコード番号 0 ブックマーク レコードの中で、0 から番号が付けられます。 この引数は、0 以上である必要があります。 場合*RecNumber* SQL_DESC_COUNT、SQL_DESC_COUNTis の値に変更の値よりも大きい*RecNumber*します。  
  
 *型*  
 [入力]記述子のレコードの SQL_DESC_TYPE フィールドを設定する値。  
  
 *SubType*  
 [入力]レコード型を持つが SQL_DATETIME または SQL_INTERVAL の SQL_DESC_DATETIME_INTERVAL_CODE フィールドを設定する値になります。  
  
 *Length*  
 [入力]記述子のレコードの SQL_DESC_OCTET_LENGTH フィールドを設定する値。  
  
 *Precision*  
 [入力]記述子のレコードの SQL_DESC_PRECISION フィールドを設定する値。  
  
 *Scale*  
 [入力]記述子のレコードの SQL_DESC_SCALE フィールドを設定する値。  
  
 *DataPtr*  
 [遅延の入力または出力]記述子のレコードの SQL_DESC_DATA_PTR フィールドを設定する値。 *DataPtr* null ポインターを設定することができます。  
  
 *DataPtr*引数は、SQL_DESC_DATA_PTR フィールドに null ポインターを設定に null ポインターを設定することができます。 場合のハンドル、 *DescriptorHandle*引数は、ARD に関連付け、これは、列をバインド解除します。  
  
 *StringLengthPtr*  
 [遅延の入力または出力]記述子のレコードの SQL_DESC_OCTET_LENGTH_PTR フィールドを設定する値。 *StringLengthPtr* SQL_DESC_OCTET_LENGTH_PTR フィールドに null ポインターを設定に null ポインターを設定することができます。  
  
 *IndicatorPtr*  
 [遅延の入力または出力]記述子のレコードの SQL_DESC_INDICATOR_PTR フィールドを設定する値。 *IndicatorPtr* SQL_DESC_INDICATOR_PTR フィールドに null ポインターを設定に null ポインターを設定することができます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetDescRec** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_DESC と*処理*の*DescriptorHandle*します。 次の表に、一般的にによって返される SQLSTATE 値**SQLSetDescRec** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07009|無効な記述子のインデックス|*RecNumber*引数が 0 に設定された、 *DescriptorHandle* IPD ハンドルと呼ばれます。<br /><br /> *RecNumber*引数が 0 未満でした。<br /><br /> *RecNumber*引数が列またはデータ ソースをサポートできますが、パラメーターの最大数よりも大きいと*DescriptorHandle*引数が APD、IPD、または ARD します。<br /><br /> *RecNumber*引数が 0 に等しいと*DescriptorHandle*引数は、暗黙的に割り当てられた APD 呼ばれます。 (このエラーは発生しません、明示的に割り当てられたアプリケーション記述子を使用して実行時間を明示的に割り当てられたアプリケーション記述子を APD またはまで ARD かどうかが不明ためです)。|  
|08S01|通信リンク エラー|関数が完了した処理の前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクに失敗しました。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、 *DescriptorHandle*に関連付けられているが、 *StatementHandle*に (このない) 非同期的に実行中の関数が呼び出されたこの関数が呼び出されたときに実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle*られて、 *DescriptorHandle*が関連付けられているし、SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *DescriptorHandle*します。 この非同期関数ではときに実行されている、 **SQLSetDescRec**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかが呼び出された、 *DescriptorHandle* SQL_PARAM_DATA_AVAILABLE が返されます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY016|実装行記述子は変更できません。|*DescriptorHandle*引数は、IRD に関連付けられていました。|  
|HY021|不整合な記述子情報|*型*フィールド、または、記述子の SQL_DESC_TYPE フィールドに関連付けられているその他の任意のフィールドが無効であるか、一貫性のあります。<br /><br /> 整合性チェック中にチェック記述子の情報は、一貫性のあるでした。 ("整合性チェックをこのセクションの後半を参照してください)。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM)、ドライバーは ODBC *2.x*ドライバー、記述子が、ARD、 *ColumnNumber*引数が 0、および引数が指定された値に設定された*BufferLength*されました4 と等しくありません。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *DescriptorHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 アプリケーションが呼び出すことができます**SQLSetDescRec**を 1 つの列またはパラメーターの次のフィールドを設定します。  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (の型を持つが SQL_DATETIME または SQL_INTERVAL レコード)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  呼び出し**SQLSetDescRec**で識別される記述子レコードの内容は、失敗、 *RecNumber*引数が定義されていません。  
  
 列またはパラメーターをバインドするときに**SQLSetDescRec**呼び出さずに、バインドに影響を与える複数のフィールドを変更することができます**SQLBindCol**または**SQLBindParameter**または複数の呼び出しを行う**SQLSetDescField**します。 **SQLSetDescRec**ステートメントに関連付けられているない記述子でフィールドを設定することができます。 なお**SQLBindParameter**より多くのフィールドを設定**SQLSetDescRec**APD と、IPD で 1 回の呼び出しの両方でフィールドを設定することや、記述子ハンドルは必要ありません。  
  
> [!NOTE]  
>  ステートメント属性 SQL_ATTR_USE_BOOKMARKS は常に設定する呼び出しの前に**SQLSetDescRec**で、 *RecNumber*ブックマークのフィールドを設定するには 0 の引数。 これは必須ではありません、中に強くお勧めします。  
  
## <a name="consistency-checks"></a>整合性チェック  
 アプリケーションが、ARD、または IPD APD の SQL_DESC_DATA_PTR フィールドを設定するたびに、整合性チェックがドライバーによって自動的に実行されます。 任意のフィールドが、他のフィールドと一致しない場合**SQLSetDescRec** SQLSTATE HY021 が返されます (不整合な記述子情報)。  
  
 アプリケーションが、ARD、または IPD APD の SQL_DESC_DATA_PTR フィールドを設定するたびに、SQL_DESC_TYPE フィールドの値とその SQL_DESC_TYPE フィールドに適用可能な値が有効であり、一貫性のあるドライバーを確認します。 このチェックは常に際に実行**SQLBindParameter**または**SQLBindCol**と呼びますか**SQLSetDescRec** APD、ARD、または IPD と呼びます。 この整合性チェックには、記述子フィールドについては、次のチェックが含まれています。  
  
-   SQL_DESC_TYPE フィールドは、有効な ODBC C または SQL 型、またはドライバー固有の SQL 型のいずれかを指定する必要があります。 SQL_DESC_CONCISE_TYPE フィールドには、有効な ODBC C または SQL 型または簡潔な datetime と間隔の種類など、個々 のドライバーの C または SQL 型のいずれかを指定する必要があります。  
  
-   SQL_DESC_TYPE レコードのフィールドが SQL_DATETIME または SQL_INTERVAL の場合は、SQL_DESC_DATETIME_INTERVAL_CODE フィールドは、有効な datetime 間隔コードのいずれかを指定する必要があります。 (SQL_DESC_DATETIME_INTERVAL_CODE のフィールドの説明を参照して[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md))。  
  
-   SQL_DESC_TYPE フィールドには、数値型が示されている場合は、有効である、SQL_DESC_PRECISION および SQL_DESC_SCALE フィールドが検証されます。  
  
-   SQL_DESC_CONCISE_TYPE フィールドが、時間またはタイムスタンプ データ型の場合は、間隔の種類を秒の部分または時刻のコンポーネントを含む interval データ型のいずれかの SQL_DESC_PRECISION フィールドを検証する有効な秒の有効桁数。  
  
-   SQL_DESC_CONCISE_TYPE が間隔のデータ型の場合は、SQL_DESC_DATETIME_INTERVAL_PRECISION フィールドは先頭有効桁数の有効期間値にすることを確認します。  
  
 IPD の SQL_DESC_DATA_PTR フィールドが正常に設定されていません。ただし、アプリケーションは、IPD フィールドの整合性チェックを強制するために行うことができます。 整合性チェックは、IRD では実行できません。 IPD の SQL_DESC_DATA_PTR フィールドに設定されている値が実際に保存されていないとへの呼び出しで取得することはできません**SQLGetDescField**または**SQLGetDescRec**; のみを強制的には、設定、整合性チェックです。  
  
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
