---
title: "ConfigDriver 関数 |Microsoft ドキュメント"
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
- ConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDriver
helpviewer_keywords:
- ConfigDriver [ODBC]
ms.assetid: 9473f48f-bcae-4784-89c1-7839bad4ed13
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 037d4ffcbe7d81c6e4a9c1a524f5f4977621f277
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="configdriver-function"></a>ConfigDriver 関数
**準拠**  
 2.5 ODBC のバージョンで導入されました。  
  
 **概要**  
 **ConfigDriver**により、セットアップ プログラムをインストールを実行し、関数を呼び出すプログラムを必要とせずアンインストール**ConfigDSN**です。 この関数では、ドライバー固有のシステム情報を作成して、インストール中に DSN 変換を実行するだけでなくシステム情報の変更のアンインストール中にクリーンアップなどのドライバー固有の関数を実行します。 この関数は、ドライバーのセットアップ DLL または別のセットアップ DLL によって公開されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 [入力]親ウィンドウ ハンドル。 関数では、ハンドルが null の場合、ダイアログ ボックスは表示されません。  
  
 *起こり*  
 [入力]要求の種類。 *起こり*引数は、次の値のいずれかを含める必要があります。  
  
 ODBC_INSTALL_DRIVER: は、新しいドライバーをインストールします。  
  
 ODBC_REMOVE_DRIVER: は、ドライバーを削除します。  
  
 このオプションはドライバー固有を場合にも、*起こり*ODBC_CONFIG_DRIVER_MAX は + 1 から最初のオプションの引数を開始する必要があります。 *起こり*ODBC_CONFIG_DRIVER_MAX は + 1 より大きい値から、追加のオプションの引数を開始する必要がありますもします。  
  
 *lpszDriver*  
 [入力]システム情報の Odbcinst.ini キーに登録されているドライバーの名前。  
  
 *lpszArgs*  
 [入力]ドライバー固有の引数を含む null で終わる文字列*起こり*です。  
  
 *lpszMsg*  
 [出力]ドライバーのセットアップからの出力メッセージを含む null で終わる文字列。  
  
 *cbMsgMax*  
 [入力]長さ*lpszMsg*です。  
  
 *pcbMsgOut*  
 [出力]返される使用可能なバイトの合計数*lpszMsg*です。  
  
 場合は、使用できるバイト数を返すより大きいまたは等しい*cbMsgMax*、内の出力メッセージ*lpszMsg*に切り捨てられます*cbMsgMax* null 終了負符号文字があります。 *PcbMsgOut*引数が null ポインターを指定できます。  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**ConfigDriver**は FALSE を返します、関連付けられている *\*pfErrorCode*への呼び出しで値がインストーラー エラー バッファーにポストされた**SQLPostInstallerError**呼び出すことによって取得できます**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*HwndParent*引数が無効です。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な要求の種類|*起こり*引数が、次のいずれか。<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> ドライバー固有のオプションは、ODBC_CONFIG_DRIVER_MAX に等しいまたはそれよりも小さいをでした。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバーまたは変換者の名前|*LpszDriver*引数が無効です。 これをレジストリで見つかりませんでした。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*できませんでした|要求した操作を実行できませんでした、*起こり*引数。|  
|ODBC_ERROR_DRIVER_SPECIFIC|ドライバー固有またはトランスレーター エラー|定義された ODBC インストーラーのエラーがないドライバー固有のエラーです。 *SzError*への呼び出しで引数、 **SQLPostInstallerError**関数は、ドライバー固有のエラー メッセージを含める必要があります。|  
  
## <a name="comments"></a>コメント  
  
### <a name="driver-specific-options"></a>ドライバー固有のオプション  
 アプリケーションが要求するドライバー固有の機能を使用して、ドライバーによって公開されている、*起こり*引数。 *起こり*され 1 を加えた ODBC_CONFIG_DRIVER_MAX 最初のオプションが表示されます。 その他のオプションはその値の 1 つずつ増加するのです。 その関数は、null で終わる文字列で指定する必要がありますのドライバーが必要な引数が渡された、 *lpszArgs*引数。 このような機能を提供するドライバーは、ドライバー固有のオプションのテーブルを維持する必要があります。 オプションは、ドライバーのマニュアルで完全に記述する必要があります。 ドライバー固有のオプションを使用するアプリケーション ライターは、この操作を行うアプリケーション小さい相互運用可能な対応にする必要があります。  
  
### <a name="messages"></a>メッセージ  
 ドライバーのセットアップ ルーチンは null で終わる文字列としてアプリケーションにテキスト メッセージを送信することができます、 *lpszMsg*バッファー。 メッセージに切り捨てられます*cbMsgMax*によって null 終端文字マイナス、 **ConfigDriver**に以上である場合に機能*cbMsgMax*文字です。

