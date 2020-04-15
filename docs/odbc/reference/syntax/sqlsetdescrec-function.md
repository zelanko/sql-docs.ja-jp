---
title: 関数の設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetDescRec
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescRec
helpviewer_keywords:
- SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b29879ff7635d6eb7d5a0f7489ff3994758d4a35
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299532"
---
# <a name="sqlsetdescrec-function"></a>SQLSetDescRec 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLSetDescRec**関数は、列またはパラメーターのデータにバインドされたデータ型とバッファーに影響を与える複数の記述子フィールドを設定します。  
  
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
 [入力]記述子ハンドル。 これは IRD ハンドルであってはなりません。  
  
 *RecNumber*  
 [入力]設定するフィールドを含む記述子レコードを示します。 記述子レコードには 0 から番号が付けられ、レコード番号 0 はブックマーク・レコードになります。 この引数は 0 以上である必要があります。 *RecNumber*が SQL_DESC_COUNT の値より大きい場合、SQL_DESC_COUNTisは*RecNumber*の値に変更されます。  
  
 *Type*  
 [入力]記述子レコードのSQL_DESC_TYPEフィールドを設定する値。  
  
 *サブタイプ*  
 [入力]タイプがSQL_DATETIMEまたはSQL_INTERVALのレコードの場合、これはSQL_DESC_DATETIME_INTERVAL_CODEフィールドを設定する値です。  
  
 *長さ*  
 [入力]記述子レコードのSQL_DESC_OCTET_LENGTHフィールドを設定する値。  
  
 *有効桁数*  
 [入力]記述子レコードのSQL_DESC_PRECISION フィールドを設定する値。  
  
 *スケール*  
 [入力]記述子レコードのSQL_DESC_SCALEフィールドを設定する値。  
  
 *データプラー*  
 [遅延入力または出力]記述子レコードのSQL_DESC_DATA_PTRフィールドを設定する値。 *DataPtr*は、null ポインターに設定できます。  
  
 *DataPtr*引数を null ポインターに設定すると、SQL_DESC_DATA_PTRフィールドを null ポインターに設定できます。 *引数 DescriptorHandle*のハンドルが ARD に関連付けられている場合、これは列のバインドを解除します。  
  
 *文字列を長くします。*  
 [遅延入力または出力]記述子レコードのSQL_DESC_OCTET_LENGTH_PTRフィールドを設定する値。 *StringLengthPtr*を null ポインターに設定すると、SQL_DESC_OCTET_LENGTH_PTRフィールドを null ポインターに設定できます。  
  
 *インジケータPtr*  
 [遅延入力または出力]記述子レコードのSQL_DESC_INDICATOR_PTRフィールドを設定する値。 *IndicatorPtr*を null ポインターに設定して、SQL_DESC_INDICATOR_PTRフィールドを null ポインターに設定できます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLSetDescRec**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときに、SQL_HANDLE_DESCの*ハンドル型*と*記述子ハンドル*を使用して**SQLGetDiagRec***を呼*び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLSetDescRec**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07009|記述子インデックスが無効です|*引数 RecNumber*が 0 に設定され、*記述子ハンドル*が IPD ハンドルを参照しました。<br /><br /> *引数が*0 未満でした。<br /><br /> *RecNumber*引数は、データ ソースがサポートできる列またはパラメーターの最大数を超えており、引数*DescriptorHandle*は APD、IPD、または ARD でした。<br /><br /> *RecNumber*引数は 0 と等しく、*引数は*暗黙的に割り当てられた APD を参照しました。 (このエラーは、明示的に割り当てられたアプリケーション記述子が、実行時間まで APD か ARD かは不明であるため、明示的に割り当てられたアプリケーション記述子では発生しません。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM) *DescriptorHandle*は、非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていた*ステートメント ハンドル*に関連付けられていた。<br /><br /> (DM) 記述子ハンドルが関連付けられ、SQL_NEED_DATA返された*ステートメント ハンドル*に対して **、SQL 実行****、SQLExecDirect、SQLBulkOperations**、または**SQLSetPos**が呼び出されました。 **SQLExecDirect** *DescriptorHandle* この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM)*記述子ハンドル*に関連付けられている接続ハンドルに対して非同期に実行する関数が呼び出されました。 この aynchronous 関数は **、SQLSetDescRec**関数が呼び出されたときに実行されていました。<br /><br /> (DM) 記述子*ハンドル*に関連付けられているステートメント ハンドルの 1 つに対して **、SQL 実行** **、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY016|実装行記述子を変更できません|引数*が*IRD に関連付けられていた。|  
