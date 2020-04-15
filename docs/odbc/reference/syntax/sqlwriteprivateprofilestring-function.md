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
- SQLWritePrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWritePrivateProfileString
helpviewer_keywords:
- SQLWritePrivateProfileString [ODBC]
ms.assetid: 526f36a4-92ed-4874-9725-82d27c0b86f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b0de5ad074fb2b760420686feddff58b26887112
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286885"
---
# <a name="sqlwriteprivateprofilestring-function"></a>SQLWritePrivateProfileString 関数
**適合 性**  
 バージョン導入: ODBC 2.0  
  
 **まとめ**  
 システム情報の Odbc.ini サブキーに値の名前とデータ**を書き**込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLWritePrivateProfileString(  
     LPCSTR     lpszSection,  
     LPCSTR     lpszEntry,  
     LPCSTR     lpszString,  
     LPCSTR     lpszFilename);  
```  
  
## <a name="arguments"></a>引数  
 *セクション*  
 [入力]文字列のコピー先となるセクションの名前を含む null で終わる文字列へのポイント。 セクションが存在しない場合は、作成されます。 セクションの名前は大文字と小文字は独立しています。文字列は、大文字と小文字の任意の組み合わせにすることができます。  
  
 *をクリックします。*  
 [入力]文字列に関連付けるキーの名前を含む null で終わる文字列へのポイント。 指定したセクションにキーが存在しない場合は、そのキーが作成されます。 この引数が NULL の場合、セクション内のすべてのエントリを含むセクション全体が削除されます。  
  
 *文字列*  
 [入力]ファイルに書き込まれる null で終わる文字列へのポイント。 この引数が NULL の場合は、引数*lpszEntry*が指すキーが削除されます。  
  
 *ファイル名*  
 [出力]初期化ファイルの名前を指定する null で終わる文字列を指します。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **FALSE を**返すと、関連付けられた*\*pfErrorCode*値を取得**できます。** 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_REQUEST_FAILED|要求が失敗しました|要求されたシステム情報を書き込めませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **ドライバー**とドライバーセットアップ DLL を Microsoft から Windows nt®/Windows 2000 に移植する簡単な方法として提供®Windows®。 Odbc.ini ファイルにプロファイル文字列を書き込む**WritePrivateProfileString**の呼び出しは **、SQLWritePrivateProfileString**への呼び出しに置き換える必要があります。 **指定**した値の名前とデータをシステム情報の Odbc.ini サブキーに追加する関数を Win32® API で呼び出します。  
  
 コンフィギュレーション モードは、DSN 値を示す Odbc.ini エントリがシステム情報内のどこにあるかを示します。 DSN がユーザー DSN (状態変数がUSERDSN_ONLY) の場合、関数は HKEY_CURRENT_USERの Odbc.ini エントリに書き込みます。 DSN がシステム DSN (SYSTEMDSN_ONLY) の場合、関数は HKEY_LOCAL_MACHINE の Odbc.ini エントリに書き込みます。 状態変数が BOTHDSN の場合、HKEY_CURRENT_USER試行され、失敗した場合は、HKEY_LOCAL_MACHINEが使用されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|システム情報から値を取得する|[文字列](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
