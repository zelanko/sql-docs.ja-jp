---
title: "SQLGetPrivateProfileString 関数 |Microsoft ドキュメント"
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
apiname: SQLGetPrivateProfileString
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLGetPrivateProfileString
helpviewer_keywords: SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b7829cbff471b431b5c4975e8066356479631596
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetprivateprofilestring-function"></a>SQLGetPrivateProfileString 関数
**準拠**  
 バージョンが導入されています。 ODBC 2.0  
  
 **概要**  
 **SQLGetPrivateProfileString**値やシステム情報の値に対応するデータの名前の一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
int SQLGetPrivateProfileString(  
     LPCSTR   lpszSection,  
     LPCSTR   lpszEntry,  
     LPCSTR   lpszDefault,  
     LPCSTR   RetBuffer,  
     INT      cbRetBuffer,  
     LPCSTR   lpszFilename);  
```  
  
## <a name="arguments"></a>引数  
 *大文字、小文字*  
 [入力]キー名が含まれているセクションを指定する null で終わる文字列へのポインター。 この引数が NULL の場合、関数では、ファイルのすべてのセクション名を指定されたバッファーにコピーします。  
  
 *lpszEntry*  
 [入力]関連付けられている文字列を取得するキーの名前を表す null で終わる文字列へのポインター。 この引数が NULL の場合、すべてのキーで指定されたセクションの名前、*大文字、小文字*引数で指定したバッファーにコピー、 *RetBuffer*引数。  
  
 *から*  
 [入力]初期化ファイルにキーが見つからない場合は、指定したキーの既定値を指定する null で終わる文字列へのポインター。 この引数は、NULL にすることはできません。  
  
 *RetBuffer*  
 [出力]取得した文字列を受け取るバッファーへのポインター。  
  
 *cbRetBuffer*  
 [入力]指すバッファーの文字のサイズを指定、 *RetBuffer*引数。  
  
 *場合*  
 [入力]初期化ファイルの名前を null で終わる文字列へのポインター。 この引数に、ファイルへの完全パスが含まれていない場合、既定のディレクトリが検索されます。  
  
## <a name="returns"></a>戻り値  
 **SQLGetPrivateProfileString**読み取られた文字数を示す整数値を返します。  
  
## <a name="diagnostics"></a>診断  
 呼び出し時に**SQLGetPrivateProfileString**失敗すると、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLGetPrivateProfileString**に Microsoft Windows/Windows 2000 から Microsoft® Windows® ポート ドライバーとドライバーのセットアップ Dll に簡単な方法で提供されます。 呼び出す**GetPrivateProfileString** 、Odbc.ini ファイルからプロファイル文字列を置き換える取得する呼び出し**SQLGetPrivateProfileString**です。 **SQLGetPrivateProfileString**値またはシステム情報の Odbc.ini サブキーの値に対応するデータの要求された名前を取得する Win32® API で関数を呼び出します。  
  
 構成モード (によって設定**SQLSetConfigMode**) DSN の値を一覧表示する Odbc.ini エントリがシステム情報内にあることを示します。 DSN がユーザー DSN (構成モードでは USERDSN_ONLY) の場合は、関数は、HKEY_CURRENT_USER の Odbc.ini エントリから読み取ります。 DSN がシステム DSN (SYSTEMDSN_ONLY) の場合は、HKEY_LOCAL_MACHINE 内の Odbc.ini エントリから関数を読み取ります。 構成モードが BOTHDSN の場合は、HKEY_CURRENT_USER 試行すると、HKEY_LOCAL_MACHINE が使用されますが失敗した場合。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|システム情報の値を書き込む|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
