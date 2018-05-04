---
title: SQLGetStmtOption マッピング |Microsoft ドキュメント
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
- SQLGetStmtOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLGetStmtOption
ms.assetid: fa599517-3f3e-4dad-a65a-b8596ae3f330
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02eaacbe3503b5d93677633aa0e98326b14e304f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetstmtoption-mapping"></a>SQLGetStmtOption マッピング
アプリケーションを呼び出すと**SQLGetStmtOption** ODBC 3 *.x*への呼び出しをサポートしていないドライバー  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 次のようになります。  
  
-   場合*fOption*は、ドライバー マネージャー呼び出し文字列を返すステートメントの ODBC で定義されたオプションを示します  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   場合*fOption*ドライバー マネージャーの呼び出し、32 ビット整数値を返すステートメントの ODBC で定義されたオプションを示します  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   場合*fOption*ドライバー定義ステートメントのオプションでは、ドライバー マネージャーの呼び出しを示します  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 上記の 3 つのケースで、 *StatementHandle*引数の値に設定されて*hstmt*、*属性*引数の値に設定されて*fOption*、および*ValuePtr*引数と同じ値に設定されて*pvParam*です。  
  
 ODBC で定義された文字列の接続オプションでは、ドライバー マネージャーの設定、 *BufferLength*への呼び出しで引数**SQLGetConnectAttr**定義済みの最大長 (SQL_MAX_OPTION_STRING_LENGTH) です。文字列以外の接続オプション、 *BufferLength*は 0 に設定します。  
  
 ODBC 3 SQL_GET_BOOKMARK ステートメント オプションが廃止 *.x*です。 ODBC 3 *.x* ODBC 2 を使用するドライバー *。x* SQL_GET_BOOKMARK を使用するアプリケーション SQL_GET_BOOKMARK をサポートする必要があります。 ODBC 3 *.x* ODBC 2 を使用するドライバー *。x*アプリケーションは、その必要がありますサポート SQL_UB_ON SQL_USE_BOOKMARKS に設定し、固定長のブックマークを公開する必要があります。 場合、ODBC 3 *.x*ドライバーは、可変長ブックマークいない固定長のブックマークをサポートしている、SQLSTATE HYC00 を返す必要があります (省略可能な機能が実装されていません) 場合は、ODBC 2 *。x*アプリケーション SQL_UB_ON に SQL_USE_BOOKMARKS を設定しようとしました。  
  
 ODBC 3 *.x*ドライバー、ドライバー マネージャーは、不要になったを確認するかどうか*オプション*SQL_STMT_OPT_MIN と SQL_STMT_OPT_MAX、間、または SQL_CONNECT_OPT_DRVR_START よりも大きいです。 ドライバーは、これをチェックする必要があります。
