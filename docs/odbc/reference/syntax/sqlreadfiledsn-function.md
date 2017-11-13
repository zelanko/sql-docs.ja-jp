---
title: "SQLReadFileDSN 関数 |Microsoft ドキュメント"
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
- SQLReadFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLReadFileDSN
helpviewer_keywords:
- SQLReadFileDSN function [ODBC]
ms.assetid: ead464aa-cdc3-47dd-a0c0-997711205d31
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f3d74f900de16f8b2b257d9af6c65e8745139d3c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlreadfiledsn-function"></a>SQLReadFileDSN 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLReadFileDSN**ファイル DSN から情報を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLReadFileDSN(  
     LPCSTR   lpszFileName,  
     LPCSTR   lpszAppName,  
     LPCSTR   lpszKeyName,  
     LPSTR    lpszString,  
     WORD     cbString,  
     WORD *   pcbString);  
```  
  
## <a name="arguments"></a>引数  
 *場合*  
 [入力].Dsn ファイルの名前を含むデータ バッファーへのポインター。 .Dsn 拡張機能は、.dsn 拡張していないすべてのファイル名に追加されます。 値*\*場合*null で終わる文字列にする必要があります。  
  
 *lpszAppName*  
 [入力]アプリケーションの名前を含むデータ バッファーへのポインター。 これは、ODBC のセクションの"ODBC"です。 値 *\*lpszAppName* null で終わる文字列にする必要があります。  
  
 *lpszKeyName*  
 [入力]読み取られるキーの名前を含むデータ バッファーへのポインター。 予約済みキーワードは、「コメント」を参照してください。 値 *\*lpszAppName* null で終わる文字列にする必要があります。  
  
 *lpszString*  
 [出力]読み取られるキーに関連付けられている文字列を含むデータ バッファーへのポインター。  
  
 場合*\*場合*は有効な .dsn ファイル名が、 *lpszAppName*引数が null ポインターと*lpszKeyName*引数が null ポインターの場合は、し、 *\*lpszString*有効なアプリケーションの一覧が含まれています。 場合*\*場合*有効 .dsn ファイルの名前を指定し、  *\*lpszAppName*は有効なアプリケーション名、ですが、 *lpszKeyName*引数が nullポインター、  *\*lpszString*適切なファイルのセクションで、DSN、セミコロンで区切られた有効な予約済みキーワードの一覧が含まれています。 場合*\*場合*は有効な .dsn ファイル名が、  *\*lpszAppName* null ポインターと*lpszKeyName*引数が null ポインターの場合は、 *\*lpszString*のセクションでは、DSN ファイルでは、セミコロンで区切られた一覧が含まれています。  
  
 *cbString*  
 [入力]長さ、  *\*lpszString*バッファー。  
  
 *pcbString*  
 [出力]返される使用可能なバイトの合計数 *\*lpszString*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*cbString*、出力文字列に *\*lpszString*に切り捨てられます*cbString*負符号null 終了文字です。 *PcbString*引数が null ポインターを指定できます。  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLReadFileDSN**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_BUFF_LEN|無効なバッファーの長さ|*LpszString*引数が NULL です。<br /><br /> *CbString*引数が 0 未満です。|  
|ODBC_ERROR_INVALID_PATH|無効なインストール パス|指定されたファイル名のパス、*場合*引数が無効です。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な要求の種類|*LpszAppName*引数が NULL の場合中、 *lpszKeyName*引数が無効です。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|出力文字列の切り捨て|返される文字列 *\*lpszString*ために切り捨てられました値*cbString*がの値以下でした *\*pcbString*.|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|キーワードは、ファイル DSN に存在しません。|  
  
## <a name="comments"></a>コメント  
 ODBC では、接続情報を格納するための [ODBC] セクションの名前を予約します。 このセクションの予約済みキーワードは、接続文字列での予約と同じ**SQLDriverConnect**です。 (詳細については、次を参照してください、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明です。)。  
  
 アプリケーションでは、ファイル dsn 情報を読み取るため、これらの予約済みキーワードを使用できます。 アプリケーションが呼び出すことができます、ファイル DSN に関連付けられている、DSN を使用しない接続文字列を検索する場合は**SQLReadFileDSN** [ODBC] セクションで、予約済みの接続文字列キーワードのいずれか。 DSN を使用しない接続で渡された完全な接続文字列は、[ODBC] セクションで、キーワード (予約済みおよびドライバー固有) のすべての組み合わせです。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ファイル DSN に情報を書き込む|[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|

