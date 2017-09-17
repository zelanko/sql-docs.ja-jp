---
title: "SQLGetDiagRec 関数 |Microsoft ドキュメント"
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
- SQLGetDiagRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagRec
helpviewer_keywords:
- SQLGetDiagRec function [ODBC]
ms.assetid: ebdbac93-3d68-438f-8416-ef1f08e04269
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 591664f329f4c7feeb24fff52b809dba567d0b80
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdiagrec-function"></a>SQLGetDiagRec 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLGetDiagRec**エラー、警告、およびステータス情報が含まれる診断レコードの複数のフィールドの現在の値を返します。 異なり**SQLGetDiagField**、呼び出しごとに 1 つの診断フィールドが返されます**SQLGetDiagRec**いくつかのよく使用される、SQLSTATE、ネイティブ エラー コードを含めて、診断レコードのフィールドを返しますと診断メッセージ テキストです。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLGetDiagRec(  
     SQLSMALLINT     HandleType,  
     SQLHANDLE       Handle,  
     SQLSMALLINT     RecNumber,  
     SQLCHAR *       SQLState,  
     SQLINTEGER *    NativeErrorPtr,  
     SQLCHAR *       MessageText,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   TextLengthPtr);  
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
 [入力]アプリケーションが情報をシークする元となる状態レコードを示します。 状態レコードは、1 から番号が付けられます。  
  
 *SQLState*  
 [出力]診断レコードの 5 文字の SQLSTATE コード (および終端の NULL) を返すバッファーへのポインター *RecNumber*です。 最初の 2 つの文字を示すクラスです。次の 3 では、サブクラスを示しています。 この情報は、SQL_DIAG_SQLSTATE 診断フィールドに含まれます。 詳細については、次を参照してください。 [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md)です。  
  
 *NativeErrorPtr*  
 [出力]ネイティブ エラー コード、データ ソースに固有の返されるバッファーへのポインター。 この情報は、SQL_DIAG_NATIVE 診断フィールドに含まれます。  
  
 *メッセージ テキスト*  
 [出力]診断メッセージのテキスト文字列を返すバッファーへのポインター。 この情報は、SQL_DIAG_MESSAGE_TEXT 診断フィールドに含まれます。 文字列の形式を次を参照してください。[診断メッセージ](../../../odbc/reference/develop-app/diagnostic-messages.md)です。  
  
 場合*MessageText* null、 *TextLengthPtr*はまだ文字 (文字データの null 終端文字を除く) の合計数を返しますが指すバッファーに返される使用可能な*MessageText*です。  
  
 *BufferLength*  
 [入力]長さ、**MessageText*文字バッファー。 診断メッセージのテキストの最大長はありません。  
  
 *TextLengthPtr*  
 [出力]文字 (null 終端文字のために必要な文字数を除く) の合計数を返すバッファーへのポインターで返される使用可能な* \*MessageText*です。 返される文字数がより大きい場合*BufferLength*、診断メッセージのテキストで* \*MessageText*に切り捨てられます*BufferLength* null 終端文字の長さマイナスです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetDiagRec**自体の診断レコードが通知されません。 次の戻り値を使用して、独自の実行の結果を報告します。  
  
-   SQL_SUCCESS: 関数では診断情報が正常に返されます。  
  
-   SQL_SUCCESS_WITH_INFO: \* *MessageText*バッファーが小さすぎるため、要求された診断メッセージを保持します。 診断レコードは生成されませんでした。 切り捨てが発生しました、アプリケーションを比較する必要がありますのことを確認する*BufferLength*実際に書き込まれますが、使用可能なバイト数へ **StringLengthPtr*です。  
  
-   SQL_INVALID_HANDLE: によってハンドルが示される*HandleType*と*処理*が有効なハンドル。  
  
-   SQL_ERROR: 次のいずれかが発生しました。  
  
    -   *RecNumber*が負または 0 です。  
  
    -   *BufferLength*が 0 未満です。  
  
    -   非同期の通知を使用する場合、ハンドルに非同期操作は完了しませんでした。  
  
