---
title: 関数の取得 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTranslator
helpviewer_keywords:
- SQLGetTranslator function [ODBC]
ms.assetid: 33879db3-5ef9-4585-9be5-69376157e017
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bcd5aeebab8539b8b94db56ff30892f4a7dbbac1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303273"
---
# <a name="sqlgettranslator-function"></a>SQLGetTranslator 関数
**適合 性**  
 バージョン導入: ODBC 2.0  
  
 **まとめ**  
 **ユーザーがトランスレータ**を選択できるダイアログ ボックスが表示されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLGetTranslator(  
     HWND      hwndParent,  
     LPSTR     lpszName,  
     WORD      cbNameMax,  
     WORD *    pcbNameOut,  
     LPSTR     lpszPath,  
     WORD      cbPathMax,  
     WORD *    pcbPathOut,  
     DWORD *   pvOption);  
```  
  
## <a name="arguments"></a>引数  
 *hwndParent*  
 [入力]親ウィンドウ ハンドル。  
  
 *名前を指定します。*  
 [入出力]システム情報から取得した変換プログラムの名前。  
  
 *cbNameMax*  
 [入力]*lpszName*バッファーの最大長。  
  
 *pcb名アウト*  
 [入出力]*lpszName*で渡されたか返されるバイト数 (null 終了バイトを除く) の合計数。 戻り値として使用可能なバイト数が*cbNameMax*以上の場合 *、lpszName*の変換プログラム名は *、cbNameMax*から NULL 終端文字を引いた値に切り捨てられます。 引数*は*null ポインターにすることができます。  
  
 *パス*  
 [出力]変換 DLL の完全パス。  
  
 *cbパスマックス*  
 [入力]*lpszPath*バッファーの最大長。  
  
 *pcb パスアウト*  
 [出力]*lpszPath*で返されるバイトの総数 (ヌル終了バイトを除く)。 戻り値に使用できるバイト数が*cbPathMax*以上の場合 *、lpszPath*の変換 DLL パスは *、cbPathMax*から NULL 終端文字を引いた値に切り捨てられます。 *引数 pcbPathOut*は、ヌル・ポインターにすることができます。  
  
 *オプション*  
 [出力] 32 ビット変換オプション。  
  
## <a name="returns"></a>戻り値  
 関数は、成功した場合は TRUE を返し、失敗した場合、またはユーザーがダイアログ ボックスをキャンセルした場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetトランスレータ**が FALSE を返すと **、SQLInstallerError**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_INVALID_BUFF_LEN|バッファ長が無効です|引数*が*0*cbPathMax*以下でした。|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*引数 hwndParent*が無効であるか、NULL でした。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバまたはトランスレータ名|*引数が*無効です。 レジストリに見つかりませんでした。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバまたはトランスレータセットアップライブラリを読み込めませんでした|変換プログラム ライブラリを読み込めませんでした。|  
|ODBC_ERROR_INVALID_OPTION|無効なトランザクション オプション|*pvOption*引数に無効な値が含まれています。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 *hwndParent*が null の場合、または*lpszName* *、lpszPath*、または*pvOption*が null ポインターの場合 **、SQLGet トランスレータは**FALSE を返します。 それ以外の場合は、インストールされているトランスレータの一覧が次のダイアログ ボックスに表示されます。  
  
 ![[トランスレーターの選択] ダイアログ ボックス](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 *lpszName*に有効なトランスレータ名が含まれている場合は、それが選択されます。 それ以外\<の場合は、[翻訳>は選択されません。  
  
 ユーザーが[\<翻訳者なし]>を選択した場合 *、lpszName 、lpszPath*、および*pvOption*の内容は触れられません。 *lpszPath* **変換器は***、pcbNameOut*と*pcbPathOut*を 0 に設定し、TRUE を返します。  
  
 ユーザーがトランスレータを選択した場合、**トランスレータ**のセットアップ DLL で**コントランスレータ**が呼び出されます。 **変換プログラムが**FALSE を返した場合、**ダイアログ**ボックスに戻ります。 **TRUE が**返された場合、**選択**したトランスレータ名、パス、および変換オプションと共に TRUE が返されます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|トランスレーターの構成|[コンフィグトランスレータ](../../../odbc/reference/syntax/configtranslator-function.md)|  
|翻訳属性の取得|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|翻訳属性の設定|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
