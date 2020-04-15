---
title: 関数を書き込む |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e781f1be79e0079f33b3d0800c665f5f5e9fda4d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286892"
---
# <a name="sqlwritefiledsn-function"></a>SQLWriteFileDSN 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 **情報を**ファイル DSN に書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>引数  
 *ファイル名*  
 [入力]ファイル DSN の名前へのポインター。 DSN 拡張子が既に付いていないすべてのファイル名に、DSN 拡張子が追加されます。  
  
 *を使用します。*  
 [入力]アプリケーションの名前へのポインター。 これは ODBC セクションの "ODBC" です。  
  
 *名前を変更します。*  
 [入力]読み取るキーの名前へのポインター。 予約キーワードについては、「コメント」を参照してください。  
  
 *文字列*  
 [出力]書き込むキーに関連付けられた文字列を指します。 この引数で指される文字列の最大長は 32,767 バイトです。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLWriteFileDSN が**FALSE を返すと、SQL**インストーラ エラー**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_PATH|インストール パスが無効です|*引数 lpszFileName*に指定されたファイル名のパスが無効です。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な種類の要求|*引数が*NULL でした。 *lpszKeyName* *lpszString*|  
  
## <a name="comments"></a>説明  
 ODBC では、接続情報を格納するセクション名 [ODBC] が予約されています。 このセクションの予約済みキーワードは **、SQLDriverConnect**での接続文字列用に予約されているものと同じです。 (詳細については[、SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明を参照してください。  
  
 アプリケーションは、これらの予約済みキーワードを使用して、ファイル DSN に情報を直接書き込むことができます。 アプリケーションがファイル DSN に関連付けられた DSN を使用しないで接続文字列を作成または変更する場合、[ODBC] セクションの予約済み接続文字列キーワードの**SQLWriteFileDSN**を呼び出すことができます。  
  
 引数*lpszString*が null ポインターの場合は、引数*lpszKeyName*が指すキーワードが .dsn ファイルから削除されます。 *引数が両方*とも null*lpszKeyName*ポインターの場合は、*引数 lpszAppName*によって指定されたセクションが .dsn ファイルから削除されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ファイル DSN からの情報の読み取り|[ファイルを読み取るDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|
