---
title: マッピング |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91264cee0dfceeb7195e2bad40d1638a88e1e01a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304903"
---
# <a name="sqlsetstmtoption-mapping"></a>SQLSetStmtOption のマッピング
アプリケーションが ODBC *3.x*ドライバを使用して**SQLSetStmtOption**を呼び出すと、次の  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 次のように結果が返されます。  
  
-   *fOption*が文字列である ODBC 定義のステートメント属性を示す場合、ドライバー マネージャーは、文字列  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   *fOption*が 32 ビット整数値を返す ODBC 定義のステートメント属性を示す場合、ドライバー マネージャーは、32 ビットの整数値を呼び出します。  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   *fOption*がドライバ定義のステートメント属性を示す場合、ドライバー マネージャーは  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 前の 3 つのケースでは、**引数引数**が*hstmt*の値に設定され、 *Attribute*引数は*fOption*の値に設定され *、ValuePtr*引数は*vParam*として値に設定されます。  
  
 ドライバー マネージャーは、ドライバー定義ステートメント属性が文字列または 32 ビット整数値を必要とするかどうかを知らないので **、SQLSetStmtAttr**の*StringLength*引数に有効な値を渡す必要があります。 ドライバーが定義した、ドライバー定義ステートメント属性の特別なセマンティクスを定義し **、SQLSetStmtOption**を使用して呼び出す必要がある場合は **、SQLSetStmtOption**をサポートする必要があります。  
  
 アプリケーションが**SQLSetStmtOption**を呼び出して ODBC *3.x*ドライバーでドライバー固有のステートメント オプションを設定し、ODBC *2.x*バージョンのドライバーでオプションが定義されている場合は、ODBC *3.x*ドライバーのオプションに新しいマニフェスト定数を定義する必要があります。 古いマニフェスト定数が**SQLSetStmtOption**の呼び出しで使用されている場合、ドライバー マネージャーは *、文字列長の*引数を 0 に設定して**SQLSetStmtAttr**を呼び出します。  
  
 アプリケーションが**SQLSetStmtAttr**を呼び出して、ODBC *3.x*ドライバーでSQL_ATTR_USE_BOOKMARKSをSQL_UB_ONに設定すると、SQL_ATTR_USE_BOOKMARKSステートメント属性がSQL_UB_FIXEDに設定されます。 SQL_UB_FIXEDと同じ定数SQL_UB_ON。 ドライバー マネージャーは、ドライバーにSQL_UB_FIXEDを渡します。 ODBC *3.x*ではSQL_UB_FIXEDは非推奨でしたが、ODBC *3.x*ドライバは、固定長ブックマークを使用する ODBC *2.x*アプリケーションで動作するように実装する必要があります。  
  
 ODBC *3.x*ドライバの場合、ドライバ マネージャは、*オプション*がSQL_STMT_OPT_MINとSQL_STMT_OPT_MAXの間にあるか、またはSQL_CONNECT_OPT_DRVR_STARTより大きいかどうかをチェックしなくなりました。
