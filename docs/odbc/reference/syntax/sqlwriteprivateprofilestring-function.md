---
title: "SQLWritePrivateProfileString 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLWritePrivateProfileString
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLWritePrivateProfileString
helpviewer_keywords: SQLWritePrivateProfileString [ODBC]
ms.assetid: 526f36a4-92ed-4874-9725-82d27c0b86f9
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 081d91ac2c257fbaa60b93de24dd134ea698bcd9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlwriteprivateprofilestring-function"></a>SQLWritePrivateProfileString 関数
**準拠**  
 バージョンが導入されています。 ODBC 2.0  
  
 **概要**  
 **SQLWritePrivateProfileString**システム情報の Odbc.ini サブキーに、値の名前とデータを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL SQLWritePrivateProfileString(  
     LPCSTR     lpszSection,  
     LPCSTR     lpszEntry,  
     LPCSTR     lpszString,  
     LPCSTR     lpszFilename);  
```  
  
## <a name="arguments"></a>引数  
 *大文字、小文字*  
 [入力]文字列のコピー先となるセクションの名前を表す null で終わる文字列へのポインター。 セクションが存在しない場合は作成されます。 セクションの名前がケースに依存しません。文字列には、任意の大文字と小文字を指定できます。  
  
 *lpszEntry*  
 [入力]文字列と関連付けられるキーの名前を表す null で終わる文字列へのポインター。 指定されたセクションにキーが存在しない場合は作成されます。 この引数が NULL の場合、セクション内のすべてのエントリを含むセクション全体が削除されます。  
  
 *lpszString*  
 [入力]ファイルに書き込まれる null で終わる文字列へのポインター。 この引数が NULL の場合、キーが指す、 *lpszEntry*引数を削除します。  
  
 *場合*  
 [出力]初期化ファイルの名前を null で終わる文字列へのポインター。  
  
## <a name="returns"></a>戻り値  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLWritePrivateProfileString**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|要求されたシステム情報を書き込めませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLWritePrivateProfileString**に Microsoft Windows/Windows 2000 から Microsoft® Windows® ポート ドライバーとドライバーのセットアップ Dll に簡単な方法で提供されます。 呼び出す**WritePrivateProfileString** 、Odbc.ini ファイルにプロファイル文字列への呼び出しに置き換える必要がありますを記述する**SQLWritePrivateProfileString**です。 **SQLWritePrivateProfileString**システム情報の Odbc.ini サブキーに、指定された値の名前とデータを追加する Win32® API で関数を呼び出します。  
  
 構成モードでは、DSN の値を一覧表示する Odbc.ini エントリがシステム情報の場所を示します。 DSN がユーザー DSN (状態変数は USERDSN_ONLY) の場合は、関数は、HKEY_CURRENT_USER 内の Odbc.ini エントリを書き込みます。 DSN がシステム DSN (SYSTEMDSN_ONLY) の場合は、関数は、HKEY_LOCAL_MACHINE 内の Odbc.ini エントリを書き込みます。 状態変数が BOTHDSN の場合は、HKEY_CURRENT_USER 試行すると、HKEY_LOCAL_MACHINE が使用されますが失敗した場合。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|システム情報の値を取得します。|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
