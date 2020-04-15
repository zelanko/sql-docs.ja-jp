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
- SQLConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDriver
helpviewer_keywords:
- SQLConfigDriver function [ODBC]
ms.assetid: 4f681961-ac9f-4d88-b065-5258ba112642
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0da15cef06e5d8392408108ce88b53f7885eb65e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301247"
---
# <a name="sqlconfigdriver-function"></a>SQLConfigDriver 関数
**適合 性**  
 バージョン導入: ODBC 2.5  
  
 **まとめ**  
 **適切**なドライバー セットアップ DLL を読み込み、**関数**を呼び出します。  
  
 **SQL コンフィグドライバー**の機能には、ODBCCONF を使用してアクセスすることもできます[。EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLConfigDriver(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszArgs,  
     LPSTR    lpszMsg,  
     WORD     cbMsgMax,  
     WORD *   pcbMsgOut);  
```  
  
## <a name="arguments"></a>引数  
 *hwndParent*  
 [入力]親ウィンドウ ハンドル。 ハンドルが null の場合、この関数はダイアログ ボックスを表示しません。  
  
 *リクエスト*  
 [入力]要求の種類。 *fRequest には*、次のいずれかの値が含まれている必要があります。  
  
 ODBC_CONFIG_DRIVER: ドライバが使用する接続プールタイムアウトを変更します。  
  
 ODBC_INSTALL_DRIVER: 新しいドライバをインストールします。  
  
 ODBC_REMOVE_DRIVER: 既存のドライバを削除します。  
  
 このオプションは、ドライバー固有の場合もありますが、その場合、最初のオプションの*fRequest*は ODBC_CONFIG_DRIVER_MAX+1 から始まる必要があります。 追加オプションの*fRequest*も、ODBC_CONFIG_DRIVER_MAX+1 より大きい値から開始する必要があります。  
  
 *ドライバー*  
 [入力]システム情報に登録されているドライバの名前。  
  
 *lpszArgs*  
 [入力]ドライバー固有の*fRequest*の引数を含む null で終わる文字列。  
  
 *をクリックします。*  
 [出力]ドライバーのセットアップからの出力メッセージを含む null で終わる文字列。  
  
 *最大*  
 [入力]の長さ *。*  
  
 *を使用します。*  
 [出力]*lpszMsg*で返されるバイト数の合計。 戻り値として使用可能なバイト数が*cbMsgMax*以上の場合 *、lpszMsg*の出力メッセージは *、cbMsgMax*からヌル終了文字を引いた値まで切り捨てられます。 *引数*は null ポインターにすることができます。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLConfigDriver が**FALSE を返すときは、SQL**インストーラ エラー**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_BUFF_LEN|バッファ長が無効です|*引数が*無効です。|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*引数 hwndParent*が無効でした。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な種類の要求|*fRequest*引数は、次の引数の 1 つではありません。<br /><br /> ODBC_INSTALL_DRIVERODBC_REMOVE_DRIVER<br /><br /> *fRequest*引数は、ODBC_CONFIG_DRIVER_MAX以下のドライバー固有のオプションでした。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバまたはトランスレータ名|*引数が*無効です。 レジストリに見つかりませんでした。|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*引数 lpszArgs*に構文エラーが含まれています。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*に失敗しました|インストーラーは *、fRequest*引数によって要求された操作を実行できませんでした。 **コンフィグドライバー**への呼び出しに失敗しました。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバまたはトランスレータセットアップライブラリを読み込めませんでした|ドライバ セットアップ ライブラリを読み込めませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **SQLConfigDriver**を使用すると、アプリケーションは、名前を知らなくても、ドライバーの**ConfigDriver**ルーチンを呼び出し、ドライバー固有のセットアップ DLL を読み込むことができます。 セットアップ プログラムは、ドライバ セットアップ DLL がインストールされた後にこの関数を呼び出します。 呼び出し元のプログラムは、この関数がすべてのドライバーで使用できるわけではない可能性があることを認識する必要があります。 このような場合、呼び出し元のプログラムはエラーなしで続行する必要があります。  
  
## <a name="driver-specific-options"></a>ドライバ固有のオプション  
 アプリケーションは *、fRequest*引数を使用して、ドライバーによって公開ドライバー固有の機能を要求できます。 最初のオプションの*fRequest*は ODBC_CONFIG_DRIVER_MAX+1 になり、追加のオプションはその値から 1 ずつ増えます。 その関数のドライバーが必要とする引数は *、引数 lpszArgs*に渡される null で終了した文字列で指定する必要があります。 このような機能を提供するドライバーは、ドライバー固有のオプションのテーブルを維持する必要があります。 オプションは、ドライバのドキュメントに完全に記載されている必要があります。 ドライバー固有のオプションを使用するアプリケーション作成者は、この使用によってアプリケーションの相互運用性が低下することを認識する必要があります。  
  
## <a name="setting-connection-pooling-timeout"></a>接続プールタイムアウトの設定  
 接続プールのタイムアウト プロパティは、ドライバーの構成を設定するときに設定できます。 **ODBC_CONFIG_DRIVER**の*fRequest*と*lpszArgs*が**CPTimeout**に設定された状態で呼び出されます。 **CPTimeout**は、接続が使用されずに接続プールに残ることができる期間を決定します。 タイムアウトが経過すると、接続は閉じられ、プールから削除されます。 デフォルトのタイムアウトは 60 秒です。  
  
 ODBC_INSTALL_DRIVERまたはODBC_REMOVE_DRIVERに設定された*fRequest*を使用して**SQLConfigDriver**が呼び出されると、ドライバー マネージャーは適切なドライバー セットアップ DLL を読み込み **、ConfigDriver**関数を呼び出します。 *fRequest*を ODBC_CONFIG_DRIVER指定して**sqlConfigDriver**が呼び出されると、すべての処理が ODBC インストーラーで実行されるため、ドライバーセットアップ DLL を読み込む必要はありません。  
  
## <a name="messages"></a>メッセージ  
 ドライバーのセットアップ ルーチンは *、lpszMsg*バッファーで null で終了文字列としてアプリケーションにテキスト メッセージを送信できます。 メッセージは *、cbMsgMax*文字以上の場合は **、cbMsgMax**から Null 終端文字を引いた値に切*cbMsgMax*り捨てられます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ドライバーの追加、変更、または削除|[構成ドライバー](../../../odbc/reference/syntax/configdriver-function.md)(セットアップ DLL 内)|  
|既定のデータ ソースを削除する|[データ ソースを削除します。](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|
