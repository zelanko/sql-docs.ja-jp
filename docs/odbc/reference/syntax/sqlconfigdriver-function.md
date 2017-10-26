---
title: "SQLConfigDriver 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9dd30a466fefda6f8b100fdd9595e9ab65e4d85f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlconfigdriver-function"></a>SQLConfigDriver 関数
**準拠**  
 2.5 ODBC のバージョンで導入されました。  
  
 **概要**  
 **SQLConfigDriver** 、適切なドライバーのセットアップ DLL と呼び出しを読み込み、 **ConfigDriver**関数。  
  
 機能**SQLConfigDriver**にアクセスすることも[ODBCCONF です。EXE](../../../odbc/odbcconf-exe.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 [入力]親ウィンドウ ハンドル。 関数では、ハンドルが null の場合、ダイアログ ボックスは表示されません。  
  
 *起こり*  
 [入力]要求の種類。 *起こり*値は次のいずれかを含める必要があります。  
  
 ODBC_CONFIG_DRIVER: は、接続プール、ドライバーによって使用されるタイムアウトを変更します。  
  
 ODBC_INSTALL_DRIVER: は、新しいドライバーをインストールします。  
  
 ODBC_REMOVE_DRIVER: は、既存のドライバーを削除します。  
  
 このオプションはドライバー固有を場合にも、*起こり*最初のオプションが ODBC_CONFIG_DRIVER_MAX は + 1 から開始する必要があります。 *起こり*ODBC_CONFIG_DRIVER_MAX は + 1 より大きい値から、追加のオプションを開始する必要がありますも用です。  
  
 *lpszDriver*  
 [入力]システム情報に登録されているドライバーの名前。  
  
 *lpszArgs*  
 [入力]ドライバー固有の引数を表す null で終わる文字列*起こり*です。  
  
 *lpszMsg*  
 [出力]ドライバーのセットアップからの出力メッセージを表す null で終わる文字列。  
  
 *cbMsgMax*  
 [入力]長さ*lpszMsg です。*  
  
 *pcbMsgOut*  
 [出力]返される使用可能なバイトの合計数*lpszMsg*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*cbMsgMax*、内の出力メッセージ*lpszMsg*に切り捨てられます*cbMsgMax* null 終了負符号文字があります。 *PcbMsgOut*引数が null ポインターを指定できます。  
  
## <a name="returns"></a>返します。  
 関数は、それが成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLConfigDriver**は FALSE を返します、関連付けられている* \*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、 * \*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_BUFF_LEN|無効なバッファーの長さ|*LpszMsg*引数が無効です。|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*HwndParent*引数が無効です。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|無効な要求の種類|*起こり*引数が、次のいずれか。<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> *起こり*引数が ODBC_CONFIG_DRIVER_MAX 少なくドライバー固有のオプションです。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバーまたは変換者の名前|*LpszDriver*引数が無効です。 これをレジストリで見つかりませんでした。|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|無効なキーワードと値のペア|*LpszArgs*引数に構文エラーが含まれています。|  
|ODBC_ERROR_REQUEST_FAILED|*要求*できませんでした|インストーラーでは、要求した操作は実行できませんでした、*起こり*引数。 呼び出し**ConfigDriver**できませんでした。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバーまたはトランスレーター セットアップ ライブラリを読み込むことができませんでした。|ドライバーのセットアップ ライブラリを読み込むことができませんでした。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 **SQLConfigDriver**により、アプリケーションを呼び出してドライバーの**ConfigDriver**名前を知っているし、ドライバー固有のセットアップ DLL をロードすることがなくルーチンです。 セットアップ プログラムは、DLL がインストールされているドライバーのセットアップ後に、この関数を呼び出します。 呼び出し元のプログラムは、この関数が使用できないことのすべてのドライバーに注意してください。 このような場合は、エラーなく呼び出し元のプログラムを続行する必要があります。  
  
## <a name="driver-specific-options"></a>ドライバー固有のオプション  
 アプリケーションが要求するドライバー固有の機能を使用して、ドライバーによって公開されている、*起こり*引数。 *起こり*ODBC_CONFIG_DRIVER_MAX + 1 の場合、最初のオプションは使用し、その他のオプションがその値の 1 つずつ増分されます。 その関数は、null で終わる文字列で指定する必要がありますのドライバーが必要な引数が渡された、 *lpszArgs*引数。 このような機能を提供するドライバーは、ドライバー固有のオプションのテーブルを維持する必要があります。 オプションは、ドライバーのマニュアルで完全に記述する必要があります。 ドライバー固有のオプションを使用しているアプリケーションの作成者を使用すると、アプリケーション小さい相互運用可能な対応にする必要があります。  
  
## <a name="setting-connection-pooling-timeout"></a>接続プールのタイムアウトを設定  
 ドライバーの構成を設定すると、接続プール タイムアウト プロパティを設定できます。 **SQLConfigDriver**してを呼び出すと、*起こり*ODBC_CONFIG_DRIVER のおよび*lpszArgs* 'éý' **CPTimeout**です。 **CPTimeout**接続は、接続プール内で使用されることがなくおくことのできる時間の期間を決定します。 タイムアウトになると、ときに、接続が閉じられ、プールから削除します。 既定のタイムアウトは 60 秒です。  
  
 ときに**SQLConfigDriver**で呼び出された*起こり*ODBC_INSTALL_DRIVER または ODBC_REMOVE_DRIVER に設定すると、ドライバー マネージャーは、適切なドライバーのセットアップ DLL と読み込む呼び出し、 **ConfigDriver**関数。 ときに**SQLConfigDriver**してを呼び出すと、*起こり*ODBC_CONFIG_DRIVER のすべての処理が ODBC インストーラーの実行ドライバーのセットアップ DLL が読み込まれる必要があるないようにします。  
  
## <a name="messages"></a>メッセージ  
 ドライバーのセットアップ ルーチンは null で終わる文字列としてアプリケーションにテキスト メッセージを送信することができます、 *lpszMsg*バッファー。 メッセージに切り捨てられます*cbMsgMax*によって null 終端文字マイナス、 **ConfigDriver**に以上である場合に機能*cbMsgMax*文字です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはドライバーを削除します。|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)で DLL のセットアップ)|  
|既定のデータ ソースを削除します。|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|

