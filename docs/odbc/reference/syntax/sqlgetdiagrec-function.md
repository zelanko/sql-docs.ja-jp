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
- SQLGetDiagRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagRec
helpviewer_keywords:
- SQLGetDiagRec function [ODBC]
ms.assetid: ebdbac93-3d68-438f-8416-ef1f08e04269
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39069526e254903509ddfef00b7bd4844f3d9e10
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285382"
---
# <a name="sqlgetdiagrec-function"></a>SQLGetDiagRec 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLGetDiagRec**は、エラー、警告、および状態情報を含む診断レコードの複数のフィールドの現在の値を返します。 呼び出しごとに 1 つの診断フィールドを返す**SQLGetDiagField**とは異なり **、SQLGetDiagRec**は、SQLSTATE、ネイティブ エラー コード、診断メッセージ テキストなど、診断レコードの一般的に使用されるフィールドを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 [入力]診断が必要なハンドルのタイプを記述するハンドル型識別子。 次のいずれかである必要があります。  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN ハンドルは、ドライバー マネージャーとドライバーによってのみ使用されます。 アプリケーションでは、このハンドル型を使用しないでください。 SQL_HANDLE_DBC_INFO_TOKENの詳細については[、「ODBC ドライバーでの接続プール認識の開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)」を参照してください。  
  
 *Handle*  
 [入力]によって示される型の診断データ構造体*のハンドル*。 *HandleType*がSQL_HANDLE_ENV場合 *、Handle*は共有または非共有環境ハンドルのいずれかになります。  
  
 *RecNumber*  
 [入力]アプリケーションが情報を取得する状態レコードを示します。 状態レコードには 1 から番号が付きます。  
  
 *Sqlstate*  
 [出力]診断レコード*RecNumber*の 5 文字の SQLSTATE コード (および終了 NULL) を返すバッファーへのポインター。 最初の 2 文字はクラスを示します。次の 3 つはサブクラスを示します。 この情報は、SQL_DIAG_SQLSTATE診断フィールドに含まれています。 詳細については[、SQLSTATE を](../../../odbc/reference/develop-app/sqlstates.md)参照してください。  
  
 *ネイティブエラープター*  
 [出力]データ ソースに固有のネイティブ エラー コードを返すバッファーへのポインター。 この情報は、SQL_DIAG_NATIVE診断フィールドに含まれています。  
  
 *[MessageText]*  
 [出力]診断メッセージテキスト文字列を返すバッファーへのポインター。 この情報は、SQL_DIAG_MESSAGE_TEXT診断フィールドに含まれています。 文字列の形式については、[診断メッセージ](../../../odbc/reference/develop-app/diagnostic-messages.md)を参照してください。  
  
 *メッセージ テキスト*が NULL の場合 *、TextLengthPtr*は*MessageText*が指すバッファに返す文字の総数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]* メッセージ*テキスト*バッファーの長さ (文字数)。 診断メッセージ・テキストの最大長はありません。  
  
 *テキスト長Ptr*  
 [出力]MessageText で返される文字の合計数 (NULL 終端文字に必要な文字数を除く) を返すバッファへのポインタ。 * \** 返される文字数が*BufferLength*より大きい場合*\*、MessageText*の診断メッセージ テキストは*BufferLength*に切り捨てられ、null 終端文字の長さを引いた値になります。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetDiagRec**は、それ自体の診断レコードをポストしません。 次の戻り値を使用して、自身の実行結果を報告します。  
  
-   SQL_SUCCESS: 関数が診断情報を正常に返しました。  
  
-   SQL_SUCCESS_WITH_INFO: \* *MessageText*バッファが小さすぎて、要求された診断メッセージを保持できませんでした。 診断レコードは生成されませんでした。 切り捨てが発生したことを確認するには、アプリケーションは*BufferLength*を使用可能な実際のバイト数と比較する必要*があります。*  
  
-   SQL_INVALID_HANDLE:*ハンドル型*とハンドルで示された*ハンドル*が有効なハンドルではありませんでした。  
  
