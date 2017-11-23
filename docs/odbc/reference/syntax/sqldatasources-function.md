---
title: "SQLDataSources 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLDataSources
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLDataSources
helpviewer_keywords: SQLDataSources function [ODBC]
ms.assetid: 3f63b1b4-e70e-44cd-96c6-6878d50d0117
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 09c64ec707be4d99bb66547f8583f707dd281277
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqldatasources-function"></a>SQLDataSources 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLDataSources**データ ソースに関する情報を返します。 この関数では、ドライバー マネージャーによってのみを実装します。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 *EnvironmentHandle*  
 [入力]環境ハンドルです。  
  
 *方向*  
 [入力]どのデータ ソース ドライバー マネージャーで、に関する情報が返されますを決定します。 次の値をとります。  
  
 SQL_FETCH_NEXT (をフェッチする一覧で、[次へ] のデータ ソース名)、SQL_FETCH_FIRST (をフェッチするリストの先頭から)、(fetch、最初のユーザーに DSN) SQL_FETCH_FIRST_USER または SQL_FETCH_FIRST_SYSTEM (をフェッチする最初のシステム DSN)。  
  
 ときに*方向*SQL_FETCH_FIRST、後続の呼び出しに設定されている**SQLDataSources**で*方向*リターン ユーザーおよびシステムの両方の Dsn を前方に設定します。 ときに*方向*SQL_FETCH_FIRST_USER、すべての後続の呼び出しに設定されている**SQLDataSources**で*方向*リターン ユーザー Dsn だけを前方に設定します。 ときに*方向*SQL_FETCH_FIRST_SYSTEM、すべての後続の呼び出しに設定されている**SQLDataSources**で*方向*リターン システム Dsn だけを前方に設定します。  
  
 *ServerName*  
 [出力]データ ソース名を返すバッファーへのポインター。  
  
 場合*ServerName* null、 *NameLength1Ptr*はまだ文字 (文字データの null 終端文字を除く) の合計数を返しますが指すバッファーに返される使用可能な*ServerName*です。  
  
 *BufferLength1*  
 [入力]長さ、**ServerName*文字内でのバッファーです。 この SQL_MAX_DSN_LENGTH と null 終了文字より長くする必要はありません。  
  
 *NameLength1Ptr*  
 [出力]文字 (null 終了文字を除く) の合計数を返すバッファーへのポインターで返される使用可能な\* *ServerName*です。 返される文字数がより大きいかに等しい場合*BufferLength1*、内のデータ ソース名\* *ServerName*に切り捨てられます*BufferLength1* null 終端文字の長さマイナスです。  
  
 *Description*  
 [出力]データ ソースに関連付けられているドライバーの説明を返すバッファーへのポインター。 たとえば、dBASE ファイルまたは SQL Server。  
  
 場合*説明*null、 *NameLength2Ptr*はまだ文字 (文字データの null 終端文字を除く) の合計数を返しますが指すバッファーに返される使用可能な*説明*です。  
  
 *BufferLength2*  
 [入力]文字の長さ、**説明*バッファー。  
  
 *NameLength2Ptr*  
 [出力]文字 (null 終了文字を除く) の合計数を返すバッファーへのポインターで返される使用可能な\**説明*です。 返される文字数がより大きいかに等しい場合*BufferLength2*、ドライバーの説明で\**説明*に切り捨てられます*BufferLength2* null 終端文字の長さマイナスです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLDataSources** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec**で、 *HandleType*sql_handle_env としての*処理*の*EnvironmentHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLDataSources**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|(DM) ドライバー マネージャー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|(DM) バッファー \* *ServerName*完全なデータ ソース名を取得するのに十分な大きさがありません。 そのため、名前は切り詰められました。 全体のデータ ソース名の長さが返される\* *NameLength1Ptr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。<br /><br /> (DM) バッファー \**説明*を完全なドライバーの説明を返すのに十分な大きさがありません。 そのため、説明が切り捨てられました。 切り詰められていないデータ ソースの説明の長さが返される **NameLength2Ptr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|(DM) エラーが発生しましたの固有の SQLSTATE がありませんでした。 これとの実装に固有の SQLSTATE が定義されていません。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバー マネージャーは、(DM) は、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|引数の指定された値 (DM) *BufferLength1*が 0 未満です。<br /><br /> 引数の指定された値 (DM) *BufferLength2*が 0 未満です。|  
|HY103|無効な取得コード|(DM) 引数の値が指定された*方向*SQL_FETCH_FIRST、SQL_FETCH_FIRST_USER、SQL_FETCH_FIRST_SYSTEM、または SQL_FETCH_NEXT と等しいでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
  
## <a name="comments"></a>コメント  
 **SQLDataSources**は実装されて、ドライバー マネージャーで、特定のドライバーの標準への準拠に関係なくすべてのドライバーのサポートされています。  
  
 アプリケーションが呼び出すことができます**SQLDataSources**すべてのデータ ソース名の取得を複数回です。 ドライバー マネージャーは、システム情報からこの情報を取得します。 データ ソース名がなくなったらが存在する場合、ドライバー マネージャーは、SQL_NO_DATA が返される。 場合**SQLDataSources**は、SQL_NO_DATA が返された後、最初のデータ ソース名が返されます。 直後に SQL_FETCH_NEXT で呼び出されます。 アプリケーションがによって返される情報を使用する方法に関する情報の**SQLDataSources**を参照してください[データ ソースまたはドライバーを選択する](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)です。  
  
 SQL_FETCH_NEXT が渡された場合**SQLDataSources**非常に初めて呼び出されると、最初のデータ ソース名を返すことはできます。  
  
 ドライバーは、実際のデータ ソースをデータ ソース名をマップする方法を決定します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|検出して、データ ソースへの接続に必要な値を一覧表示します。|[SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|接続文字列やダイアログ ボックスを使用してデータ ソースに接続します。|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|ドライバーの説明と属性を返す|[SQLDrivers 関数](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
