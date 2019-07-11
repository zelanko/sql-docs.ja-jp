---
title: SQLGetStmtOption のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLGetStmtOption
ms.assetid: fa599517-3f3e-4dad-a65a-b8596ae3f330
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98bbdcf66ed9ee8f2d716d8953fde8f4a888fca0
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792850"
---
# <a name="sqlgetstmtoption-mapping"></a>SQLGetStmtOption のマッピング
アプリケーションを呼び出すと**SQLGetStmtOption** odbc *3.x*ことへの呼び出しをサポートしていないドライバー  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 次のようになります。  
  
-   場合*fOption*ドライバー マネージャーの呼び出し、文字列を返すステートメントの ODBC で定義されたオプションを示します  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   場合*fOption*ドライバー マネージャーの呼び出し、32 ビット整数値を返すステートメントの ODBC で定義されたオプションを示します  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   場合*fOption*ドライバー定義ステートメントのオプション、ドライバー マネージャーの呼び出しを示します  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 上記の 3 つのケース、 *StatementHandle*引数の値に設定されて*hstmt*、*属性*引数の値に設定されて*fOption*、および*ValuePtr*引数と同じ値に設定されて*pvParam*します。  
  
 ODBC で定義された文字列の接続オプションは、ドライバー マネージャーの設定、 *BufferLength*への呼び出しで引数**SQLGetConnectAttr**定義済みの最大長 (SQL_MAX_OPTION_STRING_LENGTH)。文字列以外の接続オプション、 *BufferLength*は 0 に設定します。  
  
 ODBC で SQL_GET_BOOKMARK ステートメントのオプションが非推奨とされました*3.x*します。 ODBC の*3.x* ODBC を使用するドライバー *2.x* SQL_GET_BOOKMARK を使用するアプリケーション SQL_GET_BOOKMARK をサポートする必要があります。 ODBC の*3.x* ODBC を使用するドライバー *2.x*アプリケーションは、その必要がありますサポート SQL_UB_ON SQL_USE_BOOKMARKS に設定し、固定長のブックマークを公開する必要があります。 場合、ODBC *3.x*ドライバーは、可変長ブックマークいない固定長のブックマークをサポートしている、SQLSTATE HYC00 を返す必要があります (省略可能な機能が実装されていません) 場合は、ODBC *2.x*アプリケーションしようSQL_UB_ON SQL_USE_BOOKMARKS に設定します。  
  
 ODBC の*3.x*ドライバー、ドライバー マネージャーは不要になったを確認するかどうか*オプション*SQL_STMT_OPT_MIN と SQL_STMT_OPT_MAX、間、または SQL_CONNECT_OPT_DRVR_START よりも大きい。 ドライバーは、これを確認する必要があります。
