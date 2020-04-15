---
title: 関数を設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConfigMode
helpviewer_keywords:
- SQLSetConfigMode function [ODBC]
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c36da48fa1493f61131d23a07f7a820b67ebac82
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293282"
---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 **SQLSetConfigMode は**、ODBC.ini エントリの DSN 値がシステム情報のどこにあるかを示すコンフィギュレーション モードを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>引数  
 *モード*  
 [入力]インストーラーの構成モード (「コメント」を参照)。 *wConfigMode*の値は次のようになります。  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLSetConfigMode が**FALSE を返す場合は、SQL インストーラ**エラー**を呼び出すことによって、関連付けられた*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|無効なパラメータ シーケンス|*引数に*ODBC_USER_DSN、ODBC_SYSTEM_DSN、またはODBC_BOTH_DSNが含まれていませんでした。|  
  
## <a name="comments"></a>説明  
 この関数は、DSN 値をリストする Odbc.ini エントリがシステム情報内のどこにあるかを設定するために使用されます。 *wConfigMode*がODBC_USER_DSN場合、DSN はユーザー DSN であり、関数はHKEY_CURRENT_USERの Odbc.ini エントリから読み取ります。 ODBC_SYSTEM_DSN場合、DSN はシステム DSN であり、関数は HKEY_LOCAL_MACHINE の Odbc.ini エントリから読み取ります。 ODBC_BOTH_DSNの場合は、HKEY_CURRENT_USER試行され、失敗した場合は、HKEY_LOCAL_MACHINEが使用されます。  
  
 この関数は **、データ ソース**と**SQL ドライバー接続**には影響しません。 構成モードは、ドライバーが**SQLGetPrivateProfileString**を呼び出すことによってレジストリから読み取る場合、または**SQLWritePrivateProfileString**を呼び出すことによってレジストリに書き込む場合に設定する必要があります。 **呼**び出しは、構成モード**を使用して**、レジストリのどの部分を操作するかを知ります。  
  
> [!CAUTION]  
>  **必要な**場合にのみ呼び出す必要があります。モードが正しく設定されていない場合、ODBC インストーラが正しく機能しない可能性があります。  
  
 **構成モードの**レジストリを直接変更します。 これは **、SQLConfigDataSource**の呼び出しによって構成モードを変更するプロセスとは別です。 **SQLConfigDataSource**の呼び出しは、DSN を変更するときにユーザー DSN とシステム DSN を区別するコンフィギュレーション モードを設定します。 戻る前に、**構成**モードを BOTHDSN にリセットします。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|データ ソースの作成|[データ ソースを作成します。](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|接続文字列またはダイアログ ボックスを使用したデータ ソースへの接続|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|コンフィギュレーション モードの取得|[モード](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
