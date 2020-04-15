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
- SQLGetStmtOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLGetStmtOption
ms.assetid: fa599517-3f3e-4dad-a65a-b8596ae3f330
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68819269d41407f2ce9dee172c889f7d7f286793
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300602"
---
# <a name="sqlgetstmtoption-mapping"></a>SQLGetStmtOption のマッピング
アプリケーションが**SQLGetStmtOption**をサポートしない ODBC *3.x*ドライバーを呼び出すと、呼び出し  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 次のように結果が返されます。  
  
-   *fOption*が文字列を返す ODBC 定義のステートメント オプションを示す場合、ドライバー マネージャーは、呼び出し  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   *fOption*が 32 ビット整数値を返す ODBC 定義のステートメント オプションを示す場合、ドライバー マネージャーは、32 ビットの整数値を呼び出します。  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   *fOption*がドライバ定義のステートメント オプションを示す場合、ドライバー マネージャーは  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 前の 3 つのケースでは、*引数引数*が*hstmt*の値に設定され、 *Attribute*引数は*fOption*の値に設定され *、ValuePtr*引数は*pvParam*と同じ値に設定されます。  
  
 ODBC 定義の文字列の接続文字列オプションの場合、ドライバー マネージャーは **、SQLGetConnectAttr**の呼び出しで*BufferLength*引数を定義済みの最大長 (SQL_MAX_OPTION_STRING_LENGTH) に設定します。文字列以外の接続文字列オプションの場合 *、BufferLength*は 0 に設定されます。  
  
 ODBC *3.x*ではSQL_GET_BOOKMARKステートメント オプションは使用されなくなりました。 ODBC *3.x*ドライバが、SQL_GET_BOOKMARKを使用する ODBC *2.x*アプリケーションで動作するには、SQL_GET_BOOKMARKをサポートする必要があります。 ODBC *2.x*アプリケーションで動作する ODBC *3.x*ドライバーは、SQL_UB_ONにSQL_USE_BOOKMARKSをサポートする必要があり、固定長のブックマークを公開する必要があります。 ODBC *3.x*ドライバが可変長ブックマークのみをサポートし、固定長ブックマークをサポートしていない場合、ODBC 2.x アプリケーションがSQL_UB_ONに設定SQL_USE_BOOKMARKSを試みた場合、ODBC *3.x*ドライバは SQLSTATE HYC00 (オプション機能は実装されていません) を返す必要があります。  
  
 ODBC *3.x*ドライバの場合、ドライバ マネージャは *、オプション*がSQL_STMT_OPT_MINとSQL_STMT_OPT_MAXの間にあるか、またはSQL_CONNECT_OPT_DRVR_STARTより大きいかどうかをチェックしなくなりました。 ドライバーはこれをチェックする必要があります。
