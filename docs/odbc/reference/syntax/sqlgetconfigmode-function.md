---
title: 関数を取得する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc11bec24ede3352dd43f3645fb8c720b77fdabe
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285692"
---
# <a name="sqlgetconfigmode-function"></a>SQLGetConfigMode 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 **SQLGetConfigMode は**、ODBC.ini エントリのリスト DSN 値がシステム情報内のどこにあるかを示すコンフィギュレーション モードを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>引数  
 *を使用します。*  
 [出力]コンフィギュレーション モードを含むバッファーへのポインター。 (「コメント」を参照してください。* \*pwConfig モード*の値は次のようになります。  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetConfigMode が**FALSE を返す場合は **、SQL インストーラ エラー**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 この関数は、DSN 値をリストする Odbc.ini エントリがシステム情報内のどこにあるかを判別するために使用されます。 pwConfigMode がODBC_USER_DSN場合、DSN はユーザー DSN であり、関数は HKEY_CURRENT_USERの Odbc.ini エントリから読み取ります。 * \** ODBC_SYSTEM_DSN場合、DSN はシステム DSN であり、関数は HKEY_LOCAL_MACHINE の Odbc.ini エントリから読み取ります。 ODBC_BOTH_DSN場合、HKEY_CURRENT_USER試行され、失敗した場合はHKEY_LOCAL_MACHINEが使用されます。  
  
 既定では **、ODBC_BOTH_DSNを**返します。 **SQLConfigDataSource**の呼び出しによってユーザー DSN またはシステム DSN が作成されると、DSN の変更中にユーザーとシステム DSN を区別するために、構成モードが ODBC_USER_DSN またはODBC_SYSTEM_DSNに設定されます。 戻る前に、**構成**モードをODBC_BOTH_DSNにリセットします。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|構成モードの設定|[設定モード](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
