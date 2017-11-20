---
title: "SQLDrivers 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 39d6aee9cf7260d4bc21cc66d39f8845c3d7df97
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqldrivers-function"></a>SQLDrivers 関数
**準拠**  
 バージョンで導入されました ODBC 2.0 Standards 準拠: ODBC。  
  
 **概要**  
 **SQLDrivers**ドライバーの説明とドライバー属性のキーワードを示します。 この関数では、ドライバー マネージャーによってのみを実装します。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 *EnvironmentHandle*  
 [入力]環境ハンドルです。  
  
 *方向*  
 [入力]ドライバー マネージャーがリスト (SQL_FETCH_NEXT) または (SQL_FETCH_FIRST) の一覧の先頭から検索を開始するかどうかに次のドライバーの記述をフェッチするかどうかを判断します。  
  
 *DriverDescription*  
 [出力]ドライバーの説明を返すバッファーへのポインター。  
  
 場合*DriverDescription* null、 *DescriptionLengthPtr*はまだ文字 (文字データの null 終端文字を除く) の合計数を返しますで返される使用可能なバッファーを指す*DriverDescription*です。  
  
 *BufferLength1*  
 [入力]長さ、**DriverDescription*文字バッファー。  
  
 *DescriptionLengthPtr*  
 [出力]文字 (null 終了文字を除く) の合計数を返すバッファーへのポインターで返される使用可能な\* *DriverDescription*です。 返される文字数がより大きいかに等しい場合*BufferLength1*、ドライバーの説明で\* *DriverDescription*に切り捨てられます*BufferLength1* null 終端文字の長さマイナスです。  
  
 *DriverAttributes*  
 [出力]\(「コメント」を参照してください) ドライバー属性値のペアの一覧を返すバッファーへのポインター。  
  
 場合*DriverAttributes*が NULL の場合、 *AttributesLengthPtr*はバイト (文字データの null 終端文字を除く) の合計数を返しますが、バッファーに返される使用可能なによって示される*DriverAttributes*です。  
  
 *BufferLength2*  
 [入力]長さ、 \* *DriverAttributes*文字バッファー。 場合、  *\*DriverDescription*値は Unicode 文字列です (呼び出し時に**SQLDriversW**) では、 *BufferLength*引数は偶数である必要があります。  
  
 *AttributesLengthPtr*  
 [出力]合計バイト数 (null 終了バイトを除く) を返すバッファーへのポインターで返される使用可能な\* *DriverAttributes*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*BufferLength2*、属性値のペアの一覧\* *DriverAttributes*に切り捨てられます*BufferLength2* null 終端文字の長さマイナスです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLDrivers** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_ENV と*処理*の*EnvironmentHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLDrivers**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|(DM) ドライバー マネージャー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|(DM) バッファー \* *DriverDescription*を完全なドライバーの説明を返すのに十分な大きさがありません。 そのため、説明が切り捨てられました。 完全なドライバーの説明の長さが返される\* *DescriptionLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。<br /><br /> (DM) バッファー \* *DriverAttributes*属性値のペアの完全な一覧を返すのに十分な大きさがありません。 そのため、一覧が切り捨てられました。 切り詰められていない属性値ペアのリストの長さが返される **AttributesLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバー マネージャーは、(DM) は、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|引数の指定された値 (DM) *BufferLength1*が 0 未満です。<br /><br /> 引数の指定された値 (DM) *BufferLength2*が 0 未満か、1 にします。|  
|HY103|無効な取得コード|(DM) 引数の値が指定された*方向*SQL_FETCH_FIRST または SQL_FETCH_NEXT でした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
  
## <a name="comments"></a>コメント  
 **SQLDrivers**でドライバーの説明を返します、 \* *DriverDescription*バッファー。 ドライバーに関する追加情報を返します、 \* *DriverAttributes*キーワードと値のペアの一覧としてバッファー。 すべてのキーワードに一覧されたシステム情報以外のすべてのドライバー、ドライバーが返される**CreateDSN**、データ ソースの作成を要求するために使用され、したがっては省略可能です。 各ペアは、null バイトで終了し、完全な一覧が null のバイトで終了しました (つまり、2 つの null バイトがリストの末尾をマークする)。 たとえば、C の構文を使用して、ファイル ベースのドライバーでは、次の属性 (「\0」は、null 文字を表す) の一覧を返す場合があります。  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 場合\* *DriverAttributes*が十分に大きくないリスト全体を保持するために、一覧が切り捨てられた**SQLDrivers** SQLSTATE 01004 (データが切り捨てられました)、およびリストの長さを返します (を除く、最後の null 終了バイト) が返されます **AttributesLengthPtr*です。  
  
 ドライバーがインストールされている場合、システム情報のドライバー属性のキーワードが追加されます。 詳細については、次を参照してください。 [ODBC コンポーネントのインストール中](../../../odbc/reference/install/installing-odbc-components.md)です。  
  
 アプリケーションが呼び出すことができます**SQLDrivers**すべてのドライバーの説明の取得を複数回です。 ドライバー マネージャーは、システム情報からこの情報を取得します。 ない複数のドライバーの説明がある場合に**SQLDrivers** SQL_NO_DATA が返されます。 場合**SQLDrivers**は、最初のドライバーの説明を返します SQL_NO_DATA が返された後すぐに SQL_FETCH_NEXT で呼び出されます。 アプリケーションがによって返される情報を使用する方法に関する情報の**SQLDrivers**を参照してください[データ ソースまたはドライバーを選択する](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)です。  
  
 SQL_FETCH_NEXT が渡された場合**SQLDrivers** 、初めて呼び出されたとき、 **SQLDrivers**最初のデータ ソース名を取得します。  
  
 **SQLDrivers**は実装されて、ドライバー マネージャーで、特定のドライバーの標準への準拠に関係なくすべてのドライバーのサポートされています。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|検出して、データ ソースへの接続に必要な値を一覧表示します。|[SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|データ ソース名を取得します。|[SQLDataSources 関数](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|接続文字列やダイアログ ボックスを使用してデータ ソースに接続します。|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

