---
title: "SQLWriteFileDSN 関数 |Microsoft ドキュメント"
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
- SQLWriteFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteFileDSN
helpviewer_keywords:
- SQLWriteFileDSN [ODBC]
ms.assetid: 9e18f56f-1061-416b-83d4-ffeec42ab5a9
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 47cc9672aecb91917a5abc15de2fc34fac59d2c2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlwritefiledsn-function"></a>SQLWriteFileDSN 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLWriteFileDSN**ファイル DSN に情報を書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>引数  
 *場合*  
 [入力]ファイル DSN の名前へのポインター。 DSN の拡張機能は、DSN の拡張機能がないすべてのファイル名に追加されます。  
  
 *lpszAppName*  
 [入力]アプリケーションの名前へのポインター。 これは、ODBC のセクションの"ODBC"です。  
  
 *lpszKeyName*  
 [入力]読み取られるキーの名前へのポインター。 予約済みキーワードは、「コメント」を参照してください。  
  
 *lpszString*  
 [出力]書き込むキーに関連付けられている文字列を指し示していました。 この引数が指す文字列の最大長は、32,767 のバイトです。  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLWriteFileDSN**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_PATH|無効なインストール パス|指定されたファイル名のパス、*場合*引数が無効です。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な要求の種類|*LpszAppName*、 *lpszKeyName*、または*lpszString*引数が NULL です。|  
  
## <a name="comments"></a>コメント  
 ODBC では、接続情報を格納するための [ODBC] セクションの名前を予約します。 このセクションの予約済みキーワードは、接続文字列での予約と同じ**SQLDriverConnect**です。 (詳細については、次を参照してください、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明です。)。  
  
 アプリケーションは、情報を書き込むファイル DSN に直接これらの予約済みキーワードを使用できます。 アプリケーションを作成またはファイル DSN に関連付けられている DSN を使用しない接続文字列を変更する場合、呼び出すことができます**SQLWriteFileDSN** [ODBC] セクションで、予約済みの接続文字列キーワードのいずれか。  
  
 場合、 *lpszString*引数は、null ポインターが指す、キーワード、 *lpszKeyName*引数は、.dsn ファイルから削除されます。 場合、 *lpszString*と*lpszKeyName*引数が両方とも null ポインターが指すセクション、 *lpszAppName*引数は、.dsn ファイルから削除されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ファイル Dsn から情報の読み取り|[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|

