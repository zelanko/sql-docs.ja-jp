---
title: SQLGetTranslator 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 803e823de76deba750dc188c2f01e69b0a2f84db
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgettranslator-function"></a>SQLGetTranslator 関数
**準拠**  
 バージョンが導入されています。 ODBC 2.0  
  
 **概要**  
 **SQLGetTranslator**ユーザーが、変換プログラムを選択できるダイアログ ボックスを表示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
  
 *lpszName*  
 [入力/出力]システム情報の変換プログラムの名前です。  
  
 *cbNameMax*  
 [入力]最大長、 *lpszName*バッファー。  
  
 *pcbNameOut*  
 [入力/出力]\(Null 終了バイトを除く) バイトの合計数が指定値を渡したりで返される*lpszName*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*cbNameMax*で変換プログラム名*lpszName*に切り捨てられます*cbNameMax*マイナス、null 終端文字です。 *PcbNameOut*引数が null ポインターを指定できます。  
  
 *lpszPath*  
 [出力]トランスレーター DLL の完全パス。  
  
 *cbPathMax*  
 [入力]最大長、 *lpszPath*バッファー。  
  
 *pcbPathOut*  
 [出力]合計バイト数 (null 終了バイトを除く) で返される*lpszPath*です。 場合は、使用できるバイト数を返すより大きいまたは等しい*cbPathMax*、翻訳の DLL パス*lpszPath*に切り捨てられます*cbPathMax*マイナス、null 終端文字です。 *PcbPathOut*引数が null ポインターを指定できます。  
  
 *pvOption*  
 [出力] の 32 ビットの変換オプション。  
  
## <a name="returns"></a>返します。  
 関数が正常に終了したが失敗した場合、またはユーザーがダイアログ ボックスを取り消す場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetTranslator**は FALSE を返します、関連付けられている *\*pfErrorCode*を呼び出して値を取得する**SQLInstallerError**です。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とコンテキストでこの関数のいずれかを説明します。  
  
|*\*pfErrorCode*|[エラー]|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーのエラー|エラーが発生する特定のインストーラーのエラーがなかった。|  
|ODBC_ERROR_INVALID_BUFF_LEN|無効なバッファーの長さ|*CbNameMax*または*cbPathMax*引数が 0 未満です。|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*HwndParent*引数が無効または NULL。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバーまたは変換者の名前|*LpszName*引数が無効です。 これをレジストリで見つかりませんでした。|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|ドライバーまたはトランスレーター セットアップ ライブラリを読み込むことができませんでした。|トランスレーター ライブラリを読み込むことができませんでした。|  
|ODBC_ERROR_INVALID_OPTION|無効なトランザクションのオプション|*PvOption*引数に無効な値が含まれています。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|インストーラーは、メモリの不足のため、関数を実行できませんでした。|  
  
## <a name="comments"></a>コメント  
 場合*hwndParent*が null 場合、または*lpszName*、 *lpszPath*、または*pvOption* null ポインターでは、 **SQLGetTranslator** FALSE を返します。 それ以外の場合、次のダイアログ ボックスでインストールされている翻訳の一覧が表示されます。  
  
 ![[翻訳] ダイアログ ボックス](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 場合*lpszName*変換プログラムの有効な名前が含まれていますが選択されています。 それ以外の場合、\<いいえトランスレーター > を選択します。  
  
 ユーザーが選択した場合\<いいえトランスレーター > の内容*lpszName*、 *lpszPath*、および*pvOption*に影響はないです。 **SQLGetTranslator**設定*pcbNameOut*と*pcbPathOut* 0 と TRUE を返します。  
  
 場合は、ユーザーが、このトランスレータ**SQLGetTranslator**呼び出し**ConfigTranslator**変換プログラムのセットアップ DLL にします。 場合**ConfigTranslator**は FALSE を返します**SQLGetTranslator**ダイアログ ボックスを返します。 場合**ConfigTranslator**に TRUE を返します**SQLGetTranslator**選択した翻訳者名、パス、および翻訳オプションと TRUE を返します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|翻訳者を構成します。|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|翻訳属性の取得|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|翻訳の属性を設定|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
