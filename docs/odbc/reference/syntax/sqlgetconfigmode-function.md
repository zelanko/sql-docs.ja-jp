---
title: SQLGetConfigMode 関数 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285692"
---
# <a name="sqlgetconfigmode-function"></a>SQLGetConfigMode 関数
**互換性**  
 導入されたバージョン: ODBC 3.0  
  
 **まとめ**  
 **Sqlgetconfigmode**は、DSN 値を一覧表示する Odbc .ini エントリのシステム情報の場所を示す構成モードを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>引数  
 *pwConfigMode*  
 Output構成モードを格納しているバッファーへのポインター。 (「コメント」を参照してください)。* \*PwConfigMode*の値は次のようになります。  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>戻り値  
 関数は、成功した場合は TRUE、失敗した場合は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **Sqlgetconfigmode**から FALSE が返された場合、 **sqlインストーラエラー**を呼び出すことによって、関連* \*する pferrorcode*値を取得できます。 次の表は、 **sqlインストーラエラー**によって返される可能性がある* \*pferrorcode*値と、この関数のコンテキストにおけるそれぞれの値を示しています。  
  
|*\*pfErrorCode*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラーで関数を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 この関数は、DSN 値を一覧表示する Odbc .ini エントリのシステム情報内の場所を決定するために使用されます。 * \*PwConfigMode*が ODBC_USER_DSN 場合、dsn はユーザー dsn で、関数は HKEY_CURRENT_USER の ODBC .ini エントリから読み取ります。 ODBC_SYSTEM_DSN の場合、DSN はシステム DSN で、関数は HKEY_LOCAL_MACHINE の Odbc .ini エントリから読み取ります。 ODBC_BOTH_DSN 場合は HKEY_CURRENT_USER が試行され、失敗した場合は HKEY_LOCAL_MACHINE が使用されます。  
  
 既定では、 **Sqlgetconfigmode**は ODBC_BOTH_DSN を返します。 ユーザー DSN またはシステム DSN が**Sqlconfigdatasource**への呼び出しによって作成された場合、関数は、構成モードを ODBC_USER_DSN または ODBC_SYSTEM_DSN に設定して、dsn を変更するときにユーザーとシステムの dsn を区別します。 返される前に、 **Sqlconfigdatasource**によって構成モードが ODBC_BOTH_DSN にリセットされます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|解決方法については、|  
|---------------------------|---------|  
|構成モードの設定|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
