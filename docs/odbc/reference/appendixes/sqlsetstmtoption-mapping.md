---
title: SQLSetStmtOption マッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70bd586f601e8641c482b94d1a688bbdb1d528e9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetstmtoption-mapping"></a>SQLSetStmtOption マッピング
アプリケーションを呼び出すと**SQLSetStmtOption**から ODBC 3 *.x*ドライバーへの呼び出し  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 次のようになります。  
  
-   場合*fOption*文字列、ドライバー マネージャーの呼び出しであるステートメントの ODBC で定義された属性を示します  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   場合*fOption*ドライバー マネージャーの呼び出し、32 ビット整数値を返すステートメントの ODBC で定義された属性を示します  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   場合*fOption*ステートメントのドライバーの定義済みの属性では、ドライバー マネージャーの呼び出しを示します  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 上記の 3 つのケースで、 **StatementHandle**引数の値に設定されて*hstmt*、*属性*引数の値に設定されて*fOption*、および*ValuePtr*引数として値に設定されて*vParam*です。  
  
 有効な値で渡す必要がある、ドライバー マネージャーが、文字列または 32 ビット整数値には、ドライバーの定義済みのステートメント属性が必要かどうかを把握していないため、 *StringLength*の引数**SQLSetStmtAttr**. ドライバーがドライバーの定義済みのステートメント属性の特別な意味を定義し、呼び出す必要がありますを使用して場合**SQLSetStmtOption**、サポートする必要がある必要があります**SQLSetStmtOption**です。  
  
 アプリケーションを呼び出す場合**SQLSetStmtOption**オプションを設定する、ドライバー固有のステートメントで ODBC 3 *.x*ドライバーとオプションは、ODBC 2 内で定義されました*。x* ODBC 3 のオプションのドライバー、新しいマニフェスト定数のバージョンを定義する必要があります *.x*ドライバー。 呼び出しで、古いマニフェスト定数が使用されている場合**SQLSetStmtOption**、ドライバー マネージャーが呼び出す**SQLSetStmtAttr**で、 *StringLength*引数を 0 に設定されています。  
  
 アプリケーションを呼び出すと**SQLSetStmtAttr** SQL_ATTR_USE_BOOKMARKS を SQL_UB_ON ODBC 3 に設定する *.x*ドライバー、SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_FIXED に設定します。 SQL_UB_ON は、SQL_UB_FIXED として同じ定数です。 ドライバー マネージャーは、を通じて SQL_UB_FIXED をドライバーに渡します。 ODBC 3 SQL_UB_FIXED は廃止されて *.x*が、ODBC 3 *.x*ドライバーは ODBC 2 と連動するを実装する必要があります*。x*固定長のブックマークを使用するアプリケーション。  
  
 ODBC 3 *.x*ドライバー、ドライバー マネージャーがチェックされなくなるかどうかを*オプション*SQL_STMT_OPT_MIN と SQL_STMT_OPT_MAX、間、または SQL_CONNECT_OPT_DRVR_START よりも大きいです。
