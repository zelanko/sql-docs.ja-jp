---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSources
helpviewer_keywords:
- SQLDataSources function [ODBC]
ms.assetid: 3f63b1b4-e70e-44cd-96c6-6878d50d0117
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b56a6c25e54897e67beaf39d3b7797ac45391d7b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301182"
---
# <a name="sqldatasources-function"></a>SQLDataSources 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **データ ソースに**関する情報を返します。 この関数は、ドライバー マネージャーによってのみ実装されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLDataSources(  
     SQLHENV          EnvironmentHandle,  
     SQLUSMALLINT     Direction,  
     SQLCHAR *        ServerName,  
     SQLSMALLINT      BufferLength1,  
     SQLSMALLINT *    NameLength1Ptr,  
     SQLCHAR *        Description,  
     SQLSMALLINT      BufferLength2,  
     SQLSMALLINT *    NameLength2Ptr);  
```  
  
## <a name="arguments"></a>引数  
 *環境ハンドル*  
 [入力]環境ハンドル。  
  
 *方向*  
 [入力]ドライバー マネージャーが情報を返すデータ ソースを決定します。 次の値をとります。  
  
 SQL_FETCH_NEXT (リスト内の次のデータ・ソース名をフェッチする)、SQL_FETCH_FIRST (リストの先頭からフェッチする)、SQL_FETCH_FIRST_USER (最初のユーザー DSN をフェッチする)、またはSQL_FETCH_FIRST_SYSTEM (最初のシステム DSN をフェッチする) 。  
  
 *方向*が SQL_FETCH_FIRST に設定されている場合、後続の**SQLDataSources**への呼び出しでは *、ユーザー*とシステム DSN の両方が返SQL_FETCH_NEXT方向が設定されます。 *[方向]* を SQL_FETCH_FIRST_USER に設定すると、その後の [*方向]* が設定された**SQLDataSources**へのすべての呼び出しが、ユーザー DSN のみを返SQL_FETCH_NEXT。 *方向*がSQL_FETCH_FIRST_SYSTEMに設定されている場合、その後の**SQLDataSources**へのすべての呼び出しは *、システム*DSN のみを返すSQL_FETCH_NEXTに設定された方向を持ちます。  
  
 *ServerName*  
 [出力]データ ソース名を返すバッファーへのポインター。  
  
 *サーバー名が*NULL の場合 *、NameLength1Ptr*は *、ServerName*によって指されているバッファーで返される使用可能な文字の合計数 (文字データの NULL 終端文字を除く) を返します。  
  
 *バッファ長1*  
 [入力]**サーバー名*バッファーの長さ (文字数)。これは、SQL_MAX_DSN_LENGTH + ヌル終了文字より長くする必要はありません。  
  
 *名前長1Ptr*  
 [出力]\* *ServerName*で返される文字の合計数 (NULL 終端文字を除く) を返すバッファーへのポインター。 返される文字の数が*BufferLength1*以上の場合、\**サーバー名*のデータ ソース名は*BufferLength1*から NULL 終端文字の長さを引いた値に切り捨てられます。  
  
 *説明*  
 [出力]データ ソースに関連付けられているドライバーの説明を返すバッファーへのポインター。 たとえば、dBASE や SQL サーバーなどです。  
  
 *説明*が NULL の場合 *、NameLength2Ptr*は*Description*が指すバッファーで返される文字の合計数 (文字データの NULL 終端文字を除く) を返します。  
  
 *バッファ長2*  
 [入力]* 記述バッファーの文字数で*表*された長さ。  
  
 *名前長2Ptr*  
 [出力]\* *Description*に返される文字の合計数 (NULL 終端文字を除く) を返すバッファーへのポインター。 返される文字の数が*BufferLength2*以上の場合、\**説明*のドライバーの説明は*BufferLength2*から null 終端文字の長さを引いた値に切り捨てられます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLDataSources**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_ENVの*ハンドル型*と*環境ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は、SQL データソースによって返される**SQLSTATE**値を一覧し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|(DM) ドライバー マネージャー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|(DM) バッファ\**サーバー名*が、完全なデータ ソース名を返すのに十分な大きさではありませんでした。 したがって、名前は切り捨てられました。 データ ソース名全体の長さは、 \* *NameLength1Ptr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。<br /><br /> (DM) バッファー\*の*説明*は、完全なドライバーの説明を返すのに十分な大きさではありませんでした。 そのため、説明は切り捨てられました。 切り捨てられていないデータ ソースの説明の長さは、 **NameLength2Ptr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|HY000|一般的なエラー|(DM) 特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|(DM) ドライバー マネージャーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*BufferLength1*に指定された値が 0 未満でした。<br /><br /> (DM) 引数*BufferLength2*に指定された値が 0 未満でした。|  
|HY103|無効な取得コード|(DM)*引数 Direction*に指定された値が、SQL_FETCH_FIRST、SQL_FETCH_FIRST_USER、SQL_FETCH_FIRST_SYSTEM、またはSQL_FETCH_NEXTと等しくありません。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
  
## <a name="comments"></a>説明  
 **SQLDataSources**はドライバー マネージャーで実装されるため、ドライバーの標準に準拠する特定のドライバーに関係なくすべてのドライバーでサポートされています。  
  
 アプリケーションは **、SQLDataSources を**複数回呼び出して、すべてのデータ ソース名を取得できます。 ドライバー マネージャーは、システム情報からこの情報を取得します。 これ以上データ ソース名がない場合、ドライバー マネージャーはSQL_NO_DATAを返します。 **SQLDataSources**がSQL_NO_DATAを返した直後にSQL_FETCH_NEXTを指定して呼び出された場合、最初のデータ ソース名が返されます。 アプリケーションが**SQLDataSources**によって返される情報をどのように使用するかについては、「[データ ソースまたはドライバの選択](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)」を参照してください。  
  
 SQL_FETCH_NEXTが最初に呼び出された時に**SQLDataSources**に渡された場合、最初のデータ ソース名が返されます。  
  
 ドライバーは、データ ソース名が実際のデータ ソースにマップされる方法を決定します。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースへの接続に必要な値の検出と一覧表示|[SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|接続文字列またはダイアログ ボックスを使用したデータ ソースへの接続|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|ドライバーの説明と属性を返す|[SQLDrivers 関数](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