-   SQL_NO_DATA: *RecNumber*診断レコードで指定されたハンドルに存在していた数よりも大きかった*を処理します。* 関数は、任意の正の SQL_NO_DATA が返さも*RecNumber*に対する診断レコードが存在しない場合*処理*です。  
  
## <a name="comments"></a>コメント  
 アプリケーションを呼び出す通常**SQLGetDiagRec** SQL_ERROR または SQL_SUCCESS_WITH_INFO ODBC 関数を前回呼び出したときに返すとき。 ただし、ため、任意の ODBC 関数が投稿できる 0 個以上の診断レコードが呼び出されるたび、アプリケーションを呼び出せる**SQLGetDiagRec** ODBC 関数呼び出しの後にします。 アプリケーションが呼び出すことができます**SQLGetDiagRec**診断データの構造の一部またはすべてのレコードを返すを複数回です。 ODBC では、任意の時点で格納できる診断レコードの数に制限はありません。  
  
 **SQLGetDiagRec**診断データの構造体のヘッダーからフィールドを返すには使用できません。 (、 *RecNumber*引数は 0 より大きくする必要があります)。アプリケーションを呼び出す必要があります**SQLGetDiagField**この目的のためです。  
  
 **SQLGetDiagRec**最近で指定されたハンドルに関連付けられている診断の情報のみを取得、*処理*引数。 アプリケーションが別の ODBC 関数を呼び出す場合を除く**SQLGetDiagRec**、 **SQLGetDiagField**、または**SQLError**、前の呼び出しからの診断情報、同じハンドルは失われます。  
  
 アプリケーション スキャンできるすべての診断レコードをループするには、インクリメント*RecNumber*限り、 **SQLGetDiagRec** SQL_SUCCESS を返します。 呼び出す**SQLGetDiagRec**ヘッダーとレコード フィールドに非破壊的です。 アプリケーションが呼び出すことができます**SQLGetDiagRec**を除く、他の関数の限りレコードからフィールドを取得するは後でもう一度**SQLGetDiagRec**、 **SQLGetDiagField**、または**SQLError**は暫定的で呼び出されました。 呼び出して、アプリケーションで使用できる診断レコードの合計数のカウントが取得できますも**SQLGetDiagField** SQL_DIAG_NUMBER フィールドと、呼び出し元の値を取得する**SQLGetDiagRec**その回数。  
  
 診断データの構造体のフィールドの説明は、次を参照してください。 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)です。 詳細については、次を参照してください。[を使用して SQLGetDiagRec と SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)と[SQLGetDiagRec の実装と SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)です。  
  
 非同期的に実行されているもの以外の API を呼び出すと、HY010 が生成されます「関数のシーケンス エラー」です。 ただし、非同期操作が完了する前に、エラー レコードを取得できません。  
  
## <a name="handletype-argument"></a>HandleType 引数  
 各ハンドル型には、関連付けられている診断の情報を持つことができます。 *HandleType*引数のハンドル型を示します、*処理*引数。  
  
 いくつかのヘッダーとレコード フィールドは、環境、接続、ステートメント、および記述子ハンドル返されることはできません。 それらのハンドル フィールドは適用されませんが、「ヘッダー フィールド」と「レコードのフィールド」セクションに示される[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)です。  
  
 呼び出し**SQLGetDiagRec**場合 SQL_INVALID_HANDLE が返されます*HandleType*は SQL_HANDLE_SENV で、共有環境ハンドルを表します。 ただし場合、 *HandleType*を sql_handle_env として、*処理*共有または共有されていない環境ハンドルのいずれかを指定できます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|診断レコードのフィールドまたは診断のヘッダーのフィールドを取得します。|[SQLGetDiagField 関数](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC のサンプル プログラム](../../../odbc/reference/sample-odbc-program.md)
