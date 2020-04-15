---
title: 関数を読み取る |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLReadFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLReadFileDSN
helpviewer_keywords:
- SQLReadFileDSN function [ODBC]
ms.assetid: ead464aa-cdc3-47dd-a0c0-997711205d31
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3abda956ee7682c9ac49270e8bf69fb039641790
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303953"
---
# <a name="sqlreadfiledsn-function"></a>SQLReadFileDSN 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 **ファイル DSN**から情報を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLReadFileDSN(  
     LPCSTR   lpszFileName,  
     LPCSTR   lpszAppName,  
     LPCSTR   lpszKeyName,  
     LPSTR    lpszString,  
     WORD     cbString,  
     WORD *   pcbString);  
```  
  
## <a name="arguments"></a>引数  
 *ファイル名*  
 [入力]dsn ファイルの名前を含むデータ バッファーへのポインター。 拡張子が .dsn でないすべてのファイル名に拡張子 .dsn が付加されます。 * \*lpszFileName*の値は、null で終わる文字列である必要があります。  
  
 *を使用します。*  
 [入力]アプリケーションの名前を含むデータ バッファーへのポインター。 これは ODBC セクションの "ODBC" です。 * \*lpszAppName*の値は、null で終わる文字列である必要があります。  
  
 *名前を変更します。*  
 [入力]読み取るキーの名前を含むデータ バッファーへのポインター。 予約キーワードについては、「コメント」を参照してください。 * \*lpszAppName*の値は、null で終わる文字列である必要があります。  
  
 *文字列*  
 [出力]読み取るキーに関連付けられている文字列を含むデータ バッファーへのポインター。  
  
 * \*lpszFileName*が有効な .dsn ファイル名であるが *、引数 lpszAppName*が null ポインターであり、*引数 lpszKeyName*が null ポインターである場合*\*、lpszString*には有効なアプリケーションのリストが含まれます。 * \*lpszFileName*が有効な .dsn ファイル名であり*\*、lpszAppName*が有効なアプリケーション名である場合、*引数 lpszKeyName*が null ポインターである場合*\*、lpszString*には、有効な予約キーワードのリストが DSN ファイルの適切なセクションに含まれます。 * \*lpszFileName*が有効な .dsn ファイル名であり*\*、lpszAppName*が null ポインターであり、*引数 lpszKeyName*が null ポインターである場合*\*、lpszString*には DSN ファイル内のセクションのリストがセミコロンで区切られます。  
  
 *cb文字列*  
 [入力]*\*バッファ*の長さ。  
  
 *pcb ストリング*  
 [出力]* \*lpszString*で返されるバイト数の合計。 戻り値のバイト数が*cbString*以上の場合*\*、lpszString*の出力文字列は *、cbString*から null 終端文字を引いた値に切り捨てられます。 *引数の引数*は null ポインターにすることができます。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLReadFileDSN が**FALSE を返すと、関連付けられた*\*pfErrorCode*値を取得するには **、SQLInstallerError**を呼び出します。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_BUFF_LEN|バッファ長が無効です|*引数が*NULL でした。<br /><br /> *引数 cbString*が 0 以下でした。|  
|ODBC_ERROR_INVALID_PATH|インストール パスが無効です|*引数 lpszFileName*に指定されたファイル名のパスが無効です。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な種類の要求|*引数が*NULL であるのに対して、*引数は有効*です。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|出力文字列が切り捨てられました|*cbString*の*\***\** 値が pcbString の値以下であったため、lpszString で返された文字列が切り捨てられました。|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|ファイル DSN にキーワードが存在しませんでした。|  
  
## <a name="comments"></a>説明  
 ODBC では、接続情報を格納するセクション名 [ODBC] が予約されています。 このセクションの予約済みキーワードは **、SQLDriverConnect**での接続文字列用に予約されているものと同じです。 (詳細については[、SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明を参照してください。  
  
 アプリケーションは、これらの予約済みキーワードを使用して、ファイル DSN 内の情報を読み取ることができます。 アプリケーションがファイル DSN に関連付けられた DSN を使用しないで接続文字列を検索する場合は、[ODBC] セクションで予約されている接続文字列キーワードの**SQLReadFileDSN**を呼び出すことができます。 DSN レス接続で渡される完全な接続文字列は、[ODBC] セクションのすべてのキーワード (予約済みおよびドライバ固有) の組み合わせです。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ファイル DSN への情報の書き込み|[ファイルを書き込む](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|
