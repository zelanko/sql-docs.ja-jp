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
- SQLConfigDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- SQLConfigDataSource function [ODBC]
ms.assetid: f8d6e342-c010-434e-b1cd-f5371fb50a14
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90a51193a8f4edbb013527c4dde0625b75131583
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299632"
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource 関数
**適合 性**  
 バージョン導入: ODBC 1.0  
  
 **まとめ**  
 **データ ソースを**追加、変更、または削除します。  
  
 **SQLConfig データ ソース**の機能には、ODBCCONF を使用してアクセスすることもできます[。EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLConfigDataSource(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>引数  
 *hwndParent*  
 [入力]親ウィンドウ ハンドル。 ハンドルが null の場合、この関数はダイアログ ボックスを表示しません。  
  
 *リクエスト*  
 [入力]要求の種類。 *fRequest*引数には、次のいずれかの値を指定する必要があります。  
  
 ODBC_ADD_DSN: 新しいユーザー データ ソースを追加します。  
  
 ODBC_CONFIG_DSN: 既存のユーザー データ ソースを構成 (変更) します。  
  
 ODBC_REMOVE_DSN: 既存のユーザー データ ソースを削除します。  
  
 ODBC_ADD_SYS_DSN: 新しいシステム データ ソースを追加します。  
  
 ODBC_CONFIG_SYS_DSN: 既存のシステム データ ソースを変更します。  
  
 ODBC_REMOVE_SYS_DSN: 既存のシステム データ ソースを削除します。  
  
 ODBC_REMOVE_DEFAULT_DSN: システム情報から既定のデータ ソース仕様セクションを削除します。 (システム情報の Odbcinst.ini エントリから既定のドライバーの仕様セクションも削除されます。 この*fRequest は*、廃止された**SQLRemoveDefaultDataSource**関数と同じ関数を実行します。このオプションを指定すると、呼び出しで **、他**のすべてのパラメーターは、ヌルである必要があります。NULL でない場合は無視されます。  
  
 *ドライバー*  
 [入力]物理ドライバ名の代わりに、ドライバの説明 (通常は関連付けられた DBMS の名前) をユーザーに表示します。  
  
 *属性*  
 [入力]キーワードと値のペアの形式での属性の二重に終端された一覧。 詳細については、 [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)を参照してください。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。 この関数が呼び出されたときにシステム情報にエントリが存在しない場合、この関数は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLConfigDataSource が**FALSE を返すと、SQL**インストーラ エラー**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*引数 hwndParent*が無効であるか、NULL でした。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な種類の要求|*fRequest*引数は、次の引数の 1 つではありません。<br /><br /> ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSNODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSNODBC_CONFIG_DSN ODBC_REMOVE_DSNODBC_CONFIG_DSNODBC_ADD_SYS_DSNODBC_ADD_DSN|  
|ODBC_ERROR_INVALID_NAME|無効なドライバまたはトランスレータ名|*引数が*無効です。 レジストリに見つかりませんでした。|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*引数 lpszAttributes*に構文エラーが含まれていました。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*に失敗しました|インストーラーは *、fRequest*引数によって要求された操作を実行できませんでした。 **ConfigDSN**への呼び出しに失敗しました。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバまたはトランスレータセットアップライブラリを読み込めませんでした|ドライバ セットアップ ライブラリを読み込めませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **ドライバー**のセットアップ DLL の完全なパスをシステム情報から読み取るために*lpszDriver*の値を使用します。 DLL を読み込み、渡された引数と同じ引数を使用して**ConfigDSN**を呼び出します。  
  
 **セットアップ**DLL を検索または読み込むことができない場合、またはユーザーがダイアログ ボックスをキャンセルした場合は、FALSE を返します。 それ以外の場合は **、ConfigDSN**から受信した状態を返します。  
  
 **SQLConfigDataSource は**、システム DSN *fRequest*s をユーザー DSN *fRequest*s にマップします (ODBC_ADD_DSN、ODBC_CONFIG_SYS_DSNをODBC_CONFIG_DSNに、ODBC_REMOVE_SYS_DSNをODBC_REMOVE_DSNにODBC_ADD_SYS_DSN)。 ユーザー DSN とシステム DSN を区別するために、**次**の表に従ってインストーラーの構成モードを設定します。 戻る前に、**構成**モードを BOTHDSN にリセットします。 (ドライバーによって実装される)**構成DSN**は、システム DSN をサポートするために**SQLWriteDSNToIni**と**SQLWritePrivateProfileString**を呼び出す必要があります。 詳細については、 [ConfigDSN 関数](../../../odbc/reference/syntax/configdsn-function.md)を参照してください。  
  
|*リクエスト*|コンフィギュレーション モード|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースの追加、変更、または削除|[(](../../../odbc/reference/syntax/configdsn-function.md)セットアップ DLL 内) の構成 DSN|  
|システム情報からのデータ・ソース名の除去|[イニから削除します。](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|システム情報へのデータ・ソース名の追加|[を使用します。](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
