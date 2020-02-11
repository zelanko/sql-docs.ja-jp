---
title: SQLGetTranslator 関数 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f769d3c5b2dcfe5d2aa8a431695cb18a52893b91
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030650"
---
# <a name="sqlgettranslator-function"></a>SQLGetTranslator 関数
**互換性**  
 導入されたバージョン: ODBC 2.0  
  
 **まとめ**  
 [ **Sqlgettranslator** ] ユーザーが翻訳者を選択できるダイアログボックスが表示されます。  
  
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
 代入親ウィンドウハンドル。  
  
 *lpszName*  
 [入力/出力]システム情報からの変換プログラムの名前。  
  
 *cbNameMax*  
 代入*Lpszname*バッファーの最大長。  
  
 *pcbNameOut*  
 [入力/出力]*Lpszname*で渡された (null 終了バイトを除く) 合計バイト数。 返される使用可能なバイト数が*cbNameMax*以上の場合、 *lpszname*の翻訳者名は、 *cbNameMax*から null 終了文字を引いた値に切り捨てられます。 *Pcbnameout*引数は null ポインターにすることができます。  
  
 *lpszPath*  
 Output変換 DLL の完全パスです。  
  
 *cbPathMax*  
 代入*Lpszpath*バッファーの最大長。  
  
 *pcbPathOut*  
 Output*Lpszpath*で返された合計バイト数 (null 終端バイトを除く)。 返される使用可能なバイト数が*Cbpathmax*以上の場合、 *lpszpath*内の翻訳 DLL パスは、 *cbpathmax*から null 終了文字を引いた値に切り捨てられます。 *Pcbpathout*引数は null ポインターにすることができます。  
  
 *pvOption*  
 [出力] 32-ビット変換オプション。  
  
## <a name="returns"></a>戻り値  
 関数は、成功した場合は TRUE を返し、失敗した場合、またはユーザーがダイアログボックスをキャンセルした場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **Sqlgettranslator**から FALSE が返された場合、 **sqlインストーラエラー**を呼び出すことによって、関連* \*する pferrorcode*値を取得できます。 次の表は、 **sqlインストーラエラー**によって返される可能性がある* \*pferrorcode*値と、この関数のコンテキストにおけるそれぞれの値を示しています。  
  
|*\*pfErrorCode*|エラー|[説明]|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーエラー|特定のインストーラーエラーがなかったためにエラーが発生しました。|  
|ODBC_ERROR_INVALID_BUFF_LEN|バッファーの長さが無効です|*CbNameMax*または*cbpathmax*引数が0以下でした。|  
|ODBC_ERROR_INVALID_HWND|ウィンドウハンドルが無効です|*HwndParent*引数が無効であるか、NULL でした。|  
|ODBC_ERROR_INVALID_NAME|ドライバーまたは翻訳者名が無効です|*Lpszname*引数が無効でした。 レジストリに見つかりませんでした。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバーまたはトランスレーターセットアップライブラリを読み込めませんでした|トランスレーターライブラリを読み込めませんでした。|  
|ODBC_ERROR_INVALID_OPTION|無効なトランザクションオプション|*Pvoption*引数に無効な値が含まれています。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラーで関数を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 *HwndParent*が null の場合、または*lpszname*、 *Lpszname*、または*Pvoption*が null ポインターの場合、 **sqlgettranslator**は FALSE を返します。 それ以外の場合は、次のダイアログボックスにインストールされている翻訳者の一覧が表示されます。  
  
 ![[トランスレーターの選択] ダイアログ ボックス](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 *Lpszname*に有効な変換者名が含まれている場合は、それが選択されます。 それ以外\<の場合は、[トランスレーター> が選択されていません。  
  
 ユーザーがトランスレーター> \<を選択しなかった場合、 *lpszname*、 *Lpszname*、および*pvoption*の内容には影響しません。 **Sqlgettranslator**は*pcbnameout*と*pcbnameout*を0に設定し、TRUE を返します。  
  
 ユーザーがトランスレーターを選択すると、 **Sqlgettranslator**は translator のセットアップ DLL で**configtranslator**を呼び出します。 **Configtranslator**が FALSE を返す場合、 **sqlgettranslator**はそのダイアログボックスに戻ります。 **Configtranslator**によって true が返された場合、 **sqlgettranslator**は、選択した変換プログラムの名前、パス、および翻訳オプションと共に true を返します。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|以下を参照してください。|  
|---------------------------|---------|  
|変換プログラムの構成|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|変換属性の取得|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|変換属性の設定|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
