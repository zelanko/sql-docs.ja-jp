---
title: コンフィグトランスレータ機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigTranslator
helpviewer_keywords:
- ConfigTranslator [ODBC]
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb2f26f87854d74a217885010014633963472787
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306033"
---
# <a name="configtranslator-function"></a>ConfigTranslator 関数
**適合 性**  
 バージョン導入: ODBC 2.0  
  
 **まとめ**  
 **トランスレータの**デフォルトの変換オプションを返します。 トランスレータ DLL または別のセットアップ DLL に含めることができます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>引数  
 *hwndParent*  
 [入力]親ウィンドウ ハンドル。 ハンドルが null の場合、この関数はダイアログ ボックスを表示しません。  
  
 *オプション*  
 [出力]32 ビット変換オプション。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **コントランスレータが**FALSE を返すと、関連付けられた*\*pfErrorCode*値が**SQLPostInstallerErrorError**の呼び出しによってインストーラー エラー バッファにポストされ **、SQLInstallerError**を呼び出すことによって取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*引数 hwndParent*が無効であるか、NULL でした。|  
|ODBC_ERROR_DRIVER_SPECIFIC|ドライバまたはトランスレータ固有のエラー|定義された ODBC インストーラー エラーがないドライバー固有のエラー。 関数の呼び出しで*SzError*引数には、ドライバー固有のエラー メッセージが含まれている必要があります。 **SQLPostInstallerError**|  
|ODBC_ERROR_INVALID_OPTION|無効な変換オプション|*pvOption*引数に無効な値が含まれています。|  
  
## <a name="comments"></a>説明  
 トランスレータが 1 つの変換オプションのみをサポートしている場合 **、True が**返され *、pvOption*が 32 ビット オプションに設定されます。 それ以外の場合は、使用する既定の変換オプションが決定されます。 **ユーザー**がデフォルトの翻訳オプションを選択するダイアログボックスを表示できます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|翻訳オプションの取得|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|翻訳者の選択|[トランスレータを取得します。](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|翻訳オプションの設定|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