-   SQL_ERROR: 次のいずれかが発生しました。  
  
    -   *RecNumber*が負の値または 0 でした。  
  
    -   *バッファ長*が 0 未満でした。  
  
    -   非同期通知を使用する場合、ハンドルに対する非同期操作は完了しませんでした。  
  
-   SQL_NO_DATA: *RecNumber*が *、[ハンドル*] で指定されたハンドルに存在する診断レコードの数より多かった。 この関数は、*ハンドル*の診断レコードがない場合は、正の*RecNumber*のSQL_NO_DATAも返します。  
  
## <a name="comments"></a>説明  
 アプリケーションは通常、ODBC 関数の以前の呼び出しがSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返した場合に **、SQLGetDiagRec**を呼び出します。 ただし、どの ODBC 関数も呼び出されるたびに 0 個以上の診断レコードをポストできるため、アプリケーションは ODBC 関数呼び出しの後に**SQLGetDiagRec**を呼び出すことができます。 アプリケーションは **、SQLGetDiagRec**を複数回呼び出して、診断データ構造内のレコードの一部またはすべてを返すことができます。 ODBC では、一度に格納できる診断レコードの数に制限はありません。  
  
 **SQLGetDiagRec**を使用して、診断データ構造体のヘッダーからフィールドを返すことはできません。 *(RecNumber*引数は 0 より大きくなければなりません。アプリケーションは、この目的のために**SQLGetDiagField**を呼び出す必要があります。  
  
 **SQLGetDiagRec**は、*ハンドル*引数で指定されたハンドルに関連付けられた最も最近の診断情報のみを取得します。 アプリケーションが別の ODBC 関数を呼び出す場合は **、SQLGetDiagRec** **、SQLGetDiagField**、または**SQLError**を除き、同じハンドルでの以前の呼び出しからの診断情報はすべて失われます。  
  
 **SQLGetDiagRec**がSQL_SUCCESSを返す限り、アプリケーションは*RecNumber*をループしてインクリメントすることで、すべての診断レコードをスキャンできます。 **SQLGetDiagRec**への呼び出しは、ヘッダー フィールドおよびレコード フィールドに対して非破壊的です。 アプリケーションは **、SQLGetDiagRec 、SQLGetDiagField** 、または**SQLError**を除き、他の関数が暫定的に呼び出**SQLGetDiagField**されていない限り、後で再び**SQLGetDiagRec**を呼び出してレコードからフィールドを取得できます。 また、アプリケーションは **、SQLGetDiagField**を呼び出して SQL_DIAG_NUMBER フィールドの値を取得し、その後**SQLGetDiagRec**を何度も呼び出すことで、使用可能な診断レコードの合計数を取得することもできます。  
  
 診断データ構造体のフィールドの説明については、「 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)」を参照してください。 詳細については[、「SQLGetDiagRec および SQLGetDiagField の使用」](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)および[「SQLGetDiagRec および SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)の実装」を参照してください。  
  
 非同期に実行されている API 以外の API を呼び出すと、HY010 「関数シーケンスエラー」が生成されます。 ただし、非同期操作が完了する前にエラー レコードを取得することはできません。  
  
## <a name="handletype-argument"></a>ハンドル型引数  
 各ハンドルタイプには、診断情報を関連付けることができます。 *引数 HandleType*は、*ハンドル*引数のハンドル型を示します。  
  
 一部のヘッダーフィールドおよびレコード・フィールドは、環境、接続、ステートメント、および記述子ハンドルでは戻すことができません。 フィールドが適用されないハンドルは、 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)の 「ヘッダー フィールド」 および 「レコード フィールド」のセクションに示されています。  
  
 **SqlGetDiagRec**の呼び出しは、共用環境ハンドルを示す*ハンドル型*がSQL_HANDLE_SENV場合はSQL_INVALID_HANDLEを返します。 ただし *、HandleType*がSQL_HANDLE_ENV場合 *、Handle*は共有環境ハンドルまたは非共有環境ハンドルのいずれかになります。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|診断レコードのフィールドまたは診断ヘッダーのフィールドの取得|[SQLGetDiagField 関数](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC のサンプル プログラム](../../../odbc/reference/sample-odbc-program.md)
