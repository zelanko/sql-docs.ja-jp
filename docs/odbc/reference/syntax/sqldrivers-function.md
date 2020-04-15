---
title: SQL ドライバ関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDrivers
helpviewer_keywords:
- SQLDrivers function [ODBC]
ms.assetid: 6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2496e7cd5f2abe0831c72484bed374d7aa1513ce
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302763"
---
# <a name="sqldrivers-function"></a>SQLDrivers 関数
**適合 性**  
 バージョン導入: ODBC 2.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQLDrivers は、ドライバーの**説明とドライバー属性キーワードを一覧表示します。 この関数は、ドライバー マネージャーによってのみ実装されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLDrivers(  
     SQLHENV         EnvironmentHandle,  
     SQLUSMALLINT    Direction,  
     SQLCHAR *       DriverDescription,  
     SQLSMALLINT     BufferLength1,  
     SQLSMALLINT *   DescriptionLengthPtr,  
     SQLCHAR *       DriverAttributes,  
     SQLSMALLINT     BufferLength2,  
     SQLSMALLINT *   AttributesLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *環境ハンドル*  
 [入力]環境ハンドル。  
  
 *方向*  
 [入力]ドライバー マネージャーは、一覧 (SQL_FETCH_NEXT) 内の次のドライバーの説明をフェッチするか、または検索が一覧の先頭から開始 (SQL_FETCH_FIRST) かどうかを決定します。  
  
 *DriverDescription*  
 [出力]ドライバーの説明を返すバッファーへのポインター。  
  
 *DriverDescription*が NULL の場合 *、DescriptionLengthPtr*は、*ドライバー説明*によって指されるバッファーで返される使用可能な文字の合計数 (文字データの null 終端文字を除く) を返します。  
  
 *バッファ長1*  
 [入力]**ドライバ記述*バッファの長さ(文字数)。  
  
 *説明長Ptr*  
 [出力]\* *DriverDescription*で返される文字の合計数 (NULL 終端文字を除く) を返すバッファーへのポインター。 返される文字の数が*BufferLength1*以上の場合、\**ドライバーの説明は**、BufferLength1*から null 終端文字の長さを引いた値に切り捨てられます。  
  
 *ドライバー属性*  
 [出力]ドライバー属性値のペアの一覧を返すバッファーへのポインター (「コメント」を参照)。  
  
 *DriverAttributes が*NULL の場合 *、AttributesLengthPtr*は *、DriverAttributes*によって指されるバッファーで返される使用可能なバイトの合計数 (文字データの null 終端文字を除く) を返します。  
  
 *バッファ長2*  
 [入力]\**文字で、ドライバー属性*バッファーの長さ。 *\*値*が Unicode 文字列の場合 **(SQLDriversW**を呼び出すとき)、BufferLength 引数は偶数である必要があります。 *BufferLength*  
  
 *属性の長さPtr*  
 [出力]\* *DriverAttributes*で返されるバイトの総数 (null 終了バイトを除く) を返すバッファーへのポインター。 返されるバイト数が*BufferLength2*以上の場合\**、DriverAttributes*の属性値ペアのリストは *、BufferLength2*から null 終端文字の長さを引いた値に切り捨てられます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLDrivers が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_ENVの*ハンドル型*と*環境ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLDrivers**によって返される SQLSTATE 値を一覧表示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|(DM) ドライバー マネージャー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|(DM) バッファー\**ドライバーの説明*は、完全なドライバーの説明を返すのに十分な大きさではありませんでした。 そのため、説明は切り捨てられました。 完全なドライバーの説明の長さは、 \* *DescriptionLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。<br /><br /> (DM) バッファー \* *DriverAttributes*は、属性値ペアの完全なリストを返すのに十分な大きさではありませんでした。 したがって、リストは切り捨てられました。 属性値ペアの切り捨てられていないリストの長さは、 **AttributesLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|(DM) ドライバー マネージャーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*BufferLength1*に指定された値が 0 未満でした。<br /><br /> (DM) 引数*BufferLength2*に指定された値が 0 未満または 1 に等しい。|  
|HY103|無効な取得コード|(DM)*引数 Direction*に指定された値が、SQL_FETCH_FIRSTまたはSQL_FETCH_NEXTと等しくありません。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
  
## <a name="comments"></a>説明  
 **SQL ドライバーは、** ドライバー\**の説明*バッファーにドライバーの説明を返します。 キーワードと値のペアの一覧として\* *DriverAttributes*バッファー内のドライバーに関する追加情報を返します。 ドライバーのシステム情報にリストされているすべてのキーワードは、データ ソースの作成を要求するために使用される**CreateDSN**を除くすべてのドライバーに対して返されます。 各ペアはヌルバイトで終了し、完全なリストはヌルバイトで終了します(つまり、2つのNULLバイトがリストの終わりを示します)。 たとえば、C 構文を使用するファイル ベースのドライバーは、次の属性の一覧を返す場合があります ("\0" は null 文字を表します)。  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 \* *DriverAttributes*がリスト全体を保持するのに十分な大きさでない場合、リストは切り捨てられ **、SQLDrivers**は SQLSTATE 01004 (データが切り捨てられた) を返し、リストの長さ (最後のヌル終了バイトを除く) が **AttributesLengthPtr*で返されます。  
  
 ドライバー属性キーワードは、ドライバーがインストールされると、システム情報から追加されます。 詳細については[、「ODBC コンポーネントのインストール](../../../odbc/reference/install/installing-odbc-components.md)」を参照してください。  
  
 アプリケーションは、すべての**ドライバーの説明を取得する SQLDrivers**を複数回呼び出すことができます。 ドライバー マネージャーは、システム情報からこの情報を取得します。 これ以上ドライバーの説明がない場合は **、sqlDrivers は**SQL_NO_DATAを返します。 **SQL_NO_DATAを返した**直後にSQL_FETCH_NEXTを指定して呼び出された場合、最初のドライバーの説明が返されます。 アプリケーションが**SQLDrivers**によって返される情報をどのように使用するかについては、「[データ ソースまたはドライバの選択](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)」を参照してください。  
  
 SQL_FETCH_NEXTが最初に呼び出されるときに**SQLDrivers**に渡された場合 **、SQLDrivers**は最初のデータ ソース名を返します。  
  
 **SQLDrivers**はドライバー マネージャーで実装されているため、ドライバーの標準に準拠する特定のドライバーに関係なくすべてのドライバーでサポートされています。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースへの接続に必要な値の検出と一覧表示|[SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|データ ソース名を返す|[SQLDataSources 関数](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|接続文字列またはダイアログ ボックスを使用したデータ ソースへの接続|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
