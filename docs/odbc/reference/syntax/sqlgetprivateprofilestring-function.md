---
title: 関数を取得する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetPrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetPrivateProfileString
helpviewer_keywords:
- SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c12fc8d08535960cbb239c14e017b2ad5faa6c0e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303294"
---
# <a name="sqlgetprivateprofilestring-function"></a>SQLGetPrivateProfileString 関数
**適合 性**  
 バージョン導入: ODBC 2.0  
  
 **まとめ**  
 システム情報の値に対応する値またはデータの名前の一覧**を取得します**。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
int SQLGetPrivateProfileString(  
     LPCSTR   lpszSection,  
     LPCSTR   lpszEntry,  
     LPCSTR   lpszDefault,  
     LPCSTR   RetBuffer,  
     INT      cbRetBuffer,  
     LPCSTR   lpszFilename);  
```  
  
## <a name="arguments"></a>引数  
 *セクション*  
 [入力]キー名を含むセクションを指定する null で終わる文字列へのポイント。 この引数が NULL の場合、この関数は、ファイル内のすべてのセクション名を指定されたバッファーにコピーします。  
  
 *をクリックします。*  
 [入力]関連付けられた文字列を取得するキー名を含む null で終わる文字列へのポイント。 この引数が NULL の場合、*引数 lpszSection*で指定されたセクション内のすべてのキー名が *、RetBuffer*引数で指定されたバッファーにコピーされます。  
  
 *デフォルト*  
 [入力]初期化ファイルでキーが見つからない場合に、指定されたキーの既定値を指定する null で終わる文字列を指します。 この引数を NULL にすることはできません。  
  
 *バッファ*  
 [出力]取得した文字列を受け取るバッファーへのポイント。  
  
 *バッファバッファ*  
 [入力]*引数 RetBuffer*によって指されるバッファーのサイズを文字で指定します。  
  
 *ファイル名*  
 [入力]初期化ファイルの名前を指定する null で終わる文字列を指します。 この引数にファイルへの完全パスが含まれていない場合は、デフォルトのディレクトリが検索されます。  
  
## <a name="returns"></a>戻り値  
 読み取**った**文字数を示す整数値を返します。  
  
## <a name="diagnostics"></a>診断  
 **呼**び出しが失敗した場合は、SQL**インストーラ エラー**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **ドライバー**とドライバーセットアップ DLL を Microsoft ® Windows ® から Windows NT ®/Windows 2000 に移植する簡単な方法として提供されています。 Odbc.ini ファイルからプロファイル文字列を取得する**呼**び出しは、**呼**び出しに置き換える必要があります。 **Win32®** API の関数を呼び出して、システム情報の Odbc.ini サブキーの値に対応する値またはデータの要求された名前を取得します。  
  
 構成モード **(SQLSetConfigMode**によって設定) は、DSN 値をリストする Odbc.ini エントリがシステム情報内のどこにあるかを示します。 DSN がユーザ DSN の場合 (コンフィギュレーション モードがUSERDSN_ONLY)、関数はHKEY_CURRENT_USERの Odbc.ini エントリから読み取ります。 DSN がシステム DSN (SYSTEMDSN_ONLY) の場合、この関数は HKEY_LOCAL_MACHINE の Odbc.ini エントリから読み取ります。 コンフィギュレーション モードが BOTHDSN の場合、HKEY_CURRENT_USER試行され、失敗した場合は、HKEY_LOCAL_MACHINEが使用されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|システム情報への値の書き込み|[文字列](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
