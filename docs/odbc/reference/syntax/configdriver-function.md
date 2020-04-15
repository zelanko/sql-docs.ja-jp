---
title: コンフィグドライバ関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDriver
helpviewer_keywords:
- ConfigDriver [ODBC]
ms.assetid: 9473f48f-bcae-4784-89c1-7839bad4ed13
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a2da5fd5ce01bd97f13d7c8d805c615c1ac436a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303963"
---
# <a name="configdriver-function"></a>ConfigDriver 関数
**適合 性**  
 バージョン導入: ODBC 2.5  
  
 **まとめ**  
 **ConfigDriver**を使用すると、セットアップ プログラムは**ConfigDSN**を呼び出す必要なく、インストールおよびアンインストールの機能を実行できます。 この関数は、ドライバ固有のシステム情報の作成やインストール中の DSN 変換の実行、アンインストール中のシステム情報の変更のクリーンアップなど、ドライバ固有の機能を実行します。 この関数は、ドライバー セットアップ DLL または別のセットアップ DLL によって公開されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL ConfigDriver(  
      HWND    hwndParent,  
      WORD    fRequest,  
      LPCSTR  lpszDriver,  
      LPCSTR  lpszArgs,  
      LPSTR   lpszMsg,  
      WORD    cbMsgMax,  
      WORD *  pcbMsgOut);  
```  
  
## <a name="arguments"></a>引数  
 *hwndParent*  
 [入力]親ウィンドウ ハンドル。 ハンドルが null の場合、この関数はダイアログ ボックスを表示しません。  
  
 *リクエスト*  
 [入力]要求の種類。 *fRequest*引数には、次のいずれかの値を指定する必要があります。  
  
 ODBC_INSTALL_DRIVER: 新しいドライバをインストールします。  
  
 ODBC_REMOVE_DRIVER: ドライバを削除します。  
  
 このオプションはドライバー固有のオプションでも可能で、その場合は最初のオプションの*fRequest*引数を ODBC_CONFIG_DRIVER_MAX+1 から始める必要があります。 追加オプションの*fRequest*引数も、ODBC_CONFIG_DRIVER_MAX+1 より大きい値から始める必要があります。  
  
 *ドライバー*  
 [入力]システム情報の Odbcinst.ini キーに登録されているドライバーの名前。  
  
 *lpszArgs*  
 [入力]ドライバー固有の*fRequest*の引数を含む null で終わる文字列。  
  
 *をクリックします。*  
 [出力]ドライバーのセットアップからの出力メッセージを含む null で終わる文字列。  
  
 *最大*  
 [入力]*の*長さ。  
  
 *を使用します。*  
 [出力]*lpszMsg*で返されるバイト数の合計。  
  
 戻り値として使用可能なバイト数が*cbMsgMax*以上の場合 *、lpszMsg*の出力メッセージは *、cbMsgMax*からヌル終了文字を引いた値まで切り捨てられます。 *引数*は null ポインターにすることができます。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **設定ドライバーが**FALSE を返すと、関連付けられた*\*pfErrorCode*値は **、SQLPostInstallerError エラー**の呼び出しによってインストーラー エラー バッファーにポストされ **、SQLInstallerError**を呼び出すことによって取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*引数 hwndParent*が無効でした。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な種類の要求|*fRequest*引数は、次の引数の 1 つではありません。<br /><br /> ODBC_INSTALL_DRIVERODBC_REMOVE_DRIVER<br /><br /> ドライバ固有のオプションがODBC_CONFIG_DRIVER_MAX以下でした。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバまたはトランスレータ名|*引数が*無効です。 レジストリに見つかりませんでした。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*に失敗しました|*fRequest*引数によって要求された操作を実行できませんでした。|  
|ODBC_ERROR_DRIVER_SPECIFIC|ドライバまたはトランスレータ固有のエラー|定義された ODBC インストーラー エラーがないドライバー固有のエラー。 関数の呼び出しで*SzError*引数には、ドライバー固有のエラー メッセージが含まれている必要があります。 **SQLPostInstallerError**|  
  
## <a name="comments"></a>説明  
  
### <a name="driver-specific-options"></a>ドライバ固有のオプション  
 アプリケーションは *、fRequest*引数を使用して、ドライバーによって公開ドライバー固有の機能を要求できます。 最初のオプションの*fRequest*は ODBC_CONFIG_DRIVER_MAX + 1 になり、追加のオプションはその値から 1 ずつ増えます。 その関数のドライバーが必要とする引数は *、引数 lpszArgs*に渡される null で終了した文字列で指定する必要があります。 このような機能を提供するドライバーは、ドライバー固有のオプションのテーブルを維持する必要があります。 オプションは、ドライバのドキュメントに完全に記載されている必要があります。 ドライバー固有のオプションを使用するアプリケーション作成者は、アプリケーションの相互運用性が低下することを認識する必要があります。  
  
### <a name="messages"></a>メッセージ  
 ドライバーのセットアップ ルーチンは *、lpszMsg*バッファーで null で終了文字列としてアプリケーションにテキスト メッセージを送信できます。 メッセージは *、cbMsgMax*文字以上の場合は **、cbMsgMax**から Null 終端文字を引いた値に切*cbMsgMax*り捨てられます。
