---
title: マッピングを行う |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetConnectOption
ms.assetid: a1b325cf-0c42-41c1-b141-b5a4fee7e708
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 757b50c7e18133e02b4cf6addaa327b2053f5439
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287472"
---
# <a name="sqlsetconnectoption-mapping"></a>SQLSetConnectOption のマッピング
ODBC 2 の場合。*x*アプリケーションは、ODBC 3 *.x*ドライバーを使用して**SQLSetConnect オプション**を呼び出します。  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 次のように結果が返されます。  
  
-   *fOption*が文字列を必要とする ODBC 定義の接続属性を示す場合、ドライバー マネージャーは、次のように呼び出します。  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   *fOption*が 32 ビット整数値を返す ODBC 定義の接続属性を示す場合、ドライバー マネージャーは、32 ビットの整数値を呼び出します。  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   *fOption が*ドライバ定義の接続属性を示す場合、ドライバ マネージャは  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 前の 3 つのケースでは、*引数引数*が*hdbc*の値に設定され、 *Attribute*引数は*fOption*の値に設定され *、ValuePtr*引数は*vParam*と同じ値に設定されます。  
  
 ドライバー マネージャーは、ドライバー定義の接続属性が文字列または 32 ビット整数値を必要とするかどうかを知らないので **、SQLSetConnectAttr**の*BufferLength*引数に有効な値を渡す必要があります。 ドライバーがドライバー定義の接続属性に対して特別なセマンティクスを定義しており **、SQLSetConnectOption**を使用して呼び出す必要がある場合は **、SQLSetConnect オプションを**サポートする必要があります。  
  
 ODBC 2 の場合。*x*アプリケーションは、ODBC 3 *.x*ドライバーでドライバー固有のステートメント オプションを設定する**SQLSetConnectOption**を呼び出し、ODBC 2 でオプションが定義されました。*x*バージョンのドライバーでは、新しいマニフェスト定数は、ODBC 3 *.x*ドライバーのオプションに対して定義する必要があります。 古いマニフェスト定数が**SQLSetConnectOption**の呼び出しで使用されている場合、ドライバー マネージャーは **、StringLength**引数を 0 に設定して**SQLSetConnectAttr**を呼び出します。  
  
 ODBC 3 *.x*ドライバの場合、ドライバ マネージャは *、fOption*がSQL_CONN_OPT_MINとSQL_CONN_OPT_MAXの間にあるか、またはSQL_CONNECT_OPT_DRVR_STARTより大きいかどうかをチェックしなくなりました。  
  
## <a name="setting-statement-options-on-the-connection-level"></a>接続レベルでのステートメントオプションの設定  
 ODBC 2 で。*x*を使用すると、アプリケーションが**SQLSetConnectOption**を呼び出してステートメント オプションを設定できます。 その後、ドライバーは、その接続に後で割り当てられたステートメントの既定としてステートメント オプションを確立します。 ドライバーが指定された接続に関連付けられている既存のステートメントのステートメント オプションを設定するかどうかは、ドライバー定義です。  
  
 この機能は ODBC 3 *.x*では廃止されました。 ODBC 3 *.x*ドライバは ODBC 2 の設定をサポートする必要があります。接続レベルで*x*ステートメント属性を使用する場合は、ODBC 2 を使用します。これを行う*x*アプリケーション。 ODBC 3 *.x*アプリケーションでは、接続レベルでステートメント属性を設定しないでください。 ODBC 3 *.x*ステートメント属性は、接続属性とステートメント属性の両方であるSQL_ATTR_METADATA_ID属性とSQL_ATTR_ASYNC_ENABLE属性を除き、接続レベルで設定することはできません。