|HY021|記述子情報の不一致|*Type*フィールド、または記述子のSQL_DESC_TYPEフィールドに関連付けられたその他のフィールドが、有効または一貫性がありませんでした。<br /><br /> 整合性チェック中にチェックされた記述子情報が一貫していません。 (後の「整合性チェック」を参照してください)。|  
|HY090|無効な文字列またはバッファ長|(DM) ドライバーは ODBC *2.x*ドライバー、記述子は*ARD、ColumnNumber*引数は 0 に設定され、引数*BufferLength*に指定された値が 4 に等しめなかった。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*記述子ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 アプリケーションは **、SQLSetDescRec**を呼び出して、単一の列またはパラメーターに対して次のフィールドを設定できます。  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (タイプがSQL_DATETIMEまたはSQL_INTERVALのレコードの場合)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  **SQLSetDescRec**の呼び出しが失敗した場合 *、RecNumber*引数によって識別される記述子レコードの内容は未定義です。  
  
 列またはパラメーターをバインドする場合、 **SQLSetDescRec**を使用すると、 **SQLBindCol または SQLBindParameter**を呼び出したり **、SQLSetDescField**を複数回呼び出したりすることなく、バインディングに影響を与える複数のフィールドを変更できます。 **SQLBindParameter** **SQLSetDescRec**は、現在ステートメントに関連付けられていない記述子にフィールドを設定できます。 **SQLBindParameter は** **SQLSetDescRec**よりも多くのフィールドを設定し、1 回の呼び出しで APD と IPD の両方にフィールドを設定でき、記述子ハンドルは必要ありません。  
  
> [!NOTE]  
>  ステートメント属性SQL_ATTR_USE_BOOKMARKSは、ブックマーク フィールドを設定するために *、RecNumber*引数 0 を指定して**SQLSetDescRec**を呼び出す前に、常に設定する必要があります。 必須ではありませんが、強くお勧めします。  
  
## <a name="consistency-checks"></a>整合性チェック  
 アプリケーションが APD、ARD、または IPD のSQL_DESC_DATA_PTRフィールドを設定するたびに、ドライバーによって整合性チェックが自動的に実行されます。 いずれかのフィールドが他のフィールドと矛盾している場合 **、SQLSetDescRec**は SQLSTATE HY021 (不整合な記述子情報) を返します。  
  
 アプリケーションが APD、ARD、または IPD のSQL_DESC_DATA_PTR フィールドを設定すると、ドライバーは、SQL_DESC_TYPE フィールドの値と、そのSQL_DESC_TYPEフィールドに適用される値が有効で一貫性があることを確認します。 このチェックは、常に **、SQLBindParameter**または**SQLBindCol**が呼び出されたとき、または APD、ARD、または IPD に対して**SQLSetDescRec**が呼び出されたときに実行されます。 この整合性チェックには、記述子フィールドに対する以下の検査が含まれます。  
  
-   SQL_DESC_TYPE フィールドは、有効な ODBC C 型または SQL 型、またはドライバー固有の SQL 型のいずれかである必要があります。 SQL_DESC_CONCISE_TYPE フィールドは、有効な ODBC C 型または SQL 型、またはドライバー固有の C 型または SQL 型 (簡潔な日時型と間隔の型を含む) のいずれかである必要があります。  
  
-   SQL_DESC_TYPEレコード・フィールドがSQL_DATETIMEまたはSQL_INTERVALの場合、SQL_DESC_DATETIME_INTERVAL_CODEフィールドは有効な日時コードまたは間隔コードのいずれかでなければなりません。 [(SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)のSQL_DESC_DATETIME_INTERVAL_CODE フィールドの説明を参照してください。  
  
-   SQL_DESC_TYPEフィールドが数値型を示している場合、SQL_DESC_PRECISIONとSQL_DESC_SCALEフィールドは有効であることが確認されます。  
  
-   SQL_DESC_CONCISE_TYPE フィールドが時刻またはタイム・スタンプのデータ・タイプ、秒コンポーネントを持つ間隔タイプ、または時間コンポーネントを持ついずれかの間隔データ・タイプである場合、SQL_DESC_PRECISIONフィールドは有効な秒精度であることが検証されます。  
  
-   SQL_DESC_CONCISE_TYPEが間隔データ・タイプである場合、SQL_DESC_DATETIME_INTERVAL_PRECISION フィールドは有効な間隔先行精度値であることが検査されます。  
  
 IPD のSQL_DESC_DATA_PTRフィールドは、通常は設定されません。ただし、アプリケーションは IPD フィールドの整合性チェックを強制するためにこれを行うことができます。 整合性チェックは、IRD では実行できません。 IPD のSQL_DESC_DATA_PTRフィールドが設定されている値は実際には格納されず **、SQLGetDescField**または**SQLGetDescRec**の呼び出しでは取得できません。この設定は、整合性チェックを強制するためだけに行われます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|列のバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|パラメーターのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|単一の記述子フィールドの取得|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|複数の記述子フィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|単一記述子フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
